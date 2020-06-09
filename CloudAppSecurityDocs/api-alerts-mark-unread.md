---
title: 未読通知としてマークする-警告 API
description: この記事では Cloud App Security の Alerts API で未読の要求としてマークする方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: b46b50b7e82c8fdab2a431489b6d6f57a0833952
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505431"
---
# <a name="mark-as-unread---alerts-api"></a>未読通知としてマークする-警告 API

*適用対象:Microsoft Cloud App Security*

POST 要求を実行して、指定された主キーと一致するアラートを未読としてマークします。

## <a name="http-request"></a>HTTP 要求

```rest
POST /api/v1/alerts/<pk>/unread/
```

## <a name="request-url-parameters"></a>要求 URL パラメーター

| パラメーター | Description |
| --- | --- |
| pk | アラートの ID |

## <a name="example"></a>例

### <a name="request"></a>Request

要求の例を次に示します。

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/alerts/<pk>/unread/"
```

[!INCLUDE [Open support ticket](includes/support.md)]
