---
title: Cloud App Security ポリシーのトラブルシューティング | Microsoft Docs
description: この記事では、Cloud App Security のポリシー作成におけるトラブルシューティングのプロセスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/9/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 31c07ffe1f19de86ce23cad099bd238d254c0bab
ms.sourcegitcommit: c497253a7ab63973bb806607e5f15dece91640be
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2018
ms.locfileid: "53123178"
---
# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Microsoft Cloud App Security ポリシーのトラブルシューティング

*適用対象: Microsoft Cloud App Security*

この記事では、Cloud App Security のポリシー作成におけるトラブルシューティングのプロセスについて説明します。

## <a name="troubleshooting"></a>トラブルシューティング

ポリシーで発生する可能性があるエラーの説明と解決方法を次の表に示します。

|Error|[説明]|解決方法|
|----|----|----|
| **構成エラーのため、ポリシー <*名前*> が自動的に無効になりました**|Microsoft Cloud App Security でこのエラーが表示される場合は、示されたポリシーの構成を修正する必要があることを意味します。 Microsoft Cloud App Security ポリシーを作成するときは、IP タグやカスタムの機密の種類など、Cloud App Security またはセキュリティとコンプライアンス センター内で作成した他のオブジェクトを頻繁に活用します。 ポリシーで使用した IP タグまたはカスタムの機密の種類が削除されると、ポリシーが自動的に無効になり、このエラーが表示されます。 このメッセージは、フィルターが複雑すぎるなど、より一般的な構成エラーを示している可能性もあります。 |ポリシーを復元するには、ポリシーを編集し、示されているすべての構成エラーを修正します。 このエラーは通常、すべての削除されたオブジェクトをポリシーのフィルターから削除して、ポリシーを保存する必要があることを意味します。|

## <a name="next-steps"></a>次の手順

[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます](https://premier.microsoft.com/)

