---
title: Azure のセキュリティ構成に関する推奨事項を取得する-Cloud App Security |Microsoft Docs
description: この記事では、Azure Security Center を統合することによって Cloud App Security で セキュリティ構成の推奨事項を取得する方法について説明します。
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 8/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: eba84847208b3dc020e9efec47a4215439751a60
ms.sourcegitcommit: 3fe4489cbb2c7d7e8f26aa358511e9f738596e98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2019
ms.locfileid: "69013222"
---
# <a name="security-configuration-for-azure"></a>Azure のセキュリティ構成

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security では、ご利用の Azure 環境におけるセキュリティ構成の評価を提供します。 Azure Security Center で提供される評価には、不足している構成とセキュリティ制御に対する推奨事項が示されます。

## <a name="enable-security-configuration-recommendations"></a>セキュリティ構成の推奨事項を有効にする

この機能を使用するには、Azure AD および Azure Portal で適切なアクセス許可が必要です。 既定では、Azure AD のグローバル管理者ロールは Azure サブスクリプションへのアクセス権を付与できません。 アクセス許可を管理者特権にして、Azure サブスクリプションへのアクセスを自分とその他のユーザーに許可します。

> [!IMPORTANT]
> 次のプロセスを完了した後は、アクセス許可の昇格を無効にすることをお勧めします。

Microsoft Cloud App Security でセキュリティ構成の推奨事項を有効にするには、次の操作を行います。

1. <a href="https://docs.microsoft.com/azure/security-center/security-center-management-groups" target="_blank">Azure Security Center に対するテナント全体の可視性を確保します</a>。 このプロセスには以下が含まれます。
   - 自分とこのページへのアクセスを許可するその他すべての Microsoft Cloud App Security 管理者に、すべてのサブスクリプションに対する閲覧者のロールを付与します。
   - Azure Security Center でルート管理グループのロールを割り当てます。
   - Azure AD のグローバル管理者を管理者特権にして、Azure サブスクリプションへのアクセスを許可します。
   - この記事では、セキュリティ管理者になるためのプロセスについて説明します。 この統合を機能させるために必要な最小のアクセス許可は、**閲覧者**です。

2. 変更を有効にするには、必ず <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">Azure Security Center</a> を開く必要があります。

3. Cloud App Security で、[**セキュリティ構成**の**調査** > ] を参照し、 **[Azure]** タブを選択します。
    - Microsoft Cloud App Security が提供するのは、上位 50 個のサブスクリプションに向けた推奨事項のみです。
    - 変更が有効になるまでに、最大 15 分かかる場合があります。

     ![セキュリティ構成メニュー](media/security-configuration-menu.png)

4. 種類、リソース、サブスクリプションによって推奨事項をフィルター処理することができます。 さらに、Azure Security Center でセキュリティ構成のアイコン ![ASC アイコン](./media/asc-icon.png) をクリックし、推奨事項を開くことができます。ここでは、推奨事項の詳細な情報を調べることができます。

セキュリティに関する推奨事項を実装する方法については、「[Azure セキュリティ センターでのセキュリティに関する推奨事項の管理](https://docs.microsoft.com/azure/security-center/security-center-recommendations)」をご覧ください。

   ![セキュリティ構成](media/security-configuration-azure.png)

## <a name="next-steps"></a>次の手順

[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)