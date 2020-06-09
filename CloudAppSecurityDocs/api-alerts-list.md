---
title: リスト-警告 API
description: この記事では、Cloud App Security の Alerts API でのリスト要求について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: ac3be42bfd076169a620a62566ed9cdad4e0c4a0
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505541"
---
# <a name="list---alerts-api"></a>リスト-警告 API

*適用対象:Microsoft Cloud App Security*

GET 要求または POST 要求を実行して、指定したフィルターに一致するアラートの一覧を取得します。

## <a name="http-request"></a>HTTP 要求

```rest
GET /api/v1/alerts/
```

```rest
POST /api/v1/alerts/
```

## <a name="request-body-parameters"></a>要求本文のパラメーター

| パラメーター | Description |
| --- | --- |
| filters | 要求のすべての検索フィルターを使用してオブジェクトをフィルター処理します。詳細については、「[アラートフィルター](api-alerts.md#filters) 」を参照してください。 |
| sortDirection | 並べ替えの方向。 使用できる値は `asc` 、とです。`desc` |
| sortField | アラートの並べ替えに使用するフィールド。 次のいずれかの値になります。<br /><br />**日付**: アラートが作成された日付<br /><br />**重要度**: アラートの重要度 |
| skip | 指定された数のレコードをスキップします |
| limit | 要求によって返されるレコードの最大数 |

## <a name="example"></a>例

### <a name="request"></a>Request

要求の例を次に示します。

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>Response

JSON 形式のアラートの一覧を返します。

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
