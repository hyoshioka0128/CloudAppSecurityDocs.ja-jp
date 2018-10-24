---
title: Microsoft Cloud App Security で Cloud Discovery をデプロイする | Microsoft Docs
description: このトピックでは、Cloud Discovery を稼働するためのセットアップ手順について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/7/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: cbc8999419f9c316323227c515fe111310231a9a
ms.sourcegitcommit: 53a1c990ff06674c26563a9ebcb1979818c3c063
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881807"
---
*適用対象: Microsoft Cloud App Security*


# <a name="set-up-cloud-discovery"></a>Cloud Discovery のセットアップ
Cloud Discovery は、16,000 を超えるクラウド アプリの 70 以上のリスク要因がランクおよびスコア付けされた Microsoft Cloud App Security のクラウド アプリ カタログに対し、トラフィック ログ解析を実行します。これにより、クラウドの使用状況、シャドウ IT の状況、およびシャドウ IT の組織に対するリスクを継続して把握できるようになります。

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>スナップショットと継続的なリスク評価レポート 

次の 2 種類のレポートを生成できます。 
- **スナップショット レポート**は、ファイアウォールやプロキシから手動でアップロードするトラフィック ログのセットに対するアドホックな可視性を提供します。

- **継続レポート**は、Cloud App Security を使用してネットワークから転送されるすべてのログを解析します。 これらにより、すべてのデータの可視性が高まり、Machine Learning 異常検出エンジンまたは定義したカスタム ポリシーが使用され、特異な使用を自動的に検出できるようになります。 これらのレポートは、次の方法で接続することにより作成できます。
  - [Windows Defender ATP 統合](wdatp-integration.md): Cloud App Security は Windows Defender Advanced Threat Protection (ATP) とネイティブに統合して、Cloud Discovery のロールアウトを簡素化し、企業ネットワーク外に Cloud Discovery 機能を拡張し、マシン ベースの調査を可能にします。
  - [ログ コレクター]( ):
  - [Zscaler の統合](zscaler-integration.md): 

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>ログのプロセス フロー: 生データからリスク評価まで  
リスク評価を生成するプロセスは次の手順で行うことができ、処理対象のデータ量によって数分間から数時間かかります。  

-   **アップロード** – ネットワークの Web トラフィック ログがポータルにアップロードされます。  

-   **解析** – Cloud App Security で、トラフィック ログからトラフィック データが抽出され、データ ソースごとに専用のパーサーを使用して解析されます。  

-   **分析** – トラフィック データをクラウド アプリ カタログと比較して分析することで、16,000 以上のクラウド アプリを識別できるほか、アプリのリスク スコアの評価もできます。 アクティブ ユーザーと IP アドレスも、分析の一環として識別されます。  

-   **レポートの生成** – ログ ファイルから抽出されたデータのリスク評価レポートが生成されます。   


>[!NOTE]
>- 継続的なレポート データは 1 日に 2 回分析されます。
> 


## <a name="see-also"></a>「

[Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

[継続的なレポートのために自動ログ アップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)

[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)