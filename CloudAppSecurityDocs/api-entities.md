---
title: Cloud App Security Entities API
description: この記事では、Entities API の使用について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: d55eb6d29586ba68cb46bd97b6718529da87ea51
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505221"
---
# <a name="entities-api"></a>Entities API

*適用対象:Microsoft Cloud App Security*

> [!NOTE]
> この API は、Office 365 Cloud App Security では使用できません。

Entities API は、組織のクラウドアプリを使用してユーザーとアカウントに関する基本的な情報を提供し、サービスの使用パターンを理解できるようにします。

サポートされている要求を次に示します。

- [リスト エンティティ](api-entities-list.md)
- [Fetch エンティティ](api-entities-fetch.md)
- [エンティティツリーのフェッチ](api-entities-fetch-tree.md)

## <a name="filters"></a>フィルター

フィルターの動作の詳細については、「[フィルター](api-introduction.md#filters)」を参照してください。

次の表では、サポートされるフィルターについて説明します。

| Assert | 種類 | 演算子 | 説明 |
| --- | --- | --- | --- |
| type| string | eq、neq | 型でエンティティをフィルター処理する |
| isAdmin | string | eq | 管理者であるエンティティをフィルター処理する |
| エンティティ | エンティティ pk | eq、neq | 特定のエンティティを含むエンティティをフィルター pk します。 ユーザーが選択されている場合は、もそのすべてのアカウントを返します。 例: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| userGroups |string | eq、neq | 関連付けられているグループ Id を使ってエンティティをフィルター処理する |
| app | 整数 (integer) | eq、neq | 指定された SaaS ID を持つサービスを使用してエンティティをフィルター処理します。例: 11770 |
| instance | 整数 (integer) | eq、neq | 指定された Appstances (SaaS ID とインスタンス ID) を持つサービスを使用してエンティティをフィルター処理します。例: 11770, 1059065 |
| isExternal | boolean | eq | エンティティの所属。 指定できる値は、次のとおりです。<br /><br />**true**: 外部<br />**false**: 内部<br />**null**: 値なし |
| domain | string | eq、neq、isset、isnotset | エンティティの関連ドメイン |
| organization | string | eq、neq、isset、isnotset | 指定された組織単位でエンティティをフィルター処理する |
| lastSeen | timestamp | lte、gte、 | 指定された日付の間に最後に見つかった範囲フィルターエンティティ |
| status | string | eq、neq | 状態でエンティティをフィルター処理します。 指定できる値は、次のとおりです。<br /><br />**0**: N/A<br />**1**: ステージング済み<br />**2**: アクティブ<br />**3**: 中断<br />**4**: 削除されました |
| score | 整数 (integer) | lt、gt、isset、isnotset | 調査の優先度スコアでエンティティをフィルター処理する |

[!INCLUDE [Open support ticket](includes/support.md)]
