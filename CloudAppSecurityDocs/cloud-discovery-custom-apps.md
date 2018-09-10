---
title: Cloud App Security で Cloud Discovery にカスタム アプリを追加する | Microsoft Docs
description: このトピックでは、シャドウ IT を監視するために Cloud App Security で Cloud Discovery にカスタム アプリを追加する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 98b0d841-b33d-4ae9-b48b-d9ee77785eaa
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e1fc6388107a33bf42aada57e17153a3d7b8437e
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44142478"
---
*適用対象: Microsoft Cloud App Security*

# <a name="add-custom-apps-to-cloud-discovery"></a>Cloud Discovery にカスタム アプリを追加する
    
Cloud Discovery では、16,000 以上のクラウド アプリを掲載した Microsoft Cloud App Security のクラウド アプリ カタログに照らしてトラフィック ログが分析されます。 このカタログには、公開されているクラウド アプリのみが含まれています。それらのアプリに対して、Cloud App Security で可視性とリスク情報が提供されます。

Cloud App Security では、クラウド アプリ カタログから除外されたクラウド アプリを把握するために、組織専用に開発されたか割り当てられたカスタム クラウド アプリ (LOB アプリ) の使用を検出できます。

新しいカスタム クラウド アプリを追加すると、アップロードされたファイアウォールおよびプロキシ トラフィックのログ メッセージが Cloud App Security によってアプリと対応付けられ、組織全体でのこのアプリの使用状況が、Cloud Discovery ページで可視化されます (たとえば、アプリを使用しているユーザーの数、アプリを使用している一意のソース IP アドレスの数、アプリの送受信トラフィックの量など)。 

新しいカスタム クラウド アプリを追加するには:

1. Cloud App Security ポータルで、**[検出]**、**[Cloud Discovery dashboard]\(Cloud Discovery ダッシュボード\)** の順にクリックします。 
  
   ![Cloud Discovery ダッシュボード メニュー](./media/cloud-discovery-dashboard-menu.png)

2. 右上隅にある 3 つの点をクリックし、**[カスタム アプリの新規追加]** を選択します。 

   ![カスタム アプリの新規追加メニュー](./media/add-custom-app-menu.png)

3. 新しいアプリ レコードを定義するフィールドに入力します。定義したレコードは、ファイアウォール ログ内で検出された後にクラウド アプリ カタログと Cloud Discovery に一覧表示されます。

   ![カスタム アプリ](./media/add-custom-app.png)

4. **[ドメイン]** には、カスタム アプリにアクセスするときに使用する一意のドメインを入力します。 入力したドメインは、トラフィック ログ メッセージをこのアプリに対応付けるために使用されます。 使用しているデータ ソースにアプリの URL 情報が含まれていない場合は、**IPv4** と **IPv6** のアドレス フィールドに必ず入力します。
5. このレコードに対する変更を追跡できるように、メモを追加することをお勧めします。

作成したアプリは、クラウド アプリ カタログに表示されます。

行の末尾にある 3 つの点をクリックして、カスタム アプリをいつでも編集または削除できます。

>[!NOTE]
> - 追加したカスタム アプリには、"**カスタム アプリ**" タグが自動的にタグ付けされます。 このアプリ タグを削除することはできません。
すべてのカスタム アプリを表示するには、**[アプリ タグ]** フィルターを "カスタム アプリ" に等しくなるように設定します。 
> - カスタム アプリのリスク スコアは、既定では 10 ですが、**[アプリ スコアのオーバーライド]** を使用していつでも変更できます。

  
## <a name="see-also"></a>参照  
[ユーザー アクティビティ ポリシー](user-activity-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  