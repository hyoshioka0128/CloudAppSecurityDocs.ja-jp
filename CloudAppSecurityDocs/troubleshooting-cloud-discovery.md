---
title: Cloud Discovery エラーのトラブルシューティング - Cloud App Security | Microsoft Docs
description: この記事では、Cloud Discovery でよく起こるエラー一覧と、各エラーの推奨される解決策について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 04/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 76dfaebb-d477-4bdb-b3d7-04cc3fe6431d
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: cd11c5a35761f21cc928a3debbc05a58ef56b6d1
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74459983"
---
# <a name="troubleshooting-cloud-discovery"></a>クラウド検出のトラブル シューティング

*適用対象: Microsoft Cloud App Security*

この記事では、Cloud Discovery のエラー一覧と、各エラーの推奨される解決策について説明します。

## <a name="microsoft-defender-atp-integration"></a>Microsoft Defender ATP integration

If you integrated Microsoft Defender ATP with Cloud App Security, and you don't see the results of the integration - there's not a **Win10 endpoint users** report - make sure the machines you're connecting to are Windows 10 version 1809 or later, and that you waited the necessary two hours that it takes before your data is accessible.


## <a name="log-parsing-errors"></a>ログ解析エラー

ガバナンス ログを使用して Cloud Discovery ログの処理を追跡できます。 この記事では、表示される可能性がある各エラーに対する解決方法について説明します。

### <a name="governance-log-errors"></a>ガバナンス ログ エラー

|Error|[説明]|解決方法|
|----|----|----|
|サポートされていないファイルの種類|アップロードしたファイルが有効なログ ファイルではありません (画像ファイルなど)。|ファイアウォールまたはプロキシから直接エクスポートされた **text**、**zip、または **gzip** ファイルをアップロードします。|
|ログ形式が予期される形式と一致しません|アップロードしたログの形式が、このデータ ソースで予期されるログの形式と一致しませんでした。|1. Verify that the log isn't corrupt. <br /> 2. Compare and match your log to the sample format shown in the upload page.|
|Transactions are more than 90 days old (トランザクションは 90 日より前のものです)|すべてのトランザクションは 90 日よりも前のもので、無視されます。|最近のイベントが含まれる新しいログをエクスポートし、アップロードし直します。|
|No transactions to cataloged cloud apps (カタログ化されたクラウド アプリに対するトランザクションがありません)|認識されているクラウド アプリに対するトランザクションがログに見つかりません。|ログに送信トラフィック情報が含まれていることを確認します。|
|サポートされていないログの種類|**[データ ソース] = [その他 (サポートされていません)]** の場合、ログは解析されません。 代わりに、Cloud App Security テクニカル チームに送信され、レビューされます。|Cloud App Security テクニカル チームは、データ ソースごとに専用のパーサーを構築しています。 よく使用されているデータ ソースは、[既にサポートされています](set-up-cloud-discovery.md)。 サポートされないデータ ソースの各アップロードはレビューされ、新しいデータ ソース パーサーのパイプラインに追加されます。 新しいパーサーの通知は、Cloud App Security [リリース ノート](release-notes.md)の一部として公開されます。|

## <a name="log-collector-errors"></a>ログ コレクターのエラー

|問題 | 解決方法 |
|--------|--|
|FTP でログ コレクターに接続できません| 1. Verify that you are using FTP credentials and not SSH credentials. <br />2. Verify that the FTP client you are using is not set to SFTP.  |
|コレクター構成を更新できませんでした | 1. Verify that you entered the latest access token. <br />2. Verify in your firewall that the log collector is allowed to initiate outbound traffic on port 443.|
|コレクターに送信されたログがポータルに表示されません | 1.  Check to see if there are failed parsing tasks in the Governance log.  <br />  &nbsp;&nbsp;&nbsp;&nbsp;ある場合は、上記のログ解析エラー一覧を参照してエラーを解決してください。<br /> 2. If not, check the data sources and Log collector configuration in the portal. <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. [データ ソース] ページで、使用しているデータ ソースが正確に構成されていることを確認します。 <br />&nbsp;&nbsp;&nbsp;&nbsp;b. [ログ コレクター] ページで、データ ソースが正しいログ コレクターにリンクされていることを確認します。 <br /> 3. Check the local configuration of the on-premises log collector machine.  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. SSH でログ コレクターにログインし、collector_config ユーティリティを実行します。<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. 定義したプロトコル (Syslog/TCP、Syslog/UDP、または FTP) を使用してファイアウォールまたはプロキシがログをログ コレクターに送信していること、および正しいポートとディレクトリに送信していることを確認します。<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. コンピューターで netstat を実行し、ファイアウォールまたはプロキシからの接続を受信していることを確認します <br /> 4.   Verify that the log collector is allowed to initiate outbound traffic on port 443. |
|ログ コレクターの状態: 作成済み | ログ コレクターの展開が完了していませんでした。 展開ガイドに従って、オンプレミスの展開手順を完了します。|
|ログ コレクターの状態: 切断 | リンクされているどのデータ ソースからも、過去 24 時間以内にデータを受信していません。 |
|Failed pulling latest collector image| If you get this error during Docker deployment, it could be that you don't have enough memory ont he host machine. To check this, run this command on the host: `docker pull microsoft/caslogcollector`. If it returns this error: `failed to register layer: Error processing tar file(exist status 1): write /opt/jdk/jdk1.8.0_152/src.zip: no space left on device` contact your host machine administrator to provide more space.|

## <a name="discovery-dashboard-errors"></a>Discovery ダッシュボードのエラー

|問題|解決方法|
|----|----|
|Discovery データのアップロードと解析は成功しましたが、Cloud Discovery ダッシュボードの表示が空です|ダッシュボードは、ログに含まれていないデータでフィルターされているため、表示されるデータがない場合があります。 Cloud Discovery ダッシュボードのフィルターを変更して、別の種類のデータが結果に表示されるようにします。|

## <a name="next-steps"></a>次のステップ
  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  

