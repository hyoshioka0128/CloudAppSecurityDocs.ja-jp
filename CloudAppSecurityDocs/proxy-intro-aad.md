---
title: Microsoft Cloud App Security のアプリの条件付きアクセス制御で保護する
description: この記事では、Cloud App Security アプリの条件付きアクセス制御のリバース プロキシのしくみに関する情報を提供します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d4b800afa927b8a9151837cfbff76478c98bf71f
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460540"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Microsoft Cloud App Security Conditional Access App Control でアプリを保護する

*適用対象: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[次へ: Conditional Access App Control の展開 »](proxy-deployment-aad.md)

現代の職場では、多くの場合、犯行後にご利用のクラウド環境の状態を把握できるだけでは十分ではありません。 従業員が意図的に、あるいは不注意からデータや組織を危険にさらす前に、違反や漏洩をリアルタイムで防止することが望まれます。 組織内のユーザーが、クラウド アプリのほとんどのサービスとツールを利用できるようにし、個人所有デバイスで作業できるようにすることが重要です。 同時に、データ リークとデータ盗難から組織をリアルタイムで保護するのに役立つツールが必要です。 Azure Active Directory と共に、Microsoft Cloud App Security は Conditional Access App Control を使用する包括的な統合エクスペリエンスでこれらの機能を提供します。

> [!NOTE]
> To use Cloud App Security Conditional Access App Control, you need an [Azure Active Directory P1 license](https://azure.microsoft.com/pricing/details/active-directory/), and an active Microsoft Cloud App Security subscription or Office 365 E5 license. For a list of featured apps included with Office 365 E5, see [Office 365 featured apps](#O365-apps).

Office 365 E5 license. For a list of apps included with supported Office 365 E5, see Office 365 featured apps

## <a name="how-it-works"></a>しくみ

アプリの条件付きアクセス制御はリバース プロキシ アーキテクチャを利用し、Azure AD の条件付きアクセスと独自の方法で統合されます。 Azure AD の条件付きアクセスを使うと、特定の条件に基づくアクセス制御を組織のアプリに適用できます。 条件では、条件付きアクセス ポリシーの適用対象である "*人*" (ユーザーやユーザー グループ)、"*物*" (どのクラウド アプリか)、"*場所*" (どの場所とネットワークか) が定義されます。 条件が決まったら、ユーザーを Microsoft Cloud App Security にルーティングできます。ここで、アクセスおよびセッション制御を適用し、アプリの条件付きアクセス制御でデータを保護できます。

Conditional Access App Control では、アクセスおよびセッション ポリシーに基づいて、ユーザー アプリのアクセスとセッションをリアルタイムで監視して制御できます。 Cloud App Security ポータル内では、フィルターをさらに調整し、ユーザーに対して実行されるアクションを設定するために、アクセス ポリシーとセッション ポリシーが利用されます。 アクセス ポリシーとセッション ポリシーでは次のことができます。

- **Prevent data exfiltration**: You can block the download, cut, copy, and print of sensitive documents on, for example, unmanaged devices.

- **Protect on download**: Instead of blocking the download of sensitive documents, you can require documents to be labeled and protected with Azure Information Protection. This action ensures the document is protected and user access is restricted in a potentially risky session.

- **Prevent upload of unlabeled files**: Before a sensitive file is uploaded, distributed, and used by others, it’s important to make sure that the file has the right label and protection. You can ensure that unlabeled files with sensitive content are blocked from being uploaded until the user classifies the content.

- **Monitor user sessions for compliance**: Risky users are monitored when they sign into apps and their actions are logged from within the session. ユーザーの行動を調査して分析し、将来的に、どこで、どのような状況において、セッション ポリシーを適用する必要があるかを理解できます。

- **Block access**: You can granularly block access for specific apps and users depending on several risk factors. For example, you can block them if they are using client certificates as a form of device management.

- **Block custom activities**: Some applications have unique scenarios that carry risk, for example, sending messages with sensitive content in applications like Microsoft Teams or Slack. In these kinds of scenarios, you can scan messages for sensitive content and block them in real time.

### <a name="how-session-control-works"></a>セッション制御のしくみ

Conditional Access App Control でセッション ポリシーを作成することで、直接アプリにではなく、リバース プロキシ経由でユーザーをリダイレクトして、ユーザー セッションを制御できます。 From then on, user requests and responses go through Cloud App Security rather than directly to the app.

When a session is protected by proxy, all the relevant URLs and cookies are replaced by Cloud App Security. たとえば、ドメインが myapp.com で終わるリンクを含むページをアプリが返した場合、そのリンクは myapp.com.us.cas.ms などで終わるドメインに置き換えられます。

This method doesn't require you to install anything on the device making it ideal when monitoring or controlling sessions from unmanaged devices or partner users.

> [!NOTE]
> Cloud App Security では、世界中の Azure データ センターが活用され、位置情報によって最適化されたパフォーマンスが提供されます。 つまり、トラフィック パターンとその場所によっては、ユーザーのセッションが特定のリージョンの外部でホストされる可能性があります。 ただし、お客様のプライバシーを保護するために、これらのデータ センターにセッション データが保存されることはありません。

## <a name="managed-device-identification"></a>マネージド デバイスの識別

Conditional Access App Control を使うと、デバイスが管理されているかどうかを考慮するポリシーを作成できます。 デバイスが管理されているかどうかを識別するため、この機能では以下を利用します。

- 準拠しているデバイス
- ドメインに参加しているデバイス
- クライアント証明書のデプロイ

To configure a policy to leverage device management via client certificates:

1. 設定の歯車アイコンに移動して、 **[デバイスの識別]** を選択します。
1. 1 つ以上のルート証明書または中間証明書をアップロードします。
1. After the certificate is uploaded, you can create [access policies](access-policy-aad.md) and [session policies](session-policy-aad.md) based on **Device tag** and **Valid client certificate**.

    ![アプリの条件付きアクセス制御のデバイス ID](./media/caac-device-id.png)

> [!NOTE]
> 証明書がユーザーから要求されるのは、セッションが有効なクライアント証明書フィルターを使用するポリシーと一致する場合だけです。

### <a name="compliant-and-domain-joined-devices"></a>準拠していてドメインに参加済みのデバイス

Azure AD の条件付きアクセスでは、準拠しているデバイスとドメインに参加しているデバイスの情報を、Microsoft Cloud App Security に直接渡すことができます。 その情報から、デバイスの状態をフィルターとして使うアクセス ポリシーまたはセッション ポリシーを開発できます。 詳しくは、「[Azure Active Directory のデバイス管理の概要](https://docs.microsoft.com/azure/active-directory/device-management-introduction)」をご覧ください。

> [!NOTE]
> Some browsers may require additional configuration such as installing an extension. For more information, see [Conditional Access browser support](https://go.microsoft.com/fwlink/?linkid=2102732).

### <a name="client-certificate-authenticated-devices"></a>クライアント証明書で認証されたデバイス

デバイス識別メカニズムでは、クライアント証明書を使って関連するデバイスに認証を要求することができます。 組織で既に展開されている既存のクライアント証明書を使用するか、新しいクライアント証明書をマネージド デバイスにロールアウトできます。 それらの証明書の存在を利用し、アクセスやセッションのポリシーを設定します。

SSL client certificates are verified via a trust chain. You can upload an X.509 root or intermediate certificate authority (CA) formatted in the PEM certificate format. These certificates must contain the public key of the CA, which is then used to sign the client certificates presented during a session.

Once the certificate is uploaded and a relevant policy is configured, when an applicable session traverses Conditional Access App Control, the Cloud App Security endpoint requests the browser to present the SSL client certificates. The browser serves the SSL client certificates that are installed with a private key. This combination of certificate and private key is done by using the PKCS #12 file format, typically .p12 or .pfx.

When a client certificate check is performed, Cloud App Security checks for the following conditions:

1. The selected client certificate is valid and is under the correct root or intermediate CA.
1. The certificate is not revoked (if CRL is enabled).

> [!NOTE]
> Most major browsers support performing a client certificate check. However, mobile and desktop apps often leverage built-in browsers that may not support this check and therefore affect authentication for these apps.

クライアント証明書をデプロイする方法については、「[Azure AD アプリでの条件付きアクセス アプリ制御の展開](proxy-deployment-aad.md)」を参照してください。

## <a name="supported-apps-and-clients"></a>サポートされているアプリとクライアント

Conditional Access App Control currently supports SAML and Open ID Connect apps configured with single sign-on, along with web apps hosted on-premises configured with the [Azure AD App Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
> [!NOTE]
> アプリの条件付きアクセス制御では、Azure AD 以外の ID プロバイダーで構成されたアプリもサポートされます。 このシナリオの詳細については、mcaspreview@microsoft.com に電子メールをお送りください。

**セッション制御は、あらゆるオペレーティング システム上の、すべての主要なプラットフォーム上のすべてのブラウザーで使用可能です**。 We recommend using Internet Explorer 11, Microsoft Edge (latest), Google Chrome (latest), Mozilla Firefox (latest), or Apple Safari (latest). Access to mobile and desktop apps can also be blocked or allowed.

> [!NOTE]
> Using the **Client app** filter in access policies can cause the resulting user session to be proxied by Cloud App Security.
>
> In access policies, when using the **Client app** filter it defaults to **Mobile and desktop**. This can cause the resulting user session to be proxied by Cloud App Security. To void this behavior, set the value to **Browser**.
>
> By default, evaluating whether an app is mobile or desktop can cause the resulting user session to be proxied by Cloud App Security. To avoid this behavior, set the Client App filter in your Access policies to be equal to **Browser**.

> [!NOTE]
> Cloud App Security では、クラス最高レベルの暗号化を提供するために、トランスポート層セキュリティ (TLS) プロトコル 1.2 以降が活用されます。 TLS 1.2 以降をサポートしていないネイティブ クライアント アプリケーションとブラウザーは、セッション制御を使用して構成した場合、アクセスできなくなります。 ただし、TLS 1.1 以下を使用している SaaS アプリは、Cloud App Security を使用して構成されている場合、TLS 1.2 以降を使用しているようにブラウザーに表示されます。

<a name="featured-apps"></a>By natively integrating with Azure AD, any app that is configured with SAML or Open ID Connect you can onboard any app yourself. In addition, the following apps are featured by Cloud App Security and are already onboarded and ready to use in any tenant:

- AWS
- Azure DevOps (Visual Studio Team Services)
- Azure portal (プレビュー)
- ボックス
- Concur
- CornerStone on Demand
- DocuSign
- ドロップボックス
- Dynamics 365 CRM (preview)
- Egnyte
- Exchange Online
- G Suite
- GitHub
- HighQ
- JIRA/Confluence
- OneDrive for Business
- LinkedIn Learning
- Power BI
- Salesforce
- ServiceNow
- SharePo条件付きアクセスt Onl条件付きアクセスe
- Slack
- Tableau
- Microsoft Teams (プレビュー)
- Workday
- Workiva
- Workplace by Facebook
- Yammer (プレビュー)

### <a name="a-ido365-apps-office-365-featured-apps"></a><a id="O365-apps" />Office 365 featured apps

The following is a list of featured apps that are supported in Office 365 Cloud App Security:

- Exchange Online
- OneDrive for Business
- Power BI
- SharePo条件付きアクセスt Onl条件付きアクセスe
- Microsoft Teams (プレビュー)
- Yammer (プレビュー)

If you're interested in a specific app being featured, [send us details about the app](mailto:casfeedback@microsoft.com). 関心をお持ちのオンボード ユース ケースもお送りください。

> [!div class="step-by-step"]
> [次へ: Conditional Access App Control の展開 »](proxy-deployment-aad.md)

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Azure AD アプリでの条件付きアクセス アプリ制御の展開](proxy-deployment-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
