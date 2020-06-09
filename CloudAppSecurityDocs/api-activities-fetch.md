---
title: Fetch-アクティビティ API
description: この記事では、Cloud App Security のアクティビティ API でのフェッチ要求について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 17e5d65219e883b5c89f5c799cf02e9825d20dc5
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505641"
---
# <a name="fetch---activities-api"></a>Fetch-アクティビティ API

*適用対象:Microsoft Cloud App Security*

GET 要求を実行して、指定された主キーに一致するアクティビティをフェッチします。

## <a name="http-request"></a>HTTP 要求

```rest
GET /api/v1/activities/<pk>/
```

## <a name="request-url-parameters"></a>要求 URL パラメーター

| パラメーター | Description |
| --- | --- |
| pk | アクティビティの ID |

## <a name="example"></a>例

### <a name="request"></a>Request

要求の例を次に示します。

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/activities/<pk>/"
```

### <a name="response"></a>Response

指定されたアクティビティを JSON 形式で返します。

```json
{
  // activity record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
