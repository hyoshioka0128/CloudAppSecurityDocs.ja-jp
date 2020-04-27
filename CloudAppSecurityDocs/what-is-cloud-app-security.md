---
title: Cloud App Security とは
description: この記事では、Microsoft Cloud App Security とそのしくみについて説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/15/2019
ms.topic: overview
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: d46756b1-7dd8-4190-9799-3a97688f1266
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 49ecd0d844dd30c4816095686a353c301df4fa49
ms.sourcegitcommit: 0b929f7c8feed7dfb40d5294179fd5c6fc079614
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "74720454"
---
# <a name="microsoft-cloud-app-security-overview"></a>Microsoft Cloud App Security の概要

*適用対象:Microsoft Cloud App Security*

> [!NOTE]
> Office 365 Cloud App Security については、「[Office 365 Cloud App Security の概要](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)」を参照してください。

クラウドに移行することで、従業員と IT の柔軟性が共に向上します。 ただし、組織のセキュリティを確保するための新しい課題と複雑さも伴います。 クラウド アプリとサービスの利点を最大限に活用するために、IT チームは重要なデータを保護するための制御を維持しつつ、バランスよくアクセスを許可する必要があります。

Microsoft Cloud App Security は、ログの収集、API コネクタ、リバース プロキシなど、さまざまな展開モードをサポートする Cloud Access Security Broker です。 お使いの Microsoft およびサード パーティ製クラウド サービス全体にわたるサイバー攻撃の脅威を特定し、対処するために、豊富な表示機能、データ送受信の制御、高度な分析を備えています。

Microsoft Cloud App Security は、Microsoft の主要なソリューションとネイティブに統合され、セキュリティの専門家向けに設計されています。 シンプルな展開、一元化された管理、革新的な自動化の機能を備えています。

ライセンスの詳細については、「[Microsoft Cloud App Security ライセンス データシート](https://aka.ms/mcaslicensing)」を参照してください。

## <a name="the-cloud-app-security-framework"></a>Cloud App Security のフレームワーク

- **シャドウ IT の使用を検出し、制御する**:組織で使われているクラウド アプリ、IaaS、および PaaS サービスを特定します。 使用状況パターンを調査し、16,000 を超える SaaS アプリのリスク レベルとビジネス準備状態を、80 を超えるリスクに対して評価します。 それらの管理を開始して、セキュリティとコンプライアンスを確保しましょう。

- **クラウド全体で機密情報を保護する**:保存されている機密情報の公開範囲を把握し、分類し、保護します。 すぐに使えるポリシーと自動化されたプロセスを活用して、クラウド アプリ全体をリアルタイムで制御します。

- **サイバー攻撃の脅威と異常に対する保護**:クラウド アプリ全体で異常な動作を検出し、ランサムウェア、侵害されたユーザー、または悪質なアプリケーションを特定します。危険度の高い使用を分析して自動的に修復し、組織へのリスクを制限します。

- **クラウド アプリのコンプライアンスを評価する**:お客様のクラウド アプリが、法規制や業界標準など、関連するコンプライアンス要件を満たしているかどうか評価します。 非準拠アプリへのデータ漏洩を防ぎ、規制対象となるデータへのアクセスを制限します。

## <a name="architecture"></a>アーキテクチャ

Cloud App Security では、次の方法で可視性とクラウドが統合されます。

- Cloud Discovery を使用して、組織が使用しているクラウド環境とクラウド アプリをマップおよび識別します。
- クラウド内のアプリを承認および却下します。
- プロバイダー API を利用する、展開が簡単なアプリ コネクタを使用して、接続先のアプリの可視性とガバナンスを実現します。
- アプリの条件付きアクセス制御保護を使用して、クラウド アプリ内のアクセスとアクティビティをリアルタイムで可視化し、制御します。
- ポリシーを設定し、継続的に微調整することによって、継続的な制御を実現します。

![Cloud App Security アーキテクチャの図](media/proxy-architecture.png)

### <a name="data-retention--compliance"></a>データ保有期間とコンプライアンス

Microsoft Cloud App Security のデータ保有期間とコンプライアンスの詳細については、「[Microsoft Cloud App Security のデータ セキュリティとプライバシー](cas-compliance-trust.md)」を参照してください。

### <a name="cloud-discovery"></a>Cloud Discovery

Cloud Discovery では、トラフィック ログを使用して、組織が使用しているクラウド アプリが動的に検出されて分析されます。 組織のクラウドで使用されているスナップショット レポートを作成するには、ファイアウォールまたはプロキシからログ ファイルを手動でアップロードして分析できます。 継続的なレポートを設定するには、Cloud App Security ログ コレクターを使用して、ログを定期的に転送します。

Cloud Discovery の詳細については、「[Cloud Discovery の設定](set-up-cloud-discovery.md)」を参照してください。

### <a name="sanctioning-and-unsanctioning-an-app"></a>アプリの承認と却下

Cloud App Security を使用すると、*クラウド アプリ カタログ*を使用して、組織内のアプリを承認または却下することができます。 Microsoft のアナリスト チームは、業界標準に基づいてランク付けおよびスコア付けされる、16,000 を超えるクラウド アプリのカタログを広範囲にわたって継続的に拡大しています。 クラウド アプリ カタログを使用して、規制機関認定、業界標準、ベスト プラクティスに基づいて、クラウド アプリのリスクを評価できます。 次に、組織のニーズに合わせてさまざまなパラメーターのスコアと重みをカスタマイズします。 これらのスコアに基づいて、Cloud App Security によってアプリの危険性を知ることができます。 スコアリングは、環境に影響を与える可能性がある 80 以上のリスク要因に基づきます。

### <a name="app-connectors"></a>アプリ コネクタ

アプリ コネクタでは、クラウド アプリ プロバイダーの API を使用して、Cloud App Security クラウドが他のクラウド アプリと統合されます。 アプリ コネクタにより、制御と保護が拡張されます。 また、これにより、Cloud App Security 分析のためにクラウド アプリから直接情報にアクセスすることもできます。

アプリを接続して保護を拡張するために、アプリ管理者は Cloud App Security に対してアプリへのアクセスを承認します。 次に、Cloud App Security により、アプリに対してアクティビティ ログに関するクエリが行われ、データ、アカウント、およびクラウド コンテンツがスキャンされます。 Cloud App Security では、ポリシーを適用し、脅威を検出し、問題を解決するためのガバナンス アクションを提供することができます。

Cloud App Security では、クラウド プロバイダーによって提供される API が使用されます。 各アプリには、独自のフレームワークと API の制限事項があります。 API の使用を最適化するために Cloud App Security とアプリ プロバイダーとの連携が行われ、最適なパフォーマンスが実現されます。 Cloud App Security エンジンでは、アプリによって API に適用されるさまざまな制限事項 (調整、API の制限、動的なタイムシフト API の期間など) を考慮して、許容される容量が利用されます。 テナント内のすべてのファイルのスキャンなどの一部の操作では、多数の API が必要になるため、長期間にわたって分散されます。 ポリシーによっては、数時間または数日間にわたって実行される場合があります。

### <a name="conditional-access-app-control-protection"></a>アプリの条件付きアクセス制御の保護

Microsoft Cloud App Security のアプリの条件付きアクセス制御では、リバース プロキシ アーキテクチャを使用して、クラウド環境内で実行されるアクティビティへのアクセスをリアルタイムで把握して制御するために必要なツールが提供されます。 アプリの条件付きアクセス制御を使用すると、組織を保護することができます。

- ダウンロードが発生する前にブロックすることでデータ リークを回避する
- クラウドに格納され、クラウドからダウンロードされたデータを暗号化で保護するように強制する規則を設定する
- 管理されていないデバイスで何が行われているかを監視できるように、保護されていないエンドポイントを可視化する
- 企業以外のネットワークまたは危険な IP アドレスからのアクセスを制御する

### <a name="policy-control"></a>ポリシー コントロール

ポリシーを使用して、クラウドでのユーザーの行動を定義できます。 ポリシーを使用して、クラウド環境内の危険な動作、違反、疑わしいデータ ポイントやアクティビティを検出します。 必要に応じて、ポリシーを使用して修復プロセスを統合し、完全なリスク軽減を達成できます。 ポリシーの種類は、クラウド環境について収集する情報の種類と、実行する可能性のある修復アクションの種類に関連しています。

## <a name="related-videos"></a>関連ビデオ

- [セキュリティ コミュニティに参加する](https://channel9.msdn.com/Shows/Microsoft-Security/Join-the-Security-Community)

## <a name="next-steps"></a>次のステップ

基本については、「[Cloud App Security の使用を開始する](getting-started-with-cloud-app-security.md)」をご覧ください。

[!INCLUDE [Open support ticket](includes/support.md)] にする必要があります。
