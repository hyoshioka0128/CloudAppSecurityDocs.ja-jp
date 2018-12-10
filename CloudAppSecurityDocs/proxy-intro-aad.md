---
title: Microsoft Cloud App Security Conditional Access App Control で保護する | Microsoft Docs
description: この記事では、Cloud App Security アプリの条件付きアクセス制御のリバース プロキシのしくみに関する情報を提供します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 45584e4382583d2d14be452a21af91ee693439c9
ms.sourcegitcommit: 5d3a057a8bb2cb98fd7350775e46b0e4d34763ed
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52386266"
---
# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Microsoft Cloud App Security Conditional Access App Control でアプリを保護する

*適用対象: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[次へ: Conditional Access App Control の展開 »](proxy-deployment-aad.md)


現代の職場では、多くの場合、犯行後にご利用のクラウド環境の状態を把握できるだけでは十分ではありません。 従業員が意図的に、あるいは不注意からデータや組織を危険にさらす前に、違反や漏洩をリアルタイムで防止することが望まれます。 組織内のユーザーが、クラウド アプリのほとんどのサービスとツールを利用できるようにし、個人所有デバイスで作業できるようにすることが重要です。 同時に、データ リークとデータ盗難から組織をリアルタイムで保護するのに役立つツールが必要です。 Azure Active Directory と共に、Microsoft Cloud App Security は Conditional Access App Control を使用する包括的な統合エクスペリエンスでこれらの機能を提供します。

> [!NOTE]
> Cloud App Security のアプリの条件付きアクセス制御を使用するには、[Azure Active Directory P1 ライセンス](https://azure.microsoft.com/pricing/details/active-directory/)と Microsoft Cloud App Security のアクティブなサブスクリプションが必要です。
>

## <a name="how-it-works"></a>しくみ

アプリの条件付きアクセス制御はリバース プロキシ アーキテクチャを利用し、Azure AD の条件付きアクセスと独自の方法で統合されます。 Azure AD の条件付きアクセスを使うと、特定の条件に基づくアクセス制御を組織のアプリに適用できます。 条件では、条件付きアクセス ポリシーの適用対象である "*人*" (ユーザーやユーザー グループ)、"*物*" (どのクラウド アプリか)、"*場所*" (どの場所とネットワークか) が定義されます。 条件が決まったら、ユーザーを Microsoft Cloud App Security にルーティングできます。ここで、アクセスおよびセッション制御を適用し、アプリの条件付きアクセス制御でデータを保護できます。

Conditional Access App Control では、アクセスおよびセッション ポリシーに基づいて、ユーザー アプリのアクセスとセッションをリアルタイムで監視して制御できます。 Cloud App Security ポータル内では、フィルターをさらに調整し、ユーザーに対して実行されるアクションを設定するために、アクセス ポリシーとセッション ポリシーが利用されます。 アクセス ポリシーとセッション ポリシーでは次のことができます。

- **ダウンロードのブロック**: 機密性の高いドキュメントのダウンロードをブロックすることができます。 たとえば、管理されていないデバイスでのダウンロードなどです。

- **ダウンロードの保護**: 機密性の高いドキュメントのダウンロードをブロックする代わりに、ダウンロードに暗号化を使ってドキュメントを保護するように要求できます。 この暗号化により、データが信頼されていないデバイスにダウンロードされる場合に、ドキュメントを保護し、ユーザー アクセスを認証できます。 

- **信頼性の低いユーザー セッションの監視**: 危険性の高いユーザーはアプリにサインインするときに監視され、アクションはセッション内からログに記録されます。 ユーザーの行動を調査して分析し、将来的に、どこで、どのような状況において、セッション ポリシーを適用する必要があるかを理解できます。 

- **アクセスのブロック**: ユーザーが管理対象外のデバイスや会社のものではないネットワークを利用している場合、特定のアプリへのアクセスを完全にブロックできます。

- **読み取り専用モードの作成**: カスタムのアプリ内アクティビティを監視してブロックすることで、特定ユーザーの特定のアプリに対する読み取り専用モードを作成することができます。  

- **会社以外のネットワークからのユーザー セッションを制限**: 会社のネットワークの一部ではない場所から保護されたアプリにアクセスしているユーザーは制限されたアクセスを許可されます。 機密情報のダウンロードはブロックまたは保護されます。

### <a name="how-session-control-works"></a>セッション制御のしくみ

Conditional Access App Control でセッション ポリシーを作成することで、直接アプリにではなく、リバース プロキシ経由でユーザーをリダイレクトして、ユーザー セッションを制御できます。 それ以降、ユーザーの要求と応答は、直接アプリにではなく、Microsoft Cloud App Security を介して行われます。

セッション内でユーザーを保持するために、アプリ セッション内の関連するすべての URL、Java スクリプト、Cookie が Microsoft Cloud App Security の URL に置き換えられます。 たとえば、ドメインが myapp.com で終わるリンクを含むページをアプリが返した場合、そのリンクは myapp.com.us.cas.ms などで終わるドメインに置き換えられます。 

この方法では、デバイスに何もインストールする必要はありません。 この方法は、管理されていないデバイスからのセッションを監視するときに最適です。 

Microsoft Cloud App Security を介してセッションが送信されたら、以下の操作を実行できます。

1. トラフィックでユーザーのアクティビティを調べます
2. Microsoft Cloud App Security のアクティビティ ログに識別されたアクティビティを表示します
3. トラフィックのログを保存して分析します
4. 管理者がトラフィック ログをエクスポートできるようにします
5. セッションに対してポリシーを適用します

## <a name="managed-device-identification"></a>マネージド デバイスの識別

Conditional Access App Control を使うと、デバイスが管理されているかどうかを考慮するポリシーを作成できます。 デバイスが管理されているかどうかを識別するため、この機能では以下を利用します。

- 準拠しているデバイス
- ドメインに参加しているデバイス
- クライアント証明書のデプロイ
 
### <a name="compliant-and-domain-joined-devices"></a>準拠していてドメインに参加済みのデバイス

Azure AD の条件付きアクセスでは、準拠しているデバイスとドメインに参加しているデバイスの情報を、Microsoft Cloud App Security に直接渡すことができます。 その情報から、デバイスの状態をフィルターとして使うアクセス ポリシーまたはセッション ポリシーを開発できます。
詳しくは、「[Azure Active Directory のデバイス管理の概要](https://docs.microsoft.com/azure/active-directory/device-management-introduction)」をご覧ください。 

### <a name="client-certificate-authenticated-devices"></a>クライアント証明書で認証されたデバイス

デバイス識別メカニズムでは、クライアント証明書を使って関連するデバイスに認証を要求することができます。 組織で既に展開されている既存のクライアント証明書を使用するか、新しいクライアント証明書をマネージド デバイスにロールアウトできます。 それらの証明書の存在を利用し、アクセスやセッションのポリシーを設定します。 クライアント証明書をデプロイする方法については、「[Azure AD アプリでの条件付きアクセス アプリ制御の展開](proxy-deployment-aad.md)」を参照してください。
 
## <a name="supported-apps-and-clients"></a>サポートされているアプリとクライアント

アプリの条件付きアクセス制御では現在のところ、シングル サインオンで構成された SAML アプリと Open ID Connect アプリ、[Azure AD App Proxy](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) で構成され、オンプレミスでホストされている Web アプリがサポートされています。
> [!NOTE]
> アプリの条件付きアクセス制御では、Azure AD 以外の ID プロバイダーで構成されたアプリもサポートされます。 このシナリオの詳細については、mcaspreview@microsoft.com に電子メールをお送りください。

セッション制御はすべての主要なプラットフォーム上のすべてのブラウザーで使用可能です。 モバイル アプリとデスクトップ アプリは許可またはブロックすることもできます。 Azure AD とネイティブに統合すると、次の機能を備えたアプリを含む、SAML で構成されたアプリおよび Azure AD においてシングル サインオンで構成された Open ID Connect アプリをサポートできます。

- AWS
- ボックス
- Concur
- CornerStone on Demand
- DocuSign
- ドロップボックス
- Egnyte
- G Suite
- GitHub
- HighQ
- JIRA/Confluence
- Salesforce
- ServiceNow
- Slack
- Tableau
- Workday
- Workiva
- Workplace by Facebook
- Exchange Online (プレビュー)
- OneDrive for Business (プレビュー)
- Power BI (プレビュー)
- SharePoint Online (プレビュー)
- Azure DevOps (Visual Studio Team Services) (プレビュー)
- Yammer (プレビュー)



セッション制御には、その他のアプリが継続的に搭載されます。 ここで取り上げていないアプリに関心をお持ちの場合、[アプリに関する詳細をお送りください](mailto:casfeedback@microsoft.com)。 関心をお持ちのオンボード ユース ケースもお送りください。



>[!div class="step-by-step"]
[次へ: Conditional Access App Control の展開 »](proxy-deployment-aad.md)


## <a name="next-steps"></a>次の手順
[Azure AD アプリでの条件付きアクセス アプリ制御の展開](proxy-deployment-aad.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  


