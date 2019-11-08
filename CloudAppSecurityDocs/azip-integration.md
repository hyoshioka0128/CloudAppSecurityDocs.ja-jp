---
title: Azure Information Protection と Cloud App Security を統合する
description: この記事では、Cloud App Security で Azure Information Protection タグを使って、組織のクラウド アプリの使用をより強力に制御する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8168319a-199f-4e6c-ad68-e0f236480803
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: e9f6fe5bd55f94777901748778e40b7e00ba07ae
ms.sourcegitcommit: 1d5e5a5c418d698ba624660abf2873fce47da999
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732009"
---
# <a name="azure-information-protection-integration"></a>Azure Information Protection の統合

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security を利用すれば、ファイル ポリシーのガバナンス アクションとして Azure Information Protection 分類ラベルをファイルに自動的に適用できます。保護は適用することも、適用しないこともできます。 その適用した分類ラベルを Cloud App Security ポータル内でフィルター処理して、ファイルを詳しく調べることもできます。 分類を使用すると、クラウド内の機密データが確認しやすくなり、管理しやすくなります。 Cloud App Security への Azure Information Protection の統合は、1 つのチェックボックスを選択するだけで簡単に行うことができます。

> [!NOTE]
> この記事は[、office 365 のセキュリティとコンプライアンスセンターの分類ラベル](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)を既に移行している場合に、office 365 の統合された秘密度ラベルにも関連しています。 既存の分類ラベルを移行せず、Office 365 のセキュリティとコンプライアンスセンターで新しいラベルの作成を開始した場合、Cloud App Security は Azure Information Protection ポータルで構成された既存のラベルのみを使用します。

Azure Information Protection を Cloud App Security に統合すると、両方のサービスの全機能を使用して、クラウド内のファイルをセキュリティで保護することができます。

- 特定のポリシーに一致するファイルにガバナンス アクションとして分類ラベルを適用する機能
- 1 つの場所にある分類されたファイルをすべて表示する機能
- 分類レベルに従って調査し、クラウド アプリケーション経由での機密データの公開を定量化する機能
- 分類されたファイルが適切に処理されていることを確認するためのポリシーを作成する機能

> [!NOTE]
> この機能を有効にするには、Cloud App Security ライセンスと Azure Information Protection の Premium P1 のライセンスの両方が必要です。 両方のライセンスが配置されるとすぐに、Cloud App Security は Azure Information Protection サービスから組織ラベルを同期します。

## <a name="prerequisites"></a>必要条件

- Azure Information Protection の統合を行うには、[Office 365 用アプリ コネクタ](connect-office-365-to-microsoft-cloud-app-security.md)を有効にする必要があります。

Cloud App Security でラベルを使用するには、ラベルをポリシーの一部として公開する必要があります。 Azure Information Protection を使用している場合は、Azure Information Protection ポータルを使用してラベルを発行する必要があります。 統合ラベルに移行した場合は、Office 365 のセキュリティとコンプライアンスセンターを使用してラベルを発行する必要があります。

Cloud App Security では現在、次の種類のファイルに Azure Information Protection 分類ラベルを適用できます。

- Word: docm、docx、dotm、dotx
- Excel: xlam、xlsm、xlsx、xltx
- PowerPoint: potm、potx、ppsx、ppsm、pptm、pptx
- PDF
    > [!NOTE]
    > PDF の場合は、統合ラベルを使用する必要があります。

現在、この機能は Box、G Suite、SharePoint Online、OneDrive for Business に格納されているファイルで使用できます。 今後のバージョンで、さらに多くのクラウド アプリがサポートされるようになります。

Cloud App Security の外部で保護付きでラベル付けされたファイルは、Cloud App Security では変更できません。 ただし、[保護されたファイルのコンテンツを検査](content-inspection.md#content-inspection-for-protected-files)するアクセス許可を付与することで、これらのファイルをスキャンできます。 Cloud App Security の外で (保護なしで) ラベルが付けられたファイルはスキャンできます。Cloud App Security は、Cloud App Security ポリシーに定義されているように、(保護ありまたは保護なしで) 別のラベルを適用できます。

## <a name="how-it-works"></a>しくみ

[Azure Information Protection](https://docs.microsoft.com/azure/information-protection/what-is-information-protection) のファイル分類ラベルについてはよくご存知なのではないでしょうか。 Cloud App Security で Azure Information Protection 分類タグを表示することができます。 Cloud App Security を Azure Information Protection と統合するとすぐに、次のように Cloud App Security でファイルがスキャンされます。

1. Cloud App Security は、テナントで使用されているすべての分類ラベルの一覧を取得します。 一覧を最新の状態に保つために、このアクションは 1 時間に 1 回実行されます。

2. 次に、Cloud App Security は、ファイルをスキャンして分類タグを探します。

    - 自動スキャンを有効にした場合、すべての新しいファイルや変更されたファイルはスキャン キューに追加され、すべての既存のファイルおよびリポジトリはスキャン、分類、保護されます。
    - 分類ラベルを検索するようにファイル ポリシーを設定すると、該当するファイルが分類ラベル用のスキャン キューに追加されます。

3. 前述のように、これらのスキャンは、Cloud App Security が最初に行うスキャンで検出された分類ラベルを対象とするものであり、テナントで使用されている分類ラベルを確認することができます。 外部ラベル (テナントの部外者によって設定された分類ラベル) も分類ラベルの一覧に追加されます。 これらをスキャンしない場合は、 **[Only scan files for Azure Information Protection classification labels from this tenant \(このテナントからの Azure Information Protection 分類ラベルのファイルのみをスキャンする\)]** チェックボックスをオンにします。

4. Cloud App Security 上で Azure Information Protection を有効にすると、Office 365 に追加されたすべての新しいファイルについて分類ラベルがスキャンされます。

5. 分類ラベルを自動的に適用する新しいポリシーを Cloud App Security 内で作成できます。

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Azure Information Protection を Cloud App Security に統合する方法
  
### <a name="enable-azure-information-protection"></a>Azure Information Protection を有効にする

Azure Information Protection を Cloud App Security に統合するために必要な操作は、1 つのチェックボックスをクリックすることだけです。 自動スキャンを有効にすると、ポリシーを作成しなくても、ご利用の Office 365 ファイルでの Azure Information Protection 分類ラベルの検索が有効になります。 これを有効にすると、Azure Information Protection 分類ラベルでラベル付けされたファイルがクラウド環境内にある場合、Cloud App Security にそれらのファイルが表示されます。

Cloud App Security で、分類ラベルを対象にしたコンテンツ検査を有効にしてファイルをスキャンするには、次の手順に従います。

1. Cloud App Security の設定歯車で、 **[システム]** 見出しの下の **[設定]** ページを選択します。
    ![設定メニュー](./media/azip-system-settings.png)
1. **Azure Information Protection** で、 **[Automatically scan files for Azure Information Protection classification labels]\(Azure Information Protection 分類ラベルについてファイルを自動的にスキャンする\)** を選択します。
    ![Azure Information Protection を有効にする](./media/enable-azip.png)

Azure Information Protection を有効にすると、Cloud App Security 内で分類ラベルのあるファイルを表示し、ラベルごとにフィルターを適用できるようになります。 Cloud App Security がクラウド アプリに接続されたら、Azure Information Protection 統合機能を利用し、Azure Information Protection 分類ラベルを Cloud App Security ポータルで (保護ありまたは保護なしで) 適用できます。ファイルに直接追加するか、ガバナンス アクションとして分類ラベルを自動適用するようにファイル ポリシーを構成できます。

> [!NOTE]
> 自動スキャンは、もう一度変更されるまでは既存のファイルをスキャンしません。 Azure Information Protection 分類ラベルの既存のファイルをスキャンするには、コンテンツ検査を含む**ファイルポリシー**が少なくとも1つ必要です。 設定がない場合は、新しい**ファイルポリシー**を作成し、 **[検査方法]** の **[組み込み DLP]** を選択します の下にあるすべてのプリセットフィルターを削除します。 **[コンテンツ検査]** フィールドで、 **[事前設定された式に一致するファイルを含める]** を選択し、定義済みの値を選択して、ポリシーを保存します。 これにより、Azure Information Protection の分類ラベルを自動的に検出するコンテンツ検査が有効になります。

#### <a name="set-internal-and-external-tags"></a>内部タグおよび外部タグを設定する

既定では、Cloud App Security では、自分の組織内で定義した分類ラベルだけでなく、他の組織で定義した外部の分類ラベルもスキャンされます。 

組織の外部で設定された分類ラベルを無視するには、Cloud App Security ポータル内の **[設定]** と **[Azure Information Protection]** に移動します。 **[Only scan files for Azure Information Protection classification labels and content inspection warnings from this tenant]\(このテナントから Azure Information Protection の分類ラベルとコンテンツ検査の警告に対してのみファイルをスキャンする\)** を選択します。

![ラベルを無視する](./media/azip-ignore.png)

### <a name="apply-labels-directly-to-files"></a>ファイルにラベルを直接適用する

1. **[調査]** の **[ファイル]** ページから、保護するファイルを選択します。 ファイルの行の末尾にある 3 つのドットをクリックし、 **[分類ラベルの適用]** を選択します。  

   ![アプリの保護](./media/protect-app.png)
  
   >[!NOTE]
   > Cloud App Security は、最大 50 MB のファイルに Azure Information Protection を適用できます。  

2. ファイルに適用する組織の分類ラベルを選択し、 **[適用]** をクリックします。
   ![保護の分類ラベル](./media/protect-template.png)

3. 分類ラベルを選択して [適用] をクリックすると、Cloud App Security によって分類ラベルが元のファイルに適用されます。

4. 分類ラベルは削除することもできます。 **[分類ラベルの削除]** オプションを選択してください。

> [!NOTE]
> ラベルを削除できるのは、それが保護を含まず、かつ Cloud App Security 内から適用された場合のみです。Information Protection で直接適用されたラベルは削除できません。

Cloud App Security と Azure Information Protection の連動のしくみの詳細については、「[ユーザーのミスからデータを保護](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake)」をご覧ください。

### <a name="automatically-label-files"></a>ラベル ファイルを自動的に適用する

分類ラベルを自動的に適用できます。ファイル ポリシーを作成し、ガバナンス アクションとして **[分類ラベルの適用]** を設定します。

指示に従って、ファイル ポリシーを作成します。

1. ファイル ポリシーを作成します。
2. 検出するファイルの種類を含めるようにポリシーを設定します。 たとえば、 **[アクセス レベル]** が **[内部]** ではなく、 **[所有者 OU]** が財務チームであるすべてのファイルを選択します。
3. 関連アプリのガバナンス アクションの下で **[分類ラベルの適用]** をクリックし、ラベルの種類を選択します。

   ![ラベルを適用する](./media/aip-gov-action.png)

> [!NOTE]
> ファイル ポリシーを介して Azure Information Protection のラベルを自動的に適用する機能は、強力な機能です。 多数のファイルにラベルを誤って適用することを防ぐための安全対策として、各テナントでアプリごとに 1 日に実行できる**ラベルの適用**アクションに 100 回という上限があります。 1 日の上限に達すると、ラベルの適用アクションは一時的に停止し、次の日 (UTC 12:00 を過ぎた時点) になると自動的に続行します。 テナントの上限を引き上げるには、サポートチケットを開きます。

### <a name="control-file-exposure"></a>ファイルの公開を制限する

- 例: 以下が Azure Information Protection 分類ラベルでラベル付けしたドキュメントである場合:

   ![Azure Information Protection 画面サンプル](./media/azip-screen.png)

- **[ファイル]** ページで Azure Information Protection の分類ラベルでフィルター処理することで、Cloud App Security でこのドキュメントを表示できます。

   ![Cloud App Security と Azure Information Protection の比較](./media/cas-compared-azip.png)

- これらのファイルとその分類ラベルの詳細情報については、ファイル ドロワーで取得できます。 **[ファイル]** ページで関連ファイルをクリックし、分類ラベルが使用されているかどうかを確認します。

   ![ファイル ドロワー](./media/azip-file-drawer.png)

- Cloud App Security 内でファイル ポリシーを作成することで、不適切に共有されているファイルの制御、およびラベル付けされており最近変更されたファイルの検索を行うことができます。

- 特定のファイルに分類ラベルを自動的に適用するポリシーを作成できます。
- また、ファイルの分類に関連するアクティビティでアラートをトリガーすることもできます。

> [!Note]
> Azure Information Protection ラベルがファイルで無効になると、無効になったラベルは Cloud App Security でも無効であると表示されます。 削除されたラベルは表示されません。

**サンプル ポリシー - Box で外部共有されている機密データ:**

1. ファイル ポリシーを作成します。
2. ポリシーの名前、重要度、カテゴリを設定します。
3. Box で外部共有されている機密データをすべて検索する、以下のフィルターを追加します。

![機密性ポリシー](./media/azip-confidentiality-policy.png)

**サンプル ポリシー - SharePoint の Finance フォルダー以外にある最近変更された制限付きのデータ:**

1. ファイル ポリシーを作成します。
2. ポリシーの名前、重要度、カテゴリを設定します。
3. 次のフィルターを追加して、最近変更された制限付きデータをすべて検索します。また、フォルダー選択オプションで Finance フォルダーを除外します。

![制限付きデータのポリシー](./media/azip-restricted-data-policy.png)

これらのポリシーについて、アラートやユーザー通知を設定するか、すぐに対処することもできます。
詳細については、[ガバナンス アクション](governance-actions.md)に関するページを参照してください。

[Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) で詳細を確認するとともに、Azure Information Protection の[クイック スタート チュートリアル](https://docs.microsoft.com/information-protection/get-started/infoprotect-quick-start-tutorial)もご覧ください。

## <a name="related-videos"></a>関連ビデオ

[Cloud App Security と Azure Information Protection の統合](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations)  

## <a name="next-steps"></a>次のステップ

[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)