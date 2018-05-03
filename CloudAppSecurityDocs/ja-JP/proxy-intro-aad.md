---
title: Microsoft Cloud App Security Conditional Access App Control で保護する | Microsoft Docs
description: このトピックでは、Cloud App Security Conditional Access App Control リバース プロキシのしくみに関する情報を提供します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/25/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 35a43120-bf67-4cf9-9b48-ebe157dbbd18
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ebc88634d6a4b83effe598c45f8da62338cebf53
ms.sourcegitcommit: c5dbeb75e409518feaa26200e9a02c59accc8dcc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
*適用対象: Microsoft Cloud App Security*


# <a name="protect-apps-with-microsoft-cloud-app-security-conditional-access-app-control"></a>Microsoft Cloud App Security Conditional Access App Control でアプリを保護する

> [!NOTE]
> これはプレビュー機能です。


現在のワークプレースでは、多くの場合、クラウド環境で起こっていることを後で知るようでは十分ではありません。従業員が意図的に、または誤ってデータと組織を危険にさらす前に、リアルタイムで違反やリークを防げるようにする必要があります。 組織内のユーザーが、クラウド アプリのほとんどのサービスとツールを利用できるようにし、個人所有デバイスで作業できるようにすることが重要です。 同時に、データ リークとデータ盗難から組織をリアルタイムで保護するのに役立つツールが必要です。 Azure Active Directory と共に、Microsoft Cloud App Security は Conditional Access App Control を使用する包括的な統合エクスペリエンスでこれらの機能を提供します。

## <a name="how-it-works"></a>しくみ

Conditional Access App Control はリバース プロキシ アーキテクチャを利用し、Azure AD の条件付きアクセスと一意に統合されます。 Azure AD の条件付きアクセスを使うと、特定の条件に基づくアクセス制御を組織のアプリに適用できます。 条件では、条件付きアクセス ポリシーの適用対象である "*人*" (たとえば、ユーザーやユーザー グループ)、"*物*" (どのクラウド アプリか)、"*場所*" (どの場所とネットワークか) が定義されています。 条件が決まったら、ユーザーを Microsoft Cloud App Security にルーティングできます。ここで、アクセスおよびセッション制御を適用し、Conditional Access App Control でデータを保護することができます。

Conditional Access App Control では、アクセスおよびセッション ポリシーに基づいて、ユーザー アプリのアクセスとセッションをリアルタイムで監視して制御できます。 Cloud App Security ポータル内では、フィルターをさらに調整し、ユーザーに対して実行されるアクションを設定するために、アクセス ポリシーとセッション ポリシーが利用されます。 アクセス ポリシーとセッション ポリシーでは次のことができます。

-   **ダウンロードのブロック**: 機密性の高いドキュメントのダウンロードをブロックすることができます。 たとえば、管理されていないデバイスでのダウンロードなどです。

-   **ダウンロードの保護**: 機密性の高いドキュメントのダウンロードをブロックする代わりに、ダウンロードに暗号化を使ってドキュメントを保護するように要求できます。 これにより、データが信頼されていないデバイスにダウンロードされる場合に、ドキュメントを保護し、ユーザー アクセスを認証できます。 

-   **会社以外のネットワークからのユーザー セッションを制限**: 会社のネットワークの一部ではない場所から保護されたアプリにアクセスしているユーザーは制限されたアクセスを許可され、機密情報のダウンロードはブロックまたは保護されます。

-   **信頼性の低いユーザー セッションの監視**: 危険性の高いユーザーはアプリにサインインするときに監視され、アクションはセッション内からログに記録されます。 ユーザーの行動を調査して分析し、将来的に、どこで、どのような状況において、セッション ポリシーを適用する必要があるかを理解できます。 

- **アクセスのブロック**: ユーザーが管理対象外のデバイスや会社のものではないネットワークを利用している場合、特定のアプリへのアクセスを完全にブロックできます。


### <a name="how-session-control-works"></a>セッション制御のしくみ

Conditional Access App Control でセッション ポリシーを作成することで、直接アプリにではなく、リバース プロキシ経由でユーザーをリダイレクトして、ユーザー セッションを制御できます。 それ以降、ユーザーの要求と応答は、直接アプリにではなく、Microsoft Cloud App Security を介して行われます。

セッション内でユーザーを保持するために、アプリ セッション内の関連するすべての URL、Java スクリプト、Cookie が Microsoft Cloud App Security の URL に置き換えられます。 たとえば、ドメインが myapp.com で終わるリンクを含むページをアプリが返した場合、そのリンクは myapp.com.us.cas.ms などで終わるドメインに置き換えられます。 

この方法では、デバイスに何もインストールする必要はありません。 これは、管理されていないデバイスからのセッションを監視するときに最適です。 

Microsoft Cloud App Security を介してセッションが送信されたら、以下の操作を実行できます。
1. トラフィックでユーザーのアクティビティを調べます
2. Microsoft Cloud App Security のアクティビティ ログに識別されたアクティビティを表示します
3. トラフィックのログを保存して分析します
4. 管理者がトラフィック ログをエクスポートできるようにします
5. セッションに対してポリシーを適用します

## <a name="managed-device-identification"></a>管理されたデバイスの識別

Conditional Access App Control を使うと、デバイスが管理されているかどうかを考慮するポリシーを作成できます。 デバイスが管理されているかどうかを識別するため、この機能では以下を利用します。

-   準拠しているデバイス 
-   ドメインに参加しているデバイス 
-   クライアント証明書のデプロイ
 
 
### <a name="compliant-and-domain-joined-devices"></a>準拠していてドメインに参加済みのデバイス
Azure AD の条件付きアクセスでは、準拠しているデバイスとドメインに参加しているデバイスの情報を、Microsoft Cloud App Security に直接渡すことができます。 その情報から、デバイスの状態をフィルターとして使うアクセス ポリシーまたはセッション ポリシーを開発できます。
詳しくは、「[Azure Active Directory のデバイス管理の概要](https://docs.microsoft.com/azure/active-directory/device-management-introduction)」をご覧ください。 

### <a name="client-certificate-authenticated-devices"></a>クライアント証明書で認証されたデバイス

デバイス識別メカニズムでは、クライアント証明書を使って関連するデバイスに認証を要求することができます。 これにより、組織内に既にデプロイされている既存のクライアント証明書を利用するか、または新しいクライアント証明書を管理されたデバイスにデプロイした後、それらの証明書の存在を使ってアクセス ポリシーとセッション ポリシーを設定することができます。 クライアント証明書をデプロイする方法については、「[Azure AD アプリでの条件付きアクセス アプリ制御の展開](proxy-deployment-aad.md)」を参照してください。
 
## <a name="supported-apps-and-clients"></a>サポートされているアプリとクライアント

現在、Conditional Access App Control では、Azure AD の SAML シングル サインオンで構成されているアプリがサポートされます。 

> [!NOTE]
> - Conditional Access App Control では、プライベート プレビューの Azure AD 以外の ID プロバイダーで構成されたアプリもサポートされます。 プライベート プレビューに関する詳細については、mcaspreview@microsoft.com に電子メールをお送りください。
> - Office 365 アプリケーションは SAML を構成されないため、現在はサポートされていません。

セッション制御は任意の主なプラットフォーム上の任意のブラウザーで使用できます (モバイル アプリとデスクトップ アプリは現在サポートされていません)。 Azure AD とネイティブで統合すると、次の機能を備えたアプリを含む、 Azure AD での SAML シングル サインオンで構成されているすべてのアプリをサポートできます。

-   Salesforce

-   ボックス

-   G Suite

-   Workday

-   Slack

-   Workplace by Facebook

-   ServiceNow

-   JIRA/Confluence

-   AWS

-   Workiva

-   CornerStone on Demand

-   DocuSign

-   HighQ 

セッション制御には、その他のアプリが継続的に搭載されます。 ここに記載されていない特定のアプリに関心がある場合は、[アプリの詳細を送っていただき](mailto:casfeedback@microsoft.com)、ユース ケースとして関心があれば、そのアプリが搭載されます。




## <a name="see-also"></a>参照  
[Azure AD アプリでの条件付きアクセス アプリ制御の展開](proxy-deployment-aad.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  


