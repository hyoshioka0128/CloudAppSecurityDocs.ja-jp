---
title: トラブルシューティング-cas.ms とは何ですか?
description: この記事では、アプリの条件付きアクセス制御によって使用される cas.ms URL サフィックスに関する情報を提供します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: e08fc2af75d59ac5697593a47e3a002dfb4986f9
ms.sourcegitcommit: 3f6ef6b97a0953470135d115323a00cf11441ab7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2020
ms.locfileid: "78927880"
---
# <a name="troubleshooting---what-is-casms"></a>トラブルシューティング-cas.ms とは何ですか?

*適用対象: Microsoft Cloud App Security*

この記事では、アプリの条件付きアクセス制御によって使用される `cas.ms` の URL サフィックスについて説明します。

## <a name="our-system-flagged-a-new-dns-entry-or-generated-certificate-for-casms-but-we-dont-use-cloud-app-security"></a>`*.cas.ms`用に新しい DNS エントリまたは生成された証明書のフラグがシステムに設定されましたが、は使用しません Cloud App Security

これは、環境を保護する Cloud App Security の通常の動作と結果です。 組織で Cloud App Security を使用していない場合でも、を使用している環境から他のユーザーがサイトまたはサービスにアクセスすると、その Url が書き換えられてアクセスが保護されます。

たとえば、Contoso は Cloud App Security によって提供されるアプリの条件付きアクセス制御を使用して環境を保護します。 Contoso ユーザーが `fabrikam.com`にアクセスすると、ユーザーは自動的に `fabrikam.com.<region>.cas.ms`にリダイレクトされます。 その結果、Fabrikam のフィッシングチームには、`fabrikam.com.<region>.cas.ms`の新しい DNS エントリと証明書が表示されます。

そのため、Fabrikam は実際には Cloud App Security を使用しませんが、DNS エントリまたは証明書が表示されます。

## <a name="heres-why-you-see-casms-in-your-url"></a>URL に `*.cas.ms` が表示される理由を次に示します。

まず、フィッシングていません。 この種類の URL が想定されており、組織がビジネスに不可欠なデータを保護するために追加のセキュリティ制御を適用することを示しています。

これを行うには、組織のクラウド環境を保護するためのソリューションである Cloud App Security を使用します。これにより、使用するクラウドアプリに関連するすべての Url と cookie を置き換えることができます。

そのため、Salesforce、SharePoint Online、AWS などのクラウドアプリにアクセスしようとすると、URL の末尾に `<region>.cas.ms`が付いていることがわかります。 たとえば、XYZ アプリを使用する場合、`XYZ.com` から `XYZ.com.<region>.cas.ms`に変更を表示するために使用されている URL です。

URL が置換パターンと完全に一致しない場合 (`<app_site>.com` が `<app_site>.com.<region>.cas.ms`に置き換えられない場合など)、または追加の懸念事項がある場合は、IT 部門に問い合わせてください。
