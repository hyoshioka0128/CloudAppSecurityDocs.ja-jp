---
title: Cloud App Security に WebEx を接続します。
description: この記事では、可視性と制御を使用するより、API コネクタを使用して、WebEx アプリケーションを Cloud App Security に接続する方法についての情報を提供します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 3/22/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c43271fd-9a61-4727-9945-de1c6ea5422c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 09555165697ee66a84c99d4f3a5790f22b4d17d6
ms.sourcegitcommit: fe4cd2174f6dc83811a2d484f079e8dfbac5d082
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476980"
---
# <a name="connect-cisco-webex-to-microsoft-cloud-app-security"></a>Cisco WebEx を Microsoft Cloud App Security に接続します。

*適用対象:Microsoft Cloud App Security*

この記事では、Microsoft Cloud App Security を既存の Api コネクタを使用して Cisco WebEx アカウントに接続するための手順を提供します。 この接続を可視化と WebEx ユーザー、アクティビティ、およびファイルの制御を提供します。 
 
## <a name="prerequisites"></a>前提条件

接続専用のサービス アカウントを作成することをお勧めします。 これにより、ように、このアカウントから実行中として WebEx で実行されたガバナンス アクションが WebEx で送信されるメッセージを削除することを確認することができます。 それ以外の場合、Cloud App Security を WebEx に接続した管理者の名前は、操作を実行したユーザーとして表示されます。  

## <a name="how-to-connect-webex-to-cloud-app-security"></a>WebEx を Cloud App Security に接続する方法  
  
1.  Cloud App Security コンソールで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
2.  **アプリ コネクタ** ページで、続けて + ボタンをクリックします。 **Cisco WebEx**します。  
  
     ![接続 WebEx](./media/cisco-webex.png "WebEx の接続")  
  
3.  ポップアップで、このコネクタのインスタンス名を入力します。  
  
4.  クリックして**接続 Cisco Webex**します。 WebEx サインイン ページが開きます。 チームの WebEx インスタンスに Cloud App Security へのアクセスを許可するための資格情報を入力します。  
  
6.  WebEx は、チームの情報やアクティビティ ログを Cloud App Security のアクセスを許可し、チーム メンバーと同様のアクティビティを実行するかどうかを確認します。 続行するには、**[許可]** をクリックします。  
  
7.  Cloud App Security コンソールに戻る WebEx が正常に接続されているメッセージが表示されます。  
  
8.  **[API のテスト]** をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 成功通知を受信したら、**[閉じる]** をクリックします。  
  
WebEx を接続すると、接続までの 7 日間のイベントが表示されます。 Cloud App Security では、過去 3 か月間のイベントをスキャンします。 を増やすには、Cisco WebEx pro ライセンスがあるし、を Cloud App Security のサポート チケットを開く必要があります。

 
## <a name="next-steps"></a>次の手順 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  
