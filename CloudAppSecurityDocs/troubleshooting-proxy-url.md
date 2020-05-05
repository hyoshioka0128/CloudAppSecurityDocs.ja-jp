---
title: トラブルシューティング-cas.ms、mcas.ms、または mcas-gov.us とは何ですか?
description: この記事では、アプリの条件付きアクセス制御によって使用される cas.ms、mcas.ms、または mcas-gov.us の URL サフィックスに関する情報を提供します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/18/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 91ad245b71167785a724e02b995d33dfd2da4c20
ms.sourcegitcommit: baa9cb55d9d82808602a58ee24eeba7d83e92742
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82738996"
---
# <a name="troubleshooting---what-is-casms-mcasms-or-mcas-govus"></a>トラブルシューティング- `*.cas.ms`、 `*.mcas.ms`、または`*.mcas-gov.us`

*適用対象:Microsoft Cloud App Security*

この記事では`cas.ms`、アプリの条件付きアクセス制御に`mcas.ms`よって`mcas-gov.us`使用される、、および URL サフィックスに関する情報を提供します。

## <a name="our-system-flagged-a-new-dns-entry-or-generated-certificate-for-casms-mcasms-or-mcas-govus-but-we-dont-use-cloud-app-security"></a>システムは、 `*.mcas.ms`、、または`*.mcas-gov.us`の新しい DNS エントリ`*.cas.ms`または生成された証明書にフラグを設定しましたが、を使用していません Cloud App Security

これは、環境を保護する Cloud App Security の通常の動作と結果です。 組織で Cloud App Security を使用していない場合でも、を使用している環境から他のユーザーがサイトまたはサービスにアクセスすると、その Url が書き換えられてアクセスが保護されます。

たとえば、Contoso は Cloud App Security によって提供されるアプリの条件付きアクセス制御を使用して環境を保護します。 Contoso ユーザーがアクセス`fabrikam.com`すると、ユーザーは自動的にに`fabrikam.com.<region>.cas.ms`リダイレクトされます。 その結果、Fabrikam のフィッシングチームには、の`fabrikam.com.<region>.cas.ms`新しい DNS エントリと証明書が表示されます。

そのため、Fabrikam は実際には Cloud App Security を使用しませんが、DNS エントリまたは証明書が表示されます。

> [!NOTE]
> また、透過性ログに次のドメインが表示される場合もあります。
>
> - `*.admin-rs-mcas.ms`
> - `*.rs-mcas.ms`
> - `*.admin-rs2-mcas.ms`
> - `*.rs2-mcas.ms`
> - `*.admin-mcas.ms`
> - `*.mcas.ms`

## <a name="heres-why-you-see-casms-mcasms-or-mcas-govus-in-your-url"></a>URL に、、また`*.cas.ms`は`*.mcas.ms`が表示`*.mcas-gov.us`されるのは、次のようになります。

まず、フィッシングていません。 この種類の URL が想定されており、組織がビジネスに不可欠なデータを保護するために追加のセキュリティ制御を適用することを示しています。

これを行うには、組織のクラウド環境を保護するためのソリューションである Cloud App Security を使用します。これにより、使用するクラウドアプリに関連するすべての Url と cookie を置き換えることができます。

そのため、Salesforce、SharePoint Online、AWS などのクラウドアプリにアクセスしようとすると、URL の末尾に、 `<region>.cas.ms` `<region>.mcas.ms`、または`<region>.mcas-gov.us`が付いていることがわかります。 たとえば、XYZ アプリを使用する場合、から`XYZ.com`へ`XYZ.com.<region>.cas.ms`の変更を確認するために使用されている URL です。

URL が置換パターンのいずれかと完全に一致しない場合 (たとえば`<app_site>.com` 、がに`<app_site>.com.<region>.cas.ms`置き換えられない場合)、または追加の懸念事項がある場合は、IT 部門に問い合わせてください。
