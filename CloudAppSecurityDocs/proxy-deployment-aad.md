---
title: Azure AD アプリの Cloud App Security アプリの条件付きアクセス制御のデプロイ
description: この記事では、Azure AD アプリのリバースプロキシ機能アプリの条件付きアクセス制御 Microsoft Cloud App Security を展開する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 0fc3f43aa76f64d1228a6e45d2fdc743a494a8e3
ms.sourcegitcommit: 3f6ef6b97a0953470135d115323a00cf11441ab7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2020
ms.locfileid: "78927777"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>フィーチャー アプリでの条件付きアクセス アプリ制御の展開

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security のセッションコントロールは、おすすめアプリで動作します。 Cloud App Security で利用できるアプリの一覧については、「 [Microsoft Cloud App Security アプリの条件付きアクセス制御を使用](proxy-intro-aad.md#featured-apps)したアプリの保護」を参照してください。

## <a name="prerequisites"></a>前提条件

Azure AD アプリのアプリの条件付きアクセス制御をデプロイするには、 [Azure AD Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups)と Cloud App Security ライセンスの有効なライセンスが必要です。

## <a name="to-deploy-featured-apps"></a>おすすめアプリを展開するには

次の手順に従って、Microsoft Cloud App Security アプリの条件付きアクセス制御によって制御されるおすすめアプリを構成します。

**手順 1: [Azure AD ポータルにアクセスし、アプリの条件付きアクセスポリシーを作成して、セッションをルーティング Cloud App Security](#add-azure-ad)**

**手順 2:[ポリシーの対象となるユーザーを使用して各アプリにサインインする](#sign-in-scoped)**

**手順 3:[アクセスとセッション制御を使用するようにアプリが構成されていることを確認する](#portal)**

**手順 4:[デプロイをテストする](#test)**

## 手順 1: Azure AD 条件付きアクセステストポリシーを作成する<a name="add-azure-ad"></a>

1. Azure Active Directory の **[セキュリティ]** で、 **[条件付きアクセス]** をクリックします。

1. **[新しいポリシー]** をクリックし、新しいポリシーを作成します。

1. テストポリシーの **[ユーザー]** で、初期サインオンと検証に使用できるテストユーザーまたはユーザーを割り当てます。

1. テストポリシーの **[クラウドアプリ]** で、アプリの条件付きアクセス制御で制御するアプリを割り当てます。

1. **[セッション]** で、組み込みのポリシーのいずれかを使用するようにポリシーを設定し、 **[監視のみ]** または **[ダウンロードのブロック]** を設定します。 または、[**カスタムポリシーを使用**する] を選択して、Cloud App Security ポータルで詳細ポリシーを設定します。

1. 適用可能な**条件割り当て**を追加するか、**コントロールを許可**します (省略可能)。

    ![Azure AD 条件付きアクセス](media/azure-ad-caac-policy.png)

1. **[有効]** をクリックして**保存**します。

## 手順 2: ポリシーの対象となるユーザーを使用して各アプリにサインインする<a name="sign-in-scoped"></a>

> [!NOTE]
> 続行する前に、まず既存のセッションからサインアウトしてください。

ポリシーを作成したら、そのポリシーで構成されている各アプリにサインインします。 ポリシーで構成されたユーザーを使用してサインインしていることを確認します。

Cloud App Security によって、サインインする新しい各アプリのポリシーの詳細がサーバーに同期されます。 これには最大1分かかることがあります。

## 手順 3: アクセスとセッション制御を使用するようにアプリが構成されていることを確認する<a name="portal"></a>

上記の手順を使用すると、おすすめアプリ用の組み込みの Cloud App Security ポリシーを Azure AD で直接作成できます。 この手順では、これらのアプリに対してアクセス制御とセッション制御が構成されていることを確認します。

1. Cloud App Security ポータルで、[設定] 歯車![設定アイコン](media/settings-icon.png "設定アイコン")をクリックし、 **[アプリの条件付きアクセス制御]** を選択します。

1. アプリの条件付きアクセス制御 apps テーブルで、**使用可能なコントロール** 列を確認し、アプリに対して**アクセス制御**と**セッション制御**の両方が表示されていることを確認します。

    > [!NOTE]
    > アプリのセッション制御が表示されない場合は、その特定のアプリではまだ使用できません。 [カスタムアプリ](proxy-deployment-any-app.md)としてすぐに追加することも、要求を開いて **[セッション制御の要求]** をクリックすることでおすすめアプリとして追加することもできます。
    >
    >![アプリ制御要求の条件付きアクセス](media/caac-request.png)

## 手順 4: デプロイをテストする<a name="test"></a>

1. 既存のセッションから最初にサインアウトします。 次に、正常に展開された各アプリにサインインします。 Azure AD で構成されたポリシーに一致するユーザーを使用してサインインします。

1. Cloud App Security ポータルの **[調査]** で **[アクティビティログ]** を選択し、アプリごとにログインアクティビティがキャプチャされていることを確認します。

1. フィルター処理を行うには、 **[詳細設定]** をクリックし、 **[ソース]** を使用してフィルター処理します。

    ![Azure AD 条件付きアクセスを使用してフィルター処理する](media/sso-logon.png)

1. 管理されたデバイスと管理されていないデバイスからモバイルアプリおよびデスクトップアプリにサインインすることをお勧めします。 これは、アクティビティがアクティビティログに適切にキャプチャされるようにするためです。<br />
アクティビティが正しくキャプチャされていることを確認するには、アクティビティドロワーを開くために、[シングルサインオンのログオン] アクティビティをクリックします。 デバイスがネイティブクライアント (モバイルアプリまたはデスクトップアプリ) か、デバイスが管理対象デバイス (準拠しているか、ドメインに参加しているか、有効なクライアント証明書) であるかを、**ユーザーエージェントタグ**が正しく反映していることを確認します。

> [!NOTE]
> 展開した後は、[アプリの条件付きアクセス制御] ページからアプリを削除することはできません。 アプリでセッションまたはアクセスポリシーを設定していない限り、アプリの条件付きアクセス制御によってアプリの動作が変更されることはありません。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [« PREVIOUS: アプリの条件付きアクセス制御の概要](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [次: 任意のアプリのアプリの条件付きアクセス制御をオンボードしてデプロイする»](proxy-deployment-any-app.md)

[!INCLUDE [Open support ticket](includes/support.md)]
