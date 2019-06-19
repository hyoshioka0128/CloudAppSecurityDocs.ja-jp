---
title: Azure Advanced Threat Protection を Cloud App Security に統合します。
description: この記事では、ハイブリッド リスク検出の Cloud App Security で Azure Advanced Threat Protection の洞察を活用する方法についての情報を提供します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 6/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 63e82b47-bb08-4614-af55-f85d04edfc5a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1f920a6cb1ddcc00930527b9ba22264d4b4637a6
ms.sourcegitcommit: 62778bfbc010b95cdef4c8aed23b0f195f382242
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2019
ms.locfileid: "67171486"
---
# <a name="azure-advanced-threat-protection-integration"></a>Azure Advanced Threat Protection との統合

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security は、Azure Advanced Threat Protection (ATP) ユーザー エンティティの行動分析 (UEBA) を提供するクラウド アプリとオンプレミスの両方のハイブリッド環境全体で統合します。 Machine learning と Azure ATP によって提供される行動の分析の詳細については、次を参照してください。 [Azure ATP は何ですか?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)します。

Azure ATP を統合することで、Cloud App Security ポータルのアラートとからの洞察が示されます。
- Microsoft Cloud App Security。これによりクラウド セッション内の攻撃が特定されます。Microsoft 製品だけでなくサード パーティ製アプリケーションも対象となります
- Azure Advanced Threat Protection、機械学習と行動分析をオンプレミス ネットワーク経由で攻撃を識別するために使用します。
- Azure Active Directory Identity Protection。クラウド内で ID に対するユーザーとサインインのリスクを検出し、事前に防ぎます


## <a name="prerequisites"></a>前提条件

ハイブリッド環境全体で完全なユーザー調査を実行するためには、次が必要です。

- Microsoft Cloud App Security の有効なライセンス
- ご自身の Active Directory インスタンスに接続されている Azure ATP の有効なライセンス

>[!NOTE]
>Azure ATP 用のサブスクリプションをお持ちでない場合でも Cloud App Security ポータルを使ってユーザーを調査できますが、オンプレミス環境から分析情報を受け取ることはできません。


## <a name="enable-azure-advanced-threat-protection"></a>Azure Advanced Threat Protection を有効にします。

Azure Advanced Threat Protection を Cloud App Security に統合するために必要なは、1 つのチェック ボックスをクリックします。 統合を有効にするは Cloud App Security にアクセスし、Azure ATP では、表示される、オンプレミスで疑わしいアクティビティを分析できるように、Cloud App Security にそれらをプルし、ハイブリッド環境のリスクの高いすべてのアクティビティ全体像を提供ユーザーによって実行されます。

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
  
