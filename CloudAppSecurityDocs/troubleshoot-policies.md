---
title: Cloud App Security ポリシーのトラブルシューティング | Microsoft Docs
description: このトピックでは、Cloud App Security のポリシー作成におけるトラブルシューティングのプロセスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 5/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: cfc1d9442c50153ce06a358ccdd88b4ab316a88d
ms.sourcegitcommit: af8fad9709171b200699ca1ed513e2831826ed7e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34445337"
---
*適用対象: Microsoft Cloud App Security*


# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Microsoft Cloud App Security ポリシーのトラブルシューティング

|Error|[説明]|解決方法|
|----|----|----|
| **構成エラーのため、ポリシー <policy name> が自動的に無効になりました**|Microsoft Cloud App Security でこのエラーが表示される場合は、指定されたポリシーの構成を修正する必要があることを意味します。 Microsoft Cloud App Security ポリシーを作成するときは、IP タグやカスタムの機密の種類など、Cloud App Security またはセキュリティとコンプライアンス センター内で作成した他のオブジェクトを頻繁に活用します。 ポリシーで使用した IP タグまたはカスタムの機密の種類が後から削除されると、ポリシーが自動的に無効になり、このエラーが表示されます。 これは、フィルターが複雑すぎるなど、より一般的な構成エラーを示している可能性もあります。 |ポリシーを復元するには、ポリシーを編集し、示されているすべての構成エラーを修正します。 つまり、通常は、すべての削除されたオブジェクトをポリシーのフィルターから削除して、ポリシーを保存する必要があります。|



## <a name="see-also"></a>参照
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます](https://premier.microsoft.com/)

