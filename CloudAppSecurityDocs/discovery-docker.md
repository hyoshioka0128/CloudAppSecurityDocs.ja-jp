---
title: Cloud App Security で継続的なレポートのために自動ログ アップロードを構成する
description: この記事では、Cloud App Security で継続的なレポートの自動ログ アップロードを構成するプロセスについて説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/22/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 73b9f8a7ea1bd3f2b93b4199b58cfb5178f13edc
ms.sourcegitcommit: 72c96b9b2b9f6555e5e20749ebe61593072b1d50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84487765"
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>継続的なレポートのために自動ログ アップロードを構成する

*適用対象:Microsoft Cloud App Security*

ログ コレクターを使用すると、ネットワークからのログのアップロードを簡単に自動化することができます。 ログ コレクターをネットワーク上で実行すると、Syslog または FTP でログを受け取ります。 各ログは自動的に処理および圧縮されてから、ポータルに送信されます。 FTP ログは、ログ コレクターへのファイルの FTP 転送が完了した後に、Microsoft Cloud App Security にアップロードされます。 Syslog の場合、ログ コレクターは受信したログをディスクに書き込みます。 その後、コレクターは、ファイル サイズが 40 KB を超えると、Cloud App Security にファイルをアップロードします。

Cloud App Security にアップロードされたログは、バックアップ ディレクトリに移動されます。 バックアップ ディレクトリには、最新の 20 個のログが格納されます。 新しいログが移動されると、古いログは削除されます。 ログ コレクターのディスク領域がいっぱいになると常に、空きディスク領域が増えるまで、ログ コレクターは新しいログを破棄します。 これが発生すると、**[ログを自動的にアップロード]** 設定の **[ログ コレクター]** タブに警告が表示されます。

自動ログ ファイル コレクションを設定する前に、ログが予想されるログの種類と一致することを確認します。 Cloud App Security が特定のファイルを解析できることを確認します。 詳細については、「[Cloud Discovery に対するトラフィック ログの使用](create-snapshot-cloud-discovery-reports.md#log-format)」をご覧ください。

> [!NOTE]
>
> * ログが元々の形式で転送されると仮定した場合、Cloud App Security は、SIEM サーバーからログ コレクターへのログの転送をサポートします。 ただし、ログ コレクターをファイアウォールやプロキシに直接統合することを強くお勧めします。
> * データは、アップロードされる前にログ コレクターによって圧縮されます。 ログ コレクターの送信トラフィックは、ログ コレクターが受信するトラフィック ログのサイズの 10% となります。
> * ログ コレクターに問題が発生した場合、データが 48 時間受信されなかった後にアラートを受け取ります。

## <a name="deployment-modes"></a>デプロイ モード

ログ コレクターでは、次の 2 つの展開モードがサポートされます。

* **コンテナー**: [Windows](discovery-docker-windows.md)、 [Ubuntu オンプレミス](discovery-docker-ubuntu.md)、 [Azure の ubuntu](discovery-docker-ubuntu-azure.md)、 [RHEL オンプレミス](discovery-docker-ubuntu.md)、または centos で Docker イメージとして実行されます。

* **仮想アプライアンス**: hyper-v または VMware ハイパーバイザー上のイメージとして実行されます (非推奨)

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)
