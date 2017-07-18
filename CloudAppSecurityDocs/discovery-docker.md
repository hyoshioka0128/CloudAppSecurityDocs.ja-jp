---
title: "継続的なレポートのために自動ログ アップロードを構成する | Microsoft Docs"
description: "このトピックでは、Cloud App Security での継続的なレポートのために、自動ログ アップロードを構成する手順について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/9/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c75ba963-ad5a-48e6-8d5d-610fc6e0b990
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9f17366c62b202432d8b0c750290b4915f64c929
ms.sourcegitcommit: b2e3af9d0a62dcb6410cc3992183c2888bdf6a2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2017
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>継続的なレポートのために自動ログ アップロードを構成する


ログ コレクターを使用すると、ネットワークからのログのアップロードを簡単に自動化することができます。 ログ コレクターをネットワーク上で実行すると、Syslog または FTP でログを受け取ります。 各ログは自動的に処理および圧縮されてから、ポータルに送信されます。 ファイルがログ コレクターに FTP 転送された後、FTP ログが Cloud App Security にアップロードされます。  Syslog の場合、ログ コレクターは受信したログをディスクに書き込み、ファイル サイズが 40 KB を超えると、ファイルが Cloud App Security にアップロードされます。

ログが Cloud App Security にアップロードされた後は、バックアップ ディレクトリに移動されます。このディレクトリには、常に最新の 20 個のログが保存されています。 新しいログが移動されると、古いログは削除されます。 ログ コレクターのディスク領域がいっぱいになると、空きディスク領域が増えるまで、ログ コレクターは新しいログを削除します。

自動ログ ファイル収集を設定する前に、ログが予期されるログの種類と一致していることを検証し、Cloud App Security で特定のファイルを解析できることを確認します。

> [!NOTE]
> ログが元々の形式で転送されると仮定した場合、Cloud App Security は、SIEM サーバーからログ コレクターへのログの転送をサポートします。 ただし、ログ コレクターをファイアウォールまたはプロキシに直接統合することを強くお勧めします。

## <a name="deployment-modes"></a>展開モード

ログ コレクターでは、次の 2 つの展開モードがサポートされます。

-   **コンテナー** (*Docker CE を基にする*): オンプレミスまたは Azure のいずれかで、[Windows](discovery-docker-windows.md) および [Ubuntu](discovery-docker-ubuntu.md) の Docker イメージとして実行します。

-   **仮想アプライアンス** (*非推奨*): [Hyper-V または VMware ハイパーバイザーのイメージとして実行します](configure-automatic-log-upload-for-continuous-reports.md)




## <a name="see-also"></a>関連項目
 
[Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)

