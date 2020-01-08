---
title: プロキシの背後でログ コレクターを有効にする - Cloud App Security | Microsoft Docs
description: この記事では、プロキシの背後から Cloud App Security の Cloud Discovery ログ コレクターを有効にする方法について説明します。
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
ms.openlocfilehash: c5d4132dd88f8bf7364a77ee8a3e282c1af7fa02
ms.sourcegitcommit: 010725c70ff7b3fc9abdad92203eec6e72bb7473
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/26/2019
ms.locfileid: "75492091"
---
# <a name="enable-the-log-collector-behind-a-proxy"></a>プロキシの背後でログ コレクターを有効にする

ログ コレクターの構成後、プロキシの背後で実行すると、ログ コレクターから Cloud App Security へのデータの送信に問題が発生する場合があります。 これは、プロキシのルート証明機関がログ コレクターに信頼されていないため、Microsoft Cloud App Security に接続してその構成を取得したり、受信したログをアップロードしたりできないことが原因となっている可能性があります。

>[!NOTE]
> Syslog または FTP のログコレクターによって使用される証明書を変更する方法、およびファイアウォールとプロキシからログコレクターへの接続に関する問題を解決する方法については、「[ログコレクターの FTP 構成](log-collector-ftp.md)」を参照してください。
>

## <a name="set-up-the-log-collector-behind-a-proxy"></a>プロキシの背後でログ コレクターを設定する

Windows または Linux コンピューター上で Docker を実行し、Cloud App Security の Docker イメージをコンピューター上に正常にダウンロードするために必要な手順を実行したことを確認してください。 詳細については、「[継続的なレポートのために自動ログ アップロードを構成する](discovery-docker.md)」をご覧ください。

### <a name="validate-docker-log-collector-container-creation"></a>ログ コレクターの Docker コンテナーの作成を確認する

シェルで次のコマンドを使って、コンテナーが作成され、稼働していることを確認します。

```bash
docker ps
```

![docker ps](media/docker-1.png)

### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>プロキシのルート CA 証明書をコンテナーにコピーする

ご自身の仮想マシンから、CA 証明書を Cloud App Security のコンテナーにコピーします。 次の例では、コンテナーの名前は *Ubuntu-LogCollector*、CA 証明書の名前は *Proxy-CA.crt* となっています。
Ubuntu ホスト上でコマンドを実行します。 稼働中のコンテナー内のフォルダーに証明書がコピーされます。

```bash
docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery
```

### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>CA 証明書と連携するよう構成を設定する

1. 次のコマンドを使ってコンテナー内に移動します。 ログ コレクターのコンテナー内で bash が開かれます。

    ```bash
    docker exec -it Ubuntu-LogCollector /bin/bash
    ```

2. コンテナー内の bash から、Java *jre*フォルダーにアクセスします。 バージョンに関するパスのエラーを回避するために、このコマンドを使います。

    ```bash
    cd 'find /opt/jdk/*/jre -iname bin'
    ```

3. 先ほどコピーしたルート証明書を、[*探索*] フォルダーから Java キーストアにインポートし、パスワードを定義します。 既定のパスワードは "changeit" です。 パスワードの変更の詳細については、「 [Java キーストアのパスワードを変更する方法](#how-to-change-the-java-keystore-password)」を参照してください。

    ```bash
    ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass <password>
    ```

4. 次のコマンドを使ってインポート中に指定した別名 (*SelfSignedCert*) を検索することで、証明書が CA キーストアに正しくインポートされたことを確認します。

    ```bash
    ./keytool --list --keystore ../lib/security/cacerts | grep self
    ```

    ![keytool](media/docker-2.png "keytool")

インポートしたプロキシの CA 証明書が表示されます。

### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>新しい構成で実行されるようログ コレクターを設定する

コンテナーの準備が整いました。

ログ コレクターの作成中に使った API トークンを使って、**collector_config** コマンドを実行します。

![API トークン](media/docker-3.png "API トークン")

コマンドを実行するときに、ご自身の API トークンを指定します。

```bash
collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}
```

![構成の更新](media/docker-4.png "構成の更新")

これでログ コレクターが Cloud App Security と通信できるようになりました。 これにデータを送信すると、Cloud App Security ポータルでその状態が **[正常]** から **[接続済み]** に変わります。

![状態](media/docker-5.png "状態")

>[!NOTE]
> ログ コレクターの構成を更新する必要がある場合 (たとえば、データ ソースを追加または削除する場合) は、通常はコンテナーを**削除**して、前の手順をもう一度実行する必要があります。 これを回避するために、Cloud App Security ポータルで生成された新しい API トークンを使って *collector_config* ツールを再実行することができます。

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

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [ユーザー アクティビティ ポリシー](user-activity-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
