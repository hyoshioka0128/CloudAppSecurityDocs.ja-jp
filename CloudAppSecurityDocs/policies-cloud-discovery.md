---
title: Cloud Discovery ポリシー - Cloud App Security |Microsoft Docs
description: この記事では、Cloud App Security で Cloud Discovery の多数のポリシーを構成する手順について説明します。
author: ShlomoSagir-MS
ms.author: shsagir
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 570da960-771d-484f-932d-b086f2ec2978
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a8cf4f7564cdb8dd0470bfa6cc2c0c013b95f52e
ms.sourcegitcommit: ea1c0f7638eaf0601ae476fea0d40e01bf8a6f4d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298937"
---
# <a name="cloud-discovery-policies"></a>Cloud Discovery ポリシー

*適用対象:Microsoft Cloud App Security*

この記事では、Cloud Discovery を使用して組織のシャドウ IT への可視性を獲得できます。 Cloud App Security の使用を開始する方法の概要を示します。

Cloud App Security を使用すると、検出、組織の環境で使用されているクラウド アプリを分析できます。 Cloud Discovery ダッシュ ボードは、環境内で実行されているすべてのクラウド アプリを示し、関数や企業の準備に分類されています。 各アプリでは、エンドポイント デバイスにエージェントをインストールすることがなく、関連付けられているユーザー、IP アドレス、コンピューター、トランザクション、およびリスク評価の実施を検出します。

## 新しい高ボリューム、またはワイド アプリの使用を検出します。 <a name= "detect-volume"></a>

ユーザーの数や、組織内のトラフィックの量の点で、高い使用される新しいアプリを検出します。

### <a name="prerequisites"></a>前提条件

継続的な Cloud Discovery の構成に自動ログ アップロードを報告する」の説明に従って[継続的レポートの構成に自動ログ アップロード](configure-automatic-log-upload-for-continuous-reports.md)します。

### <a name="steps"></a>手順

1.  **ポリシー**を新規作成 ページで、**アプリ検出ポリシー**

2.  **ポリシー テンプレート**フィールドで、**新しい高ボリューム アプリ**または**人気のあるアプリが新しい**テンプレートを適用します。

3.  組織の要件を満たすポリシー フィルターをカスタマイズします。

4.  アラートがトリガーされたときに実行されるアクションを構成します。

> [!NOTE]
>  アラートは、過去 90 日以内に検出されなかった新しいアプリごとに 1 回生成されます。

## <a name="detect-new-risky-or-non-compliant-app-use"></a>新しいリスクの高いまたは非準拠アプリの使用を検出します。

セキュリティの基準を満たしていないクラウド アプリで、組織の漏えいの可能性を検出します。

### <a name="prerequisites"></a>前提条件

継続的な Cloud Discovery の構成に自動ログ アップロードを報告する」の説明に従って[継続的レポートの構成に自動ログ アップロード](configure-automatic-log-upload-for-continuous-reports.md)します。

### <a name="steps"></a>手順

1.  **ポリシー**を新規作成 ページで、**アプリ検出ポリシー。**

2.  **ポリシー テンプレート**フィールドで、選択、**新しい危険なアプリ**テンプレートとテンプレートを適用します。

3.  **アプリは、次のすべてに一致する**設定、[リスク スコア](risk-score.md)スライダーとをカスタマイズするコンプライアンス リスク要因は、アラートをトリガーしを満たすために、その他のポリシー フィルターを設定するリスクのレベル組織のセキュリティ要件です。

    1.  省略可能: 意味のある検出を取得するには、アラートをトリガーするトラフィックの量をカスタマイズします。

        1.  チェック、 **、次のすべてが同じ日に発生した場合、ポリシーの一致をトリガー**チェック ボックスをオンします。

        2.  選択**毎日のトラフィック**2000 GB (またはその他) を超えています。

4.  アラートがトリガーされたときに実行するガバナンス アクションを構成します。 **ガバナンス**選択**として承認されていないアプリ タグ。**<br>アプリへのアクセスは、ポリシーの照合時に自動的にブロックされます。

5.  省略可能: 活用[Cloud App Security のネイティブ統合](set-up-cloud-discovery.md)アプリへのアクセスをブロックする Web ゲートウェイをセキュリティで保護されたとします。

## <a name="detect-use-of-unsanctioned-business-apps"></a>承認されていないビジネス アプリの使用を検出します。

従業員がビジネス向けの承認済みアプリの代わりとして承認されていないアプリを使用する継続を検出できます。

### <a name="prerequisites"></a>前提条件

-   継続的な Cloud Discovery の構成に自動ログ アップロードを報告する」の説明に従って[継続的レポートの構成に自動ログ アップロード](configure-automatic-log-upload-for-continuous-reports.md)します。

### <a name="steps"></a>手順

1.  ビジネス向けのアプリで、クラウド アプリ カタログを検索しでマークを付けて、[カスタム アプリ タグ](discovered-app-queries.md#creating-and-managing-custom-app-tags)します。

2.  次の手順では、[新しい高ボリューム、またはワイド アプリの使用状況を検出](#detect-volume)します。

3.  追加、**アプリ タグ**のフィルター処理し、ビジネス向けのアプリ用に作成したアプリ タグを選択します。

4.  アラートがトリガーされたときに実行するガバナンス アクションを構成します。 ガバナンスの **として承認されていないアプリ タグ**します。<br>アプリへのアクセスは、ポリシーの照合時に自動的にブロックされます。

5.  省略可能: 活用[Cloud App Security のネイティブ統合](set-up-cloud-discovery.md)アプリへのアクセスをブロックする Web ゲートウェイをセキュリティで保護されたとします。

## <a name="detect-unusual-usage-patterns-on-your-network"></a>ネットワーク上の異常な使用パターンを検出します。

ユーザーまたは組織のネットワークの内部 IP アドレスから送られた、クラウド アプリで異常なトラフィックの使用パターン (アップロードまたはダウンロード) を検出します。

### <a name="prerequisites"></a>前提条件

継続的な Cloud Discovery の構成に自動ログ アップロードを報告する」の説明に従って[継続的レポートの構成に自動ログ アップロード](configure-automatic-log-upload-for-continuous-reports.md)します。

### <a name="steps"></a>手順

1.  **ポリシー**を新規作成 ページで、 **Cloud Discovery 異常検出ポリシー**します。

2.  **ポリシー テンプレート**フィールドで、**検出されたユーザーの異常な動作**または**検出された IP アドレスの異常な動作**します。

3.  組織の要件を満たすフィルターをカスタマイズします。

4. 使用して、危険なアプリに関連する異常がある場合にのみ警告を表示する場合、**リスク スコア**をフィルター処理し、危険な考慮がアプリの範囲を設定します。

4.  スライダーを使用して**異常検出秘密度を選択します。** します。

> [!NOTE]
>  継続的なログのアップロードが確立された後、異常検出エンジンは (学習期間) ベースラインまで数日かかる、組織での想定される動作が確立されました。 基準が確立されると、ユーザーによるクラウド アプリ間で予想されるトラフィックの動作や IP アドレスからの不一致に基づくアラートの受信を開始します。

## <a name="detect-data-exfiltration-to-unsanctioned-storage-apps"></a>承認されていないストレージ アプリにデータの流出を検出します。

承認されていないクラウド ストレージ アプリへのユーザーによる潜在的なデータの持ち出しを検出します。

### <a name="prerequisites"></a>前提条件

継続的な Cloud Discovery の構成に自動ログ アップロードを報告する」の説明に従って[継続的レポートの構成に自動ログ アップロード](configure-automatic-log-upload-for-continuous-reports.md)します。

### <a name="steps"></a>手順

1.  **ポリシー**  ページで、組み込みのポリシーを編集**承認されていないアプリにデータの持ち出し**します。

2.  フィルター選択**アプリ カテゴリ**equals**クラウドの記憶域**します。

3.  チェック ボックスをオン**ポリシーの重要度で一致するイベントごとのアラートの作成**です。

4.  アラートがトリガーされたときに実行されるアクションを構成します。

## <a name="detect-risky-oauth-apps"></a>危険な OAuth アプリを検出します。

可視性を取得し、制御[OAuth アプリ](investigate-risky-oauth.md)G Suite、Office 365、Salesforce などのアプリ内にインストールされています。 高いアクセス許可を要求し、まれなコミュニティを使用する OAuth アプリは危険と見なされる可能性があります。

### <a name="prerequisites"></a>前提条件

G Suite、Office 365、または Salesforce アプリを使用して接続する必要があります[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。

### <a name="steps"></a>手順

1.  **ポリシー**を新規作成 ページで、 **OAuth アプリ ポリシー**します。

2.  フィルター選択**アプリ**し、アプリ、ポリシーに対応する必要があります、G Suite、Office 365、または Salesforce に設定します。

3.  選択**アクセス許可レベル**equals をフィルター処理**高**(G Suite と O365 の使用可能)。

4.  フィルターを追加**コミュニティの利用状況**equals **Rare**します。

4.  アラートがトリガーされたときに実行されるアクションを構成します。 たとえば、Office 365、チェック**アプリの取り消し**OAuth アプリがポリシーによって検出されます。

> [!NOTE]
>  G Suite、Salesforce、Office 365、アプリ ストアのサポートされています。

## <a name="next-steps"></a>次の手順 

[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  
