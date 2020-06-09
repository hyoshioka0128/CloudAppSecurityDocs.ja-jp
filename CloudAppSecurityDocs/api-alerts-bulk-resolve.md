---
title: 一括解決-アラート API
description: この記事では Cloud App Security の Alerts API の一括解決要求について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 11d1cc9651a48042f9b7b7223e36da35b389fed4
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505561"
---
# <a name="bulk-resolve---alerts-api"></a>一括解決-アラート API

*適用対象:Microsoft Cloud App Security*

POST 要求を実行して、指定したフィルターに一致する複数のアラートを解決します。

## <a name="http-request"></a>HTTP 要求

```rest
POST /api/v1/alerts/resolve/
```

## <a name="request-body-parameters"></a>要求本文のパラメーター

| パラメーター | Description |
| --- | --- |
| filters | 要求のすべての検索フィルターを使用してオブジェクトをフィルター処理します。詳細については、「[アラートフィルター](api-alerts.md#filters) 」を参照してください。 |
| comment | アラートが解決される理由に関するコメント |

## <a name="example"></a>例

### <a name="request"></a>Request

要求の例を次に示します。

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/resolve" -d '{
  "comment": "Irrelevant",
  "filters": {
    "id": {
      "eq": [
        "55af7415f8a0a7a29eef2e1f",
        "55af741cf8a0a7a29eef2e20"
      ]
    }
  }
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]
