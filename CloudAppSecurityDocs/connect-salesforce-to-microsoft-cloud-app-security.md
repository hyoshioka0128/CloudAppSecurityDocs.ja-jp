---
title: "Salesforce の接続 | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に Salesforce を接続する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/26/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 776d7589-acdb-4cb6-99a0-3be2f7b6aab2
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 129181e4768f068a0e30f6ef3a2d3f7fc6d47024
ms.openlocfilehash: 0932c6bc696e7b050eae543fbea7d847dfa42b4b


---


# <a name="connect-salesforce-to-microsoft-cloud-app-security"></a>Salesforce を Microsoft Cloud App Security に接続する
このセクションでは、App Connector API を使用して Cloud App Security を既存の Salesforce アカウントに接続する方法を説明します。  
  
## <a name="how-to-connect-salesforce-to-cloud-app-security"></a>Salesforce を Cloud App Security に接続する方法  
  
1.  Cloud App Security 専用のサービス管理者アカウントを作成することをお勧めします。  
  
2.  Salesforce で REST API が有効になっていることを確認します。  
  
     Salesforce アカウントには、REST API のサポートを含むエディション   
  
     (**Performance**、**Enterprise**、**Unlimited**、**Developer** のいずれか) を使用する必要があります。  
  
     **Professional** エディションには、既定では REST API のサポートが含まれていませんが、オンデマンドで追加することができます。  
  
     現在のエディションで REST API を使用可能かどうか、有効化されているかどうかを確認するには、以下の手順を実行します。  
  
    -   Salesforce アカウントにログインし、[**設定**] ページに移動します。  
  
    -   [**ユーザの管理**] から [**プロファイル**] ページに移動します。  
  
         ![Salesforce の [Manage Users] (ユーザーの管理) プロファイル](./media/salesforce-manageusers-profiles.png "Salesforce の [Manage Users] (ユーザーの管理) プロファイル")  
  
    -   Cloud App Security のデプロイに使用しているプロファイルを選択して、**[編集]** をクリックします。 これは、Cloud App Security サービス アカウントでアプリ コネクターをセットアップする場合に使用されるプロファイルです。  
  
         ![Salesforce のプロファイルの編集](./media/salesforce-edit-profile.png "Salesforce のプロファイルの編集")  
  
    -   [**API の有効化**] チェックボックスがオンになっていることを確認します。 オフになっている場合は、Salesforce に連絡してアカウントに追加する必要があります。  
  
         ![Salesforce の [API Enabled] (API 有効)](./media/salesforce-api-enabled.png "Salesforce の [API Enabled] (API 有効)")  
  
3.  組織で [**Salesforce CRM Content**] を有効化している場合は、現在の管理者アカウントでも有効になっていることを確認します。  
  
    1.  Salesforce の設定ページに移動します。  
  
         ![Salesforce の [Setup] (セットアップ)](./media/salesforce-setup.png "Salesforce の [Setup] (セットアップ)")  
  
    2.  サイド メニューから **[ユーザーの管理]** を選択し、**[ユーザー]** をクリックします。  
  
         ![Salesforce メニューの [User] (ユーザー)](./media/salesforce-menu-users.png "Salesforce メニューの [User] (ユーザー)")  
  
    3.  専用の Cloud App Security ユーザーの現在の管理ユーザーを選択します。  
  
    4.  [**Salesforce CRM Content ユーザ**] チェックボックスがオンになっていることを確認します。  
  
         オフになっている場合は、[**編集**] をクリックしてチェックボックスをオンにします。  
  
         ![[Salesforce CRM Content User] (Salesforce CRM Content ユーザー)](./media/salesforce-crm-content-user.png "[Salesforce CRM Content User] (Salesforce CRM Content ユーザー)")  
  
    5.  **[Save]**(保存) をクリックします。  
  
4.  Cloud App Security コンソールで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
5.  **[アプリ コネクター]** ページで、[+] ボタン、**[Salesforce]** の順にクリックします。  
  
     ![Salesforce への接続](./media/connect-salesforce.png "Salesforce への接続")  
  
6.  Salesforce の設定ページの [API] タブで、インストールするインスタンスに応じて [**Follow this link (このリンクに移動)**] をクリックします。  
  
7.  Salesforce のログオン ページが開きます。 Cloud App Security がチームの Salesforce アプリにアクセスできるように、資格情報を入力します。  
  
     ![Salesforce へのログオン](./media/salesforce-logon.png "Salesforce へのログオン")  
  
8.  Cloud App Security からチームの情報やアクティビティ ログにアクセスし、任意のチーム メンバーと同様に任意のアクティビティを実行することを許可するかどうかを確認するメッセージが Salesforce で表示されます。 続行するには、[**許可**] をクリックします。  
  
9. この時点で、デプロイの成功または失敗に関する通知が表示されます。これにより、 Cloud App Security が Salesforce.com で承認されました。  
  
10. Cloud App Security コンソールに戻ると、Salesforce が正常に接続されたことを示すメッセージが表示されます。  
  
11. [**API のテスト**] をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 成功の通知を受信したら、[**完了**] をクリックします。  
  
  
Salesforce に接続すると、Salesforce EventMonitoring ライセンスに応じて、接続した時点からのトリガー、接続までの 60 日間のログイン イベントとセットアップ監査証跡、30 日前または 1 日前の EventMonitoring などのイベントを受け取ります。
  
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Dec16_HO2-->


