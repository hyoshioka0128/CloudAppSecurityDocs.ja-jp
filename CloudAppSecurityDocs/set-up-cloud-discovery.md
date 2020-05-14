---
title: Cloud Discovery をデプロイする - Cloud App Security | Microsoft Docs
description: この記事では、Cloud Discovery を稼働させるためのセットアップ手順について説明します。
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 8/15/2019
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a4ee042c3f24fe2fa5f15fa5ce3eb2ca0f7f2be1
ms.sourcegitcommit: a693d0bc9102a8320f9933d80ab9357f449d5316
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83369327"
---
# <a name="set-up-cloud-discovery"></a>Cloud Discovery の設定

*適用対象:Microsoft Cloud App Security*

Cloud Discovery では、16,000 以上のクラウド アプリを掲載した Microsoft Cloud App Security のクラウド アプリ カタログに照らしてトラフィック ログが分析されます。 これらのアプリは、80以上のリスク要因に基づいてランク付けおよびスコア付けされ、クラウドの使用状況を継続的に可視化し、シャドウ IT を組織にもたらすリスクシャドウを提供します。

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>スナップショットと継続的なリスク評価レポート

次の 2 種類のレポートを生成できます。

- **スナップショット レポート**: ファイアウォールやプロキシから手動でアップロードするトラフィック ログのセットに対するアドホックな可視性を提供します。

- **継続レポート**: Cloud App Security を使用してネットワークから転送されるすべてのログを分析します。 これらにより、すべてのデータの可視性が高まり、Machine Learning 異常検出エンジンまたは定義したカスタム ポリシーが使用され、特異な使用を自動的に検出できるようになります。 これらのレポートは、次の方法で接続することにより作成できます。

  - [Microsoft DEFENDER ATP 統合](wdatp-integration.md): Cloud App Security を Microsoft Defender Advanced Threat PROTECTION (ATP) にネイティブに統合することにより、Cloud Discovery のロールアウトを簡素化し、企業ネットワークを超えて Cloud Discovery 機能を拡張し、コンピューターベースの調査を可能にします。
  - [ログ コレクター](discovery-docker.md): ログ コレクターを使用すると、ネットワークからのログのアップロードを簡単に自動化することができます。 ログ コレクターをネットワーク上で実行すると、Syslog または FTP でログを受け取ります。
  - [Zscaler 統合](zscaler-integration.md): Cloud App Security と Zscaler の両方を使用する場合、2 つの製品を統合することでセキュリティの Cloud Discovery エクスペリエンスを強化することができます。 さらに Cloud App Security と Zscaler には、Cloud Discovery のシームレスなデプロイ、承認されていないアプリの自動ブロック、Zscaler ポータルでの直接のリスク評価が備わっています。
  - [iboss](iboss-integration.md)との統合: Cloud App Security と iboss の両方を使用する場合、2つの製品を統合して、セキュリティ Cloud Discovery のエクスペリエンスを向上させることができます。 また、Cloud App Security と iboss が連携して、Cloud Discovery のシームレスなデプロイ、承認されていないアプリの自動ブロック、および iboss ポータルでのリスク評価を直接行うことができます。

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>ログのプロセス フロー: 生データからリスク評価まで

リスク評価を生成するプロセスは、次の手順で構成されています。 この処理には、処理されるデータの量に応じて数分から数時間かかります。

- **アップロード** – ネットワークの Web トラフィック ログがポータルにアップロードされます。

- **解析** – Cloud App Security で、トラフィック ログからトラフィック データが抽出され、データ ソースごとに専用のパーサーを使用して解析されます。

- **分析** – トラフィック データをクラウド アプリ カタログと比較して分析することで、16,000 以上のクラウド アプリを識別できるほか、アプリのリスク スコアの評価もできます。 分析の一環として、アクティブ ユーザーと IP アドレスも特定されます。

- **レポートの生成** – ログ ファイルから抽出されたデータのリスク評価レポートが生成されます。

>[!NOTE]
> 継続的レポートのデータは 1 日に 2 回分析されます。

## <a name="supported-firewalls-and-proxies"></a>サポートされているファイアウォールとプロキシ<a name="supported-firewalls-and-proxies"></a>

- Barracuda - Web アプリ ファイアウォール (W3C)
- Blue Coat Proxy SG - アクセス ログ (W3C)
- Check Point
- Cisco ASA with FirePOWER
- Cisco ASA Firewall (Cisco ASA Firewall では、情報レベルを 6 に設定する必要があります)
- Cisco Cloud Web Security
- Cisco FWSM
- Cisco IronPort WSA
- Cisco Meraki - URL ログ
- Clavister NGFW (Syslog)
- ContentKeeper
- Digital Arts i-FILTER
- Forcepoint
- Fortinet FortiGate
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
- Stormshield
- Websense - Web Security Solutions - 調査の詳細レポート (CSV)
- Websense - Web Security Solutions - インターネットのアクティビティ ログ (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery では、IPv4 と IPv6 の両方のアドレスをサポートします。

ログがサポートされていない場合は、**データ ソース**として **[その他]** を選択し、アップロードしようとしているアプライアンスおよびログを指定します。 ログは Cloud App Security クラウド アナリスト チームによって確認され、要求したログの種類のサポートが追加されるかどうかが通知されます。 また、書式に合うカスタム パーサーを定義することもできます。 詳細については、「[カスタム ログ パーサーの使用](custom-log-parser.md)」をご覧ください。

データ属性 (ベンダーのドキュメントに従う)

| データ ソース | ターゲット アプリの URL | ターゲット アプリの IP | ユーザー名 | 配信元 IP | 合計トラフィック | アップロードされたバイト数 |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **はい** | **はい** | **はい** | **はい** | いいえ | いいえ |
| Blue Coat | **はい** | いいえ | **はい** | **はい** | **はい** | **はい** |
| Checkpoint | いいえ | **はい** | いいえ | **はい** | いいえ | いいえ |
| Cisco ASA (Syslog) | いいえ | **はい** | いいえ | **はい** | **はい** | いいえ |
| Cisco ASA with FirePOWER | **はい** | **はい** | **はい** | **はい** | **はい** | **はい** |
| Cisco Cloud Web Security |**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|
| Cisco FWSM | いいえ | **はい** | いいえ | **はい** | **はい** | いいえ |
| Cisco IronPort WSA | **はい** | **はい** | **はい** | **はい** | **はい** | **はい** |
| Cisco Meraki | **はい** | **はい** | いいえ | **はい** | いいえ | いいえ |
| Clavister NGFW (Syslog) | **はい** | **はい** | **はい** | **はい** | **はい** | **はい** |
| ContentKeeper | **はい** | **はい** | **はい** | **はい** | **はい** | **はい** |
| SonicWall (旧称 Dell) | **はい** | **はい** | いいえ | **はい** | **はい** | **はい** |
| Digital Arts i-FILTER | **はい** | **はい** | **はい** | **はい** | **はい** | **はい** |
| ForcePoint LEEF |**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|
| ForcePoint Web セキュリティクラウド |**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|
| FortiGate | いいえ | **はい** | いいえ | **はい** | **はい** | **はい** |
| Fortinet Fortinet |**はい**|**はい**|いいえ|**はい**|**はい**|**はい**|
| iboss |**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|
| Juniper SRX | いいえ | **はい** | いいえ | **はい** | **はい** | **はい** |
| Juniper SSG | いいえ | **はい** | **はい** | **はい** | **はい** | **はい** |
| McAfee SWG | **はい** | いいえ | いいえ | **はい** | **はい** | **はい** |
| MS TMG | **はい** | いいえ | **はい** | **はい** | **はい** | **はい** |
| Palo Alto Networks | いいえ | **はい** | **はい** | **はい** | **はい** | **はい** |
| Sophos | **はい** | **はい** | **はい** | **はい** | **はい** | いいえ |
| Squid (共通) | **はい** | いいえ | **はい** | **はい** | いいえ | **はい** |
| Squid (ネイティブ) | **はい** | いいえ | **はい** | **はい** | いいえ | **はい** |
| Stormshield | いいえ | **はい** | **はい** | **はい** | **はい** | **はい** |
| Websense: 調査の詳細レポート (CSV) | **はい** | **はい** | **はい** | **はい** | **はい** | **はい** |
| Websense - インターネットのアクティビティ ログ (CEF) | **はい** | **はい** | **はい** | **はい** | **はい** | **はい** |
| Zscaler | **はい** | **はい** | **はい** | **はい** | **はい** | **はい** |

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [継続的なレポートのために自動ログ アップロードを構成する](discovery-docker.md)

> [!div class="nextstepaction"]
> [Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)
