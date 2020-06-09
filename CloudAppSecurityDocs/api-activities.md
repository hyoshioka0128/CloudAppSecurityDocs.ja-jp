---
title: Cloud App Security アクティビティ API
description: この記事では、アクティビティ API の使用について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: c3459843fc2a432f664ac09ebc67ec7c52a01fe4
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505591"
---
# <a name="activities-api"></a>アクティビティ API

*適用対象:Microsoft Cloud App Security*

アクティビティ API を使用すると、クラウドアプリで実行されるすべてのアクションを表示できます。 この API のデータは、どのユーザーがどのアプリにログインしたか、どのファイルが疑わしい場所からダウンロードされているかなどに関する情報を提供できます。

サポートされている要求を次に示します。

- [アクティビティの一覧表示](api-activities-list.md)
- [Fetch アクティビティ](api-activities-fetch.md)
- [アクティビティに関するフィードバック](api-activities-feedback.md)

## <a name="filters"></a>フィルター

フィルターの動作の詳細については、「[フィルター](api-introduction.md#filters)」を参照してください。

次の表では、サポートされるフィルターについて説明します。

| Assert | 種類 | 演算子 | Description |
| --- | --- | --- | --- |
| サービス (service) | 整数 (integer) | eq | 指定されたサービス appID に関連する neq フィルターアクティビティ (例: 11770) |
| instance | 整数 (integer) | eq、neq | 指定されたインスタンスからアクティビティをフィルター処理する |
| ユーザー. orgUnit | string | eq、neq、isset、isnotset | 実行中のユーザーの組織単位によるアクティビティのフィルター処理 |
| アクティビティ. eventType | string | eq、neq | イベントの種類別のアクティビティのフィルター処理 |
| activity.id | string | eq | ID によるアクティビティの検索 |
| アクティビティ。権限を借用します。 | boolean | eq | "True" に設定すると、偽装されたイベントのみを返します。 "false" に設定すると、偽装されていないイベントが返されます。 |
| activity. 種類 | boolean | eq | "True" に設定すると、管理者イベントのみが返され、"false" に設定すると、通常のイベントが返されます。 |
| takenAction | string | eq、neq | 実行されたアクションによってアクティビティをフィルター処理します。 指定できる値は、次のとおりです。<br /><br />**ブロック**: ブロック<br />**プロキシ**: セッション制御にリダイレクトされます<br />**BypassProxy**: バイパスセッション制御<br />**暗号化**: 暗号化<br />**暗号化解除**: 暗号化解除<br />**検証**済み: 検証済み<br />**encryptionfailed**: 暗号化に失敗しました<br />**保護**: 保護<br />**確認**: ステップアップ認証が必要です<br />**null**: No action |
| デバイス. 種類 | string | eq、neq | デバイスの種類別にアクティビティをフィルター処理します。 指定できる値は、次のとおりです。<br /><br />**デスクトップ**: PC<br />**Mobile**: mobile<br />**タブレット**: タブレット<br />**その他**: その他<br />**null**: 値なし |
| デバイス。タグ | string | eq、neq | デバイスタグ Id でアクティビティをフィルター処理する |
| userAgent userAgent | string | contains、ncontains | ユーザーエージェントで特定の文字列が含まれていない、または含まれていないアクティビティをフィルター処理する |
| userAgent | string | eq、neq | 指定されたユーザーエージェントタグ Id を含むアクティビティをフィルター処理します |
| 場所. 国 | string | eq、neq、isset、isnotset | 指定された国/地域コードからのアクティビティをフィルター処理します |
| 場所. 組織 | string | eq、neq、isset、isnotset、contains | 指定された組織からのアクティビティをフィルター処理する |
| ip アドレス | string | eq、startswith、notnotstartwith、isset、isnotset、neq | 指定された IP アドレスからのアクティビティをフィルター処理します |
| fileSelector | file | eq、neq | 指定されたファイルまたはフォルダーを含むアクティビティをフィルター処理する |
| office365url | string | startswith、eq、endswith | Office 365 の Url によるアクティビティのフィルター処理 |
| フィールド | string | eq | ID でファイルを検索する |
| ip. カテゴリ | 整数 (integer) | eq、neq | 指定されたサブネットカテゴリのアクティビティをフィルター処理します。 指定できる値は、次のとおりです。<br /><br />**1**: 企業<br />**2**: 管理<br />**3**: 危険<br />**4**: VPN<br />**5**: クラウドプロバイダー<br />**6**: その他 |
| ip タグ | string | eq、neq | IP タグ Id でアクティビティをフィルター処理する |
| text | string | eq、startswithsingle、text | フリーテキスト検索を実行してアクティビティをフィルター処理する |
| date | timestamp | lte、gte、range、lte_ndays、gte_ndays | 指定された時間範囲内に発生したアクティビティをフィルター処理する |
| policy | string | eq、neq、isset、isnotset | 指定したポリシーに関連するアクティビティをフィルター処理する |
| source | string | eq、neq | ソースの種類またはストリーム ID ですべてのアクティビティをフィルター処理します。 例: `[{ "s:stream-id", "t:source-type" }]` ソースの種類の値には、次のようなものがあります。<br /><br />**0**: アクセス制御<br />**1**: セッション制御<br />**2**: アプリコネクタ<br />**3**: アプリコネクタ分析<br />**5**: 検出<br />**6**: mdatp |
| alertId | string | eq | アラート ID に関連するすべてのアクティビティをフィルター処理する |
| activityObject | string | eq、neq | 指定された ID を含むアクティビティをフィルター処理します |
| fileLabels | string | eq、neq | 指定されたファイルラベル (タグ) Id を含むファイルをフィルター処理します |
| created || lte、gte、range、gt、lt、eq | 指定された時間範囲内に作成されたアクティビティをフィルター処理する |
| エンティティ | エンティティ pk | eq、neq、isset、isnotset、startswith | アクティビティを実行したエンティティによってアクティビティをフィルター処理します。 例: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| ユーザー. ユーザー名 | string | eq、neq、isset、isnotset、startswith | アクティビティを実行したユーザーによるアクティビティのフィルター処理 |
| ユーザー。タグ | string | eq、neq、isset、isnotset、startswith | 実行中のユーザーに属するタグによってアクティビティをフィルター処理します。 グループ Id が必要です |
| アクティビティ. azureSubscriptions | string | eq、neq | Azure サブスクリプションアクティビティのフィルター処理 |
| ユーザー. ドメイン | string | eq、neq、isset、isnotset | 実行中のユーザードメインによるアクティビティのフィルター処理 |

[!INCLUDE [Open support ticket](includes/support.md)]
