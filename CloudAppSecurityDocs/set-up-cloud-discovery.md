---
title: Cloud Discovery のデプロイ-Cloud App Security |Microsoft Docs
description: この記事では、Cloud Discovery 機能を取得するためのセットアップ手順について説明します。
author: shsagir
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: conceptual
ms.date: 8/15/2019
ms.collection: M365-security-compliance
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fe21bbb39b52981d7aeba0839367d2fd54073983
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285686"
---
# <a name="set-up-cloud-discovery"></a>Cloud Discovery の設定

*適用対象: Microsoft Cloud App Security*

Cloud Discovery は、16000を超えるクラウドアプリの Microsoft Cloud App Security のクラウドアプリカタログに対するトラフィックログを分析します。 これらのアプリは、80以上のリスク要因に基づいてランク付けおよびスコア付けされ、クラウドの使用状況を継続的に可視化し、シャドウ IT を組織にもたらすリスクシャドウを提供します。

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>スナップショットおよび継続的なリスク評価レポート

生成できるレポートには、次の2種類があります。

- **[スナップショットレポート]** -ファイアウォールとプロキシから手動でアップロードするトラフィックログのセットに対するアドホックな可視性を提供します。

- **継続的なレポート**-Cloud App Security を使用してネットワークから転送されるすべてのログを分析します。 これらの機能により、すべてのデータの可視性が向上し、異常検出エンジンを使用して Machine Learning、または定義したカスタムポリシーを使用して、異常な使用を自動的に識別できます。 これらのレポートは、次の方法で接続することによって作成できます。

  - [Microsoft DEFENDER ATP 統合](wdatp-integration.md): Cloud App Security を Microsoft Defender Advanced Threat PROTECTION (ATP) にネイティブに統合することにより、Cloud Discovery のロールアウトを簡素化し、企業ネットワークを超えて Cloud Discovery 機能を拡張し、コンピューターベースの調査を可能にします。
  - [ログコレクター](discovery-docker.md): ログコレクターを使用すると、ネットワークからのログのアップロードを簡単に自動化できます。 ログ コレクターをネットワーク上で実行すると、Syslog または FTP でログを受け取ります。
  - [Zscaler 統合](zscaler-integration.md): Cloud App Security と Zscaler の両方を使用する場合は、2つの製品を統合して、セキュリティ Cloud Discovery のエクスペリエンスを向上させることができます。 Cloud App Security と Zscaler を一緒に使用すると、Zscaler ポータルで直接、承認されていないアプリの自動的なブロック、およびリスク評価をシームレスに Cloud Discovery 展開できます。
  - [iboss](iboss-integration.md)との統合: Cloud App Security と iboss の両方を使用する場合、2つの製品を統合して、セキュリティ Cloud Discovery のエクスペリエンスを向上させることができます。 また、Cloud App Security と iboss が連携して、Cloud Discovery のシームレスなデプロイ、承認されていないアプリの自動ブロック、および iboss ポータルでのリスク評価を直接行うことができます。

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>ログプロセスフロー: 生データからリスク評価まで

リスク評価を生成するプロセスは、次の手順で構成されています。 処理されるデータの量によっては、処理に数分から数時間かかります。

- **アップロード**–ネットワークからの Web トラフィックログがポータルにアップロードされます。

- **Parse** – Cloud App Security は、データソースごとに専用のパーサーを使用して、トラフィックログからトラフィックデータを解析し、抽出します。

- **分析**–トラフィックデータは、クラウドアプリカタログに対して分析され、16000を超えるクラウドアプリを識別し、そのリスクスコアを評価します。 アクティブなユーザーと IP アドレスも分析の一部として識別されます。

- **レポートの生成**-ログファイルから抽出されたデータのリスク評価レポートが生成されます。

>[!NOTE]
> 継続的なレポートデータは1日に2回分析されます。

## サポートされているファイアウォールとプロキシ<a name="supported-firewalls-and-proxies"></a>

- Barracuda-Web アプリファイアウォール (W3C)
- Blue コートプロキシ SG-アクセスログ (W3C)
- Check Point
- FirePOWER を使用した Cisco ASA
- Cisco ASA Firewall (Cisco ASA ファイアウォールの場合は、情報レベルを6に設定する必要があります)
- Cisco Cloud Web Security
- Cisco FWSM
- Cisco IronPort WSA
- Cisco のはがき– Url ログ
- Clavister (Syslog)
- ContentKeeper
- デジタルアート i-フィルター
- Forcepoint
- Fortinet Fortinet
- iboss のセキュリティで保護されたクラウドゲートウェイ
- Juniper SRX
- Juniper SSG
- McAfee Secure Web ゲートウェイ
- Microsoft Forefront Threat Management Gateway (W3C)
- Palo Alto シリーズファイアウォール
- Sonicwall (旧 Dell)
- Sophos SG
- Sophos XG
- Sophos Cyberoam
- Squid (共通)
- Squid (ネイティブ)
- Stormshield
- Websense-Web Security Solutions-調査の詳細レポート (CSV)
- Websense-Web Security Solutions-インターネットアクティビティログ (CEF)
- Zscaler

> [!NOTE]
> Cloud Discovery では、IPv4 と IPv6 の両方のアドレスがサポートされます。

ログがサポートされていない場合は、**データソース**として **[その他]** を選択し、アップロードしようとしているアプライアンスとログを指定します。 ログは Cloud App Security クラウドアナリストチームによって確認されます。ログの種類のサポートが追加されると、通知が表示されます。 または、書式に一致するカスタムパーサーを定義することもできます。 詳細については、「[カスタムログパーサーの使用](custom-log-parser.md)」を参照してください。

データ属性 (ベンダーのドキュメントによる):

| データ ソース | ターゲットアプリの URL | ターゲットアプリの IP | Username | 配信元 IP | 合計トラフィック | アップロードされたバイト数 |
|----------------------------------------------|----------------------|----------------------|----------------------|----------------------|----------------------|----------------------|
| Barracuda | **○** | **○** | **○** | **○** | いいえ | いいえ |
| 青コート | **○** | いいえ | **○** | **○** | **○** | **○** |
| チェックポイント | いいえ | **○** | いいえ | **○** | いいえ | いいえ |
| Cisco ASA (Syslog) | いいえ | **○** | いいえ | **○** | **○** | いいえ |
| FirePOWER を使用した Cisco ASA | **○** | **○** | **○** | **○** | **○** | **○** |
| Cisco Cloud Web Security |**○**|**○**|**○**|**○**|**○**|**○**|
| Cisco FWSM | いいえ | **○** | いいえ | **○** | **○** | いいえ |
| Cisco Ironport WSA | **○** | **○** | **○** | **○** | **○** | **○** |
| Cisco のおアキ | **○** | **○** | いいえ | **○** | いいえ | いいえ |
| Clavister (Syslog) | **○** | **○** | **○** | **○** | **○** | **○** |
| ContentKeeper | **○** | **○** | **○** | **○** | **○** | **○** |
| SonicWall (旧 Dell) | **○** | **○** | いいえ | **○** | **○** | **○** |
| デジタルアート i-フィルター | **○** | **○** | **○** | **○** | **○** | **○** |
| ForcePoint LEEF |**○**|**○**|**○**|**○**|**○**|**○**|
| ForcePoint Web セキュリティクラウド |**○**|**○**|**○**|**○**|**○**|**○**|
| Fortigate | いいえ | **○** | いいえ | **○** | **○** | **○** |
| Fortinet Fortinet |**○**|**○**|いいえ|**○**|**○**|**○**|
| iboss |**○**|**○**|**○**|**○**|**○**|**○**|
| Juniper SRX | いいえ | **○** | いいえ | **○** | **○** | **○** |
| Juniper SSG | いいえ | **○** | **○** | **○** | **○** | **○** |
| McAfee SWG | **○** | いいえ | いいえ | **○** | **○** | **○** |
| MS TMG | **○** | いいえ | **○** | **○** | **○** | **○** |
| Palo Alto Networks | いいえ | **○** | **○** | **○** | **○** | **○** |
| Sophos | **○** | **○** | **○** | **○** | **○** | いいえ |
| Squid (共通) | **○** | いいえ | **○** | **○** | いいえ | **○** |
| Squid (ネイティブ) | **○** | いいえ | **○** | **○** | いいえ | **○** |
| Stormshield | いいえ | **○** | **○** | **○** | **○** | **○** |
| Websense-調査の詳細レポート (CSV) | **○** | **○** | **○** | **○** | **○** | **○** |
| Websense-インターネットアクティビティログ (CEF) | **○** | **○** | **○** | **○** | **○** | **○** |
| Zscaler | **○** | **○** | **○** | **○** | **○** | **○** |

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [継続的なレポートのために自動ログ アップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)
