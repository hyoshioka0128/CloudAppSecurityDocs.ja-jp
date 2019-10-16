---
title: WebEx を Cloud App Security に接続する
description: この記事では、使用状況を表示および制御するために、API コネクタを使用して Cloud App Security に WebEx アプリを接続する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c43271fd-9a61-4727-9945-de1c6ea5422c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ef2614a2c7c2b328e3cc3510786d05684785fa62
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72335638"
---
# <a name="connect-cisco-webex-to-microsoft-cloud-app-security"></a>Cisco WebEx を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、コネクタ Api を使用して、既存の Cisco WebEx アカウントに Microsoft Cloud App Security を接続する手順について説明します。 この接続により、WebEx のユーザー、アクティビティ、ファイルを可視化し、制御できます。 
 
## <a name="prerequisites"></a>必要条件

- 接続用に専用のサービスアカウントを作成することをお勧めします。 これにより、WebEx で送信されたメッセージの削除など、WebEx で実行されるガバナンスアクションがこのアカウントから実行されていることを確認できます。 それ以外の場合は、WebEx に Cloud App Security 接続した管理者の名前が、アクションを実行したユーザーとして表示されます。  
- WebEx で、完全な管理者**と**コンプライアンス管理者のアクセス許可を持っている必要があります。


## <a name="how-to-connect-webex-to-cloud-app-security"></a>WebEx を Cloud App Security に接続する方法  
  
1.  Cloud App Security コンソールで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。  
  
2.  **[アプリコネクタ]** ページで、プラスボタンをクリックし、続いて**Cisco WebEx**をクリックします。  
  
     ![webex](./media/cisco-webex.png "connect を webex")に接続する  
  
3.  ポップアップで、このコネクタのインスタンス名を入力します。  
  
4.  **[Cisco Webex に接続]** をクリックします。 WebEx サインインページが開きます。 チームの WebEx インスタンスへの Cloud App Security アクセスを許可するための資格情報を入力します。  
  
6.  WebEx は、チームの情報やアクティビティログへの Cloud App Security アクセスを許可し、チームメンバーとしてアクティビティを実行できるようにするかどうかをたずねます。 続行するには、 **[許可]** をクリックします。  
  
7.  Cloud App Security コンソールに戻ると、WebEx が正常に接続されたことを示すメッセージが表示されます。  
  
8.  **[API のテスト]** をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。  
  
WebEx に接続すると、接続する7日間のイベントを受け取ります。 Cloud App Security は過去3か月にわたってイベントをスキャンします。 これを増やすには、Cisco WebEx pro ライセンスを所有し、Cloud App Security サポートでチケットを開く必要があります。

 
## <a name="next-steps"></a>次のステップ 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  
