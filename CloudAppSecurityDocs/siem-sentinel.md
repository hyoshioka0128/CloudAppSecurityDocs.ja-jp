---
title: Azure Sentinel と Cloud App Security の統合
description: この記事では、汎用 SIEM と Cloud App Security の統合に関する情報を提供します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 10/28/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c64952b7d760dfc124f9e64b2bd75d4520b36274
ms.sourcegitcommit: 2c2a14a58492990be5bbac88ff9beb071d556c80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198796"
---
# <a name="azure-sentinel-integration-preview"></a>Azure Sentinel 統合 (プレビュー)

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security を Azure Sentinel (スケーラブルでクラウドネイティブの SIEM と非常) と統合することにより、アラートと検出データを一元的に監視できます。 Azure Sentinel との統合により、通常のセキュリティワークフローを維持しながら、セキュリティ手順を自動化し、クラウドベースのイベントとオンプレミスのイベントを相互に関連付けることができ、クラウドアプリケーションをより効果的に保護できます。

Azure Sentinel を使用する利点は次のとおりです。

* Log Analytics によって提供されるデータ保有期間が長くなります。
* すぐに使える視覚エフェクト。
* Microsoft Power BI や Azure Sentinel ブックなどのツールを使用して、組織のニーズに合わせて独自の探索データの視覚化を作成します。

追加の統合ソリューションには次のものがあります。

* **汎用 SIEMs** -Cloud App Security と汎用 SIEM サーバーを統合します。 ジェネリック SIEM との統合の詳細については、「 [GENERIC SIEM integration](siem.md)」を参照してください。
* **Microsoft security GRAPH API** -複数のセキュリティプロバイダーに接続するための単一のプログラムインターフェイスを提供する仲介サービス (またはブローカー) です。 詳細については、「 [Microsoft Graph セキュリティ API を使用したセキュリティソリューションの統合](https://docs.microsoft.com/graph/security-integration#list-of-connectors-from-microsoft)」を参照してください。

## <a name="how-to-integrate"></a>統合方法

SIEM との統合は、次の2つの手順で行われます。

1. Cloud App Security に設定します。
1. Azure Sentinel で設定します。

### <a name="prerequisites"></a>必要条件

Azure Sentinel と統合するには:

* 有効な Azure Sentinel ライセンスが必要です
* テナントのグローバル管理者またはセキュリティ管理者である必要があります。

### <a name="integrating-with-azure-sentinel"></a>Azure Sentinel との統合

1. Cloud App Security ポータルの**設定**歯車で、 **[セキュリティ拡張機能]** をクリックします。

1. **[SIEM エージェント]** タブで、[追加 ( **+** )] をクリックし、 **[Azure Sentinel]** を選択します。

    ![SIEM 統合の追加メニューを示すスクリーンショット](media/siem0.png)

1. ウィザードで、Azure Sentinel に転送するデータの種類を選択します。 統合を構成するには、次の手順を実行します。
    1. **アラート**: Azure Sentinel が有効になると、アラートは自動的に有効になります。 <!--Use the **Apply to** drop-down to filter which alerts are sent to Azure Sentinel.-->
    1. **検出ログ**: スライダーを使用して有効または無効にします。既定ではすべて選択されています。次に、 **[適用先]** ドロップダウンを使用して、Azure Sentinel に送信する探索ログをフィルター処理します。

    ![Azure Sentinel 統合の構成の開始ページを示すスクリーンショット](media/siem-sentinel-configuration.png)

1. **[次へ]** をクリックし、Azure Sentinel に進み、統合を完了します。 Azure Sentinel の構成の詳細については、「 [https://docs.microsoft.com/azure/sentinel/connect-cloud-app-security](https://docs.microsoft.com/azure/sentinel/connect-cloud-app-security)」を参照してください。

    ![Azure Sentinel 統合の構成の完了ページを示すスクリーンショット](media/siem-sentinel-configuration-complete.png)

> [!NOTE]
> 検出ログは、Cloud app Security ポータルでの構成後、15分以内に Azure Sentinel への転送を開始します。

## <a name="alerts-and-discovery-logs-in-azure-sentinel"></a>Azure Sentinel のアラートと検出ログ

統合が完了すると、Azure Sentinel で Cloud App Security アラートと検出ログを表示できます。

Azure Sentinel の **[ログ]** の下にある **[Security Insights]** で、次のように Cloud App Security データ型のログを確認できます。

| ［データの種類］ | Table |
| --- | --- |
| 検出ログ | McasShadowItReporting |
| アラート | SecurityAlert |

次の表では、 **McasShadowItReporting**スキーマの各フィールドについて説明します。

| フィールド | 種類 | [説明] | 例 |
| --- | --- | --- | --- |
| TenantId | 文字列型 | ワークスペース ID | b459b4u5-912x-46d5-9cb1-p43069212nb4 |
| SourceSystem | 文字列型 | ソースシステム-静的な値 | Azure |
| TimeGenerated [UTC] | DateTime | 探索データの日付 | 2019-07-23T11:00: 35.858 Z |
| StreamName | 文字列型 | 特定のストリームの名前 | マーケティング部門 |
| TotalEvents | 整数型 | セッションあたりのイベントの合計数 | 122 |
| BlockedEvents | 整数型 | ブロックされたイベントの数 | 0 |
| UploadedBytes | 整数型 | アップロードされたデータの量 | 1514874 |
| TotalBytes | 整数型 | データの合計量 | 4067785 |
| ダウンロードバイト数 | 整数型 | ダウンロードされたデータの量 | 2552911 |
| IpAddress | 文字列型 | 送信元 IP アドレス | 127.0.0.0 |
| UserName | 文字列型 | [ユーザー名] | `Raegan@contoso.com` |
| EnrichedUserName | 文字列型 | Azure AD ユーザー名を使用してユーザー名を拡充する | `Raegan@contoso.com` |
| AppName | 文字列型 | クラウドアプリの名前 | Microsoft OneDrive for Business |
| AppId | 整数型 | クラウドアプリ識別子 | 15600 |
| AppCategory | 文字列型 | クラウドアプリのカテゴリ | クラウドの記憶域 |
| AppTags | 文字列配列 | アプリに対して定義されている組み込みタグとカスタムタグ | [承認済みの "] |
| AppScore | 整数型 | アプリケーションのリスクスコアがスケール0-10、10は危険度が低いアプリのスコアである | 10 |
| 種類 | 文字列型 | ログの種類-静的な値 | McasShadowItReporting |

## <a name="use-power-bi-with-cloud-app-security-data-in-azure-sentinel"></a>Azure Sentinel で Cloud App Security データと共に Power BI を使用する

統合が完了したら、他のツールで Azure Sentinel に格納されている Cloud App Security データを使用することもできます。

このセクションでは、Microsoft Power BI (Power BI) を使用して、組織のニーズを満たすレポートとダッシュボードを構築するために、データの整形と結合を簡単に行う方法について説明します。

すぐに開始するには、次の手順を実行します。

1. Power BI では、Cloud App Security データに対して Azure Sentinel からクエリをインポートします。 詳細については、「 [Power BI に Azure Monitor ログデータをインポート](https://docs.microsoft.com/azure/azure-monitor/platform/powerbi)する」を参照してください。
1. [Cloud App Security Shadow IT Discovery アプリをインストール](https://aka.ms/MCASShadowITReporting)し、検出ログデータに[接続](#connect-the-cloud-app-security-app)して、組み込みの Shadow IT Discovery ダッシュボードを表示します。

    > [!NOTE]
    > 現時点では、アプリは Microsoft AppSource で公開されていません。 そのため、アプリをインストールするためのアクセス許可について、Power BI 管理者に連絡する必要がある場合があります。

    ![Shadow IT Discovery ダッシュボードを示すスクリーンショット](media/siem-sentinel-configuration-powerbi-dashboard.png)

1. 必要に応じて Power BI Desktop でカスタムダッシュボードを作成し、組織のビジュアル分析やレポートの要件に合わせて調整します。

### <a name="connect-the-cloud-app-security-app"></a>Cloud App Security アプリを接続する

1. Power BI で、 **[アプリ]** をクリックし、 **Shadow IT Discovery**アプリをクリックします。

1. **[新しいアプリの使用を開始]** します ページで、 **[接続]** をクリックします。

    ![[アプリデータの接続] ページを示すスクリーンショット](media/siem-sentinel-powerbi-connect.png)

1. ワークスペース ID ページで、log analytics の 概要 ページに表示される Azure Sentinel ワークスペース ID を入力し、**次へ** をクリックします。

    ![ワークスペース ID の要求を示すスクリーンショット](media/siem-sentinel-powerbi-workspace-id.png)

1. 認証 ページで、認証方法とプライバシーレベルを指定し、**サインイン** をクリックします。

    ![認証ページを示すスクリーンショット](media/siem-sentinel-powerbi-authentication.png)

1. データを接続したら、ワークスペースの **[データセット]** タブにアクセスし、最新の情報に **[更新]** をクリックします。 これにより、レポートが独自のデータで更新されます。

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)
