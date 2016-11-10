---
title: "Cloud Discovery のスナップショット レポートを作成する | Microsoft Docs"
description: "この記事では、ログを手動でアップロードして Cloud Discovery アプリのスナップショット レポートを作成する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 669d1c1942e8c7e930cd2421e9b56821eff04d12


---

# <a name="create-snapshot-cloud-discovery-reports"></a>Cloud Discovery のスナップショット レポートを作成する
自動ログ コレクターを使用する前に、手動でログをアップロードし、Cloud App Security でログ解析することが重要です。

スナップショット レポートを作成するには:
  
1.  組織のユーザーがインターネット アクセスに使用するファイアウォールとプロキシからログ ファイルを収集します。 組織内のすべてのユーザー アクティビティを示す、トラフィック ピーク時のログを収集するようにしてください。  
  
2.  Cloud App Security ポータルで [**探索**] をクリックし、[**新しいスナップショット レポートの作成**] をクリックします。  
  
     ![新しいスナップショット レポートを作成する](./media/create-new-snapshot-report.png)
     
      
3.  [**レポート名**] と [**説明**] を入力します。
  
4.  ログ ファイルのアップロード元にする [**データソース**] を選択します。  
  
5.  アップロードする**トラフィック ログを選択**します。 一度に最大 20 個のファイルをアップロードできます。  
  
6.  [**作成**] をクリックします。  
  
     ![新しいスナップショット レポート](./media/new-snapshot-report.png) 
  
7.  アップロードが完了すると、ログが正常にアップロードされたことを通知するステータス メッセージが画面右上隅に表示されます。  
  
8.  ログ ファイルのアップロード後、ファイルの解析および分析には多少時間がかかります。  
ログ ファイルの処理が完了した後、終了したことを通知する電子メールを受け取ります。 
  
9. ポータル上部のステータス バーに、ログ ファイルの処理状態を知らせる通知バナーが表示されます。  
  
![ログ ファイル メニュー バーの処理](./media/processing-log-file-menu-bar.png) 
  
     After the logs are uploaded successfully, you should see a notification letting you know that the log file processing completed successfully.  
   
10. この時点で、ステータス バーのリンクをクリックするか、設定歯車アイコンの [**Cloud Discovery の設定**] を選択することで、レポートを表示できます。   
  
     ![Discovery の [設定] タブ](./media/discovery-settings-tab.png)
11. [**スナップショット レポートの管理**] を選択し、スナップショット レポートを選択します。
 
![スナップショット レポートの管理](./media/snapshot-report-managment.png)
      
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
    
      
  


<!--HONumber=Oct16_HO4-->


