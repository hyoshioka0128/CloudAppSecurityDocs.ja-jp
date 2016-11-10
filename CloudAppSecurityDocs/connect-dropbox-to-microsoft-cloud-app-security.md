---
title: "Dropbox を Microsoft Cloud App Security に接続する | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に Dropbox アプリを接続する方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4acd93f4-b885-4e1f-a385-43b5db02a3ee
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 105003dfbd8afbb10cdb2058e2da180d4b49e294


---

# <a name="connect-dropbox-to-microsoft-cloud-app-security"></a>Dropbox を Microsoft Cloud App Security に接続する
このセクションでは、コネクタ API を使用して Cloud App Security を既存の Dropbox アカウントに接続する方法を説明します。  
 
 
Dropbox ではサインインしなくても共有リンクからファイルにアクセスできるため、Cloud App Security はこのようなユーザーを非認証ユーザーとして登録します。 Dropbox の非認証ユーザーが表示された場合、組織外のユーザーであることを示しているか、あるいは組織内のサインインしていないユーザーと認識される可能性があります。

## <a name="how-to-connect-dropbox-to-cloud-app-security"></a>Dropbox を Cloud App Security に接続する方法  
  
1.  Cloud App Security コンソールで **[調査]**、**[承認されたアプリ]** の順にクリックします。  
  
2.  [Dropbox] 行で、[**アプリ コネクタの状態**] 列の [**接続**] をクリックするか、または [**アプリを接続**] ボタンをクリックしてから [**Dropbox**] をクリックします。  
  
     ![Dropbox を接続する](./media/connect-dropbox.png "connect dropbox")  
  
3.  Dropbox の設定ページの [API] タブで、管理者アカウントの電子メール アドレスを入力します。  
  
4.  [**リンクを生成**] をクリックします。  
  
5.  [**リンクに移動**] をクリックします。  
  
     Dropbox のログオン ページが開きます。 Cloud App Security がチームの Dropbox インスタンスにアクセスできるように、資格情報を入力します。  
  
6.  Cloud App Security からチームの情報やアクティビティ ログにアクセスし、任意のチーム メンバーと同様に任意のアクティビティを実行することを許可するかどうかを確認するメッセージが Dropbox で表示されます。 続行するには、[**許可**] をクリックします。  
  
7.  Cloud App Security コンソールに戻ると、Dropbox が正常に接続されたことを通知するメッセージが届いています。  
  
8.  [**API のテスト**] をクリックして、正常に接続されたことを確認します。  
  
     テストには数分かかる場合があります。 成功通知を受信したら、 [**閉じる**] をクリックします。  
  
Dropbox を接続すると、接続までの 60 日間のイベントを受け取ります。

> [!NOTE] 
> ファイルを追加する Dropbox のすべてのイベントは、Cloud App Security に接続された他のすべてのアプリに合わせるためにアップロード ファイルとして Cloud App Security に表示されます。 
 
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Oct16_HO4-->


