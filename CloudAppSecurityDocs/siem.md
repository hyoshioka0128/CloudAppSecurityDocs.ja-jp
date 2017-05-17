---
title: "Cloud App Security と SIEM の統合 | Microsoft Docs"
description: "このトピックでは、SIEM と Cloud App Security との統合に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/9/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 4649423b-9289-49b7-8b60-04b61eca1364
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5880ea404d6830c5d8f12534c04f123d8c517946
ms.sourcegitcommit: ea8207f412f31127beafd18a0bd028052fbadf90
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/09/2017
---
# <a name="siem-integration"></a>SIEM の統合
    
Cloud App Security と SIEM サーバーを統合し、アラートとアクティビティを一元的に監査できるようになりました。 SIEM サービスとの統合により、通常のセキュリティ ワークフローを維持し、セキュリティ手順を自動化してクラウドベースのイベントとオンプレミス イベントを関連付けた状態で、クラウド アプリケーションの保護を強化することができます。 Cloud App Security SIEM エージェントはサーバー上で実行され、Cloud App Security からアラートとアクティビティを取得し、SIEM サーバーに送ります。

SIEM を Cloud App Security と初めて統合した場合、過去 2 日間のアクティビティとアラートは SIEM に転送され、以降のすべてのアクティビティとアラートも (選択したフィルターに基づいて) 転送されます。 また、この機能を長期間無効にしてから再び有効にすると、過去 2 日間分とそれ以降のすべてのアラートとアクティビティが転送されます。

SIEM との統合は次の 3 つの手順で行われます。
1. Cloud App Security ポータルでセットアップします。 
2. JAR ファイルをダウンロードし、サーバーで実行します。
3. SIEM エージェントが動作しているか検証します。

## <a name="prerequisites"></a>前提条件

- 標準的な Windows または Linux サーバー (仮想マシンを使用可)。
- サーバーでは Java 8 を実行する必要があります。これより前のバージョンはサポートされていません。

## <a name="integrating-with-your-siem"></a>SIEM との統合

### <a name="step-1-set-it-up-in-the-cloud-app-security-portal"></a>手順 1: Cloud App Security ポータルでセットアップする

1. Cloud App Security ポータルの [設定]\(歯車アイコン) で、**[SIEM エージェント]** をクリックします。

2. [SIEM エージェントの追加] をクリックしてウィザードを起動します。
3. ウィザードで、**[SIEM エージェントの追加]** をクリックします。    
4. ウィザードで、名前を入力し、**SIEM 形式を選択**して、その形式に関する**詳細設定**をすべて設定します。 **[次へ]**をクリックします。

   ![SIEM の全般設定](./media/siem1.png)

5. **リモートの Syslog ホスト**の IP アドレスと **Syslog ポート番号**を入力します。 リモートの Syslog プロトコルとして TCP または UDP を選択します。
これらの詳細がわからない場合は、セキュリティ管理者と協力して取得してださい。
**[次へ]**をクリックします。
  ![リモートの Syslog 設定](./media/siem2.png)

6. SIEM サーバーにエクスポートするデータの種類を選択します。**アラート**と**アクティビティ**があります。 スライダーを使用してこれらを有効および無効にします。既定では、すべて選択されます。 **[適用先]** ドロップダウンを使用して、SIEM サーバーに特定のアラートとアクティビティのみを送信するようにフィルターを設定することができます。
**[結果の編集とプレビュー]** をクリックし、フィルターが予期したとおりに動作していることを確認できます。 **[次へ]**をクリックします。 

  ![データの種類の設定](./media/siem3.png)

7. トークンをコピーし、保存して後で使用できるようにします。 [完了] をクリックし、ウィザードから SIEM ページに戻り、テーブルで追加した SIEM エージェントを確認できます。 後で接続されるまで **[作成済み]** と表示されます。

### <a name="step-2-download-the-jar-file-and-run-it-on-your-server"></a>手順 2: JAR ファイルをダウンロードし、サーバーで実行する

1. [Microsoft Download Center から .zip ファイルをダウンロード](https://go.microsoft.com/fwlink/?linkid=838596)し、解凍します。

2. zip ファイルから .jar ファイルを抽出し、サーバーで実行します。
 ファイルを実行したら、次のように実行します。
    
      java -jar mcas-siemagent-0.87.20-signed.jar [--logsDirectory DIRNAME] [--proxy ADDRESS[:PORT]] --token TOKEN
> [!NOTE]
> - ファイル名は、SIEM エージェントのバージョンによって異なる場合があります。
> - 角かっこ [] で囲まれたパラメーターは省略可能です。関係する場合にのみ使用してください。

各変数の使用方法:
- DIRNAME は、ローカル エージェント デバッグ ログで使用するディレクトリのパスです。
- ADDRESS[:PORT] は、サーバーがインターネットに接続する際に使用するプロキシ サーバーのアドレスとポートです。
- TOKEN は、前の手順でコピーした SIEM エージェント トークンです。

「-h」と入力すれば、いつでもヘルプを表示できます。



### <a name="step-3-validate-that-the-siem-agent-is-working"></a>手順 3: SIEM エージェントが動作しているか検証する

1. Cloud App Security ポータルの SIEM エージェントの状態が **[接続エラー]** または **[切断]** ではないことと、エージェント通知がないことを確認します。 接続がダウンしている状態が 2 時間を超える場合は **[接続エラー]**、12 時間を超える場合は **[切断]** と表示されます。
 ![SIEM が切断されている状態](./media/siem-not-connected.png)
 
   以下のように接続状態である必要があります。 ![SIEM が接続されている状態](./media/siem-connected.png)

2. Syslog/SIEM サーバーで、Cloud App Security から送られたアクティビティとアラートが表示されていることを確認します。


## <a name="regenerating-your-token"></a>トークンの再生成
トークンが失われた場合は、テーブルの SIEM エージェント行の末尾にある 3 つの点をクリックし、**[トークンの再生成]** を選択して、いつでも再生成することができます。

 ![SIEM - トークンの再生成](./media/siem-regenerate-token.png)

## <a name="editing-your-siem-agent"></a>SIEM エージェントの編集 
SIEM エージェントを後で編集する必要がある場合は、テーブルの SIEM エージェント行の末尾にある 3 つの点をクリックし、**[編集]** を選択できます。 SIEM エージェントを編集する場合、.jar ファイルを再実行する必要はありません。自動的に更新されます。

![SIEM - 編集](./media/siem-edit.png)

## <a name="deleting-your-siem-agent"></a>SIEM エージェントの削除
後で SIEM エージェントを削除する必要がある場合は、テーブルの SIEM エージェント行の末尾にある 3 つの点をクリックし、**[削除]** を選択できます。

![SIEM - 削除](./media/siem-delete.png)

> [!NOTE]
> この機能はパブリック プレビュー段階です。

## <a name="see-also"></a>参照  
[SIEM 統合問題のトラブルシューティング](troubleshooting-siem.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  