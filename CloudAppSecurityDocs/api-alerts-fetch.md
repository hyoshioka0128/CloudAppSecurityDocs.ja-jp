---
title: Fetch-Alerts API
description: この記事では、Cloud App Security の Alerts API でのフェッチ要求について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: aff7a98093101585ce7ed451b1eb983bcc53dfa8
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505531"
---
# <a name="fetch---alerts-api"></a>Fetch-Alerts API

*適用対象:Microsoft Cloud App Security*

GET 要求を実行して、指定された主キーと一致するアラートをフェッチします。

## <a name="http-request"></a>HTTP 要求

```rest
GET /api/v1/alerts/<pk>/
```

## <a name="request-url-parameters"></a>要求 URL パラメーター

| パラメーター | Description |
| --- | --- |
| pk | アラートの ID |

## <a name="example"></a>例

### <a name="request"></a>Request

要求の例を次に示します。

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/"
```

### <a name="response"></a>Response

指定された警告を JSON 形式で返します。

```json
{
  // alert record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
