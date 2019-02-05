---
title: プロキシの背後でログ コレクターを有効にする - Cloud App Security | Microsoft Docs
description: この記事では、プロキシの背後から Cloud App Security の Cloud Discovery ログ コレクターを有効にする方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/2/2019
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 6bde2a6c-60cc-4a7d-9e83-e8b81ac229b0
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b256affd64705b874e68359c51af118b355330df
ms.sourcegitcommit: 7b1b1e80f90bd12e38a2e14dfea6708341eb0f34
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2019
ms.locfileid: "55668930"
---
# <a name="enable-the-log-collector-behind-a-proxy"></a>プロキシの背後でログ コレクターを有効にする

ログ コレクターの構成後、プロキシの背後で実行すると、ログ コレクターから Cloud App Security へのデータの送信に問題が発生する場合があります。 これは、プロキシのルート証明機関がログ コレクターに信頼されていないため、Microsoft Cloud App Security に接続してその構成を取得したり、受信したログをアップロードしたりできないことが原因となっている可能性があります。

>[!NOTE] 
> Syslog や FTP 用にログ コレクターで使われる証明書を変更する方法や、ファイアウォールやプロキシからログ コレクターまで、接続に関する問題を解決する方法については、「[Microsoft Cloud App Security の Cloud Discovery の展開に関するトラブルシューティング](troubleshoot-docker.md)」をご覧ください。
>

## <a name="set-up-the-log-collector-behind-a-proxy"></a>プロキシの背後でログ コレクターを設定する

Windows または Linux コンピューター上で Docker を実行し、Cloud App Security の Docker イメージをコンピューター上に正常にダウンロードするために必要な手順を実行したことを確認してください。 詳細については、「[継続的なレポートのために自動ログ アップロードを構成する](discovery-docker.md)」をご覧ください。

### <a name="validate-docker-log-collector-container-creation"></a>ログ コレクターの Docker コンテナーの作成を確認する

シェルで次のコマンドを使って、コンテナーが作成され、稼働していることを確認します。

    bash
    docker ps


![docker ps](./media/docker-1.png "docker ps")

### <a name="copy-proxy-root-ca-certificate-to-the-container"></a>プロキシのルート CA 証明書をコンテナーにコピーする

ご自身の仮想マシンから、CA 証明書を Cloud App Security のコンテナーにコピーします。 次の例では、コンテナーの名前は *Ubuntu-LogCollector*、CA 証明書の名前は *Proxy-CA.crt* となっています。
Ubuntu ホスト上でコマンドを実行します。 稼働中のコンテナー内のフォルダーに証明書がコピーされます。

    bash
    docker cp Proxy-CA.crt Ubuntu-LogCollector:/var/adallom/ftp/discovery


### <a name="set-the-configuration-to-work-with-the-ca-certificate"></a>CA 証明書と連携するよう構成を設定する

1. 次のコマンドを使ってコンテナー内に移動します。 ログ コレクターのコンテナー内で bash が開かれます。

        bash
        docker exec -it Ubuntu-LogCollector /bin/bash

2. コンテナー内の bash から、Java の jre ディレクトリに移動します。 バージョンに関するパスのエラーを回避するために、このコマンドを使います。

       bash
       cd 'find /opt/jdk/*/jre -iname bin'

3. 先ほどコピーしたルート証明書を、*discovery* フォルダーから Java のキーストアにインポートして、パスワードを定義します。 既定のパスワードは "changeit" です。

       bash
       ./keytool --import --noprompt --trustcacerts --alias SelfSignedCert --file /var/adallom/ftp/discovery/Proxy-CA.crt --keystore ../lib/security/cacerts --storepass changeit


4. 次のコマンドを使ってインポート中に指定した別名 (*SelfSignedCert*) を検索することで、証明書が CA キーストアに正しくインポートされたことを確認します。

       bash
       ./keytool --list --keystore ../lib/security/cacerts | grep self


![keytool](./media/docker-2.png "keytool")

インポートしたプロキシの CA 証明書が表示されます。

### <a name="set-the-log-collector-to-run-with-the-new-configuration"></a>新しい構成で実行されるようログ コレクターを設定する

コンテナーの準備が整いました。 

ログ コレクターの作成中に使った API トークンを使って、**collector_config** コマンドを実行します。

![API トークン](./media/docker-3.png "API トークン")

コマンドを実行するときに、ご自身の API トークンを指定します。

      bash
      collector_config abcd1234abcd1234abcd1234abcd1234 ${CONSOLE} ${COLLECTOR}


![構成の更新](./media/docker-4.png "構成の更新")

これでログ コレクターが Cloud App Security と通信できるようになりました。 これにデータを送信すると、Cloud App Security ポータルでその状態が **[正常]** から **[接続済み]** に変わります。

![状態](./media/docker-5.png "状態")

>[!NOTE]
> ログ コレクターの構成を更新する必要がある場合 (たとえば、データ ソースを追加または削除する場合) は、通常はコンテナーを**削除**して、前の手順をもう一度実行する必要があります。 これを回避するために、Cloud App Security ポータルで生成された新しい API トークンを使って *collector_config* ツールを再実行することができます。



 
  
## <a name="next-steps"></a>次の手順 
[ユーザー アクティビティ ポリシー](user-activity-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  