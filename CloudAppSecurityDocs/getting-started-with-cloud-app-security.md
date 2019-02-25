---
title: Cloud App Security の展開
description: このクイックスタートでは、クラウド アプリを使用、洞察、制御できるように、Cloud App Security を準備して使用を開始するプロセスの概要について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 1/27/2019
ms.topic: quickstart
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: cf040b18-93d1-41e8-a26a-647c56afb00f
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d6e6206b9d361ad9a5b47c3ec76ecc8dac4a1e20
ms.sourcegitcommit: fd1bf30af3117d8ad6cf241f3e02ad5e4c4bc9a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "56409615"
---
#  <a name="quickstart-get-started-with-microsoft-cloud-app-security"></a>クイック スタート:Microsoft Cloud App Security の使用を開始する

*適用対象: Microsoft Cloud App Security*

このクイックスタートでは、Cloud App Security を準備して使用を開始する手順を示します。 Microsoft Cloud App Security は、クラウド アプリケーションの利点の活用に役立つだけでなく、会社のリソース管理にも役立ちます。 これは、クラウドの利用状況の可視性を向上させ、企業データの保護を強化することによって機能します。 この記事では、Microsoft Cloud App Security をセットアップして使用する手順を順番に説明していきます。  

組織で Cloud App Security を使用するためのライセンスを所有している必要があります。 詳細については、Cloud App Security のホーム ページの「[Cloud App Security の購入方法](https://www.microsoft.com/cloud-platform/cloud-app-security)」セクションを参照してください。  

>[!NOTE]
>Cloud App Security を使用するのに、Office 365 ライセンスは不要です。  

## <a name="prerequisites"></a>前提条件  
  
- 製品を使用するには、企業が Cloud App Security のライセンスを所有している必要があります。 詳細については、Cloud App Security のホーム ページの「[Cloud App Security の購入方法](https://www.microsoft.com/cloud-platform/cloud-app-security)」セクションを参照してください。  
  
     テナントのライセンス認証のサポートが必要な場合は、「[一般法人向け Office 365 のサポートへのお問い合わせ - 管理者向けヘルプ](https://support.office.com/article/Contact-Office-365-for-business-support-Admin-Help-32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)」をご覧ください。  
- Cloud App Security のライセンスを入手すると、ライセンス認証情報と Cloud App Security ポータルへのリンクが記載されたメールが送信されます。  
  
- Cloud App Security をセットアップするには、Azure Active Directory または Office 365 のグローバル管理者、コンプライアンス管理者、またはセキュリティ閲覧者である必要があります。 管理者ロールを割り当てられたユーザーは、組織がサブスクライブしているすべてのクラウド アプリについて同じアクセス許可を持つことを理解しておくことが重要です。 これは、ロールの割り当てを、Office 365 ポータル、Azure クラシック ポータル、または [Windows PowerShell](https://technet.microsoft.com/library/mt736914.aspx) 用 Azure AD モジュールのいずれで行った場合でも同じです。 詳細については、「[Office 365 で管理者ロールを割り当てる](https://support.office.com/article/Assigning-admin-roles-in-Office-365-eac4d046-1afd-4f1a-85fc-8219c79e1504)」および「[Azure Active Directory の管理者ロールの割り当て](https://azure.microsoft.com/documentation/articles/active-directory-assign-admin-roles/)」を参照してください。  
  
- Cloud App Security ポータルを実行するには、Internet Explorer 11、Microsoft Edge (最新版)、Google Chrome (最新版)、Mozilla Firefox (最新版)、Apple Safari (最新版) のいずれかを使用してください。  

## <a name="to-access-the-portal"></a>ポータルにアクセスするには

Cloud App Security ポータルにアクセスするには、[https://portal.cloudappsecurity.com](https://portal.cloudappsecurity.com) に移動します。  
管理センター アイコンをクリックして、**Office 365 管理センター**からポータルにアクセスすることもできます。 ![O365 管理センター アイコン](./media/o365-admin-centers-icon.png "O365 管理センター アイコン") その後、**[Cloud App Security]** を選択します。  
  
![O365 からのアクセス](./media/access-from-o365.png "Access from O365")  
  



## <a name="step-1-set-instant-visibility-protection-and-governance-actions-for-your-appsenable-instant-visibility-protection-and-governance-actions-for-your-appsmd"></a>手順 1. [アプリの可視性、保護、およびガバナンス アクションをすぐに設定します](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)。
必要なタスク:アプリを接続する

1. 設定の歯車アイコンから **[アプリ コネクタ]** を選択します。
2. アプリを追加するプラス記号をクリックし、アプリを選択します。
3. 構成手順に従ってアプリを接続します。

**アプリを接続する必要がある理由。**
アプリを接続すると、クラウド環境でアプリのアクティビティやファイル、アカウントの詳細な調査ができます。


## <a name="step-2-control-cloud-apps-with-policiescontrol-cloud-apps-with-policiesmd"></a>手順 2. [ポリシーによってクラウド アプリを制御します](control-cloud-apps-with-policies.md)。
必要なタスク:ポリシーの作成

**ポリシーを作成するには**

1. **[制御]** > **[テンプレート]** の順に選択します。
2. リストからポリシー テンプレートを選択し、**[ポリシーの作成]** \(+) を選択します。
3. ポリシーをカスタマイズ (フィルター、アクション、およびその他の設定を選択) し、**[作成]** を選びます。
4. **[ポリシー]** タブでポリシーを選択して、関連する一致項目 (アクティビティ、ファイル、アラート) を確認できます。
 ヒント社内のクラウド環境のあらゆるセキュリティ シナリオに対応するには、**リスク カテゴリ**ごとにポリシーを作成します。

**ポリシーは企業でどのように役立つか。**
ポリシーは、傾向を監視したり、セキュリティ上の脅威を確認したり、カスタマイズされたレポートやアラートを生成することに利用できます。 ポリシーを使用すると、ガバナンス アクションの作成や、データ損失防止およびファイル共有コントロールの設定ができます。


## <a name="step-3-set-up-cloud-discoveryset-up-cloud-discoverymd"></a>手順 3. [Cloud Discovery をセットアップします](set-up-cloud-discovery.md)。

必要なタスク:クラウド アプリの使用を確認できるように Cloud App Security を有効にする

1. [Windows Defender ATP と統合](wdatp-integration.md)することで、Cloud App Security が自動的に有効にされ、会社内外のご利用の Windows 10 デバイスを監視できるようになります。
2. Zscaler を使用する場合は、Cloud App Security に [Zscaler を統合](zscaler-integration.md)します。
3. 完全なカバレッジを実現するには、継続的な Cloud Discovery レポートを作成します。

   1. 設定の歯車アイコンから **[Cloud Discovery 設定]** を選択します。
   2. **[ログの自動アップロード]** を選択します。
   3. **[データ ソース]** タブでソースを追加します。
   4. **[ログ コレクター]** タブでログ コレクターを構成します。
 
**Cloud Discovery のスナップショット レポートを作成するには**

 **[検出]** > **[スナップショット レポート]** に移動し、次に示す手順に従います。

**Cloud Discovery レポートを構成する必要がある理由。**
社内のシャドウ IT 対策を把握することは不可欠です。
ログを分析すると、どのクラウド アプリが、どのユーザーに、どのデバイスで使用されているかを簡単に特定できます。

## <a name="step-4-personalize-your-experiencemail-settingsmd"></a>手順 4. [エクスペリエンスの個人設定を行います](mail-settings.md)。
推奨されるタスク:企業の詳細を追加する

**電子メールの設定を入力するには**

1. 設定の歯車アイコンから **[メールの設定]** を選択します。
2. **[メール送信者の ID]** でメール アドレスと表示名を入力します。
3. **[メールのデザイン]** で企業のメール テンプレートをアップロードします。

**管理者通知を設定するには**

1. ナビゲーション バーでユーザー名を選択し、**[ユーザー設定]** に移動します。
2. **[通知]** で、システム通知を設定する方法を構成します。
3. **[保存]** を選択します。

**スコアのメトリックをカスタマイズするには**

1. 設定の歯車アイコンから **[Cloud Discovery 設定]** を選択します。
1. 設定の歯車アイコンから **[Cloud Discovery 設定]** を選択します。
2. **[Score metris]\(スコア メトリック\)** で各種のリスクの値の重要度を構成します。
3. **[保存]** を選択します。

検出されたアプリに付与されたリスク スコアは、企業のニーズと優先順位に従って正確に構成されます。

**環境のカスタマイズが必要な理由。**
一部の機能は、お客様のニーズに合わせてカスタマイズされたときに最大の効果を発揮します。 独自のメール テンプレートでユーザー用の優れたエクスペリエンスを提供します。 どのような通知を受信するかを決定し、企業のニーズに応じてリスク スコア メトリックをカスタマイズします。


## <a name="step-5-organize-the-data-according-to-your-needsip-tagsmd"></a>手順 5. [ニーズに応じてデータを編成します](ip-tags.md)。
推奨されるタスク:重要な設定を構成する

**IP アドレスのタグを作成するには**

1. 設定の歯車アイコンから **[Cloud Discovery 設定]** を選択します。
1. 設定の歯車アイコンから **[IP アドレスの範囲]** を選択します。
2. IP アドレスの範囲を追加するプラス記号をクリックします。
3. IP アドレス範囲の**詳細**や**場所**、**タグ**、**カテゴリ**を入力します。
4. **[作成]** を選択します。

   これでポリシーを作成するときや、継続的レポートをフィルター処理して作成するときに、IP タグを使うことができるようになります。

**継続的レポートを作成するには**

1. 設定の歯車アイコンから、**[Cloud Discovery 設定**] を選択します。
2. **[継続的レポート]** で **[レポートの作成]** を選びます。
3. 以下の構成手順に従います。
4. **[作成]** を選択します。

部署や IP アドレス範囲などの設定に基づいて、検出されたデータを表示できます。

**ドメインを追加するには**

1. 設定の歯車アイコンから **[設定]** を選択します。
2. **[組織の詳細]** で企業の内部ドメインを追加します。
3. **[保存]** を選択します。

**これらの設定を構成する必要がある理由。**
これらの設定によって、コンソールの機能をより適切に制御できるようになります。 IP タグを使用すると、ニーズに応じたポリシーの作成や、正確なデータのフィルタリングなどの作業が簡単になります。 データを論理カテゴリにグループ化する際にこのデータ ビューをご利用ください。
  

## <a name="next-steps"></a>次の手順

ポリシーの設定については、「[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)」を参照してください。    

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)   
