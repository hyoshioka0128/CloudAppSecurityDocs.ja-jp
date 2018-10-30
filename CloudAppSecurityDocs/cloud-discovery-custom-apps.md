---
title: Cloud App Security で Cloud Discovery にカスタム アプリを追加する | Microsoft Docs
description: このトピックでは、シャドウ IT を監視するために Cloud App Security で Cloud Discovery にカスタム アプリを追加する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 98b0d841-b33d-4ae9-b48b-d9ee77785eaa
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ed32435d0add14f1db3ef8457e54a628d9b26747
ms.sourcegitcommit: 9c314d566a1dd35e32650928052b8a817dd20d9d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990683"
---
*適用対象: Microsoft Cloud App Security*

# <a name="add-custom-apps-to-cloud-discovery"></a>Cloud Discovery にカスタム アプリを追加する
    
Cloud Discovery では、Microsoft Cloud App Security のクラウド アプリ カタログに照らしてトラフィック ログが分析されます。 クラウド アプリ カタログには、16,000 以上のクラウド アプリが掲載されています。 このカタログには、公開されているクラウド アプリのみが含まれています。それらのアプリに対して、Cloud App Security で可視性とリスク情報が提供されます。

Cloud App Security では、クラウド アプリ カタログから除外されたクラウド アプリを把握するために、組織専用に開発されたか割り当てられたカスタム クラウド アプリ (LOB アプリ) の使用を検出できます。

新しいカスタム クラウド アプリを追加すると、アップロードされたファイアウォールおよびプロキシ トラフィックのログ メッセージが Cloud App Security によってアプリと対応付けられ、組織全体でのこのアプリの使用状況が、Cloud Discovery ページで可視化されます (たとえば、アプリを使用しているユーザーの数、アプリを使用している一意のソース IP アドレスの数、アプリの送受信トラフィックの量など)。 

## <a name="add-a-new-custom-cloud-app"></a>新しいカスタム クラウド アプリを追加する

1. Cloud App Security ポータルで、**[検出]**、**[Cloud Discovery dashboard]\(Cloud Discovery ダッシュボード\)** の順にクリックします。 
  
   ![Cloud Discovery ダッシュボード メニュー](./media/cloud-discovery-dashboard-menu.png)

2. 右上隅にある 3 つの点をクリックし、**[カスタム アプリの新規追加]** を選択します。 

   ![カスタム アプリの新規追加メニュー](./media/add-custom-app-menu.png)

3. 新しいアプリ レコードを定義するフィールドに入力します。定義したレコードは、ファイアウォール ログ内で検出された後にクラウド アプリ カタログと Cloud Discovery に一覧表示されます。

   ![カスタム アプリ](./media/add-custom-app.png)

4. **[ドメイン]** には、カスタム アプリにアクセスするときに使用する一意のドメインを入力します。 入力したドメインは、トラフィック ログ メッセージをこのアプリに対応付けるために使用されます。 使用しているデータ ソースにアプリの URL 情報が含まれていない場合は、**IPv4** と **IPv6** のアドレス フィールドが入力されていることを確認します。
5. **ホスティング プラットフォーム**と **Azure サブスクリプション ID** を追加します。 必要に応じて、アプリの**部署**を指定します。 
6. リスク **スコア**を割り当て、このレコードの変更が追跡できるように、**アプリのメモ**を追加します。
7. **[作成]** をクリックします。

作成したアプリは、クラウド アプリ カタログに表示されます。

行の末尾にある 3 つの点をクリックして、カスタム アプリをいつでも編集または削除できます。

>[!NOTE]
> 追加したカスタム アプリには、"**カスタム アプリ**" タグが自動的にタグ付けされます。 このアプリ タグを削除することはできません。
すべてのカスタム アプリを表示するには、**[アプリ タグ]** フィルターを "カスタム アプリ" に等しくなるように設定します。 
<!-- -  By default, custom apps have a risk score of 10, but you can use the **Override app score** action to change it at any time.-->

  
## <a name="next-steps"></a>次の手順 
[ユーザー アクティビティ ポリシー](user-activity-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  