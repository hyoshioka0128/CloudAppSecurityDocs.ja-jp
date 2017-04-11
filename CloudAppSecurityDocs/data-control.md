---
title: "データ コントロール シナリオの概要 |Microsoft Docs"
description: "このトピックでは、クラウド環境内でデータを制御するシナリオについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/2/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 57927618-cb66-4c7f-afd7-c96926460816
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e7e735519caa7da514f06db13afc737cf6ef1806
ms.sourcegitcommit: 661f4ce41262e8462c90fd2a4f1232e2154d5113
translationtype: HT
---
# <a name="controlling-and-protecting-your-files"></a>ファイルの制御と保護  

現代の企業社会では大量のデータとデバイスが存在し、自分のデータのありかや誰がそれにアクセスできるのか追跡し続けていくのは難しいものです。 Cloud App Security では、クラウド全体でファイル保護を有効にすることで、データを管理することができます。 Cloud App Security は、企業クラウドで許可するもの、許可しないものについてポリシーを作成するツールを提供し、さらに幅広い自動化プロセスを用意して、継続的なコンプライアンスのスキャン、法的な電子情報開示タスク、独自クラウドに保管または外部やパブリックに共有している機密性の高いコンテンツの DLP、その他多くの使用ケースを提供します。  
Cloud App Security は、20 を超えるメタデータ フィルター (アクセス レベルやファイルの種類など) に基づいてファイルの種類を監視できます。 詳細については、「[ファイル](file-filters.md)」を参照してください。 下記の 2 つは、すべての組織が直面するデータに関する脅威の例で、クラウド上のファイルを保護する方法と手順を述べています。
 
## <a name="files-that-contain-sensitive-data-are-being-shared-externally"></a>機密データを含むファイルが外部に共有されている 

この使用ケースは、Office 365、G Suite、Box、Dropbox、Salesforce に適用されます。

### <a name="the-threat"></a>脅威の内容
従業員は、機密データを含む企業ファイルを組織の外部に共有しています。 これは、監視されないデータのリークにつながります。 悪意はなく、会社のポリシーには違反していないかもしれませんが、それでも、何が共有されているか監視することは重要です。それによってネットワークがどのように使用され、どのようなデータが外部共有されているかを常に把握できるようになります。

### <a name="the-solution"></a>解決策
Cloud App Security で下記のポリシーをデプロイし、Cloud App Security でガバナンス アクションをデプロイすることにより、ネットワークにおけるファイル共有の詳細を把握し、ガバナンス アクションを展開します。

#### <a name="prerequisites"></a>前提条件

Cloud App Security に、少なくとも 1 つのクラウド アプリを[接続](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。

#### <a name="setting-up-monitoring"></a>監視の設定

1.    ポリシーを作成してファイルを制御する

    1. **[ポリシー]** ページで、[**[ファイル ポリシーの作成]**](data-protection-policies.md) をクリックします。 
    ![ファイル ポリシーの作成](./media/create-file-policy.png)

    2. [**[ポリシー テンプレート]**](policy-template-reference.md) フィールドで、**[PII の入ったファイルがクラウドで検出されました (組み込み DLP エンジン)]** を選択し、**[テンプレートを適用]** をクリックします。 
    ![ファイル ポリシー テンプレート](./media/file-policy-template.png)
    3. 個人情報を含むこうしたファイルの不適切な共有を監視するには、防止するアクセス レベルでフィルターを追加します。たとえば、**アクセス レベルが次と等しい - 外部、パブリック、パブリック (インターネット)**とします。 
     ![ファイル ポリシー フィルター](./media/file-policy-filter.png)

2. 一致を調査する
    
    1. **[ポリシー]** ページで、ポリシー名をクリックして **[ポリシー レポート]** に移動し、そのポリシーにトリガーされた一致を確認します。

    2. 特定の一致をクリックしてファイルのドロワーを開き、一致を調査します。 ドロワーでは、このファイルが一致した他のポリシーおよびコンテンツのスキャン状態が表示され、コンテンツのスキャン状態をクリックするとコンテンツの一致が表示できます。**[コラボレーター]** をクリックしてコラボレーターの一覧を表示でき、ファイルに分類のラベルがあるかどうか表示されます。 **[パス]** を見て、そのファイルの保存場所を確認し、ファイルの使われ方を調べることもできます。
    
    3. 誤検知を見つけた場合は、チェック ボックスをオンにマークして、レポートおよびライブ一致から除外します。 フィードバック機能を使用して、Cloud App Security チームに機能改善要求を知らせることができます。 


#### <a name="validating-your-policy"></a>ポリシーの検証

1. 新しい Word 文書を作成して、「078-05-1120」というテキストを入力します。
2. 次にこのファイルを *test file.docx* として保存し、ドメインの外部のユーザーまたはパブリック URL を使用して共有します。 
3. ポリシー レポートに移動します。 ファイル ポリシーの一致がすぐに表示されます。 
4. 一致をクリックして、ファイルのコンテキストを表示できます。 一致自体は、機密データを保護するようにマスクされます。 

#### <a name="removing-the-risk"></a>リスクの排除

ポリシーを検証し、想定通りに動作するよう微調整したら、次の操作を行います。 
  1. 行の最後にある 3 つのドットをクリックし、関連するガバナンス アクション、たとえば **[Put user in quarantine]** (ユーザー検疫に配置) を選択すると、[ガバナンス アクション](governance-actions.md)を即時に実行できます。

 ![外部自動ガバナンス](./media/auto-gov-external.png)

   2. 検証が完了したら、自動ガバナンス アクションを実行するように設定できます。 たとえば、SharePoint および OneDrive では **[外部ユーザーの削除]** または **[Put in user quarantine]** (ユーザー検疫に配置) 、G Suite および Box では **[外部ユーザーの削除]** と **[パブリック アクセスの削除]** ができます。

  ![自動ガバナンス アクションを適用](./media/apply-automatic-gov-actions.png)

## <a name="files-shared-publicly-and-labeled-as-confidential"></a>ファイルがパブリックに共有され、機密情報とラベル付けされている

この使用ケースは、Office 365、G Suite、Box、Dropbox、Salesforce に適用されます。

この使用ケースでは、Cloud App Security と Azure Information Protection の統合を活用します。 組織全体で Azure Information Protection を実行していて、Azure Information Protection のラベルでファイルにラベル付けしてある場合は、Cloud App Security を使用してラベル付与後のファイルに対する動作を監視および制御できます。

## <a name="the-threat"></a>脅威の内容

データを保護する必要があることは理解しており、すでに苦労して Azure Information Protection でファイルを分類しました。 しかし分類した後は、そのファイルがどこにあり、誰がそれを見ているか、どうやったらわかるのでしょうか。 

## <a name="the-solution"></a>解決策
 Cloud App Security を使用して、分類されたこれらのファイルがクラウド内にあるときに監視できます。 これによって、**機密情報** (またはその他の機密性の高い分類) として分類したデータが不適切に共有されないことを確実にできます。以下のポリシーとガバナンス アクションを展開して、Cloud App Security に Azure Information Protection で分類したファイルを監視および管理させます。

### <a name="prerequisites"></a>前提条件

- Cloud App Security に、少なくとも 1 つのクラウド アプリを[接続](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。
- [Azure Information Protection の統合の手順](azip-integration.md)に従って、自動スキャンを有効にします。

### <a name="setting-up-monitoring"></a>監視の設定

1. ポリシーを作成してデータを制御する    
    
    1. **[ポリシー]** ページで、[**[ファイル ポリシーの作成]**](data-protection-policies.md) をクリックします。 

    2.    [フィルター] セクションで、**[アクセス レベル]** および **[最終変更]** のフィルターを削除して、このポリシーをクラウド内のすべてのファイルで実行することができます。 これらのフィルターは、この時点から変更されたファイルにのみ適用されます。 **[分類ラベル]** フィルターと **[が次と等しい]** を選択し、自分の組織の分類ラベルを選択します。 
    
    ![ファイル ポリシー分類ラベル](./media/file-policy-class-label.png)

    3.    こうした分類されたファイルの不適切な共有を監視するには、防止するアクセス レベルでフィルターを追加します。たとえば、**アクセス レベルが次と等しい - パブリック、パブリック (インターネット)**とします。  ポリシーを開始すると、Cloud App Security が既存ファイルや新たに追加したファイルをスキャンするのに時間が必要です。 クラウド内にあるデータの量に応じて、スキャンが完了するまでに時間がかかることがあります。

    ![ファイル ポリシー パブリック フィルター](./media/file-policy-filter-public.png)

2. 一致を調査する

    1. ポリシー名をクリックして **[ポリシー レポート]** ページに移動し、そのポリシーにトリガーされた一致を確認します。
    
    2. 特定の一致をクリックしてファイルのドロワーを開き、一致を調査します。 ドロワーでは、このファイルに設定された分類のラベルおよびこのファイルが一致した他のポリシーを確認でき、**[コラボレーター]** をクリックするとコラボレーターの一覧を表示できます。 **[パス]** を見て、そのファイルの保存場所を確認し、ファイルの使われ方を調べることもできます。
      
    3. 誤検知を見つけた場合は、チェック ボックスをオンにマークして、レポートおよびライブ一致から除外します。 フィードバック機能を使用して、Cloud App Security チームに機能改善要求を知らせることができます。 


### <a name="validating-your-policy"></a>ポリシーの検証

1. 新しい Word 文書を作成し、Azure Information Protection のツール バーを使用して**社外秘**などの秘密度ラベルを設定します。 

2. クラウド アプリにファイルをアップロードし、パブリック URL を使用して共有します。 

3. **[ポリシー レポート]** に移動します。 ファイル ポリシーの一致がすぐに表示されます。 

4. ファイルをクリックして **[ファイル ドロワー]** を開くと、分類ラベルを表示することができます。 


#### <a name="removing-the-risk"></a>リスクの排除

ポリシーを検証し、想定通りに動作するよう微調整したら、次の操作を行います。 

1. 行の最後にある 3 つのドットをクリックし、関連するガバナンス アクション、たとえば **[Put in user quarantine]** (ユーザー検疫に配置) を選択すると、[ガバナンス アクション](governance-actions.md)を即時に実行できます。
    
2. 検証が完了したら、自動ガバナンス アクションを実行するように設定できます。 たとえば、SharePoint および OneDrive では **[Put in user quarantine]** (ユーザー検疫に配置) 、G Suite および Box では **[パブリック アクセスの削除]** ができます。
 
 ![自動ガバナンス アクション - パブリック アクセスの削除](./media/gov-action-public-access.png)

## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  