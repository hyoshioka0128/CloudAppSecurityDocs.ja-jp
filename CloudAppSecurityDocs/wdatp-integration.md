---
title: Windows Defender Advanced Threat Protection と Cloud App Security を統合する | Microsoft Docs
description: この記事では、Windows Defender ATP と Cloud App Security をシームレスに統合してシャドウ IT とリスク管理の可視性を高める方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3c6546f1f98b3ebbb8f7cff5d9e8ec053e84f102
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53124521"
---
*適用対象: Microsoft Cloud App Security*


# <a name="windows-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Windows Defender Advanced Threat Protection と Microsoft Cloud App Security の統合

Microsoft Cloud App Security は Windows Defender Advanced Threat Protection (ATP) とネイティブに統合して、Cloud Discovery のロールアウトを簡素化し、企業ネットワーク外に Cloud Discovery 機能を拡張し、マシン ベースの調査を可能にします。 

[Windows Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) は、インテリジェントな保護、検出、調査、および応答のためのセキュリティ プラットフォームです。 Windows Defender ATP は、エンドポイントをサイバー脅威から保護し、高度な攻撃とデータ侵害を検出し、セキュリティ インシデントを自動化し、セキュリティ体制を強化します。

Microsoft Cloud App Security では、IT 部門で管理された Windows 10 マシンからアクセスされているクラウド アプリおよびサービスについての、Windows Defender ATP によって収集されたトラフィック情報が利用されます。 これにより、ローミングおよびリモート アクセスの間にパブリック Wi-Fi を使用して、企業ネットワーク内のマシンで Cloud Discovery を実行できます。 また、マシン ベースの調査も可能です。リスクの高いユーザーが見つかったら、そのユーザーがアクセスしたすべてのマシンを調べて、潜在的なリスクを検出できます。リスクの高いマシンが見つかったら、そのマシンを使用したすべてのユーザーを調べて、潜在的なリスクを検出できます。 Cloud App Security にルーティングされたエンドポイントからのログでは、トラフィック アクティビティに関するユーザー情報が提供されます。 Windows Defender ATP ネットワーク アクティビティではデバイス コンテキストが提供され、それとユーザー名を組み合わせると、ネットワーク全体でどのユーザーがどのマシンからどのアクティビティを実行したかが詳細にわかります。 Microsoft Cloud App Security は Windows Defender ATP とのネイティブ統合を使用して、マネージド Windows デバイスからのクラウド アプリおよびサービスのトラフィックに関するデータを利用できます。 このシームレスな統合では、標準以外の追加の展開と作業は必要ありません。 エンドポイントからトラフィックをルーティングまたはミラーリングする必要も、複雑な統合の手順を行う必要もありません。

> [!NOTE]
> Windows Defender ATP を体験したいですか。 [無料試用版にサインアップしてください](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)。
>


## <a name="prerequisites"></a>前提条件

- Microsoft Cloud App Security ライセンス
- Windows Defender ATP ライセンス
- バージョン 1809 以降を実行している Windows 10 マシン


## <a name="how-it-works"></a>しくみ

Cloud App Security は自動的に、[ユーザーがアップロードしたログ](create-snapshot-cloud-discovery-reports.md)を使用するか、または[自動ログ アップロードを構成する](discovery-docker.md)ことにより、エンドポイントからログを収集します。 このネイティブ統合により、ユーザーは、Windows Defender ATP のエージェントが Windows で実行してネットワーク トランザクションを監視するときに作成するログを利用して、ネットワーク上の Windows マシンでシャドウ IT を検出できます。 

他のプラットフォームで Cloud Discovery を実行するには、Cloud App Security の[ログ コレクター](discovery-docker.md)と、Windows Defender ATP との統合の両方を使用して、Windows 10 マシンを監視するのが最善です。


## <a name="how-to-integrate-windows-defender-atp-with-cloud-app-security"></a>Windows Defender ATP と Cloud App Security を統合する方法

Windows Defender ATP から Cloud App Security との統合を有効にするには:

1. Windows Defender ATP ポータルのナビゲーション ウィンドウで、**[Preferences setup]\(基本設定のセットアップ\)** を選択します。
2. **[設定]** メニューの **[全般]** の **[高度な機能]** を選択します。
3. **[Microsoft Cloud App Security]** を **[オン]** に切り替えます。
4. **[Save preferences]\(基本設定の保存\)** をクリックします。

>[!NOTE]
> データの統合を有効にしてから Cloud App Security に表示されるまで、最大で 2 時間かかります。
>

   ![WD ATP の設定](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Cloud App Security でマシンを調査する

Windows Defender ATP と Cloud App Security を統合した後、検出されたマシンのデータを Cloud Discovery ダッシュボードで調査することができます。

1. Cloud App Security ポータルで、**[Cloud Discovery]**、**[Cloud Discovery dashboard]\(Cloud Discovery ダッシュボード\)** の順にクリックします。
2. 上部のナビゲーション バーで、**[継続的レポート]** の **[Win10 endpoint users]\(Win10 エンドポイント ユーザー\)** を選択します。
  ![WD ATP レポート](./media/win10-dashboard-report.png)
4. 統合後に上部に検出されたマシンの数が追加されたことがわかります。
5. **[マシン]** タブをクリックします。
6. リストの各マシンにドリルダウンし、タブを使用して、調査データを表示し、マシンとインシデントに関係するユーザー、IP アドレス、アプリ間の相関関係を検索できます。
   - **概要**
      - トランザクション: 選択した期間にマシンで行われたトランザクションの数に関する情報が提供されます。
      - 合計トラフィック: 選択した期間の合計トラフィック量 (単位は MB) に関する情報が提供されます。
     - アップロード: 選択した期間にマシンによってアップロードされた合計トラフィック量 (単位は MB) に関する情報が提供されます。
     - ダウンロード: 選択した期間にマシンによってダウンロードされた合計トラフィック量 (単位は MB) に関する情報が提供されます。
   - **検出されたアプリ**<br>
  マシンによってアクセスされたすべての検出されたアプリの一覧が表示されます。
   - **ユーザーの履歴**<br>
    マシンにサインインしたすべてのユーザーの一覧が表示されます。
   - **IP アドレスの履歴**<br>
    マシンに割り当てられたすべての IP アドレスの一覧が表示されます。
 ![マシンの概要](./media/machines-overview.png)
 

他の Cloud Discovery ソースと同様、Win10 エンドポイント ユーザー レポートからデータをエクスポートして、さらに詳しく調査できます。 


## <a name="related-videos"></a>関連ビデオ  
[Windows Defender ATP とクラウドによる企業ネットワーク外のシャドウ IT の検出](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
