---
title: IP アドレス範囲の作成-Data 強化 API
description: この記事では、Cloud App Security の Data 強化 API での IP アドレス範囲の作成要求について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 790389f16409b5554fe44e0b20d2f584b0fd0fe5
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505411"
---
# <a name="create-ip-address-range---data-enrichment-api"></a>IP アドレス範囲の作成-Data 強化 API

*適用対象:Microsoft Cloud App Security*

POST 要求を実行して、新しい IP アドレス範囲を追加します。

## <a name="http-request"></a>HTTP 要求

```rest
POST /cas/api/subnet/
```

## <a name="request-body-parameters"></a>要求本文のパラメーター

| パラメーター | 説明 |
| --- | --- |
| category | 範囲カテゴリの id |
| サブネットマスク | 文字列としてのマスクの配列 (IPv4/IPv6) |
| 組織 (オプション) | 登録されている ISP |
| タグ (省略可能) | タグの配列 ("text" プロパティがタグ名で設定されているオブジェクト)-new または existing |

現在、次のカテゴリがサポートされています。

| カテゴリ | Id |
| --- | -- |
| 企業 | 1 |
| 管理 | 2 |
| 遅延 | 3 |
| VPN | 4 |
| クラウドプロバイダー | 5 |
| その他 | 6 |

## <a name="example"></a>例

### <a name="request"></a>Request

要求の例を次に示します。

```rest
curl -XPOST -H "Authorization:<your_token_key>" "https://<tenant_id>.<tenant_region>.contoso.com/cas/api/subnet/create_rule/" -d '{
  "name":"range name",
  "category":5,
  "organization":"Microsoft",
  "subnets":[
    "192.168.1.0/24",
    "192.168.2.0/16"
  ],
  "tags":[
    "existing tag"
  ]
}'
```

### <a name="response"></a>Response

新しい範囲の id を文字列として返します。

[!INCLUDE [Open support ticket](includes/support.md)]
