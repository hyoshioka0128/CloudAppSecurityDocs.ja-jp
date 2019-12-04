---
title: 脅威保護ポリシー-Cloud App Security |Microsoft Docs
description: このトピックでは、Cloud App Security で多くの脅威保護ポリシーを構成する手順について説明します。
author: shsagir
ms.author: shsagir
ms.date: 06/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 405bdd5636bdcdf93dbfc858ecc6578d1a43c402
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720904"
---
# <a name="threat-protection-policies"></a>脅威保護に関するポリシー

*適用対象: Microsoft Cloud App Security*

Cloud App Security を使用すると、リスクの高い使用とクラウドのセキュリティの問題を特定し、異常なユーザー動作を検出して、承認されたクラウドアプリでの脅威を防ぐことができます。 ユーザーと管理者のアクティビティの可視性を取得し、リスクがあると考えられる疑わしい動作または特定のアクティビティが検出されたときに自動的にアラートを作成するポリシーを定義します。 Microsoft の脅威インテリジェンスおよびセキュリティ研究に関する膨大な量のデータから、承認されたアプリに必要なすべてのセキュリティ制御を確実に提供し、管理を維持することができます。

## <a name="detect-and-control-user-activity-from-unfamiliar-locations"></a>不明な場所からのユーザーアクティビティの検出と制御

組織内の他のユーザーによって閲覧されていない不明な場所からのユーザーアクセスまたはアクティビティの自動検出。

### <a name="prerequisites"></a>必要条件

アプリ[コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)またはオンボードを使用して接続されているアプリが、[セッションコントロールで条件付きアクセスアプリコントロール](proxy-deployment-aad.md)を使用している必要があります。

### <a name="steps"></a>手順

この検出は、新しい場所からのアクセスがある場合に自動的に警告するように自動的に構成されます。 このポリシーを構成するために何らかの操作を行う必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。

## <a name="detect-compromised-account-by-impossible-location-impossible-travel"></a>危険な場所によって侵害されたアカウントを検出する (不可能な移動)

2つの場所の間の移動にかかる時間よりも短い、2つの異なる場所からのユーザーアクセスまたはアクティビティの自動検出。

### <a name="prerequisites"></a>必要条件

アプリ[コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)またはオンボードを使用して接続されているアプリが、[セッションコントロールで条件付きアクセスアプリコントロール](proxy-deployment-aad.md)を使用している必要があります。
### <a name="steps"></a>手順

1. この検出は、不可能な場所からのアクセスが発生した場合にアラートを送信するように自動的に構成されます。 このポリシーを構成するために何らかの操作を行う必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。
2. 省略可能:[異常検出ポリシーをカスタマイズ](anomaly-detection-policy.md#scope-anomaly-detection-policies)できます。

    - ユーザーとグループの観点から検出スコープをカスタマイズする

    - 考慮するサインインの種類を選択する

    - アラートの秘密度を設定する

3. 異常検出ポリシーを作成します。

## <a name="detect-suspicious-activity-from-an-on-leave-employee"></a>"休暇中" の従業員からの不審なアクティビティの検出

退職したユーザーが組織のリソースでアクティブにならないと、組織のクラウドリソースのいずれかにアクセスしていることを検出します。

### <a name="prerequisites"></a>必要条件

- [アプリコネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)を使用して、少なくとも1つのアプリが接続されている必要があります。

- Azure Active Directory にセキュリティグループを作成し、そのユーザーに対して、[欠勤] をクリックして、監視するすべてのユーザーを追加します。

### <a name="steps"></a>手順

1. [[ユーザーグループ](user-groups.md)] 画面で、 **[ユーザーグループの作成]** をクリックし、関連する Azure AD グループをインポートします。

2. **[ポリシー]** ページで、新しい**アクティビティポリシー**を作成します。

3. [**ユーザーグループ**のフィルター] は、"Azure AD" で作成したユーザーグループの名前に等しくなります。

4. 省略可能: 違反が検出されたときにファイルに対して実行される**ガバナンス**アクションを設定します。 使用できるガバナンスアクションは、サービスによって異なります。 [ユーザーの**中断**] を選択できます。

5. ファイルポリシーを作成します。

## <a name="detect-and-notify-when-outdated-browser-os-is-used"></a>古いブラウザー OS が使用されたときに検出して通知する

組織に対してコンプライアンスやセキュリティ上のリスクをもたらす可能性がある、期限切れのクライアントバージョンのブラウザーをユーザーが使用していることを検出します。

### <a name="prerequisites"></a>必要条件

アプリ[コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)またはオンボードを使用して接続されているアプリが、[セッションコントロールで条件付きアクセスアプリコントロール](proxy-deployment-aad.md)を使用している必要があります。

### <a name="steps"></a>手順

1. **[ポリシー]** ページで、新しい**アクティビティポリシー**を作成します。

2. **[ユーザーエージェントタグ]** のフィルター を **[古いブラウザー]** と **[古いオペレーティングシステム]** に設定します。

3. 違反が検出されたときにファイルに対して実行される**ガバナンス**アクションを設定します。 使用できるガバナンスアクションは、サービスによって異なります。 **[すべてのアプリ]** で、ユーザーへの **[通知]** を選択して、ユーザーがアラートに対して操作し、必要なコンポーネントを更新できるようにします。

4. アクティビティポリシーを作成します。

## <a name="detect-and-alert-when-admin-activity-is-detected-on-risky-ip-addresses"></a>危険な IP アドレスで管理者アクティビティが検出されたときに検出してアラートを行う

リスクの高い IP アドレスと見なされる、から実行された管理者のアクティビティを検出し、詳細な調査を行うか、管理者のアカウントにガバナンスアクションを設定します。

### <a name="prerequisites"></a>必要条件

- [アプリコネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)を使用して、少なくとも1つのアプリが接続されている必要があります。

- 設定の歯車から **ip アドレスの範囲** を選択し、+ をクリックして、内部サブネットとその送信パブリック ip アドレスの ip アドレスの範囲を追加します。 カテゴリを [**内部** **]** に設定します。

### <a name="steps"></a>手順

1. **[ポリシー]** ページで、新しい**アクティビティポリシー**を作成します。

2. **Act**を**1 つのアクティビティ**に設定します。

3. フィルターの**IP アドレス**をカテゴリとして [**危険** **]** に設定します。

4. **管理アクティビティ**のフィルターを**True**に設定する。

5. 違反が検出されたときにファイルに対して実行される**ガバナンス**アクションを設定します。 使用できるガバナンスアクションは、サービスによって異なります。 **[すべてのアプリ]** の下で **[ユーザー]** への通知 を選択し、ユーザーがアラートに対して操作を実行し、必要なコンポーネントを更新して、**ユーザーのマネージャーを CC**にします。

6. アクティビティポリシーを作成します。

## <a name="detect-activities-by-service-account-from-external-ip-addresses"></a>外部 IP アドレスからサービスアカウントを使ってアクティビティを検出する

内部 IP アドレス以外から発生したサービスアカウントアクティビティを検出します。 これは、疑わしい動作または侵害されたアカウントを示している可能性があります。

### <a name="prerequisites"></a>必要条件

- [アプリコネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)を使用して、少なくとも1つのアプリが接続されている必要があります。
- 設定の歯車から **ip アドレスの範囲** を選択し、+ をクリックして、内部サブネットとその送信パブリック ip アドレスの ip アドレスの範囲を追加します。 カテゴリを [**内部** **]** に設定します。

- 環境内のサービスアカウントの名前付け規則を標準化します。たとえば、すべてのアカウント名を "svc" で始まるように設定します。

### <a name="steps"></a>手順

1. **[ポリシー]** ページで、新しい**アクティビティポリシー**を作成します。

2. フィルター**ユーザー**を **[名前]** に設定し、 **[開始]** をクリックして、名前付け規則 (svc など) を入力します。

3. **[IP アドレス]** をカテゴリにフィルター を **[その他]** および [**会社** **]** と等しくないように設定します。

4. 違反が検出されたときにファイルに対して実行される**ガバナンス**アクションを設定します。 使用できるガバナンスアクションは、サービスによって異なります。

5. ポリシーを作成します。

## <a name="detect-mass-download-data-exfiltration"></a>大量ダウンロードの検出 (データ exfiltration)

特定のユーザーが短時間に大量のファイルにアクセスしたりダウンロードしたりするタイミングを検出します。

### <a name="prerequisites"></a>必要条件

アプリ[コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)またはオンボードを使用して接続されているアプリが、[セッションコントロールで条件付きアクセスアプリコントロール](proxy-deployment-aad.md)を使用している必要があります。

### <a name="steps"></a>手順

1. **[ポリシー]** ページで、新しい**アクティビティポリシー**を作成します。

2. **IP アドレス**のフィルターを **タグ**に一致しない**Microsoft Azure**に設定します。 これにより、非対話型のコンピューターベースのアクティビティは除外されます。

3. [フィルター**アクティビティの種類**] をに設定し、関連するすべてのダウンロードアクティビティを選択します。

4. 違反が検出されたときにファイルに対して実行される**ガバナンス**アクションを設定します。 使用できるガバナンスアクションは、サービスによって異なります。
5. ポリシーを作成します。

## <a name="detect-potential-ransomware-activity"></a>ランサムウェアアクティビティの検出

ランサムウェアアクティビティの可能性を自動検出します。

### <a name="prerequisites"></a>必要条件

[アプリコネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)を使用して、少なくとも1つのアプリが接続されている必要があります。

### <a name="steps"></a>手順

1. この検出は、自動で設定された機能によって自動的に構成され、発生する可能性のあるマルウェアのリスクが検出された場合にアラートを送信します。 このポリシーを構成するために何らかの操作を行う必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。

2. 検出の**範囲**を構成し、アラートがトリガーされたときに実行されるガバナンスアクションをカスタマイズすることができます。 ランサムウェアを識別 Cloud App Security 方法の詳細については、「[ランサムウェアから組織を保護](use-case-ransomware.md)する」を参照してください。

> [!NOTE]
> これは、Office 365、G Suite、Box、Dropbox に適用されます。

## <a name="detect-malware-in-the-cloud"></a>クラウド内のマルウェアを検出する

Microsoft の脅威インテリジェンスエンジンと Cloud App Security の統合を利用して、クラウド環境内のマルウェアを含むファイルを検出します。

### <a name="prerequisites"></a>必要条件

[アプリコネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)を使用して、少なくとも1つのアプリが接続されている必要があります。

### <a name="steps"></a>手順

- この検出は、マルウェアが含まれている可能性があるファイルがある場合に自動的に警告するように自動的に構成されます。 このポリシーを構成するために何らかの操作を行う必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。

## <a name="detect-rogue-admin-takeover"></a>悪意のある管理者の引き継ぎの検出

悪意のある意図を示す可能性がある、繰り返される管理アクティビティを検出します。

### <a name="prerequisites"></a>必要条件

[アプリコネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)を使用して、少なくとも1つのアプリが接続されている必要があります。

### <a name="steps"></a>手順

1. **[ポリシー]** ページで、新しい**アクティビティポリシー**を作成します。

2. **[Act** ] を **[反復活動]** に設定し、**反復活動の最小**数をカスタマイズして、組織のポリシーに準拠する**期間**を設定します。

3. **[ユーザー]** のフィルター を **[グループ]** equals に設定し、関連するすべての管理者グループを **[アクターのみ]** として選択します。

4. フィルターアクティビティの**種類**を、パスワードの更新、変更、およびリセットに関連するすべての活動に設定します。

5. 違反が検出されたときにファイルに対して実行される**ガバナンス**アクションを設定します。 使用できるガバナンスアクションは、サービスによって異なります。
6. ポリシーを作成します。

## <a name="detect-suspicious-inbox-manipulation-rules"></a>疑わしい受信トレイ操作ルールの検出

疑わしい受信トレイの規則がユーザーの受信トレイに設定されている場合は、ユーザーアカウントが侵害されていること、およびメールボックスが組織内のスパムおよびマルウェアの配布に使用されていることを示している可能性があります。

### <a name="prerequisites"></a>必要条件

- 電子メールに Microsoft Exchange を使用します。

### <a name="steps"></a>手順

- この検出は、疑わしい受信トレイの規則が設定されている場合にアラートを送信するように自動的に構成されます。 このポリシーを構成するために何らかの操作を行う必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。

## <a name="detect-leaked-credentials"></a>漏洩した資格情報の検出

サイバー犯罪者が正当なユーザーの有効なパスワードを侵害すると、多くの場合、これらの資格情報が共有されます。 通常、これを行うには、ダーク web または貼り付けサイトに公開するか、ブラック市場で資格情報を売買または販売します。

Cloud App Security は、Microsoft の脅威インテリジェンスを利用して、このような資格情報を組織内で使用されているものと照合します。

### <a name="prerequisites"></a>必要条件

[アプリコネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)を使用して、少なくとも1つのアプリが接続されている必要があります。

### <a name="steps"></a>手順

この検出は、資格情報の漏洩の可能性が検出された場合にアラートを送信するように自動的に構成されます。 このポリシーを構成するために何らかの操作を行う必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。

## <a name="detect-anomalous-file-downloads"></a>異常なファイルダウンロードの検出

学習したベースラインを基準として、ユーザーが1つのセッションで複数のファイルダウンロードアクティビティを実行したことを検出します。 これは、侵害の試行を示している可能性があります。

### <a name="prerequisites"></a>必要条件

アプリ[コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)またはオンボードを使用して接続されているアプリが、[セッションコントロールで条件付きアクセスアプリコントロール](proxy-deployment-aad.md)を使用している必要があります。

### <a name="steps"></a>手順

1. この検出は、異常なダウンロードが発生した場合にアラートを送信するように自動的に構成されます。 このポリシーを構成するために何らかの操作を行う必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。

2. 検出の範囲を構成し、アラートがトリガーされたときに実行されるアクションをカスタマイズすることができます。

## <a name="detect-anomalous-file-shares-by-a-user"></a>ユーザーによる異常なファイル共有の検出

学習したベースラインに関して、ユーザーが1つのセッションで複数のファイル共有アクティビティを実行したことを検出します。これは、侵害の試行を示している可能性があります。

### <a name="prerequisites"></a>必要条件

アプリ[コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)またはオンボードを使用して接続されているアプリが、[セッションコントロールで条件付きアクセスアプリコントロール](proxy-deployment-aad.md)を使用している必要があります。

### <a name="steps"></a>手順

1. この検出は、ユーザーが複数のファイル共有を実行するときにアラートを通知するように自動的に構成されます。 このポリシーを構成するために何らかの操作を行う必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。

2. 検出の範囲を構成し、アラートがトリガーされたときに実行されるアクションをカスタマイズすることができます。

## <a name="detect-anomalous-activities-from-infrequent-country"></a>頻度の低い国からの異常なアクティビティの検出

ユーザーまたは組織内のユーザーによって最近使用されていない、またはユーザーによって閲覧されていない場所からのアクティビティを検出します。

### <a name="prerequisites"></a>必要条件

アプリ[コネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)またはオンボードを使用して接続されているアプリが、[セッションコントロールで条件付きアクセスアプリコントロール](proxy-deployment-aad.md)を使用している必要があります。

### <a name="steps"></a>手順

1. この検出は、頻度の低い国から異常なアクティビティが発生した場合にアラートを送信するように自動的に構成されます。 このポリシーを構成するために何らかの操作を行う必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。

2. 検出の範囲を構成し、アラートがトリガーされたときに実行されるアクションをカスタマイズすることができます。

> [!NOTE]
> 異常な場所を検出するには、7日間の初期学習期間があります。 学習期間中は、Cloud App Security は新しい場所のアラートを生成しません。

## <a name="detect-activity-performed-by-a-terminated-user"></a>終了したユーザーによって実行されたアクティビティを検出する

組織の従業員ではなくなったユーザーが承認されたアプリでアクティビティを実行したことを検出します。 これは、退職した従業員が会社のリソースに引き続きアクセスできることを示している可能性があります。

### <a name="prerequisites"></a>必要条件

[アプリコネクタ](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)を使用して、少なくとも1つのアプリが接続されている必要があります。

### <a name="steps"></a>手順

1. この検出は、終了した従業員によって活動が実行されたときにアラートを通知するように自動的に構成されます。 このポリシーを構成するために何らかの操作を行う必要はありません。 詳細については、[異常検出ポリシー](anomaly-detection-policy.md)に関する記事を参照してください。

2. 検出の範囲を構成し、アラートがトリガーされたときに実行されるアクションをカスタマイズすることができます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
