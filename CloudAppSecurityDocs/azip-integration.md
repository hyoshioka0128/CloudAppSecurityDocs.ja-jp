---
title: "Cloud App Security との Azure Information Protection の統合 | Microsoft ドキュメント"
description: "この記事では、Cloud App Security で Azure Information Protection タグを使って、組織のクラウド アプリの使用をより強力に制御する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/2/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 8168319a-199f-4e6c-ad68-e0f236480803
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b5807498a87c39b54ece698cd5bec10f05b29fe2
ms.sourcegitcommit: f4fcea309a5ba8c99d1dea306abf5bf07649d6fb
translationtype: HT
---
# <a name="azure-information-protection-integration"></a>Azure Information Protection の統合

Cloud App Security では、Azure Information Protection の分類ラベルに基づいてファイルの調査およびポリシーの設定を行い、クラウド内の機密データの視認性とコントロールを高めることができます。 Cloud App Security への Azure Information Protection の統合は、1 つのチェックボックスを選択するだけで簡単に行うことができます。 

Azure Information Protection を Cloud App Security に統合すると、両方のサービスの全機能を活用し、クラウド内のファイルをセキュリティで保護することができます。
- 1 つの場所にある分類されたファイルをすべて表示する機能
- 分類レベルに従って調査を実行し、クラウド アプリケーション経由で機密データの公開を定量化する機能
- 分類されたファイルが適切に処理されていることを確認するためのポリシーを作成する機能

> [!NOTE] 
> この機能を有効にするには、Cloud App Security ライセンスと、Azure Information Protection の Premium P1 または P2 のライセンスの両方が必要です。 両方のライセンスが配置されるとすぐに、Cloud App Security は Azure Information Protection サービスから組織ラベルを同期します。

## <a name="how-it-works"></a>しくみ
[Azure Information Protection](https://docs.microsoft.com/information-protection/) のファイル分類ラベルについてはよくご存知なのではないでしょうか。 Cloud App Security で Azure Information Protection 分類タグを表示することができます。 Cloud App Security を Azure Information Protection と統合するとすぐに、次のように Cloud App Security でファイルがスキャンされます。
1. Cloud App Security は、テナントで使用されているすべての分類ラベルの一覧を取得します。 一覧を最新の状態に保つために、この処理は 1 時間に 1 回実行されます。
2. 次に、Cloud App Security は、ファイルをスキャンして分類タグを探します。 自動スキャン (下記参照) を有効にした場合は、新しいファイルまたは変更されたファイルがすべて、スキャン キューに追加されます。
    b. 分類ラベルを検索するようにファイル ポリシー (下記参照) を設定すると、該当するファイルが分類ラベル用のスキャン キューに追加されます。
3. 前述のように、これらのスキャンは、Cloud App Security が最初に実行するスキャンで検出された分類ラベルを対象とするものであり、テナントで使用されている分類ラベルを確認することができます。 外部ラベル (テナントの部外者によって設定された分類ラベル) も分類ラベルの一覧に追加されます。 外部ラベルをスキャンしない場合は、**[Only scan files for Azure Information Protection classification labels from this tenant (このテナントからの Azure Information Protection 分類ラベルのファイルのみをスキャンする)]** チェックボックスをオンにします (下記参照)。
4. Cloud App Security 上で Azure Information Protection を有効にすると、Office 365 に追加されたすべての新しいファイルについても分類ラベルがスキャンされます。

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Azure Information Protection を Cloud App Security に統合する方法
  
### <a name="enable-azure-information-protection"></a>Azure Information Protection を有効にする

Cloud App Security に Azure Information Protection を統合する上で必要な操作: Office 365 ファイルの Azure Information Protection 分類ラベルを検索できるようにするための自動スキャンを有効にするだけです。ポリシーを作成する必要はありません。 自動スキャンを有効にすると、Azure Information Protection 分類ラベルでラベル付けされたファイルがクラウド環境内にある場合、Cloud App Security にそれらのファイルが表示されます。

Cloud App Security で、分類ラベルを対象にしたコンテンツ検査を有効にしてファイルをスキャンするには、次の手順に従います。

1. Cloud App Security の設定歯車で、[**全般設定**] ページを選択します。
2. Azure Information Protection で、**「Automatically scan files for Azure Information Protection classification labels」** (Azure Information Protection 分類ラベルについてファイルを自動的にスキャンする) を選択します。 

Azure Information Protection を有効にすると、Cloud App Security 内で分類ラベルのあるファイルを表示し、ラベルごとにフィルターを適用できるようになります。

 ![Azure Information Protection を有効にする](./media/enable-azip.png)

> [!NOTE] 
> 自動スキャンは、再度変更されるまでは既存のファイルをスキャンしません。 Azure Information Protection の分類ラベルの既存のファイルをスキャンするには、少なくとも 1 つの**コンテンツ検査ファイル ポリシー**が必要になります。 1 つもない場合は、新しい**ファイル ポリシー**を作成し、すべてのプリセット フィルターを削除してから、[**コンテンツ検査**] オプションを確認します。 次に、[**コンテンツ検査**] の [**プリセットの式と一致するファイルを含む**] をクリックし、定義済みの値を選択してから、ポリシーを保存します。 これで、Azure Information Protection の分類ラベルを自動的に検出するコンテンツ検査が有効になります。

### <a name="set-internal-and-external-tags"></a>内部タグおよび外部タグを設定する
既定では、Cloud App Security は、組織内で定義された分類ラベルだけでなく、他の組織で定義された外部の分類ラベルもスキャンします。 

組織の部外者によって設定された分類ラベルを無視するには、Cloud App Security ポータルの [**Azure security settings (Azure セキュリティ設定)**] の [**全般設定**] で、[**Ignore Azure Information Protection classification labels from other tenants (他のテナントからの Azure Information Protection 分類ラベルを無視する)**] を選択します。
 
![ラベルを無視する](./media/azip-ignore.png)

### <a name="control-file-exposure"></a>ファイルの公開を制限する
- Azure Information Protection 分類ラベルでラベル付けしたドキュメントである場合:

![AZIP のサンプル画面](./media/azip-screen.png)

- Cloud App Security の [**ファイル**] ページで、分類ラベルにフィルターを適用することにより、該当するファイルを確認できるようになります。

![AZIP と CAS の比較](./media/cas-compared-azip.png)

- それらのファイルとその分類ラベルの詳細情報については、ファイル ドロワーで取得できます。

- [**ファイル**] ページで該当ファイルをクリックすると、ファイルに分類ラベルが使用されているかどうかを確認できます。

![ファイル ドロワー](./media/azip-file-drawer.png)

- 分類ラベルをクリックすることにより、詳細情報の確認または分類ラベルの完全な一覧の表示を行うことができます。
 
![タグ一覧](./media/azip-tags-list.png)

- Cloud App Security 内でファイル ポリシーを作成することで、不適切に共有されているファイルの制御、およびラベル付けされており最近変更されたファイルの検索を行うことができます。
- また、分類されたファイルに関連するアクティビティでアラートをトリガーできます。

![Cloud App Security における Azure Information Protection タグ](./media/azip-tags-in-cas.png)

> [!Note]
> Azure Identity Protection ラベルがファイルで無効になると、無効になったラベルは Cloud App Security でも無効であると表示されます。 無効になったラベルは表示されません。


**ポリシー #1 - Box で外部共有されている機密データ:**

1.    ファイル ポリシーを作成します。
2.    ポリシーの名前、重要度、カテゴリを設定します。
3.    Box で外部共有されている機密データをすべて検索する、以下のフィルターを追加します。

![機密性ポリシー](./media/azip-confidentiality-policy.png) 

**ポリシー #2 - SharePoint の Finance フォルダー以外にある最近変更された制限付きのデータ:**

1.    ファイル ポリシーを作成します。
2.    ポリシーの名前、重要度、カテゴリを設定します。
3.    最近変更された制限付きデータをすべて検索する以下のフィルターを追加して、フォルダー選択オプションで Finance フォルダーを除外します。 
 
![制限付きデータのポリシー](./media/azip-restricted-data-policy.png) 

これらのポリシーについて、アラートやユーザー通知を設定するか、すぐに対処することもできます。
詳細については、[ガバナンス アクション](governance-actions.md)に関するページを参照してください。

[Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-information-protection) で詳細を確認するとともに、Azure Information Protection の[クイック スタート チュートリアル](https://docs.microsoft.com/en-us/information-protection/get-started/infoprotect-quick-start-tutorial)もご覧ください。


## <a name="integration-with-azure-rights-management"></a>Azure Rights Management との統合

Cloud App Security と Azure RMS を統合するには、組織は Azure Rights Management のライセンスを持ち、アクティブ化している必要があります。  これら 2 つの異なる手順については、「[Rights Management をアクティブにする](https://docs.microsoft.com/information-protection/deploy-use/activate-service)」を参照してください。

Cloud App Security は現在、汎用的な保護レベルのみをサポートしています。 Office、PDF および画像ファイルのネイティブ保護は、今後のバージョンで提供されます。 

この機能は現在、SharePoint Online と OneDrive for Business に格納されているファイルで使用できます。 今後のバージョンで、さらに多くのクラウド アプリがサポートされるようになります。

Cloud App Security がお使いの Office 365 サービスに接続されると、Cloud App Security RMS 統合機能を使用できるようになります。以下の手順で、Cloud App Security ポータルで直接、RMS でドキュメントを保護することができます。

1. **[ファイル]** ページで、保護するファイルを選択して、ファイルの行の最後にある 3 つのドットをクリックし、**[保護]** を選択します。 
![アプリの保護](./media/protect-app.png)
2. ファイルの保護に使用する組織のテンプレートを選択し、**[保護]** をクリックします。 
![保護テンプレート](./media/protect-template.png)
3. テンプレートを選択して [保護] をクリックすると、Cloud App Security によってテンプレートが適用され、元のファイルを保護します。 保護されたファイルは、元のファイルと同じ名前になりますが、ファイル拡張子が新しく ".pfile" となります。
> [!NOTE]
>     ファイルの元の所有者を含む組織内の全ユーザーがこうしたファイルにアクセスできるように、ファイルには会社全体での RMS テンプレートを適用することをお勧めします。 ファイルが保護されている場合は、ファイルの所有者、ファイルの共有ポリシー、およびアクセス権を既に持っているユーザーの一覧は変わりません。

4. 保護されたファイルにユーザーがアクセスする場合、RMS 共有アプリがユーザーのデバイスにインストールされている必要があります。 詳細については、「[Microsoft Rights Management 共有アプリケーションの技術的概要と保護の詳細](https://docs.microsoft.com/information-protection/rms-client/sharing-app-admin-guide-technical)」を参照してください。

5. この操作は、**ガバナンス ログ**で直前に行った保護操作の行の最後にある **[元に戻す]** ボタンをクリックすると、いつでも元に戻すことができます。 




 
## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
