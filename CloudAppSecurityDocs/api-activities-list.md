---
title: リスト-アクティビティ API
description: この記事では Cloud App Security のアクティビティ API でのリスト要求について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: f108ea5de6bc026e691f951c02a68c848a1818c4
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505601"
---
# <a name="list---activities-api"></a>リスト-アクティビティ API

*適用対象:Microsoft Cloud App Security*

GET 要求または POST 要求を実行して、指定したフィルターに一致するアクティビティの一覧を取得します。

## <a name="http-request"></a>HTTP 要求

```rest
GET /api/v1/activities/
```

```rest
POST /api/v1/activities/
```

## <a name="request-body-parameters"></a>要求本文のパラメーター

| パラメーター | Description |
| --- | --- |
| filters | 要求のすべての検索フィルターを使用してオブジェクトをフィルター処理します。詳細については、「[アクティビティフィルター](api-activities.md#filters) 」を参照してください。 |
| sortDirection | 並べ替えの方向。 使用できる値は `asc` 、とです。`desc` |
| sortField | アクティビティの並べ替えに使用するフィールド。 次のいずれかの値になります。<br /><br />**日付**: 活動が発生した日付<br /><br />**created**: アクティビティが保存されたときのタイムスタンプ |
| skip | 指定された数のレコードをスキップします |
| limit | 要求によって返されるレコードの最大数 |

## <a name="example"></a>例

### <a name="request"></a>Request

要求の例を次に示します。

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>Response

アクティビティの一覧を JSON 形式で返します。

```json
{
  "total": 5 // total number of records
  "hasNext": true // whether there is more data to show or not.
  "data": [
    // returned records
  ]
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
