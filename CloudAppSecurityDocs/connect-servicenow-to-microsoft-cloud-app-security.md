---
title: "ServiceNow の接続 | Microsoft Docs"
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
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: 7935006b6b28ed93601ca60adf3c1a408440eae7


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
  
4.  Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
5.  **[アプリ コネクター]** ページで、[+] ボタン、**[ServiceNow]** の順にクリックします。  
  
     ![ServiceNow を接続する](./media/connect-servicenow.png "connect servicenow")  
  
6.  ポップアップの該当するボックスに ServiceNow のユーザー名、パスワード、およびインスタンス URL を追加します。  
  
7.  **[接続]**をクリックします。  
  
     ![ServiceNow のパスワードの更新](./media/servicenow-update-password.png "servicenow update password")  
  
8.  [**API のテスト**] をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 成功通知を受信したら、 [**閉じる**] をクリックします。  
  
ServiceNow を接続すると、接続までの 60 日間のイベントを受け取ります。
  
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


