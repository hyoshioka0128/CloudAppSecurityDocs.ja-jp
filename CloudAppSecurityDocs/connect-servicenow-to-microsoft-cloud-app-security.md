---
title: ServiceNow を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に ServiceNow アプリを接続する方法に関する情報を提供します。
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 6/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c626d94d-2ffd-4daf-8fa4-4b6d308cf012
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 81272602fcdab13b8a0e5ffff85c4eec8ebf968d
ms.sourcegitcommit: 8fd13c10c2f66a553a8a8fc413555ca837fc9c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610771"
---
# <a name="connect-servicenow-to-microsoft-cloud-app-security"></a>ServiceNow を Microsoft Cloud App Security に接続する

*適用対象:Microsoft Cloud App Security*

この記事では、App Connector API を使用して Microsoft Cloud App Security を既存の ServiceNow アカウントに接続する方法を説明します。 この接続により、ServiceNow の使用状況を視覚化して制御できるようになります。

> [!NOTE]
>  Fuji 以降のリリースで使用可能な OAuth アプリ トークンを使用して ServiceNow を展開することをお勧めします (関連する [ServiceNow ドキュメント](https://wiki.servicenow.com/index.php?title=OAuth_Applications#gsc.tab=0)を参照)。 以前のリリースの場合は、[レガシー接続モード](#legacy-servicenow-connection)がユーザー/パスワードに基づいて使用可能です。 指定したユーザー名/パスワードは、API トークンの生成にのみ使用され、最初の接続処理後に保存されません。
> 
> [!NOTE]
>  Cloud App Security には、ジャカルタ、Kingston、Eureka、Fiji、Geneva、ヘルシンキ、イスタンブール、ロンドン、およびマドリッドのバージョンの ServiceNow がサポートしています。 ServiceNow を Cloud App Security に接続するには、**管理者**ロールが必要であるほか、ServiceNow インスタンスが API アクセスをサポートしていることを確認する必要があります。  詳細については、「[ServiceNow Product Documentation](https://wiki.servicenow.com/index.php?title=Base_System_Roles#gsc.tab=0)」 (ServiceNow 製品ドキュメント) を参照してください。
  
## <a name="how-to-connect-servicenow-to-cloud-app-security-using-oauth"></a>OAuth を使用して ServiceNow を Cloud App Security に接続する方法
  
  
1. ServiceNow アカウントに管理者アカウントでサインインします。  
 
   > [!NOTE]
   >  指定したユーザー名/パスワードは、API トークンの生成にのみ使用され、最初の接続処理後に保存されません。

2. **[Filter navigator (フィルター ナビゲーター)]** 検索バーに「**OAuth**」と入力し、 **[アプリケーション レジストリ]** を選択します。

3. **[アプリケーション レジストリ]** メニュー バーで、 **[新規作成]** をクリックし、新しい OAuth プロファイルを作成します。

   ![ServiceNow の新しい OAuth プロファイル](./media/servicenow-app-registry.png)

4. **[What kind of OAuth application? (OAuth アプリケーションの種類は?)]** で **[Create an OAuth API endpoint for external clients (外部クライアントの OAuth API エンドポイントを作成する)]** をクリックします。

   ![ServiceNow OAuth の種類](./media/servicenow-oauth-app-type.png)

5. **[Application Registries New record (アプリケーション レジストリの新しいレコード)]** の次のフィールドに入力します。
    
    - **[名前]** フィールドに新しい OAuth プロファイルの名前を入力します。たとえば、「CloudAppSecurity」にします。 
    
    - **[クライアント ID]** は自動的に生成されます。 この ID をコピーします。接続を完了するには、これを Cloud App Security に貼り付ける必要があります。
    
    - **[クライアント シークレット]** フィールドに文字列を入力します。 空のままにすると、無作為のシークレットが自動的に生成されます。 後で使用するためにコピーし、保存します。 
    
    - **[Access Token Lifespan (アクセス トークン有効期間)]** を 3,600 以上に増やします。
    
    - **[送信]** をクリックします。

   ![ServiceNow プロファイル ID](./media/servicenow-profile-ids.png)

6. Cloud App Security ポータルで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。  
  
7. **[アプリ コネクター]** ページで、[+] ボタン、 **[ServiceNow]** の順にクリックします。  
  
    ![ServiceNow を接続する](./media/connect-servicenow.png "ServiceNow を接続する")  
  
8. ポップアップの該当するボックスに ServiceNow のユーザー ID、パスワード、インスタンス URL、クライアント ID、クライアント シークレットを追加します。 ServiceNow のユーザー ID を見つけるには、ServiceNow ポータルの **[ユーザー]** に移動して、テーブルの自分の名前を見つけます。

   ![ServiceNow ユーザー ID](./media/servicenow-userid.png)
  
9. **[接続]** をクリックします。  
  
    ![ServiceNow を CAS に接続する](./media/servicenow-portal-connect.png "ポータルで ServiceNow を接続する")  
  
10. **[今すぐテスト]** をクリックし、正常に接続されたことを確認します。  
  
    テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。  
  
ServiceNow を接続すると、接続までの 60 日間のイベントを受け取ります。
  
## <a name="legacy-servicenow-connection"></a>レガシー ServiceNow 接続

ServiceNow を Cloud App Security に接続するには、管理者レベルのアクセス許可が必要であるほか、ServiceNow インスタンスが API アクセスをサポートしていることを確認する必要があります。   

1. ServiceNow アカウントに管理者アカウントでサインインします。   

2. Cloud App Security 用の新しいサービス アカウントを作成し、その新しいアカウントに管理者のロールを与えます。   

3. REST API のプラグインが有効になっていることを確認します。   

   ![ServiceNow アカウント](./media/servicenow-account.png "ServiceNow アカウント")   

4. Cloud App Security のポータルで **[調査]** 、 **[承認されたアプリ]** の順にクリックします。   

5. ServiceNow 行の **アプリ コネクタの状態** 列で **接続** をクリックするか、または **アプリを接続** ボタンをクリックして **ServiceNow** を選択します。   

   ![ServiceNow を接続する](./media/connect-servicenow.png "ServiceNow を接続する")   

6. ServiceNow の設定ページの [API] タブで、該当するボックスに ServiceNow ユーザー ID、パスワード、およびインスタンス URL を追加します。   

7. **[接続]** をクリックします。   

   ![ServiceNow のパスワードの更新](./media/servicenow-update-password.png "ServiceNow のパスワードの更新")   

8. **[API のテスト]** をクリックして、正常に接続されたことを確認します。   
  
   テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。    
   ServiceNow を接続すると、接続までの 60 日間のイベントを受け取ります。 


## <a name="next-steps"></a>次の手順 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
