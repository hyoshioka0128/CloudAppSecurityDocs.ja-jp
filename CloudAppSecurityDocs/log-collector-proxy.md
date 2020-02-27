---
title: プロキシの背後でログコレクターを有効にする-Cloud App Security |Microsoft Docs
description: この記事では、プロキシの背後から Cloud App Security Cloud Discovery ログコレクターを有効にする方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/6/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2b6d888c90a3e21ee98002372c16484f6a471610
ms.sourcegitcommit: d340917143d37ded0dd342a277a1b6ad267f9a7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2020
ms.locfileid: "77618450"
---
# <a name="enable-the-log-collector-behind-a-proxy"></a>プロキシの背後でログコレクターを有効にする

ログコレクターを構成した後、プロキシの内側で実行している場合は、ログコレクターが Cloud App Security にデータを送信するときに問題が発生する可能性があります。 これは、log collector がプロキシのルート証明機関を信頼しておらず、Microsoft Cloud App Security に接続してその構成を取得したり、受信したログをアップロードしたりできないために発生する可能性があります。

>[!NOTE]
> Syslog または FTP のログコレクターによって使用される証明書を変更する方法、およびファイアウォールとプロキシからログコレクターへの接続に関する問題を解決する方法については、「[ログコレクターの FTP 構成](log-collector-ftp.md)」を参照してください。
>

## <a name="set-up-the-log-collector-behind-a-proxy"></a>プロキシの背後にログコレクターを設定する

Windows または Linux コンピューターで Docker を実行するために必要な手順を実行したことを確認し、コンピューターに Cloud App Security Docker イメージを正常にダウンロードします。 詳細については、「[継続的なレポートのために自動ログアップロードを構成する](discovery-docker.md)」を参照してください。

### <a name="validate-docker-log-collector-container-creation"></a>Docker ログコレクターコンテナーの作成の検証

シェルで、次のコマンドを使用して、コンテナーが作成され、実行されていることを確認します。

```bash
docker ps
```

![docker ps](media/docker-1.png)

### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>プロキシルート CA 証明書をコンテナーにコピーする

仮想マシンから、Cloud App Security コンテナーに CA 証明書をコピーします。 次の例では、コンテナーの名前は*Ubuntu-LogCollector*で、CA 証明書には*Proxy-CA*という名前が付けられています。
Ubuntu ホストでコマンドを実行します。 次のように、実行中のコンテナー内のフォルダーに証明書をコピーします。

```bash
docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery
```

### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>CA 証明書を使用するように構成を設定する

1. 次のコマンドを使用して、コンテナーに移ります。 ログコレクターコンテナーで bash が開きます。

    ```bash
    docker exec -it Ubuntu-LogCollector /bin/bash
    ```

2. コンテナー内の bash から、Java *jre*フォルダーにアクセスします。 バージョンに関連するパスエラーを回避するには、次のコマンドを使用します。

    ```bash
    cd "$(find /opt/jdk/*/jre -name "bin" -printf '%h' -quit)"
    ```

3. 先ほどコピーしたルート証明書を、[*探索*] フォルダーから Java キーストアにインポートし、パスワードを定義します。 既定のパスワードは "changeit" です。 パスワードの変更の詳細については、「 [Java キーストアのパスワードを変更する方法](#how-to-change-the-java-keystore-password)」を参照してください。

    ```bash
    ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass <password>
    ```

4. 次のコマンドを使用して、インポート中に指定したエイリアス (*Selfsignedcert*) を検索し、証明書が CA キーストアに正しくインポートされたことを確認します。

    ```bash
    ./keytool --list --keystore ../lib/security/cacerts | grep self
    ```

    ![keytool](media/docker-2.png "keytool")

インポートしたプロキシ CA 証明書が表示されます。

### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>新しい構成で実行するようにログコレクターを設定します。

これでコンテナーの準備ができました。

Log collector の作成時に使用した API トークンを使用して、 **collector_config**コマンドを実行します。

![API トークン](media/docker-3.png "API トークン")

コマンドを実行するときに、独自の API トークンを指定します。

```bash
collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}
```

![構成の更新](media/docker-4.png "構成の更新")

ログコレクターが Cloud App Security と通信できるようになりました。 データを送信すると、Cloud App Security ポータルで状態が "**健全**" から " **Connected** " に変わります。

![状態](media/docker-5.png "状態")

>[!NOTE]
> たとえば、ログコレクターの構成を更新する必要がある場合、データソースを追加または削除するには、通常、コンテナーを**削除**し、前の手順を再度実行する必要があります。 これを回避するには、Cloud App Security ポータルで生成された新しい API トークンを使用して*collector_config*ツールを再実行します。

## <a name="how-to-change-the-java-keystore-password"></a>Java キーストアのパスワードを変更する方法

1. Java キーストアサーバーを停止します。
1. コンテナー内で bash シェルを開き、 *appdata/conf*フォルダーにアクセスします。
1. 次のコマンドを使用して、サーバーキーストアのパスワードを変更します。

    ```bash
    keytool -storepasswd -new newStorePassword -keystore server.keystore
    -storepass changeit
    ```

    > [!NOTE]
    > 既定のサーバーパスワードは*changeit*です。

1. 次のコマンドを使用して、証明書のパスワードを変更します。

    ```bash
    keytool -keypasswd -alias server -keypass changeit -new newKeyPassword -keystore server.keystore -storepass newStorePassword
    ```

    > [!NOTE]
    > 既定のサーバーの別名は*server*です。

1. テキストエディターで*server-install\conf\server\secured-installed.properties*ファイルを開き、次のコード行を追加して、変更を保存します。
    1. サーバーの新しい Java キーストアパスワードを指定してください: `server.keystore.password=newStorePassword`
    1. サーバーの新しい証明書のパスワードを指定してください: `server.key.password=newKeyPassword`
1. サーバーを起動します。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [ユーザーアクティビティポリシー](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
