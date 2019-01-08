---
title: Cloud Discovery をデプロイする - Cloud App Security | Microsoft Docs
description: この記事では、Cloud Discovery を稼働させるためのセットアップ手順について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0ad041c73f1bb8871e08357e6d85269ef20f3903
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53175908"
---
# <a name="set-up-cloud-discovery"></a>Cloud Discovery のセットアップ

*適用対象:Microsoft Cloud App Security*

Cloud Discovery では、16,000 以上のクラウド アプリを掲載した Microsoft Cloud App Security のクラウド アプリ カタログに照らしてトラフィック ログが分析されます。 このアプリは 70 を超えるリスク要因に基づいてランクおよびスコア付けされ、クラウドの使用状況、シャドウ IT の状況、およびシャドウ IT の組織に対するリスクを継続して把握できるようになります。

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>スナップショットと継続的なリスク評価レポート 

次の 2 種類のレポートを生成できます。 

- **スナップショット レポート**: ファイアウォールやプロキシから手動でアップロードするトラフィック ログのセットに対するアドホックな可視性を提供します。

- **継続レポート**: Cloud App Security を使用してネットワークから転送されるすべてのログを分析します。 これらにより、すべてのデータの可視性が高まり、Machine Learning 異常検出エンジンまたは定義したカスタム ポリシーが使用され、特異な使用を自動的に検出できるようになります。 これらのレポートは、次の方法で接続することにより作成できます。

  - [Windows Defender ATP 統合](wdatp-integration.md): Cloud App Security は Windows Defender Advanced Threat Protection (ATP) とネイティブに統合して、Cloud Discovery のロールアウトを簡素化し、企業ネットワーク外に Cloud Discovery 機能を拡張し、マシン ベースの調査を可能にします。
  - [ログ コレクター](discovery-docker.md):ログ コレクターを使用すると、ネットワークからのログのアップロードを簡単に自動化することができます。 ログ コレクターをネットワーク上で実行すると、Syslog または FTP でログを受け取ります。
  - [Zscaler の統合](zscaler-integration.md):Cloud App Security と Zscaler の両方を使用する場合、2 つの製品を統合することでセキュリティの Cloud Discovery エクスペリエンスを強化することができます。 さらに Cloud App Security と Zscaler には、Cloud Discovery のシームレスなデプロイ、承認されていないアプリの自動ブロック、Zscaler ポータルでの直接のリスク評価が備わっています。

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>ログのプロセス フロー: 生データからリスク評価まで

リスク評価を生成するプロセスは、次の手順で構成されています。 この処理には、処理されるデータの量に応じて数分から数時間かかります。  

- **アップロード** – ネットワークの Web トラフィック ログがポータルにアップロードされます。  

- **解析** – Cloud App Security で、トラフィック ログからトラフィック データが抽出され、データ ソースごとに専用のパーサーを使用して解析されます。  

- **分析** – トラフィック データをクラウド アプリ カタログと比較して分析することで、16,000 以上のクラウド アプリを識別できるほか、アプリのリスク スコアの評価もできます。 アクティブ ユーザーと IP アドレスも、分析の一環として識別されます。  

- **レポートの生成** – ログ ファイルから抽出されたデータのリスク評価レポートが生成されます。


>[!NOTE]
> 継続的なレポート データは 1 日に 2 回分析されます。


## <a name="next-steps"></a>次の手順

[Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

[継続的なレポートのために自動ログ アップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)

[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)