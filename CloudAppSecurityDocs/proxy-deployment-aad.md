---
title: Azure AD アプリの Microsoft Cloud App Security Conditional Access App Control をデプロイする | Microsoft Docs
description: このトピックでは、Azure AD アプリの Microsoft Cloud App Security Conditional Access App Control リバース プロキシ機能をデプロイする方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/5/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 636c0e407db3a7460cf64a76dc82133e7febf4c9
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143345"
---
*適用対象: Microsoft Cloud App Security*

# <a name="deploy-conditional-access-app-control-for-azure-ad-apps"></a>Azure AD アプリの Conditional Access App Control のデプロイ

>[!div class="step-by-step"]
[« 戻る: 条件付きのアクセス アプリ制御の概要](proxy-intro-aad.md)<br>
[次へ: セッション ポリシーを作成する方法 »](session-policy-aad.md)


Microsoft Cloud App Security Conditional Access App Control によって制御されるように Azure AD アプリを構成するには、以下の手順に従います。

**手順 1: [Azure AD ポータルに移動してアプリの条件付きアクセス ポリシーを作成し、セッションを Cloud App Security にルーティングします](#add-azure-ad)。**

**手順 2: [ポリシーのスコープに含まれるユーザーでアプリにサインインします](#sign-in-scoped)。**

**手順 3: [Cloud App Security ポータルに戻り、アプリを追加するバナー通知を選択します](#banner-notification)。**

**手順 4: Cloud App Security 内のアプリのために、[アクセス ポリシーを作成](access-policy-aad.md)するか、[セッション ポリシーを作成](session-policy-aad.md)します。**


> [!NOTE]
> Azure AD アプリに対するアプリの条件付きアクセス制御をデプロイするには、有効な [Azure AD Premium P1 のライセンス](https://docs.microsoft.com/azure/active-directory/license-users-groups)が必要です。

## 手順 1: Cloud App Security に Azure AD アプリを追加する <a name="add-azure-ad"></a>  

1. Azure AD 条件付きアクセスの TEST ポリシーを作成します。

   1. Azure Active Directory の **[セキュリティ]** で、**[条件付きアクセス]** をクリックします。

      ![Azure AD の条件付きアクセス](./media/aad-conditional-access.png)

   2. **[新しいポリシー]** をクリックし、新しいポリシーを作成します。その場合、**[セッション]** で必ず **[Use Conditional Access App Control enforced restrictions]\(Conditional Access App Control によって適用される制限を使用する\)** を選択します。

      ![Azure AD の条件付きアクセス](./media/proxy-deploy-restrictions-aad.png)

   3. TEST ポリシーの **[ユーザー]** で、初期サインオンに使用できるテスト ユーザーまたはユーザーを割り当てます。
    
   4. TEST ポリシーの **[クラウド アプリ]** で、Conditional Access App Control で制御するアプリを割り当てます。 

      > [!NOTE]
      >必ず、Conditional Access App Control でサポートされているアプリを選択してください。 Conditional Access App Control では、Azure AD の SAML シングル サインオンで構成されているアプリがサポートされます。 たとえば、Office 365 アプリケーションは SAML で構成されていないため、現在はサポートされていません。

## 手順 2: ポリシーのスコープに含まれるユーザーでアプリにサインインする <a name="sign-in-scoped"></a>

ポリシーを作成したら、ポリシーに構成されているユーザーで、ポリシーに構成されている各アプリにログインします。 必ず、最初に既存のセッションからログアウトしてください。

## 手順 3: Cloud App Security ポータルに戻り、アプリを追加するバナー通知を選択する <a name="banner-notification"></a>

1. Cloud App Security ポータルで、設定の歯車アイコンに移動して **[Conditional Access App Control]** を選択します。 
    
     ![プロキシ メニュー](./media/proxy-menu.png)

2. 新しい Azure AD アプリが Conditional Access App Control で検出されたことを知らせるメッセージが表示されます。 **[新しいアプリを表示します]** リンクをクリックします。

   ![Conditional Access App Control の [新しいアプリを表示します]](./media/proxy-view-new-apps.png)

3. 開いたダイアログで、前の手順でログインしたすべてのアプリを確認できます。 アプリごとに、+ 記号をクリックしてから **[追加]** をクリックします。

   ![Conditional Access App Control の新しいアプリ](./media/proxy-new-app.png)

   > [!NOTE]
   > アプリが Cloud App Security アプリ カタログに表示されない場合は、ダイアログの定義されていないアプリの下にログイン URL と共に表示されます。 これらのアプリの + 記号をクリックするときに、カタログへのアプリの追加を提案することができます。 アプリがカタログに表示されたら、アプリのデプロイ手順を再度実行します。 

4. Conditional Access App Control アプリ テーブルで、**[利用可能なコントロール]** 列を参照し、Azure AD の条件付きアクセスとセッション制御の両方が表示されていることを確認します。 <br></br>アプリのセッション制御が表示されない場合、その特定のアプリではまだ使用できないことを意味し、代わりに **[要求セッション制御]** リンクが表示されます。 それをクリックしてダイアログを開き、セッション制御へのアプリのオンボードを要求します。 このシナリオでは、オンボード プロセスは Microsoft Cloud App Security チームと共に行います。
  
   ![セッション制御の要求](./media/proxy-view-new-apps.png)

5. 省略可能 - 次のように、クライアント証明書を使用してデバイスを識別します。

   1. 設定の歯車アイコンに移動して、**[デバイスの識別]** を選択します。

   2. ルート証明書をアップロードします。

      ![デバイスの識別](./media/device-identification.png)
 
      証明書がアップロードされたら、**[デバイス タグ]** の [次の値と等しい] または [次の値に等しくない]、**[有効なクライアント証明書]** に基づいて、アクセス ポリシーとセッション ポリシーを作成できます。
 
      > [!NOTE]
      >証明書がユーザーから要求されるのは、セッションが有効なクライアント証明書フィルターを使用するポリシーと一致する場合だけです。 

## <a name="test-the-deployment"></a>デプロイをテストする

1. まず、既存のセッションからログアウトします。 次に、Azure AD で構成されているポリシーと一致するユーザーを使用して、正常にデプロイされた各アプリにログインしてみます。 

2. Cloud App Security ポータルの **[調査]** で、**[アクティビティ ログ]** を選択し、アプリごとにログイン アクティビティがキャプチャされていることを確認します。

3. **[詳細]** をクリックし、**[ソース]、[次の値と等しい]、[Azure Active Directory 条件付きアクセス]** を使用してフィルター処理を行うことができます。

    ![Azure AD の条件付きアクセスを使用するフィルター処理](./media/sso-logon.png)

4. マネージド デバイスとアンマネージド デバイスからモバイル アプリやデスクトップ アプリにログインし、アクティビティがアクティビティ ログに適切にキャプチャされていることを確認することをお勧めします。<br></br>
   アクティビティが適切にキャプチャされていることを確認するには、シングル サインオン ログオン アクティビティをクリックしてアクティビティ ドロアーを開き、**[ユーザー エージェント タグ]** に、デバイスがネイティブ クライアント (モバイルまたはデスクトップ アプリのいずれかであることを意味する) であるか、またはデバイスがマネージド デバイス (準拠、ドメイン参加済み、または有効なクライアント証明書) であるかが適切に反映されていることを確認します。
 
   ![テストのユーザー エージェント タグ](./media/domain-joined.png)


これで、Conditional Access App Control アプリを制御するための[アクセス ポリシー](access-policy-aad.md)と[セッション ポリシー](session-policy-aad.md)を作成できるようになりました。


>[!div class="step-by-step"]
[« 戻る: 条件付きのアクセス アプリ制御の概要](proxy-intro-aad.md)<br>
[次へ: セッション ポリシーを作成する方法 »](session-policy-aad.md)


## <a name="see-also"></a>参照  
[Cloud App Security Conditional Access App Control の操作](proxy-intro-aad.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  