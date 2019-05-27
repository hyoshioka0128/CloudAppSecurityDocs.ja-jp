---
title: Cloud App Security と Microsoft Defender ATP を統合します。
description: この記事では、シャドウ IT やリスク管理の強化された可視性の Cloud App Security と Microsoft Defender Advanced Threat Protection を統合する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/14/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: b35ca44c-da8e-49ec-89d1-c076d123c14f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b49ab77b33548d6fd188eadde97294ceb6c62ca5
ms.sourcegitcommit: 235b7d5f1f49075c199b154abc38e51326c0493e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66173518"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Microsoft Cloud App Security と Microsoft Defender Advanced Threat Protection の統合

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security では、ネイティブで Microsoft Defender Advanced Threat Protection (ATP) を統合します。 統合により、Cloud Discovery のロールアウトが簡単になり、Cloud Discovery の機能が企業ネットワークの範囲を超えて拡張され、マシンベースの調査が可能になりします。 [Microsoft Defender Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)はインテリジェントな保護、検出、調査、および応答のセキュリティ プラットフォームです。 Microsoft Defender ATP で、エンドポイントをサイバー脅威から保護、高度な攻撃やデータ侵害を検出、セキュリティ インシデント、自動化、およびセキュリティ体制を強化します。

Microsoft Cloud App Security では、クラウド アプリおよび Windows 10 の IT で管理されたコンピューターからアクセスされているサービスに関する Microsoft Defender ATP によって収集されたトラフィックの情報を使用します。 統合により、ローミングおよびリモート アクセスの間にパブリック Wi-Fi を使用して、企業ネットワーク内のマシンで Cloud Discovery を実行できます。 また、マシンベースの調査も可能になります。

リスクの高いユーザーが見つかったら、そのユーザーがアクセスしたすべてのマシンを調べて、潜在的なリスクを検出できます。 リスクの高いマシンが見つかったら、そのマシンを使用したすべてのユーザーを調べて、潜在的なリスクを検出できます。 Cloud App Security にルーティングされたエンドポイントからのログでは、トラフィック アクティビティに関するユーザー情報が提供されます。 Microsoft Defender ATP ネットワーク アクティビティは、デバイス コンテキストを提供します。 デバイス コンテキストとユーザー名を組み合わせると、ネットワーク全体でどのユーザーがどのマシンからどのアクティビティを実行したかが詳細にわかります。

Microsoft Cloud App Security では、Microsoft Defender ATP とのネイティブ統合を使用して、管理対象 Windows デバイスからクラウド アプリとサービスのトラフィックに関するデータをタップします。 統合では、標準以外の追加の展開と作業は必要ありません。 エンドポイントからトラフィックをルーティングまたはミラーリングする必要も、複雑な統合の手順を行う必要もありません。

> [!NOTE]
> Microsoft Defender ATP を体験したいですか。 [無料試用版にサインアップしてください](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)。
>


## <a name="prerequisites"></a>前提条件

- Microsoft Cloud App Security ライセンス
- Microsoft Defender ATP のライセンス
- バージョン 1809 以降を実行している Windows 10 マシン
- **[プレビュー機能]** をオンに切り替え、Cloud App Security でこの機能を有効にする

## <a name="how-it-works"></a>しくみ

Cloud App Security は自動的に、[ユーザーがアップロードしたログ](create-snapshot-cloud-discovery-reports.md)を使用するか、または[自動ログ アップロードを構成する](discovery-docker.md)ことにより、エンドポイントからログを収集します。 ネイティブ統合では、Microsoft Defender ATP エージェントは、Windows で実行時にで作成されます。 ログの活用でき、ネットワーク トランザクションを監視します。 この情報を、ネットワーク上の Windows マシンでのシャドウ IT の検出に使用できます。

その他のプラットフォーム間で Cloud Discovery を実行することを有効にするのには、Cloud App Security を使用する最適な[ログ コレクター](discovery-docker.md)、と共に、Windows 10 コンピューターを監視する Microsoft Defender ATP 統合します。

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Cloud App Security と Microsoft Defender ATP を統合する方法

Microsoft Defender ATP から Cloud App Security との統合を有効にします。

1. Microsoft Defender ATP ポータルのナビゲーション ウィンドウで、次のように選択します。**の基本設定のセットアップ**します。
2. **[設定]** メニューの **[全般]** の **[高度な機能]** を選択します。
3. **[Microsoft Cloud App Security]** を **[オン]** に切り替えます。
4. **[Save preferences]\(基本設定の保存\)** をクリックします。

>[!NOTE]
> データの統合を有効にしてから Cloud App Security に表示されるまで、最大で 2 時間かかります。
>

   ![WD ATP の設定](./media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Cloud App Security でマシンを調査する

Cloud App Security と Microsoft Defender ATP を統合した後は、Cloud Discovery ダッシュ ボードで検出されたマシン データを調査できます。

1. Cloud App Security ポータルで、 **[Cloud Discovery]** 、 **[Cloud Discovery dashboard]\(Cloud Discovery ダッシュボード\)** の順にクリックします。
2. 上部のナビゲーション バーで、 **[継続的レポート]** の **[Win10 endpoint users]\(Win10 エンドポイント ユーザー\)** を選択します。
  ![WD ATP レポート](./media/win10-dashboard-report.png)
3. 上部では、検出されたマシンの数が統合後に追加されていることがわかります。
4. **[マシン]** タブをクリックします。
5. リストの各マシンにドリルダウンし、タブを使用して、調査データを表示します。 インシデントに関係したマシン、ユーザー、IP アドレス、アプリの間の相関関係を検索します。
   - **概要**
      - トランザクション:選択した期間にマシンで行われたトランザクションの数に関する情報。
      - 合計トラフィック:選択した期間の合計トラフィック量 (単位は MB) に関する情報。
     - アップロード:選択した期間にマシンによってアップロードされた合計トラフィック量 (単位は MB) に関する情報。
     - ダウンロード:選択した期間にマシンによってダウンロードされた合計トラフィック量 (単位は MB) に関する情報。
   - **検出されたアプリ**<br>
  マシンによってアクセスされたすべての検出されたアプリの一覧が表示されます。
   - **ユーザーの履歴**<br>
    マシンにサインインしたすべてのユーザーの一覧が表示されます。
   - **IP アドレスの履歴**<br>
    マシンに割り当てられたすべての IP アドレスの一覧が表示されます。
 ![マシンの概要](./media/machines-overview.png)
 
他の Cloud Discovery ソースと同様、Win10 エンドポイント ユーザー レポートからデータをエクスポートして、さらに詳しく調査できます。 

> [!NOTE]
> - Defender ATP を Cloud App Security に最大 4 MB (1 ~ 4000 のエンドポイントのトランザクション) のチャンク単位でデータを転送します。
> - 4 MB の制限はありません、1 時間以内に達すると、Defender ATP のレポートのすべてのトランザクションは、過去 1 時間実行されます。

## <a name="related-videos"></a>関連ビデオ

[Microsoft Defender ATP と Cloud App Security で企業ネットワーク外のシャドウ IT 検出](https://www.youtube.com/watch?v=f8hbvbY1Hnc)  

## <a name="next-steps"></a>次の手順 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md) 

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
