---
title: 脅威保護ポリシーで Cloud App Security |Microsoft Docs
description: このトピックでは、Cloud App Security で多くの脅威保護ポリシーを構成する手順について説明します。
author: rkarlin
ms.author: rkarlin
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.assetid: 7c8d5bfd-194e-40ba-b0b0-dfae80f45ecb
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4cb65835bf2f03eb6bef2fc5973be3420cdedb3d
ms.sourcegitcommit: 9f671d5dd5e5da023d598425442d8736546ca183
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66837770"
---
# <a name="threat-protection-policies"></a>脅威保護ポリシー

*適用対象:Microsoft Cloud App Security*


Cloud App Security を使用すると、危険度の高い使用とクラウドのセキュリティに関する問題を識別する、異常なユーザーの動作を検出し、承認されたクラウド アプリでの脅威を防ぎます。 ユーザーと管理者のアクティビティを把握し、疑わしい動作または危険と考えられる特定のアクティビティが検出された場合に自動的にアラートを生成するポリシーを定義します。 膨大な Microsoft 脅威インテリジェンスと、承認されたアプリで必要なセキュリティ コントロールを配置し、その制御を維持するためすべていることを確認するセキュリティ調査データから描画します。

## <a name="detect-and-control-user-activity-from-unfamiliar-locations"></a>検出し、未知の場所からユーザーのアクティビティを制御します。

ユーザーのアクセスや、組織内の他のすべてのユーザーが閲覧された決して未知の場所からアクティビティの自動検出します。

### <a name="prerequisites"></a>前提条件

使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)オンボードを使用してまたは[セッション コントロールでの条件付きアクセス アプリ制御](proxy-deployment-aad.md)します。

### <a name="steps"></a>手順

この検出では、自動的に構成されたタイムアウトの-使える新しい場所からのアクセス権があるときにアラートです。 このポリシーを構成するアクションを実行する必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。

## <a name="detect-compromised-account-by-impossible-location-impossible-travel"></a>検出不可能な場所で侵害されたアカウント (あり得ない移動)

2 つの間の移動にかかる時間より短い期間内のユーザーのアクセスや 2 つの異なる場所からアクティビティの自動検出。

### <a name="prerequisites"></a>前提条件

使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)オンボードを使用してまたは[セッション コントロールでの条件付きアクセス アプリ制御](proxy-deployment-aad.md)します。
### <a name="steps"></a>手順

1.  この検出では、自動的に構成された-、-インボックス不可能な場所からのアクセス権があるときにアラートです。 このポリシーを構成するアクションを実行する必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。
2. 省略可能:[異常検出ポリシーをカスタマイズ](anomaly-detection-policy.md#scope-anomaly-detection-policies): 
    - ユーザーとグループの観点から検出スコープをカスタマイズします。

    - 考慮すべきは、サインインの種類を選択します。

    - アラートの秘密度を設定します。

3.  異常検出ポリシーを作成します。

## <a name="detect-suspicious-activity-from-an-on-leave-employee"></a>"Leave"従業員からの疑わしいアクティビティを検出します。

ある欠勤し、組織のリソースをアクティブにしないとユーザーがアクセスして、組織のクラウド リソースのいずれかを検出します。

### <a name="prerequisites"></a>前提条件

- 使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。

- 欠勤上のユーザーに対して Azure Active directory セキュリティ グループを作成し、監視するすべてのユーザーを追加します。

### <a name="steps"></a>手順

1.  [ユーザー グループ](user-groups.md)画面で、**ユーザー グループの作成**とインポート、関連する Azure AD のグループ化します。

2.  **ポリシー**を新規作成 ページで、**アクティビティ ポリシー**します。

3.  フィルターを設定します**ユーザー グループ**equals、未払いのままにしてユーザーの Azure AD で作成したユーザー グループの名前にします。

4.  省略可能: 設定、**ガバナンス**違反が検出されたときに、ファイルに対して実行されるアクション。 使用できるガバナンス アクションは、サービスによって異なります。 選択できる**ユーザーの停止**します。

6.  ファイル ポリシーを作成します。

## <a name="detect-and-notify-when-outdated-browser-os-is-used"></a>検出し、古くなったときに通知する OS ブラウザーの使用

ユーザーは、コンプライアンスまたは組織のセキュリティ リスクにさらす恐れのある古いクライアント バージョン、ブラウザーを使用しているときに検出します。

### <a name="prerequisites"></a>前提条件

使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)オンボードを使用してまたは[セッション コントロールでの条件付きアクセス アプリ制御](proxy-deployment-aad.md)します。

### <a name="steps"></a>手順

1.  **ポリシー**を新規作成 ページで、**アクティビティ ポリシー**します。

2.  フィルターを設定します**ユーザー エージェント タグ**と等しい**古いブラウザー**と**古いオペレーティング システム**します。

3. 設定、**ガバナンス**違反が検出されたときに、ファイルに対して実行されるアクション。 使用できるガバナンス アクションは、サービスによって異なります。 **すべてのアプリ**、**ユーザーに通知**いるため、ユーザーは、アラートに対して操作を実行して、必要なコンポーネントを更新します。

5.  アクティビティ ポリシーを作成します。

## <a name="detect-and-alert-when-admin-activity-is-detected-on-risky-ip-addresses"></a>検出し、危険な IP で管理アクティビティが検出された場合にアラートに対処

実行された管理者のアクティビティや危険な IP アドレスと見なされる IP アドレスを検出して、詳しい調査のため、システム管理者に通知または管理者のアカウントでガバナンス アクションを設定します。

### <a name="prerequisites"></a>前提条件

- 使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。
 
- 設定の歯車アイコンから次のように選択します。 **IP アドレス範囲** をクリックし、+、内部サブネットとそのエグレス パブリック IP アドレスの IP アドレス範囲を追加します。 設定、**カテゴリ**に**内部**します。

### <a name="steps"></a>手順

1.  **ポリシー**を新規作成 ページで、**アクティビティ ポリシー**します。

2.  設定**に基づいて**に**1 つのアクティビティ**します。

3.  フィルターを設定します**IP アドレス**に**カテゴリ**equals**危険**

4.  フィルターを設定します**管理アクティビティ**に**は True。**

5.  設定、**ガバナンス**違反が検出されたときに、ファイルに対して実行されるアクション。 使用できるガバナンス アクションは、サービスによって異なります。 **すべてのアプリ**を選択します**ユーザーに通知**いるため、ユーザーは、アラートに対して操作を実行して、必要なコンポーネントを更新 **、ユーザーのマネージャーを CC**します。

7.  アクティビティ ポリシーを作成します。

## <a name="detect-activities-by-service-account-from-external-ip-addresses"></a>外部の IP アドレスからのサービス アカウントでアクティビティを検出します。

非内部の IP から送信されたサービス アカウントのアクティビティを検出するアドレス。 疑わしい動作または侵害されたアカウント可能性があります。

### <a name="prerequisites"></a>前提条件

- 使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。
- 設定の歯車アイコンから次のように選択します。 **IP アドレス範囲** をクリックし、+、内部サブネットとそのエグレス パブリック IP アドレスの IP アドレス範囲を追加します。 設定、**カテゴリ**に**内部**します。

- たとえば、環境内でのサービス アカウントの名前付け規則を標準化、"svc"で開始するすべてのアカウント名を設定します。

### <a name="steps"></a>手順

1.  **ポリシー**を新規作成 ページで、**アクティビティ ポリシー**します。

2.  フィルターを設定します**ユーザー**に**名前**し**で始まる**svc など、名前付け規則を入力します。

3.  フィルターを設定します**IP アドレス**に**カテゴリ**と等しくない**他**と**企業**します。

4.  設定、**ガバナンス**違反が検出されたときに、ファイルに対して実行されるアクション。 使用できるガバナンス アクションは、サービスによって異なります。

5.  ポリシーを作成します。

## <a name="detect-mass-download-data-exfiltration"></a>大量ダウンロード (データの持ち出し) の検出します。

特定のユーザーにアクセスするか、短時間で多数のファイルのダウンロードを検出します。

### <a name="prerequisites"></a>前提条件

使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)オンボードを使用してまたは[セッション コントロールでの条件付きアクセス アプリ制御](proxy-deployment-aad.md)します。

### <a name="steps"></a>手順

1.  **ポリシー**を新規作成 ページで、**アクティビティ ポリシー**します。

2.  フィルターを設定します**IP アドレス**に**タグ**と等しくない**Microsoft Azure**します。 これにより、マシン ベースの非対話型のアクティビティは除外します。

3.  フィルターを設定します**アクティビティの種類**と等しいし、関連するダウンロードのすべてのアクティビティを選択します。

4. 設定、**ガバナンス**違反が検出されたときに、ファイルに対して実行されるアクション。 使用できるガバナンス アクションは、サービスによって異なります。
5.  ポリシーを作成します。

## <a name="detect-potential-ransomware-activity"></a>潜在的なランサムウェアのアクティビティを検出します。

潜在的なランサムウェア アクティビティの自動検出。

### <a name="prerequisites"></a>前提条件

使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。

### <a name="steps"></a>手順

- この検出では、自動的に構成された-、-インボックス潜在的なランサムウェア リスクが検出されたときにアラートです。 このポリシーを構成するアクションを実行する必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。  

- 構成することは、**スコープ**の検出とアラートがトリガーされたときに実行するガバナンス アクションをカスタマイズします。 Cloud App Security がランサムウェアを特定する方法の詳細については、次を参照してください。[ランサムウェアから組織を保護する](use-case-ransomware.md)します。

> [!NOTE]
> これは、Office 365、G Suite、ボックス、および Dropbox に適用されます。

## <a name="detect-malware-in-the-cloud"></a>クラウドでのマルウェアを検出します。

Microsoft の脅威インテリジェンス エンジンと Cloud App Security の統合を利用することで、クラウド環境でのマルウェアを含むファイルを検出します。

### <a name="prerequisites"></a>前提条件

使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。

### <a name="steps"></a>手順

- この検出では、自動的に構成された-、-インボックス マルウェアを含む可能性のあるファイルがあるときにアラートです。 このポリシーを構成するアクションを実行する必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。  

## <a name="detect-rogue-admin-takeover"></a>悪意のある管理者の引き継ぎを検出します。

悪意のある開発者の意図を示す可能性がある繰り返される管理アクティビティを検出します。

### <a name="prerequisites"></a>前提条件

使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。

### <a name="steps"></a>手順

1.  **ポリシー**を新規作成 ページで、**アクティビティ ポリシー**します。

2.  設定**に基づいて**に**反復アクティビティ**をカスタマイズして、**最小反復アクティビティ**設定と、**期間**に準拠する、組織のポリシー.

3.  フィルターを設定します**ユーザー**に**グループから**equals および関連するすべての管理者グループとして選択**アクターのみ**します。

4.  フィルターを設定します**アクティビティの種類**パスワードの更新、変更、およびリセットに関連するすべてのアクティビティと等しい。

5. 設定、**ガバナンス**違反が検出されたときに、ファイルに対して実行されるアクション。 使用できるガバナンス アクションは、サービスによって異なります。
6.  ポリシーを作成します。

## <a name="detect-suspicious-inbox-manipulation-rules"></a>不審な受信トレイの操作規則を検出します。

不審な受信トレイの規則は、ユーザーの受信トレイに設定された、ユーザー アカウントが侵害されたことと、メールボックスがスパムと、組織内のマルウェアの配布に使用されている可能性があります。

### <a name="prerequisites"></a>前提条件

- Microsoft Exchange の電子メールに使用します。

### <a name="steps"></a>手順

- この検出では、自動的に構成された-、-インボックス不審な受信トレイの規則セットがあるときにアラートです。 このポリシーを構成するアクションを実行する必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。  


## <a name="detect-leaked-credentials"></a>漏洩した資格情報を検出します。
  
サイバー犯罪者は、正当なユーザーの有効なパスワードをセキュリティ侵害と多くの場合、これらの資格情報を共有します。 これは通常、投稿することで公開されている、濃い web サイトや貼り付けサイトや取引先または販売、資格情報を闇市によって行われます。

Cloud App Security では、組織内で使用されているこのような資格情報と一致する Microsoft の脅威インテリジェンスで使用します。

### <a name="prerequisites"></a>前提条件

使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。

### <a name="steps"></a>手順

この検出では、自動的に構成された-、-インボックス可能な資格情報のリークが検出されたときにアラートです。 このポリシーを構成するアクションを実行する必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。  


## <a name="detect-anomalous-file-downloads"></a>異常なファイルのダウンロードを検出します。

ユーザーが学習したベースラインを基準とした、単一セッションで複数のファイル ダウンロード アクティビティを実行するときを検出します。 これは、侵害の試行を示している可能性があります。

### <a name="prerequisites"></a>前提条件

使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)オンボードを使用してまたは[セッション コントロールでの条件付きアクセス アプリ制御](proxy-deployment-aad.md)します。

### <a name="steps"></a>手順

- この検出では、自動的に構成された-、-インボックス、異常なダウンロードが行われるときにアラートです。 このポリシーを構成するアクションを実行する必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。  
- 検出のスコープを構成し、アラートがトリガーされたときに実行されるアクションをカスタマイズすることができます。

## <a name="detect-anomalous-file-shares-by-a-user"></a>ユーザーが異常なファイル共有を検出します。

ユーザー アクティビティを実行複数ファイルの共有、学習したベースラインに関して、単一セッションでことを示す侵害の試行を検出します。

### <a name="prerequisites"></a>前提条件
使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)オンボードを使用してまたは[セッション コントロールでの条件付きアクセス アプリ制御](proxy-deployment-aad.md)します。
### <a name="steps"></a>手順

- この検出は、自動的に構成された-、-インボックス ユーザーは、複数のファイル共有を実行するときに警告するためです。 このポリシーを構成するアクションを実行する必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。  
- 検出のスコープを構成し、アラートがトリガーされたときに実行されるアクションをカスタマイズすることができます。

## <a name="detect-anomalous-activities-from-infrequent-country"></a>頻度の低い国からの異常なアクティビティを検出します。

最近がないか、ユーザーまたは組織内のすべてのユーザーがアクセスしたことができる場所からアクティビティを検出します。

### <a name="prerequisites"></a>前提条件

使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)オンボードを使用してまたは[セッション コントロールでの条件付きアクセス アプリ制御](proxy-deployment-aad.md)します。

### <a name="steps"></a>手順

- この検出では、自動的に構成された-、-インボックス、頻度の低い国から異常なアクティビティが発生したときにアラートです。 このポリシーを構成するアクションを実行する必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。  
- 検出のスコープを構成し、アラートがトリガーされたときに実行されるアクションをカスタマイズすることができます。

> [!NOTE]
> 異常な場所を検出するには、7 日間の初期学習期間が必要です。 Cloud App Security では、学習期間中に新しい場所の警告は生成されません。

## <a name="detect-activity-performed-by-a-terminated-user"></a>終了させられたユーザーによって実行されたアクティビティを検出します。

組織の従業員は、不要になったユーザーが承認されたアプリでアクティビティを実行するときに検出します。 まだ会社のリソースへのアクセスを持つ解雇された従業員による悪意のあるアクティビティがある可能性があります。

### <a name="prerequisites"></a>前提条件

使用して接続された少なくとも 1 つのアプリが必要[アプリ コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。

### <a name="steps"></a>手順

- この検出では、自動的に構成された-、-インボックス解雇された従業員によるアクティビティが実行されるときにアラートです。 このポリシーを構成するアクションを実行する必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。  
- 検出のスコープを構成し、アラートがトリガーされたときに実行されるアクションをカスタマイズすることができます。


## <a name="next-steps"></a>次の手順 

[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  
