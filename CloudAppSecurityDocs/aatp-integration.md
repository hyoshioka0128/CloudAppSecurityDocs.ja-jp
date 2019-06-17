---
title: Azure Advanced Threat Protection を Cloud App Security に統合します。
description: この記事では、ハイブリッド リスク検出の Cloud App Security で Azure Advanced Threat Protection の洞察を活用する方法についての情報を提供します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 6/21/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 63e82b47-bb08-4614-af55-f85d04edfc5a
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 4ca98ab0cb5655d774c6ee4e7f917a6e9456092a
ms.sourcegitcommit: a25543c14c35f159dd06f7c0c89d6bc0e36a0413
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031064"
---
# <a name="azure-information-protection-integration"></a>Azure Information Protection の統合

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security は、Azure Advanced Threat Protection (ATP) ユーザー エンティティの行動分析 (UEBA) を提供するクラウド アプリとオンプレミスの両方のハイブリッド環境全体で統合します。 Machine learning と Azure ATP によって提供される行動の分析の詳細については、次を参照してください。 [Azure ATP は何ですか?](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp)します。

Azure ATP を統合することで、Cloud App Security ポータルのアラートとからの洞察が示されます。
- マイクロソフト製品だけでなく、サード パーティ製のアプリケーションも攻撃を識別する、クラウドのセッション内で、Microsoft Cloud App Security をカバーします。
- Azure Advanced Threat Protection、機械学習と行動分析をオンプレミス ネットワーク経由で攻撃を識別するために使用します。
- Azure Active Directory Identity Protection で検出され、クラウド内の id を事前にユーザーとサインインのリスクを防ぎます


## <a name="prerequisites"></a>前提条件

ハイブリッド環境全体で完全なユーザー調査の結果、次が必要です。

- Microsoft Cloud App Security の有効なライセンス
- Azure ATP の有効なライセンスは、Active Directory インスタンスに接続されています。

>[!NOTE]
>Azure ATP のサブスクリプションを持っていない場合、Cloud App Security ポータルを使用して、ユーザーを調査することができますが、オンプレミス環境から洞察を受信しません。


## <a name="enable-azure-advanced-threat-protection"></a>Azure Advanced Threat Protection を有効にします。

Azure Advanced Threat Protection を Cloud App Security に統合するために必要なは、1 つのチェック ボックスをクリックします。 統合を有効にするは Cloud App Security にアクセスし、Azure ATP では、表示される、オンプレミスで疑わしいアクティビティを分析できるように、Cloud App Security にそれらをプルし、ハイブリッド環境のリスクの高いすべてのアクティビティ全体像を提供ユーザーによって実行されます。

Cloud App Security と Azure ATP 統合を有効にします。

1. Cloud App Security では、[選択] 設定の歯車アイコンで**設定**します。
    
   ![[設定] メニュー](./media/azip-system-settings.png)

1. **Threat Protection**、 **Azure ATP**します。
   
    ![azure の高度な脅威保護を有効にします。](./media/aatp-integration.png)

3. チェック ボックスをオン**アラートと Cloud App Security でアクティビティを含む Azure ATP の接続データ**します。
 
Azure Advanced Threat Protection の統合を有効にした後、組織内のすべてのユーザーに対して、オンプレミスのアクティビティが表示できるします。 強化 insights をアラートと不審なアクティビティを組み合わせて、クラウドおよびオンプレミス環境間で、ユーザーにします。



## <a name="next-steps"></a>次の手順 
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
