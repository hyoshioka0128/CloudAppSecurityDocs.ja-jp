---
title: Cloud App Security ネットワークの要件 | Microsoft Docs
description: このトピックでは、Cloud App Security で作業するために開く必要があるポートと IP アドレスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4de606f2-a09e-4e48-a578-e223de8b5e69
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9bc1064b28a8d7781718f121a0f64bd9cfa97395
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144314"
---
*適用対象: Microsoft Cloud App Security*


# <a name="network-requirements"></a>ネットワーク要件

このトピックでは、Microsoft Cloud App Security で作業するために許可し、ホワイトリストに追加する必要があるポートと IP アドレスの一覧を提供します。 


## <a name="view-your-data-center"></a>データ センターを表示する

以下の要件の一部は、接続しているデータ センターに依存します。 

接続しているデータ センターを確認するには:

1. Cloud App Security ポータルで、メニュー バーの **[?]** をクリックして、 **[バージョン情報]** を選択します。 

    ![[バージョン情報] をクリックします。](./media/about-menu.png)

2. Cloud App Security のバージョン画面で、リージョンとデータ センターを確認できます。

    ![データ センターを表示する](./media/data-center.png)

## <a name="portal-access"></a>ポータル アクセス

Cloud App Security ポータルにアクセスするには、次の IP アドレスと DNS 名について、ファイアウォールのホワイトリストに**発信ポート 443** を追加します。  


> [!div class="mx-tableFixed"]
> 
> |データ センター|IP アドレス|DNS 名|
> |----|----|----|
> |US|13.80.125.22<br></br>52.183.75.62<br></br>13.91.91.243|portal.cloudappsecurity.com<br></br>\*.portal.cloudappsecurity.com <br></br>\*.us.portal.cloudappsecurity.com<br></br>cdn.cloudappsecurity.com|
> |US2|13.80.125.22<br></br>52.183.75.62<br></br>52.184.165.82|portal.cloudappsecurity.com<br></br>\*.portal.cloudappsecurity.com <br></br>\*.us2.portal.cloudappsecurity.com<br></br>cdn.cloudappsecurity.com|
> |US3|13.80.125.22<br></br>52.183.75.62<br></br>40.90.218.198<br></br>40.90.218.196|portal.cloudappsecurity.com<br></br>*.portal.cloudappsecurity.com <br></br>*.us3.portal.cloudappsecurity.com<br></br>cdn.cloudappsecurity.com|
> |EU|13.80.125.22<br></br>52.183.75.62<br></br>52.174.56.180|portal.cloudappsecurity.com<br></br>\*.portal.cloudappsecurity.com <br></br>\*.eu.portal.cloudappsecurity.com<br></br>cdn.cloudappsecurity.com|
> |EU2|13.80.125.22<br></br>52.183.75.62<br></br>40.81.156.154<br></br>40.81.156.156|portal.cloudappsecurity.com<br></br>*.portal.cloudappsecurity.com <br></br>*.eu2.portal.cloudappsecurity.com<br></br>cdn.cloudappsecurity.com|


> 
> [!NOTE]
> ワイルドカード (\*) の代わりに、特定のテナント URL のみを開くことができます。たとえば、上記のスクリーンショットでは、mod244533.us.portal.cloudappsecurity.com を開くことができます。

## <a name="siem-agent-connection"></a>SIEM エージェントの接続

Cloud App Security が SIEM に接続できるようにするには、ファイアウォールのホワイトリストに対する次の IP アドレスに**発信ポート 443** を追加します。  


> [!div class="mx-tableFixed"]
> 
> |データ センター|IP アドレス|  
> |----|----|
> |US|13.91.91.243|
> |US2|52.184.165.82|
> |US3|40.90.218.198<br>40.90.218.196|
> |EU|52.174.56.180|
> |EU2|40.81.156.154<br>40.81.156.156|

## <a name="app-connector"></a>アプリ コネクタ

Cloud App Security にアクセスされるサードパーティ製アプリによっては、Cloud App Security によるログ収集や、Cloud App Security コンソールのアクセスの提供を可能にするために上記の IP アドレスが利用されることがあります。 

> [!NOTE]
>Cloud App Security は上記の IP アドレスからガバナンス アクションとスキャンを実行するため、ベンダーからのアクティビティ ログにこの IP アドレスが表示される場合があります。 

サードパーティ製のアプリに接続するには、Cloud App Security を有効にして次の IP アドレスから接続します。


> [!div class="mx-tableFixed"]
> 
> |データ センター|IP アドレス|  
> |----|----|
> |US|13.91.91.243 <br></br> 104.209.35.177 <br></br> 13.91.98.185 <br></br> 40.118.211.172 <br></br> 13.93.216.68 <br></br> 13.91.61.249 <br></br> 13.93.233.42 <br></br> 13.64.196.27 <br></br> 13.64.198.97 <br></br> 13.64.199.41 <br></br> 13.64.198.19|
> |US2|52.184.165.82<br></br> 40.84.4.93 <br></br> 40.84.4.119 <br></br> 40.84.2.83 |
> |US3|40.90.218.197<br>40.90.218.203|
> |EU|52.174.56.180<br></br>13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|
> |EU2|40.81.156.155<br>40.81.156.153|


## <a name="third-party-dlp-integration"></a>サード パーティ DLP との統合

Cloud App Security で stunnel 経由でデータを ICAP サーバーに送信するには、上記の IP アドレスに DMZ ファイアウォールを開きます。このとき、動的ソース ポート番号を使用します。 

1.  ソースのアドレス: 上記の API コネクタのサードパーティ製アプリについて記載したように、これらをホワイトリストに追加する必要があります
2.  ソース TCP ポート: 動的
3.  宛先アドレス: 外部 ICAP サーバーに接続されている stunnel の 1 つまたは 2 つの IP アドレス
4.  宛先 TCP ポート: ネットワークに定義されている宛先 TCP ポート

> [!NOTE] 
> -  既定では、stunnel ポート番号は 11344 に設定されます。 これは必要に応じて別のポートに変更できますが、新しいポート番号を必ず書き留めてください。
> - Cloud App Security は上記の IP アドレスからガバナンス アクションとスキャンを実行するため、ベンダーからのアクティビティ ログにこの IP アドレスが表示される場合があります。 

サードパーティ製のアプリに接続し、外部 DLP ソリューションと統合するには、Cloud App Security を有効にして次の IP アドレスから接続します。

> [!div class="mx-tableFixed"]
> 
> |データ センター|IP アドレス|  
> |----|----|
> |US|13.91.91.243 <br></br> 104.209.35.177 <br></br> 13.91.98.185 <br></br> 40.118.211.172 <br></br> 13.93.216.68 <br></br> 13.91.61.249 <br></br> 13.93.233.42 <br></br> 13.64.196.27 <br></br> 13.64.198.97 <br></br> 13.64.199.41 <br></br> 13.64.198.19|
> |US2|52.184.165.82<br></br> 40.84.4.93 <br></br> 40.84.4.119 <br></br> 40.84.2.83 |
> |US3|40.90.218.197<br>40.90.218.203|
> |EU|52.174.56.180<br></br>13.80.22.71<br></br>13.95.29.177<br></br>13.95.30.46|
> |EU2|40.81.156.155<br>40.81.156.153|

## <a name="mail-server"></a>メール サーバー

既定のテンプレートと設定から通知が送信されるようにするには、スパム対策のホワイトリストにこれらの IP アドレスを追加します。 Cloud App Security 専用の電子メールの IP アドレスは次のとおりです。 

- 65.55.234.192/26
- 207.46.200.0/27
- 65.55.52.224/27
- 94.245.112.0/27
- 111.221.26.0/27
- 207.46.50.192/26

メール送信者の ID をカスタマイズする場合、Microsoft Cloud App Security では、サード パーティ製の電子メール サービス MailChimp® を使用してこれを可能にします。 これを機能させるには、Microsoft Cloud App Security ポータルの、**[設定]** の下で **[メールの設定]** を選択し、MailChimp のサービス利用規約とプライバシーに関する声明を確認して、Microsoft がユーザーの代理として MailChimp を使用することを許可します。

これを行わない場合、電子メール通知はすべての既定の設定を使用して送信されます。

MailChimp を使用するには、スパム対策のホワイトリストに IP アドレス 198.2.134.139 (mail1.cloudappsecurity.com) を追加して、通知の送信を可能にします。


## <a name="log-collector"></a>ログ コレクター 

Cloud Discovery 機能がログ コレクターを使って組織内のシャドウ IT を検出できるようにするには、以下を開始する必要があります。

- ログ コレクターが着信 FTP および Syslog トラフィックを受信できる。
- ログ コレクターがポート 443 でポータル (contoso.cloudappsecurity.com など) への発信トラフィックを開始できる。
- ログ コレクターがポート 80 と 443 で Azure Blob Storage への送信トラフィックを開始できる。


  | データ センター |                        URL                        |
  |-------------|---------------------------------------------------|
  |     US      |   https://adaprodconsole.blob.core.windows.net/   |
  |     US2     | https://prod03use2console1.blob.core.windows.net/ |
  |     US3     |https://prod5usw2console1.blob.core.windows.net/   |
  |     EU      | https://prod02euwconsole1.blob.core.windows.net/  |
  |     EU2     |https://prod4uksconsole1.blob.core.windows.net/    |

> [!NOTE]
> - ファイアウォールが静的 IP アドレスのアクセス リストを必要としていて、URL に基づくホワイト リストをサポートしていない場合は、ログ コレクターで [Microsoft Azure データセンターのポート 443 上の IP 範囲](https://www.microsoft.com/download/details.aspx?id=41653)への送信トラフィックを開始できるようにします。
>- ログ コレクターが Cloud App Security ポータルへの送信トラフィックを開始できるようにします。



## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  

