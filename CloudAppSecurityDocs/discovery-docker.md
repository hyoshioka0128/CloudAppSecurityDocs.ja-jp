---
title: 継続的なレポートのために自動ログ アップロードを構成する | Microsoft Docs
description: この記事では、Cloud App Security で継続的なレポートの自動ログ アップロードを構成するプロセスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c75ba963-ad5a-48e6-8d5d-610fc6e0b990
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 379d2153f0e309ca5694f132432249c7df81010d
ms.sourcegitcommit: 77850c6777504c2478611cb71a387e7fcc5f2551
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2018
ms.locfileid: "51596740"
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>継続的なレポートのために自動ログ アップロードを構成する

*適用対象: Microsoft Cloud App Security*

ログ コレクターを使用すると、ネットワークからのログのアップロードを簡単に自動化することができます。 ログ コレクターをネットワーク上で実行すると、Syslog または FTP でログを受け取ります。 各ログは自動的に処理および圧縮されてから、ポータルに送信されます。 FTP ログは、ログ コレクターへのファイルの FTP 転送が完了した後に、Microsoft Cloud App Security にアップロードされます。 Syslog の場合、ログ コレクターは受信したログをディスクに書き込みます。 その後、コレクターは、ファイル サイズが 40 KB を超えると、Cloud App Security にファイルをアップロードします。 

Cloud App Security にアップロードされたログは、バックアップ ディレクトリに移動されます。 バックアップ ディレクトリには、最新の 20 個のログが格納されます。 新しいログが移動されると、古いログは削除されます。 ログ コレクターのディスク領域がいっぱいになると常に、空きディスク領域が増えるまで、ログ コレクターは新しいログを破棄します。 これが発生すると、**[ログを自動的にアップロード]** 設定の **[ログ コレクター]** タブに警告が表示されます。

自動ログ ファイル コレクションを設定する前に、ログが予想されるログの種類と一致することを確認します。 Cloud App Security が特定のファイルを解析できることを確認します。 詳細については、「[Cloud Discovery に対するトラフィック ログの使用](create-snapshot-cloud-discovery-reports.md#log-format)」をご覧ください。


> [!NOTE]
>-  ログが元々の形式で転送されると仮定した場合、Cloud App Security は、SIEM サーバーからログ コレクターへのログの転送をサポートします。 ただし、ログ コレクターをファイアウォールやプロキシに直接統合することを強くお勧めします。
>- データはアップロードされる前に、ログ コレクターによって圧縮されます。 ログ コレクターの送信トラフィックは、ログ コレクターが受信するトラフィック ログのサイズの 10% となります。 
>-  ログ コレクターに問題が発生した場合、データが 48 時間受信されなかった後にアラートを受け取ります。
>

## <a name="deployment-modes"></a>展開モード

ログ コレクターでは、次の 2 つの展開モードがサポートされます。

-   **コンテナー**: [オンプレミス Ubuntu](discovery-docker-ubuntu.md)、[Azure の Ubuntu](discovery-docker-ubuntu-azure.md)、または [オンプレミス RHEL](discovery-docker-ubuntu.md) で Docker イメージとして実行します。 

-   **仮想アプライアンス**: [Hyper-V または VMware ハイパーバイザー上のイメージとして実行します](configure-automatic-log-upload-for-continuous-reports.md)




## <a name="next-steps"></a>次の手順
 
[Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)

