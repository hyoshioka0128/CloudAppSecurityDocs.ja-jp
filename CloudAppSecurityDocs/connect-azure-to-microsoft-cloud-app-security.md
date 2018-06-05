---
title: Azure を Cloud App Security に接続して使用状況を表示および管理する | Microsoft Docs
description: このトピックでは、API コネクタを使用して Cloud App Security に Azure を接続する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/23/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3a677bc7-c8b7-4c6a-aada-82c8b3778352
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 03adc7e16df6985060814a66fccd7b881df53f60
ms.sourcegitcommit: af8fad9709171b200699ca1ed513e2831826ed7e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34568528"
---
*適用対象: Microsoft Cloud App Security*


# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Azure を Microsoft Cloud App Security に接続する

このセクションでは、App Connector API を使用して Microsoft Cloud App Security を既存の Azure アカウントに接続する方法を説明します。  
  
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


## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  