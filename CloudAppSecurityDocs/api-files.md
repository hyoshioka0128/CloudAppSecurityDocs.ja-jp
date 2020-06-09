---
title: Cloud App Security Files API
description: この記事では、Files API の使用について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 486455bb28d49514e1e3926796425411fa147e45
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505241"
---
# <a name="files-api"></a>Files API

*適用対象:Microsoft Cloud App Security*

> [!NOTE]
> この API は、Office 365 Cloud App Security では使用できません。

Files API は、クラウドアプリに格納されているファイルやフォルダーに関するメタデータを提供します (最終更新日、所有権など)。

サポートされている要求を次に示します。

- [ファイルの一覧表示](api-files-list.md)
- [ファイルのフェッチ](api-files-fetch.md)

## <a name="filters"></a>フィルター

フィルターの動作の詳細については、「[フィルター](api-introduction.md#filters)」を参照してください。

次の表では、サポートされるフィルターについて説明します。

| Assert | 種類 | 演算子 | Description |
| --- | --- | --- | --- |
| サービス (service) | 整数 (integer) | eq、neq | 指定されたアプリ appID からファイルをフィルター処理します。例: 11770 |
| instance | 整数 (integer) | eq、neq | 指定されたインスタンスのファイルをフィルター処理する |
| fileType | 整数 (integer) | eq、neq | ファイルの種類が指定されたファイルをフィルター処理します。 指定できる値は、次のとおりです。<br /><br />**0**: その他<br />**1**: ドキュメント<br />**2**: スプレッドシート<br />**3**: プレゼンテーション<br />**4**: テキスト<br />**5**: 画像<br />**6**: フォルダー |
| allowDeleted | boolean | eq | 指定できる値は、次のとおりです。<br /><br />**true**: 削除されたファイルを返します<br />**false**または not set: (trashed を含む) 削除されていないファイルを返します。 これは trashed 演算子によって上書きされます |
| policy | string | cabinetmatchedrulesequals、neq、isset、isnotset | 指定したポリシーに関連するアクティビティをフィルター処理する |
| filename | string | eq | ファイルをファイル名でフィルター処理する |
| modifiedDate | timestamp | lte、gte、range、lte_ndays、gte_ndays | ファイルが最後に変更された日付でフィルター処理する |
| createdDate | timestamp | lte、gte、範囲 | ファイルが作成された日付でフィルター処理する |
| コラボレーター. エンティティ | エンティティ pk | eq、neq | 指定したエンティティと共有されているファイルをフィルター処理します。 例: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| コラボレーター. domains | string | eq、neq | 指定したドメインと共有されているファイルをフィルター処理する |
| コラボレーター. グループ | string | eq、neq | 指定したグループと共有されているファイルをフィルター処理する |
| コラボレーター. withDomain | string | eq、neq、deq | 指定したドメインと共有されているファイルをフィルター処理する |
| owner. entity | エンティティ pk | eq、neq | 指定されたエンティティが所有するファイルをフィルター処理します。 例: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| 所有者. orgUnit | string | eq、neq | 指定した組織単位の所有者を含むファイルをフィルター処理する |
| 共有 | 整数 (integer) | eq、neq | 指定された共有レベルでファイルをフィルター処理します。 指定できる値は、次のとおりです。<br /><br />**4**: パブリック (インターネット)<br />**3**: パブリック<br />**2**: 外部<br />**1**: 内部<br />**0**: プライベート |
| フィールド | string | eq、neq | ファイル ID でファイルをフィルター処理する |
| fileLabels | string | eq、neq、isset、isnotset | 指定されたファイルラベル (タグ) Id を含むファイルをフィルター処理します |
| fileScanLabels | string | eq、neq、isset、isnotset | 指定されたコンテンツ検査警告 (タグ) Id を含むファイルをフィルター処理します |
| 拡張機能 | string | eq、neq | 指定されたファイル拡張子でファイルをフィルター処理する |
| mimeType | string | eq、neq | 指定された MIME の種類でファイルをフィルター処理します。1つの文字列である必要があります |
| trashed | boolean | eq | 指定できる値は、次のとおりです。<br /><br />**true**: trashed ファイルのみを返します。<br />**false**: trashed 以外のファイルを返します。 |
| parentFolder | folder | eq、neq | 指定されたフォルダーに含まれるファイルをフィルター処理する |
| folder | boolean | eq | 指定できる値は、次のとおりです。<br /><br />**true**: フォルダーのみを返します。<br >**false**: ファイルのみを返します |
| 検疫 | boolean | eq | 指定できる値は、次のとおりです。<br /><br />**true**: 検疫済みのファイルのみを返します。<br />**false**: 非検疫ファイルのみを返します |
| snapshotLastModifiedDate | timestamp | lte、gte、範囲 | スナップショットが最後に変更された日付でファイルをフィルター処理する |

[!INCLUDE [Open support ticket](includes/support.md)]
