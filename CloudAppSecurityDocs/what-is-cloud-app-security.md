---
title: "Cloud App Security とは | Microsoft Docs"
description: "このトピックでは、Cloud App Security とそのしくみについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 224c7039ecb7200ad951774ac5fb76202543a35c
ms.openlocfilehash: 690e58cd598ee9a6dd329e19cd65129df160e009


---
# <a name="what-is-cloud-app-security"></a>Cloud App Security とは

> [!NOTE]
> Office 365 の Advanced Security Management と Cloud App Security の詳細については、「[Get started with Advanced Security Management](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)」(Advanced Security Management の概要) を参照してください。

クラウドに移行することで、従業員の柔軟性が向上し、IT コストが削減されますが、組織のセキュリティを確保するための複雑さと課題も新たに生じます。 クラウド アプリケーションの利点を最大限に活用するには、IT チームはアクセスを許可することと、重要なデータを保護するための制御を維持することの間で適切なバランスを見つける必要があります。  

Cloud App Security は、Microsoft Cloud Security スタックの重要なコンポーネントで、 クラウド アプリケーションが約束するメリットをユーザーが十分に受けられるように組織を支援するだけでなく、アクティビティの可視性を強化して制御を維持できる包括的なソリューションです。 また、クラウド アプリケーション全体で重要なデータの保護も強化します。 シャドウ IT の発見、リスクの評価、ポリシーの適用、アクティビティの調査、脅威の防止に役立つツールを使用することで、組織は重要なデータの制御を維持しながらクラウドにより安全に移行できます。  

## <a name="the-cloud-app-security-framework"></a>Cloud App Security のフレームワーク  

|       |   |   |
|-------|---|:---|
|![[探索]](./media/discovery-icon.png)|[探索]|Cloud App Security でシャドウ IT を検出します。 クラウド環境内のアプリ、アクティビティ、ユーザー、データ、ファイルを検出して把握します。 クラウドに接続されているサードパーティ製アプリを検出します。|
|![調査](./media/investigate-icon.png)|調査|クラウド フォレンジクス ツールを使用して、ネットワーク内の危険なアプリ、特定のユーザー、ファイルの詳細を調査します。 クラウドから収集されたデータのパターンを検索します。 クラウドを監視するレポートを生成します。|
|![Control](./media/protect-icon.png)|Control|ポリシーとアラートを設定して、クラウドのネットワーク トラフィックを最大限に制御し、リスクを軽減します。 Cloud App Security を使用すると、承認された安全な代替クラウド アプリにユーザーを移行できます。|
|![保護](./media/protect-icon.png)|保護|Cloud App Security を使用すると、アプリケーションの承認または却下、データ損失防止の実施、アクセス許可と共有の制御、カスタムのレポートおよびアラートの生成を行うことができます。|


## <a name="architecture"></a>アーキテクチャ  

以下を行うことで、Cloud App Security によってクラウドに可視性が統合されます。  

-   Cloud Discovery を使用して、クラウド環境と組織で使用しているクラウド アプリをマップおよび特定する。
-   クラウド内のアプリを承認および却下する。  
-   プロバイダーの API を活用する簡単にデプロイ可能なアプリ コネクタを使用して、接続したアプリを把握および統制する。  
-   ポリシーを設定し、継続的に調整できるようにすることで、継続的に制御する。  

![Cloud App Security アーキテクチャ](./media/architecture.png)  

> [!NOTE]  
> Cloud App Security でコンテンツの調査を実施する際には、データのプライバシー保護が適用されます。 Cloud App Security データベースに保存されるのは、ファイル レコードのメタデータと特定された違反のみです。 お客様のデータは Cloud App Security データベースに保存されません。 データ保持期間の詳細については、Microsoft の[プライバシー ポリシー](http://go.microsoft.com/fwlink/?LinkId=512132)と [Microsoft セキュリティ センター](https://www.microsoft.com/TrustCenter/Privacy/You-are-in-control-of-your-data)を参照してください。
Cloud App Security は次のようにデータを保持しています。
>- アクティビティ ログ: 180 日間
>- 検出データ: 90 日間
>- アラート: 無制限

これらのソースからデータが収集されると、Cloud App Security はデータを使って高度な分析を実行します。 異常なアクティビティはすぐに通知され、クラウド環境の詳細が提供されます。 Cloud App Security でポリシーを構成し、クラウド環境内のすべてのデータを保護するために使用することができます。  

### <a name="cloud-discovery"></a>Cloud Discovery  

Cloud Discovery では、トラフィック ログを使用して、組織内で使用しているクラウド アプリを動的に検出、分析します。 組織のクラウド使用のスナップショット レポートを作成するために、ファイアウォールまたはプロキシから分析用のログ ファイルを手動でアップロードすることができます。 継続的なレポートをセットアップするには、Cloud App Security ログ コレクターを使用して定期的にログを転送します。  

Cloud Discovery の詳細については、「[Set up Cloud Discovery](set-up-cloud-discovery.md)」(Cloud Discovery のセットアップ) を参照してください。

### <a name="sanctioning-and-unsanctioning-an-app"></a>アプリの承認および却下  

Cloud App Security では、*クラウド アプリ カタログ*を使用して、組織内のアプリを承認または却下することができます。 Microsoft のアナリスト チームでは、13,000 以上のクラウド アプリを掲載した大規模なカタログを作成し、新たなアプリを継続的に追加しています。このカタログのクラウド アプリは、業界標準に基づいてランク付けおよびスコア付けされています。 クラウド アプリ カタログを使用して、規制遵守の認定、業界標準、ベスト プラクティスに基づいて、クラウド アプリのリスクをランク付けできます。 その後、組織のニーズに合わせて、さまざまなパラメーターのスコアと重みをカスタマイズします。 Cloud App Security では、これらのスコアに基づき、お客様の環境に影響を与える 50 以上のリスク要因に基づいてアプリの危険度を確認できます。  

### <a name="app-connectors"></a>アプリ コネクタ  
アプリ コネクタは、クラウド アプリ プロバイダーが提供する API を使用して、Cloud App Security クラウドとその他のクラウド アプリを統合します。 アプリ コネクタは、コントロールと保護を拡張します。 また、Cloud App Security の分析のため、クラウド アプリから直接情報にアクセスすることもできます。  

アプリを接続して保護を拡張するにはめ、アプリの管理者がアプリにアクセスする Cloud App Security を認証します。 すると、Cloud App Security はアクティビティ ログに対してアプリを照会し、データ、アカウント、およびクラウド コンテンツをスキャンします。 Cloud App Security は、ポリシーを適用して脅威を検出し、問題を解決するためのガバナンス アクションを提供します。  

Cloud App Security は、クラウド プロバイダーから提供される API を使用します。 各アプリには、独自のフレームワークと API の制限事項があります。 Cloud App Security では、各アプリ プロバイダーと連携して、API の使用を最適化すると共に、最適なパフォーマンスを確保しています。 アプリが API に課すさまざまな制限事項 (調整、API の制限、動的なタイムシフト API の期間など) を考慮して、Cloud App Security エンジンでは使用可能な機能が活用されます。 テナント内のすべてのファイルのスキャンなど、一部の処理には大量の API が必要となるため、長時間にわたって実行されます。 ポリシーによっては、数時間または数日間にわたって実行される場合があります。  

### <a name="policy-control"></a>ポリシー コントロール  

ポリシーを使用して、クラウドでのユーザーの動作を定義できます。 ポリシーを使用して、危険な動作、違反、またはクラウド環境内の疑わしいデータ ポイントやアクティビティを検出します。 必要に応じて、ポリシーを使用して修復プロセスを統合し、完全なリスクの軽減を実現することができます。 収集するクラウド環境の情報の種類や実行する修復アクションの種類ごとに、さまざまな種類のポリシーが関連付けられています。  

## <a name="see-also"></a>参照  

基本については、「[Cloud App Security の使用を開始する](getting-started-with-cloud-app-security.md)」をご覧ください。    
テクニカル サポートが必要な場合は、[Cloud App Security のサポート](http://support.microsoft.com/oas/default.aspx?prid=16031) ページをご利用ください。   
Premier サポートをご利用のお客様も、[Premier ポータル](https://premier.microsoft.com/)から直接 Cloud App Security を選択することができます。   



<!--HONumber=Nov16_HO3-->


