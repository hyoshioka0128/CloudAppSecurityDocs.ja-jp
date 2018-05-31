---
title: Azure を Cloud App Security に接続して使用状況を表示および管理する | Microsoft Docs
description: このトピックでは、API コネクタを使用して Cloud App Security に Azure を接続する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/27/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3a677bc7-c8b7-4c6a-aada-82c8b3778352
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: f93a78e35c76e9dd76e1264fb11d6046ed2b6d18
ms.sourcegitcommit: 0d73d21f961dc883f01a329bcf16dcaf070dca2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2018
ms.locfileid: "34558942"
---
*適用対象: Microsoft Cloud App Security*


# <a name="connect-azure-to-microsoft-cloud-app-security"></a>Azure を Microsoft Cloud App Security に接続する

このセクションでは、App Connector API を使用して Microsoft Cloud App Security を既存の Azure アカウントに接続する方法を説明します。  
  
## <a name="setting-up-azure-for-connection-to-cloud-app-security"></a>Cloud App Security に接続するために Azure を設定する

Event Hubs を使用して Cloud App Security を Azure に接続します。 このセクションでは、お使いのサブスクリプションですべてのアクティビティ ログを 1 つのイベント ハブにストリーミングする手順を説明します。 

### <a name="step-1-stream-your-azure-activity-logs-to-event-hubs"></a>手順 1: Event Hubs への Azure アクティビティ ログのストリーミング

1. Azure サブスクリプションの Azure アクティビティ ログをイベント ハブにストリーミングします。 https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-stream-activity-logs-event-hubs にある Azure ドキュメントの公式ガイドに従います。

   > [!NOTE]
   > 複数の Azure サブスクリプションをお持ちの場合は、1 つのイベント ハブを全サブスクリプションで共有して使用し、各サブスクリプションでこの手順を繰り返します。

   この手順を完了すると、新しいイベント ハブが選択した名前空間に作成されます。
 
   > [!NOTE]
   > アクティビティ ログのエクスポートを試みた後でエラーが発生する場合は、Azure の左側にあるメニューで **[リソース プロバイダー]** に移動し、"microsoft.insights" が登録されていることを確認します。

### <a name="step-2-get-a-connection-string-to-your-event-hub"></a>手順 2: イベント ハブへの接続文字列の取得

1. 左側のメニューで **[Event Hubs - Preview]\(Event Hubs - プレビュー\)** に移動します。
  
   ![Event Hubs メニュー](media/azure-event-hubs.png "Azure Event Hubs")

2.  Azure のポップアップで、**[Connect Microsoft Azure]\(Microsoft Azure に接続\)** をクリックします。

3. メニューの **[エンティティ]** から、**[イベント ハブ]** をクリックします。 
  
   ![イベント ハブ エンティティ](media/azure-event-hubs-entities.png "Azure イベント ハブ エンティティ")

4. Azure Monitor によって作成された新しいイベント ハブを選択します。 **insights-operational-logs** という名前です。
   > [!NOTE]
   > イベント ハブが作成されるまで数分かかることがあります。

   ![Insights operational logs](media/azure-insight-operational-logs.png "Azure insight operational logs")
  
  
5. **[共有アクセス ポリシー]**、**[追加]** の順にクリックして新しいアクセス ポリシーを作成します。このポリシーで Cloud App Security にイベント ハブからの読み取りのアクセス許可を与えます。
  
    ![共有アクセス ポリシー](media/azure-shared-access-policies.png "Azure 共有アクセス ポリシー")

6. 新しいポリシーの名前を入力し、少なくとも **[リッスン] 要求**が含まれていることを確認します。 完了したら、**[作成]** をクリックします。
  
   ![Azure の新しいポリシー](media/azure-new-policy.png "Azure の新しいポリシー")

7. **[設定]** から、**[共有アクセス ポリシー]**、作成したアクセス ポリシーの順にクリックします。   
  
   ![Azure ポリシー](media/azure-select-policy.png "Azure ポリシー")

8. [ポリシー] ウィンドウで、**[Connection string- Primary Key]\(接続文字列 – プライマリ キー\)** または **[Connection String- Secondary Key]\(接続文字列 - セカンダリ キー\)** の隣のボタンをクリックし、いずれかの接続文字列をコピーします。

### <a name="step-3-add-azure-to-cloud-app-security"></a>手順 3: Cloud App Security への Azure の追加
 
1. Cloud App Security ポータルで、**[調査]**、**[接続アプリ]** の順にクリックします。  
  
2. **[アプリ コネクタ]** ページで、[+] ボタンをクリックして **[Microsoft Azure]** を選択します。  
  
    ![Azure を Cloud App Security に接続する](media/azure-connect-app.png "Azure の接続")  
  
3. **[接続文字列]** フィールドに、前の手順でコピーした接続文字列を貼り付けます。  
  
4. **[コンシューマー グループ]** フィールドに「`$Default`」と入力します。
    
   >[!NOTE] 
   > 使うコンシューマー グループを別に作成した場合は、その**コンシューマー グループ**名を使います。
  
5. **[接続]** をクリックして接続し、接続をテストします。 これには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。  


> [!NOTE]
> この機能は、プライベート プレビューです。


## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  