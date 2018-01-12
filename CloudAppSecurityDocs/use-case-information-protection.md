---
title: "Azure Information Protection 分類ラベルを自動的に適用する | Microsoft Docs"
description: "このトピックでは、Microsoft Cloud App Security で Azure Information Protection 分類ラベルを自動的に適用するプロセスについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 12/24/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eac0b192-98d7-4939-9a07-1d4a7f8c39c3
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 6ef94215cbb07dd35e9353e3a63b9e575905b16b
ms.sourcegitcommit: c0c0612cdf6805c8e92d7929be0f12f33660b2d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2017
---
# <a name="automatically-apply-azure-information-protection-classification-labels"></a>Azure Information Protection 分類ラベルを自動的に適用する  

すべての従業員が情報保護の重要性を理解し、ポリシー範囲内で作業を行うのが理想的です。 しかし、現実では、会計に携わるパートナーが不適切なアクセス許可で Box リポジトリにドキュメントをアップロードしてから 1 週間後に会社の機密情報が競合他社にリークしたことに気付く場合があります。 

Microsoft Cloud App Security は、このようなことを事前に防ぐのに役立ちます。

Cloud App Security では、Box アカウントに保存されているドキュメントに対する公開アクセス許可があることを識別し、分類エンジンを使用して、公開共有ドキュメント内に機密情報があることを識別します。 Cloud App Security はアラートを送信して事象の発生をユーザーに知らせるだけでなく、Azure Information Protection の**社外秘**分類ラベルを自動的に適用して、ファイルの暗号化を強化します。 

>[!NOTE]
> - Azure Information Protection ラベルの適用は、使用可能な[ガバナンス アクション](governance-actions.md)の長いリストに含まれています。
> - この機能は、Box、SharePoint、OneDrive for Business で使用できます。

### <a name="enhanced-data-level-encryption-protection"></a>強化されたデータ レベルの暗号化による保護

Cloud App Security と Azure Information Protection との統合により、ファイルを自動的に暗号化して保護レベルを追加することができます。 たとえば、Azure Information Protection がファイルを暗号化する場合、Azure Information Protection をサポートする (Office 365 などの) アプリケーションはそのファイルを開き、分類ラベルで設定されているアクセス許可に従う方法を認識します。 ラベルを使用して、特定の保護ルールを適用することができます。 たとえば、ファイルを開くことができても、共有、印刷、転送、編集はできないように設定することができます。 

このような強い保護レベルをファイルに適用することで、オンライン ストレージ アプリでファイルを送信し、コピーし、格納する場合でも、ファイルは保護されます。 従業員のいずれがファイルを含むサム ドライブを紛失した場合、ファイルはロックされ、誰かがそれを開こうとすると、ファイルの所有者はアラートを受け取ることになります。 Cloud App Security を使用することで、保護を自動的に適用できます。 たとえば、クレジット カード番号を含むか、あるいは財務部によってアップロードされており、外部で共有されるすべてのファイルを分類ラベルで自動的に保護されるように設定できます。 

## <a name="the-threat"></a>脅威 
組織内のユーザーは、Box に顧客の機密情報ファイルを保存し、組織内のすべてのユーザーと共有できるように設定します。 このユーザーは、直属チームだけでなく、ベンダー、パートナー、時々オフィスを訪れるビジターを含め、サポート スタッフ全体がその Box アカウントにアクセスできることに気づいていません。 組織の Box アカウントにアクセスできるユーザーならだれでも、その情報にアクセスできることになります。 組織にとって危険なだけでなく、多くの国では PII の規制に違反するおそれがあり、結果的に法的な問題が発生することがあります。

## <a name="the-solution"></a>解決策
Cloud App Security と Microsoft Azure Information Protection を併用して、分類情報と保護情報を組み込み、データを永続的に保護できるようにします。そうすれば、データの格納場所や共有相手に関係なく、保護状態を維持することができます。 また、同僚だけでなく、顧客やパートナーとデータを安全に共有できるようになります。 データにアクセスできるユーザーを定義します。また、コラボレーターの削除や共有機能の削除などの Cloud App Security でサポートされている他の[ガバナンス アクション](governance-actions.md)に加え、ユーザーがデータを操作できる内容 (ユーザーにファイルの表示と編集は許可するが、印刷や転送は許可しないようにするなど) を定義します。

## <a name="prerequisites"></a>前提条件

- テナントに対する [Cloud App Security と Azure Information Protection の有効化](azip-integration.md)。
- Cloud App Security に [Box を接続します](connect-box-to-microsoft-cloud-app-security.md)。

## <a name="setting-up-data-protection"></a>データ保護のセットアップ

Box アカウントに保存されているファイルでクレジット カード番号を探すポリシーを設定しましょう。番号が見つかると、Azure Information Protection ラベルが自動的に適用され、そのラベルを持つすべてのファイルに対して行われる操作が制御されます。

1. Box に格納されているすべての機密データを暗号化するポリシーを設定して、Box に格納するデータの保護を開始します。

    1. **[コントロール]** タブの [**[ポリシー]**](control-cloud-apps-with-policies.md) をクリックします。 
    
    2. **[ポリシーの作成]** をクリックして **[ファイル ポリシー]** を選択します。
    
    3. *Box データ保護* ポリシーを呼び出します。
    
    4. **[このポリシーの対象となるファイルのためのフィルターを作成]** で、個人の機密データを対象に設定します。<br></br>
    たとえば、**[親フォルダー]** に Box の **[Customer data]\(顧客データ\)** を選択し、**[所有者]** に財務チームを選択します。
    
    4. そのフォルダー内で、次のようにしてクレジット カード情報を含むファイルを見つけます。**[コンテンツ検査方法]** で、**[組み込み DLP]**、**[事前設定した式に一致するファイルを含める]**、**[すべての国: ファイナンス: クレジット カード番号]** の順に選択します。
    
    5. **[ガバナンス]** で、**[Box]** セクションを開き、**[分類ラベルの適用]** を選択し、適用するラベルを選択します。
    
    6. [Cloud App Security は Azure Information Protection と統合されている](azip-integration.md)ため、データの保護に使用される分類ラベルを既存の一覧から選択できます。
 
    7. **[作成]** をクリックします。 
   
   ![ポリシーに分類ラベルを追加する](./media/aip-auto-policy.png)
     
2. 一致を調査する
    
    1. **[ポリシー]** ページで、ポリシー名をクリックして **[ポリシー レポート]** に移動し、そのポリシーにトリガーされた一致を確認します。

    2. 特定の一致をクリックしてファイルのドロワーを開き、一致を調査します。 ドロワーでは、このファイルと一致した他のポリシーを確認できます。 
     
## <a name="validating-your-policy"></a>ポリシーの検証

1. アラートのシミュレーションを行うには、Box アカウントに移動して、**[Customer data]\(顧客データ\)** フォルダーのファイルへのアクセスを試みます。
3. ポリシー レポートに移動します。 ファイル ポリシーの一致がすぐに表示されます。 
4. この一致をクリックして、保護されたファイルを確認することができます。 一致自体は、機密データを保護するようにマスクされます。 

>[!NOTE]
>Cloud App Security は、現時点で Box、SharePoint、OneDrive for Business での Azure Information Protection ラベルの自動適用をサポートしています。


 ## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  