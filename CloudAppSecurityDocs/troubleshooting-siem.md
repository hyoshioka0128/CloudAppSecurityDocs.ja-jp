---
title: SIEM の統合のトラブルシューティング - Cloud App Security | Microsoft Docs
description: この記事では、SIEM を Cloud App Security に接続するときに考えられる問題とその解決方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 08/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: de64d9ca-eaed-4243-bcf7-adca5aff18c8
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: a5ab44813959db6ad7b1f437ba88b47223ce5e41
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459965"
---
# <a name="troubleshooting-the-siem-agent"></a>SIEM エージェントのトラブルシューティング

*適用対象: Microsoft Cloud App Security*

この記事では、SIEM を Cloud App Security に接続するときに考えられる問題とその解決方法について説明します。

## <a name="recover-missing-activity-events-in-mcas-siem-agent"></a>Recover missing activity events in MCAS SIEM Agent 

If you received a system alert regarding an issue with activity delivery through the SIEM agent, follow the steps below to recover the activity events in the timeframe of the issue. These steps will guide you through setting up a new Recovery SIEM agent that will run in parallel and resend the activity events to your SIEM.

>[!NOTE]
>The recovery process will resend all activity events in the timeframe described in the system alert. If your SIEM already contains activity events from this timeframe, you will experience duplicated events after this recovery. 

### <a name="step-1--configure-a-new-siem-agent-in-parallel-to-your-existing-agent"></a>Step 1 – Configure a new SIEM Agent in parallel to your existing agent 
1. In the Cloud App Security portal, go to Security Extensions page.  
2. In the SIEM Agents tab, click on [add a new SIEM agent](siem.md), and use the wizard to configure the connection details to your SIEM. 

    >[!NOTE]
    >This agent should run in parallel to the existing one, so network configuration might not be identical. 

1. In the wizard, configure the Data Types to include **only Activities** and apply the same activity filter that was used in your original SIEM agent (if it exists). 
2. Turn on **Recovery mode** by checking the Recovery mode checkbox. This action will automatically configure the SIEM Agent to send only the missing activities due to the issue and stop sending activities once all activities are fully recovered.
3. 設定を保存します。
4. Run the new agent using the generated token.


### <a name="step-2--validate-the-successful-data-delivery-to-your-siem"></a>Step 2 – Validate the successful data delivery to your SIEM 
1. Connect to your SIEM and validate that new data is received from the new SIEM Agent that you configured. 
2. The agent will only send activities from the timeframe of the issue, which you were alerted on. 

### <a name="step-3--remove-the-recovery-siem-agent"></a>Step 3 – Remove the Recovery SIEM agent 
1. The recovery SIEM agent will automatically stop sending data and be disabled once it reaches the end date.
2. Validate in your SIEM that no new data is sent by the recovery SIEM agent. 
3. Stop the execution of the agent on your machine. 
4. In the portal, go to SIEM Agent page, and remove the Recovery SIEM Agent. 
5. Make sure your original SIEM Agent is still running properly. 

## <a name="general-troubleshooting"></a>General troubleshooting

Microsoft Cloud App Security ポータルの SIEM エージェントの状態が **[接続エラー]** または **[切断]** ではないことと、エージェント通知がないことを確認します。 接続が 2 時間以上停止した場合、状態が **[接続エラー]** として表示されます。 接続の停止時間が 12 時間を超えると、状態が **[切断]** に変わります。

エージェントを実行しているときにコマンド プロンプト ウィンドウに次のようなエラーのいずれかが表示された場合は、以下の手順を使用して問題を修正します。

|Error|[説明]|解決方法|
|----|----|----|
|General error during bootstrap|エージェントのブートストラップ中の予期しないエラーです。|サポートにお問い合わせください。|
|Too many critical errors|コンソールの接続中に発生する重大なエラーが多すぎます。 シャットダウンします。|サポートにお問い合わせください。|
|Invalid token|指定されたトークンが有効ではありません。|正しいトークンをコピーしたことを確認してください。 上記のプロセスを使用することで、トークンを再生成できます。|
|Invalid proxy address|指定されたプロキシ アドレスが有効ではありません。|正しいプロキシとポートを入力したことを確認してください。|


エージェントを作成したら、Cloud App Security ポータルで SIEM エージェント ページを確認してください。 次の**エージェントの通知**のいずれかが表示された場合は、以下の手順を使用して問題を修正します。

|Error|[説明]|解決方法|
|----|----|----|
|**内部エラー**|SIEM エージェントで不明なエラーが発生しました。|サポートにお問い合わせください。|
|**データ サーバー送信エラー**|TCP 経由で Syslog サーバーを使用している場合、このエラーが発生することがあります。 SIEM エージェントが Syslog サーバーに接続できません。  このエラーが発生した場合、エージェントはエラーが修正されるまで新しいアクティビティを取得しません。 エラーが表示されなくなるまで修正手順に従ってください。|1. Make sure you properly defined your Syslog server: In the Cloud App Security UI, edit your SIEM agent as described above. サーバー名を正しく記述したことを確認して、正しいポートを設定します。 </br>2. Check connectivity to your Syslog server: Make sure your firewall isn't blocking communication.| 
|**データ サーバー接続エラー**| TCP 経由で Syslog サーバーを使用している場合、このエラーが発生することがあります。 SIEM エージェントが Syslog サーバーに接続できません。  このエラーが発生した場合、エージェントはエラーが修正されるまで新しいアクティビティを取得しません。 エラーが表示されなくなるまで修正手順に従ってください。|1. Make sure you properly defined your Syslog server: In the Cloud App Security UI, edit your SIEM agent as described above. サーバー名を正しく記述したことを確認して、正しいポートを設定します。 </br>2. Check connectivity to your Syslog server: Make sure your firewall isn't blocking communication.|
|**SIEM エージェント エラー**|SIEM エージェントの接続が X 時間以上切断されている|Cloud App Security ポータルで SIEM 構成を変更していないことを確認します。 変更していない場合、このエラーは Cloud App Security と SIEM エージェントを実行しているコンピューターとの間で接続の問題が発生している可能性があることを示します。|
|**SIEM エージェント通知エラー**|SIEM エージェント通知エラーが SIEM エージェントから受信されました。|このエラーは、SIEM エージェントと SIEM サーバー間の接続に関するエラーを受信したことを示します。 SIEM サーバーまたは SIEM エージェントを実行しているコンピューターでファイアウォールがブロックしていないことを確認します。 SIEM サーバーの IP アドレスが変更されていないことも確認してください。|


## <a name="next-steps"></a>次のステップ
  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
  
