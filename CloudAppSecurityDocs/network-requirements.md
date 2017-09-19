---
title: "Cloud App Security ネットワークの要件 | Microsoft Docs"
description: "このトピックでは、Cloud App Security で作業するために開く必要があるポートと IP アドレスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/17/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 82bdda2ab26fa1c954edb5186eeb37d909d65e64
ms.sourcegitcommit: d012fc1a099773bd9e9dc61906faab68dae0e996
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2017
---
# <a name="network-requirements"></a>ネットワーク要件

このトピックでは、Cloud App Security で作業するために許可し、ホワイトリストに追加する必要があるポートと IP アドレスの一覧を提供します。 

接続先の Cloud App Security データ センターの確認方法については、「[API トークン](api-tokens.md)」を参照してください。



## <a name="portal-access-siem-agent-authentication-gateway-and-log-collector"></a>ポータル アクセス, SIEM エージェント, 認証ゲートウェイ, ログ コレクター

ポータルと認証ゲートウェイにアクセスするため、また、Cloud App Security を SIEM に接続できるように、さらに Cloud App Security ログ コレクターを実行できるようにするには、次の IP アドレスの**送信ポート 443** をファイアウォールのホワイト リストに追加する必要があります。  


> [!div class="mx-tableFixed"]
|データ センター|IP アドレス|  
|----|----|
|US1|13.91.91.243<br></br>52.183.75.62|
|EU1|52.174.56.180<br></br>13.80.125.22|

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


    



  
## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  

   