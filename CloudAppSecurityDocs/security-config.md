---
title: Cloud App Security でセキュリティ構成の推奨事項を取得する |Microsoft Docs
description: この記事では、Azure Security Center を統合することによって Cloud App Security で セキュリティ構成の推奨事項を取得する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/1/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c6d8f8af-867b-43ab-adee-f06520577fe7
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 95611b155930836b50d6ac0b7bc395555e12451a
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143668"
---
*適用対象: Microsoft Cloud App Security*


# <a name="security-configuration"></a>セキュリティ構成

Microsoft Cloud App Security では、お客様の Azure 環境のセキュリティ構成に対して評価を与え、不足している構成やセキュリティ制御に関して Azure Security Center を使用した推奨事項を提供しています。 

この機能を使用するには、Azure AD および Azure Portal で適切なアクセス許可が必要です。
 
既定では、Azure AD のグローバル管理者ロールは Azure サブスクリプションへのアクセス権を付与できません。 このため、自分や他のユーザーに Azure サブスクリプションへのアクセス権を付与できるように、自身のアクセス許可を昇格させる必要があります。 

> [!NOTE]
> 次のプロセスを完了した後は、アクセス許可の昇格を無効にすることをお勧めします。

Microsoft Cloud App Security でセキュリティ構成の推奨事項を有効にするには、次の操作を行います。

1. <a href="https://docs.microsoft.com/azure/security-center/security-center-management-groups" target="_blank">Azure Security Center に対するテナント全体の可視性を確保します</a>。 このプロセスには、自分自身とこのページへのアクセス権を付与する他のすべての Microsoft Cloud App Security 管理者に対する、すべてのサブスクリプションの閲覧者ロールの付与、Azure Security Center のルート管理グループに対するロールの割り当て、Azure サブスクリプションへのアクセス権の付与を可能にするための Azure AD グローバル管理者の昇格が含まれます。 

   > [!NOTE]
   > この記事では、セキュリティ管理者になるためのプロセスについて説明します。 この統合を機能させるために必要な最小のアクセス許可は、閲覧者です。

2. 変更を有効にするには、必ず <a href="https://ms.portal.azure.com/#blade/Microsoft_Azure_Security/SecurityMenuBlade/0" target="_blank">Azure Security Center</a> を開く必要があります。

3. Microsoft Cloud App Security ポータルで、**[調査]** に移動し、**[セキュリティの構成]** を実行します。 

   ![セキュリティ構成メニュー](./media/security-configuration-menu.png)

   > [!NOTE]
   > Microsoft Cloud App Security が提供するのは、上位 50 個のサブスクリプションに向けた推奨事項のみです。
   > 変更が有効になるまでに、最大 15 分かかる場合があります。

5. 種類、リソース、サブスクリプションによって推奨事項をフィルター処理することができます。 さらに、Azure Security Center でセキュリティ構成のアイコン ![ASC アイコン](./media/asc-icon.png) をクリックし、推奨事項を開くことができます。ここでは、推奨事項の詳細な情報を調べることができます。 <br></br><br></br>セキュリティに関する推奨事項を実装する方法については、「[Azure セキュリティ センターでのセキュリティに関する推奨事項の管理](https://docs.microsoft.com/azure/security-center/security-center-recommendations)」をご覧ください。

 
   ![セキュリティ構成](./media/security-configuration1.png)

 

## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
