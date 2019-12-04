---
title: Cloud App Security ポリシーのトラブルシューティング
description: この記事では、Cloud App Security のポリシー作成におけるトラブルシューティングのプロセスについて説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c6bd51063d2ddb6e8154bfefb962fac9b41baf18
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720967"
---
# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Microsoft Cloud App Security ポリシーのトラブルシューティング

*適用対象: Microsoft Cloud App Security*

この記事では、Cloud App Security のポリシー作成におけるトラブルシューティングのプロセスについて説明します。

## <a name="troubleshooting"></a>トラブルシューティング

ポリシーで発生する可能性があるエラーの説明と解決方法を次の表に示します。

|Error|[説明]|解決方法|
|----|----|----|
| **構成エラーのため、ポリシー <*名前*> が自動的に無効になりました**|Microsoft Cloud App Security でこのエラーが表示される場合は、示されたポリシーの構成を修正する必要があることを意味します。 Microsoft Cloud App Security ポリシーを作成するときは、IP タグやカスタムの機密の種類など、Cloud App Security またはセキュリティとコンプライアンス センター内で作成した他のオブジェクトを頻繁に活用します。 ポリシーで使用した IP タグまたはカスタムの機密の種類が削除されると、ポリシーが自動的に無効になり、このエラーが表示されます。 このメッセージは、フィルターが複雑すぎるなど、より一般的な構成エラーを示している可能性もあります。 |ポリシーを復元するには、ポリシーを編集し、示されているすべての構成エラーを修正します。 このエラーは通常、すべての削除されたオブジェクトをポリシーのフィルターから削除して、ポリシーを保存する必要があることを意味します。|

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
