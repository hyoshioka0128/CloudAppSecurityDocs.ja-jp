---
title: "脅威保護シナリオの概要 | Microsoft Docs"
description: "このトピックでは、クラウド環境における脅威から組織を保護するシナリオについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/30/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 0017be99-29c3-468e-a181-255e343ed4f5
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: fcc793f0fea71ef0666a7c99034185c5cd5fd894
ms.sourcegitcommit: 7e9ae94cb4f90fbccaa84f19bdebb4652a425e45
translationtype: HT
---
# <a name="controlling-and-protecting-your-files"></a>ファイルの制御と保護  

危険性の高い使用とクラウドのセキュリティに関する問題を特定し、異常なユーザー動作を検出して、承認されたクラウド アプリでの脅威を防ぎます。 ユーザーと管理者のアクティビティを把握し、疑わしい動作が見られる場合や、危険と思われる特定のアクティビティが承認された環境で発生した場合に自動的にアラートを生成するポリシーを定義します。 膨大な量の Microsoft 脅威インテリジェンスおよびセキュリティ調査データから情報を取り出します。 脅威検出ポリシーは、承認されたアプリで必要なすべてのセキュリティ制御が確実に実行されるようにするのに役立ちます。また、その制御を維持するのにも役立ちます。
 
## <a name="massive-quantities-of-files-are-being-downloaded-insider-data-exfiltration"></a>大量のファイルがダウンロードされる (内部者によるデータの持ち出し)

このユース ケースは、Office 365、Google Apps、Box、Dropbox、Salesforce に適用されます。

### <a name="the-threat"></a>脅威の内容
危険な状態のアカウントを持つ攻撃者は、複数のファイルのダウンロードまたはアクセスにより、Office 365 や他のクラウド アプリからデータを抜き取ることができます。

### <a name="the-solution"></a>解決策
ユーザーが短期間に大量のファイルのダウンロードまたはアクセスを行うタイミングを検出します。

#### <a name="prerequisites"></a>前提条件

Cloud App Security に、少なくとも 1 つのクラウド アプリを[接続](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。

#### <a name="setting-up-monitoring"></a>監視の設定

1.    既定では、Cloud App Security はネットワークをスキャンして基準を確立し、クラウドでユーザーが通常行う動作、タイミング、よく行う動作のパターンを学習します。 

2. さらに、クラウド アプリの監視を開始することが重要です。その場合、クラウド アプリを監視して大量ダウンロードを検出し、通常とは異なる動作が行われている場合にアラートを生成するポリシーを設定します。

    1. **[ポリシー]** ページで、[**[アクティビティ ポリシーの作成]**](user-activity-policies.md) をクリックします。 
    ![アクティビティ ポリシーの作成](./media/create-activity-policy.png)

    2. [**[ポリシー テンプレート]**](policy-template-reference.md) フィールドで、**[1 人のユーザーによる大量ダウンロード]** を選択します。
    
    3. 必要に応じて、反復アクティビティ フィルターを微調整できます。
    
    4. **[テンプレートの適用]** をクリックします。 
    ![アクティビティ ポリシー テンプレート](./media/activity-policy-template.png)
     
2. 一致を調査する
    
    1. **[ポリシー]** ページで、ポリシー名をクリックして **[ポリシー レポート]** に移動し、そのポリシーにトリガーされた一致を確認します。

    2. 特定の一致をクリックしてアクティビティ ドロワーを開き、一致を調査することができます。 ドロワーでは、このアクティビティと一致した他のポリシーを確認できます。 
     


#### <a name="validating-your-policy"></a>ポリシーの検証

1. アラートをシミュレートするには、ポリシー構成で定義したとおり、短期間に数回 (たとえば、30 分未満に 10 回)、接続されたクラウド アプリから複数のドキュメントをダウンロードします。
3. ポリシー レポートに移動します。 アクティビティ ポリシーの一致がすぐに表示されます。 
4. この一致をクリックして、ダウンロードされたファイルを確認することができます。 一致自体は、機密データを保護するようにマスクされます。 

#### <a name="removing-the-risk"></a>リスクの排除

リスクを検証してポリシーを微調整したら、ポリシーと一致する可能性があった誤検知を排除します。 次に、以下の操作を行います。 
  1. 行の最後にある 3 つのドットをクリックし、関連するガバナンス アクション、たとえば **[Put user in quarantine]** (ユーザー検疫に配置) を選択すると、[ガバナンス アクション](governance-actions.md)を即時に実行できます。

 ![外部自動ガバナンス](./media/auto-gov-external.png)

   2. 検証が完了したら、自動ガバナンス アクションを実行するように設定できます。 たとえば、SharePoint および OneDrive では **[外部ユーザーの削除]** または **[Put in user quarantine]** (ユーザー検疫に配置)、G Suite および Box では **[外部ユーザーの削除]** と **[パブリック アクセスの削除]** ができます。

  ![自動ガバナンス アクションを適用](./media/apply-automatic-gov-actions.png)



## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  