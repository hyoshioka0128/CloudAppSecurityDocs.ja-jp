---
title: Cloud Discovery クラウド アプリの使用に関するスナップショット レポートの作成 | Microsoft ドキュメント
description: この記事では、ログを手動でアップロードして Cloud Discovery アプリのスナップショット レポートを作成する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: ecc1949d-c861-4636-952a-c3a260719bb5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: c2c9395841277f14d59b83cd0883f8e98cc38a6e
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2018
---
*適用対象: Microsoft Cloud App Security*


# <a name="create-snapshot-cloud-discovery-reports"></a>Cloud Discovery のスナップショット レポートを作成する
自動ログ コレクターを使用する前に、手動でログをアップロードし、Microsoft Cloud App Security でログ解析することが重要です。
まだログを取得していなく、ログがどのようなものかをサンプルで確認したい場合は、以下の手順に従ってサンプル ログ ファイルをダウンロードし、ログがどのように表示されるかを確認してください。


スナップショット レポートを作成するには:
  
1. 組織のユーザーがインターネット アクセスに使用するファイアウォールとプロキシからログ ファイルを収集します。 組織内のすべてのユーザー アクティビティを示す、トラフィック ピーク時のログを収集するようにしてください。  
  
2. Cloud App Security ポータルで **[探索]** をクリックし、**[新しいスナップショット レポートの作成]** をクリックします。  
  
   ![新しいスナップショット レポートを作成する](./media/create-new-snapshot-report.png)
     
3. **[レポート名]** と **[説明]** を入力します。
  
    ![新しいスナップショット レポート](./media/new-snapshot-report.png) 

4. ログ ファイルのアップロード元にする **[データソース]** を選択します。  
  
5. ダウンロードできるサンプルに従ってログが正しく書式設定されているかどうかを確認します。 「**View and verify**」 (表示して確認) をクリックし、「**Download sample log**」 (サンプル ログのダウンロード) をクリックします。 自分のログとサンプルを比較し、互換性があることを確認します。 

   ![ログの書式を確認する](./media/cloud-discovery-snapshot-verify.png)  

   > [!NOTE]
   > FTP サンプル形式はスナップショットと自動アップロードでサポートされています。一方、syslog は自動アップロードでのみサポートされています。<br></br>
   サンプル ログのダウンロードを実行すると、サンプル FTP ログがダウンロードされます。


6. アップロードする**トラフィック ログを選択**します。 一度に最大 20 個のファイルをアップロードできます。 圧縮された ZIP 形式のファイルもサポートされます。  
  
7. **[作成]** をクリックします。  

8. アップロードが完了すると、ログが正常にアップロードされたことを通知するステータス メッセージが画面右上隅に表示されます。  
  
9. ログ ファイルのアップロード後、ファイルの解析および分析には多少時間がかかります。  
   ログ ファイルの処理が完了した後、終了したことを通知する電子メールを受け取ります。 
  
10. ポータル上部のステータス バーに、ログ ファイルの処理状態を知らせる通知バナーが表示されます。  
    ![ログ ファイル メニュー バーの処理](./media/processing-log-file-menu-bar.png) 
   
11. ログが正常にアップロードされると、ログ ファイルの処理が正常に完了したことを知らせる通知が表示されます。 この時点で、ステータス バーのリンクをクリックするか、設定歯車アイコンの **[Cloud Discovery の設定]** を選択することで、レポートを表示できます。   
  
     ![Discovery の [設定] タブ](./media/discovery-settings-tab.png)
12. **[スナップショット レポート]** を選択し、スナップショット レポートを選択します。
 
![スナップショット レポートの管理](./media/snapshot-report-managment.png)

  
      
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
    
      
  