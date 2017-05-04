---
title: "Cloud App Security で Cloud Discovery を展開する | Microsoft Docs"
description: "このトピックでは、Cloud Discovery を稼働するためのセットアップ手順について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/30/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: a9b5bd8d-305b-4e93-9a4c-a4683ea09080
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f9c86d2ce7b45a8de88ebba84ff8608b67117080
ms.sourcegitcommit: 7e9ae94cb4f90fbccaa84f19bdebb4652a425e45
translationtype: HT
---
# <a name="set-up-cloud-discovery"></a>Cloud Discovery のセットアップ
Cloud Discovery は、13,000 を超えるクラウド アプリの 50 以上の属性がランクおよびスコア付けされた Cloud App Security のクラウド アプリ カタログに対し、トラフィック ログ解析を実行します。これにより、クラウドの使用状況、シャドウ IT の状況、およびシャドウ IT の組織に対するリスクを継続して把握できるようになります。
**クラウド アプリ カタログ**では、規制遵守の認定、業界標準、ベスト プラクティスに基づいて、クラウド アプリのリスクをランク付けします。 クラウド アプリ カタログを最新に保つために、次の 4 つの補完的なプロセスが実行されます。
1.    データのクラウド アプリからの自動抽出 (SOC 2 に対する準拠などの属性)。
2.    Cloud App Security のアルゴリズムを使用したデータの高度な自動抽出 (HTTP セキュリティ ヘッダーなどの属性)。
3.    Cloud App Security のアナリスト チームによる継続的な分析 (保存時の暗号化などの属性)。
4.    顧客ベースの変更要求 (クラウド アプリ カタログに対する顧客から送信されてくる変更要求に基づいたもの)。 すべての要求がマイクロソフトのクラウド アナリスト チームによって確認され、検出されたことに基づいて更新が行われます。
  
## <a name="cloud-discovery-data-anonymization"></a>Cloud Discovery データの匿名化

Cloud Discovery データを匿名化することで、ユーザーのプライバシーを保護することができます。 データ ログが Cloud App Security ポータルにアップロードされると、ログはサニタイズされ、すべてのユーザー名情報が暗号化されたユーザー名に置き換えられます。 このように、すべてのクラウド アクティビティの匿名が維持されます。 詳細については、[Cloud Discovery の匿名化](cloud-discovery-anonymizer.md)に関するページを参照してください。

## <a name="snapshot-and-continuous-risk-assessment-reports"></a>スナップショットと継続的なリスク評価レポート 

次の 2 種類のレポートを生成できます。 
- **スナップショット レポート**は、ファイアウォールやプロキシから手動でアップロードするトラフィック ログのセットに対するアドホックな可視性を提供します。
 
- **継続レポート**は、Cloud App Security のログ コレクターを使用してネットワークから転送されるすべてのログを解析します。 これらにより、すべてのデータの可視性が高まり、Machine Learning 異常検出エンジンまたは定義したカスタム ポリシーが使用され、特異な使用を自動的に検出できるようになります。
 
## <a name="log-process-flow-from-raw-data-to-risk-assessment"></a>ログのプロセス フロー: 生データからリスク評価まで  
リスク評価を生成するプロセスは次の手順で行うことができ、処理対象のデータ量によって数分間から数時間かかります。  
  
-   **アップロード** – ネットワークの Web トラフィック ログがポータルにアップロードされます。  
  
-   **解析** – Cloud App Security で、トラフィック ログからトラフィック データが抽出され、データ ソースごとに専用のパーサーを使用して解析されます。  
  
-   **分析** – トラフィック データをクラウド アプリ カタログと比較して分析することで、13,000 以上のクラウド アプリケーションを識別できるほか、アプリケーションのリスク スコアの評価もできます。 アクティブ ユーザーと IP アドレスも、分析の一環として識別されます。  
  
-   **レポートの生成** – ログ ファイルから抽出されたデータのリスク評価レポートが生成されます。   
 
 
>[!NOTE]
>継続的なレポート データは 1 日に 2 回分析されます。
 
## <a name="using-traffic-logs-for--cloud-discovery"></a>Cloud Discovery のトラフィック ログを使用する
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
 
## <a name="supported-firewalls-and-proxies"></a>サポートされているファイアウォールとプロキシ
- Blue Coat Proxy SG - Access ログ (W3C)
- Check Point
- Cisco ASA Firewall (Cisco ASA Firewall では情報レベルを 6 に設定する必要があります)
- Cisco IronPort WSA
- Cisco ScanSafe
- Cisco Meraki - URL ログ
- Dell SonicWall
- Fortinet Fortigate
- Juniper SRX
- McAfee Secure Web Gateway
- Microsoft Forefront Threat Management Gateway (W3C)
- Palo Alto Firewall シリーズ
- Sophos SG
- Sophos Cyberoam
- Squid (共通)
- Squid (ネイティブ)
- Websense - Web Security Solutions - 調査の詳細レポート (CSV)
- Websense - Web Security Solutions - インターネットのアクティビティ ログ (CEF)
- Zscaler


ログがサポートされていない場合は、**データ ソース**に **[その他]** を選択し、アップロードしようとしているアプライアンスおよびログを指定します。 ログは確認され、Cloud App Security のクラウド アナリスト チームによって要求したログの種類が追加されるかどうかが通知されます。 


データ属性 (ベンダーのドキュメントに従う)

|[データ ソース]|ターゲット アプリの URL|ターゲット アプリの IP|Username|配信元 IP|総トラフィック|アップロードされたバイト数|
|----|----|----|-----|----|----|----|
|Blue Coat|**はい**|いいえ|**はい**|**はい**|**はい**|**はい**|
|Checkpoint|いいえ|**はい**|いいえ|**はい**|いいえ|いいえ|
|Cisco ASA|いいえ|**はい**|いいえ|**はい**|**はい**|いいえ|
|Cisco FWSM|いいえ|**はい**|いいえ|**はい**|**はい**|いいえ|
|Cisco IronPort WSA|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|
|Cisco ScanSafe|**はい**|いいえ|**はい**|**はい**|**はい**|**はい**|
|Dell SonicWall|**はい**|**はい**|いいえ|**はい**|**はい**|**はい**|
|Fortigate|いいえ|**はい**|いいえ|**はい**|**はい**|**はい**|
|Juniper SRX|いいえ|**はい**|いいえ|**はい**\*|**はい**|**はい**|
|McAfee SWG|**はい**|いいえ|いいえ|**はい**|**はい**|**はい**|
|Meraki|**はい**|**はい**|いいえ|**はい**|いいえ|いいえ|
|MS TMG|**はい**|いいえ|**はい**|**はい**|**はい**|**はい**|
|Palo Alto Networks|**はい**|**はい**|**はい**|**はい**\*|**はい**|**はい**|
|Sophos|**はい**|**はい**|**はい**|**はい**|**はい**|いいえ|
|Websense: 調査の詳細レポート (CSV)|**はい**|いいえ|いいえ|**はい**|いいえ|いいえ|
|Websense: インターネットのアクティビティ ログ (CEF)|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|
|Zscaler|**はい**|いいえ|**はい**|いいえ|**はい**|**はい**|

\* Cloud Discovery は IPv6 をサポートしています。

## <a name="see-also"></a>関連項目
 
[Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

[継続的なレポートのために自動ログ アップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)

[Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)