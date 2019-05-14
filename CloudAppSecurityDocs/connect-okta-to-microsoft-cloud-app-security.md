---
title: Okta を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に Okta を接続する方法に関する情報を提供します。
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
ms.assetid: 9c3673b9-99bd-400c-9da1-5bf809ea5892
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ca7ee59430227c193f2532f3cffb2fde756dd793
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65567226"
---
# <a name="connect-okta-to-microsoft-cloud-app-security"></a>Okta を Microsoft Cloud App Security に接続する

*適用対象:Microsoft Cloud App Security*

この記事では、コネクタ API を使用して Microsoft Cloud App Security を既存の Okta アカウントに接続する方法を説明します。 この接続により、Okta の使用状況を視覚化して制御できるようになります。
  
  
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
  
