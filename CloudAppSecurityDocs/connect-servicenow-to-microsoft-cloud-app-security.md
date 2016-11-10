---
title: "ServiceNow を Microsoft Cloud App Security に接続する | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に ServiceNow アプリを接続する方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c626d94d-2ffd-4daf-8fa4-4b6d308cf012
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 30ddba23a0c481cb434e9239950cce90c52efc4f


---

# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>ServiceNow を Microsoft Cloud App Security に接続する
このセクションでは、App Connector API を使用して Cloud App Security を既存の ServiceNow アカウントに接続する方法を説明します。  
  
## <a name="how-to-connect-servicenow-to-cloud-app-security"></a>ServiceNow を Cloud App Security に接続する方法  
  
> [!NOTE]  
>  Cloud App Security では、ServiceNow の Eureka および Fiji のバージョンがサポートされています。 ServiceNow を Cloud App Security に接続するには、管理者レベルのアクセス許可が必要であるほか、ServiceNow インスタンスが API アクセスをサポートしていることを確認する必要があります。  
  
1.  ServiceNow アカウントに管理者アカウントでログオンします。  
  
2.  Cloud App Security 用の新しいサービス アカウントを作成し、その新しいアカウントに管理者のロールを与えます。  
  
3.  REST API のプラグインが有効になっていることを確認します。  
  
     ![ServiceNow アカウント](./media/servicenow-account.png "servicenow account")  
  
4.  Cloud App Security のポータルで [**調査**]、[**承認されたアプリ**] の順にクリックします。  
  
5.  [ServiceNow] 行の [**アプリ コネクタの状態**] 列で [**接続**] をクリックするか、または [**アプリを接続**] ボタンをクリックして [**ServiceNow**] を選択します。  
  
     ![ServiceNow を接続する](./media/connect-servicenow.png "connect servicenow")  
  
6.  ServiceNow の設定ページの [API] タブで、該当するボックスに ServiceNow ユーザー名、パスワード、およびインスタンス URL を追加します。  
  
7.  **[接続]**をクリックします。  
  
     ![ServiceNow のパスワードの更新](./media/servicenow-update-password.png "servicenow update password")  
  
8.  [**API のテスト**] をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 成功通知を受信したら、 [**閉じる**] をクリックします。  
  
ServiceNow を接続すると、接続までの 60 日間のイベントを受け取ります。
  
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


