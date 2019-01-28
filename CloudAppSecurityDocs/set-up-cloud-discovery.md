---
title: Cloud Discovery をデプロイする - Cloud App Security | Microsoft Docs
description: この記事では、Cloud Discovery を稼働させるためのセットアップ手順について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/27/2019
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 8a59316b3a2a6aef42a161e70dd0705ab5708911
ms.sourcegitcommit: c24732bc40350c3cf416640b7d15f3c6f7be371d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2019
ms.locfileid: "55086166"
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



## サポートされているファイアウォールとプロキシ <a name="supported-firewalls-and-proxies"></a>

- Barracuda - Web App Firewall (W3C)
- Blue Coat Proxy SG - Access ログ (W3C)
- Check Point
- Cisco ASA Firewall (Cisco ASA Firewall では、情報レベルを 6 に設定する必要があります)
- Cisco ASA with FirePOWER
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki - URL ログ
- Clavister NGFW (Syslog)
- Digital Arts i-FILTER
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Palo Alto Firewall シリーズ
- Sonicwall (旧称 Dell)
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (共通)
- Squid (ネイティブ)
- Websense - Web Security Solutions - 調査の詳細レポート (CSV)
- Websense - Web Security Solutions - インターネットのアクティビティ ログ (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery では、IPv4 と IPv6 の両方のアドレスをサポートします。

ログがサポートされていない場合は、**データ ソース**として **[その他]** を選択し、アップロードしようとしているアプライアンスおよびログを指定します。 ログは Cloud App Security クラウド アナリスト チームによって確認され、要求したログの種類のサポートが追加されるかどうかが通知されます。 また、書式に合うカスタム パーサーを定義することもできます。 詳細については、「[カスタム ログ パーサーの使用](custom-log-parser.md)」を参照してください。


データ属性 (ベンダーのドキュメントに従う)


|                 [データ ソース]                  |    ターゲット アプリの URL    |    ターゲット アプリの IP     |       Username       |      配信元 IP       |    総トラフィック     |    アップロードされたバイト数    |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
|                  Barracuda                   | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |          いいえ          |          いいえ          |
|                  Blue Coat                   | <strong>はい</strong> |          いいえ          | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|                  Checkpoint                  |          いいえ          | <strong>はい</strong> |          いいえ          | <strong>はい</strong> |          いいえ          |          いいえ          |
|              Cisco ASA (Syslog)              |          いいえ          | <strong>はい</strong> |          いいえ          | <strong>はい</strong> | <strong>はい</strong> |          いいえ          |
|           Cisco ASA with FirePOWER           | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|                  Cisco FWSM                  |          いいえ          | <strong>はい</strong> |          いいえ          | <strong>はい</strong> | <strong>はい</strong> |          いいえ          |
|              Cisco IronPort WSA              | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|                 Cisco Meraki                 | <strong>はい</strong> | <strong>はい</strong> |          いいえ          | <strong>はい</strong> |          いいえ          |          いいえ          |
|           Clavister NGFW (Syslog)            | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|                SonicWall (旧称 Dell)                | <strong>はい</strong> | <strong>はい</strong> |          いいえ          | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|            Digital Arts i-FILTER             | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|                  Fortigate                   |          いいえ          | <strong>はい</strong> |          いいえ          | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|                 Juniper SRX                  |          いいえ          | <strong>はい</strong> |          いいえ          | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|                 Juniper SSG                  |          いいえ          | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|                  McAfee SWG                  | <strong>はい</strong> |          いいえ          |          いいえ          | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|                    MS TMG                    | <strong>はい</strong> |          いいえ          | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|              Palo Alto Networks              |          いいえ          | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|                    Sophos                    | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |          いいえ          |
|                Squid (共通)                | <strong>はい</strong> |          いいえ          | <strong>はい</strong> | <strong>はい</strong> |          いいえ          | <strong>はい</strong> |
|                Squid (ネイティブ)                | <strong>はい</strong> |          いいえ          | <strong>はい</strong> | <strong>はい</strong> |          いいえ          | <strong>はい</strong> |
| Websense: 調査の詳細レポート (CSV) | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|    Websense: インターネットのアクティビティ ログ (CEF)    | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
|                   Zscaler                    | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
     


## <a name="next-steps"></a>次の手順

[Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

[継続的なレポートのために自動ログ アップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)

[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)