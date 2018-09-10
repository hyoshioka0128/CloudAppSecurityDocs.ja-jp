---
title: Microsoft Cloud App Security で Cloud Discovery をデプロイする | Microsoft Docs
description: このトピックでは、Cloud Discovery を稼働するためのセットアップ手順について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/15/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 805cb008b60d3ab74119d15e4e24944fe82c8bd7
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144518"
---
*適用対象: Microsoft Cloud App Security*


# <a name="set-up-cloud-discovery"></a>Cloud Discovery のセットアップ
Cloud Discovery は、16,000 を超えるクラウド アプリの 70 以上のリスク要因がランクおよびスコア付けされた Microsoft Cloud App Security のクラウド アプリ カタログに対し、トラフィック ログ解析を実行します。これにより、クラウドの使用状況、シャドウ IT の状況、およびシャドウ IT の組織に対するリスクを継続して把握できるようになります。

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>スナップショットと継続的なリスク評価レポート 

次の 2 種類のレポートを生成できます。 
- **スナップショット レポート**は、ファイアウォールやプロキシから手動でアップロードするトラフィック ログのセットに対するアドホックな可視性を提供します。

- **継続レポート**は、Cloud App Security のログ コレクターを使用してネットワークから転送されるすべてのログを解析します。 これらにより、すべてのデータの可視性が高まり、Machine Learning 異常検出エンジンまたは定義したカスタム ポリシーが使用され、特異な使用を自動的に検出できるようになります。

## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>ログのプロセス フロー: 生データからリスク評価まで  
リスク評価を生成するプロセスは次の手順で行うことができ、処理対象のデータ量によって数分間から数時間かかります。  

-   **アップロード** – ネットワークの Web トラフィック ログがポータルにアップロードされます。  

-   **解析** – Cloud App Security で、トラフィック ログからトラフィック データが抽出され、データ ソースごとに専用のパーサーを使用して解析されます。  

-   **分析** – トラフィック データをクラウド アプリ カタログと比較して分析することで、16,000 以上のクラウド アプリを識別できるほか、アプリのリスク スコアの評価もできます。 アクティブ ユーザーと IP アドレスも、分析の一環として識別されます。  

-   **レポートの生成** – ログ ファイルから抽出されたデータのリスク評価レポートが生成されます。   


>[!NOTE]
>- 継続的なレポート データは 1 日に 2 回分析されます。
>- データはアップロードされる前に、ログ コレクターによって圧縮されます。 ログ コレクターの送信トラフィックは、ログ コレクターが受信するトラフィック ログのサイズの 10% となります。 

## <a name="using-traffic-logs-for-cloud-discovery"></a>Cloud Discovery のトラフィック ログを使用する
Cloud Discovery はトラフィック ログ内のデータを使用します。 ログが詳細であるほど、可視性は高まります。 Cloud Discovery では、次の属性の Web トラフィック データを必要とします。
- トランザクションの日付
- Source IP
- ソース ユーザー: 推奨
- 宛先 IP アドレス
- 宛先 URL **推奨** (URL は IP アドレスよりも、クラウド アプリを正確に検出します)
- データ総量 (データ情報は重要)
- アップロードおよびダウンロードされたデータの量 (クラウド アプリの使用状況のパターンを知ることができます)
- 実行したアクション (許可/ブロック)

Cloud Discovery は、ログに含まれていない属性の表示や分析はできません。
たとえば、**Cisco ASA Firewall** の標準のログ形式には、**トランザクションごとにアップロードされるバイト数**も**ユーザー名**も含まれず、**ターゲット URL** も含みません (ターゲット IP は含みます)。
そのため、これらの属性はこれらのログの Cloud Discovery データに表示されず、クラウド アプリの可視性は制限されます。 Cisco ASA Firewall では、情報レベルを 6 に設定する必要があります。 


Cloud Discovery レポートを正しく生成するには、トラフィック ログで次の要件を満たしている必要があります。
1.  データ ソースがサポートされている (次の一覧を参照)。
2.  ログの形式が期待されている標準の形式と一致する (これはログ ツールのアップロードで確認されます)。
3.  イベントが 90 日以上経過していない。
4.  ログ ファイルが有効で、送信トラフィック情報を含む。



## サポートされているファイアウォールとプロキシ <a name="supported-firewalls-and-proxies"></a>

- Barracuda - Web App Firewall (W3C)
- Blue Coat Proxy SG - Access ログ (W3C)
- Check Point
- Cisco ASA Firewall (Cisco ASA Firewall では情報レベルを 6 に設定する必要があります)
- Cisco ASA with FirePOWER
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki - URL ログ
- Clavister NGFW (Syslog)
- Dell SonicWall
- Digital Arts i-FILTER
- Fortinet Fortigate
- iboss Secure Cloud Gateway
- Juniper SRX
- Juniper SSG
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Palo Alto Firewall シリーズ
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

ログがサポートされていない場合は、**データ ソース**に **[その他]** を選択し、アップロードしようとしているアプライアンスおよびログを指定します。 ログは確認され、Cloud App Security のクラウド アナリスト チームによって要求したログの種類が追加されるかどうかが通知されます。 また、書式に合うカスタム パーサーを定義することもできます。 詳細については、「[カスタム ログ パーサーの使用](custom-log-parser.md)」を参照してください。


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
|                Dell SonicWall                | <strong>はい</strong> | <strong>はい</strong> |          いいえ          | <strong>はい</strong> | <strong>はい</strong> | <strong>はい</strong> |
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

## <a name="see-also"></a>「

[Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

[継続的なレポートのために自動ログ アップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)

[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)