---
title: Workday を Cloud App Security に接続する
description: この記事では、API コネクタを使用して Cloud App Security に Workday アプリを接続し、使用状況を表示して制御する方法について説明します。
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 9/1/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1b467600661209d299ca5f5f4079a572aa3016c2
ms.sourcegitcommit: 0b78b13bc163bfcd6f2ae13b1f57acee05e5b423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2019
ms.locfileid: "70208912"
---
# <a name="connect-workday-to-microsoft-cloud-app-security"></a>Workday を Microsoft Cloud App Security に接続する

*適用対象:Microsoft Cloud App Security*

この記事では、App connector API を使用して、既存の Workday アカウントに Microsoft Cloud App Security を接続する手順について説明します。 この接続により、Workday の使用を可視化し、制御することができます。

## <a name="prerequisites"></a>前提条件

Cloud App Security への接続に使用する Workday アカウントは、次のドメインが有効になっているセキュリティグループのメンバーである必要があります。

- システム-セキュリティ管理
- システムシステムの監査
- スタッフ-ワーカーデータ:パブリックワーカーレポート

Workday 統合システムユーザーを使用することをお勧めします。

## <a name="how-to-connect-workday-to-cloud-app-security-using-oauth"></a>OAuth を使用して Workday を Cloud App Security に接続する方法

1. Workday アカウントに管理者アカウントでサインインします。

1. テナント設定の編集–システム を検索し、**ユーザーアクティビティログ** で **ユーザーアクティビティログを有効にする** を選択します。

    ![ユーザーアクティビティログの許可のスクリーンショット](media/connect-workday-enable-logging.png)

1. 「Edit tenant setup – security」を検索し、 **[oauth 2.0 設定]** で **[Oauth 2.0 Clients Enabled]** を選択します。

1. "API クライアントの登録" を検索し、 **[Api クライアントの登録-タスク]** を選択します。

1. **[API クライアントの登録]** ページで、次の情報を入力し、 **[OK]** をクリックします。

    | フィールド名 | 値 |
    | ---- | ---- |
    | クライアント名 | Microsoft Cloud App Security |
    | クライアント許可の種類 | 認証コード付与 |
    | アクセストークンの種類 | Bearer |
    | リダイレクト URI | `https://portal.cloudappsecurity.com/api/oauth/connect` |
    | OAuth2 スコープ | **スタッフ**と**システム** |
    | スコープ (機能領域) | **スタッフ**と**システム** |

    ![API クライアントの登録のスクリーンショット](media/connect-workday-register-api-client.png)

1. 登録したら、次のパラメーターをメモして、 **[完了]** をクリックします。

    - クライアント ID
    - クライアントシークレット
    - Workday REST API エンドポイント
    - トークンエンドポイント
    - 承認エンドポイント

    ![API クライアントの登録を確認するスクリーンショット](media/connect-workday-register-api-client-confirm.png)

1. Cloud App Security ポータルで、 **[調査]** をクリックし、 **[接続さ]** れたアプリ をクリックします。

1. **[アプリコネクタ]** ページで、プラスボタンをクリックし、 **[Workday]** をクリックします。

    ![アプリコネクタの追加のスクリーンショット](media/connect-workday-add-app.png)

1. ポップアップでインスタンス名を追加し、[Workday に**接続**] をクリックします。

    ![インスタンス名の追加のスクリーンショット](media/connect-workday-add-app-connect.png)

1. 次のページで、メモしておいた情報を詳細に入力し、 **[Workday で接続]** をクリックします。

    ![アプリの詳細を入力したスクリーンショット](media/connect-workday-add-app-connect-details.png)

1. Workday では、Workday アカウントへの Cloud App Security アクセスを許可するかどうかを確認するポップアップが表示されます。 続行するには、 **[許可]** をクリックします。

    ![アプリへのアクセスの承認のスクリーンショット](media/connect-workday-add-app-allow.png)

1. Cloud App Security ポータルに戻ると、Workday が正常に接続されたことを示すメッセージが表示されます。 **[API のテスト]** をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。

> [!NOTE]
> Workday に接続すると、接続する7日間のイベントが表示されます。

## <a name="next-steps"></a>次の手順

[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)
