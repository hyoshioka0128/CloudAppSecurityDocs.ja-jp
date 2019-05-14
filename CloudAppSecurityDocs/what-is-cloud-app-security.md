---
title: Cloud App Security とは
description: この記事では、Microsoft Cloud App Security とそのしくみについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 1/27/2019
ms.topic: overview
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 525df694492667bf12ceb8a9fe30654f97c19935
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568779"
---
# <a name="microsoft-cloud-app-security-overview"></a>Microsoft Cloud App Security の概要

*適用対象:Microsoft Cloud App Security*

> [!NOTE]
> Office 365 Cloud App Security については、「[高度なセキュリティ管理の使用を開始する](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)」をご覧ください。

クラウドに移行することで、従業員の柔軟性が向上し、IT コストが削減されます。 ただし、組織のセキュリティを確保するための複雑さと課題も新たに生じます。 クラウド アプリケーションの利点を最大限に活用するには、IT チームはアクセスを許可することと、重要なデータを保護するための制御を維持することの間で適切なバランスを見つける必要があります。  

Cloud App Security は、Microsoft Cloud Security スタックの重要なコンポーネントで、 クラウド アプリケーションが約束するメリットをユーザーが十分に受けられるように組織を支援するだけでなく、アクティビティの可視性を強化して制御を維持できる包括的なソリューションです。 また、クラウド アプリケーション全体で重要なデータの保護も強化します。 シャドウ IT の発見、リスクの評価、ポリシーの適用、アクティビティの調査、脅威の防止に役立つツールを使用することで、組織は重要なデータの制御を維持しながらクラウドにより安全に移行できます。 

ライセンスについて詳しくは、[Microsoft Cloud App Security のライセンスのデータシート](https://aka.ms/mcaslicensing)をご覧ください。

## <a name="the-cloud-app-security-framework"></a>Cloud App Security のフレームワーク  

- **Cloud Discovery**:シャドウ IT のレポート、制御およびリスク評価を含む、組織でのクラウドの使用をすべて検出します。

- **データ保護**:可視化、DLP ポリシーの適用、アラートおよび調査により、クラウド内のデータを監視および制御します。 

- **脅威保護**:異常な使用とセキュリティ インシデントを検出します。 動作分析および高度な調査ツールを使用して、リスクを軽減し、ポリシーとアラートを設定してクラウドのネットワーク トラフィックを最大限に制御します。

## <a name="architecture"></a>アーキテクチャ  

以下を行うことで、Cloud App Security によってクラウドに可視性が統合されます。  

- Cloud Discovery を使用して、クラウド環境と組織で使用しているクラウド アプリをマップおよび特定する。
- クラウド内のアプリを承認および却下する。  
- プロバイダーの API を活用する簡単にデプロイ可能なアプリ コネクタを使用して、接続したアプリを把握および統制する。  
- アプリの条件付きアクセス制御の保護を使用して、クラウド アプリ内でのアクセスとアクティビティをリアルタイムで把握し、制御する。
- ポリシーを設定し、継続的に調整できるようにすることで、継続的に制御する。  

![Cloud App Security アーキテクチャの図](./media/proxy-architecture.png)  

### <a name="data-retention--compliance"></a>データ保有期間およびコンプライアンス

Microsoft Cloud App Security のデータ保有期間とコンプライアンスについて詳しくは、「[Microsoft Cloud App Security のデータのセキュリティとプライバシー](cas-compliance-trust.md)」をご覧ください。

### <a name="cloud-discovery"></a>Cloud Discovery  

Cloud Discovery では、トラフィック ログを使用して、組織内で使用しているクラウド アプリを動的に検出、分析します。 組織のクラウド使用のスナップショット レポートを作成するために、ファイアウォールまたはプロキシから分析用のログ ファイルを手動でアップロードすることができます。 継続的なレポートをセットアップするには、Cloud App Security ログ コレクターを使用して定期的にログを転送します。  

Cloud Discovery の詳細については、「[Set up Cloud Discovery](set-up-cloud-discovery.md)」(Cloud Discovery のセットアップ) を参照してください。

### <a name="sanctioning-and-unsanctioning-an-app"></a>アプリの承認および却下  

Cloud App Security では、*クラウド アプリ カタログ*を使用して、組織内のアプリを承認または却下することができます。 Microsoft のアナリスト チームでは、16,000 以上のクラウド アプリを掲載した大規模なカタログを作成し、新たなアプリを継続的に追加しています。このカタログのクラウド アプリは、業界標準に基づいてランク付けおよびスコア付けされています。 クラウド アプリ カタログを使用して、規制遵守の認定、業界標準、ベスト プラクティスに基づいて、クラウド アプリのリスクをランク付けできます。 その後、組織のニーズに合わせて、さまざまなパラメーターのスコアと重みをカスタマイズします。 Cloud App Security では、これらのスコアに基づき、アプリの危険度を確認できます。 スコアリングは、環境に影響を与える可能性がある 70 以上のリスク要因に基づきます。  

### <a name="app-connectors"></a>アプリ コネクタ

アプリ コネクタは、クラウド アプリ プロバイダーが提供する API を使用して、Cloud App Security クラウドとその他のクラウド アプリを統合します。 アプリ コネクタは、コントロールと保護を拡張します。 また、Cloud App Security の分析のため、クラウド アプリから直接情報にアクセスすることもできます。  

アプリを接続して保護を拡張するにはめ、アプリの管理者がアプリにアクセスする Cloud App Security を認証します。 すると、Cloud App Security はアクティビティ ログに対してアプリを照会し、データ、アカウント、およびクラウド コンテンツをスキャンします。 Cloud App Security は、ポリシーを適用して脅威を検出し、問題を解決するためのガバナンス アクションを提供します。  

Cloud App Security は、クラウド プロバイダーから提供される API を使用します。 各アプリには、独自のフレームワークと API の制限事項があります。 Cloud App Security では、各アプリ プロバイダーと連携して、API の使用を最適化すると共に、最適なパフォーマンスを確保しています。 アプリが API に課すさまざまな制限事項 (調整、API の制限、動的なタイムシフト API の期間など) を考慮して、Cloud App Security エンジンでは使用可能な機能が活用されます。 テナント内のすべてのファイルのスキャンなど、一部の処理には大量の API が必要となるため、長時間にわたって実行されます。 ポリシーによっては、数時間または数日間にわたって実行される場合があります。  

### <a name="conditional-access-app-control-protection"></a>Conditional Access App Control 保護

Microsoft Cloud App Security のアプリの条件付きアクセス制御では、リバース プロキシ アーキテクチャを使用して、クラウド環境へのアクセスとクラウド環境内で実行されるアクティビティのリアルタイムの表示と制御を行うのに必要なツールが提供されます。 Conditional Access App Control では、次のようにして組織を保護することができます。

- データのダウンロードをブロックして、事前にデータ リークを防ぐ
- 暗号化によって保護されるように、クラウドでのデータの格納とクラウドからのデータのダウンロードを強制するルールを設定する
- 非管理対象デバイスでの実行内容を監視できるように、保護されていないエンドポイントを把握する
- 会社以外のネットワークまたは危険な IP アドレスからのアクセスを制御する

### <a name="policy-control"></a>ポリシー コントロール  

ポリシーを使用して、クラウドでのユーザーの動作を定義できます。 ポリシーを使用して、危険な動作、違反、またはクラウド環境内の疑わしいデータ ポイントやアクティビティを検出します。 必要に応じて、ポリシーを使用して修復プロセスを統合し、完全なリスクの軽減を実現することができます。 ポリシーの種類は、収集するクラウド環境の情報の種類や、実行する修復アクションの種類に関連付けられています。  

## <a name="related-videos"></a>関連ビデオ

- [セキュリティ コミュニティに参加する](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)

## <a name="next-steps"></a>次の手順  

基本については、「[Cloud App Security の使用を開始する](getting-started-with-cloud-app-security.md)」をご覧ください。    

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)   
