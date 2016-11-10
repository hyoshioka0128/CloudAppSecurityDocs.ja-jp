---
title: "Cloud App Security とは | Microsoft Docs"
description: "このトピックでは、Cloud App Security の概要とそのしくみについて説明します。"
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
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: d2ece0e3a47dc0febbb1314c496045abdc5c8d61


---
# <a name="what-is-cloud-app-security"></a>Cloud App Security とは
 
> [!NOTE] 
> Office 365 の Advanced Security Management - Cloud App Security 機能の詳細については、[Advanced Security Management](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a) の概要を参照してください。 
 
クラウドに移行することで、従業員の柔軟性が向上し、IT コストが削減されますが、組織のセキュリティを確保するための複雑さと課題も新たに生じます。 クラウド アプリケーションのメリットを完全に実現するために、IT チームはアクセスを許可することと、重要なデータを保護するための制御を維持することの間で適切なバランスを見つける必要があります。  
  
Cloud App Security は、Microsoft Cloud Security スタックの重要なコンポーネントで、 クラウド アプリケーションが約束する完全なメリットを実現すると同時に、アクティビティの可視性を強化して制御を維持できる包括的なソリューションです。 また、クラウド アプリケーション全体で重要なデータの保護も強化します。 シャドウ IT の発見、リスクの評価、ポリシーの適用、アクティビティの調査、脅威の防止を行うためのツールを使用して、組織のお客様は重要なデータの制御を維持しながらクラウドに安全に移行できます。  
  
## <a name="the-cloud-app-security-framework"></a>Cloud App Security のフレームワーク  

|       |   |   |
|-------|---|:---|
|![[探索]](./media/discovery-icon.png)|[探索]|Cloud App Security でシャドウ ITを検出することができます。 クラウド環境内のアプリ、アクティビティ、ユーザー、データ、ファイルに加えて、クラウドに接続されているサードパーティ製アプリを検出して把握できます。|
|![調査](./media/investigate-icon.png)|調査|クラウド フォレンジクス ツールを使用して、クラウド アプリを調査し、ネットワーク内の危険なアプリ、特定のユーザー、ファイルの詳細を確認できるほか、クラウドから収集されたデータのパターンを特定したり、クラウドを監視するレポートを生成したりできます。|
|![Control](./media/protect-icon.png)|Control|ポリシーとアラートを設定して、クラウドのネットワーク トラフィックを最大限に制御し、リスクを軽減します。 Cloud App Security を使用すると、承認された安全な代替クラウド アプリにユーザーを移行できます。|
|![保護](./media/protect-icon.png)|保護|Cloud App Security を使用すると、アプリケーションの承認または却下、データ損失防止 (DLP) の実施、アクセス許可と共有の制御、カスタムのレポートおよびアラートの生成を行うことができます。|


## <a name="architecture"></a>アーキテクチャ  

Cloud App Security では、以下の方法で、クラウドの可視性の統合を実現します。  
  
-   Cloud Discovery を使用して、クラウド環境と使用されているクラウド アプリをマップおよび特定して把握します。  
-   クラウド内のアプリを承認および却下します。  
-   プロバイダーの API を活用する簡単にデプロイ可能なアプリ コネクタを使用して、接続したアプリを把握および統制します。  
-   ポリシーを設定し、継続的に調整できるようにすることで、継続的に制御します。  
  
![](./media/architecture.png)  
  
> [!NOTE]  
>  Cloud App Security でコンテンツの調査を実施する際には、データのプライバシー保護が適用されます。 Cloud App Security データベースに保存されるのは、ファイル レコードのメタデータと特定された違反のみで、お客様のデータは保存されません。 データ リテンション期間の詳細については、Microsoft の[プライバシー ポリシー](http://go.microsoft.com/fwlink/?LinkId=512132)と [Microsoft セキュリティ センター](https://www.microsoft.com/TrustCenter/Privacy/You-are-in-control-of-your-data)を参照してください。
Cloud App Security は次のようにデータを保持しています。
>- アクティビティ ログ: 180 日間
>- 検出データ: 90 日間
>- アラート: 無制限 

これらのソースからデータが収集されると、Cloud App Security で高度な分析が実行されます。異常なアクティビティが検出された場合はすぐに警告して、詳細な可視性を提供します。 この場合、Cloud App Security でポリシーを構成し、クラウド環境内のすべてのデータを保護するために使用することができます。  
  
###  <a name="how-cloud-discovery-works"></a>Cloud Discovery のしくみ  

Cloud Discovery では、トラフィック ログを使用して、組織内でどのクラウド アプリが使用されているかを動的に検出、分析します。  
  
組織のクラウド使用に関するスナップショット レポートを作成するには、ファイアウォールまたはプロキシからログ ファイルを手動でアップロードして分析するか、Cloud App Security のログ コレクターを使用してログを定期的に転送することで継続的なレポートを設定することができます。  

Cloud Discovery の詳細については、「[Set up Cloud Discovery](set-up-cloud-discovery.md)」(Cloud Discovery のセットアップ) を参照してください。
  
### <a name="how-sanctioning-and-unsanctioning-an-app-works"></a>アプリの承認および却下のしくみ  

Cloud App Security では、**クラウド アプリ カタログ**を使用して、組織内のアプリを承認または却下することができます。  
  
Microsoft のアナリスト チームでは、13,000 以上のクラウド アプリを掲載した大規模なカタログを作成し、新たなアプリを継続的に追加しています。このカタログのクラウド アプリは、業界標準に基づいてランク付けおよびスコア付けされています。 **クラウド アプリ カタログ** では、規制遵守の認定、業界標準、ベスト プラクティスに基づいて、クラウド アプリのリスクがランク付けされます。 お客様は、組織のニーズに合わせて、さまざまなパラメーターのスコアと重みをカスタマイズできます。 Cloud App Security では、これらのスコアに基づき、お客様の環境に影響を与える 50 以上のリスク要因に照らしたアプリの危険度を確認できます。  
  
### <a name="how-app-connectors-work"></a>アプリ コネクタのしくみ  
アプリ コネクタでは、さまざまなクラウド アプリ プロバイダーによって提供される API を利用することで、Cloud App Security のクラウドを他のクラウド アプリと統合し、制御や保護を拡張します。 これにより、Cloud App Security は分析する情報をクラウド アプリから直接取得することができます。  
アプリを接続して保護を拡張するために、アプリ管理者は Cloud App Security に対してアプリへのアクセス許可を承認します。Cloud App Security はアプリへのクエリを実行してアクティビティ ログを取得し、データ、アカウント、クラウドのコンテンツをスキャンします。 Cloud App Security はその後、ポリシーを適用して脅威を検出し、問題を解決するためのガバナンス アクションを提供します。  
  
Cloud App Security はクラウド プロバイダーが提供する API を利用しますが、各アプリには独自のフレームワークと API の制限事項があります。 Cloud App Security では、各アプリ プロバイダーと連携して、API の使用を最適化すると共に、最適なパフォーマンスを確保しています。 アプリが API に加えたさまざまな制限事項 (調整、API の制限、動的なタイムシフト API の期間など) を考慮して、Cloud App Security エンジンでは使用可能な機能が活用されます。 テナント内のすべてのファイルのスキャンなど、一部の処理には大量の API が必要となるため、長時間にわたって実行されます。 ポリシーによっては、数時間または数日間にわたって実行される場合があります。  
  
### <a name="how-policy-control-works"></a>ポリシー制御のしくみ  

ポリシーを使用すると、クラウド内のユーザーの動作を定義できます。 クラウド環境内の危険な動作、違反、疑わしいデータ ポイントやアクティビティを検出し、必要な場合には、修復プロセスを統合してリスクを完全に抑制します。 収集するクラウド環境の情報の種類や実行する修復アクションの種類ごとに、さまざまな種類のポリシーが関連付けられています。  
  
## <a name="see-also"></a>参照  

[Cloud App Security の使用を開始する](getting-started-with-cloud-app-security.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


