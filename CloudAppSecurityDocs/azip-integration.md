---
title: "Azure Information Protection の統合 | Microsoft Docs"
description: "この記事では、Cloud App Security で Azure Information Protection タグを使って、組織のクラウド アプリの使用をより強力に制御する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/23/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8168319a-199f-4e6c-ad68-e0f236480803
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eceb326c4ab14852ecd284cfbaa0d2eb07149168
ms.openlocfilehash: bf3b2c9fcd374ee9a980d123890b9c78f6fb9e07


---

# <a name="azure-information-protection-integration"></a>Azure Information Protection の統合

Cloud App Security では、Azure Information Protection ファイル ラベルに基づいてファイルの調査およびポリシーの設定を行い、クラウド内の機密データの視認性とコントロールを高めることができます。 そのためには、Cloud App Security でポリシーを設定し、コンテンツ検査を有効にしてファイルをスキャンします。 また、分類されたファイルに関連するアクティビティでアラートをトリガーできます。 Azure Information Protection の統合では、以下のことが可能です。
-   クラウド アプリケーション経由での機密データの公開を数値化する。
-   接続されているクラウド アプリでの分類済みデータのアップロードに関するポリシー、およびアップロード違反に関するアラートを作成する。または、機密データを隔離するか、機密データの外部共有を禁止する。
-   監査証跡を調査し、ポリシーに違反しているファイルを修復する。 

> [!NOTE] 
> 既定では、コンテンツ検査が有効になっていて、ファイルをスキャンするファイル ポリシーがある場合のみ、そのファイルのラベルがスキャンされます。 ファイル ポリシーのないすべてのファイルでラベルをスキャンするには、自動スキャンを有効にしてください。

## <a name="terminology-overview"></a>用語の概要
-   Azure Information Protection の分類ラベル - 組織内のファイルに追加された属性です。追加は、ポリシーに基づいて自動的に行うか、またはエンド ユーザーが手動で設定します。
-   外部 - 組織の部外者によって設定されたタグです。
-   ファイル タグ - Cloud App Security で分類ラベルを表したものです。 このフィールドは、ファイル テーブル内の各ファイルについて表示され、フィルターで使用できます。
-   ファイル ポリシー - ファイル フィルターに基づく一連の規則です。これにより、クラウド プロバイダーの API を利用してさまざまな自動プロセスを適用することができます。

## <a name="license-and-tenant-creation"></a>ライセンスとテナントの作成
この機能を有効にするには、Cloud App Security ライセンスと、Azure Information Protection の Premium P1 または P2 のライセンスの両方が必要です。 両方のライセンスが配置されるとすぐに、Cloud App Security は Azure Information Protection サービスから組織ラベルを同期します。

![AZIP のサンプル画面](./media/azip-screen.png)

![AZIP と CAS の比較](./media/cas-compared-azip.png)
     
さらに、既定では、1 つ以上のファイル ポリシーによるコンテンツ検査の対象となっているファイルも、分類ラベルをスキャンされます。

## <a name="gain-visibility"></a>視認性の向上

ファイルごとにスキャンされたファイル タグは、ファイル ドロワーに表示されます。
**[ファイル]** ページで該当ファイルをクリックすると、ファイル タグの有無を確認できます。

![ファイル ドロワー](./media/azip-file-drawer.png)

タグをクリックすると、タグの詳細を表示したり、タグの一覧を表示することができます。
 
![タグ一覧](./media/azip-tags-list.png)

**ファイル タグ** フィルターを使用して、特定のタグが付けられたファイルを検索できます。
 
![ファイル タグ フィルター](./media/azip-file-tags-filter.png)

また、タグ付けされたファイルすべてを検索することもできます。

![すべてのファイル タグ フィルター](./media/azip-file-tags-all-filter.png)

## <a name="how-it-works"></a>しくみ
Cloud App Security を Azure Information Protection と接続するとすぐに、次のように Cloud App Security でファイルがスキャンされます。
1. テナントで使用されているすべての分類ラベル一覧を取得します。 一覧を最新の状態に保つために、この処理は 1 時間に 1 回実行されます。
2. 分類ラベルのファイルをスキャンします。 この処理は 2 つの方法で実行できます。a. ファイル ポリシーの一部としてコンテンツがスキャンされるファイルは、分類ラベル用のスキャン キューにも追加されます。
    b. ファイル ポリシーを設定することなく、すべてのファイルをスキャン キューに追加するには、自動スキャンを有効にします (下記を参照)。これですべての新規ファイルまたは変更されたファイルがスキャンされます。
3. **[Ignore Azure Information Protection classification labels from other tenants]** (他のテナントからの Azure Information Protection 分類ラベルを無視する) チェック ボックスをオンにしていない場合、外部ラベルが特定のファイルにある場合にのみ、外部ラベルは分類ラベルの一覧に追加されます。

## <a name="enable-automatic-scan"></a>自動スキャンを有効にする
Office 365 内の新しいファイルのファイル タグに対する自動スキャンを有効にするには、次の操作を行います。

1. Office 365 で、**[全般設定]** ページに移動します。
2. [Azure security settings] (Azure セキュリティ設定) で、**[Automatically scan files for Azure Information Protection classification labels] (Azure Information Protection 分類ラベルについてファイルを自動的にスキャンする)** を選択します。 自動スキャンを有効にすると、ファイル ポリシーによるコンテンツ スキャンの対象ファイルだけでなく、Office 365 に追加されるすべての新しいファイルもスキャンされ、ファイル タグが確認されます。

![Azure Information Protection を有効にする](./media/enable-azip.png)
 

## <a name="internal-and-external-tags"></a>内部および外部のタグ
既定では、Cloud App Security は、組織内で定義された分類ラベルだけでなく、他の組織で定義された外部の分類ラベルもスキャンします。 

外部のラベルを無視するには、**[Azure security setting]** (Azure セキュリティ設定) で、**[Ignore Azure Information Protection classification labels from other tenants]** (他のテナントからの Azure Information Protection 分類ラベルを無視する) を選択します。
 
![ラベルを無視する](./media/azip-ignore.png)

> [!Note]
> テスト テナントで作業をしている場合、他のテナントから受信するファイルをテストできるようにするために、外部の分類ラベルは無視しないことをお勧めします。

![Cloud App Security における Azure Information Protection タグ](./media/azip-tags-in-cas.png)

## <a name="use-azure-information-protection-tags-to-apply-control"></a>Azure Information Protection タグを使用してコントロールを適用する
Cloud App Security でファイル ポリシーを作成し、不適切に共有されているファイルと、ラベル付けされており最近変更されたファイルを検索します。 

**ポリシー #1 - Box で外部共有されている機密データ:**

1.  ファイル ポリシーを作成します。
2.  ポリシーの名前、重要度、カテゴリを設定します。
3.  Box で外部共有されている機密データをすべて検索する、以下のフィルターを追加します。

![機密性ポリシー](./media/azip-confidentiality-policy.png) 

**ポリシー #2 - SharePoint の Finance フォルダー以外にある最近変更された制限付きのデータ:**

1.  ファイル ポリシーを作成します。
2.  ポリシーの名前、重要度、カテゴリを設定します。
3.  最近変更された制限付きデータをすべて検索する以下のフィルターを追加して、フォルダー選択オプションで Finance フォルダーを除外します。 
 
![制限付きデータのポリシー](./media/azip-restricted-data-policy.png) 

これらのポリシーについて、アラートやユーザー通知を設定するか、すぐに対処することもできます。
詳細については、[ガバナンス アクション](governance-actions.md)に関するページを参照してください。

[Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-information-protection) で詳細を確認するとともに、Azure Information Protection の[クイック スタート チュートリアル](https://docs.microsoft.com/en-us/information-protection/get-started/infoprotect-quick-start-tutorial)もご覧ください。

  

## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  



<!--HONumber=Nov16_HO5-->


