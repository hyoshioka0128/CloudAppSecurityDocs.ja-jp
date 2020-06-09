---
title: Cloud App Security Alerts API
description: この記事では、Alerts API の使用について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 0363d275c764d1e92d8d3f295de82e0c5bd2143a
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505441"
---
# <a name="alerts-api"></a>アラート API

*適用対象:Microsoft Cloud App Security*

Alerts API は、Cloud App Security によって識別される即時のリスクに関する情報を提供し、注意が必要です。 アラートは、不審な使用パターン、または会社のポリシーに違反しているコンテンツを含むファイルから生成されます。

サポートされている要求を次に示します。

- [アラートを一覧表示する](api-alerts-list.md)
- [一括破棄](api-alerts-bulk-dismiss.md)
- [一括解決](api-alerts-bulk-resolve.md)
- [フェッチアラート](api-alerts-fetch.md)
- [アラートを無視](api-alerts-dismiss.md)
- [アラートを開封済みとしてマーク](api-alerts-mark-read.md)
- [警告を未読としてマーク](api-alerts-mark-unread.md)

## <a name="filters"></a>フィルター

フィルターの動作の詳細については、「[フィルター](api-introduction.md#filters)」を参照してください。

次の表では、サポートされるフィルターについて説明します。

| Assert | 種類 | 演算子 | Description |
| --- | --- | --- | --- |
| entity. エンティティ | エンティティ pk | eq、neq | 指定されたエンティティに関連するアラートをフィルター処理します。 例: `[{ "id": "entity-id", "saas": 11161, "inst": 0 }]` |
| エンティティ. ip | string | eq、neq | 指定された IP アドレスに関連するアラートをフィルター処理する |
| entity. サービス | 整数 (integer) | eq、neq | 指定されたサービス appId に関連するアラートをフィルター処理します。例: 11770 |
| entity. インスタンス | 整数 (integer) | eq、neq | 指定されたインスタンスに関連するアラートをフィルター処理します。例: 11770、1059065 |
| エンティティ. ポリシー | string | eq、neq | 指定したポリシーに関連するアラートをフィルター処理する |
| entity. ファイル | string | eq、neq | 指定されたファイルに関連するアラートをフィルター処理する |
| severity | 整数 (integer) | eq、neq | 重要度でフィルターします。 指定できる値は、次のとおりです。<br /><br />**0**: 低<br />**1**: 中<br/>**2**: 高 |
| 解決状態 | 整数 (integer) | eq、neq | アラートの解決状態でフィルター処理します。有効な値は次のとおりです。<br /><br />**0**: 開く<br />**1**: 破棄<br />**2**: 解決済み |
| 読み取り | boolean | eq | "True" に設定すると、"false" に設定した場合、未読のアラートのみが返されます。 |
| date | timestamp | lte、gte、range、lte_ndays、gte_ndays | アラートがトリガーされた時刻でフィルター処理する |
| 解決日 | timestamp | lte、gte、範囲 | アラートが解決された時刻でフィルター処理する |
| リスク | 整数 (integer) | eq、neq | リスクによるフィルター |
| alertType | 整数 (integer) | eq、neq | アラートの種類でフィルター |
| id | string | eq、neq | アラート Id でフィルター処理する |
| source | string | eq | アラートの配信元 (組み込みまたはポリシー) |

[!INCLUDE [Open support ticket](includes/support.md)]
