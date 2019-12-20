---
title: Workday を Cloud App Security に接続する (プレビュー)
description: この記事では、API コネクタを使用して Cloud App Security に Workday アプリを接続し、使用状況を表示して制御する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 9/8/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 697e0bf88d8373faa050c82f5c9e659df6310706
ms.sourcegitcommit: db5ec79d219dd6674939c872ace7cd2ca80860a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75189793"
---
# <a name="connect-workday-to-microsoft-cloud-app-security-preview"></a>Workday を Microsoft Cloud App Security に接続する (プレビュー)

*適用対象: Microsoft Cloud App Security*

この記事では、App connector API を使用して、既存の Workday アカウントに Microsoft Cloud App Security を接続する手順について説明します。 この接続により、Workday の使用を可視化し、制御することができます。 Cloud App Security が Workday を保護する方法の詳細については、「 [workday を保護](protect-workday.md)する」を参照してください。

## <a name="prerequisites"></a>必要条件

Cloud App Security への接続に使用する Workday アカウントは、セキュリティグループ (新規または既存) のメンバーである必要があります。 Workday 統合システムユーザーを使用することをお勧めします。 セキュリティグループには、次のドメインセキュリティポリシーに対して次のアクセス許可を選択する必要があります。

| 機能領域 | ドメインセキュリティポリシー | サブドメインのセキュリティポリシー | レポート/タスクの権限 | 統合権限 |
| --- | --- | --- | --- | --- |
| System (システム) | 設定: テナントのセットアップ-全般 | 設定: テナントのセットアップ–セキュリティ | 表示、変更 | Get、Put |
| System (システム) | セキュリティ管理 | | 表示、変更 | Get、Put |
| System (システム) | システム監査 | | 表示 | 取得 |
| スタッフ | Worker データ: スタッフ | Worker データ: パブリックワーカーレポート | 表示 | 取得 |

> [!NOTE]
>
> * セキュリティグループのアクセス許可を設定するために使用するアカウントは、Workday 管理者である必要があります。
> * アクセス許可を設定するには、「機能領域のドメインセキュリティポリシー」を検索し、各機能領域 ("システム"/"スタッフ") を検索して、表に記載されているアクセス許可を付与します。
> * すべてのアクセス許可が設定されたら、"保留中のセキュリティポリシーの変更をアクティブにする" を検索し、変更を承認します。

Workday 統合ユーザー、セキュリティグループ、およびアクセス許可を設定する方法の詳細については、「アクセス[許可の統合または外部エンドポイント](https://go.microsoft.com/fwlink/?linkid=2103212)へのアクセス」の手順 1 ~ 4 を参照してください。

## <a name="how-to-connect-workday-to-cloud-app-security-using-oauth"></a>OAuth を使用して Workday を Cloud App Security に接続する方法

1. 「前提条件」に記載されているセキュリティグループのメンバーであるアカウントを使用して、Workday にサインインします。

1. [テナント設定の編集–システム] を検索し、[**ユーザーアクティビティログ**] で [**ユーザーアクティビティログを有効にする**] を選択します。

    ![ユーザーアクティビティログの許可のスクリーンショット](media/connect-workday-enable-logging.png)

1. 「Edit tenant setup – security」を検索し、[ **oauth 2.0 設定**] で [ **Oauth 2.0 Clients Enabled**] を選択します。

1. "API クライアントの登録" を検索し、[ **Api クライアントの登録-タスク**] を選択します。

1. [ **API クライアントの登録**] ページで、次の情報を入力し、[ **OK**] をクリックします。

    | フィールド名 | 値 |
    | ---- | ---- |
    | クライアント名 | Microsoft Cloud App Security |
    | クライアント許可の種類 | 認証コード付与 |
    | アクセストークンの種類 | Bearer |
    | リダイレクト URI | `https://portal.cloudappsecurity.com/api/oauth/connect` |
    | OAuth2 スコープ | **スタッフ**と**システム** |
    | スコープ (機能領域) | **スタッフ**と**システム** |

    ![API クライアントの登録のスクリーンショット](media/connect-workday-register-api-client.png)

1. 登録したら、次のパラメーターをメモして、[**完了**] をクリックします。

    * クライアント ID
    * クライアントシークレット
    * Workday REST API エンドポイント
    * トークンエンドポイント
    * 承認エンドポイント

    ![API クライアントの登録を確認するスクリーンショット](media/connect-workday-register-api-client-confirm.png)

1. Cloud App Security ポータルで、[**調査**] をクリックし、[**接続さ**れたアプリ] をクリックします。

1. [**アプリコネクタ**] ページで、プラスボタンをクリックし、[ **Workday**] をクリックします。

    ![アプリコネクタの追加のスクリーンショット](media/connect-workday-add-app.png)

1. ポップアップでインスタンス名を追加し、[Workday に**接続**] をクリックします。

    ![インスタンス名の追加のスクリーンショット](media/connect-workday-add-app-connect.png)

1. 次のページで、メモしておいた情報を詳細に入力し、[ **Workday で接続**] をクリックします。

    ![アプリの詳細を入力したスクリーンショット](media/connect-workday-add-app-connect-details.png)

1. Workday では、Workday アカウントへの Cloud App Security アクセスを許可するかどうかを確認するポップアップが表示されます。 続行するには、[**許可**] をクリックします。

    ![アプリへのアクセスの承認のスクリーンショット](media/connect-workday-add-app-allow.png)

1. Cloud App Security ポータルに戻ると、Workday が正常に接続されたことを示すメッセージが表示されます。 [**API のテスト**] をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、 [**閉じる**] をクリックします。

> [!NOTE]
> Workday に接続すると、接続する7日間のイベントが表示されます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
