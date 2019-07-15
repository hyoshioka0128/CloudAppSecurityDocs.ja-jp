---
title: すべてのアプリのクラウド アプリ セキュリティ Conditional Access App Control のデプロイします。
description: この記事では、すべてのアプリの Microsoft Cloud App Security Conditional Access App Control リバース プロキシ機能を展開する方法について説明します。
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 7/2/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.suite: ems
ms.openlocfilehash: 4fc756d2c077d97bef295b40cefd2336ecb25c16
ms.sourcegitcommit: 8fd13c10c2f66a553a8a8fc413555ca837fc9c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610712"
---
# <a name="onboard-and-deploy-conditional-access-app-control-for-any-app"></a>オンボードと任意のアプリの Conditional Access App Control をデプロイします。

*適用対象:Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« 戻る: 条件付きのアクセス アプリ制御の概要](proxy-intro-aad.md)<br>
[次へ: セッション ポリシーを作成する方法 »](session-policy-aad.md)

すべての web アプリを使用する、Microsoft Cloud App Security でセッション制御を構成できます。 この記事で説明方法をオンボードするカスタムの基幹業務アプリ、SaaS アプリの機能を備えた非およびセッション コントロールでの Azure AD アプリケーション プロキシ経由でホストされているオンプレミスのアプリと展開します。

ボックスの動作を Cloud App Security では機能を備えたアプリの一覧は、次を参照してください。 [Microsoft Cloud App Security Conditional Access App Control でアプリを保護する](proxy-intro-aad.md)します。

## <a name="prerequisites"></a>前提条件

- 組織 Conditional Access App Control を使用する次のライセンスが必要です。

  - Azure Active Directory Premium edition
  - クラウド アプリ セキュリティ

- アプリを Azure ad のシングル サインオンを構成する必要があります。
- アプリは、SAML または Open ID Connect 2.0 プロトコルを使用する必要があります。

## <a name="to-deploy-a-any-app"></a>すべてのアプリをデプロイするには

Cloud App Security Conditional Access App Control で制御するすべてのアプリを構成するこれらの手順に従います。

**ステップ 1: [関連するアプリを Cloud App Security にルーティングする Azure Active Directory の条件付きアクセス ポリシーの機能を構成する](#conf-azure-ad)します。**

**手順 2:[アプリを展開するユーザーを構成する](#conf-users)します。**

**手順 3:[展開するアプリを構成します。](#conf-app)**

**手順 4:[アプリのドメインを追加します。](#add-domains)**

**手順 5:[アプリが正しく動作していることを確認します。](#verify-app)**

**手順 6:[組織で使用するようにアプリケーションを有効にします。](#enable-app)**

**手順 7:[Azure AD のポリシーを更新します。](#update-azure-ad)**

> [!NOTE]
> Azure AD アプリに対してアプリの条件付きアクセス制御をデプロイするには、Cloud App Security ライセンスと共に有効な [Azure AD Premium P1 のライセンス](https://docs.microsoft.com/azure/active-directory/license-users-groups)が必要になります。

## 手順 1:関連するアプリを Cloud App Security にルーティングする Azure Active Directory の条件付きアクセス ポリシーの機能を構成します。<a name="conf-azure-ad"></a>  

1. Azure Active Directory で [**セキュリティ**、] をクリックして**条件付きアクセス**します。

1. **条件付きアクセス**ページの上部のツールバーで、をクリックして**新しいポリシー**します。

1. **新規** ページの 、**名前** ボックスに「**テスト**します。

1. **ユーザーとグループ** ページで、関連するテスト ユーザーのオンボードとなるアプリを割り当てます。

1. **クラウド アプリ** ページで、Conditional Access App Control で制御アプリを割り当てます。

1. **セッション**を選択します**Conditional Access App Control を使用して**選び**監視のみ**。

   ![Azure AD 条件付きアクセス](./media/azure-ad-caac-policy.png)

1. クリックして**を有効にする**と**保存**します。

## 手順 2:アプリを展開するユーザーを構成します。<a name="conf-users"></a>

1. Cloud App Security では、メニュー バーで設定の歯車アイコンをクリックして![設定アイコン](./media/settings-icon.png "設定アイコン")選択**設定**します。

1. **Conditional Access App Control**を選択します**オンボード/メンテナンス**します。

1. ユーザー プリンシパル名を入力します。 または、アプリをオンボードとなるユーザーの電子メールをクリック**保存**します。

    ![アプリのオンボードおよびメンテナンスの設定のスクリーン ショット。](media/app-onboarding-settings.png)

## 手順 3:展開するアプリを構成します。<a name="conf-app"></a>

1. 展開するアプリに移動します。 アプリ ドメインが認識されない場合は、アプリの構成処理を続行する促されます。 アプリ ドメインが認識されない場合は、アプリのドメインを構成する促されます。 クリックして**構成アプリ**に進んでください[アプリのドメインを追加](#add-domains)します。

    > [!NOTE]
    > 認識されているアプリのドメインで正常に動作するアプリに必要なすべてのドメインで、アプリが構成になっていることを確認します。 追加の構成に進みます[アプリのドメインを追加](#add-domains)します。

1. インストールするには、次の手順を繰り返して、**現在 CA**と**次の CA**自己署名ルート証明書。
    1. 証明書を選択します。
    1. をクリックして**オープン**、入力を求められたら、をクリックして**オープン**もう一度です。
    1. クリックして**証明書のインストール**します。
    1. いずれかを選択**現在のユーザー**または**ローカル マシン**します。
    1. 選択**次のストアに証明書をすべてを配置** をクリックし、**参照**します。
    1. 選択**信頼されたルート証明書機関**順にクリックします**OK**します。
    1. **[完了]** をクリックします。

    > [!NOTE]
    > 認識される証明書のブラウザーを再起動し、同じページに移動する必要があります、証明書をインストールしたら。 チェック マークがインストールされている証明書のリンクの確認メッセージが表示されます。

1. **[続行]** をクリックします。

## 手順 4:アプリのドメインを追加します。<a name="add-domains"></a>

アプリに正しいドメインを関連付けることにより、Cloud App Security ポリシーを適用し、アクティビティを監査します。

たとえば、関連付けられているドメインに対してファイルのダウンロードをブロックするポリシーを構成した場合はそのドメインからのアプリでファイルのダウンロードはブロックされます。 ただし、アプリに関連付けられていないドメインからのアプリでファイルのダウンロードがブロックされていないと、アクティビティ ログで、アクションは監査されません。
> [!NOTE]
> Cloud App Security では、シームレスなユーザー エクスペリエンスを実現するアプリに関連付けられていないドメインにサフィックスが追加されます。

1. Cloud App Security の管理者] ツールバーで、アプリ内から [クリックして**ドメイン検出**します。
    > [!NOTE]
    > 管理者ツールバーをオンボードする権限を持つユーザーやメンテナンスのアプリを表示するだけです。
1. 検出されたドメイン パネルで、ドメイン名をメモしておきます。 または一覧を .csv ファイルとしてエクスポートします。
    > [!NOTE]
    > パネルには、アプリでは、関連付けられていない探索されたドメインの一覧が表示されます。 ドメイン名は、完全修飾されます。
1. メニュー バーで、Cloud App Security に移動して、設定の歯車アイコンをクリックします![設定アイコン](./media/settings-icon.png "設定アイコン")選択と**条件付きアクセス アプリ制御**します。
1. 展開するアプリが表示されて、アプリの一覧で選択し、行での最後に 3 つのドット**アプリの詳細**、選択**編集**します。
    > [!TIP]
    > アプリで構成されているドメインの一覧を表示する をクリックして**アプリ ドメインを表示**します。
1. **ドメインのユーザー定義**、クリックして、このアプリに関連付けるすべてのドメインを入力**保存**します。
    > [!NOTE]
    > 使用することができます、* ワイルドカード文字の任意の文字のプレース ホルダーとして。 ドメインを追加する場合は、特定のドメインを追加するかどうかを決定 (`sub1.contoso.com`、`sub2.contoso.com`) または複数のドメイン (`*.contoso.com`)。

## 手順 5:アプリが正しく動作していることを確認します。<a name="verify-app"></a>

1. サインイン フローが正しく動作することを確認します。
    > [!NOTE]
    > 一部のアプリは、サインイン プロセスを中断する可能性があります認証時に nonce のハッシュを発行します。 この場合、問題を解決するトラブルシューティング ガイドを参照してください。
1. アプリでは後、は、次のチェックを実行します。
    1. ユーザーの作業プロセスの一部であり、ページが正しく表示することを確認する、アプリ内のすべてのページを参照してください。
    1. 動作と、アプリの機能が悪影響を受けていないダウンロード、およびファイルのアップロードなど一般的な操作を実行して確認します。
    1. アプリに関連付けられているドメインの一覧を確認します。 詳細については、次を参照してください。 [、app4 のドメインを追加](#add-domains)します。

## 手順 6:組織で使用するようにアプリケーションを有効にします。<a name="enable-app"></a>

組織の運用環境で使用するためのアプリを有効にする準備ができたら、次の手順を実行します。

1. Cloud App Security では、メニュー バーで設定の歯車アイコンをクリックして![設定アイコン](./media/settings-icon.png "設定アイコン")選択**Conditional Access App Control**します。
1. 展開するアプリが表示されて、アプリの一覧で 行の最後に 3 つのドットを選択し、**編集アプリ**します。
1. 選択**Conditional Access App Control で使用** をクリックし、**保存**します。

## 手順 7:Azure AD のポリシーを更新します。<a name="update-azure-ad"></a>

1. Azure Active Directory で [**セキュリティ**、] をクリックして**条件付きアクセス**します。
1. 作成したポリシーの更新[Azure Active Directory の条件付きアクセス ポリシーの機能を構成する](#conf-azure-ad)に関連するユーザー、グループ、および必要なコントロールが含まれます。
1. **セッション** > **Conditional Access App Control を使用して**選択した場合、**カスタム ポリシーを使用して**を Cloud App Security に移動し、対応するを作成します。セッション ポリシー。 詳しくは、「[セッション ポリシー](session-policy-aad.md)」をご覧ください。

>[!div class="step-by-step"]
[« 戻る: Conditional Access App Control をおすすめのアプリを展開します。](proxy-deployment-aad.md)<br>
[次へ: セッション ポリシーを作成する方法 »](session-policy-aad.md)

## <a name="next-steps"></a>次の手順 
[Cloud App Security Conditional Access App Control の操作](proxy-intro-aad.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)