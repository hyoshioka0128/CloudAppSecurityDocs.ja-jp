---
title: "Cloud App Security ネットワークの要件 | Microsoft Docs"
description: "このトピックでは、Cloud App Security で作業するために開く必要があるポートと IP アドレスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: dac230e191c7c2d8159a2f373e6ef939fdd841a4
ms.sourcegitcommit: c3fda43ef6fe0d15f0eb9ea23a6f245bad8c371b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2017
---
# <a name="network-requirements"></a>ネットワーク要件

このトピックでは、Cloud App Security で作業するために許可し、ホワイトリストに追加する必要があるポートと IP アドレスの一覧を提供します。 


## <a name="portal-access"></a>ポータル アクセス

ポータル アクセスの場合、次の IP アドレスをファイアウォールのホワイトリストに追加し、Cloud App Security ポータルにアクセスできるようにする必要があります。  
  
104.42.231.28  


## <a name="app-connector-access"></a>アプリ コネクタへのアクセス

Cloud App Security によってアクセスされるサードパーティー製アプリによっては、次の IP アドレスをホワイト リストに追加して Cloud App Security によるログ収集や、Cloud App Security コンソールへのアクセスを可能にする必要がある場合があります。  
  
104.209.35.177  
13.91.98.185 40.118.211.172 13.93.216.68 13.91.61.249 13.93.233.42 13.64.196.27 13.64.198.97 13.64.199.41 13.64.198.19

> [!NOTE]
>Cloud App Security は上記の IP アドレスからガバナンス アクションとスキャンを実行するため、ベンダーからのアクティビティ ログにこの IP アドレスが表示される場合があります。 
  

## <a name="siem-agent-and-log-collector"></a>SIEM エージェントおよびログ コレクター

Cloud App Security を有効にして SIEM に接続し、Cloud App Security のログ コレクターが実行されるようにするには、次を開く必要があります。

- 送信ポート 443 から 104.42.231.28

## <a name="external-dlp-integration"></a>外部 DLP 統合

Cloud App Security で stunnel 経由でデータを ICAP サーバーに送信するには、Cloud App Security で使用される外部 IP アドレスに DMZ ファイアウォールを開きます。このとき、動的ソース ポート番号を使用します。 

1.  ソースのアドレス: 上記の API コネクタのサードパーティー製アプリについて記載したように、これらをホワイトリストに追加する必要があります
2.  ソース TCP ポート: 動的
3.  宛先アドレス: 外部 ICAP サーバーに接続されている stunnel の 1 つまたは 2 つの IP アドレス
4.  宛先 TCP ポート: ネットワークに定義されている宛先 TCP ポート

> [!NOTE] 
> 既定では、stunnel ポート番号は 11344 に設定されます。 これは必要に応じて別のポートに変更できますが、新しいポート番号を必ず書き留めてください。



  
## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  

   