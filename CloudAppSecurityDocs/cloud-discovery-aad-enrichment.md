---
title: Azure AD ユーザー名を利用し、Cloud App Security Discovery データを強化する
description: この記事では、Azure AD ユーザー名を使用して、Cloud App Security Discovery データを強化する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c288b153976f50851a72a54393c099b011521c33
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720155"
---
# <a name="cloud-discovery-enrichment"></a>Cloud Discovery を強化する

*適用対象: Microsoft Cloud App Security*

Cloud Discovery のデータを、Azure Active Directory のユーザー名データを使用して強化できるようになりました。 この機能を有効にすると、検出トラフィック ログで受け取ったユーザー名が Azure AD のユーザー名と照合され、置き換えられます。 Cloud Discovery の強化により、次の機能が有効になります。

- Azure Active Directory のユーザーによるシャドウ IT の使用を調査できます。
- 検出されたクラウド アプリの使用と API で収集されたアクティビティを関連付けることができます。
- Azure AD ユーザー グループに基づくカスタム ログを作成できるようになります。 たとえば、特定のマーケティング部門のシャドウ IT レポートなどです。

## <a name="prerequisites"></a>必要条件

- ユーザー名情報がデータ ソースから提供されること
- Office 365 アプリ コネクタに接続されていること

## <a name="enabling-user-data-enrichment"></a>ユーザー データの強化を有効にすること

1. 「設定」 (歯車アイコン) の **[Cloud Discovery 設定]** を選択します。

2. **[ユーザー エンリッチメント]** タブで、 **[Enrich discovered user identifiers with Azure Active Directory usernames]\(検出されたユーザー ID を Azure Active Directory のユーザー名で強化する\)** を選択します。 このオプションにより、Cloud App Security で Azure Active Directory データを使用して、既定のユーザー名を強化できます。

3. **[Save]** (保存) をクリックします。

![Azure AD ユーザー名を利用し、Cloud App Security Discovery を強化する](media/discovery-enrichment.png)

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
