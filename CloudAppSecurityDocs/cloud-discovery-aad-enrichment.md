---
title: "Azure AD ユーザー名を使用して Cloud App Security Discovery データを強化する | Microsoft Docs"
description: "この記事では、Azure AD ユーザー名を使用して、Cloud App Security Discovery データを強化する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/19/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 45295c2c-3e4d-4482-bf95-2e47072f9236
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 909fa75c48fb9c698d083f2fb85f5f53bfadf76c
ms.sourcegitcommit: 2f4474084c7e07ac4853945ab5aa1ea78950675d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2017
---
# <a name="cloud-discovery-enrichment"></a>Cloud Discovery を強化する

Cloud Discovery のデータを、Azure Active Directory のユーザー名データを使用して強化できるようになりました。 この機能を有効にすると、検出トラフィック ログで受け取ったユーザー名が Azure AD のユーザー名と照合され、置き換えられることで、次の新機能が有効になります。
-   Azure Active Directory のユーザーによるシャドウ IT の使用を調査できます。
-   検出されたクラウド アプリの使用と API で収集されたアクティビティを関連付けることができます。
-   Azure AD ユーザー グループに基づくカスタム ログを作成できるようになります。 たとえば、特定のマーケティング部門のシャドウ IT レポートなどです。


## <a name="prerequisites"></a>前提条件:
- ユーザー名情報がデータ ソースから提供されること
- Office 365 アプリ コネクタに接続されていること

## <a name="enabling-user-data-enrichment"></a>ユーザー データの強化を有効にすること 
    
1. 「設定」 (歯車アイコン) の **[Cloud Discovery 設定]** を選択します。
     
2. **[ユーザー エンリッチメント]** タブで、Cloud App Security を有効にして Azure Active Directory データを使用し、既定でユーザー名を強化するために、**[検出されたユーザー識別子を Azure Active Directory ユーザー名で強化します]** を選択します。

3. **[Save]**(保存) をクリックします。
 
![Azure AD ユーザー名を利用し、Cloud App Security Discovery を強化する](./media/discovery-enrichment.png)
  

  
      
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
    
      
  