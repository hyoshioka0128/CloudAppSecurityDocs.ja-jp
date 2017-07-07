---
title: "アプリを Cloud App Security に接続して使用状況を詳細に表示し、管理する | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して、アプリを組織のクラウド内のアプリに接続するプロセスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/3/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 7e718d77-aae7-4a3a-8421-5ba7cee7d67c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c8c9b63f4265876fc1de6a24c6576f917f9d2278
ms.sourcegitcommit: a0290ac2a662994f7771975ef6c20d0b47e9edd8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2017
---
Cloud App Security は、次のようにユーザーのネットワークへの接続が必要です。 

## <a name="cloud-app-security-system-ip-addresses"></a>Cloud App Security のシステム IP アドレス

Cloud App Security は顧客の環境に接続するために次の IP アドレスを使います。 これは、[ICAP](icap-stunnel.md) を使って接続するとき、およびアプリ コネクタに接続するときに必要です。 アプリによっては、次の IP アドレスをホワイト リストに追加して Cloud App Security によるログ収集や、Cloud App Security コンソールへのアクセスを可能にする必要がある場合があります。 一部のアプリでは、これらの IP アドレスは、サービスの監査ログなどで Cloud App Security のアクティビティを識別するためにも使うことができます。 
  
-   ログ収集の場合:  
  
    104.209.35.177  
  
    13.91.98.185
 
    40.118.211.172

    13.93.216.68

    13.91.61.249

    13.93.233.42

    13.64.196.27

    13.64.198.97

    13.64.199.41

    13.64.198.19
  
  
## <a name="cas-portal-url-and-ip-addresses"></a>CAS ポータルの URL および IP アドレス

ポータルへの顧客アクセス、および CAS API、ログ コレクター、SIEM エージェントに接続するときの API 接続には、Cloud App Security URL、ポート 443、IP アドレスが使われます。 
  
     104.42.231.28  

 
  
> [!NOTE]  
>  URL および IP アドレスが変更されときに更新されるようにするには、「[Office 365 の URL および IP アドレス範囲](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)」で説明されているように RSS を購読します。  
  

  
## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  

   