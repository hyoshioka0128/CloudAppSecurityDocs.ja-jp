---
title: Cloud App Security との Azure Information Protection の統合 | Microsoft ドキュメント
description: この記事では、Cloud App Security で Azure Information Protection タグを使って、組織のクラウド アプリの使用をより強力に制御する方法について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 7/2/2018
ms.topic: article
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 8168319a-199f-4e6c-ad68-e0f236480803
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 2e81d57768f552f5564e35733f5a09ca17f9217c
ms.sourcegitcommit: 9d2a34a2d4145b39d855dd6f596c0fc858b92f9b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37340058"
---
*適用対象: Microsoft Cloud App Security*


# <a name="azure-information-protection-integration"></a>Azure Information Protection の統合

Microsoft Cloud App Security を利用すれば、ファイル ポリシーのガバナンス アクションとして Azure Information Protection 分類ラベルをファイルに自動的に適用できます。保護は適用することも、適用しないこともできます。 その適用した分類ラベルを Cloud App Security ポータル内でフィルター処理して、ファイルを詳しく調べることもできます。 処理後、クラウドに置いてある機密データが確認しやすくなり、管理しやすくなります。 Cloud App Security への Azure Information Protection の統合は、1 つのチェックボックスを選択するだけで簡単に行うことができます。 

Azure Information Protection を Cloud App Security に統合すると、両方のサービスの全機能を活用し、クラウド内のファイルをセキュリティで保護することができます。
- 特定のポリシーに一致するファイルにガバナンス アクションとして分類ラベルを適用する機能
- 1 つの場所にある分類されたファイルをすべて表示する機能
- 分類レベルに従って調査を実行し、クラウド アプリケーション経由で機密データの公開を定量化する機能
- 分類されたファイルが適切に処理されていることを確認するためのポリシーを作成する機能


> [!NOTE] 
> この機能を有効にするには、Cloud App Security ライセンスと Azure Information Protection の Premium P2 のライセンスの両方が必要です。 両方のライセンスが配置されるとすぐに、Cloud App Security は Azure Information Protection サービスから組織ラベルを同期します。


## <a name="prerequisites"></a>前提条件

- Azure Information Protection の統合を行うには、[Office 365 用アプリ コネクタ](connect-office-365-to-microsoft-cloud-app-security.md)を有効にする必要があります。

Cloud App Security では現在、次の種類のファイルに Azure Information Protection 分類ラベルを適用できます。

- Word: docm、docx、dotm、dotx
- Excel: xlam、xlsm、xlsx、xltx
- PowerPoint: potm、potx、ppsx、ppsm、pptm、pptx
- PDF は、今後のバージョンで対応する予定です。 

この機能は現在、Box、G Suite、SharePoint Online、OneDrive for Business に格納されているファイルで使用できます。 今後のバージョンで、さらに多くのクラウド アプリがサポートされるようになります。

Cloud App Security の外で、保護されてラベルが付けられたファイルは、現在 Cloud App Security ではスキャンしたり変更したりすることができません。 Cloud App Security の外で (保護なしで) ラベルが付けられたファイルはスキャンできます。Cloud App Security は、Cloud App Security ポリシーに定義されているように、(保護ありまたは保護なしで) 別のラベルを適用できます。


## <a name="how-it-works"></a>しくみ
[Azure Information Protection](https://docs.microsoft.com/information-protection/) のファイル分類ラベルについてはよくご存知なのではないでしょうか。 Cloud App Security で Azure Information Protection 分類タグを表示することができます。 Cloud App Security を Azure Information Protection と統合するとすぐに、次のように Cloud App Security でファイルがスキャンされます。

1. Cloud App Security は、テナントで使用されているすべての分類ラベルの一覧を取得します。 一覧を最新の状態に保つために、この処理は 1 時間に 1 回実行されます。

2. 次に、Cloud App Security は、ファイルをスキャンして分類タグを探します。

   1. 自動スキャンを有効にした場合 (以下参照)、すべての新しいファイルや変更されたファイルはスキャン キューに追加され、すべての既存のファイルおよびリポジトリはスキャン、分類、保護されます。
   2. 分類ラベルを検索するようにファイル ポリシー (下記参照) を設定すると、該当するファイルが分類ラベル用のスキャン キューに追加されます。

3. 前述のように、これらのスキャンは、Cloud App Security が最初に実行するスキャンで検出された分類ラベルを対象とするものであり、テナントで使用されている分類ラベルを確認することができます。 外部ラベル (テナントの部外者によって設定された分類ラベル) も分類ラベルの一覧に追加されます。 これらをスキャンしない場合は、**[Only scan files for Azure Information Protection classification labels from this tenant]\(このテナントからの Azure Information Protection 分類ラベルのファイルのみをスキャンする\)** チェックボックスをオンにします (下記参照)。

4. Cloud App Security 上で Azure Information Protection を有効にすると、Office 365 に追加されたすべての新しいファイルについても分類ラベルがスキャンされます。

5. 分類ラベルを自動的に適用する新しいポリシーを Cloud App Security 内で作成できます。

## <a name="how-to-integrate-azure-information-protection-with-cloud-app-security"></a>Azure Information Protection を Cloud App Security に統合する方法
  
### <a name="enable-azure-information-protection"></a>Azure Information Protection を有効にする

Cloud App Security に Azure Information Protection を統合する上で必要な操作: Office 365 ファイルの Azure Information Protection 分類ラベルを検索できるようにするための自動スキャンを有効にするだけです。ポリシーを作成する必要はありません。 自動スキャンを有効にすると、Azure Information Protection 分類ラベルでラベル付けされたファイルがクラウド環境内にある場合、Cloud App Security にそれらのファイルが表示されます。

Cloud App Security で、分類ラベルを対象にしたコンテンツ検査を有効にしてファイルをスキャンするには、次の手順に従います。

1. Cloud App Security の設定歯車で、**[全般設定]** ページを選択します。
2. Azure Information Protection で、**「Automatically scan files for Azure Information Protection classification labels」** (Azure Information Protection 分類ラベルについてファイルを自動的にスキャンする) を選択します。 

Azure Information Protection を有効にすると、Cloud App Security 内で分類ラベルのあるファイルを表示し、ラベルごとにフィルターを適用できるようになります。 Cloud App Security がクラウド アプリに接続されたら、Cloud App Security の Azure Information Protection 統合機能を利用し、Azure Information Protection ラベルを Cloud App Security ポータルで直接 (保護ありまたは保護なしで) 適用できます。ファイルに直接追加するか、ガバナンス アクションとして分類ラベルを自動適用するようにファイル ポリシーを構成できます。


 ![Azure Information Protection を有効にする](./media/enable-azip.png)

> [!NOTE] 
> 自動スキャンは、もう一度変更されるまでは既存のファイルをスキャンしません。 Azure Information Protection の分類ラベルの既存のファイルをスキャンするには、少なくとも 1 つの**コンテンツ検査ファイル ポリシー**が必要になります。 1 つもない場合は、新しい**ファイル ポリシー**を作成し、すべてのプリセット フィルターを削除してから、**[コンテンツ検査]** オプションを確認します。 次に、**[コンテンツ検査]** の **[プリセットの式と一致するファイルを含む]** をクリックし、定義済みの値を選択してから、ポリシーを保存します。 これにより、Azure Information Protection の分類ラベルを自動的に検出するコンテンツ検査が有効になります。

#### <a name="set-internal-and-external-tags"></a>内部タグおよび外部タグを設定する
既定では、Cloud App Security は、自分の組織内で定義された分類ラベルだけでなく、他の組織で定義された外部の分類ラベルもスキャンします。 


組織の部外者によって設定された分類ラベルを無視するには、Cloud App Security ポータルの **[Azure security settings (Azure セキュリティ設定)]** の **[全般設定]** で、**[Ignore Azure Information Protection classification labels from other tenants (他のテナントからの Azure Information Protection 分類ラベルを無視する)]** を選択します。
 
![ラベルを無視する](./media/azip-ignore.png)

### <a name="apply-labels-directly-to-files"></a>ファイルにラベルを直接適用する

1. **[ファイル]** ページで、保護するファイルを選択して、ファイルの行の最後にある 3 つのドットをクリックし、**[分類ラベルの適用]** を選択します。

   ![アプリの保護](./media/protect-app.png)
  
   >[!NOTE]
   > Cloud App Security は、最大 50 MB のファイルに Azure Information Protection を適用できます。  

2. ファイルに適用する組織の分類ラベルを選択し、**[適用]** をクリックします。 
   ![保護の分類ラベル](./media/protect-template.png)

3. 分類ラベルを選択して [適用] をクリックすると、Cloud App Security によって分類ラベルが元のファイルに適用されます。

4. 分類ラベルは削除することもできます。**[分類ラベルの削除]** オプションを選択してください。 


Cloud App Security と Azure Information Protection の連動のしくみの詳細については、「[ユーザーのミスからデータを保護](https://docs.microsoft.com/enterprise-mobility-security/solutions/protect-data-user-mistake)」をご覧ください。

### <a name="automatically-label-files"></a>ラベル ファイルを自動的に適用する

分類ラベルを自動的に適用できます。ファイル ポリシーを作成し、ガバナンス アクションとして **[分類ラベルの適用]** を設定します。

指示に従って、ファイル ポリシーを作成します。

1. ファイル ポリシーを作成します。
2. 検出するファイルの種類など、ポリシーを設定します。たとえば、**[アクセス レベル]** が **[内部]** ではないすべてのファイルや **[所有者 OU]** が財務チームではないすべてのファイルを検出します。 
3. 関連アプリのガバナンス アクションの下で**分類ラベルを適用**し、ラベルの種類を選択します。

   ![ラベルを適用する](./media/aip-gov-action.png)

> [!NOTE]
> ファイル ポリシーを介して Azure Information Protection のラベルを自動的に適用する機能は、強力な機能です。 多数のファイルにラベルを誤って適用することを防ぐための安全対策として、各テナントでアプリごとに 1 日に実行できる**ラベルの適用**アクションに 100 回という上限があります。 1 日の上限に達すると、ラベルの適用アクションは一時的に停止し、次の日 (UTC 12:00 を過ぎた時点) になると自動的に続行します。 テナントの上限を引き上げるには、[Cloud App Security のサポートにお問い合わせ](mailto:cascoresupport@microsoft.com)ください。

### <a name="control-file-exposure"></a>ファイルの公開を制限する

- Azure Information Protection 分類ラベルでラベル付けしたドキュメントである場合:

   ![Azure Information Protection 画面サンプル](./media/azip-screen.png)

- Cloud App Security の **[ファイル]** ページで、分類ラベルにフィルターを適用するとこのファイルを確認できます。

   ![Cloud App Security と Azure Information Protection の比較](./media/cas-compared-azip.png)

- **[ファイル]** ページで関連ファイルをクリックしてファイル ドロワーでこれらのファイルとその分類ラベルに関する詳細を取得したり、分類ラベルが含まれているかどうかを確認したりすることができます。

   ![ファイル ドロワー](./media/azip-file-drawer.png)

- Cloud App Security 内でファイル ポリシーを作成することで、不適切に共有されているファイルの制御、およびラベル付けされており最近変更されたファイルの検索を行うことができます。
- また、分類されたファイルに関連するアクティビティでアラートをトリガーできます。

  ![Cloud App Security における Azure Information Protection タグ](./media/azip-tags-in-cas.png)

- 特定のファイルに分類ラベルを自動的に適用するポリシーを作成することもできます。


> [!Note]
> Azure Identity Protection ラベルがファイルで無効になると、無効になったラベルは Cloud App Security でも無効と表示されます。 削除されたラベルは表示されません。


**サンプル ポリシー - Box で外部共有されている機密データ:**

1.  ファイル ポリシーを作成します。
2.  ポリシーの名前、重要度、カテゴリを設定します。
3.  Box で外部共有されている機密データをすべて検索する、以下のフィルターを追加します。

![機密性ポリシー](./media/azip-confidentiality-policy.png) 

**サンプル ポリシー - SharePoint の Finance フォルダー以外にある最近変更された制限付きのデータ:**

1.  ファイル ポリシーを作成します。
2.  ポリシーの名前、重要度、カテゴリを設定します。
3.  最近変更された制限付きデータをすべて検索する以下のフィルターを追加して、フォルダー選択オプションで Finance フォルダーを除外します。 
 
![制限付きデータのポリシー](./media/azip-restricted-data-policy.png) 

これらのポリシーについて、アラートやユーザー通知を設定するか、すぐに対処することもできます。
詳細については、[ガバナンス アクション](governance-actions.md)に関するページを参照してください。

[Azure Information Protection](https://docs.microsoft.com/information-protection/understand-explore/what-is-information-protection) で詳細を確認するとともに、Azure Information Protection の[クイック スタート チュートリアル](https://docs.microsoft.com/information-protection/get-started/infoprotect-quick-start-tutorial)もご覧ください。


 
## <a name="related-videos"></a>関連ビデオ  
[Cloud App Security と Azure Information Protection の統合](https://channel9.msdn.com/Shows/Microsoft-Security/MCAS--AIP-Integrations)  

## <a name="see-also"></a>参照  
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
