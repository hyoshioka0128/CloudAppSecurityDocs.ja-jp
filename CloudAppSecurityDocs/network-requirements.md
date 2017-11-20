---
title: "Cloud App Security ネットワークの要件 | Microsoft Docs"
description: "このトピックでは、Cloud App Security で作業するために開く必要があるポートと IP アドレスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/30/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f67e363f9b6cdb866124960037ecb81e07756d8a
ms.sourcegitcommit: 9eb5c9c43629329a081f970b480956975e424ecb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2017
---
# <a name="network-requirements"></a>ネットワーク要件

このトピックでは、Cloud App Security で作業するために許可し、ホワイトリストに追加する必要があるポートと IP アドレスの一覧を提供します。 


## <a name="view-your-data-center"></a>データ センターを表示する

以下の要件の一部は、接続しているデータ センターに依存します。 

接続しているデータ センターを確認するには:

1. Cloud App Security ポータルで、メニュー バーの **[?]** をクリックして、 **[バージョン情報]** を選択します。 

    ![[バージョン情報] をクリックします。](./media/about-menu.png)

2. Cloud App Security のバージョン画面で、リージョンとデータ センターを確認できます。

    ![データ センターを表示する](./media/data-center.png)

## <a name="portal-access"></a>ポータル アクセス

Cloud App Security ポータルにアクセスするには、ファイアウォールのホワイトリストに対する次の IP アドレスに**発信ポート 443** を追加します。  


> [!div class="mx-tableFixed"]
|データ センター|IP アドレス|  
|----|----|
|US1|13.80.125.22<br></br>52.183.75.62<br></br>13.91.91.243|
|EU1|13.80.125.22<br></br>52.183.75.62<br></br>52.174.56.180|

## <a name="siem-agent-connection"></a>SIEM エージェントの接続

Cloud App Security が SIEM に接続できるようにするには、ファイアウォールのホワイトリストに対する次の IP アドレスに**発信ポート 443** を追加します。  


> [!div class="mx-tableFixed"]
|データ センター|IP アドレス|  
|----|----|
|US1|13.91.91.243|
|EU1|52.174.56.180|

## <a name="app-connector-access-and-external-dlp-integration"></a>アプリ コネクタ アクセスと外部 DLP 統合

サードパーティ製のアプリに接続し、外部 DLP ソリューションと統合するには、Cloud App Security を有効にして次の IP アドレスに接続します。


> [!div class="mx-tableFixed"]
|データ センター|IP アドレス|  
|----|----|
|US1|104.209.35.177<br></br>13.91.98.185<br></br>40.118.211.172<br></br>13.93.216.68<br></br>13.91.61.249<br></br>13.93.233.42<br></br>13.64.196.27<br></br>13.64.198.97<br></br>13.64.199.41<br></br>13.64.198.19|
|EU1|13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|


### <a name="app-connector"></a>アプリ コネクタ
Cloud App Security にアクセスされるサードパーティ製アプリによっては、Cloud App Security によるログ収集や、Cloud App Security コンソールのアクセスの提供を可能にするために上記の IP アドレスが利用されることがあります。 

> [!NOTE]
>Cloud App Security は上記の IP アドレスからガバナンス アクションとスキャンを実行するため、ベンダーからのアクティビティ ログにこの IP アドレスが表示される場合があります。 
  

### <a name="dlp-integration"></a>DLP 統合

Cloud App Security で stunnel 経由でデータを ICAP サーバーに送信するには、上記の IP アドレスに DMZ ファイアウォールを開きます。このとき、動的ソース ポート番号を使用します。 

1.  ソースのアドレス: 上記の API コネクタのサードパーティ製アプリについて記載したように、これらをホワイトリストに追加する必要があります
2.  ソース TCP ポート: 動的
3.  宛先アドレス: 外部 ICAP サーバーに接続されている stunnel の 1 つまたは 2 つの IP アドレス
4.  宛先 TCP ポート: ネットワークに定義されている宛先 TCP ポート

> [!NOTE] 
> 既定では、stunnel ポート番号は 11344 に設定されます。 これは必要に応じて別のポートに変更できますが、新しいポート番号を必ず書き留めてください。

## <a name="email-server"></a>電子メール サーバー

Cloud App Security 専用の電子メールの IP アドレスは次のとおりです。 

198.2.134.139 (mail1.cloudappsecurity.com)

この IP アドレスを必ずお使いのスパム対策サービスにホワイトリスト登録し、通知が送信されるようにしてください。
    
## <a name="log-collector"></a>ログ コレクター 

Cloud Discovery 機能がログ コレクターを使って組織内のシャドウ IT を検出できるようにするには、以下を開始する必要があります。

- ログ コレクターが着信 FTP および Syslog トラフィックを受信できる。
- ログ コレクターがポート 443 でポータル (contoso.cloudappsecurity.com など) への発信トラフィックを開始できる。
- ログ コレクターがポート 80 と 443 で Azure Blob Storage (https://adaprodconsole.blob.core.windows.net/) への送信トラフィックを開始できる。

> [!NOTE]
> ファイアウォールが静的 IP アドレスのアクセス リストを必要としていて、URL に基づくホワイト リストをサポートしていない場合は、ログ コレクターで Microsoft Azure データセンターのポート 443 上の IP 範囲への送信トラフィックを開始できるようにします。




## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  

   