---
title: Microsoft Defender ATP を Cloud App Security に統合する
description: この記事では、Microsoft Defender Advanced Threat Protection を Cloud App Security に統合して、シャドウ IT およびリスク管理の可視性を向上させる方法について説明します。
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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 90efa85fccd71e488f80db290b09b1636013304b
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720390"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Microsoft Defender Advanced Threat Protection と Microsoft Cloud App Security の統合

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security は、Microsoft Defender Advanced Threat Protection (ATP) とネイティブに統合されます。 統合により、Cloud Discovery のロールアウトが簡単になり、Cloud Discovery の機能が企業ネットワークの範囲を超えて拡張され、マシンベースの調査が可能になりします。 [Microsoft Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)は、インテリジェントな保護、検出、調査、および対応を行うためのセキュリティプラットフォームです。 Microsoft Defender ATP は、サイバー脅威からのエンドポイントを保護し、高度な攻撃とデータ侵害を検出し、セキュリティインシデントを自動化し、セキュリティ体制を強化します。

Microsoft Cloud App Security は、IT が管理する Windows 10 コンピューターからアクセスされるクラウドアプリとサービスについて、Microsoft Defender ATP によって収集されたトラフィック情報を使用します。 統合により、ローミングおよびリモート アクセスの間にパブリック Wi-Fi を使用して、企業ネットワーク内のマシンで Cloud Discovery を実行できます。 また、マシンベースの調査も可能になります。

リスクの高いユーザーが見つかったら、そのユーザーがアクセスしたすべてのマシンを調べて、潜在的なリスクを検出できます。 リスクの高いマシンが見つかったら、そのマシンを使用したすべてのユーザーを調べて、潜在的なリスクを検出できます。 Cloud App Security にルーティングされたエンドポイントからのログでは、トラフィック アクティビティに関するユーザー情報が提供されます。 Microsoft Defender ATP ネットワークアクティビティは、デバイスコンテキストを提供します。 デバイス コンテキストとユーザー名を組み合わせると、ネットワーク全体でどのユーザーがどのマシンからどのアクティビティを実行したかが詳細にわかります。

Microsoft Cloud App Security は、Microsoft Defender ATP とのネイティブ統合を使用して、管理された Windows デバイスからクラウドアプリとサービストラフィックに関するデータをタップします。 統合では、標準以外の追加の展開と作業は必要ありません。 エンドポイントからトラフィックをルーティングまたはミラーリングする必要も、複雑な統合の手順を行う必要もありません。

> [!NOTE]
> Microsoft Defender ATP を体験する場合は、 [無料試用版にサインアップしてください](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)。

## <a name="prerequisites"></a>必要条件

- Microsoft Cloud App Security ライセンス
- Microsoft Defender ATP ライセンス
- Windows 10 バージョン 1709 (OS Build 16299.1085 with KB4493441)、Windows 10 version 1803 (OS Build 17134.704 with KB4493464)、Windows 10 version 1809 (OS Build 17763.379 with KB4489899)、またはそれ以降のバージョンの Windows 10
- **[プレビュー機能]** をオンに切り替え、Cloud App Security でこの機能を有効にする

## <a name="how-it-works"></a>しくみ

Cloud App Security は自動的に、[ユーザーがアップロードしたログ](create-snapshot-cloud-discovery-reports.md)を使用するか、または[自動ログ アップロードを構成する](discovery-docker.md)ことにより、エンドポイントからログを収集します。 ネイティブ統合を使用すると、Windows で実行されるときに Microsoft Defender ATP のエージェントが作成するログを利用し、ネットワークトランザクションを監視できます。 この情報を、ネットワーク上の Windows マシンでのシャドウ IT の検出に使用できます。

他のプラットフォーム間で Cloud Discovery を実行できるようにするには、Windows 10 コンピューターを監視するために、Cloud App Security [log collector](discovery-docker.md)と MICROSOFT Defender ATP 統合の両方を使用することをお勧めします。

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Microsoft Defender ATP を Cloud App Security に統合する方法

Microsoft Defender ATP から Cloud App Security との統合を有効にするには:

1. Microsoft Defender ATP ポータルのナビゲーションウィンドウで、設定 **セットアップ** の順番に選択します。
2. **[設定]** メニューの **[全般]** の **[高度な機能]** を選択します。
3. **[Microsoft Cloud App Security]** を **[オン]** に切り替えます。
4. **[Save preferences]\(基本設定の保存\)** をクリックします。

>[!NOTE]
> データの統合を有効にしてから Cloud App Security に表示されるまで、最大で 2 時間かかります。
>

![WD ATP の設定](media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Cloud App Security でマシンを調査する

Microsoft Defender ATP を Cloud App Security に統合したら、Cloud Discovery ダッシュボードで検出されたマシンデータを調査できます。

1. Cloud App Security ポータルで、 **[Cloud Discovery]** 、 **[Cloud Discovery dashboard]\(Cloud Discovery ダッシュボード\)** の順にクリックします。
2. 上部のナビゲーション バーで、 **[継続的レポート]** の **[Win10 endpoint users]\(Win10 エンドポイント ユーザー\)** を選択します。
  ![WD ATP レポート](media/win10-dashboard-report.png)
3. 上部では、検出されたマシンの数が統合後に追加されていることがわかります。
4. **[マシン]** タブをクリックします。
5. リストの各マシンにドリルダウンし、タブを使用して、調査データを表示します。 インシデントに関係したマシン、ユーザー、IP アドレス、アプリの間の相関関係を検索します。

    - **概要**
        - トランザクション: 選択した期間にコンピューターで発生したトランザクションの数に関する情報。
        - 合計トラフィック数: 選択した期間のトラフィックの総量 (MB 単位) に関する情報。
        - アップロード: 選択した期間にマシンによってアップロードされたトラフィックの総量 (MB 単位) に関する情報。
        - ダウンロード: 選択した期間にコンピューターによってダウンロードされたトラフィックの総量 (MB 単位) に関する情報。
    - **検出されたアプリ**  
  マシンによってアクセスされたすべての検出されたアプリの一覧が表示されます。
    - **ユーザーの履歴**  
    マシンにサインインしたすべてのユーザーの一覧が表示されます。
    - **IP アドレスの履歴**  
    マシンに割り当てられたすべての IP アドレスの一覧が表示されます。
 ![マシンの概要](media/machines-overview.png)

他の Cloud Discovery ソースと同様、Win10 エンドポイント ユーザー レポートからデータをエクスポートして、さらに詳しく調査できます。

> [!NOTE]
>
> - Defender ATP は、最大 4 MB のチャンク単位で Cloud App Security にデータを転送します (約4000エンドポイントトランザクション)
> - 1時間以内に 4 MB の制限に達していない場合、Defender ATP は過去1時間に実行されたすべてのトランザクションを報告します。
> - エンドポイントデバイスがフォワードプロキシの背後にある場合、トラフィックの量は Microsoft Defender ATP に表示されないため、Cloud Discovery レポートには含まれません。 詳細については、「[転送プロキシの背後にあるネットワーク接続の監視](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/MDATP-Monitoring-network-connection-behind-forward-proxy-Public/ba-p/758274)」を参照してください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>関連ビデオ

> [!div class="nextstepaction"]
> [企業ネットワークを超えたシャドウ IT 検出](https://www.youtube.com/watch?v=f8hbvbY1Hnc)

[!INCLUDE [Open support ticket](includes/support.md)]
