---
title: SIEM の統合のトラブルシューティング - Cloud App Security | Microsoft Docs
description: この記事では、SIEM を Cloud App Security に接続するときに考えられる問題とその解決方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: de64d9ca-eaed-4243-bcf7-adca5aff18c8
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 47158a4fba1027f4e1ac3bfe0a73b2b1014375e8
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568801"
---
# <a name="troubleshooting-the-siem-agent"></a>SIEM エージェントのトラブルシューティング

*適用対象:Microsoft Cloud App Security*

この記事では、SIEM を Cloud App Security に接続するときに考えられる問題とその解決方法について説明します。

## <a name="troubleshooting"></a>トラブルシューティング

Microsoft Cloud App Security ポータルの SIEM エージェントの状態が **[接続エラー]** または **[切断]** ではないことと、エージェント通知がないことを確認します。 接続が 2 時間以上停止した場合、状態が **[接続エラー]** として表示されます。 接続の停止時間が 12 時間を超えると、状態が **[切断]** に変わります。

エージェントを実行しているときにコマンド プロンプト ウィンドウに次のようなエラーのいずれかが表示された場合は、以下の手順を使用して問題を修正します。

|[エラー]|説明|解決策|
|----|----|----|
|General error during bootstrap|エージェントのブートストラップ中の予期しないエラーです。|サポートにお問い合わせください。|
|Too many critical errors|コンソールの接続中に発生する重大なエラーが多すぎます。 シャットダウンします。|サポートにお問い合わせください。|
|Invalid token|指定されたトークンが有効ではありません。|正しいトークンをコピーしたことを確認してください。 上記のプロセスを使用することで、トークンを再生成できます。|
|Invalid proxy address|指定されたプロキシ アドレスが有効ではありません。|正しいプロキシとポートを入力したことを確認してください。|


エージェントを作成したら、Cloud App Security ポータルで SIEM エージェント ページを確認してください。 次の**エージェントの通知**のいずれかが表示された場合は、以下の手順を使用して問題を修正します。

|[エラー]|説明|解決策|
|----|----|----|
|**内部エラー**|SIEM エージェントで不明なエラーが発生しました。|サポートにお問い合わせください。|
|**データ サーバー送信エラー**|TCP 経由で Syslog サーバーを使用している場合、このエラーが発生することがあります。 SIEM エージェントが Syslog サーバーに接続できません。  このエラーが発生した場合、エージェントはエラーが修正されるまで新しいアクティビティを取得しません。 エラーが表示されなくなるまで修正手順に従ってください。|1.Syslog サーバーが正しく定義されていることを確認する: Cloud App Security UI で、上記の説明のとおり、SIEM エージェントを編集します。 サーバー名を正しく記述したことを確認して、正しいポートを設定します。 </br>2.Syslog サーバーへの接続を確認する: ファイアウォールで通信がブロックされていないことを確認します。| 
|**データ サーバー接続エラー**| TCP 経由で Syslog サーバーを使用している場合、このエラーが発生することがあります。 SIEM エージェントが Syslog サーバーに接続できません。  このエラーが発生した場合、エージェントはエラーが修正されるまで新しいアクティビティを取得しません。 エラーが表示されなくなるまで修正手順に従ってください。|1.Syslog サーバーが正しく定義されていることを確認する: Cloud App Security UI で、上記の説明のとおり、SIEM エージェントを編集します。 サーバー名を正しく記述したことを確認して、正しいポートを設定します。 </br>2.Syslog サーバーへの接続を確認する: ファイアウォールで通信がブロックされていないことを確認します。|
|**SIEM エージェント エラー**|SIEM エージェントの接続が X 時間以上切断されている|Cloud App Security ポータルで SIEM 構成を変更していないことを確認します。 変更していない場合、このエラーは Cloud App Security と SIEM エージェントを実行しているコンピューターとの間で接続の問題が発生している可能性があることを示します。|
|**SIEM エージェント通知エラー**|SIEM エージェント通知エラーが SIEM エージェントから受信されました。|このエラーは、SIEM エージェントと SIEM サーバー間の接続に関するエラーを受信したことを示します。 SIEM サーバーまたは SIEM エージェントを実行しているコンピューターでファイアウォールがブロックしていないことを確認します。 SIEM サーバーの IP アドレスが変更されていないことも確認してください。|


## <a name="next-steps"></a>次の手順
  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
