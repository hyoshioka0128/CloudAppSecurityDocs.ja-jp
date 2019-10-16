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
ms.openlocfilehash: 0612f759fbefa8880386b881277ad3cbff1896cd
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72336034"
---
# <a name="troubleshooting-the-siem-agent"></a>SIEM エージェントのトラブルシューティング

*適用対象: Microsoft Cloud App Security*

この記事では、SIEM を Cloud App Security に接続するときに考えられる問題とその解決方法について説明します。

## <a name="recover-missing-activity-events-in-mcas-siem-agent"></a>MCAS SIEM エージェントで不足しているアクティビティイベントを回復する 

SIEM エージェントによるアクティビティの配信に関する問題に関するシステムアラートを受け取った場合は、次の手順に従って、問題が発生した時間帯にアクティビティイベントを回復します。 次の手順では、並列で実行される新しい Recovery SIEM エージェントを設定し、SIEM にアクティビティイベントを再送信します。

>[!NOTE]
>回復プロセスでは、システムアラートに記載されている期間内にすべてのアクティビティイベントが再送信されます。 SIEM にこの期間のアクティビティイベントが既に含まれている場合は、この復旧後に重複するイベントが発生します。 

### <a name="step-1--configure-a-new-siem-agent-in-parallel-to-your-existing-agent"></a>手順 1-既存のエージェントと並行して新しい SIEM エージェントを構成する 
1. Cloud App Security ポータルで、[セキュリティ拡張機能] ページにアクセスします。  
2. [SIEM エージェント] タブで、[[新しい SIEM エージェントの追加](siem.md)] をクリックし、ウィザードを使用して、SIEM への接続の詳細を構成します。 

    >[!NOTE]
    >このエージェントは、既存のエージェントと並行して実行する必要があるため、ネットワーク構成が同じではない可能性があります。 

1. ウィザードで、**アクティビティのみ**を含むようにデータ型を構成し、元の SIEM エージェントで使用されていたのと同じアクティビティフィルター (存在する場合) を適用します。 
2. 回復モードチェックボックスをオンにして、**回復モード**をオンにします。 この操作により、問題が発生したため、不足しているアクティビティのみを送信するように SIEM エージェントが自動的に構成され、すべてのアクティビティが完全に回復された後にアクティビティの送信が停止されます。
3. 設定を保存します。
4. 生成されたトークンを使用して、新しいエージェントを実行します。


### <a name="step-2--validate-the-successful-data-delivery-to-your-siem"></a>手順2– SIEM へのデータ配信が成功したことを検証する 
1. SIEM に接続し、構成した新しい SIEM エージェントから新しいデータを受信したことを確認します。 
2. エージェントは、問題が発生した期間からのみアクティビティを送信します。アラートは発生しました。 

### <a name="step-3--remove-the-recovery-siem-agent"></a>手順3– Recovery SIEM エージェントを削除する 
1. Recovery SIEM エージェントは、データの送信を自動的に停止し、終了日に達すると無効になります。
2. SIEM で、recovery SIEM エージェントによって新しいデータが送信されていないことを確認します。 
3. コンピューター上のエージェントの実行を停止します。 
4. ポータルで、SIEM エージェントのページにアクセスし、Recovery SIEM エージェントを削除します。 
5. 元の SIEM エージェントが正常に実行されていることを確認します。 

## <a name="general-troubleshooting"></a>一般的なトラブルシューティング

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
|**データ サーバー送信エラー**|TCP 経由で Syslog サーバーを使用している場合、このエラーが発生することがあります。 SIEM エージェントが Syslog サーバーに接続できません。  このエラーが発生した場合、エージェントはエラーが修正されるまで新しいアクティビティを取得しません。 エラーが表示されなくなるまで修正手順に従ってください。|1. Syslog サーバーが正しく定義されていることを確認します。 Cloud App Security UI で、前述のように SIEM エージェントを編集します。 サーバー名を正しく記述したことを確認して、正しいポートを設定します。 </br>2. Syslog サーバーへの接続を確認します。ファイアウォールが通信をブロックしていないことを確認してください。| 
|**データ サーバー接続エラー**| TCP 経由で Syslog サーバーを使用している場合、このエラーが発生することがあります。 SIEM エージェントが Syslog サーバーに接続できません。  このエラーが発生した場合、エージェントはエラーが修正されるまで新しいアクティビティを取得しません。 エラーが表示されなくなるまで修正手順に従ってください。|1. Syslog サーバーが正しく定義されていることを確認します。 Cloud App Security UI で、前述のように SIEM エージェントを編集します。 サーバー名を正しく記述したことを確認して、正しいポートを設定します。 </br>2. Syslog サーバーへの接続を確認します。ファイアウォールが通信をブロックしていないことを確認してください。|
|**SIEM エージェント エラー**|SIEM エージェントの接続が X 時間以上切断されている|Cloud App Security ポータルで SIEM 構成を変更していないことを確認します。 変更していない場合、このエラーは Cloud App Security と SIEM エージェントを実行しているコンピューターとの間で接続の問題が発生している可能性があることを示します。|
|**SIEM エージェント通知エラー**|SIEM エージェント通知エラーが SIEM エージェントから受信されました。|このエラーは、SIEM エージェントと SIEM サーバー間の接続に関するエラーを受信したことを示します。 SIEM サーバーまたは SIEM エージェントを実行しているコンピューターでファイアウォールがブロックしていないことを確認します。 SIEM サーバーの IP アドレスが変更されていないことも確認してください。|


## <a name="next-steps"></a>次のステップ
  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
