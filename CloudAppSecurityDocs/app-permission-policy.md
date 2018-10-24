---
title: Cloud App Security でアプリのアクセス許可を制御するポリシーの作成 | Microsoft Docs
description: このトピックでは、Microsoft Cloud App Security でアプリのアクセス許可ポリシーを作成し、操作するための手順について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 303e821f95aeeb3fafb0f8b41fe7970ed54f0077
ms.sourcegitcommit: 82052a88acbc33893f7b9e0d10cc2e8c652ef003
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349435"
---
*適用対象: Microsoft Cloud App Security*


# <a name="app-permission-policies"></a>アプリのアクセス許可ポリシー

ご利用の環境に接続されている [OAuth アプリの既存の調査](manage-app-permissions.md)に加え、OAuth アプリが特定の条件を満たした場合に自動通知を受け取るようにアクセス許可ポリシーを設定することができます。 たとえば、高いアクセス許可レベルが必要であり、50 人を超えるユーザーによって承認されているアプリがある場合、自動的にアラートを表示させることができます。 

アプリのアクセス許可ポリシーでは、Office 365、G Suite および Salesforce について、各アプリで要求されたアクセス許可とそれを承認したユーザーを調査することができます。 これらのアクセス許可は、承認されているものまたは禁止されているものとしてマークすることもできます。 禁止されているものとしてマークすると、アプリを承認した各ユーザーのそれぞれのアプリのアクセス許可が取り消されます。 

## <a name="create-a-new-app-permission-policy"></a>新しいアプリのアクセス許可ポリシーを作成する
新しいアプリのアクセス許可ポリシーを作成するには、2 つの方法があります。 1 番目の方法は **[調査]** の下で行われ、2 番目の方法は **[コントロール]** の下で行われます。 

新しいアプリのアクセス許可ポリシーを作成するには、次のようにします。

1. **[調査]** で、**[アプリのアクセス許可]** を選択します。
2. 必要に応じてアプリをフィルター処理します。たとえば、**メールボックスの予定表を変更**するための**アクセス許可**を要求するすべてのアプリを表示することができます。
3. **[検索に基づく新しいポリシー]** ボタンをクリックします。 
    ![検索に基づく新しいポリシー](./media/app-permissions-filter.png)
4. **[コミュニティの利用状況]** フィルターを使用して、アプリに対するアクセス許可が一般的であるか、一般的でないか、あるいはまれであるかに関する情報を取得することができます。 このフィルターは、珍しいアプリで、重大度レベルが高いアクセス許可か、多くのユーザーからのアクセス許可を要求する場合に便利です。 

また、**[コントロール]**、**[ポリシー]** の順にクリックして、ポリシーを作成することもできます。 その後、**[ポリシーの作成]**、**[App permission policy]\(アプリのアクセス許可ポリシー\)** の順にクリックします。

  
   ![新しいアプリのアクセス許可ポリシー](./media/app-permissions-policy.png)



  ## <a name="next-steps"></a>次の手順 
  [データ保護ポリシー](data-protection-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  