---
title: "Azure を Cloud App Security に接続して使用状況を表示および管理する | Microsoft Docs"
description: "このトピックでは、API コネクタを使用して Cloud App Security に Azure を接続する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 9/3/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 3a677bc7-c8b7-4c6a-aada-82c8b3778352
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7e2b6d0f02d49eaa4354f5344d0555fc3f503fb8
ms.sourcegitcommit: 5688d3916a54deada225f7a83c34a7c501953960
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2017
---
# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Azure を Microsoft Cloud App Security に接続する

このセクションでは、App Connector API を使用して Cloud App Security を既存の Azure アカウントに接続する手順を説明します。  
  
## <a name="setting-up-azure-for-connection-to-cloud-app-security"></a>Cloud App Security に接続するために Azure を設定する

Event Hubs を使用して Cloud App Security を Azure に接続します。 このセクションでは、お使いのサブスクリプションですべてのアクティビティ ログを 1 つのイベント ハブにストリーミングする手順を説明します。 

### <a name="step-1-stream-your-azure-activity-logs-to-event-hubs"></a>手順 1: Event Hubs への Azure アクティビティ ログのストリーミング

1.  Azure サブスクリプションの Azure アクティビティ ログをイベント ハブにストリーミングします。 https://docs.microsoft.com/en-us/azure/monitoring-and-diagnostics/monitoring-stream-activity-logs-event-hubs にある Azure ドキュメントの公式ガイドに従います。

 > [!NOTE]
 > Azure サブスクリプションを複数お持ちの場合は、各サブスクリプションでこの手順を繰り返しますが、イベント ハブは 1 つだけを使用し、全サブスクリプションで共有するようにします。

 この手順を完了すると、新しいイベント ハブが選択した名前空間に作成されます。
 
 > [!NOTE]
 > アクティビティ ログのエクスポートを試みた後でエラーが発生する場合は、Azure で **[リソース プロバイダー]** ブレードに移動し、"microsoft.insights" が登録されていることを確認します。

### <a name="step-2-get-a-connection-string-to-your-event-hub"></a>手順 2: イベント ハブへの接続文字列の取得

1.  **[Event Hubs - プレビュー]** ブレードに移動します。
  
   ![[Event Hubs] ブレード](media/azure-event-hubs.png "Azure Event Hubs")

2.  イベント ハブの名前空間を選択します。
  
    ![イベント ハブの名前空間](media/azure-namespace.png "Azure 名前空間")

3.  メニューの**[エンティティ]** から、**[イベント ハブ]** をクリックします。 
  
    ![イベント ハブ エンティティ](media/azure-event-hubs-entities.png "Azure イベント ハブ エンティティ")

4.  Azure Monitor によって作成された新しいイベント ハブを選択します。 **insights-operational-logs** という名前です。
  > [!NOTE]
  > Event Hub が作成されるまで数分かかることがあります。

   ![Insights operational logs](media/azure-insight-operational-logs.png "Azure insight operational logs")
  
  
5. **[共有アクセス ポリシー]**、**[追加]** の順にクリックして新しいアクセス ポリシーを作成します。このポリシーで Cloud App Security にイベント ハブからの読み取りのアクセス許可を与えます。
  
    ![共有アクセス ポリシー](media/azure-shared-access-policies.png "Azure 共有アクセス ポリシー")

6.  新しいポリシーの名前を入力し、少なくとも **[リッスン] 要求**が含まれていることを確認します。 完了したら、**[作成]** をクリックします。
  
    ![Azure の新しいポリシー](media/azure-new-policy.png "Azure の新しいポリシーの作成")

7.  **[設定]** から、**[共有アクセス ポリシー]**、先ほど作成したアクセス ポリシーの順にクリックします。   
  
    ![Azure のポリシーの選択](media/azure-select-policy.png "Azure のポリシーの選択")

8. [ポリシー] ウィンドウで、**[接続文字列 – プライマリ キー]** または **[接続文字列 - セカンダリ キー]** の隣のボタンをクリックし、いずれかの接続文字列をコピーします。

### <a name="step-3-add-azure-to-cloud-app-security"></a>手順 3: Cloud App Security への Azure の追加
 
1.  Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
3.  **[アプリ コネクタ]** ページで、[+] ボタンをクリックして **[Microsoft Azure]** を選択します。  
  
     ![Azure を Cloud App Security に接続する](media/azure-connect-app.png "Azure の接続")  
  
4.  **[接続文字列]** フィールドに、前の手順でコピーした接続文字列を貼り付けます。  
  
5.  **[コンシューマー グループ]** フィールドに「`$Default`」と入力します。
    
   >[!NOTE] 
   > 使うコンシューマー グループを別に作成した場合は、その**コンシューマー グループ**名を使います。
  
6.  **[接続]**をクリックします。
     これにより、接続のテストが行われます。これには数分かかる場合があります。 成功通知を受信したら、 [**閉じる**] をクリックします。  


> [!NOTE]
> この機能はパブリック プレビュー段階です。


## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  