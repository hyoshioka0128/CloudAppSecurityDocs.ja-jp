---
title: Fetch entity tree-Entities API
description: この記事では、Cloud App Security の Entities API でのエンティティツリーのフェッチ要求について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: f3dad3e2e868af0399153b2b6995dcdb104be166
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505181"
---
# <a name="fetch-entity-tree---entities-api"></a>Fetch entity tree-Entities API

*適用対象:Microsoft Cloud App Security*

> [!NOTE]
> この要求は、Office 365 Cloud App Security では使用できません。

GET 要求を実行して、指定された主キーと一致するエンティティに関連するすべてのエンティティをフェッチします。 エンティティがユーザーである場合、は、そのユーザーに関連付けられているすべてのアカウントをフェッチします。 エンティティがアカウントである場合、はエンティティの親と兄弟をフェッチします。

## <a name="http-request"></a>HTTP 要求

```rest
GET /api/v1/entities/<pk>/retrieve_tree/
```

## <a name="request-url-parameters"></a>要求 URL パラメーター

| パラメーター | Description |
| --- | --- |
| pk | エンティティの ID |

## <a name="example"></a>例

### <a name="request"></a>Request

要求の例を次に示します。

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/api/v1/entities/<pk>/retrieve_tree/"
```

### <a name="response"></a>Response

指定されたエンティティツリーを JSON 形式で返します。

```json
{
  // entity tree record
}
```

[!INCLUDE [Open support ticket](includes/support.md)]
