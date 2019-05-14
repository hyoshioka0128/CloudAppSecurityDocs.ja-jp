---
title: Azure を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に Azure を接続する方法に関する情報を提供します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3a677bc7-c8b7-4c6a-aada-82c8b3778352
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1233afd9fe455150f228e060fa3610f675ee9dd2
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65567586"
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Azure を Microsoft Cloud App Security に接続する

*適用対象:Microsoft Cloud App Security*

この記事では、App Connector API を使用して Microsoft Cloud App Security を既存の Azure アカウントに接続する方法を説明します。 この接続により、Azure の使用状況を視覚化して制御できるようになります。 
  
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
  
  
