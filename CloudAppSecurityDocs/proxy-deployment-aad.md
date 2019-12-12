---
title: Azure AD アプリの Cloud App Security Conditional Access App Control をデプロイする
description: この記事では、Azure AD アプリの Microsoft Cloud App Security のアプリの条件付きアクセス制御リバース プロキシ機能をデプロイする方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 290429e345e6b814a34a3e9214b5f69fdcbf7ddf
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74720928"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>フィーチャー アプリでの条件付きアクセス アプリ制御の展開

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security のセッションコントロールは、おすすめアプリで動作します。 Cloud App Security で利用できるアプリの一覧については、「 [Microsoft Cloud App Security アプリの条件付きアクセス制御を使用](proxy-intro-aad.md#featured-apps)したアプリの保護」を参照してください。

## <a name="prerequisites"></a>必要条件

Azure AD アプリに対してアプリの条件付きアクセス制御をデプロイするには、Cloud App Security ライセンスと共に有効な [Azure AD Premium P1 のライセンス](https://docs.microsoft.com/azure/active-directory/license-users-groups)が必要になります。

## <a name="to-deploy-featured-apps"></a>おすすめアプリを展開するには

次の手順に従って、Microsoft Cloud App Security アプリの条件付きアクセス制御によって制御されるおすすめアプリを構成します。

**手順 1: [Azure AD ポータルにアクセスし、アプリの条件付きアクセスポリシーを作成して、セッションをルーティング Cloud App Security](#add-azure-ad)**

**手順 2:[ポリシーの対象となるユーザーを使用して各アプリにサインインする](#sign-in-scoped)**

**手順 3:[アクセスとセッション制御を使用するようにアプリが構成されていることを確認する](#portal)**

**手順 4:[デプロイをテストする](#test)**

## 手順 1: Azure AD 条件付きアクセステストポリシーを作成する<a name="add-azure-ad"></a>

1. Azure Active Directory の **[セキュリティ]** で、 **[条件付きアクセス]** をクリックします。

1. **[新しいポリシー]** をクリックして新しいポリシーを作成します。

1. TEST ポリシーの **[ユーザー]** の下で、初期サインオンと検証に使用できるテスト ユーザーまたはユーザーを割り当てます。

1. TEST ポリシーの **[クラウド アプリ]** で、Conditional Access App Control で制御するアプリを割り当てます。

1. **[セッション]** の下で、組み込みのポリシーである **[監視のみ]** または **[ダウンロードを禁止する]** のどちらかを使用するように、ポリシーを設定します。 または、 **[カスタム ポリシーを使用する]** を選択して、Cloud App Security ポータル内で詳細なポリシーを設定します。

1. 該当する **[Condition assignments]** \(条件に同意する\) または **[制御の許可]** を追加します (省略可能)。

    ![Azure AD 条件付きアクセス](media/azure-ad-caac-policy.png)

1. **[有効]** をクリックして**保存**します。

## 手順 2: ポリシーの対象となるユーザーを使用して各アプリにサインインする<a name="sign-in-scoped"></a>

> [!NOTE]
> 続行する前に、まず既存のセッションからサインアウトしてください。

ポリシーを作成したら、そのポリシーで構成されている各アプリにサインインします。 必ずポリシーで構成されているユーザーでサインインしてください。

Cloud App Security によって、サインインする新しい各アプリのポリシーの詳細がサーバーに同期されます。 これには最大 で1 分かかることがあります。

## 手順 3: アクセスとセッション制御を使用するようにアプリが構成されていることを確認する<a name="portal"></a>

上記の手順を利用して、おすすめアプリ用の組み込みの Cloud App Security ポリシーを Azure AD 内に直接作成できました。 この手順では、これらのアプリに対してアクセス制御とセッション制御が構成されていることを確認します。

1. Cloud App Security ポータルで、[設定] 歯車![設定アイコン](media/settings-icon.png "設定アイコン")をクリックし、 **[アプリの条件付きアクセス制御]** を選択します。

1. アプリの条件付きアクセス制御 apps テーブルで、**使用可能なコントロール** 列を確認し、アプリに対して**アクセス制御**と**セッション制御**の両方が表示されていることを確認します。

    > [!NOTE]
    > アプリのセッション制御が表示されない場合は、その特定のアプリではまだ使用できません。 [カスタムアプリ](proxy-deployment-any-app.md)としてすぐに追加することも、要求を開いて **[セッション制御の要求]** をクリックすることでおすすめアプリとして追加することもできます。
    >
    >![アプリの条件付きアクセス制御の要求](media/caac-request.png)

## 手順 4: デプロイをテストする<a name="test"></a>

1. まず、既存のセッションからサインアウトします。 次に、正常にデプロイされた各アプリにサインインします。 Azure AD で構成されているポリシーと一致するユーザーでサインインしてください。

1. Cloud App Security ポータルの **[調査]** で、 **[アクティビティ ログ]** を選択し、アプリごとにログイン アクティビティがキャプチャされていることを確認します。

1. フィルター処理は、 **[詳細]** をクリックし、 **[Source equals Access control]** \(ソースがアクセス制御と等しい\) を使用してフィルター処理することで実行できます。

    ![Azure AD の条件付きアクセスを使用するフィルター処理](media/sso-logon.png)

1. マネージド デバイスとアンマネージド デバイスからモバイルおよびデスクトップのアプリにサインインすることをお勧めします。 これは、アクティビティ ログで、アクティビティを正常にキャプチャするためです。<br />
アクティビティが正常にキャプチャされたことを確認するには、アクティビティ ドロワーが開くようにシングル サインオン ログオン アクティビティをクリックします。 **[ユーザー エージェント タグ]** に、デバイスがネイティブ クライアント (モバイルまたはデスクトップ アプリのいずれかであることを意味する) であるか、またはデバイスがマネージド デバイス (準拠、ドメイン参加済み、または有効なクライアント証明書) であるかが適切に反映されていることを確認します。

> [!NOTE]
> デプロイ後は、[アプリの条件付きアクセス制御] ページからアプリを削除することはできません。 アプリにセッションやアクセス ポリシーを設定しないかぎり、アプリの条件付きアクセス制御でアプリの動作が変更されることは一切ありません。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [アクセスポリシーを作成する方法](access-policy-aad.md)

## <a name="see-also"></a>「

> [!div class="nextstepaction"]
> [アプリの条件付きアクセス制御の概要](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [Cloud App Security Conditional Access App Control の操作](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [任意のアプリにアプリの条件付きアクセス制御をデプロイする»](proxy-deployment-any-app.md)

[!INCLUDE [Open support ticket](includes/support.md)]
