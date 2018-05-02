---
title: Cloud App Security ポリシーのトラブルシューティング | Microsoft Docs
description: このトピックでは、Cloud App Security のポリシー作成におけるトラブルシューティングのプロセスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 9bfc880cdaa0bf87abfd2b3b34cdf647a4aa1aaf
ms.sourcegitcommit: 45311f2cafef79483e40d971a4c61c7673834d96
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2018
---
*適用対象: Microsoft Cloud App Security*


# <a name="troubleshooting-microsoft-cloud-app-security-policies"></a>Microsoft Cloud App Security ポリシーのトラブルシューティング

|Error|[説明]|解決方法|
|----|----|----|
| **ポリシー <policy name> が自動的に無効になりました。**|Microsoft Cloud App Security でこのエラーが表示される場合は、指定されたポリシーの構成を修正する必要があることを意味します。 Microsoft Cloud App Security ポリシーを作成するときは、IP タグや IP 範囲フィルターなどの Cloud App Security 内で作成された他のオブジェクトを頻繁に活用します。 ポリシーで使用した IP タグまたは範囲が後から削除されると、ポリシーが自動的に無効になり、このエラーが表示されます。 |ポリシーを復元するには、ポリシーを編集してそのフィルターから消去されたすべてのオブジェクトを削除して、ポリシーを保存します。|



## <a name="see-also"></a>参照
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます](https://premier.microsoft.com/)

