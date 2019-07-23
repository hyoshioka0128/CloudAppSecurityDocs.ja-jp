---
title: Azure AD アプリの Cloud App Security Conditional Access App Control をデプロイする
description: この記事では、Azure AD アプリの Microsoft Cloud App Security のアプリの条件付きアクセス制御リバース プロキシ機能をデプロイする方法について説明します。
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/12/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 2490c5e5-e723-4fc2-a5e0-d0a3a7d01fc2
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6f12926e79e7f3311737cc734e2eec8a60bfb752
ms.sourcegitcommit: cad2ead82bb76e4749c75eb7a0594e97f40545db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372367"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>フィーチャー アプリでの条件付きアクセス アプリ制御の展開

*適用対象:Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« 戻る: 条件付きのアクセス アプリ制御の概要](proxy-intro-aad.md)<br>
[次へ: すべてのアプリに対してアプリの条件付きアクセス制御のオンボードとデプロイを行う»](proxy-deployment-any-app.md)

次の手順に従って、Microsoft Cloud App Security アプリの条件付きアクセス制御によって制御されるおすすめアプリを構成します。

**ステップ 1: [Azure AD ポータルにアクセスし、アプリの条件付きアクセスポリシーを作成して、セッションをルーティング Cloud App Security](#add-azure-ad)**

**手順 2:[ポリシーをスコープとするユーザーを使用して、各アプリにサインインします。](#sign-in-scoped)**

**手順 3:Azure AD で組み込みの Cloud App Security ポリシーを選択しなかった場合、または任意のアプリにポリシーを適用する場合は、 [Cloud App Security ポータルにアクセス](#portal)します。**

[**手順 4: デプロイをテストする**](#test)

> [!NOTE]
> Azure AD アプリに対してアプリの条件付きアクセス制御をデプロイするには、Cloud App Security ライセンスと共に有効な [Azure AD Premium P1 のライセンス](https://docs.microsoft.com/azure/active-directory/license-users-groups)が必要になります。

## 手順 1:Azure AD 条件付きアクセスの TEST ポリシーを作成する<a name="add-azure-ad"></a>  

1. Azure Active Directory の **[セキュリティ]** で、 **[条件付きアクセス]** をクリックします。

2. **[新しいポリシー]** をクリックして新しいポリシーを作成します。

3. TEST ポリシーの **[ユーザー]** の下で、初期サインオンと検証に使用できるテスト ユーザーまたはユーザーを割り当てます。

4. TEST ポリシーの **[クラウド アプリ]** で、Conditional Access App Control で制御するアプリを割り当てます。 

5. **[セッション]** の下で、組み込みのポリシーである **[監視のみ]** または **[ダウンロードを禁止する]** のどちらかを使用するように、ポリシーを設定します。 または、 **[カスタム ポリシーを使用する]** を選択して、Cloud App Security ポータル内で詳細なポリシーを設定します。 

6. 該当する **[Condition assignments]** \(条件に同意する\) または **[制御の許可]** を追加します (省略可能)。

   ![Azure AD 条件付きアクセス](./media/azure-ad-caac-policy.png)

      > [!NOTE]
      >アプリの条件付きアクセス制御では、これらのおすすめ以外のアプリを含め、Azure AD のシングル サインオンを利用して構成されている SAML または OpenID 接続のアプリをサポートしています。 おすすめ以外のアプリは、Cloud App Security ポータル内のアクセス制御を利用して、セッション制御を使ってオンボードされているアプリに対して要求を行うことで、構成できます。 

7. **[有効]** をクリックして**保存**します。

## 手順 2:ポリシーをスコープとするユーザーを使用して、各アプリにサインインします。<a name="sign-in-scoped"></a>

ポリシーを作成したら、そのポリシーで構成されている各アプリにサインインします。 必ずポリシーで構成されているユーザーでサインインしてください。 最初に、既存のセッションからサインアウトしてください。

Cloud App Security によって、サインインする新しい各アプリのポリシーの詳細がサーバーに同期されます。  これには最大 で1 分かかることがあります。

## 手順 3:Cloud App Security ポータルでの高度なコントロールとアプリの構成<a name="portal"></a>

上記の手順を利用して、おすすめアプリ用の組み込みの Cloud App Security ポリシーを Azure AD 内に直接作成できました。

高度なポリシーを構成するには、Cloud App Security で[アクセスポリシー](access-policy-aad.md)または[セッションポリシー](session-policy-aad.md)を作成します。

任意のアプリにポリシーを適用するには、手順に従って、[アプリの条件付きアクセス制御で使用する任意のアプリをセルフオンボード](proxy-deployment-any-app.md)します。

任意のアプリのサポートを要求するには、次のようにします。

1. Cloud App Security ポータルで、設定の歯車アイコンに移動して **[Conditional Access App Control]** を選択します。 新しい Azure AD アプリが Conditional Access App Control で検出されたことを知らせるメッセージが表示されます。

    ![アプリの条件付きアクセス制御のメニュー](./media/caac-menu.png)

2. **[View new apps]** \(新しいアプリの表示\) をクリックします。

    ![アプリの条件付きアクセス制御に表示された新しいアプリ](./media/caac-view-apps.png)

3. 開いた画面で、前の手順でログインしたすべてのアプリを確認できます。 アプリごとに、+ 記号をクリックしてから **[追加]** をクリックします。

   > [!NOTE]
   > アプリが Cloud App Security アプリ カタログに表示されない場合は、ダイアログの定義されていないアプリの下にログイン URL と共に表示されます。 これらのアプリの + 記号をクリックすると、カスタム アプリとしてアプリケーションをオンボードできます。

   ![アプリの条件付きアクセス制御で検出された Azure AD アプリ](./media/caac-discovered-aad-apps.png)

4. アプリの条件付きアクセス制御のアプリ テーブルで、 **[利用可能なコントロール]** 列を参照し、**Azure AD 条件付きアクセス**と**セッション制御**の両方が表示されていることを確認します。

   > [!NOTE]
   > アプリのセッション制御が表示されない場合、該当のアプリでは使用できません。 代わりに、 **[要求セッション制御]** のリンクが表示されます。

     ![アプリの条件付きアクセス制御の要求](./media/caac-request.png)

5. **[要求セッション制御]** をクリックして、アプリがセッション制御にオンボードされるように要求します。 オンボード プロセスは、Microsoft Cloud App Security チームと共に行います。

6. クライアント証明書を使用してデバイス管理を活用するようにポリシーを構成するには:
    1. 設定の歯車アイコンに移動して、 **[デバイスの識別]** を選択します。
    2. 1 つ以上のルート証明書または中間証明書をアップロードします。
    3. 証明書がアップロードされたら、 **[デバイス タグ]** と **[有効なクライアント証明書]** に基づいて、アクセス ポリシーとセッション ポリシーを作成できます。

       ![アプリの条件付きアクセス制御のデバイス ID](./media/caac-device-id.png)

> [!NOTE]
> 証明書がユーザーから要求されるのは、セッションが有効なクライアント証明書フィルターを使用するポリシーと一致する場合だけです。

## 手順 4:デプロイをテストする<a name="test"></a>

1. まず、既存のセッションからサインアウトします。 次に、正常にデプロイされた各アプリにサインインします。 Azure AD で構成されているポリシーと一致するユーザーでサインインしてください。

2. Cloud App Security ポータルの **[調査]** で、 **[アクティビティ ログ]** を選択し、アプリごとにログイン アクティビティがキャプチャされていることを確認します。

3. フィルター処理は、 **[詳細]** をクリックし、 **[Source equals Access control]** \(ソースがアクセス制御と等しい\) を使用してフィルター処理することで実行できます。

    ![Azure AD の条件付きアクセスを使用するフィルター処理](./media/sso-logon.png)

4. マネージド デバイスとアンマネージド デバイスからモバイルおよびデスクトップのアプリにサインインすることをお勧めします。 これは、アクティビティ ログで、アクティビティを正常にキャプチャするためです。<br>
アクティビティが正常にキャプチャされたことを確認するには、アクティビティ ドロワーが開くようにシングル サインオン ログオン アクティビティをクリックします。 **[ユーザー エージェント タグ]** に、デバイスがネイティブ クライアント (モバイルまたはデスクトップ アプリのいずれかであることを意味する) であるか、またはデバイスがマネージド デバイス (準拠、ドメイン参加済み、または有効なクライアント証明書) であるかが適切に反映されていることを確認します。

> [!NOTE]
> デプロイ後は、[アプリの条件付きアクセス制御] ページからアプリを削除することはできません。 アプリにセッションやアクセス ポリシーを設定しないかぎり、アプリの条件付きアクセス制御でアプリの動作が変更されることは一切ありません。

>[!div class="step-by-step"]
[« 戻る: 条件付きのアクセス アプリ制御の概要](proxy-intro-aad.md)<br>[次へ: すべてのアプリに対してアプリの条件付きアクセス制御のオンボードとデプロイを行う»](proxy-deployment-any-app.md)

## <a name="next-steps"></a>次の手順 
[Cloud App Security アプリの条件付きアクセス制御の操作](proxy-intro-aad.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)