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
ms.openlocfilehash: 81555a0839090af293cc58ce1bde9c70a2a82aac
ms.sourcegitcommit: c342abeec95359ddabdabcc3a081a0f91d52407c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72336044"
---
# <a name="troubleshooting-cloud-discovery"></a>クラウド検出のトラブル シューティング

*適用対象: Microsoft Cloud App Security*

この記事では、Cloud Discovery のエラー一覧と、各エラーの推奨される解決策について説明します。

## <a name="microsoft-defender-atp-integration"></a>Microsoft Defender ATP 統合

Microsoft Defender ATP を Cloud App Security に統合し、統合の結果が表示されない場合は、 **Win10 エンドポイントユーザー**のレポートはありません。接続先のコンピューターが Windows 10 バージョン1809以降であることを確認してください。は、データがアクセス可能になるまでに必要な2時間待機していました。


## <a name="log-parsing-errors"></a>ログ解析エラー

ガバナンス ログを使用して Cloud Discovery ログの処理を追跡できます。 この記事では、表示される可能性がある各エラーに対する解決方法について説明します。

### <a name="governance-log-errors"></a>ガバナンス ログ エラー

|Error|[説明]|解決方法|
|----|----|----|
|サポートされていないファイルの種類|アップロードしたファイルが有効なログ ファイルではありません (画像ファイルなど)。|ファイアウォールまたはプロキシから直接エクスポートされた **text**、**zip、または **gzip** ファイルをアップロードします。|
|ログ形式が予期される形式と一致しません|アップロードしたログの形式が、このデータ ソースで予期されるログの形式と一致しませんでした。|1. ログが破損していないことを確認します。 <br /> 2. [アップロード] ページに表示されるサンプル形式にログを比較して照合します。|
|Transactions are more than 90 days old (トランザクションは 90 日より前のものです)|すべてのトランザクションは 90 日よりも前のもので、無視されます。|最近のイベントが含まれる新しいログをエクスポートし、アップロードし直します。|
|No transactions to cataloged cloud apps (カタログ化されたクラウド アプリに対するトランザクションがありません)|認識されているクラウド アプリに対するトランザクションがログに見つかりません。|ログに送信トラフィック情報が含まれていることを確認します。|
|サポートされていないログの種類|**[データ ソース] = [その他 (サポートされていません)]** の場合、ログは解析されません。 代わりに、Cloud App Security テクニカル チームに送信され、レビューされます。|Cloud App Security テクニカル チームは、データ ソースごとに専用のパーサーを構築しています。 よく使用されているデータ ソースは、[既にサポートされています](set-up-cloud-discovery.md)。 サポートされないデータ ソースの各アップロードはレビューされ、新しいデータ ソース パーサーのパイプラインに追加されます。 新しいパーサーの通知は、Cloud App Security [リリース ノート](release-notes.md)の一部として公開されます。|

## <a name="log-collector-errors"></a>ログ コレクターのエラー

|問題 | 解決方法 |
|--------|--|
|FTP でログ コレクターに接続できません| 1. SSH 資格情報ではなく、FTP 資格情報を使用していることを確認します。 <br />2. 使用している FTP クライアントが SFTP に設定されていないことを確認します。  |
|コレクター構成を更新できませんでした | 1. 最新のアクセストークンを入力したことを確認します。 <br />2. ログコレクターがポート443で送信トラフィックを開始できることをファイアウォールで確認します。|
|コレクターに送信されたログがポータルに表示されません | 1. ガバナンスログに失敗した解析タスクがあるかどうかを確認します。  <br />  &nbsp;&nbsp;&nbsp;&nbsp;ある場合は、上記のログ解析エラー一覧を参照してエラーを解決してください。<br /> 2. 見つからない場合は、ポータルでデータソースとログコレクターの構成を確認します。 <br /> &nbsp;&nbsp;&nbsp;&nbsp;a. [データ ソース] ページで、使用しているデータ ソースが正確に構成されていることを確認します。 <br />&nbsp;&nbsp;&nbsp;&nbsp;b. [ログ コレクター] ページで、データ ソースが正しいログ コレクターにリンクされていることを確認します。 <br /> 3. オンプレミスのログコレクターコンピューターのローカル構成を確認します。  <br />&nbsp;&nbsp;&nbsp;&nbsp;a. SSH でログ コレクターにログインし、collector_config ユーティリティを実行します。<br/>&nbsp;&nbsp;&nbsp;&nbsp;b. 定義したプロトコル (Syslog/TCP、Syslog/UDP、または FTP) を使用してファイアウォールまたはプロキシがログをログ コレクターに送信していること、および正しいポートとディレクトリに送信していることを確認します。<br /> &nbsp;&nbsp;&nbsp;&nbsp;c. コンピューターで netstat を実行し、ファイアウォールまたはプロキシからの接続を受信していることを確認します <br /> 4. log collector がポート443で送信トラフィックを開始できることを確認します。 |
|ログ コレクターの状態: 作成済み | ログ コレクターの展開が完了していませんでした。 展開ガイドに従って、オンプレミスの展開手順を完了します。|
|ログ コレクターの状態: 切断 | リンクされているどのデータ ソースからも、過去 24 時間以内にデータを受信していません。 |
|最新のコレクターイメージをプルできませんでした| Docker の展開中にこのエラーが発生した場合は、ホストコンピューターに十分なメモリがない可能性があります。 これを確認するには、ホストで次のコマンドを実行します: `docker pull microsoft/caslogcollector`。 このエラーが返された場合は、ホストコンピューターの管理者に連絡して、より多くの領域を提供してください。 @no__t。|

## <a name="discovery-dashboard-errors"></a>Discovery ダッシュボードのエラー

|問題|解決方法|
|----|----|
|Discovery データのアップロードと解析は成功しましたが、Cloud Discovery ダッシュボードの表示が空です|ダッシュボードは、ログに含まれていないデータでフィルターされているため、表示されるデータがない場合があります。 Cloud Discovery ダッシュボードのフィルターを変更して、別の種類のデータが結果に表示されるようにします。|

## <a name="next-steps"></a>次のステップ
  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  

