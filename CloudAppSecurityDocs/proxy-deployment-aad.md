---
title: Azure AD アプリの Cloud App Security Conditional Access App Control をデプロイする
description: この記事では、Azure AD アプリの Microsoft Cloud App Security のアプリの条件付きアクセス制御リバース プロキシ機能をデプロイする方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: b2cc376ee93d4f052227cbc3a0e8e8f04e564ae3
ms.sourcegitcommit: ecb1835d1cd880de38f32ce7a7031b0015f3cae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81241364"
---
# <a name="deploy-conditional-access-app-control-for-featured-apps"></a>フィーチャー アプリでの条件付きアクセス アプリ制御の展開

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security のセッションコントロールは、おすすめアプリで動作します。 Cloud App Security で利用できるアプリの一覧については、「 [Cloud App Security アプリの条件付きアクセス制御を使用](proxy-intro-aad.md#featured-apps)したアプリの保護」を参照してください。

## <a name="prerequisites"></a>前提条件

- アプリの条件付きアクセス制御を使用するには、組織が次のライセンスを持っている必要があります。

  - [Azure Active Directory (Azure AD) Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups)以上、または id プロバイダー (IdP) ソリューションに必要なライセンス
  - Microsoft Cloud App Security

- アプリはシングルサインオンで構成する必要があります
- アプリでは、次のいずれかの認証プロトコルを使用する必要があります。

    |IdP|プロトコル|
    |---|---|
    |Azure AD|SAML 2.0 または OpenID Connect|
    |その他|SAML 2.0|

## <a name="to-deploy-featured-apps"></a>おすすめアプリを展開するには

次の手順に従って、Microsoft Cloud App Security アプリの条件付きアクセス制御によって制御されるおすすめアプリを構成します。

**手順 1: [Cloud App Security を使用するように IdP を構成する](#conf-idp)**

**手順 2:[ポリシーの対象となるユーザーを使用して各アプリにサインインする](#sign-in-scoped)**

**手順 3:[アクセスとセッション制御を使用するようにアプリが構成されていることを確認する](#portal)**

**手順 4:[デプロイをテストする](#test)**

## <a name="step-1--configure-your-idp-to-work-with-cloud-app-security"></a>手順 1: Cloud App Security を使用するように IdP を構成する<a name="conf-idp"></a><a name="add-azure-ad"></a>

### <a name="configure-integration-with-azure-ad"></a>Azure AD との統合の構成

アプリセッションを Cloud App Security にルーティングする条件付きアクセスポリシーを Azure AD 作成するには、次の手順に従います。 その他の IdP ソリューションについては、「[他の IdP ソリューションとの統合の構成](#configure-integration-with-other-idp-solutions)」を参照してください。

1. Azure AD で、[**セキュリティ** > **条件付きアクセス**] を参照します。

1. [**条件付きアクセス**] ウィンドウの上部にあるツールバーで、[**新しいポリシー**] をクリックします。

1. **新しい**ウィンドウの [**名前**] ボックスに、ポリシー名を入力します。

1. [**割り当て**] で [**ユーザーとグループ**] をクリックし、アプリのオンボード (初期サインオンと検証) するユーザーを割り当てて、[**完了**] をクリックします。

1. [**割り当て**] で [**クラウドアプリ**] をクリックし、アプリの条件付きアクセス制御によって制御するアプリを割り当てて、[**完了**] をクリックします。

1. [**アクセス制御**] の [**セッション**] をクリックし、[**アプリの条件付きアクセス制御の使用**] を選択して組み込みのポリシーを選択します (**モニターのみ**または**ダウンロードをブロック**します)。または、**カスタムポリシーを使用**して Cloud App Security で詳細ポリシーを設定し、[**選択**] をクリックします。

    ![Azure AD の条件付きアクセス](media/azure-ad-caac-policy.png)

1. 必要に応じて、条件を追加し、必要に応じてコントロールを許可します。

1. [**ポリシーを有効**にする] を **[オン**] に設定し、[**作成**] をクリックします。

### <a name="configure-integration-with-other-idp-solutions"></a>他の IdP ソリューションとの統合の構成

他の IdP ソリューションから Cloud App Security にアプリセッションをルーティングするには、次の手順に従います。 Azure AD については、「 [Azure AD との統合の構成](#configure-integration-with-azure-ad)」を参照してください。

1. Cloud App Security で、[参照] を参照し**て、接続されているアプリ** > **アプリの条件付きアクセス制御アプリ**を**調査** > します。

1. プラス記号をクリックし、ポップアップで展開するアプリを選択し、[**ウィザードの開始**] をクリックします。
1. [**アプリ情報**] ページで、アプリの [シングルサインオンの構成] ページの情報を使用してフォームに入力し、[**次へ**] をクリックします。
    - IdP で、選択したアプリのシングルサインオンメタデータファイルが提供されている場合は、**アプリから [メタデータファイルのアップロード**] を選択し、メタデータファイルをアップロードします。
    - または、[**データを手動で入力**する] を選択し、次の情報を指定します。
        - **Assertion consumer service URL**
        - アプリで SAML 証明書が提供されている場合は、[ **<使用して saml 証明書を> app_name** ] を選択し、証明書ファイルをアップロードします。

    ![アプリ情報ページを示すスクリーンショット](media/proxy-deploy-add-idp-app-info.png)

1. [ **ID プロバイダー** ] ページで、提供されている手順を使用して IdP のポータルに新しいアプリケーションを設定し、[**次へ**] をクリックします。
    1. IdP のポータルにアクセスし、新しいカスタム SAML アプリを作成します。
    1. 既存`<app_name>`のアプリのシングルサインオン構成を新しいカスタムアプリにコピーします。
    1. 新しいカスタムアプリにユーザーを割り当てます。
    1. アプリのシングルサインオン構成をコピーします。次の手順で必要になります。

    ![[Id プロバイダー情報の収集] ページを示すスクリーンショット](media/proxy-deploy-add-idp-get-conf.png)

    > [!NOTE]
    > これらの手順は、id プロバイダーによって多少異なる場合があります。 この手順は、次の理由で推奨されます。
    >
    > - 一部の id プロバイダーでは、ギャラリーアプリの SAML 属性または URL プロパティを変更することはできません
    > - カスタムアプリを構成すると、組織の既存の動作を変更することなく、アクセスおよびセッション制御を使用してこのアプリケーションをテストできます。

1. 次のページで、アプリのシングルサインオン構成ページの情報を使用してフォームに入力し、[**次へ**] をクリックします。
    - IdP で、選択したアプリのシングルサインオンメタデータファイルが提供されている場合は、**アプリから [メタデータファイルのアップロード**] を選択し、メタデータファイルをアップロードします。
    - または、[**データを手動で入力**する] を選択し、次の情報を指定します。
        - **Assertion consumer service URL**
        - アプリで SAML 証明書が提供されている場合は、[ **<使用して saml 証明書を> app_name** ] を選択し、証明書ファイルをアップロードします。

    ![[Id プロバイダー情報の入力] ページを示すスクリーンショット](media/proxy-deploy-add-idp-enter-conf.png)

1. 次のページで、次の情報をコピーして、[**次へ**] をクリックします。 次の手順で情報が必要になります。

    - シングルサインオン URL
    - 属性と値

    ![[Id プロバイダーの収集 SAML 情報] ページのスクリーンショット](media/proxy-deploy-add-idp-ext-conf.png)

1. IdP のポータルで、次の操作を行います。
    > [!NOTE]
    > この設定は、IdP portal の [カスタムアプリ設定] ページでよく見られます。

    1. [シングルサインオン URL] フィールドに、前の手順でメモしたシングルサインオン URL を入力します。
        > [!NOTE]
        > 一部のプロバイダーでは、*応答 url*としてシングルサインオン url を参照できます。
    1. 前にメモしておいた属性と値をアプリのプロパティに追加します。
        > [!NOTE]
        > プロバイダーによっては、*ユーザー属性*または*要求*として参照される場合があります。
    1. 名前識別子が電子メールアドレスの形式であることを確認します。
    1. 設定を保存します。
1. [**アプリの変更**] ページで、次の操作を行ってから、[**次へ**] をクリックします。 次の手順で情報が必要になります。

    - シングルサインオン URL をコピーする
    - Cloud App Security SAML 証明書をダウンロードする

    ![[Cloud App Security SAML 情報の収集] ページを示すスクリーンショット](media/proxy-deploy-add-idp-app-changes.png)

1. アプリのポータルの [single sign-on settings (シングルサインオンの設定)] で、次の操作を行います。
    1. しない現在の設定のバックアップを作成します。
    1. [シングルサインオン URL] フィールドに、前の手順でメモしたシングルサインオン URL を入力します。
    1. 先ほどメモした Cloud App Security SAML 証明書をアップロードします。
    > [!NOTE]
    > 設定を保存すると、このアプリに関連付けられているすべてのログイン要求がアプリの条件付きアクセス制御経由でルーティングされます。

## <a name="step-2-sign-in-to-each-app-using-a-user-scoped-to-the-policy"></a>手順 2: ポリシーの対象となるユーザーを使用して各アプリにサインインする<a name="sign-in-scoped"></a>

> [!NOTE]
> 続行する前に、まず既存のセッションからサインアウトしてください。

ポリシーを作成したら、そのポリシーで構成されている各アプリにサインインします。 必ずポリシーで構成されているユーザーでサインインしてください。

Cloud App Security によって、サインインする新しい各アプリのポリシーの詳細がサーバーに同期されます。 これには最大 で1 分かかることがあります。

## <a name="step-3-verify-the-apps-are-configured-to-use-access-and-session-controls"></a>手順 3: アクセスとセッション制御を使用するようにアプリが構成されていることを確認する<a name="portal"></a>

上記の手順を利用して、おすすめアプリ用の組み込みの Cloud App Security ポリシーを Azure AD 内に直接作成できました。 この手順では、これらのアプリに対してアクセス制御とセッション制御が構成されていることを確認します。

1. Cloud App Security ポータルで、[設定] 歯車![設定アイコン](media/settings-icon.png "設定アイコン")をクリックし、[**アプリの条件付きアクセス制御**] を選択します。

1. [アプリの条件付きアクセス制御 apps] テーブルで、[**使用可能なコントロール**] 列を確認し、アプリに対して**アクセス制御**または**Azure AD 条件付きアクセス**と**セッション制御**の両方が表示されていることを確認します。

    > [!NOTE]
    > アプリのセッション制御が表示されない場合は、その特定のアプリではまだ使用できません。 [カスタムアプリ](proxy-deployment-any-app.md)としてすぐに追加することも、要求を開いて [**セッション制御の要求**] をクリックすることでおすすめアプリとして追加することもできます。
    >
    >![アプリの条件付きアクセス制御の要求](media/caac-request.png)

## <a name="step-4-test-the-deployment"></a>手順 4: デプロイをテストする<a name="test"></a>

1. まず、既存のセッションからサインアウトします。 次に、正常にデプロイされた各アプリにサインインします。 Azure AD で構成されたポリシーに一致するユーザー、または id プロバイダーで構成された SAML アプリにサインインします。

1. Cloud App Security ポータルの **[調査]** で、**[アクティビティ ログ]** を選択し、アプリごとにログイン アクティビティがキャプチャされていることを確認します。

1. フィルター処理は、**[詳細]** をクリックし、**[Source equals Access control]** \(ソースがアクセス制御と等しい\) を使用してフィルター処理することで実行できます。

    ![Azure AD の条件付きアクセスを使用するフィルター処理](media/sso-logon.png)

1. マネージド デバイスとアンマネージド デバイスからモバイルおよびデスクトップのアプリにサインインすることをお勧めします。 これは、アクティビティ ログで、アクティビティを正常にキャプチャするためです。  
アクティビティが正しくキャプチャされていることを確認するには、シングルサインオンのログインアクティビティをクリックして、アクティビティドロワーを開きます。 **[ユーザー エージェント タグ]** に、デバイスがネイティブ クライアント (モバイルまたはデスクトップ アプリのいずれかであることを意味する) であるか、またはデバイスがマネージド デバイス (準拠、ドメイン参加済み、または有効なクライアント証明書) であるかが適切に反映されていることを確認します。

> [!NOTE]
> デプロイ後は、[アプリの条件付きアクセス制御] ページからアプリを削除することはできません。 アプリにセッションやアクセス ポリシーを設定しないかぎり、アプリの条件付きアクセス制御でアプリの動作が変更されることは一切ありません。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [« PREVIOUS: アプリの条件付きアクセス制御の概要](proxy-intro-aad.md)

> [!div class="nextstepaction"]
> [次: 任意のアプリのアプリの条件付きアクセス制御をオンボードしてデプロイする»](proxy-deployment-any-app.md)

[!INCLUDE [Open support ticket](includes/support.md)]
