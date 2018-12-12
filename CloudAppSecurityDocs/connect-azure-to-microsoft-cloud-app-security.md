---
title: Azure を Cloud App Security に接続して使用状況を表示および管理する | Microsoft Docs
description: この記事では、API コネクタを使用して Cloud App Security に Azure を接続する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3a677bc7-c8b7-4c6a-aada-82c8b3778352
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b07cf027b024d1b3cc3af0f82d54866ecd82574e
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53123654"
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Azure を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、App Connector API を使用して Microsoft Cloud App Security を既存の Azure アカウントに接続する方法を説明します。  
  
## <a name="how-to-connect-azure-to-cloud-app-security"></a>Azure を Cloud App Security に接続する方法  
  
> [!NOTE]
> - Azure を Microsoft Cloud App Security に接続するには、Azure AD のグローバル管理者である必要があります。 
> - Cloud App Security には**すべての**サブスクリプションのアクティビティが表示されます。
>-  現時点では、Cloud App Security は ARM アクティビティのみを監視します。 
 
1.  **[接続アプリ]** ページで、[+] ボタン、**[Microsoft Azure]** の順にクリックします。  
  
     ![Azure の接続](./media/connect-azure-menu.png) 

2.  Azure のポップアップで、**[Connect Microsoft Azure]\(Microsoft Azure に接続\)** をクリックします。

      ![Azure の接続](./media/connect-azure.png) 
 
> [!NOTE] 
> Azure を接続すると、データがプルされます。 以降のデータが表示されます。


## <a name="next-steps"></a>次の手順 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  