---
title: "Okta の接続 | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に Okta アプリを接続する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 9c3673b9-99bd-400c-9da1-5bf809ea5892
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6beb9041b338406fb5b16f4bd045dbdc4592c6d9
ms.openlocfilehash: 1e82f94cb8423bdaa3dcdc8d4a4f04179089546c


---

# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Okta を Microsoft Cloud App Security に接続する
このセクションでは、コネクタ API を使用して Cloud App Security を既存の Okta アカウントに接続する方法を説明します。  
  
## <a name="how-to-connect-okta-to-cloud-app-security"></a>Okta を Cloud App Security に接続する方法  
  
1.  Okta で、Cloud App Security 向けの管理者サービス アカウントを作成することをお勧めします。  
  
     スーパー管理者のアクセス許可を付与されたアカウントを必ず使用してください。  
  
     Okta アカウントが検証済みであることを確認します。  
  
2.  Okta コンソールで [**管理者**] をクリックします。  
  
    -   [**セキュリティ**]、[**API**] の順にクリックします。  
  
         ![Okta の API](./media/okta-api.png "okta api")  
  
    -   [**トークンを作成します**] をクリックします。  
  
         ![Okta のトークン作成](./media/okta-createtoken.jpg "okta createtoken")  
  
    -   **[トークンを作成します]** ポップアップで、Cloud App Security トークンに名前を付けてから **[トークンを作成します]** をクリックします。  
  
         ![Okta のトークン ポップアップ](./media/okta-token-popup.png "okta token popup")  
  
    -   [**Token cated successfully popup (トークンは正常に作成されました)**] ポップアップで、[**トークン値 (Token value)**] をコピーします。  
  
         ![Okta のトークン値](./media/okta-token-value.png "okta token value")  
  
3.  Cloud App Security コンソールで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
4.  **[アプリ コネクター]** ページで、[+] ボタン、**[Okta]** の順にクリックします。  
  
     ![Okta を接続する](./media/connect-okta.png "connect okta")  
  
5.  表示されたポップアップの **[ドメイン]** フィールドに Okta ドメインを入力し、トークンを **[トークン]** フィールドに貼り付けます。  
  
6.  **[接続]** をクリックして、Okta のトークンを Cloud App Security で作成します。  
  
7.  [**API のテスト**] をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 成功通知を受信したら、 [**閉じる**] をクリックします。  
  
Okta を接続すると、接続までの 60 日間のイベントを受け取ります。
  
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


