---
title: Azure Information Protection 分類ラベルを自動的に適用する
description: このチュートリアルでは、Microsoft Cloud App Security で Azure Information Protection 分類ラベルを自動的に適用する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 1/27/2019
ms.topic: tutorial
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: c28cb20566ee3497dda7607c4d1a011d28d04a49
ms.sourcegitcommit: c24732bc40350c3cf416640b7d15f3c6f7be371d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2019
ms.locfileid: "55086415"
---
# <a name="tutorial-automatically-apply-azure-information-protection-classification-labels"></a>チュートリアル: Azure Information Protection 分類ラベルを自動的に適用する

*適用対象:Microsoft Cloud App Security*

すべての従業員が情報保護の重要性を理解し、ポリシー範囲内で作業を行うのが理想的です。 しかし、現実では、会計に携わるパートナーが不適切なアクセス許可で Box リポジトリにドキュメントをアップロードします。 1 週間後に、会社の機密情報が競合他社にリークしたことに気付くのです。 Microsoft Cloud App Security は、このようなことを事前に防ぐのに役立ちます。 この機能は、Box、SharePoint、OneDrive for Business で使用できます。 Azure Information Protection ラベルの適用は、使用可能な[ガバナンス アクション](governance-actions.md)の長いリストに含まれています。

このチュートリアルでは、お使いのクラウド ストレージ内に保存されたドキュメントにどのパブリック アクセス許可が設定されているかを特定して、違反が発生したときにアラート通知を受け取れるようにすることが可能です。 さらに、ご利用の Azure Information Protection の **[機密]** ラベルを自動適用して、ファイルに追加の暗号化を提供できます。

> [!div class="checklist"]
> * データ保護の設定 
> * ポリシーの検証


## <a name="enhanced-data-level-encryption-protection"></a>強化されたデータ レベルの暗号化による保護

Cloud App Security と Azure Information Protection との統合により、ファイルを自動的に暗号化して保護レベルを追加することができます。 Azure Information Protection でファイルが暗号化されると、Office 365 などの Azure Information Protection をサポートするアプリケーションでは、そのファイルを開き、分類ラベルで設定されているアクセス許可に従う方法が認識されます。 特定の保護ルールを適用するには、ラベルを使用します。 たとえば、開くことはできても、共有、印刷、転送、編集はできないファイルを設定します。

このような強い保護レベルは、ファイルと共に伝達されます。 ファイルを送信したり、コピーしたり、オンライン ストレージ アプリに格納したりしても、ファイルは保護されています。 ファイルが収められている USB ドライブを従業員がなくした場合は、ファイルがロックされます。 誰かがファイルを開こうとすると、ファイルの所有者はアラートを受け取ります。 Cloud App Security を使用することで、保護を自動的に適用できます。 たとえば、クレジット カード番号を含むか、あるいは財務部によってアップロードされており、外部で共有されるすべてのファイルを、分類ラベルで自動的に保護されるように設定します。

## <a name="the-threat"></a>脅威

組織内のユーザーは、Box に顧客の機密情報ファイルを保存し、組織内のすべてのユーザーと共有できるように設定します。 ユーザーは、直属チームだけでなく、サポート スタッフ全体がその Box アカウントにアクセスできることに気づいていません。 このアクセスには、ベンダー、パートナー、ときどきオフィスを訪れるビジターも含まれます。 組織の Box アカウントにアクセスできるユーザーならだれでも、その情報にアクセスできることになります。 そのようなアクセスは組織にとって危険なだけでなく、多くの国では個人情報の規制に違反するおそれがあり、結果的に法的な問題が発生することがあります。

## <a name="the-solution"></a>解決策

Cloud App Security と Microsoft Azure Information Protection を併用して、分類情報と保護情報を組み込み、データを永続的に保護できるようにします。そうすれば、データの格納場所や共有相手に関係なく、保護状態を維持することができます。 この保護により、同僚、顧客、パートナーとデータを安全に共有できるようになります。 データにアクセスできる人と、その人がデータに対してできることを定義します。 たとえば、ユーザーにファイルの表示と編集は許可しますが、印刷や転送は禁止します。 また、コラボレーターの削除や共有機能の削除など、Cloud App Security でファイルに対してサポートされている他の[ガバナンス アクション](governance-actions.md)も追加できます。

## <a name="prerequisites"></a>前提条件

- テナントに対する [Cloud App Security と Azure Information Protection の有効化](azip-integration.md)。
- Cloud App Security に [Box を接続します](connect-box-to-microsoft-cloud-app-security.md)。

## <a name="set-up-data-protection"></a>データ保護の設定

Box アカウントに格納されているファイルでクレジット カード番号を見つけるポリシーをセットアップしてみましょう。 ファイルが見つかったら、Azure Information Protection のラベルを自動的に適用し、そのラベルを持つすべてのファイルに対して行われる操作を制御します。

1. Box に格納されているすべての機密データを暗号化するポリシーを設定して、Box に格納するデータの保護を開始します。

    1. **[コントロール]** タブの [**[ポリシー]**](control-cloud-apps-with-policies.md) をクリックします。 

    2. **[ポリシーの作成]** をクリックして **[ファイル ポリシー]** を選択します。

    3. *Box データ保護* ポリシーを呼び出します。

    4. **[このポリシーの対象となるファイルのためのフィルターを作成]** で、個人の機密データを対象に設定します。
        - たとえば、**[親フォルダー]** を Box の**顧客データ**と同じになるように選択し、**[所有者]** を財務チームと同じになるように選択します。

    5. そのフォルダー内で、クレジット カード情報を含むファイルを探します。 **[コンテンツ検査方法]** で、**[組み込み DLP]**、**[事前設定した式に一致するファイルを含める]**、**[すべての国: ファイナンス: クレジット カード番号]** の順に選択します。

    6. **[ガバナンス]** で、**[Box]** セクションを開き、**[分類ラベルの適用]** を選択します。 適用するラベルを選択します。

    7. [Cloud App Security は Azure Information Protection と統合されている](azip-integration.md)ため、データの保護に使用される分類ラベルを既存の一覧から選択できます。

    8. **[作成]** をクリックします。 

   ![ポリシーに分類ラベルを追加する](./media/aip-auto-policy.png)

2. 一致を調査する

    1. **[ポリシー]** ページで、ポリシー名をクリックして **[ポリシー レポート]** に移動します。 そのポリシーに対してトリガーされた一致を確認します。

    2. 特定の一致をクリックしてファイルのドロワーを開き、一致を調査します。 ドロワーでは、このファイルと一致した他のポリシーを確認できます。

## <a name="validate-your-policy"></a>ポリシーの検証

1. アラートのシミュレーションを行うには、Box アカウントに移動して、**顧客データ** フォルダーのファイルへのアクセスを試みます。
2. ポリシー レポートに移動します。 ファイル ポリシーの一致がすぐに表示されます。 
3. この一致をクリックして、保護されたファイルを確認することができます。 一致自体は、機密データを保護するようにマスクされます。

>[!NOTE]
>
> - Cloud App Security は、現時点で Box、SharePoint、OneDrive for Business での Azure Information Protection ラベルの自動適用をサポートしています。
> - Cloud App Security を使用してドキュメントがラベル付けされると、視覚的なマーキングはすぐには適用されず、ドキュメントが Office アプリで開かれ、最初に保存されたときに適用されます。 詳細については、「[Azure Information Protection 用の視覚的なマーキングのラベルを構成する方法](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-markings#when-visual-markings-are-applied)」を参照してください。

## <a name="next-steps"></a>次の手順

[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  