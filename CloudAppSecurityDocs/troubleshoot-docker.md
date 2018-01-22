---
title: "Cloud Discovery の Docker の展開に関するトラブルシューティング | Microsoft Docs"
description: "このトピックでは、Cloud App Security の Cloud Discovery の Docker 構成を変更するプロセスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b994661f0f875db100a0aa2eb293b88e637b89cb
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2018
---
# <a name="troubleshooting-the-cloud-app-security-cloud-discovery-docker"></a>Cloud App Security の Cloud Discovery の Docker のトラブルシューティング

## <a name="changing-the-ftp-password"></a>FTP パスワードの変更


1. ログ コレクター ホストに接続します。

2.  `docker exec -it <collector name> pure-pw passwd <ftp user>` を実行します。

    1. 新しいパスワードを入力します。
    2. 確認のために、新しいパスワードをもう一度入力します。
 
3.  `docker exec -it <collector name> pure-pw mkdb` を実行して変更を適用します。


  ![FTP パスワードの変更](./media/ftp-connect.png)

## <a name="customize-certificate-files"></a>証明書ファイルのカスタマイズ

この手順に従って、Cloud Discovery Docker へのセキュリティで保護された接続で使用する証明書ファイルをカスタマイズできます。

1.  FTP クライアントを開いて、ログ コレクターに接続します。

  ![FTP クライアントへの接続](./media/ftp-connect.png)

2.  `ssl_update` ディレクトリに移動します。
3.  新しい証明書ファイルを `ssl_update` ディレクトリにアップロードします (名前は必須)。

    ![FTP パスワードの変更](./media/new-certs.png)

    1.  FTP: キーと証明書データをこの順序で含む、**pure-ftpd.pem** という名前の 1 ファイルのみが必要です。
    
    2.  Syslog: **ca.pem**、**server-key.pem**、**server-cert.pem** という 3 つのファイルが必要です。 いずれかのファイルが欠けていると、更新は行われません。

4.  ターミナルでの実行: `docker exec -t <collector name> update_certs` これにより、次の画面と同様の出力が表示されます。

    ![FTP パスワードの変更](./media/update-certs.png)

## <a name="see-also"></a>参照
[Cloud Discovery の展開](set-up-cloud-discovery.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます](https://premier.microsoft.com/)

