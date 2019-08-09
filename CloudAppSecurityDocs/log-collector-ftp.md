---
title: ログコレクターの FTP 構成
description: この記事では、Cloud App Security の Cloud Discovery の Docker 構成を変更するプロセスについて説明します。
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 8/7/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 776e834f-3c20-4d5f-9fab-4c5b975edb06
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ab97993b283df9a6669fcb475bc60d6030accbae
ms.sourcegitcommit: 39faa183e7d781660d475c79c827adbb4cc635fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68878829"
---
# <a name="log-collector-ftp-configuration"></a>ログコレクターの FTP 構成

*適用対象:Microsoft Cloud App Security*

この記事では、Cloud App Security の Cloud Discovery の Docker 構成を変更する方法について説明します。

## <a name="docker-deployment"></a>Docker の展開

Cloud App Security の Cloud Discovery の Docker 構成を変更する必要がある場合があります。

### <a name="changing-the-ftp-password"></a>FTP パスワードの変更

1. ログ コレクター ホストに接続します。

2. `docker exec -it <collector name> pure-pw passwd <ftp user>`を実行します。

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
    - **Syslog:** **ca.pem**、\*\*server-key.pem、**server-cert.pem** という 3 つのファイルが必要です。 いずれかのファイルが欠けていると、更新は行われません。

4. ターミナルでの実行: `docker exec -t <collector name> update_certs` このコマンドにより、次のスクリーンショットと同様の出力が表示されます。

    ![FTP パスワードの変更](./media/update-certs.png)

## <a name="next-steps"></a>次の手順

[Cloud Discovery の展開](set-up-cloud-discovery.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)