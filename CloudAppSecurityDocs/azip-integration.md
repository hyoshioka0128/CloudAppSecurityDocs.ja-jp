---
title: Azure Information Protection を Cloud App Security と統合する
description: この記事では、Cloud App Security で Azure Information Protection タグを活用して、組織のクラウドアプリの使用状況をさらに制御する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/09/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b32007479ece2828cc13376f88188bfdc08ade7c
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666461"
---
# <a name="azure-information-protection-integration"></a>Azure Information Protection の統合

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security を使用すると、ファイルポリシーのガバナンスアクションとして、Azure Information Protection 分類ラベルを保護の有無にかかわらず、ファイルに自動的に適用することができます。 また、Cloud App Security ポータル内で適用された分類ラベルをフィルター処理してファイルを調査することもできます。 分類を使用すると、クラウド内の機微なデータの可視性と制御を向上させることができます。 Azure Information Protection と Cloud App Security の統合は、1つのチェックボックスをオンにするだけで簡単に行うことができます。

> [!NOTE]
> この記事は[、office 365 のセキュリティとコンプライアンスセンターの分類ラベル](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels)を既に移行している場合に、office 365 の統合された秘密度ラベルにも関連しています。 既存の分類ラベルを移行せず、Office 365 のセキュリティとコンプライアンスセンターで新しいラベルの作成を開始した場合、Cloud App Security は Azure Information Protection ポータルで構成された既存のラベルのみを使用します。

Azure Information Protection を Cloud App Security に統合することによって、次のような、クラウド内のサービスとセキュリティで保護されたファイルの両方の機能を使用できます。

- 特定のポリシーに一致するファイルに分類ラベルをガバナンスアクションとして適用する機能
- 1か所に分類されたすべてのファイルを表示する機能
- 分類レベルに従って調査を行い、クラウドアプリケーションの機密データの公開を定量化する機能
- ポリシーを作成して、分類されたファイルが適切に処理されていることを確認する機能

> [!NOTE]
> この機能を有効にするには、Cloud App Security ライセンスと Azure Information Protection Premium P1 のライセンスの両方が必要です。 両方のライセンスが配置されるとすぐに、Cloud App Security は Azure Information Protection サービスから組織ラベルを同期します。

## <a name="prerequisites"></a>前提条件

- Azure Information Protection 統合を使用するには、 [Office 365 用のアプリコネクタ](connect-office-365-to-microsoft-cloud-app-security.md)を有効にする必要があります。

Cloud App Security でラベルを使用するには、ラベルをポリシーの一部として公開する必要があります。 Azure Information Protection を使用している場合は、Azure Information Protection ポータルを使用してラベルを発行する必要があります。 統合ラベルに移行した場合は、Office 365 のセキュリティとコンプライアンスセンターを使用してラベルを発行する必要があります。

Cloud App Security は、次のファイルの種類の Azure Information Protection 分類ラベルの適用を現在サポートしています。

- Word: .docm、.docx、normal.dotm、.dotx
- Excel: xlam、.xlsm、.xlsx、xlam
- PowerPoint: potm、potx、ppsx、ppsm、ppsm、.pptx
- PDF
  > [!NOTE]
  > PDF の場合は、統合ラベルを使用する必要があります。

この機能は現在、Box、G Suite、SharePoint Online、および OneDrive for Business に格納されているファイルで使用できます。 今後のバージョンでは、より多くのクラウドアプリがサポートされる予定です。

Cloud App Security の外部で保護付きでラベル付けされたファイルは、Cloud App Security では変更できません。 ただし、[保護されたファイルのコンテンツを検査](content-inspection.md#content-inspection-for-protected-files)するアクセス許可を付与することで、これらのファイルをスキャンできます。

## <a name="how-it-works"></a>しくみ

[Azure Information Protection](https://docs.microsoft.com/azure/information-protection/what-is-information-protection)では、ファイル分類ラベルについてよく理解しているでしょう。 Cloud App Security に Azure Information Protection 分類タグが表示されます。 Cloud App Security を Azure Information Protection と統合するとすぐに、Cloud App Security は次のようにファイルをスキャンします。

1. Cloud App Security は、テナントで使用されているすべての分類ラベルの一覧を取得します。 この操作は、リストを最新の状態に保つために1時間ごとに実行されます。

2. Cloud App Security は、次のようにファイルをスキャンして分類ラベルを検索します。

    - 自動スキャンを有効にした場合、新規または変更されたすべてのファイルがスキャンキューに追加され、既存のすべてのファイルとリポジトリがスキャンされます。
    - 分類ラベルを検索するようにファイルポリシーを設定した場合、これらのファイルは分類ラベルのスキャンキューに追加されます。

3. 前述のように、これらのスキャンは最初のスキャンで検出された分類ラベルを対象としており、テナントで使用されている分類ラベルを確認するために Cloud App Security します。 外部ラベル、テナントの外部のユーザーによって設定された分類ラベルは、分類ラベルの一覧に追加されます。 スキャンしない場合は、[**このテナントから Azure Information Protection の分類ラベルをスキャン**する] チェックボックスをオンにします。

4. Cloud App Security で Azure Information Protection を有効にすると、接続されているクラウドアプリに追加されたすべての新しいファイルの分類ラベルがスキャンされます。

5. 分類ラベルを自動的に適用する Cloud App Security 内に新しいポリシーを作成できます。

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Azure Information Protection を Cloud App Security と統合する方法
  
### <a name="enable-azure-information-protection"></a>Azure Information Protection を有効にする

Azure Information Protection を Cloud App Security と統合するために必要な作業は、1つのチェックボックスをクリックすることだけです。 自動スキャンを有効にすると、ポリシーを作成しなくても、Office 365 ファイルで Azure Information Protection 分類ラベルを検索できるようになります。 これを有効にすると、クラウド環境内に Azure Information Protection 分類ラベルのラベルが付いたファイルがある場合は、Cloud App Security に表示されます。

分類ラベルに対してコンテンツ検査が有効になっているファイルを Cloud App Security でスキャンするには、次のようにします。

1. Cloud App Security の設定歯車の下にある **[システム]** 見出しの下にある **[設定]** ページを選択します。

    ![[設定] メニュー](media/azip-system-settings.png)
1. **Azure Information Protection**で、**Azure Information Protection の分類ラベルのファイルを自動的にスキャンする** を選択します。

    ![azure information protection を有効にする](media/enable-azip.png)

Azure Information Protection を有効にすると、分類ラベルのあるファイルを表示し、Cloud App Security のラベルごとにフィルター処理できます。 Cloud App Security がクラウドアプリに接続されたら、Azure Information Protection 統合機能を使用して Cloud App Security ポータルに Azure Information Protection 分類ラベルを適用することができます。これには、ファイルに直接追加するか、ガバナンスアクションとして分類ラベルを自動的に適用するようにファイルポリシーを構成します。

> [!NOTE]
> 自動スキャンでは、変更されるまで、既存のファイルはスキャンされません。 Azure Information Protection 分類ラベルの既存のファイルをスキャンするには、コンテンツ検査を含む**ファイルポリシー**が少なくとも1つ必要です。 設定がない場合は、新しい**ファイルポリシー**を作成し、 **[検査方法]** の **[組み込み DLP]** を選択します の下にあるすべてのプリセットフィルターを削除します。 **[コンテンツ検査]** フィールドで、 **[事前設定された式に一致するファイルを含める]** を選択し、定義済みの値を選択して、ポリシーを保存します。 これにより、Azure Information Protection 分類ラベルを自動的に検出するコンテンツ検査が有効になります。

#### <a name="set-internal-and-external-tags"></a>内部タグと外部タグを設定する

既定では、Cloud App Security は、組織内で定義された分類ラベルと、他の組織で定義されている外部のラベルをスキャンします。 

組織の外部に設定されている分類ラベルを無視するには、Cloud App Security ポータルで [**設定**と**Azure Information Protection**] を開きます。 **このテナントからの Azure Information Protection 分類ラベルとコンテンツ検査の警告については、[ファイルのスキャンのみ**] を選択します。

![ラベルを無視する](media/azip-ignore.png)

### <a name="apply-labels-directly-to-files"></a>ファイルにラベルを直接適用する

1. **[調査]** の **[ファイル]** ページで、保護するファイルを選択します。 ファイルの行の末尾にある3つの点をクリックし、 **[分類ラベルの適用]** を選択します。  

    ![アプリの保護](media/protect-app.png)
  
    >[!NOTE]
    > Cloud App Security は、50 MB までのファイルに Azure Information Protection 適用できます。

2. ファイルに適用する組織の分類ラベルの1つを選択し、 **[適用]** をクリックするように求められます。

    ![保護の分類ラベル](media/protect-template.png)

3. 分類ラベルを選択して [適用] をクリックすると、Cloud App Security によって分類ラベルが元のファイルに適用されます。

4. **[分類ラベルの削除]** オプションを選択して分類ラベルを削除することもできます。

> [!NOTE]
> ラベルを削除できるのは、保護が含まれておらず、Information Protection に直接適用されたラベルではなく Cloud App Security 内から適用された場合のみです。

Cloud App Security と Azure Information Protection を連携させる方法の詳細については、「[ユーザーのミスからデータを保護](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake)する」を参照してください。

### <a name="automatically-label-files"></a>ファイルに自動的にラベルを付ける

分類ラベルをファイルに自動的に適用するには、ファイルポリシーを作成し、 **[分類ラベルの適用]** をガバナンスアクションとして設定します。

ファイルポリシーを作成するには、次の手順に従います。

1. ファイルポリシーを作成します。
2. 検出するファイルの種類を含めるようにポリシーを設定します。 たとえば、 **[アクセスレベル]** が **[内部]** ではなく、**所有者 OU**が財務チームと等しいすべてのファイルを選択します。
3. 関連するアプリの ガバナンスアクション で、**分類ラベルの適用** をクリックし、ラベルの種類を選択します。

    ![ラベルの適用](media/aip-gov-action.png)

> [!NOTE]
> ファイル ポリシーを介して、Azure Information Protection のラベルを自動的に適用する機能は強力です。 お客様が多数のファイルに誤ってラベルを適用することを防ぐための安全策として、アプリごと、テナントごとに 1 日に実行できる**ラベルの適用**操作は 100 回に制限されています。 1 日の上限に達すると、ラベルの適用操作は一時的に停止し、翌日 (UTC 12 時 00分 を過ぎてから) に自動的に再開します。 テナントの上限を引き上げるには、サポートチケットを開きます。

### <a name="control-file-exposure"></a>ファイルの露出の制御

- たとえば、次のような場合は、Azure Information Protection 分類ラベルでラベル付けしたドキュメントが表示されます。

    ![サンプル Azure Information Protection 画面](media/azip-screen.png)

- このドキュメントは、 **[ファイル]** ページの Azure Information Protection の分類ラベルに基づいてフィルター処理することで、Cloud App Security で確認できます。

    ![Cloud App Security Azure Information Protection と比較](media/cas-compared-azip.png)

- これらのファイルとその分類ラベルの詳細については、「ファイルドロアー」を参照してください。 **[ファイル]** ページで関連するファイルをクリックし、分類ラベルがあるかどうかを確認します。

    ![ファイルドロワー](media/azip-file-drawer.png)

- その後、Cloud App Security でファイルポリシーを作成して、不適切に共有されているファイルを制御したり、ラベル付けされ、最近変更されたファイルを検索したりすることができます。

- 分類ラベルを特定のファイルに自動的に適用するポリシーを作成できます。
- また、ファイル分類に関連するアクティビティのアラートをトリガーすることもできます。

> [!Note]
> ファイルで Azure Information Protection ラベルを無効にすると、無効になっているラベルが Cloud App Security で無効として表示されます。 削除されたラベルは表示されません。

**サンプルポリシー-Box で外部共有されている機密データ:**

1. ファイルポリシーを作成します。
2. ポリシーの名前、重要度、およびカテゴリを設定します。
3. Box で外部共有されているすべての機密データを検索するには、次のフィルターを追加します。

    ![機密性ポリシー](media/azip-confidentiality-policy.png)

**サンプルポリシー-SharePoint の Finance フォルダー以外で最近変更されたデータ:**

1. ファイルポリシーを作成します。
2. ポリシーの名前、重要度、およびカテゴリを設定します。
3. 次のフィルターを追加して、[フォルダーの選択] オプションの Finance フォルダーを除外した状態で、最近変更されたすべての制限されたファイルを検索します。

    ![制限付きデータポリシー](media/azip-restricted-data-policy.png)

また、アラートやユーザー通知を設定したり、これらのポリシーに対して直ちにアクションを実行したりすることもできます。
[ガバナンスアクション](governance-actions.md)の詳細についてはこちらをご覧ください。

[Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection)の詳細については、Azure Information Protection[クイックスタートチュートリアル](https://docs.microsoft.com/information-protection/get-started/infoprotect-quick-start-tutorial)をご覧ください。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>関連ビデオ

> [!div class="nextstepaction"]
> [Cloud App Security + Azure Information Protection 統合](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations)  

[!INCLUDE [Open support ticket](includes/support.md)]
