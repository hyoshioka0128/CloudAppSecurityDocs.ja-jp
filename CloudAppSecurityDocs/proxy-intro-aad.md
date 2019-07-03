---
title: Microsoft Cloud App Security のアプリの条件付きアクセス制御で保護する
description: この記事では、Cloud App Security アプリの条件付きアクセス制御のリバース プロキシのしくみに関する情報を提供します。
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
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: fca34e1bb6a9f83928ef3a4eaf388090468ce06a
ms.sourcegitcommit: ee00e0033bf45a5f795bfd3e1d71fa1f70f97acb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67511364"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Microsoft Cloud App Security Conditional Access App Control でアプリを保護する

*適用対象:Microsoft Cloud App Security*

>[!div class="step-by-step"]
[次へ:アプリの条件付きアクセス制御の展開 »](proxy-deployment-aad.md)

現代の職場では、多くの場合、犯行後にご利用のクラウド環境の状態を把握できるだけでは十分ではありません。 従業員が意図的に、あるいは不注意からデータや組織を危険にさらす前に、違反や漏洩をリアルタイムで防止することが望まれます。 組織内のユーザーが、クラウド アプリのほとんどのサービスとツールを利用できるようにし、個人所有デバイスで作業できるようにすることが重要です。 同時に、データ リークとデータ盗難から組織をリアルタイムで保護するのに役立つツールが必要です。 Azure Active Directory と共に、Microsoft Cloud App Security は Conditional Access App Control を使用する包括的な統合エクスペリエンスでこれらの機能を提供します。

> [!NOTE]
> Cloud App Security のアプリの条件付きアクセス制御を使用するには、[Azure Active Directory P1 ライセンス](https://azure.microsoft.com/pricing/details/active-directory/)と Microsoft Cloud App Security のアクティブなサブスクリプションが必要です。
>

## <a name="how-it-works"></a>しくみ

アプリの条件付きアクセス制御はリバース プロキシ アーキテクチャを利用し、Azure AD の条件付きアクセスと独自の方法で統合されます。 Azure AD の条件付きアクセスを使うと、特定の条件に基づくアクセス制御を組織のアプリに適用できます。 条件では、条件付きアクセス ポリシーの適用対象である "*人*" (ユーザーやユーザー グループ)、"*物*" (どのクラウド アプリか)、"*場所*" (どの場所とネットワークか) が定義されます。 条件が決まったら、ユーザーを Microsoft Cloud App Security にルーティングできます。ここで、アクセスおよびセッション制御を適用し、アプリの条件付きアクセス制御でデータを保護できます。

Conditional Access App Control では、アクセスおよびセッション ポリシーに基づいて、ユーザー アプリのアクセスとセッションをリアルタイムで監視して制御できます。 Cloud App Security ポータル内では、フィルターをさらに調整し、ユーザーに対して実行されるアクションを設定するために、アクセス ポリシーとセッション ポリシーが利用されます。 アクセス ポリシーとセッション ポリシーでは次のことができます。

- **データの流出を防ぐため**:ダウンロード、切り取り、コピー、ブロックし、たとえば、管理されていないデバイス上の機密文書の印刷できます。

- **ダウンロードの保護**:機密性の高いドキュメントのダウンロードをブロックする代わりに、ラベル付け、Azure Information Protection で保護するドキュメントを要求できます。 この動作により、ドキュメントが保護されているし、リスクの高いセッションでユーザーのアクセスを制限します。

- **ラベルのないファイルのアップロードを防ぐため**:機密性の高いファイルがアップロードされた、分散、および他のユーザーによって使用されると、前に、ファイルに正しいラベルと保護があることを確認してください。 機密性の高いコンテンツを持つラベル付けされていないファイルが、ユーザーは、コンテンツを分類するまでのアップロードからブロックされているを確認できます。

- **コンプライアンスのためのユーザー セッションを監視**:危険性の高いユーザーはアプリにサインインするときに監視され、アクションはセッション内からログに記録されます。 ユーザーの行動を調査して分析し、将来的に、どこで、どのような状況において、セッション ポリシーを適用する必要があるかを理解できます。

- **[アクセスのブロック]** : 細かく、特定のアプリといくつかのリスク要因に依存しているユーザーのアクセスをブロックできます。 たとえば、デバイス管理の形式としてクライアント証明書を使用している場合にブロックすることができます。

- **カスタム アクティビティをブロック**:一部のアプリケーションでは、たとえば、Microsoft Teams、Slack などのアプリケーションで機密性の高いコンテンツを持つメッセージを送信するリスクを持つ一意のシナリオがあります。 これらの種類のシナリオでは、機密性の高いコンテンツ メッセージをスキャンし、それらをリアルタイムでブロックできます。

### <a name="how-session-control-works"></a>セッション制御のしくみ

Conditional Access App Control でセッション ポリシーを作成することで、直接アプリにではなく、リバース プロキシ経由でユーザーをリダイレクトして、ユーザー セッションを制御できます。 ユーザーの要求と応答は、Cloud App Security ではなく、アプリに直接移動します。

セッションがプロキシによって保護されると、関連する Url と cookie が Cloud App Security によって置き換えられます。 たとえば、ドメインが myapp.com で終わるリンクを含むページをアプリが返した場合、そのリンクは myapp.com.us.cas.ms などで終わるドメインに置き換えられます。

この方法は、にとって理想的なは、監視または管理されていないデバイスまたはパートナーのユーザーからのセッションを制御するときに、デバイスに何もインストールすることで必要はありません。

## <a name="managed-device-identification"></a>マネージド デバイスの識別

Conditional Access App Control を使うと、デバイスが管理されているかどうかを考慮するポリシーを作成できます。 デバイスが管理されているかどうかを識別するため、この機能では以下を利用します。

- 準拠しているデバイス
- ドメインに参加しているデバイス
- クライアント証明書のデプロイ
 
### <a name="compliant-and-domain-joined-devices"></a>準拠していてドメインに参加済みのデバイス

Azure AD の条件付きアクセスでは、準拠しているデバイスとドメインに参加しているデバイスの情報を、Microsoft Cloud App Security に直接渡すことができます。 その情報から、デバイスの状態をフィルターとして使うアクセス ポリシーまたはセッション ポリシーを開発できます。
詳しくは、「[Azure Active Directory のデバイス管理の概要](https://docs.microsoft.com/azure/active-directory/device-management-introduction)」をご覧ください。 

### <a name="client-certificate-authenticated-devices"></a>クライアント証明書で認証されたデバイス

デバイス識別メカニズムでは、クライアント証明書を使って関連するデバイスに認証を要求することができます。 組織で既に展開されている既存のクライアント証明書を使用するか、新しいクライアント証明書をマネージド デバイスにロールアウトできます。 それらの証明書の存在を利用し、アクセスやセッションのポリシーを設定します。

SSL クライアント証明書が信頼チェーンを使用して検証されます。 X.509 ルートまたは中間証明書機関 (CA) 証明書の PEM 形式で書式設定をアップロードすることができます。 これらの証明書は、セッション中に表示されるクライアント証明書の署名を使用して、CA の公開キーを含める必要があります。

証明書をアップロードし、関連するポリシーが構成されている、適用可能なセッションを Conditional Access App Control を通過するときに、Cloud App Security のエンドポイントは、ブラウザー クライアント SSL 証明書の提示を要求します。 ブラウザーは、秘密キーと共にインストールされる証明書を SSL クライアントに機能します。 この証明書と秘密キーの組み合わせは、PKCS #12 ファイル形式、通常 .p12 または .pfx を使用して行われます。

クライアント証明書の確認を実行すると、Cloud App Security を次の条件を確認します。

1. 選択したクライアント証明書は有効は、正しいルートまたは中間 CA 下。
1. (CRL が有効になっている) 場合は、証明書は失効しません。

クライアント証明書をデプロイする方法については、「[Azure AD アプリでの条件付きアクセス アプリ制御の展開](proxy-deployment-aad.md)」を参照してください。

## <a name="supported-apps-and-clients"></a>サポートされているアプリとクライアント

アプリの条件付きアクセス制御では現在のところ、シングル サインオンで構成された SAML アプリと Open ID Connect アプリ、[Azure AD App Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) で構成され、オンプレミスでホストされている Web アプリがサポートされています。
> [!NOTE]
> アプリの条件付きアクセス制御では、Azure AD 以外の ID プロバイダーで構成されたアプリもサポートされます。 このシナリオの詳細については、mcaspreview@microsoft.com に電子メールをお送りください。

**セッション制御は、あらゆるオペレーティング システム上の、すべての主要なプラットフォーム上のすべてのブラウザーで使用可能です**。 Internet Explorer 11、Microsoft Edge (最新)、Google Chrome (最新)、Mozilla Firefox (最新)、または Apple Safari (最新) を使用することをお勧めします。 モバイル アプリとデスクトップ アプリは許可またはブロックすることもできます。 ネイティブ Azure AD との統合で SAML または Open ID Connect で構成されているすべてのアプリは、自己オンボードを指定できます。 さらに、次のアプリは Cloud App Security では機能を備えたが既にオンボードし、任意のテナントで使用する準備ができました。

- AWS
- Azure DevOps (Visual Studio Team Services)
- Azure portal (プレビュー)
- ボックス
- Concur
- CornerStone on Demand
- DocuSign
- ドロップボックス
- Dynamics 365 CRM (プレビュー)
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
- SharePoint Online
- Slack
- Tableau
- Microsoft Teams (プレビュー)
- Workday
- Workiva
- Workplace by Facebook
- Yammer (プレビュー)

特定の機能を備えたされているアプリで関心がある場合[アプリの詳細をお送り](mailto:casfeedback@microsoft.com)します。 関心をお持ちのオンボード ユース ケースもお送りください。

>[!div class="step-by-step"]
[次へ:アプリの条件付きアクセス制御の展開 »](proxy-deployment-aad.md)

## <a name="next-steps"></a>次の手順
[Azure AD アプリでの条件付きアクセス アプリ制御の展開](proxy-deployment-aad.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)