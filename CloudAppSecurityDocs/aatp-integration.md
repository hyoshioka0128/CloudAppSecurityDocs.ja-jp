---
title: Azure Advanced Threat Protection を Cloud App Security と統合する
description: この記事では、ハイブリッドリスク検出のために Cloud App Security で Azure Advanced Threat Protection インサイトを活用する方法について説明します。
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
ms.openlocfilehash: 63da07db9a3fa29c49f08f8082b969adcbda6bca
ms.sourcegitcommit: 4861a99debc71f266de738d5db78b711590b5e88
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68431147"
---
# <a name="azure-advanced-threat-protection-integration"></a>Azure Advanced Threat Protection の統合

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security は Azure Advanced Threat Protection (Azure ATP) と統合されており、クラウドアプリとオンプレミスの両方のハイブリッド環境でユーザーエンティティ行動分析 (UEBA) を提供[します。詳細については、「チュートリアル:Azure ATP によっ](tutorial-ueba.md)て提供される機械学習と行動分析の詳細については、危険なユーザーを調査してください。 Azure ATP について[は](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)、「」を参照してください。

## <a name="prerequisites"></a>前提条件

ハイブリッド環境全体で完全なユーザー調査を実行するためには、次が必要です。

- ご自身の Active Directory インスタンスに接続されている Azure ATP の有効なライセンス
- Azure ATP と Microsoft Cloud App Security 間の統合を有効にするには、グローバル管理者である必要があります 
- Azure ATP がない場合は、今すぐ試してみてください


>[!NOTE]
>Microsoft Cloud App Security のサブスクリプションを持っていない場合でも、Cloud App Security ポータルを使用して Azure ATP の洞察を得ることができます。


## <a name="enable-azure-advanced-threat-protection"></a>Azure Advanced Threat Protection を有効にする

Cloud App Security を Azure ATP と統合できるようにするには、次のようにします。

1. Cloud App Security の設定歯車で、 **[設定]** を選択します。
    
   ![[設定] メニュー](./media/azip-system-settings.png)

1. **[脅威保護]** で、 **[Azure ATP]** を選択します。
   
    ![azure advanced threat protection を有効にする](./media/aatp-integration.png)

3. **アラートやアクティビティなどの Azure ATP データを Cloud App Security に接続**するには、チェックボックスをオンにします。


> [!NOTE]
> 統合が有効になるまで、最大で12時間かかることがあります。
 
Azure Advanced Threat Protection 統合を有効にすると、組織内のすべてのユーザーに対してオンプレミスのアクティビティを表示できるようになります。 また、クラウドとオンプレミスの環境でアラートと疑わしいアクティビティを組み合わせることにより、ユーザーに関する高度な洞察も得られます。



## <a name="next-steps"></a>次の手順 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
