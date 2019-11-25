---
title: Integrate Microsoft Defender ATP with Cloud App Security
description: This article describes how to integrate Microsoft Defender Advanced Threat Protection with Cloud App Security for enhanced visibility into Shadow IT and risk management.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/11/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: aeddfb56542309b0ee6b1f0d4cdec85bb36a120e
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459434"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Microsoft Defender Advanced Threat Protection integration with Microsoft Cloud App Security

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security integrates with Microsoft Defender Advanced Threat Protection (ATP) natively. 統合により、Cloud Discovery のロールアウトが簡単になり、Cloud Discovery の機能が企業ネットワークの範囲を超えて拡張され、マシンベースの調査が可能になりします。 [Microsoft Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) is a security platform for intelligent protection, detection, investigation, and response. Microsoft Defender ATP protects endpoints from cyber threats, detects advanced attacks and data breaches, automates security incidents, and improves security posture.

Microsoft Cloud App Security uses the traffic information collected by Microsoft Defender ATP about the cloud apps and services being accessed from IT-managed Windows 10 machines. 統合により、ローミングおよびリモート アクセスの間にパブリック Wi-Fi を使用して、企業ネットワーク内のマシンで Cloud Discovery を実行できます。 また、マシンベースの調査も可能になります。

リスクの高いユーザーが見つかったら、そのユーザーがアクセスしたすべてのマシンを調べて、潜在的なリスクを検出できます。 リスクの高いマシンが見つかったら、そのマシンを使用したすべてのユーザーを調べて、潜在的なリスクを検出できます。 Cloud App Security にルーティングされたエンドポイントからのログでは、トラフィック アクティビティに関するユーザー情報が提供されます。 Microsoft Defender ATP network activity provides device context. デバイス コンテキストとユーザー名を組み合わせると、ネットワーク全体でどのユーザーがどのマシンからどのアクティビティを実行したかが詳細にわかります。

Microsoft Cloud App Security uses the native integration with Microsoft Defender ATP to tap into data about cloud app and service traffic from managed Windows devices. 統合では、標準以外の追加の展開と作業は必要ありません。 エンドポイントからトラフィックをルーティングまたはミラーリングする必要も、複雑な統合の手順を行う必要もありません。

> [!NOTE]
> Want to experience Microsoft Defender ATP? [無料試用版にサインアップしてください](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)。
>


## <a name="prerequisites"></a>必要条件

- Microsoft Cloud App Security ライセンス
- Microsoft Defender ATP license
- Windows 10 version 1709 (OS Build 16299.1085 with KB4493441), Windows 10 version 1803 (OS Build 17134.704 with KB4493464), Windows 10 version 1809 (OS Build 17763.379 with KB4489899) or later Windows 10 versions
- **[プレビュー機能]** をオンに切り替え、Cloud App Security でこの機能を有効にする

## <a name="how-it-works"></a>しくみ

Cloud App Security は自動的に、[ユーザーがアップロードしたログ](create-snapshot-cloud-discovery-reports.md)を使用するか、または[自動ログ アップロードを構成する](discovery-docker.md)ことにより、エンドポイントからログを収集します。 Native integration enables you to take advantage of the logs Microsoft Defender ATP's agent creates when it runs on Windows and monitors network transactions. この情報を、ネットワーク上の Windows マシンでのシャドウ IT の検出に使用できます。

To enable you to perform Cloud Discovery across other platforms, it's best to use both the Cloud App Security [log collector](discovery-docker.md), along with Microsoft Defender ATP integration to monitor your Windows 10 machines.

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>How to integrate Microsoft Defender ATP with Cloud App Security

To enable integration with Cloud App Security from Microsoft Defender ATP:

1. In the Microsoft Defender ATP portal, from the navigation pane, select **Preferences setup**.
2. **[設定]** メニューの **[全般]** の **[高度な機能]** を選択します。
3. **[Microsoft Cloud App Security]** を **[オン]** に切り替えます。
4. **[Save preferences]\(基本設定の保存\)** をクリックします。

>[!NOTE]
> データの統合を有効にしてから Cloud App Security に表示されるまで、最大で 2 時間かかります。
>

   ![WD ATP の設定](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Cloud App Security でマシンを調査する

After you integrate Microsoft Defender ATP with Cloud App Security, you can investigate discovered machine data in the Cloud Discovery dashboard.

1. Cloud App Security ポータルで、 **[Cloud Discovery]** 、 **[Cloud Discovery dashboard]\(Cloud Discovery ダッシュボード\)** の順にクリックします。
2. 上部のナビゲーション バーで、 **[継続的レポート]** の **[Win10 endpoint users]\(Win10 エンドポイント ユーザー\)** を選択します。
  ![WD ATP レポート](./media/win10-dashboard-report.png)
3. 上部では、検出されたマシンの数が統合後に追加されていることがわかります。
4. **[マシン]** タブをクリックします。
5. リストの各マシンにドリルダウンし、タブを使用して、調査データを表示します。 インシデントに関係したマシン、ユーザー、IP アドレス、アプリの間の相関関係を検索します。
   - **概要**
      - Transactions: Information about the number of transactions that took place on the machine over the selected period of time.
      - Total traffic: Information about the total amount of traffic (in MB) over the selected period of time.
     - Uploads: Information about the total amount of traffic (in MB) uploaded by the machine over the selected period of time.
     - Downloads: Information about the total amount of traffic (in MB) downloaded by the machine over the selected period of time.
   - **検出されたアプリ**<br>
  マシンによってアクセスされたすべての検出されたアプリの一覧が表示されます。
   - **ユーザーの履歴**<br>
    マシンにサインインしたすべてのユーザーの一覧が表示されます。
   - **IP アドレスの履歴**<br>
    マシンに割り当てられたすべての IP アドレスの一覧が表示されます。
 ![マシンの概要](./media/machines-overview.png)
 
他の Cloud Discovery ソースと同様、Win10 エンドポイント ユーザー レポートからデータをエクスポートして、さらに詳しく調査できます。 

> [!NOTE]
> - Defender ATP forwards data to Cloud App Security in chunks of ~4 MB (~4000 endpoint transactions)
> - If the 4 MB limit isn't reached within 1 hour, Defender ATP reports all the transactions performed over the last hour.

## <a name="related-videos"></a>関連ビデオ

[Shadow IT discovery beyond the corporate network with Microsoft Defender ATP and Cloud App Security](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="next-steps"></a>次のステップ 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md) 

[!INCLUDE [Open support ticket](includes/support.md)]  
  
