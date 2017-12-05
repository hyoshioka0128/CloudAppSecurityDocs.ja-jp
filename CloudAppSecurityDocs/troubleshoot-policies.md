---
title: "Cloud App Security ポリシーのトラブルシューティング | Microsoft Docs"
description: "このトピックでは、Cloud App Security のポリシー作成におけるトラブルシューティングのプロセスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 29/11/2017
ms.topic: get-started-article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 828cc94a-248b-44f6-a1ba-c28c0a135f8c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6c8cbfa8899a6cfa66f6fc2a9ec9ff75375acecb
ms.sourcegitcommit: f4ec7f2cb81c9d83bb7f406ddcca91ab07790a98
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshooting-cloud-app-security-policies"></a>Cloud App Security ポリシーのトラブルシューティング

|エラー|説明|解決方法|
|----|----|----|
| **ポリシー <policy name> が自動的に無効になりました。**|Cloud App Security でこのエラーが表示される場合は、指定されたポリシーの構成を修正する必要があることを意味します。 Cloud App Security ポリシーを作成するときは、IP タグや IP 範囲フィルターなどの Cloud App Security 内で作成された他のオブジェクトを頻繁に活用します。 ポリシーで使用した IP タグまたは範囲が後から削除されると、ポリシーが自動的に無効になり、このエラーが表示されます。 |ポリシーを復元するには、ポリシーを編集してそのフィルターから消去されたすべてのオブジェクトを削除して、ポリシーを保存します。|



## <a name="see-also"></a>参照
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください](http://support.microsoft.com/oas/default.aspx?prid=16031)  
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます](https://premier.microsoft.com/)

