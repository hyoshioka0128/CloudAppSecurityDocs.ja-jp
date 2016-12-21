---
title: "Cloud Discovery のスナップショット レポートを作成する | Microsoft Docs"
description: "この記事では、ログを手動でアップロードして Cloud Discovery アプリのスナップショット レポートを作成する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/14/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a2d4396a3960bd3124196b9c616f6a7765247ce
ms.openlocfilehash: ce887ed4f8727b0c36f5e5e9a40b13b11dc78920


---

# <a name="create-snapshot-cloud-discovery-reports"></a>Cloud Discovery のスナップショット レポートを作成する
自動ログ コレクターを使用する前に、手動でログをアップロードし、Cloud App Security でログ解析することが重要です。
まだログを取得していなく、ログがどのようなものかをサンプルで確認したい場合は、以下の手順に従ってサンプル ログ ファイルをダウンロードし、ログがどのように表示されるかを確認してください。


スナップショット レポートを作成するには:
  
1.  組織のユーザーがインターネット アクセスに使用するファイアウォールとプロキシからログ ファイルを収集します。 組織内のすべてのユーザー アクティビティを示す、トラフィック ピーク時のログを収集するようにしてください。  
  
2.  Cloud App Security ポータルで [**探索**] をクリックし、[**新しいスナップショット レポートの作成**] をクリックします。  
  
   ![新しいスナップショット レポートを作成する](./media/create-new-snapshot-report.png)
     
3.  [**レポート名**] と [**説明**] を入力します。
  
     ![新しいスナップショット レポート](./media/new-snapshot-report.png) 

4.  ログ ファイルのアップロード元にする [**データソース**] を選択します。  
  
5. ダウンロードできるサンプルに従ってログが正しく書式設定されているかどうかを確認します。 [**View and verify**] (表示して確認) をクリックし、[**Download sample log**] (サンプル ログのダウンロード) をクリックします。 自分のログとサンプルを比較し、互換性があることを確認します。 

 ![ログの書式を確認する](./media/cloud-discovery-snapshot-verify.png)  

5.  アップロードする**トラフィック ログを選択**します。 一度に最大 20 個のファイルをアップロードできます。 圧縮された ZIP 形式のファイルもサポートされます。  
  
6.  [**作成**] をクリックします。  

7.  アップロードが完了すると、ログが正常にアップロードされたことを通知するステータス メッセージが画面右上隅に表示されます。  
  
8.  ログ ファイルのアップロード後、ファイルの解析および分析には多少時間がかかります。  
ログ ファイルの処理が完了した後、終了したことを通知する電子メールを受け取ります。 
  
9. ポータル上部のステータス バーに、ログ ファイルの処理状態を知らせる通知バナーが表示されます。  
![ログ ファイル メニュー バーの処理](./media/processing-log-file-menu-bar.png) 
   
10. ログが正常にアップロードされると、ログ ファイルの処理が正常に完了したことを知らせる通知が表示されます。 この時点で、ステータス バーのリンクをクリックするか、設定歯車アイコンの [**Cloud Discovery の設定**] を選択することで、レポートを表示できます。   
  
     ![Discovery の [設定] タブ](./media/discovery-settings-tab.png)
11. [**スナップショット レポートの管理**] を選択し、スナップショット レポートを選択します。
 
![スナップショット レポートの管理](./media/snapshot-report-managment.png)

  
      
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
    
      
  


<!--HONumber=Dec16_HO2-->


