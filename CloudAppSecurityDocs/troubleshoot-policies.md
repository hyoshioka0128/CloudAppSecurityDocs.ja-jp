---
title: "Cloud App Security ポリシーのトラブルシューティング | Microsoft Docs"
description: "このトピックでは、Cloud App Security のポリシー作成におけるトラブルシューティングのプロセスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/15/2018
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ccd15579fd18616dccd663947d6513c21e1e1527
ms.sourcegitcommit: 458e936e1ac548eda37e9bf955b439199bbdd018
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2018
---
# <a name="troubleshooting-cloud-app-security-policies"></a>Cloud App Security ポリシーのトラブルシューティング

|Error|[説明]|解決方法|
|----|----|----|
| **ポリシー <policy name> が自動的に無効になりました。**|Cloud App Security でこのエラーが表示される場合は、指定されたポリシーの構成を修正する必要があることを意味します。 Cloud App Security ポリシーを作成するときは、IP タグや IP 範囲フィルターなどの Cloud App Security 内で作成された他のオブジェクトを頻繁に活用します。 ポリシーで使用した IP タグまたは範囲が後から削除されると、ポリシーが自動的に無効になり、このエラーが表示されます。 |ポリシーを復元するには、ポリシーを編集してそのフィルターから消去されたすべてのオブジェクトを削除して、ポリシーを保存します。|



## <a name="see-also"></a>参照
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます](https://premier.microsoft.com/)

