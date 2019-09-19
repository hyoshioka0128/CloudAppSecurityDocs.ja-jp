---
title: Microsoft Cloud App Security のアプリの条件付きアクセス制御で保護する
description: この記事では、Cloud App Security アプリの条件付きアクセス制御のリバース プロキシのしくみに関する情報を提供します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 8/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 10f17632f5b611b86b1555ff50be5237c103ea88
ms.sourcegitcommit: 8a49c166424fea83853b0a6895212367526abe78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71085031"
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

- **データを禁止する**:管理されていないデバイスなど、機密性の高いドキュメントのダウンロード、切り取り、コピー、および印刷をブロックできます。

- **ダウンロードの保護**:機密性の高いドキュメントのダウンロードをブロックするのではなく、ドキュメントにラベルを付け、Azure Information Protection で保護するように要求することができます。 この操作により、ドキュメントが保護され、ユーザーアクセスが危険な可能性のあるセッションで制限されます。

- **ラベルのないファイルをアップロードできないようにする**:機密ファイルがアップロードされ、配布されて、他のユーザーによって使用される前に、ファイルに適切なラベルと保護が設定されていることを確認することが重要です。 機密コンテンツが含まれているラベルのないファイルが、ユーザーがコンテンツを分類するまでアップロードされないようにすることができます。

- **コンプライアンス対応のユーザーセッションの監視**:危険性の高いユーザーはアプリにサインインするときに監視され、アクションはセッション内からログに記録されます。 ユーザーの行動を調査して分析し、将来的に、どこで、どのような状況において、セッション ポリシーを適用する必要があるかを理解できます。

- **[アクセスのブロック]** : いくつかのリスク要因に応じて、特定のアプリとユーザーのアクセスを細かくブロックできます。 たとえば、デバイス管理の形式としてクライアント証明書を使用している場合は、ブロックできます。

- **カスタムアクティビティをブロック**する:アプリケーションによっては、Microsoft Teams や余裕のようなアプリケーションで機密性の高いコンテンツを含むメッセージを送信するなど、リスクを伴う固有のシナリオがあります。 このようなシナリオでは、機密性の高いコンテンツのメッセージをスキャンし、リアルタイムでブロックできます。

### <a name="how-session-control-works"></a>セッション制御のしくみ

Conditional Access App Control でセッション ポリシーを作成することで、直接アプリにではなく、リバース プロキシ経由でユーザーをリダイレクトして、ユーザー セッションを制御できます。 その後、ユーザーの要求と応答は、アプリに直接ではなく Cloud App Security 経由で実行されます。

セッションがプロキシによって保護されている場合、関連するすべての Url と cookie が Cloud App Security に置き換えられます。 たとえば、ドメインが myapp.com で終わるリンクを含むページをアプリが返した場合、そのリンクは myapp.com.us.cas.ms などで終わるドメインに置き換えられます。

この方法では、デバイスに何もインストールする必要はありません。管理されていないデバイスやパートナーユーザーからのセッションを監視または制御する場合に最適です。

> [!NOTE]
> Cloud App Security では、世界中の Azure データ センターが活用され、位置情報によって最適化されたパフォーマンスが提供されます。 つまり、トラフィック パターンとその場所によっては、ユーザーのセッションが特定のリージョンの外部でホストされる可能性があります。 ただし、お客様のプライバシーを保護するために、これらのデータ センターにセッション データが保存されることはありません。

## <a name="managed-device-identification"></a>マネージド デバイスの識別

Conditional Access App Control を使うと、デバイスが管理されているかどうかを考慮するポリシーを作成できます。 デバイスが管理されているかどうかを識別するため、この機能では以下を利用します。

- 準拠しているデバイス
- ドメインに参加しているデバイス
- クライアント証明書のデプロイ

### <a name="compliant-and-domain-joined-devices"></a>準拠していてドメインに参加済みのデバイス

Azure AD の条件付きアクセスでは、準拠しているデバイスとドメインに参加しているデバイスの情報を、Microsoft Cloud App Security に直接渡すことができます。 その情報から、デバイスの状態をフィルターとして使うアクセス ポリシーまたはセッション ポリシーを開発できます。 詳しくは、「[Azure Active Directory のデバイス管理の概要](https://docs.microsoft.com/azure/active-directory/device-management-introduction)」をご覧ください。

> [!NOTE]
> 一部のブラウザーでは、拡張機能のインストールなどの追加の構成が必要になる場合があります。 詳細については、「[条件付きアクセスブラウザーのサポート](https://go.microsoft.com/fwlink/?linkid=2102732)」を参照してください。

### <a name="client-certificate-authenticated-devices"></a>クライアント証明書で認証されたデバイス

デバイス識別メカニズムでは、クライアント証明書を使って関連するデバイスに認証を要求することができます。 組織で既に展開されている既存のクライアント証明書を使用するか、新しいクライアント証明書をマネージド デバイスにロールアウトできます。 それらの証明書の存在を利用し、アクセスやセッションのポリシーを設定します。

SSL クライアント証明書は、信頼チェーンによって検証されます。 PEM 証明書形式でフォーマットされた x.509 ルートまたは中間証明機関 (CA) をアップロードできます。 これらの証明書には、CA の公開キーが含まれている必要があります。これは、セッション中に提示されたクライアント証明書の署名に使用されます。

証明書がアップロードされ、関連するポリシーが構成されている場合、該当するセッションがアプリの条件付きアクセス制御になると、Cloud App Security エンドポイントはブラウザーに SSL クライアント証明書を提示するように要求します。 ブラウザーは、秘密キーと共にインストールされる SSL クライアント証明書を提供します。 この証明書と秘密キーの組み合わせは、PKCS #12 ファイル形式 (通常は p12 または .pfx) を使用して行われます。

クライアント証明書の確認を実行すると、Cloud App Security によって次の条件が確認されます。

1. 選択されたクライアント証明書は有効で、正しいルート CA または中間 CA の下にあります。
1. 証明書は失効していません (CRL が有効になっている場合)。

> [!NOTE]
> ほとんどの主要なブラウザーは、クライアント証明書の確認をサポートしています。 ただし、モバイルアプリとデスクトップアプリは、多くの場合、このチェックをサポートしていないため、これらのアプリの認証に影響を与える組み込みのブラウザーを活用します。

クライアント証明書をデプロイする方法については、「[Azure AD アプリでの条件付きアクセス アプリ制御の展開](proxy-deployment-aad.md)」を参照してください。

## <a name="supported-apps-and-clients"></a>サポートされているアプリとクライアント

アプリの条件付きアクセス制御では現在のところ、シングル サインオンで構成された SAML アプリと Open ID Connect アプリ、[Azure AD App Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) で構成され、オンプレミスでホストされている Web アプリがサポートされています。
> [!NOTE]
> アプリの条件付きアクセス制御では、Azure AD 以外の ID プロバイダーで構成されたアプリもサポートされます。 このシナリオの詳細については、mcaspreview@microsoft.com に電子メールをお送りください。

**セッション制御は、あらゆるオペレーティング システム上の、すべての主要なプラットフォーム上のすべてのブラウザーで使用可能です**。 Internet Explorer 11、Microsoft Edge (最新)、Google Chrome (最新)、Mozilla Firefox (最新)、または Apple Safari (最新) を使用することをお勧めします。 モバイルアプリとデスクトップアプリへのアクセスをブロックまたは許可することもできます。

> [!NOTE]
> アクセスポリシーで**クライアントアプリ**フィルターを使用すると、結果として得られるユーザーセッションが Cloud App Security によってプロキシ化される可能性があります。

> [!NOTE]
> Cloud App Security では、クラス最高レベルの暗号化を提供するために、トランスポート層セキュリティ (TLS) プロトコル 1.2 以降が活用されます。 TLS 1.2 以降をサポートしていないネイティブ クライアント アプリケーションとブラウザーは、セッション制御を使用して構成した場合、アクセスできなくなります。 ただし、TLS 1.1 以下を使用している SaaS アプリは、Cloud App Security を使用して構成されている場合、TLS 1.2 以降を使用しているようにブラウザーに表示されます。

Azure AD とネイティブに統合することにより、SAML または Open ID Connect で構成されているすべてのアプリを自己オンボードにすることができます。 さらに、次のアプリは Cloud App Security によって機能しており、既にオンボードで、任意のテナントで使用する準備ができています。

- AWS
- Azure DevOps (Visual Studio Team Services)
- Azure portal (プレビュー)
- ボックス
- Concur
- CornerStone on Demand
- DocuSign
- Dropbox
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

おすすめのアプリに関心がある場合は、[アプリに関する詳細情報をお送り](mailto:casfeedback@microsoft.com)ください。 関心をお持ちのオンボード ユース ケースもお送りください。

>[!div class="step-by-step"]
[次へ:アプリの条件付きアクセス制御の展開 »](proxy-deployment-aad.md)

## <a name="next-steps"></a>次の手順

[Azure AD アプリでの条件付きアクセス アプリ制御の展開](proxy-deployment-aad.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)
