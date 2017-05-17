---
title: "ServiceNow を Cloud App Security に接続して使用状況を表示し、管理する | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に ServiceNow アプリを接続する方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: c626d94d-2ffd-4daf-8fa4-4b6d308cf012
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 18ae1b7bfd740303470504f3abd4021c8aa1deb9
ms.sourcegitcommit: f1ac8ccd470229078aaf1b58234a9a2095fa9550
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2017
---
# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>ServiceNow を Microsoft Cloud App Security に接続する

このセクションでは、App Connector API を使用して Cloud App Security を既存の ServiceNow アカウントに接続する方法を説明します。 

 >  [!NOTE]
>  Fuji 以降のリリースで使用可能な OAuth アプリ トークンを使用して ServiceNow を展開することをお勧めします (関連する [ServiceNow ドキュメント](http://wiki.servicenow.com/index.php?title=OAuth_Applications#gsc.tab=0)を参照)。 以前のリリースの場合は、[レガシー接続モード](#legacy-servicenow-connection)がユーザー/パスワードに基づいて使用可能です。

 > [!NOTE]  
>  Cloud App Security では、Eureka、Fiji、Geneva、Helsinki、Istanbul バージョンの ServiceNow がサポートされています。 ServiceNow を Cloud App Security に接続するには、**管理者**ロールが必要であるほか、ServiceNow インスタンスが API アクセスをサポートしていることを確認する必要があります。  詳細については、「[ServiceNow Product Documentation](http://wiki.servicenow.com/index.php?title=Base_System_Roles#gsc.tab=0)」を参照してください。
  
## <a name="how-to-connect-servicenow-to-cloud-app-security-using-oauth"></a>OAuth を使用して ServiceNow を Cloud App Security に接続する方法
  
  
1.  ServiceNow アカウントに管理者アカウントでログオンします。  
  
2.  **[Filter navigator (フィルター ナビゲーター)]** 検索バーに「**OAuth**」と入力し、**[アプリケーション レジストリ]** を選択します。

3. **[アプリケーション レジストリ]** メニュー バーで、**[新規作成]** をクリックし、新しい OAuth プロファイルを作成します。

   ![ServiceNow の新しい OAuth プロファイル](./media/servicenow-app-registry.png)

4. **[What kind of OAuth application? (OAuth アプリケーションの種類は?)]** で **[Create an OAuth API endpoint for external clients (外部クライアントの OAuth API エンドポイントを作成する)]** をクリックします。

   ![ServiceNow OAuth の種類](./media/servicenow-oauth-app-type.png)

5. **[Application Registries New record (アプリケーション レジストリの新しいレコード)]** の次の項目に入力します。
    
    - **[名前]** フィールドに新しい OAuth プロファイルの名前を入力します。たとえば、「CloudAppSecurity」にします。 
    
    - **[クライアント ID]** は自動的に生成されます。 この ID をコピーします。接続を完了するには、これを Cloud App Security に貼り付ける必要があります。
    
    - **[クライアント シークレット]** フィールドに文字列を入力します。 空のまま残した場合、無作為のシークレットが自動的に生成されます。 後で使用するためにコピーし、保存します。 
    
    - **[Access Token Lifespan (アクセス トークン有効期間)]** を 3,600 以上に増やします。
    
    - [ **送信**] をクリックします。

   ![ServiceNow プロファイル ID](./media/servicenow-profile-ids.png)

6.  Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
7.  **[アプリ コネクター]** ページで、[+] ボタン、**[ServiceNow]** の順にクリックします。  
  
     ![ServiceNow を接続する](./media/connect-servicenow.png "ServiceNow を接続する")  
  
8.  ポップアップの該当するボックスに ServiceNow のユーザー ID、パスワード、インスタンス URL、クライアント ID、クライアント シークレットを追加します。  
  
9.  **[接続]**をクリックします。  
  
     ![ServiceNow を CAS に接続する](./media/servicenow-portal-connect.png "ポータルで ServiceNow を接続する")  
  
10.  [**今すぐテスト**] をクリックし、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 成功通知を受信したら、 [**閉じる**] をクリックします。  
  
ServiceNow を接続すると、接続までの 60 日間のイベントを受け取ります。
  
## <a name="legacy-servicenow-connection"></a>レガシー ServiceNow 接続

ServiceNow を Cloud App Security に接続するには、管理者レベルのアクセス許可が必要であるほか、ServiceNow インスタンスが API アクセスをサポートしていることを確認する必要があります。   

1.  ServiceNow アカウントに管理者アカウントでログオンします。   

2.  Cloud App Security 用の新しいサービス アカウントを作成し、その新しいアカウントに管理者のロールを与えます。   

3.  REST API のプラグインが有効になっていることを確認します。   

    ![ServiceNow アカウント](./media/servicenow-account.png "ServiceNow アカウント")   

4.  Cloud App Security のポータルで [**調査**]、[**承認されたアプリ**] の順にクリックします。   

5.  [ServiceNow] 行の [**アプリ コネクタの状態**] 列で [**接続**] をクリックするか、または [**アプリを接続**] ボタンをクリックして [**ServiceNow**] を選択します。   

    ![ServiceNow を接続する](./media/connect-servicenow.png "ServiceNow を接続する")   

6.  ServiceNow の設定ページの [API] タブで、該当するボックスに ServiceNow ユーザー ID、パスワード、およびインスタンス URL を追加します。   

7.  **[接続]**をクリックします。   

   ![ServiceNow のパスワードの更新](./media/servicenow-update-password.png "ServiceNow のパスワードの更新")   

8.  [**API のテスト**] をクリックして、正常に接続されたことを確認します。   
  
   テストには数分かかる場合があります。 成功通知を受信したら、 [**閉じる**] をクリックします。   
 ServiceNow を接続すると、接続までの 60 日間のイベントを受け取ります。 


## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
