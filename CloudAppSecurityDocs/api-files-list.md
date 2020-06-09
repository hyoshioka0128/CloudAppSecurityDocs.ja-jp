---
title: List-Files API
description: この記事では、Cloud App Security の Files API でのリスト要求について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 36ad7275650f130263777a18ff7f5a3198de897d
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505191"
---
# <a name="list---files-api"></a>List-Files API

*適用対象:Microsoft Cloud App Security*

> [!NOTE]
> この要求は、Office 365 Cloud App Security では使用できません。

GET 要求または POST 要求を実行して、指定したフィルターに一致するファイルの一覧をフェッチします。

## <a name="http-request"></a>HTTP 要求

```rest
GET /api/v1/files/
```

```rest
POST /api/v1/files/
```

## <a name="request-body-parameters"></a>要求本文のパラメーター

| パラメーター | Description |
| --- | --- |
| filters | 要求のすべての検索フィルターを使用してオブジェクトをフィルター処理します。詳細については、「[ファイルフィルター](api-files.md#filters) 」を参照してください。 |
| skip | 指定された数のレコードをスキップします |
| limit | 要求によって返されるレコードの最大数 |

## <a name="example"></a>例

### <a name="request"></a>Request

要求の例を次に示します。

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/files/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### <a name="response"></a>Response

JSON 形式のファイルの一覧を返します。

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
