---
title: アラートを無視する API
description: この記事では Cloud App Security の Alerts API での破棄要求について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 54c7b05a65c5a57e44381afe7c6f273a2cb364c7
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505551"
---
# <a name="dismiss---alerts-api"></a>アラートを無視する API

*適用対象:Microsoft Cloud App Security*

POST 要求を実行して、指定された主キーと一致するアラートを破棄します。

## <a name="http-request"></a>HTTP 要求

```rest
POST /api/v1/alerts/<pk>/dismiss/
```

## <a name="request-url-parameters"></a>要求 URL パラメーター

| パラメーター | Description |
| --- | --- |
| pk | アラートの ID |

## <a name="request-body-parameters"></a>要求本文のパラメーター

|Parameter |説明 | |comment |アラートが破棄された理由に関するコメント |

## <a name="example"></a>例

### <a name="request"></a>Request

要求の例を次に示します。

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/dismiss/" -d '{
  "comment": "Irrelevant"
}'
```

[!INCLUDE [Open support ticket](includes/support.md)]
