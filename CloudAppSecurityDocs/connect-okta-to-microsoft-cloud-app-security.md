---
title: Okta を Cloud App Security に接続して使用状況を表示し、管理する | Microsoft Docs
description: この記事では、API コネクタを使用して Cloud App Security に Okta アプリを接続する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9c3673b9-99bd-400c-9da1-5bf809ea5892
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 46e9439ae4157976385db40ee7c89e968cd690c0
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53122773"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Okta を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、コネクタ API を使用して Microsoft Cloud App Security を既存の Okta アカウントに接続する方法を説明します。  
  
## <a name="how-to-connect-okta-to-cloud-app-security"></a>Okta を Cloud App Security に接続する方法  
  
1.  Okta で、Cloud App Security 向けの管理者サービス アカウントを作成することをお勧めします。  
  
     スーパー管理者のアクセス許可を付与されたアカウントを必ず使用してください。  
  
     Okta アカウントが検証済みであることを確認します。  
  
2.  Okta コンソールで **[管理者]** をクリックします。  
  
    -   **[セキュリティ]**、**[API]** の順にクリックします。  
  
         ![Okta API](./media/okta-api.png "Okta API")  
  
    -   **[トークンを作成します]** をクリックします。  
  
         ![Okta のトークンの作成](./media/okta-createtoken.jpg "Okta のトークンの作成")  
  
    -   **[トークンを作成します]** ポップアップで、Cloud App Security トークンに名前を付けてから **[トークンを作成します]** をクリックします。  
  
         ![Okta のトークン ポップアップ](./media/okta-token-popup.png "Okta のトークン ポップアップ")  
  
    -   **[Token created successfully (トークンは正常に作成されました)]** ポップアップで、**[Token value (トークン値)]** をコピーします。  
  
         ![Okta のトークン値](./media/okta-token-value.png "Okta のトークン値")  
  
3.  Cloud App Security コンソールで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
4.  **[アプリ コネクター]** ページで、[+] ボタン、**[Okta]** の順にクリックします。  
  
     ![Okta の接続](./media/connect-okta.png "Okta の接続")  
  
5.  表示されたポップアップの **[ドメイン]** フィールドに Okta ドメインを入力し、トークンを **[トークン]** フィールドに貼り付けます。  
  
6.  **[接続]** をクリックして、Okta のトークンを Cloud App Security で作成します。  
  
7.  **[API のテスト]** をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。  
  
Okta を接続すると、接続までの 60 日間のイベントを受け取ります。
  
## <a name="next-steps"></a>次の手順  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
