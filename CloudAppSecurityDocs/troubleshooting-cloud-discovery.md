---
title: Cloud Discovery エラーのトラブルシューティング-Cloud App Security |Microsoft Docs
description: この記事では、Cloud Discovery 頻繁に発生するエラーと解決策に関する推奨事項の一覧を示します。
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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: ea537c11bfb94f8f33f467ca04b5d797a3821635
ms.sourcegitcommit: 94f36e81067f05f841bec25bc31dd8983fde18f9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2020
ms.locfileid: "80675474"
---
# <a name="troubleshooting-cloud-discovery"></a>Cloud Discovery のトラブルシューティング

*適用対象: Microsoft Cloud App Security*

この記事では、それぞれの Cloud Discovery エラーと解決策に関する推奨事項の一覧を示します。

## <a name="microsoft-defender-atp-integration"></a>Microsoft Defender ATP 統合

Microsoft Defender ATP を Cloud App Security に統合し、統合の結果が表示されない場合。

|問題|解決方法|
|----|----|
|**Win10 エンドポイントユーザー**のレポートが一覧に表示されない|接続先のコンピューターが Windows 10 バージョン1809以降であり、データがアクセス可能になるまでに必要な2時間待機していることを確認します。|
|検出レポートが空です|エンドポイントデバイスがフォワードプロキシの背後にある場合は、ログコレクターを使用して、フォワードプロキシからログを送信することができます。|

## <a name="log-parsing-errors"></a>ログ解析エラー

ガバナンスログを使用して、Cloud Discovery ログの処理を追跡できます。 この記事では、表示される可能性がある各エラーに対して実行される解決方法について説明します。

### <a name="governance-log-errors"></a>ガバナンスログエラー

|エラー|説明|解決方法|
|----|----|----|
|サポートされていないファイルの種類|アップロードされたファイルは有効なログファイルではありません (画像ファイルなど)。|ファイアウォールまたはプロキシから直接エクスポートされた**テキスト**、* * zip、または**gzip**ファイルをアップロードします。|
|ログの形式が一致しません|アップロードしたログ形式が、このデータソースに必要なログ形式と一致しませんでした。|1. ログが破損していないことを確認します。 <br /> 2. [アップロード] ページに表示されるサンプル形式にログを比較して照合します。|
|トランザクションが90日を超えています|すべてのトランザクションが90日を超えているため、無視されます。|新しいログを最新のイベントと共にエクスポートし、再度アップロードします。|
|クラウドアプリをカタログ化するトランザクションがありません|認識されたクラウドアプリに対するトランザクションがログに見つかりません。|ログに送信トラフィック情報が含まれていることを確認します。|
|サポートされていないログの種類|[**データソース = その他 (サポート**されていません)] を選択した場合、ログは解析されません。 代わりに、レビューのために Cloud App Security テクニカルチームに送信されます。|Cloud App Security テクニカルチームは、各データソースごとに専用のパーサーを作成します。 最も一般的なデータソースは[既にサポート](set-up-cloud-discovery.md)されています。 サポートされていないデータソースの各アップロードは、新しいデータソースパーサーのパイプラインに確認され、追加されます。 新しいパーサーの通知は、Cloud App Security の[リリースノート](release-notes.md)の一部として公開されています。|

## <a name="log-collector-errors"></a>ログコレクターのエラー

|問題|解決方法|
|----|----|
|FTP 経由でログコレクターに接続できませんでした| 1. SSH 資格情報ではなく、FTP 資格情報を使用していることを確認します。 <br />2. 使用している FTP クライアントが SFTP に設定されていないことを確認します。  |
|コレクター構成の更新に失敗しました | 1. 最新のアクセストークンを入力したことを確認します。 <br />2. ログコレクターがポート443で送信トラフィックを開始できることをファイアウォールで確認します。|
|コレクターに送信されたログがポータルに表示されない | 1. ガバナンスログに失敗した解析タスクがあるかどうかを確認します。  <br />  &nbsp;&nbsp;&nbsp;&nbsp;場合は、上のログ解析エラーテーブルでエラーのトラブルシューティングを行います。<br /> 2. 見つからない場合は、ポータルでデータソースとログコレクターの構成を確認します。 <br /> &nbsp;&nbsp;&nbsp;&nbsp;。 [データソース] ページで、使用しているデータソースが正しく構成されていることを確認します。 <br />&nbsp;&nbsp;&nbsp;b &nbsp;ます。 [ログコレクター] ページで、データソースが適切なログコレクターにリンクされていることを確認します。 <br /> 3. オンプレミスのログコレクターコンピューターのローカル構成を確認します。  <br />&nbsp;&nbsp;&nbsp;&nbsp;。 SSH 経由でログコレクターにログインし、collector_config ユーティリティを実行します。<br/>&nbsp;&nbsp;&nbsp;b &nbsp;ます。 定義したプロトコル (Syslog/TCP、Syslog/UDP、または FTP) を使用して、ファイアウォールまたはプロキシがログコレクターにログを送信していること、およびそれらを正しいポートとディレクトリに送信していることを確認します。<br /> &nbsp;&nbsp;&nbsp;&nbsp;c。 コンピューターで netstat を実行し、ファイアウォールまたはプロキシから着信接続を受信することを確認します。 <br /> 4. log collector がポート443で送信トラフィックを開始できることを確認します。 |
|ログコレクターの状態: 作成済み | ログコレクターの展開が完了しませんでした。 展開ガイドに従って、オンプレミスのデプロイの手順を完了します。|
|ログコレクターの状態: 切断 | リンクされたデータソースから24時間以内に受信したデータはありません。 |
|最新のコレクターイメージをプルできませんでした| Docker の展開中にこのエラーが発生した場合は、ホストコンピューターに十分なメモリがない可能性があります。 これを確認するには、ホスト: `docker pull microsoft/caslogcollector`で次のコマンドを実行します。 このエラーが返された場合は、ホストコンピューターの管理者に連絡して、より多くの領域を提供 `failed to register layer: Error processing tar file(exist status 1): write /opt/jdk/jdk1.8.0_152/src.zip: no space left on device`。|

## <a name="discovery-dashboard-errors"></a>検出ダッシュボードのエラー

|問題|解決方法|
|----|----|
|探索データが正常にアップロードおよび解析されましたが、Cloud Discovery ダッシュボードが空になっています|ダッシュボードは、ログに記録されていないデータにフィルターを適用して、表示するデータがない場合があります。 Cloud Discovery ダッシュボードのフィルターを変更して、さまざまな種類のデータを表示し、結果を確認してみてください。|

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
