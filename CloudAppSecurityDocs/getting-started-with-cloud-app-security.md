---
title: Cloud App Security の展開
description: このクイックスタートでは、クラウド アプリを使用、洞察、制御できるように、Cloud App Security を準備して使用を開始するプロセスの概要について説明します。
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 8/28/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 489bdc036d8e2b51303e79509af39d851385aa00
ms.sourcegitcommit: 0552bfd3f75ed24b2b9de668c0c25bf7be5f5526
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70076436"
---
# <a name="quickstart-get-started-with-microsoft-cloud-app-security"></a>クイック スタート:Microsoft Cloud App Security の使用を開始する

*適用対象:Microsoft Cloud App Security*

このクイックスタートでは、Cloud App Security を準備して使用を開始する手順を示します。 Microsoft Cloud App Security は、クラウド アプリケーションの利点の活用に役立つだけでなく、会社のリソース管理にも役立ちます。 これは、クラウドの利用状況の可視性を向上させ、企業データの保護を強化することによって機能します。 この記事では、Microsoft Cloud App Security をセットアップして使用する手順を順番に説明していきます。

組織で Cloud App Security を使用するためのライセンスを所有している必要があります。 価格詳細については、[Cloud App Security ライセンス データシート](https://aka.ms/mcaslicensing)を参照してください。

>[!NOTE]
>Cloud App Security を使用するのに、Office 365 ライセンスは不要です。

## <a name="prerequisites"></a>必要条件

- 組織で Cloud App Security を使用するためのライセンスを所有している必要があります。 価格詳細については、[Cloud App Security ライセンス データシート](https://aka.ms/mcaslicensing)を参照してください。

     テナントのライセンス認証のサポートが必要な場合は、「[一般法人向け Office 365 のサポートへのお問い合わせ - 管理者向けヘルプ](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)」をご覧ください。
- Cloud App Security のライセンスを入手すると、ライセンス認証情報と Cloud App Security ポータルへのリンクが記載されたメールが送信されます。

- Cloud App Security をセットアップするには、Azure Active Directory または Office 365 のグローバル管理者、コンプライアンス管理者、またはセキュリティ閲覧者である必要があります。 管理者ロールを割り当てられたユーザーは、組織がサブスクライブしているすべてのクラウド アプリについて同じアクセス許可を持つことを理解しておくことが重要です。 これは、ロールの割り当てを、Microsoft 365 管理センター、Azure クラシック ポータル、または [Windows PowerShell](https://technet.microsoft.com/library/mt736914.aspx) 用 Azure AD モジュールのいずれで行った場合でも同じです。 詳細については、「[Office 365 で管理者ロールを割り当てる](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504)」および「[Azure Active Directory の管理者ロールの割り当て](https://azure.microsoft.com/documentation/articles/active-directory-assign-admin-roles/)」を参照してください。

- Cloud App Security ポータルを実行するには、Internet Explorer 11、Microsoft Edge (最新版)、Google Chrome (最新版)、Mozilla Firefox (最新版)、Apple Safari (最新版) のいずれかを使用してください。

## <a name="to-access-the-portal"></a>ポータルにアクセスするには

Cloud App Security ポータルにアクセスするには、[https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com) に移動します。
管理センター アイコンをクリックして、**Microsoft 365 管理センター**からポータルにアクセスすることもできます。 ![O365 管理センター アイコン](./media/o365-admin-centers-icon.png "O365 管理センター アイコン") その後、 **[Cloud App Security]** を選択します。

![O365 からのアクセス](./media/access-from-o365.png "Access from O365")

## <a name="step-1-set-instant-visibility-protection-and-governance-actions-for-your-appsenable-instant-visibility-protection-and-governance-actions-for-your-appsmd"></a>手順 1. [アプリのインスタント表示、保護、およびガバナンス アクションの設定](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)

必要なタスク:アプリを接続する

1. 設定の歯車アイコンから **[アプリ コネクタ]** を選択します。
1. アプリを追加するプラス記号をクリックし、アプリを選択します。
1. 構成手順に従ってアプリを接続します。

**アプリを接続する必要がある理由。**
アプリを接続すると、クラウド環境でアプリのアクティビティやファイル、アカウントの詳細な調査ができます。

## <a name="step-2-control-cloud-apps-with-policiescontrol-cloud-apps-with-policiesmd"></a>手順 2. [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

必要なタスク:ポリシーの作成

### <a name="to-create-policies"></a>ポリシーを作成するには

1. **[制御]**  >  **[テンプレート]** の順に選択します。
1. リストからポリシー テンプレートを選択し、 **[ポリシーの作成]** \(+) を選択します。
1. ポリシーをカスタマイズ (フィルター、アクション、およびその他の設定を選択) し、 **[作成]** を選びます。
1. **[ポリシー]** タブでポリシーを選択して、関連する一致項目 (アクティビティ、ファイル、アラート) を確認できます。
 ヒント:社内のクラウド環境のあらゆるセキュリティ シナリオに対応するには、**リスク カテゴリ**ごとにポリシーを作成します。

### <a name="how-can-policies-help-your-organization"></a>ポリシーは企業でどのように役立つか

ポリシーは、傾向を監視したり、セキュリティ上の脅威を確認したり、カスタマイズされたレポートやアラートを生成することに利用できます。 ポリシーを使用すると、ガバナンス アクションの作成や、データ損失防止およびファイル共有コントロールの設定ができます。

## <a name="step-3-set-up-cloud-discoveryset-up-cloud-discoverymd"></a>手順 3. [Cloud Discovery のセットアップ](set-up-cloud-discovery.md)

必要なタスク:クラウド アプリの使用を確認できるように Cloud App Security を有効にする

1. [Microsoft Defender ATP と統合](wdatp-integration.md)することで、Cloud App Security が自動的に有効にされ、会社内外のご利用の Windows 10 デバイスを監視できるようになります。
1. Zscaler を使用する場合は、Cloud App Security に [Zscaler を統合](zscaler-integration.md)します。
1. 完全なカバレッジを実現するには、継続的な Cloud Discovery レポートを作成します。

   1. 設定の歯車アイコンから **[Cloud Discovery 設定]** を選択します。
   1. **[ログの自動アップロード]** を選択します。
   1. **[データ ソース]** タブでソースを追加します。
   1. **[ログ コレクター]** タブでログ コレクターを構成します。

### <a name="to-create-a-snapshot-cloud-discovery-report"></a>Cloud Discovery のスナップショット レポートを作成するには

 **[検出]**  >  **[スナップショット レポート]** に移動し、次に示す手順に従います。

### <a name="why-should-you-configure-cloud-discovery-reports"></a>Cloud Discovery レポートを構成する必要がある理由

社内のシャドウ IT 対策を把握することは不可欠です。
ログを分析すると、どのクラウド アプリが、どのユーザーに、どのデバイスで使用されているかを簡単に特定できます。

## <a name="step-4-personalize-your-experiencemail-settingsmd"></a>手順 4. [エクスペリエンスの個人設定](mail-settings.md)

推奨されるタスク:企業の詳細を追加する

### <a name="to-enter-email-settings"></a>電子メールの設定を入力するには

1. 設定の歯車アイコンから **[メールの設定]** を選択します。
1. **[メール送信者の ID]** でメール アドレスと表示名を入力します。
1. **[メールのデザイン]** で企業のメール テンプレートをアップロードします。

### <a name="to-set-admin-notifications"></a>管理者通知を設定するには

1. ナビゲーション バーでユーザー名を選択し、 **[ユーザー設定]** に移動します。
1. **[通知]** で、システム通知を設定する方法を構成します。
1. **[保存]** を選びます。

### <a name="to-customize-the-score-metrics"></a>スコアのメトリックをカスタマイズするには

1. 設定の歯車アイコンから **[Cloud Discovery 設定]** を選択します。
1. 設定の歯車アイコンから **[Cloud Discovery 設定]** を選択します。
1. **[Score metris]\(スコア メトリック\)** で各種のリスクの値の重要度を構成します。
1. **[保存]** を選択します。

検出されたアプリに付与されたリスク スコアは、企業のニーズと優先順位に従って正確に構成されます。

### <a name="why-personalize-your-environment"></a>環境のカスタマイズが必要な理由

一部の機能は、お客様のニーズに合わせてカスタマイズされたときに最大の効果を発揮します。
独自のメール テンプレートでユーザー用の優れたエクスペリエンスを提供します。 どのような通知を受信するかを決定し、企業のニーズに応じてリスク スコア メトリックをカスタマイズします。

## <a name="step-5-organize-the-data-according-to-your-needsip-tagsmd"></a>手順 5. [ニーズに応じたデータの編成](ip-tags.md)

推奨されるタスク:重要な設定を構成する

### <a name="to-create-ip-address-tags"></a>IP アドレスのタグを作成するには

1. 設定の歯車アイコンから **[Cloud Discovery 設定]** を選択します。
1. 設定の歯車アイコンから **[IP アドレスの範囲]** を選択します。
1. IP アドレスの範囲を追加するプラス記号をクリックします。
1. IP アドレス範囲の**詳細**や**場所**、**タグ**、**カテゴリ**を入力します。
1. **[作成]** を選択します。

   これでポリシーを作成するときや、継続的レポートをフィルター処理して作成するときに、IP タグを使うことができるようになります。

### <a name="to-create-continuous-reports"></a>継続的レポートを作成するには

1. 設定の歯車アイコンから、 **[Cloud Discovery 設定**] を選択します。
1. **[継続的レポート]** で **[レポートの作成]** を選びます。
1. 以下の構成手順に従います。
1. **[作成]** を選択します。

部署や IP アドレス範囲などの設定に基づいて、検出されたデータを表示できます。

### <a name="to-add-domains"></a>ドメインを追加するには

1. 設定の歯車アイコンから **[設定]** を選択します。
1. **[組織の詳細]** で企業の内部ドメインを追加します。
1. **[保存]** を選びます。

### <a name="why-should-you-configure-these-settings"></a>これらの設定を構成する必要がある理由

これらの設定によって、コンソールの機能をより適切に制御できるようになります。 IP タグを使用すると、ニーズに応じたポリシーの作成や、正確なデータのフィルタリングなどの作業が簡単になります。 データを論理カテゴリにグループ化する際にこのデータ ビューをご利用ください。

## <a name="next-steps"></a>次の手順

ポリシーの設定については、「[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)」を参照してください。

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)
