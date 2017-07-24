---
title: "Cloud App Security と SIEM の統合 | Microsoft Docs"
description: "このトピックでは、SIEM と Cloud App Security との統合に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/16/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4649423b-9289-49b7-8b60-04b61eca1364
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 09a42f6b767f1924803f99e9a530f58b6fd13358
ms.sourcegitcommit: ae4c8226f6037c5eb286eb27142d6bbb397609e9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2017
---
# <a name="siem-integration"></a>SIEM の統合
    
Cloud App Security と SIEM サーバーを統合し、Office 365 のアラートとアクティビティを一元的に監視できるようになりました。 Office 365 では新しいアクティビティとイベントがサポートされるため、それらの表示が Cloud App Security にロールアウトされます。 SIEM サービスとの統合により、通常のセキュリティ ワークフローを維持し、セキュリティ手順を自動化してクラウドベースのイベントとオンプレミス イベントを関連付けた状態で、クラウド アプリケーションの保護を強化することができます。 Cloud App Security SIEM エージェントはサーバー上で実行され、Cloud App Security からアラートとアクティビティを取得し、SIEM サーバーに送ります。

SIEM を Cloud App Security と初めて統合した場合、過去 2 日間のアクティビティとアラートは SIEM に転送され、以降のすべてのアクティビティとアラートも (選択したフィルターに基づいて) 転送されます。 また、この機能を長期間無効にしてから再び有効にすると、過去 2 日間分とそれ以降のすべてのアラートとアクティビティが転送されます。

## <a name="siem-integration-architecture"></a>SIEM 統合アーキテクチャ

SIEM エージェントは組織のネットワークに展開されます。 展開と構成が行われると、Cloud App Security RESTful API を使用して構成を行ったデータの種類 (アラートとアクティビティ) がプルされます。
ポーリングされるトラフィックはポート 443 の暗号化された HTTPS チャネルを通じて送信されます。

SIEM エージェントは Cloud App Security からデータを取得すると、セットアップ中に指定したネットワーク構成 (TCP または UDP とカスタム ポート) を使用してローカル SIEM に Syslog メッセージを送信します。 

![SIEM 統合アーキテクチャ](./media/siem-architecture.png)



## <a name="how-to-integrate"></a>統合方法

SIEM との統合は次の 3 つの手順で行われます。
1. Cloud App Security ポータルでセットアップします。 
2. JAR ファイルをダウンロードし、サーバーで実行します。
3. SIEM エージェントが動作しているか検証します。

### <a name="prerequisites"></a>前提条件

- 標準的な Windows または Linux サーバー (仮想マシンを使用可)。
- サーバーでは Java 8 を実行する必要があります。これより前のバージョンはサポートされていません。

## <a name="integrating-with-your-siem"></a>SIEM との統合

### <a name="step-1-set-it-up-in-the-cloud-app-security-portal"></a>手順 1: Cloud App Security ポータルでセットアップする

1. Cloud App Security ポータルの設定歯車の下で **[セキュリティ拡張機能]** をクリックし、**[SIEM エージェント]** タブをクリックします。

2. プラス記号アイコンをクリックし、**[SIEM エージェントを追加する]** ウィザードを開始します。
3. ウィザードで、**[SIEM エージェントの追加]** をクリックします。 
4. ウィザードで、名前を入力し、**SIEM 形式を選択**して、その形式に関する**詳細設定**をすべて設定します。 **[次へ]**をクリックします。

   ![SIEM の全般設定](./media/siem1.png)

5. **リモートの Syslog ホスト**の IP アドレスまたはホスト名と **Syslog ポート番号**を入力します。 リモートの Syslog プロトコルとして TCP または UDP を選択します。
これらの詳細がわからない場合は、セキュリティ管理者と協力して取得してださい。
**[次へ]**をクリックします。
  ![リモートの Syslog 設定](./media/siem2.png)

6. SIEM サーバーにエクスポートするデータの種類を選択します。**アラート**と**アクティビティ**があります。 スライダーを使用してこれらを有効および無効にします。既定では、すべて選択されます。 **[適用先]** ドロップダウンを使用して、SIEM サーバーに特定のアラートとアクティビティのみを送信するようにフィルターを設定することができます。
**[結果の編集とプレビュー]** をクリックし、フィルターが予期したとおりに動作していることを確認できます。 **[次へ]**をクリックします。 

  ![データの種類の設定](./media/siem3.png)

7. トークンをコピーし、保存して後で使用できるようにします。 [完了] をクリックし、ウィザードから SIEM ページに戻り、テーブルで追加した SIEM エージェントを確認できます。 後で接続されるまで **[作成済み]** と表示されます。

### <a name="step-2-download-the-jar-file-and-run-it-on-your-server"></a>手順 2: JAR ファイルをダウンロードし、サーバーで実行する

1. [Microsoft Download Center から .zip ファイルをダウンロード](https://go.microsoft.com/fwlink/?linkid=838596)し、解凍します。

2. zip ファイルから .jar ファイルを抽出し、サーバーで実行します。
 ファイルを実行したら、次のように実行します。
    
      java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory DIRNAME] [--proxy ADDRESS[:PORT]] --token TOKEN
> [!NOTE]
> - ファイル名は、SIEM エージェントのバージョンによって異なる場合があります。
> - 角かっこ [] で囲まれたパラメーターは省略可能です。関係する場合にのみ使用してください。

各変数の使用方法:
- DIRNAME は、ローカル エージェント デバッグ ログで使用するディレクトリのパスです。
- ADDRESS[:PORT] は、サーバーがインターネットに接続する際に使用するプロキシ サーバーのアドレスとポートです。
- TOKEN は、前の手順でコピーした SIEM エージェント トークンです。

「-h」と入力すれば、いつでもヘルプを表示できます。

SIEM に送信されるアクティビティ ログのサンプルを次に示します。
```
    2017-07-11T19:14:55.895Z CEF:0|MCAS|SIEM_Agent|0.101.113|EVENT_CATEGORY_LOGIN|Log on|0|externalId=1499800495894_e453bc33-a7c1-48f7-8397-8ae8e2758183 start=1499800495895 end=1499800495895 msg=Log on suser=admin@contoso.com destinationServiceName=Microsoft Exchange Online dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149980022970038514 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499800495894_e453bc33-a7c1-48f7-8397-8ae8e2758183,) cs2Label=uniqueServiceAppIds cs2=APPID_OUTLOOK cs3Label=targetObjects cs3=admin@contoso.com c6a1Label="Device IPv6 Address" c6a1=

    2017-07-11T19:14:56.781Z CEF:0|MCAS|SIEM_Agent|0.101.113|EVENT_CATEGORY_DOWNLOAD_FILE|Download file|0|externalId=1499800496781_2e50118e-dee7-40d7-b912-b81a10feed28 start=1499800496781 end=1499800496781 msg=Download file: file name50280117yyct6t.xlsx suser=roy@adallom.com.test destinationServiceName=Salesforce dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149979855250880034 cs1Label=portalURL cs1=https://cloud-app-security/#/audits?activity.id\=eq(1499800496781_2e50118e-dee7-40d7-b912-b81a10feed28,) cs2Label=uniqueServiceAppIds cs2=APPID_SALESFORCE cs3Label=targetObjects cs3=name50280117yyct6t.xlsx c6a1Label="Device IPv6 Address" c6a1=

    2017-07-11T19:16:04.666Z CEF:0|MCAS|SIEM_Agent|0.101.113|EVENT_CATEGORY_SSO_LOGIN|Single sign-on log on|0|externalId=1499800564666_06496600-edde-4d81-a995-7632e70fb24f start=1499800564666 end=1499800564666 msg=Single sign-on log on suser=admin@contoso.com destinationServiceName=Microsoft Online Services dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149980039637481908 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499800564666_06496600-edde-4d81-a995-7632e70fb24f,) cs2Label=uniqueServiceAppIds cs2=APPID_11394 cs3Label=targetObjects cs3=admin@contoso.com c6a1Label="Device IPv6 Address" c6a1=

    2017-07-12T13:28:29.067Z CEF:0|MCAS|SIEM_Agent|0.101.113|EVENT_CATEGORY_DOWNLOAD_FILE|Download file|0|externalId=1499866109067_8e3fae2c-ca5b-4163-84b6-fb9a03c4d052 start=1499866109067 end=1499866109067 msg=Download file: file CC004.txt suser=admin@box-contoso.com destinationServiceName=Box dvc=194.69.102.134 requestClientApplication=Mozilla/5.0 (Linux; Android 7.0; SAMSUNG SM-G930F Build/NRD90M) AppleWebKit/537.36 (KHTML, like Gecko) SamsungBrowser/5.0 Chrome/51.0.2704.106 Mobile Safari/537.36 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499866109067_8e3fae2c-ca5b-4163-84b6-fb9a03c4d052,) cs2Label=uniqueServiceAppIds cs2=APPID_BOX cs3Label=targetObjects cs3=CC004.txt c6a1Label="Device IPv6 Address" c6a1=
    
    2017-07-12T14:15:33.901Z CEF:0|MCAS|SIEM_Agent|0.101.113|EVENT_CATEGORY_UPLOAD_FILE|Upload file|0|externalId=1499868933901_72c21ebe-c206-4d8c-a41b-224035868d09 start=1499868933901 end=1499868933901 msg=Upload file: file response.txt suser=user1@test15-adallom.com destinationServiceName=Google Drive dvc=194.69.102.134 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; WOW64; Trident/7.0; Touch; rv:11.0) like Gecko cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499868933901_72c21ebe-c206-4d8c-a41b-224035868d09,) cs2Label=uniqueServiceAppIds cs2=APPID_26069 cs3Label=targetObjects cs3=response.txt c6a1Label="Device IPv6 Address" c6a1=

    2017-07-12T18:53:16.519Z CEF:0|MCAS|SIEM_Agent|0.101.113|EVENT_CATEGORY_LOGIN|Log on|0|externalId=1499885596519_ed261269-9b07-4418-9ded-8cad464d677f start=1499885596519 end=1499885596519 msg=Log on suser=admin@contoso.com destinationServiceName=Office 365 dvc=13.82.149.151 requestClientApplication=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Safari/537.36 machine_id_149988543613557447 cs1Label=portalURL cs1=https://cloud-app-security.com/#/audits?activity.id\=eq(1499885596519_ed261269-9b07-4418-9ded-8cad464d677f,) cs2Label=uniqueServiceAppIds cs2=APPID_O365 cs3Label=targetObjects cs3=admin@contoso.com c6a1Label="Device IPv6 Address" c6a1=
```
同様に、次はアラート ログ ファイルのサンプルです。
```
  2017-07-15T20:42:30.531Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|myPolicy|3|externalId=596a7e360c204203a335a3fb start=1500151350531 end=1500151350531 msg=Activity policy ''myPolicy'' was triggered by ''admin@box-contoso.com'' suser=admin@box-contoso.com destinationServiceName=Box cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596a7e360c204203a335a3fb cs2Label=uniqueServiceAppIds cs2=APPID_BOX cs3Label=relatedAudits cs3=1500151288183_acc891bf-33e1-424b-a021-0d4370789660
  
  2017-07-16T09:36:26.550Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b339b0c204203a33a51ae start=1500197786550 end=1500197786550 msg=Activity policy ''test-activity-policy'' was triggered by ''user@contoso.com'' suser=user@contoso.com destinationServiceName=Salesforce cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b339b0c204203a33a51ae cs2Label=uniqueServiceAppIds cs2=APPID_SALESFORCE cs3Label=relatedAudits cs3=1500197720691_b7f6317c-b8de-476a-bc8f-dfa570e00349

  2017-07-16T09:17:03.361Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy3|3|externalId=596b2fd70c204203a33a3eeb start=1500196623361 end=1500196623361 msg=Activity policy ''test-activity-policy3'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Office 365 cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eeb cs2Label=uniqueServiceAppIds cs2=APPID_O365 cs3Label=relatedAudits cs3=1500196549157_a0e01f8a-e29a-43ae-8599-783c1c11597d

  2017-07-16T09:17:15.426Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy|3|externalId=596b2fd70c204203a33a3eec start=1500196635426 end=1500196635426 msg=Activity policy ''test-activity-policy'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft Office 365 admin center cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b2fd70c204203a33a3eec cs2Label=uniqueServiceAppIds cs2=APPID_O365_PORTAL cs3Label=relatedAudits cs3=1500196557398_3e102b20-d9fa-4f66-b550-8c7a403bb4d8

  2017-07-16T09:17:46.290Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy4|3|externalId=596b30200c204203a33a4765 start=1500196666290 end=1500196666290 msg=Activity policy ''test-activity-policy4'' was triggered by ''admin@contoso.com'' suser=admin@contoso.com destinationServiceName=Microsoft Exchange Online cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b30200c204203a33a4765 cs2Label=uniqueServiceAppIds cs2=APPID_OUTLOOK cs3Label=relatedAudits cs3=1500196587034_a8673602-7e95-46d6-a1fe-c156c4709c5d

  2017-07-16T09:41:04.369Z CEF:0|MCAS|SIEM_Agent|0.102.17|ALERT_CABINET_EVENT_MATCH_AUDIT|test-activity-policy2|3|externalId=596b34b10c204203a33a5240 start=1500198064369 end=1500198064369 msg=Activity policy ''test-activity-policy2'' was triggered by ''user2@test15-adallom.com'' suser=user2@test15-adallom.com destinationServiceName=Google cn1Label=riskScore cn1= cs1Label=portalURL cs1=https://cloud-app-security.com/#/alerts/596b34b10c204203a33a5240 cs2Label=uniqueServiceAppIds cs2=APPID_33626 cs3Label=relatedAudits cs3=1500197996117_fd71f265-1e46-4f04-b372-2e32ec874cd3
```

### <a name="step-3-validate-that-the-siem-agent-is-working"></a>手順 3: SIEM エージェントが動作しているか検証する

1. Cloud App Security ポータルの SIEM エージェントの状態が **[接続エラー]** または **[切断]** ではないことと、エージェント通知がないことを確認します。 接続がダウンしている状態が 2 時間を超える場合は **[接続エラー]**、12 時間を超える場合は **[切断]** と表示されます。
 ![SIEM が切断されている状態](./media/siem-not-connected.png)
 
   以下のように、接続状態である必要があります。![SIEM が接続されている状態](./media/siem-connected.png)

2. Syslog/SIEM サーバーで、Cloud App Security から送られたアクティビティとアラートが表示されていることを確認します。


## <a name="regenerating-your-token"></a>トークンの再生成
トークンが失われた場合は、テーブルの SIEM エージェント行の末尾にある 3 つの点をクリックし、**[トークンの再生成]** を選択して、いつでも再生成することができます。

 ![SIEM - トークンの再生成](./media/siem-regenerate-token.png)

## <a name="editing-your-siem-agent"></a>SIEM エージェントの編集 
SIEM エージェントを後で編集する必要がある場合は、テーブルの SIEM エージェント行の末尾にある 3 つの点をクリックし、**[編集]** を選択できます。 SIEM エージェントを編集する場合、.jar ファイルを再実行する必要はありません。自動的に更新されます。

![SIEM - 編集](./media/siem-edit.png)

## <a name="deleting-your-siem-agent"></a>SIEM エージェントの削除
後で SIEM エージェントを削除する必要がある場合は、テーブルの SIEM エージェント行の末尾にある 3 つの点をクリックし、**[削除]** を選択できます。

![SIEM - 削除](./media/siem-delete.png)

> [!NOTE]
> この機能はパブリック プレビューの状態にあります。

## <a name="high-availability-options"></a>高可用性オプション

SIEM エージェントは、最大 2 日間のダウンタイムの復旧をサポートする、単一のエンドポイントです。 顧客のエンドポイントとしてロード バランサーを設けることで、高可用性をさらに高められます。

## <a name="see-also"></a>関連項目  
[SIEM 統合問題のトラブルシューティング](troubleshooting-siem.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  