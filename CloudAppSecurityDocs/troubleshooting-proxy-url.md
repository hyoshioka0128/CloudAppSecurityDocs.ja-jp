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
ms.openlocfilehash: 9759be6e7c6cddd1b3140fd00bd19834c235352b
ms.sourcegitcommit: 6886d285601955f0efc7acf980c9d4740ff873fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2020
ms.locfileid: "84250606"
---
# <a name="troubleshooting---what-is-casms-mcasms-or-mcas-govus"></a>トラブルシューティング- `*.cas.ms` 、 `*.mcas.ms` 、または `*.mcas-gov.us`

*適用対象:Microsoft Cloud App Security*

この記事では `cas.ms` 、 `mcas.ms` `mcas-gov.us` アプリの条件付きアクセス制御によって使用される、、および URL サフィックスに関する情報を提供します。

## <a name="our-system-flagged-a-new-dns-entry-or-generated-certificate-for-casms-mcasms-or-mcas-govus-but-we-dont-use-cloud-app-security"></a>システムは、、、またはの新しい DNS エントリまたは生成された証明書にフラグを設定しましたが、を `*.cas.ms` `*.mcas.ms` `*.mcas-gov.us` 使用していません Cloud App Security

これは、環境を保護する Cloud App Security の通常の動作と結果です。 組織で Cloud App Security を使用していない場合でも、を使用している環境から他のユーザーがサイトまたはサービスにアクセスすると、その Url が書き換えられてアクセスが保護されます。

たとえば、Contoso は Cloud App Security によって提供されるアプリの条件付きアクセス制御を使用して環境を保護します。 Contoso ユーザーがアクセスすると `fabrikam.com` 、ユーザーは自動的ににリダイレクトされ `fabrikam.com.cas.ms` ます。 その結果、Fabrikam のフィッシングチームには、の新しい DNS エントリと証明書が表示され `fabrikam.com.cas.ms` ます。

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

## <a name="heres-why-you-see-casms-mcasms-or-mcas-govus-in-your-url"></a>`*.cas.ms`URL に、、またはが表示されるのは、次のようになります。 `*.mcas.ms` `*.mcas-gov.us`

まず、フィッシングていません。 この種類の URL が想定されており、組織がビジネスに不可欠なデータを保護するために追加のセキュリティ制御を適用することを示しています。

これを行うには、組織のクラウド環境を保護するためのソリューションである Cloud App Security を使用します。これにより、使用するクラウドアプリに関連するすべての Url と cookie を置き換えることができます。

そのため、Salesforce、SharePoint Online、AWS などのクラウドアプリにアクセスしようとすると、URL の末尾に、、またはが付いていることがわかり `.cas.ms` `.mcas.ms` `.mcas-gov.us` ます。 たとえば、XYZ アプリを使用する場合、からへの変更を確認するために使用されている URL `XYZ.com` `XYZ.com.cas.ms` です。

URL が置換パターンのいずれかと完全に一致しない場合 (たとえば、 `<app_site>.com` がに置き換えられない場合 `<app_site>.com.cas.ms` )、または追加の懸念事項がある場合は、IT 部門に問い合わせてください。
