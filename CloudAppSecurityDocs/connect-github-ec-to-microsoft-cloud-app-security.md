---
title: GitHub Enterprise Cloud を Cloud App Security に接続する
description: この記事では、GitHub Enterprise Cloud アプリを Cloud App Security に接続する方法について説明します。 API コネクタを使用して、使用状況を表示したり制御したりすることができます。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 06/02/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 645e5b93b9fe9f27d3a2ca52258fa3fc904230ef
ms.sourcegitcommit: 5822fcdb1433a6a26195692b05aed160bc339656
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292246"
---
# <a name="connect-github-enterprise-cloud-to-microsoft-cloud-app-security"></a>GitHub Enterprise Cloud を Microsoft Cloud App Security に接続する

*適用対象:Microsoft Cloud App Security*

この記事では、アプリコネクタ Api を使用して Microsoft Cloud App Security を既存の GitHub エンタープライズクラウド組織に接続する手順について説明します。 この接続により、組織の GitHub エンタープライズクラウドの使用状況を可視化し、制御することができます。<!-- For more information about how Cloud App Security protects GitHub Enterprise Cloud, see **//TODO:: ???**.-->

## <a name="prerequisites"></a>必須コンポーネント

- 組織は、GitHub Enterprise Cloud ライセンスを持っている必要があります。
- Cloud App Security に接続するために使用する GitHub アカウントには、組織に対する*所有者*のアクセス許可が必要です。
- 組織の所有者を確認するには、組織のページに移動し、[ **People**] を選択して、*所有者*でフィルター処理します。

## <a name="how-to-connect-github-enterprise-cloud-to-cloud-app-security"></a>GitHub Enterprise Cloud を Cloud App Security に接続する方法

### <a name="verify-your-github-domains"></a>GitHub ドメインを確認する

ドメインの確認は任意です。 ただし、Cloud App Security が GitHub 組織のメンバーのドメインのメールを対応する Azure Active Directory ユーザーに照合できるように、ドメインを確認することを強くお勧めします。

これらの手順は、「 [GitHub エンタープライズクラウドの構成](#configure-github-enterprise-cloud)」の手順とは無関係に完了できます。また、既にドメインを検証している場合はスキップできます。

1. [会社のサービス条件](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/upgrading-to-the-corporate-terms-of-service)に組織をアップグレードします。
1. [組織のドメイン](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/verifying-your-organizations-domain)を確認します。

    > [!NOTE]
    > Cloud App Security ポータルに表示されている各管理対象ドメインを確認してください。 管理対象ドメインを表示するには、Cloud App Security で、[**設定**] [組織の詳細] [  >  **Organization details**  >  **管理対象ドメイン**] を参照します。

### <a name="configure-github-enterprise-cloud"></a>GitHub Enterprise Cloud の構成

1. **組織のログイン名を検索する**  
GitHub で組織のページを参照し、URL から組織のログイン名をメモしておきます。後で必要になります。

    > [!NOTE]
    > このページには、のような URL が表示され `https://github.com/<your-organization>` ます。 たとえば、組織のページがの場合、 `https://github.com/sample-organization` 組織のログイン名は " *sample-organization*" になります。

    ![組織のログイン名を取得していることを示すスクリーンショット](media/connect-github-org-login-name.png)

1. **組織内に OAuth アプリを作成します。**  
接続されている追加の組織ごとに、この手順を繰り返します。

    1. [**設定**] [  >  **開発者の設定**] を参照して [ **OAuth アプリ**] を選択し、[**アプリケーションの登録**] をクリックします。 または、既存の OAuth アプリがある場合は、[**新しい Oauth アプリ**] をクリックします。

        ![Oauth アプリの作成を示すスクリーンショット](media/connect-github-create-oauth-app.png)

    1. [**新しい OAuth アプリの登録**] の詳細を入力し、[**アプリケーションの登録**] をクリックします。
        - [**アプリケーション名**] ボックスに、アプリの名前を入力します。
        - [**ホームページの url** ] ボックスに、アプリのホームページの url を入力します。
        - [**承認コールバック URL** ] ボックスに、値として「」を入力し `https://portal.cloudappsecurity.com/api/oauth/connect` ます。

        ![Oauth アプリの登録を示すスクリーンショット](media/connect-github-register-oauth-app.png)

    > [!NOTE]
    >
    > - 既定では、OAuth アプリアクセスは組織に限定されています。 アクセスを有効にするには、[**設定**]  >  [**サードパーティのアクセス**] に移動し、[制限の**削除**] をクリックして、[**はい、アプリケーションの制限を削除**します] をクリックします。
    > - 組織が所有するアプリは、組織のアプリにアクセスできます。 詳細については、「 [OAuth アプリのアクセス制限につい](https://help.github.com/en/github/setting-up-and-managing-organizations-and-teams/about-oauth-app-access-restrictions)て」を参照してください。

1. [**設定**] [oauth アプリ] を参照して、作成した  >  **OAuth Apps**oauth アプリを選択し、その**クライアント ID**と**クライアントシークレット**をメモします。

    ![Oauth アプリの詳細を示すスクリーンショット](media/connect-github-oauth-app-details.png)

### <a name="configure-cloud-app-security"></a>Cloud App Security の設定

1. Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。

1. [**アプリコネクタ**] ページで、プラスボタンをクリックし、次に**GitHub**をクリックします。

1. ポップアップで、前にメモした**クライアント ID**、**クライアントシークレット**、および**組織のログイン名**を入力し、[ **GitHub で接続**] をクリックします。

    ![Connect github api を示すスクリーンショット](media/connect-github-connect-app.png)

    GitHub のサインインページが開きます。 必要に応じて、GitHub 管理者の資格情報を入力して、チームの GitHub Enterprise Cloud インスタンスへの Cloud App Security アクセスを許可します。

1. GitHub 組織にアクセスする Cloud App Security を付与するようにアプリを承認します。

    > [!NOTE]
    > Cloud App Security には、次の OAuth スコープが必要です。
    >
    > - **管理者:** 組織の監査ログを同期するために必要な組織
    > - **read: user**および**user: email** -組織のメンバーを同期するために必要です。
    > - リポジトリ **: 状態**-監査ログでリポジトリ関連のイベントを同期するために必要な oauth スコープの詳細については、「 [oauth アプリのスコープ](https://developer.github.com/apps/building-oauth-apps/understanding-scopes-for-oauth-apps/)について」を参照してください。

    ![Github oauth の承認を示すスクリーンショット](media/connect-github-authorize-app.png)

1. Cloud App Security コンソールに戻ると、GitHub が正常に接続されたことを示すメッセージが表示されます。

1. [**API のテスト**] をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、[**閉じる**] をクリックします。

GitHub Enterprise Cloud に接続すると、接続する7日間のイベントを受け取ります。

アプリの接続で問題が発生した場合は、「[アプリコネクタのトラブルシューティング](troubleshooting-api-connectors-using-error-messages.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
