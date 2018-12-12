---
title: Azure AD ユーザー名を使用して Cloud App Security Discovery データを強化する | Microsoft Docs
description: この記事では、Azure AD ユーザー名を使用して、Cloud App Security Discovery データを強化する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 45295c2c-3e4d-4482-bf95-2e47072f9236
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: d57d1eccdc1d835fb828388b422ce12b211172df
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53123909"
---
# <a name="cloud-discovery-enrichment"></a>Cloud Discovery を強化する

*適用対象: Microsoft Cloud App Security*

Cloud Discovery のデータを、Azure Active Directory のユーザー名データを使用して強化できるようになりました。 この機能を有効にすると、検出トラフィック ログで受け取ったユーザー名が Azure AD のユーザー名と照合され、置き換えられます。 Cloud Discovery の強化により、次の機能が有効になります。
- Azure Active Directory のユーザーによるシャドウ IT の使用を調査できます。
- 検出されたクラウド アプリの使用と API で収集されたアクティビティを関連付けることができます。
- Azure AD ユーザー グループに基づくカスタム ログを作成できるようになります。 たとえば、特定のマーケティング部門のシャドウ IT レポートなどです。


## <a name="prerequisites"></a>前提条件:
- ユーザー名情報がデータ ソースから提供されること
- Office 365 アプリ コネクタに接続されていること

## <a name="enabling-user-data-enrichment"></a>ユーザー データの強化を有効にすること 
    
1. 「設定」 (歯車アイコン) の **[Cloud Discovery 設定]** を選択します。
     
2. **[ユーザー エンリッチメント]** タブで、**[Enrich discovered user identifiers with Azure Active Directory usernames]\(検出されたユーザー ID を Azure Active Directory のユーザー名で強化する\)** を選択します。 このオプションにより、Cloud App Security で Azure Active Directory データを使用して、既定のユーザー名を強化できます。

3. **[Save]**(保存) をクリックします。
 
![Azure AD ユーザー名を利用し、Cloud App Security Discovery を強化する](./media/discovery-enrichment.png)
  

  
      
## <a name="next-steps"></a>次の手順
  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
    
      
  