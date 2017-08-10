---
title: "継続的なレポートのために自動ログ アップロードを構成する | Microsoft Docs"
description: "このトピックでは、Cloud App Security で継続的なレポートの自動ログ アップロードを構成するプロセスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/6/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c75ba963-ad5a-48e6-8d5d-610fc6e0b990
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a102951d6600f960ee9c045f6ce6fdb3adbe1f42
ms.sourcegitcommit: f9851779aa15b11f559e56ac818f1333f027c000
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2017
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>継続的なレポートのために自動ログ アップロードを構成する


ログ コレクターを使用すると、ネットワークからのログのアップロードを簡単に自動化することができます。 ログ コレクターをネットワーク上で実行すると、Syslog または FTP でログを受け取ります。 各ログは自動的に処理および圧縮されてから、ポータルに送信されます。 FTP ログは、ログ コレクターへのファイルの FTP 転送が完了した後に、Cloud App Security にアップロードされます。  Syslog の場合、ログ コレクターは受信したログをディスクに書き込み、そのファイル サイズが 40 KB より大きい場合に、ファイルを Cloud App Security にアップロードします。

ログが Cloud App Security にアップロードされた後は、バックアップ ディレクトリに移動されます。このディレクトリには、常に最新の 20 個のログが保存されています。 新しいログが移動されると、古いログは削除されます。 ログ コレクターのディスク領域がいっぱいになると、空きディスク領域が増えるまで、ログ コレクターは新しいログを削除します。 これが発生すると、**[ログを自動的にアップロード]** 設定の **[ログ コレクター]** タブに警告が表示されます。

自動ログ ファイル収集を設定する前に、ログが予期されるログの種類と一致していることを検証し、Cloud App Security で特定のファイルを解析できることを確認します。

> [!NOTE]
> ログが元々の形式で転送されると仮定した場合、Cloud App Security は、SIEM サーバーからログ コレクターへのログの転送をサポートします。 ただし、ログ コレクターをファイアウォールやプロキシに直接統合することを強くお勧めします。

## <a name="deployment-modes"></a>展開モード

ログ コレクターでは、次の 2 つの展開モードがサポートされます。

-   **コンテナー** (*プレビュー*): オンプレミスと Azure のいずれかで、[Windows](discovery-docker-windows.md) および [Ubuntu](discovery-docker-ubuntu.md) 上の Docker イメージとして実行します。 



-   **仮想アプライアンス** (*非推奨*): [Hyper-V または VMware ハイパーバイザー上のイメージとして実行します](configure-automatic-log-upload-for-continuous-reports.md)。




## <a name="see-also"></a>関連項目
 
[Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)

