---
title: Cloud App Security で継続的なレポートの自動ログアップロードを構成する
description: この記事では、Cloud App Security で継続的なレポートの自動ログアップロードを構成するプロセスについて説明します。
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
ms.openlocfilehash: fb79f5515799ad93e456bb3a97bfa26d16416e5c
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285266"
---
# <a name="configure-automatic-log-upload-for-continuous-reports"></a>継続的なレポートのために自動ログ アップロードを構成する

*適用対象: Microsoft Cloud App Security*

ログ コレクターを使用すると、ネットワークからのログのアップロードを簡単に自動化することができます。 ログ コレクターをネットワーク上で実行すると、Syslog または FTP でログを受け取ります。 各ログは自動的に処理され、圧縮され、ポータルに送信されます。 FTP ログは、ファイルのログコレクターへの FTP 転送が完了した後に Microsoft Cloud App Security にアップロードされます。 Syslog の場合、ログコレクターは受信したログをディスクに書き込みます。 その後、ファイルのサイズが 40 KB を超えると、コレクターは Cloud App Security にファイルをアップロードします。

Cloud App Security にアップロードされたログは、バックアップディレクトリに移動されます。 バックアップディレクトリには、最後の20個のログが格納されます。 新しいログが移動されると、古いログは削除されます。 ログコレクターのディスク領域がいっぱいになると、ログコレクターは、空きディスク領域が増えるまで新しいログを削除します。 この場合、ログを **[自動的にアップロード]** する の設定の **[ログコレクター]** タブに警告が表示されます。

自動ログファイル収集を設定する前に、ログが予期されるログの種類と一致していることを確認してください。 Cloud App Security が特定のファイルを解析できることを確認する必要があります。 詳細については、「 [Cloud Discovery のトラフィックログの使用](create-snapshot-cloud-discovery-reports.md#log-format)」を参照してください。

> [!NOTE]
>
> * ログが元々の形式で転送されると仮定した場合、Cloud App Security は、SIEM サーバーからログ コレクターへのログの転送をサポートします。 ただし、ログ コレクターをファイアウォールまたはプロキシに直接統合することを強くお勧めします。
> * ログコレクターは、アップロードする前にデータを圧縮します。 ログコレクターの送信トラフィックは、受信したトラフィックログのサイズの10% になります。
> * ログコレクターで問題が発生した場合は、データを受信してから48時間が経過するとアラートが表示されます。

## <a name="deployment-modes"></a>展開モード

ログ コレクターでは、次の 2 つの展開モードがサポートされます。

* **コンテナー**: [Windows](discovery-docker-windows.md)、 [Ubuntu オンプレミス](discovery-docker-ubuntu.md)、 [Azure の ubuntu](discovery-docker-ubuntu-azure.md)、 [RHEL オンプレミス](discovery-docker-ubuntu.md)、または centos で Docker イメージとして実行されます。

* **仮想アプライアンス**: hyper-v または VMware ハイパーバイザー上のイメージとして実行されます (非推奨)

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)
