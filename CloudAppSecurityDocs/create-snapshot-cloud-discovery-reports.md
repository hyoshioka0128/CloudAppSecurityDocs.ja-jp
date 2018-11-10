---
title: Cloud Discovery クラウド アプリの使用に関するスナップショット レポートの作成 | Microsoft ドキュメント
description: この記事では、ログを手動でアップロードして Cloud Discovery アプリのスナップショット レポートを作成する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/29/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 82193845bffa1f88f69eef035dbcc20dbb2da40b
ms.sourcegitcommit: bb010d8dd0a6eff39df31e33c2cc9c37ec321b46
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2018
ms.locfileid: "50217392"
---
*適用対象: Microsoft Cloud App Security*


# <a name="create-snapshot-cloud-discovery-reports"></a>Cloud Discovery のスナップショット レポートを作成する
自動ログ コレクターの使用を試みる前に、手動でログをアップロードし、Microsoft Cloud App Security でログ解析することが重要です。 ログ コレクターのしくみと予想されるログの形式については、「[Cloud Discovery に対するトラフィック ログの使用](#log-format)」をご覧ください。

ログがまだない状態で、ログの表示例を確認する場合は、サンプル ログ ファイルをダウンロードします。 ログがどのように表示されるかを確認するには、以下の手順に従います。


スナップショット レポートを作成するには:
  
1. 組織のユーザーがインターネット アクセスに使用するファイアウォールとプロキシからログ ファイルを収集します。 組織内のすべてのユーザー アクティビティを示す、トラフィック ピーク時のログを収集するようにしてください。  
  
2. Cloud App Security ポータルで、**[探索]**、**[スナップショット レポートの作成]** の順にクリックします。  
  
   ![新しいスナップショット レポートを作成する](./media/create-new-snapshot-report.png)
     
3. **[レポート名]** と **[説明]** を入力します。
  
    ![新しいスナップショット レポート](./media/new-snapshot-report.png) 

4. ログ ファイルのアップロード元にする **[データソース]** を選択します。  
  
5. ログの形式を調べ、ダウンロードできるサンプル ログに従ってログが正しく書式設定されているかどうかを確認します。 **[View and verify]\(表示して確認\)**、**[サンプル ログのダウンロード]** の順にクリックします。 自分のログとサンプルを比較し、互換性があることを確認します。 

   ![ログの書式を確認する](./media/cloud-discovery-snapshot-verify.png)  

   > [!NOTE]
   > FTP サンプル形式はスナップショットと自動アップロードでサポートされています。一方、syslog は自動アップロードでのみサポートされています。<br></br>
   サンプル ログのダウンロードを実行すると、サンプル FTP ログがダウンロードされます。


6. アップロードする**トラフィック ログを選択**します。 一度に最大 20 個のファイルをアップロードできます。 圧縮された ZIP 形式のファイルもサポートされます。  
  
7. **[作成]** をクリックします。  

8. アップロードが完了すると、ログが正常にアップロードされたことを通知するステータス メッセージが画面右上隅に表示されます。  
  
9. ログ ファイルのアップロード後、ファイルの解析および分析には多少時間がかかります。  
   ログ ファイルの処理が完了した後、終了したことを通知する電子メールを受け取ります。 
  
10. **Cloud Discovery ダッシュボード**の上部にあるステータス バーに通知バナーが表示されます。 バナーは、自分のログ ファイルの処理状態で更新されます。  
    ![ログ ファイル メニュー バーの処理](./media/processing-log-file-menu-bar.png) 
   
11. ログが正常にアップロードされると、ログ ファイルの処理が正常に完了したことを知らせる通知が表示されます。 この時点で、ステータス バーのリンクをクリックするか、設定の歯車アイコンに移動して **[Cloud Discovery の設定]** を選択することで、レポートを表示できます。   
  
     ![Discovery の [設定] タブ](./media/discovery-settings-tab.png)
12. **[スナップショット レポート]** を選択し、スナップショット レポートを選択します。
 
     ![スナップショット レポートの管理](./media/snapshot-report-managment.png)

  
## Cloud Discovery に対するトラフィック ログの使用 <a name="log-format"></a>
Cloud Discovery では、トラフィック ログ内のデータが使用されます。 ログが詳細であるほど、可視性は高まります。 Cloud Discovery では、次の属性の Web トラフィック データを必要とします。
- トランザクションの日付
- Source IP
- ソース ユーザー: 推奨
- 宛先 IP アドレス
- 宛先 URL **推奨** (URL は IP アドレスよりも、クラウド アプリを正確に検出します)
- データ総量 (データ情報は重要)
- アップロードおよびダウンロードされたデータの量 (クラウド アプリの使用状況のパターンを知ることができます)
- 実行したアクション (許可/ブロック)

Cloud Discovery で、ログに含まれていない属性の表示や分析はできません。
たとえば、**Cisco ASA Firewall** の標準のログ形式には、**トランザクションごとにアップロードされるバイト数**、**ユーザー名**、**ターゲット URL** (ターゲット IP のみ) は含まれません。
そのため、これらの属性はこれらのログの Cloud Discovery データに表示されず、クラウド アプリの可視性は制限されます。 Cisco ASA Firewall では、情報レベルを 6 に設定する必要があります。 


Cloud Discovery レポートを正しく生成するには、トラフィック ログで次の要件を満たす必要があります。
1. データ ソースがサポートされている (次の一覧を参照)。
2. ログの形式が期待されている標準の形式と一致する (形式はログ ツールのアップロードで確認されます)。
3. イベントが 90 日以上経過していない。
4. ログ ファイルが有効で、送信トラフィック情報を含む。



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
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
    
      
  