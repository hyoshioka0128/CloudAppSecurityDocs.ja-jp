---
title: Azure Advanced Threat Protection を Cloud App Security に統合します。
description: この記事では、ハイブリッド リスク検出の Cloud App Security で Azure Advanced Threat Protection の洞察を活用する方法についての情報を提供します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 6/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 63e82b47-bb08-4614-af55-f85d04edfc5a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 99c866a8b2571c9572e042572d0f5160d0ae56e5
ms.sourcegitcommit: 3938edadc5f89f87cdeba607476cf3983b2413e8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67411922"
---
# <a name="azure-advanced-threat-protection-integration"></a>Azure Advanced Threat Protection との統合

*適用対象:Microsoft Cloud App Security*

Azure Advanced Threat Protection (ATP) ユーザー エンティティの行動分析 (UEBA) を提供するハイブリッド環境全体にわたる統合 Microsoft Cloud App Security - 両方のクラウド アプリとオンプレミスで、詳細についてを参照してください[チュートリアル。リスクの高いユーザーを調査]()machine learning と Azure ATP によって提供される行動の分析の詳細については、次を参照してください。 [Azure ATP は何ですか?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)します。

## <a name="prerequisites"></a>前提条件

ハイブリッド環境全体で完全なユーザー調査を実行するためには、次が必要です。

- ご自身の Active Directory インスタンスに接続されている Azure ATP の有効なライセンス
- Azure ATP と Microsoft Cloud App Security との統合を有効にするにはグローバル管理者がある必要があります。 
- 場合はない Azure ATP がある、今すぐ試す


>[!NOTE]
>Microsoft Cloud App Security のサブスクリプションを持っていない場合、Cloud App Security ポータルを使用して、Azure ATP の洞察を得ることができます。


## <a name="enable-azure-advanced-threat-protection"></a>Azure Advanced Threat Protection を有効にします。

Cloud App Security と Azure ATP 統合を有効にします。

1. Cloud App Security では、[選択] 設定の歯車アイコンで**設定**します。
    
   ![[設定] メニュー](./media/azip-system-settings.png)

1. **Threat Protection**、 **Azure ATP**します。
   
    ![azure の高度な脅威保護を有効にします。](./media/aatp-integration.png)

3. チェック ボックスをオン**アラートと Cloud App Security でアクティビティを含む Azure ATP の接続データ**します。


> [!NOTE]
> 統合が反映されるまで、最大 12 時間がかかる場合があります。
 
Azure Advanced Threat Protection の統合を有効にした後、組織内のすべてのユーザーに対して、オンプレミスのアクティビティが表示できるします。 強化 insights をアラートと不審なアクティビティを組み合わせて、クラウドおよびオンプレミス環境間で、ユーザーにします。



## <a name="next-steps"></a>次の手順 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
