---
title: Cloud Discovery ポリシー-Cloud App Security |Microsoft Docs
description: この記事では、Cloud App Security で多数の Cloud Discovery ポリシーを構成する手順について説明します。
author: shsagir
ms.author: shsagir
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 58208567133bf9c8257e456a415c60ab3dacee0b
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719198"
---
# <a name="cloud-discovery-policies"></a>Cloud Discovery ポリシー

*適用対象: Microsoft Cloud App Security*

この記事では、Cloud Discovery を使用して組織全体の可視性を向上させるために Cloud App Security の使用を開始する方法の概要について説明します。

Cloud App Security を使用すると、組織の環境で使用されているクラウドアプリを検出して分析することができます。 Cloud Discovery ダッシュボードには、環境内で実行されているすべてのクラウドアプリが表示され、機能別およびエンタープライズ対応に分類されます。 アプリごとに、エンドポイントデバイスにエージェントをインストールしなくても、関連付けられているユーザー、IP アドレス、コンピューター、トランザクションを検出し、リスク評価を実行します。

## 新しい大量または大規模なアプリの使用を検出する<a name= "detect-volume"></a>

ユーザー数または組織内のトラフィック量に関して、使用率が高い新しいアプリを検出します。

### <a name="prerequisites"></a>必要条件

「[継続的なレポートの自動ログアップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)」の説明に従って、継続的 Cloud Discovery レポートの自動ログアップロードを構成します。

### <a name="steps"></a>手順

1. **[ポリシー]** ページで、新しい**アプリ検出ポリシー**を作成します。

2. **[ポリシーテンプレート]** フィールドで、 **[新しい高ボリュームアプリ]** または **[新しい人気]** のあるアプリ を選択し、テンプレートを適用します。

3. 組織の要件を満たすようにポリシーフィルターをカスタマイズします。

4. アラートがトリガーされたときに実行するアクションを構成します。

> [!NOTE]
> 過去90日以内に検出されなかった新しいアプリごとにアラートが生成されます。

## <a name="detect-new-risky-or-non-compliant-app-use"></a>新しい危険または非準拠のアプリの使用を検出する

セキュリティ標準を満たしていないクラウドアプリで組織が公開される可能性を検出します。

### <a name="prerequisites"></a>必要条件

「[継続的なレポートの自動ログアップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)」の説明に従って、継続的 Cloud Discovery レポートの自動ログアップロードを構成します。

### <a name="steps"></a>手順

1. **[ポリシー]** ページで、新しい**アプリ検出ポリシー**を作成します。

2. **[ポリシーテンプレート]** フィールドで、**新しい危険なアプリ**テンプレートを選択し、テンプレートを適用します。

3. **[次のすべてに一致するアプリ]** で、[リスクスコア](risk-score.md)スライダーとコンプライアンスリスク要因を設定して、アラートをトリガーするリスクのレベルを選択し、組織のセキュリティ要件を満たすように他のポリシーフィルターを設定します。

    1. 省略可能: より意味のある検出を取得するには、アラートをトリガーするトラフィックの量をカスタマイズします。

    2. **次のすべてが同じ日に発生する場合は、[ポリシーの一致をトリガーする**] チェックボックスをオンにします。

    3. **1 日あたり**2000 GB (またはそれ以外) を超えるトラフィックを選択します。

4. アラートがトリガーされたときに実行されるガバナンスアクションを構成します。 **[ガバナンス]** で、承認さ **[れていないアプリにタグ]** を付ける を選択します。<br />ポリシーが一致すると、アプリへのアクセスが自動的にブロックされます。

5. 省略可能: セキュリティで保護された Web ゲートウェイを使用して[Cloud App Security ネイティブ統合](set-up-cloud-discovery.md)を利用し、アプリのアクセスをブロックします。

## <a name="detect-use-of-unsanctioned-business-apps"></a>未承認のビジネスアプリの使用を検出する

承認されたビジネス対応アプリの代わりとして、承認されていないアプリを従業員が引き続き使用するタイミングを検出できます。

### <a name="prerequisites"></a>必要条件

- 「[継続的なレポートの自動ログアップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)」の説明に従って、継続的 Cloud Discovery レポートの自動ログアップロードを構成します。

### <a name="steps"></a>手順

1. クラウドアプリカタログで、ビジネス対応アプリを検索し、[カスタムアプリタグ](discovered-app-queries.md#creating-and-managing-custom-app-tags)でマークします。

2. 「[新しい大量または大規模なアプリの使用状況を検出](#detect-volume)する」の手順に従います。

3. **アプリタグ**フィルターを追加し、ビジネス対応アプリ用に作成したアプリタグを選択します。

4. アラートがトリガーされたときに実行されるガバナンスアクションを構成します。 [ガバナンス] で、[承認されていない**アプリにタグ**を付ける] を選択します。<br />ポリシーが一致すると、アプリへのアクセスが自動的にブロックされます。

5. 省略可能: セキュリティで保護された Web ゲートウェイを使用して[Cloud App Security ネイティブ統合](set-up-cloud-discovery.md)を利用し、アプリのアクセスをブロックします。

## <a name="detect-unusual-usage-patterns-on-your-network"></a>ネットワーク上の通常とは異なる使用パターンを検出する

組織のネットワーク内のユーザーまたは IP アドレスから発生する、クラウドアプリでの異常なトラフィックの使用パターン (アップロード/ダウンロード) を検出します。

### <a name="prerequisites"></a>必要条件

「[継続的なレポートの自動ログアップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)」の説明に従って、継続的 Cloud Discovery レポートの自動ログアップロードを構成します。

### <a name="steps"></a>手順

1. **[ポリシー]** ページで、新しい**Cloud Discovery 異常検出ポリシー**を作成します。

2. **[ポリシーテンプレート]** フィールドで、検出された **[ユーザーの異常な動作]** または 検出された **[IP アドレスの異常な動作]** を選択します。

3. 組織の要件に合わせてフィルターをカスタマイズします。

4. 危険なアプリが関係している場合にのみ警告を表示するには、**リスクスコア**フィルターを使用し、アプリが危険と見なされる範囲を設定します。

5. スライダーを使用して、**異常検出の感度を選択**します。

> [!NOTE]
> 継続的なログアップロードを確立した後、異常検出エンジンは、組織内の想定される動作に対してベースライン (学習期間) が確立されるまでに数日かかります。 ベースラインが確立されると、ユーザーまたは IP アドレスから実行されたクラウドアプリ全体における予想されるトラフィックの動作とは異なることに基づいて、アラートの受信を開始します。

## <a name="detect-data-exfiltration-to-unsanctioned-storage-apps"></a>承認されるストレージアプリのデータを検出する

ユーザーが承認されていないクラウドストレージアプリに対して潜在的なデータを検出します。

### <a name="prerequisites"></a>必要条件

「[継続的なレポートの自動ログアップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)」の説明に従って、継続的 Cloud Discovery レポートの自動ログアップロードを構成します。

### <a name="steps"></a>手順

1. **[ポリシー]** ページで、組み込みポリシーのデータを編集して、承認されていない**アプリを**作成します。

2. [アプリのフィルター **] カテゴリ**が **[クラウドストレージ]** と同じであることを選択します。

3. **ポリシーの重大度が一致するイベントごとにアラートを作成**するには、チェックボックスをオンにします。

4. アラートがトリガーされたときに実行するアクションを構成します。

## <a name="detect-risky-oauth-apps"></a>危険な OAuth アプリの検出

G Suite、Office 365、Salesforce などのアプリ内にインストールされている[OAuth アプリ](investigate-risky-oauth.md)の可視性と制御を実現します。 高いアクセス許可を要求し、まれにコミュニティを使用している OAuth アプリは危険であると見なされる場合があります。

### <a name="prerequisites"></a>必要条件

[アプリコネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)を使用して、G Suite、Office 365、または Salesforce アプリを接続している必要があります。

### <a name="steps"></a>手順

1. **[ポリシー]** ページで、新しい**OAuth アプリポリシー**を作成します。

2. フィルター**アプリ**を選択し、ポリシーでカバーするアプリ (G Suite、Office 365、または Salesforce) を設定します。

3. **[アクセス許可レベル]** フィルター が **[高]** (G Suite および O365 で使用可能) を選択します。

4. フィルターコミュニティの**使用**頻度が**低い**ことを追加します。

5. アラートがトリガーされたときに実行するアクションを構成します。 たとえば、Office 365 の場合は、ポリシーによって検出された OAuth アプリの**失効アプリ**を確認します。

> [!NOTE]
> G Suite、Office 365、Salesforce アプリストアでサポートされています。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
