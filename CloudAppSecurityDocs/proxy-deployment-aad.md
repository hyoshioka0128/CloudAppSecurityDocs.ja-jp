---
title: "Azure AD アプリの Cloud App Security プロキシのデプロイ | Microsoft Docs"
description: "このトピックでは、Azure AD アプリの Microsoft Cloud App Security プロキシをデプロイする方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/17/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: a784b9e935bfa3396a64edb12202b50be17a7319
ms.sourcegitcommit: e547c4c91d8de9d4da376e4d4eebbe18c503b7ca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2017
---
# <a name="deploy-proxy-for-azure-ad-apps"></a>Azure AD アプリのプロキシをデプロイする

> [!NOTE]
> これはプレビュー機能です。

Cloud App Security プロキシによって制御されるように Azure AD アプリを構成するには、以下の手順に従います。

> [!NOTE]
> Azure AD アプリの Cloud App Security プロキシをデプロイするには、有効な [Azure AD Premium P2 のライセンス](https://docs.microsoft.com/azure/active-directory/license-users-groups)が必要です。

## <a name="step-1-add-azure-ad-apps-in-cloud-app-security"></a>手順 1: Cloud App Security に Azure AD アプリを追加する  

1. Azure AD 条件付きアクセスの TEST ポリシーを作成します。

    1. Azure Active Directory の **[セキュリティ]** で、**[条件付きアクセス]** をクリックします。

     ![Azure AD の条件付きアクセス](./media/aad-conditional-access.png)

    2. **[新しいポリシー]** をクリックし、新しいポリシーを作成します。**[セッション]** で必ず **[プロキシによって適用される制限を使用する]** を選択します。

     ![Azure AD の条件付きアクセス](./media/proxy-deploy-restrictions-aad.png)

    3. TEST ポリシーの **[ユーザー]** で、初期サインオンに使用できるテスト ユーザーまたはユーザーを割り当てます。
    
    4. TEST ポリシーの **[クラウド アプリ]** で、プロキシで制御するアプリを割り当てます。 

     > [!NOTE]
     >必ず、プロキシでサポートされているアプリを選択してください。 プロキシでは、Azure AD の SAML シングル サインオンで構成されているアプリがサポートされます。 たとえば、Office 365 アプリケーションは SAML で構成されていないため、現在はサポートされていません。


2.  ポリシーを作成したら、ポリシーに構成されているユーザーで、ポリシーに構成されている各アプリにログインします。 必ず、最初に既存のセッションからログアウトしてください。

3.  Cloud App Security ポータルで、設定の歯車アイコンに移動して **[プロキシ]** を選択します。 
    
      ![プロキシ メニュー](./media/proxy-menu.png)

4.  新しい Azure AD アプリがプロキシで検出されたことを知らせるメッセージが表示されます。 **[新しいアプリを表示します]** リンクをクリックします。

 ![プロキシの新しいアプリの表示](./media/proxy-view-new-apps.png)

5.  開いたダイアログで、前の手順でログインしたすべてのアプリを確認できます。 アプリごとに、+ 記号をクリックしてから **[追加]** をクリックします。

 ![プロキシの新しいアプリ](./media/proxy-new-app.png)

 > [!NOTE]
 > アプリが Cloud App Security アプリ カタログに表示されない場合は、ダイアログの定義されていないアプリの下にログイン URL と共に表示されます。 これらのアプリの + 記号をクリックするときに、カタログへのアプリの追加を提案することができます。 アプリがカタログに表示されたら、アプリのデプロイ手順を再度実行します。 

6.  プロキシ アプリ テーブルで、**[利用可能なコントロール]** 列を参照し、Azure AD の条件付きアクセスとセッション制御の両方が表示されていることを確認します。 <br></br>アプリのセッション制御が表示されない場合、その特定のアプリではまだ使用できないことを意味し、代わりに **[要求セッション制御]** リンクが表示されます。 それをクリックしてダイアログを開き、セッション制御へのアプリのオンボードを要求します。 プロキシのパブリック プレビュー期間中は、オンボード プロセスは Cloud App Security チームと共に行います。
  
 ![セッション制御の要求](./media/request-session-control.png)

7. 省略可能 - 次のように、クライアント証明書を使用してデバイスを識別します。

      1. 設定の歯車アイコンに移動して、**[デバイスの識別]** を選択します。

      2. ルート証明書をアップロードします。

        ![デバイスの識別](./media/device-identification.png)
 
       証明書がアップロードされたら、**[デバイス タグ]** の [次の値と等しい] または [次の値に等しくない]、**[有効なクライアント証明書]** に基づいて、アクセス ポリシーとセッション ポリシーを作成できます。
 
      > [!NOTE]
      >証明書がユーザーから要求されるのは、セッションが有効なクライアント証明書フィルターを使用するポリシーと一致する場合だけです。 

## <a name="step-2-test-the-deployment"></a>手順 2: デプロイをテストする

1. まず、既存のセッションからログアウトします。 次に、Azure AD で構成されているポリシーと一致するユーザーを使用して、正常にデプロイされた各アプリにログインしてみます。 

2.  Cloud App Security ポータルの **[調査]** で、**[アクティビティ ログ]** を選択し、アプリごとにログイン アクティビティがキャプチャされていることを確認します。

3.  **[詳細]** をクリックし、**[ソース]、[次の値と等しい]、[Azure Active Directory 条件付きアクセス]** を使用してフィルター処理を行うことができます。

     ![Azure AD の条件付きアクセスを使用するフィルター処理](./media/sso-logon.png)

3. 管理対象デバイスと管理されていないデバイスからモバイル アプリやデスクトップ アプリにログインし、アクティビティがアクティビティ ログに適切にキャプチャされていることを確認することをお勧めします。<br></br>
アクティビティが適切にキャプチャされていることを確認するには、シングル サインオン ログオン アクティビティをクリックしてアクティビティ ドロアーを開き、**[ユーザー エージェント タグ]** に、デバイスがネイティブ クライアント (モバイルまたはデスクトップ アプリのいずれかであることを意味する) であるか、またはデバイスが管理対象デバイス (準拠、ドメイン参加済み、または有効なクライアント証明書) であるかが適切に反映されていることを確認します。
 
 ![テストのユーザー エージェント タグ](./media/domain-joined.png)


これで、プロキシ アプリを制御するための[アクセス ポリシー](access-policy-aad.md)と[セッション ポリシー](session-policy-aad.md)を作成できるようになりました。



## <a name="see-also"></a>参照  
[Cloud App Security プロキシの操作](proxy-intro-aad.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  