---
title: Cloud Discovery の Docker のデプロイに関するトラブルシューティング
description: この記事では、Cloud App Security の Cloud Discovery の Docker 構成を変更するプロセスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 01fa2f69422bd3c1c272a76c113254f819b90137
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56280881"
---
# <a name="troubleshooting-the-microsoft-cloud-app-security-cloud-discovery-deployment"></a>Microsoft Cloud App Security の Cloud Discovery の展開に関するトラブルシューティング

*適用対象:Microsoft Cloud App Security*

この記事では、Cloud App Security の Cloud Discovery の Docker 構成を変更する方法について説明します。

## <a name="windows-defender-atp-integration"></a>Windows Defender ATP の統合

Windows Defender ATP と Cloud App Security を統合し、統合の結果が表示されない (**Win10 エンドポイント ユーザー** レポートがない) 場合は、接続しているマシンが Windows 10 バージョン 1809 以降であること、およびデータにアクセスできるようになるまでに必要な 2 時間待ったことを確認します。

## <a name="docker-deployment"></a>Docker の展開

Cloud App Security の Cloud Discovery の Docker 構成を変更する必要がある場合があります。 

### <a name="changing-the-ftp-password"></a>FTP パスワードの変更

1. ログ コレクター ホストに接続します。

2. `docker exec -it <collector name> pure-pw passwd <ftp user>` を実行します。

    1. 新しいパスワードを入力します。
    2. 確認のために、新しいパスワードをもう一度入力します。
 
3. `docker exec -it <collector name> pure-pw mkdb` を実行して変更を適用します。

  ![FTP パスワードの変更](./media/ftp-connect.png)

### <a name="customize-certificate-files"></a>証明書ファイルのカスタマイズ

この手順に従って、Cloud Discovery Docker へのセキュリティで保護された接続で使用する証明書ファイルをカスタマイズできます。

1. FTP クライアントを開いて、ログ コレクターに接続します。

   ![FTP クライアントへの接続](./media/ftp-connect.png)

2. `ssl_update` ディレクトリに移動します。
3. 新しい証明書ファイルを `ssl_update` ディレクトリにアップロードします (名前は必須)。

   ![FTP パスワードの変更](./media/new-certs.png)

    - **FTP:** 1 ファイルのみが必要です。 このファイルは、キーと証明書データをこの順序で含む、**pure-ftpd.pem** という名前です。
    - **Syslog:** **ca.pem**、**server-key.pem、**server-cert.pem** という 3 つのファイルが必要です。 いずれかのファイルが欠けていると、更新は行われません。

4. ターミナルでの実行: `docker exec -t <collector name> update_certs` このコマンドにより、次のスクリーンショットと同様の出力が表示されます。

   ![FTP パスワードの変更](./media/update-certs.png)

## <a name="next-steps"></a>次の手順

[Cloud Discovery の展開](set-up-cloud-discovery.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます](https://premier.microsoft.com/)
