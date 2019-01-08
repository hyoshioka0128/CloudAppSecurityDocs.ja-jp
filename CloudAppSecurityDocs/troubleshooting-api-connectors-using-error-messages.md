---
title: アプリ コネクタのエラー メッセージ トラブルシューティング - Cloud App Security | Microsoft ドキュメント
description: この記事では、API アプリ コネクタのエラー メッセージの一覧と各エラーの推奨される解決策について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 4b6ac04a-4653-4c4a-bd6f-5926743475cc
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 58258c189c3e4c271a1ae4e60ab8f517d20344ab
ms.sourcegitcommit: b86c3afd1093fbc825fec5ba4103e3a95f65758e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53176962"
---
# <a name="troubleshooting-app-connectors-using-error-messages"></a>エラー メッセージを使用したアプリ コネクタのトラブルシューティング

*適用対象:Microsoft Cloud App Security*

この記事では、API アプリ コネクタのエラー メッセージの一覧と各エラーの推奨される解決策について説明します。

## <a name="troubleshooting"></a>トラブルシューティング

API アプリ コネクタを使用してクラウド アプリに接続しようとしたときに発生したアプリ コネクタ エラーは、アプリ コネクタ ダイアログで確認できます。


> [!div class="mx-tableFixed"]
> 
> |エラー メッセージ|関連するアプリ|[説明]|解決方法|
> |----|----|----|------------|
> |HttpRequestFailure:Server returned:400 Bad Request: {"error":{"code":"AF20012","message":"Specified tenant ID (Tenant_ID goes here) is incorrectly configured in the system."|Office 365 |割り当てられた Office 365 ライセンスが見つかりませんでした。 |テナントに少なくとも 1 つの Office 365 ライセンスを割り当ててください。| 
> |AuthFatalFailureException: com.box.boxjavalibv2.exceptions.BoxServerException: {"error":"invalid_grant","error_description":"Invalid refresh token"}|ボックス|Box の更新トークンが有効ではありません。|プロセスに従って Box を Cloud App Security に接続し直してください。|
> |BoxRestException:Failed to parse response.|ボックス|内部エラー。|[今すぐテストする] リンクをもう一度クリックして Box への接続をテストします。|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"Invalid refresh token"}'|ボックス|Box の更新トークンが有効ではありません。|プロセスに従って Box を Cloud App Security に接続し直してください。|
> |BoxServerException:User cannot access this feature without having an enterprise|ボックス|Box アカウントがエンタープライズ アカウントではありません。|Box ライセンスをエンタープライズ バージョンの Box にアップグレードしてから、プロセスに従って Box を Cloud App Security に接続し直してください。|
> |BoxServerException:Unauthorized - Cannot authorize with this service|ボックス|Box 管理者が Box で Cloud App Security アプリケーションを削除しました。|プロセスに従って Box を Cloud App Security に接続し直してください。|
> |HttpRequestFailure:Server returned:401 Unauthorized|Okta|Okta トークンが有効ではありません。|プロセスに従って Okta を Cloud App Security に接続し直してください。|
> |IOException:|Okta|内部エラー。|サポートにお問い合わせください|
> |HttpRequestFailure:Server returned:404 Not Found|Okta|内部エラー。|サポートにお問い合わせください|
> |SocketTimeoutException:Read timed out|Salesforce|内部エラー。|[今すぐテストする] リンクをもう一度クリックして Salesforce への接続をテストします。|
> |HttpRequestFailure:Server returned:400 Bad Request|Salesforce|Salesforce への接続が完了していないか、期限切れです。|プロセスに従って Salesforce を Cloud App Security に接続し直してください。|
> |HttpRequestFailure:Server returned:401 Unauthorized|Office 365|内部の問題|[今すぐテストする] リンクをもう一度クリックします|
> |TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002:Error validating credentials. AADSTS70008:The provided authorization code or refresh token is expired. Send a new interactive authorization request for this user and resource.|Office 365|トークンが期限切れです|プロセスに従って Office 365 を Cloud App Security に接続し直してください。|
> |SocketTimeoutException:Read timed out|Office 365|内部エラー。|[今すぐテストする] リンクをもう一度クリックします|
> |NullPointerException|Office 365|内部エラー。|サポートにお問い合わせください|
> |IgniteException|Office 365|ドメインまたはユーザーが有効ではありません|設定をリセットし、プロセスに従って Office 365 を Cloud App Security に接続し直してください。|
> |ContextManagerServiceException: com.adallom.adalib.httputils.exceptions.TokenRefreshException: {"error":"invalid_grant","error_description":"AADSTS70002:Error validating credentials. AADSTS70008:The provided authorization code or refresh token is expired. Send a new interactive authorization request for this user and resource.|Office 365|ドメインまたはユーザーが有効ではありません|設定をリセットし、プロセスに従って Office 365 を Cloud App Security に接続し直してください。|
> |HttpRequestFailure:Server returned:400 Bad Request|Office 365|内部エラー。|数分後に [今すぐテストする] リンクをもう一度クリックしても動作しない場合は、プロセスに従って Office 365 を Cloud App Security に接続し直します。|
> |GoogleJsonResponseException:401 Unauthorized|G Suite|アクセスが拒否されました。 アクティビティ レコードの読み取り権限がありません。 G Suite にログインするユーザーは、管理者である必要があります。|管理者アカウントを使用して、プロセスに従って G Suite を Cloud App Security に接続し直します。|
> |GoogleJsonResponseException:403 Forbidden|G Suite|G Suite API を実行中に問題が発生する問題。|G Suite 用 Cloud App Security App Connector を展開した場合、次の点を確認してください。[無制限] をクリックした場合、G Suite アカウントが実際に無制限であることを確認します。 それ以外の場合は、App Connector をもう一度実行し、無制限アカウントのオプションをオフにします。 セットアップ中に定義した範囲が正しいことを確認します。 これが新しい展開ではなく、このエラーが表示される場合は、その日の API 制限に達しており、G Suite イベントが明日更新される可能性があります。|
> |TokenResponseException:400 Bad Request|G Suite|G Suite への接続が完了していないか、期限切れです。|プロセスに従って G Suite を Cloud App Security に接続し直してください。|
> |RuntimeException: com.adallom.adalib.httputils.exceptions.HttpRequestFailure:Server returned:403 Forbidden|ServiceNow|アクセス許可が正しくありません|管理者アカウントを使用して、プロセスに従って ServiceNow を Cloud App Security に接続し直します。|
> |HttpRequestFailure:Server returned:401 Unauthorized|Exchange Online|ユーザーまたはパスワードが正しくありません|ユーザー名とパスワードが正しいことを確認し、プロセスに従って Exchange Online を Cloud App Security に接続し直してください。|
> |HttpRequestFailure:Server returned:404 Not Found|Exchange Online|Exchange Online へのログインに使用しているユーザーが、Exchange Online にプライマリ メールボックスを持っていません (たとえば、Azure AD に存在しないユーザーや、Azure AD には存在しても Exchange Online ライセンスを持っていないユーザーがいます)。|新しい管理者アカウントを使用して、プロセスに従って Exchange Online を Cloud App Security に接続し直します。|
> |NullPointerException|AWS|内部エラー。|サポートにお問い合わせください|
> |HttpRequestFailure:Server returned:500 Internal server error|すべてのアプリ|アプリ内にエラーがありました。|アプリの状態を確認してください|
> |Service timeout|すべてのアプリ|Cloud App Security とアプリ間の接続でタイムアウトが検出されました。 アプリに問題がある可能性があります。|後でやり直してください。|

## <a name="next-steps"></a>次の手順

[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  

