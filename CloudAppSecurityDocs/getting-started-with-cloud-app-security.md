---
title: "Cloud App Security の使用を開始する | Microsoft Docs"
description: "このトピックでは、Cloud App Security を準備して使用を開始するプロセスの概要について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: cf040b18-93d1-41e8-a26a-647c56afb00f
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 8b454edde557c408b644c9bff6f7bf6136ba9819


---

# <a name="getting-started-with-cloud-app-security"></a>Cloud App Security の使用を開始する
Cloud App Security では、クラウド アプリのメリットを活用しながら、同時にアクティビティの可視性を向上させて管理性を維持し、重要な企業データの保護を強化することができます。  このドキュメントでは、Cloud App Security の使用手順を順を追って説明します。  
  
製品を使用するには、企業が Cloud App Security のライセンスを所有している必要があります。 詳細については、[Cloud App Security の購入方法](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx)および[ライセンス関連資料](https://www.microsoft.com/server-cloud/products/cloud-app-security/default.aspx)を参照してください。  
  
>[!NOTE]
>Office 365 のライセンスは Cloud App Security には必要ありません。  
  
## <a name="get-started-quickly-with-cloud-app-security"></a>Cloud App Security の使用をすばやく開始する  
  
|手順の内容|タスク|必須?|手順|説明|  
|-------------------------|----------|---------------|-------------|-----------------|  
|手順 1. [Cloud Discovery をセットアップします](set-up-cloud-discovery.md)。|トラフィック ログのアップロード|必須|**継続的な Cloud Discovery レポートを作成する**<br /><br /> 1. [**設定**] -> [**Cloud Discovery settings**] (Cloud Discovery の設定) の順に選択します。<br /><br /> 2.  [**Upload log automatically ログを自動的にアップロード)**] をクリックします。<br /><br /> 3. [**データ ソース**] タブでデータ ソースを追加します。<br /><br /> 4.  [**ログ コレクター**] タブでログ コレクターを構成します。<br /><br /> Cloud Discovery のスナップショット レポートを作成する<br /><br /> 1.  [**検出**] -> [**新しいスナップショット レポートの作成**] に移動し、次の手順のようにします|**Cloud Discovery レポートを構成する必要がある理由。** 社内のシャドウ IT 対策を把握することは不可欠です。  <br />ログを分析すると、どのクラウド アプリが、どのユーザーに、どのデバイスで使用されたかを簡単に特定できます。|  
|手順 2. [アプリの可視性、保護、およびガバナンス アクションをすぐに有効化します](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)。|アプリを接続する|必須|1. [**設定**] -> [**承認されたアプリ**] の順に選択します。<br /><br /> 2.[**アプリを接続**] をクリックしてからアプリを選択します。<br /><br /> 3.構成手順に従ってアプリを接続します。|**アプリを接続する必要がある理由。**<br /><br /> アプリを接続しないと、クラウド環境でクラウド アプリのアクティビティやファイル、アカウントの詳細な調査を実施できません。|  
|手順 3. [ポリシーによってクラウド アプリを制御します](control-cloud-apps-with-policies.md)。|ポリシーの作成|必須|**ポリシーを作成する**<br /><br /> 1.[**制御**] -> [**テンプレート**] の順に選択します。<br /><br /> 2.  リストからポリシー テンプレートを選択し、[**ポリシーの作成**] (+) をクリックします。<br /><br /> 3.ニーズに合わせてポリシーをカスタマイズ (フィルター、アクション、およびその他の構成) し、[**作成**] をクリックします。<br /><br /> 4.  作成したポリシーを [**ポリシー**] タブでクリックすると、関連する一致項目 (アクティビティやファイル、アラートなど) を確認できます。<br /><br /> ヒント - **リスク カテゴリ**ごとにポリシーを作成し、社内のクラウド環境のあらゆるセキュリティ シナリオに対応してください。|**ポリシーは企業でどのように役立つか。**<br /><br /> ポリシーは、傾向を監視したり、セキュリティ上の脅威を確認したり、カスタマイズされたレポートやアラートを生成したりするツールとして利用できます。 ポリシーを使用すると、さまざまなガバナンス アクションや DLP、ファイル共有コントロールを作成できます。|  
|手順 4. [エクスペリエンスの個人設定を行います](general-setup.md#Adallom_mailsettings)。|企業の詳細を追加する|推奨|**電子メールの設定を入力する**<br /><br /> 1.[**設定**] -> [**メールの設定**] の順に選択します。<br /><br /> 2. [**メール送信者の ID**] でメール アドレスと表示名を入力します。<br /><br /> 3.[**メールのデザイン**] で企業のメール テンプレートをアップロードします。<br /><br /> **管理者通知を設定する**<br /><br /> 1.  ナビゲーション バーでユーザー名をクリックしてから [**ユーザー設定**] に移動します。<br /><br /> 2.  [**通知**] で、システム通知を設定する方法を構成します。<br /><br /> 3.**[Save]**(保存) をクリックします。<br /><br /> **スコアのメトリックをカスタマイズする**<br /><br /> 1.[**設定**] -> [**Cloud Discovery settings**] (Cloud Discovery の設定) の順に選択します。<br /><br /> 2.  [**Score metric configuration (スコア メトリックの構成)**] で各種のリスクの値の重要度を構成します。<br /><br /> 3.  **[Save]**(保存) をクリックします。<br /><br /> 検出されたアプリに付与されたリスク スコアは、企業のニーズと優先順位に従って正確に構成されます。|**環境のカスタマイズが必要な理由。**<br /><br /> 一部の機能は、お客様のニーズに合わせてカスタマイズされたときに最大の効果を発揮します。  <br />独自の電子メール テンプレートをユーザーに提供したり、どのような通知を受信するかを決定したり、企業のニーズに応じてリスク スコア メトリックをカスタマイズしたりできます。|  
|手順 5. [ニーズに応じてデータを編成します](general-setup.md#IPtagsandRanges)。|重要な設定を構成する|推奨|**IP アドレスのタグを作成する**<br /><br /> 1. [**設定**] -> [**IP アドレス タグ**] の順に選択します。<br /><br /> 2.[**IP アドレス範囲の追加**] (+) をクリックします。<br /><br /> 3.  IP アドレス範囲の**詳細**や**場所**、**タグ**、**カテゴリ**を入力します。<br /><br /> 4.[**作成**] をクリックします。<br /><br /> これで、ポリシーの作成、データ ビューの作成やフィルタリングに IP タグを使用できるようになりました。<br /><br /> **ビューを作成する**<br /><br /> 1.[**設定**] -> [**Cloud Discovery settings**] (Cloud Discovery の設定) の順に選択します。<br /><br /> 2.  [**データ ビュー**] の [**Add data view**] (データ ビューの追加) (+) をクリックします。<br /><br /> 3.以下の構成手順に従います。<br /><br /> 4.[**作成**] をクリックします。<br /><br /> 部署や IP アドレス範囲などの設定に基づいて、検出されたデータを表示できます。<br /><br /> **ドメインを追加する**<br /><br /> 1.  [**設定**] -> [**全般設定**] の順に選択します。<br /><br /> 2.  [**組織の詳細**] で企業の内部ドメインを追加します。<br /><br /> 3.**[Save]**(保存) をクリックします。|**これらの設定を構成する必要がある理由。**<br /><br /> これらの設定を使用すると、コンソールのさまざまな機能が向上し、また簡単に制御できるようになります。 IP タグでは、ニーズに応じてポリシーを作成したり、正確にデータをフィルタリングするなどの作業が簡単になります。 データを論理カテゴリにグループ化する際にこのデータ ビューをご利用ください。|  
  
## <a name="see-also"></a>参照  
[一般的なセットアップ](general-setup.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


