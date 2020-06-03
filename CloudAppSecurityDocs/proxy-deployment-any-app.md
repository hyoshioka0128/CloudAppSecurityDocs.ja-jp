---
title: すべてのアプリに Cloud App Security アプリの条件付きアクセス制御をデプロイする
description: この記事では、すべてのアプリのリバースプロキシ機能アプリの条件付きアクセス制御 Microsoft Cloud App Security を展開する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: ddbcbbe72c83f926b8307904a9d5e2bb2731dcba
ms.sourcegitcommit: 5822fcdb1433a6a26195692b05aed160bc339656
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84275797"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>アプリのアプリの条件付きアクセス制御をオンボードしてデプロイする

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security のセッション制御は、任意の web アプリで動作するように構成できます。 この記事では、カスタムの基幹業務アプリ、非機能の SaaS アプリ、および Azure Active Directory (Azure AD) アプリケーションプロキシを使用してホストされているオンプレミスのアプリをセッションコントロールでオンボードする方法について説明します。

Cloud App Security で利用できるアプリの一覧については、「 [Cloud App Security アプリの条件付きアクセス制御を使用](proxy-intro-aad.md#featured-apps)したアプリの保護」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

- アプリの条件付きアクセス制御を使用するには、組織が次のライセンスを持っている必要があります。

  - [Azure Active Directory (Azure AD) Premium P1](https://docs.microsoft.com/azure/active-directory/license-users-groups)以上、または id プロバイダー (IdP) ソリューションに必要なライセンス
  - Microsoft Cloud App Security

- アプリはシングルサインオンで構成する必要があります
- アプリでは、次のいずれかの認証プロトコルを使用する必要があります。

    |IdP|プロトコル|
    |---|---|
    |Azure AD|SAML 2.0 または OpenID Connect|
    |その他|SAML 2.0|

## <a name="to-deploy-any-app"></a>アプリを展開するには

次の手順に従って、Cloud App Security アプリの条件付きアクセス制御によって制御されるようにアプリを構成します。

**手順 1: [Cloud App Security を使用するように IdP を構成する](#conf-idp)**

**手順 2:[アプリを展開するユーザーを構成する](#conf-users)**

**手順 3:[展開するアプリを構成](#conf-app)する**

**手順 4:[アプリが正常に動作していることを確認する](#verify-app)**

**手順 5:[組織で使用するアプリを有効にする](#enable-app)**

**手順 6: [Azure AD ポリシーを更新する](#update-azure-ad)**

> [!NOTE]
> Azure AD アプリのアプリの条件付きアクセス制御をデプロイするには、 [Azure Active Directory Premium P1 以上の](https://docs.microsoft.com/azure/active-directory/license-users-groups)有効なライセンスと Cloud App Security ライセンスが必要です。

## <a name="step-1--configure-your-idp-to-work-with-cloud-app-security"></a>手順 1: Cloud App Security を使用するように IdP を構成する<a name="conf-idp"></a><a name="conf-azure-ad"></a>

### <a name="configure-integration-with-azure-ad"></a>Azure AD との統合の構成

アプリセッションを Cloud App Security にルーティングする条件付きアクセスポリシーを Azure AD 作成するには、次の手順に従います。 その他の IdP ソリューションについては、「[他の IdP ソリューションとの統合の構成](#configure-integration-with-other-idp-solutions)」を参照してください。

1. Azure AD で、[**セキュリティ**  >  **条件付きアクセス**] を参照します。

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

1. Cloud App Security で、[参照**Investigate**] を参照し  >  **て、接続されているアプリ**  >  **アプリの条件付きアクセス制御アプリ**を調査します。

1. プラス記号をクリックし、ポップアップで展開するアプリを選択し、[**ウィザードの開始**] をクリックします。
1. [**アプリ情報**] ページで、アプリの [シングルサインオンの構成] ページの情報を使用してフォームに入力し、[**次へ**] をクリックします。
    - IdP で、選択したアプリのシングルサインオンメタデータファイルが提供されている場合は、**アプリから [メタデータファイルのアップロード**] を選択し、メタデータファイルをアップロードします。
    - または、[**データを手動で入力**する] を選択し、次の情報を指定します。
        - **Assertion consumer service URL**
        - アプリで SAML 証明書が提供されている場合は、[ **<使用して saml 証明書を> app_name** ] を選択し、証明書ファイルをアップロードします。

    ![アプリ情報ページを示すスクリーンショット](media/proxy-deploy-add-idp-app-info.png)

1. [ **ID プロバイダー** ] ページで、提供されている手順を使用して IdP のポータルに新しいアプリケーションを設定し、[**次へ**] をクリックします。
    1. IdP のポータルにアクセスし、新しいカスタム SAML アプリを作成します。
    1. 既存のアプリのシングルサインオン構成 `<app_name>` を新しいカスタムアプリにコピーします。
    1. 新しいカスタムアプリにユーザーを割り当てます。
    1. アプリのシングルサインオンの構成情報をコピーします。次の手順で必要になります。

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
        >
        > - プロバイダーによっては、*ユーザー属性*または*要求*として参照される場合があります。
        > - 新しい SAML アプリを作成する場合、Okta Id プロバイダーは属性を1024文字に制限します。 この制限を緩和するには、まず、関連する属性を指定せずにアプリを作成します。 アプリを作成したら、それを編集して、関連する属性を追加します。
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

## <a name="step-2-configure-the-users-that-will-deploy-the-app"></a>手順 2: アプリを展開するユーザーを構成する<a name="conf-users"></a>

1. Cloud App Security のメニューバーで、[設定] 歯車![設定アイコン](media/settings-icon.png "設定アイコン")をクリックし、[**設定**] を選択します。

1. [**アプリの条件付きアクセス制御**で、[**アプリのオンボード/メンテナンス**] を選択します。

1. アプリをオンボードするユーザーのユーザープリンシパル名または電子メールアドレスを入力し、[**保存**] をクリックします。

    ![アプリのオンボードとメンテナンスの設定のスクリーンショット。](media/app-onboarding-settings.png)

## <a name="step-3-configure-the-app-that-you-are-deploying"></a>手順 3: 展開するアプリを構成する<a name="conf-app"></a>

デプロイするアプリにアクセスします。 表示されるページは、アプリが認識されているかどうかによって異なります。 次のいずれかの操作を行います。

| アプリの状態 | 説明 | 手順 |
| --- | --- | --- |
| 認識できません | アプリを構成するよう求める画面が表示されません。 | 1.[アプリの条件付きアクセス制御にアプリを追加](#add-app)します。<br /> 2.[アプリのドメインを追加](#add-domains)し、アプリに戻り、ページを最新の状態に更新します。<br /> 3.[アプリの証明書をインストール](#install-certs)します。 |
| Recognized | アプリの構成プロセスを続行するように求めるオンボードページが表示されます。 | - [アプリの証明書をインストール](#install-certs)します。 <br /><br /> **注:** アプリが正常に機能するために必要なすべてのドメインを使用してアプリが構成されていることを確認します。 追加のドメインを構成するには、「[アプリのドメインを追加](#add-domains)する」に進み、アプリのページに戻ります。 |

### <a name="to-add-a-new-app"></a>新しいアプリを追加するには<a name="add-app"></a>

1. メニューバーで、[設定] 歯車![設定アイコン](media/settings-icon.png "設定アイコン")をクリックし、[**アプリの条件付きアクセス制御**] を選択します。

1. **[View new apps]** \(新しいアプリの表示\) をクリックします。

    ![アプリの条件付きアクセス制御に表示された新しいアプリ](media/caac-view-apps.png)

1. 開いた画面に、新しいアプリの一覧が表示されます。 オンボードするアプリごとに、[署名] をクリックし、[ **+** **追加**] をクリックします。

    > [!NOTE]
    > アプリが Cloud App Security アプリ カタログに表示されない場合は、ダイアログの定義されていないアプリの下にログイン URL と共に表示されます。 これらのアプリの + 記号をクリックすると、カスタム アプリとしてアプリケーションをオンボードできます。

    ![アプリの条件付きアクセス制御で検出された Azure AD アプリ](media/caac-discovered-aad-apps.png)

### <a name="to-add-domains-for-an-app"></a>アプリのドメインを追加するには<a name="add-domains"></a>

適切なドメインをアプリに関連付けることにより、Cloud App Security はポリシーと監査アクティビティを適用できます。

たとえば、関連付けられているドメインのファイルのダウンロードをブロックするポリシーを構成した場合、そのドメインからのアプリによるファイルのダウンロードはブロックされます。 ただし、アプリに関連付けられていないドメインからのファイルのダウンロードはブロックされず、操作はアクティビティログで監査されません。
> [!NOTE]
> Cloud App Security は、シームレスなユーザーエクスペリエンスを確保するために、アプリに関連付けられていないドメインにサフィックスを追加します。

1. アプリ内の Cloud App Security 管理ツールバーで、[検出された**ドメイン**] をクリックします。
    > [!NOTE]
    > 管理ツールバーは、アプリをオンボードまたはメンテナンスするアクセス許可を持つユーザーにのみ表示されます。
1. [検出されたドメイン] パネルで、ドメイン名を書き留めます。または、一覧を .csv ファイルとしてエクスポートします。
    > [!NOTE]
    > パネルには、アプリに関連付けられていない、検出されたドメインの一覧が表示されます。 ドメイン名は完全修飾されています。
1. Cloud App Security にアクセスし、メニューバーの [設定] 歯車![設定アイコン](media/settings-icon.png "設定アイコン")をクリックして、[**アプリの条件付きアクセス制御**] を選択します。
1. アプリの一覧で、デプロイするアプリが表示されている行に、行の末尾にある3つの点を選択し、[**アプリの詳細**] で [**編集**] を選択します。
    > [!TIP]
    > アプリで構成されているドメインの一覧を表示するには、[**アプリドメインの表示**] をクリックします。
1. [**ユーザー定義ドメイン**] で、このアプリに関連付けるすべてのドメインを入力し、[**保存**] をクリックします。
    > [!NOTE]
    > * ワイルドカード文字は、任意の文字のプレースホルダーとして使用できます。 ドメインを追加するときに、特定のドメイン ( `sub1.contoso.com` 、 `sub2.contoso.com` ) または複数のドメイン () のどちらを追加するかを決定し `*.contoso.com` ます。

### <a name="to-install-root-certificates"></a>ルート証明書をインストールするには<a name="install-certs"></a>

1. 次の手順を繰り返して、**現在の ca**と**次の ca**の自己署名ルート証明書をインストールします。
    1. 証明書を選択します。
    1. [**開く**] をクリックし、メッセージが表示されたらもう一度 [**開く**] をクリックします。
    1. [**証明書のインストール**] をクリックします。
    1. [**現在のユーザー** ] または [**ローカルコンピューター**] を選択します。
    1. [**証明書をすべて次のストアに配置する**] を選択し、[**参照**] をクリックします。
    1. [**信頼されたルート証明機関**] を選択し、[ **OK**] をクリックします。
    1. **[完了]** をクリックします。

    > [!NOTE]
    > 証明書が認識されるようにするには、証明書をインストールしたら、ブラウザーを再起動して同じページにアクセスする必要があります。<!-- You'll see a check-mark by the certificates links confirmation they are installed.-->

1. **[Continue]** をクリックします。

## <a name="step-4-verify-that-the-app-is-working-correctly"></a>手順 4: アプリが正常に動作していることを確認する<a name="verify-app"></a>

1. サインインフローが正しく機能することを確認します。
    <!--
    > [!NOTE]
    > Some apps issue a nonce hash during authentication that may break the sign-in process. If this happens, see the Troubleshooting Guide to resolve the issue.-->
1. アプリを作成したら、次のチェックを実行します。
    1. ユーザーの作業プロセスの一部であるアプリ内のすべてのページにアクセスし、ページが正しく表示されることを確認します。
    1. ファイルのダウンロードやアップロードなどの一般的な操作を実行することで、アプリの動作と機能が悪影響を受けないことを確認します。
    1. アプリに関連付けられているドメインの一覧を確認します。 詳細については、「[アプリのドメインを追加](#add-domains)する」を参照してください。

## <a name="step-5-enable-the-app-for-use-in-your-organization"></a>手順 5: 組織で使用するアプリを有効にする<a name="enable-app"></a>

組織の運用環境でアプリを使用できるようにする準備ができたら、次の手順を実行します。

1. Cloud App Security で、[設定] 歯車![設定アイコン](media/settings-icon.png "設定アイコン")をクリックし、[**アプリの条件付きアクセス制御**] を選択します。
1. アプリの一覧で、展開するアプリが表示されている行で、行の末尾にある3つの点を選択し、[**アプリの編集**] を選択します。
1. [**アプリの条件付きアクセス制御で使用する**] を選択し、[**保存**] をクリックします。

## <a name="step-6-update-the-azure-ad-policy-azure-ad-only"></a>手順 6: Azure AD ポリシーを更新する (Azure AD のみ)<a name="update-azure-ad"></a>

1. Azure AD の [**セキュリティ**] で、[**条件付きアクセス**] をクリックします。
1. 前の手順で作成したポリシーを更新して、必要なユーザー、グループ、およびコントロールを追加します。
1. [**セッション**の  >  **使用アプリの条件付きアクセス制御**] で、[**カスタムポリシーを使用**する] を選択した場合は Cloud App Security にアクセスし、対応するセッションポリシーを作成します。 詳しくは、「[セッション ポリシー](session-policy-aad.md)」をご覧ください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [« PREVIOUS: おすすめアプリ用にアプリの条件付きアクセス制御をデプロイする](proxy-deployment-aad.md)

> [!div class="nextstepaction"]
> [次の手順: セッションポリシーを作成する方法»](session-policy-aad.md)

## <a name="see-also"></a>関連項目

> [!div class="nextstepaction"]
> [アプリの条件付きアクセス制御の概要](proxy-intro-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
