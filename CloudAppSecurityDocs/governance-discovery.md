---
title: 検出されたアプリのブロック - Cloud App Security | Microsoft Docs
description: この記事では、検出されたアプリのブロック スクリプトをエクスポートする手順について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/12/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: bc95cb2272d996752c60c49c7f7402550325b208
ms.sourcegitcommit: 6fd61d5f0953a5c1fc752091203b7dd0712f0cb3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2019
ms.locfileid: "75333267"
---
# <a name="govern-discovered-apps"></a>検出されたアプリの管理

*適用対象: Microsoft Cloud App Security*

環境内で検出されたアプリの一覧を確認したら、次の方法で安全な**アプリ (承認** **済み) を**承認するか、望ましくないアプリを禁止することで、環境をセキュリティで保護することができます。

## <a name="BKMK_SanctionApp"></a> アプリの承認/非承認

特定の危険なアプリを非承認にすることができます。それには、行の終わりにある 3 つの点をクリックします。 次に、 **[Unsanction]\(非承認\)** を選択します。 アプリを却下しても使用がブロックされることはありませんが、Cloud Discovery フィルターで使用状況を監視する作業が簡単になります。 非承認にしたアプリのユーザーに通知し、代わりに安全なアプリの使用を提案できます。

![[承認されていない] のタグを付ける](media/tag-as-unsanctioned.png)

承認または非承認にするアプリが一覧になっている場合、チェックボックスを使用して管理するアプリを選択してから、アクションを選択します。

承認されていないアプリの一覧を照会するには、[Cloud App Security API を使用してブロック スクリプトを生成](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script)します。

> [!NOTE]
> テナントが Microsoft Defender Advanced Threat Protection (ATP)、Zscaler NSS、または iboss を使用している場合は、承認されていないものとしてマークしたすべてのアプリが Cloud App Security によって自動的にブロックされ、ブロックしているスクリプトの作成に関する以下のセクションは不要です。 詳細については、「 [Microsoft DEFENDER ATP との統合](wdatp-integration.md)」、「 [Zscaler と](zscaler-integration.md)の統合」、および「 [iboss との](iboss-integration.md)統合」を参照してください。

## <a name="export-a-block-script-to-govern-discovered-apps"></a>ブロック スクリプトをエクスポートして検出されたアプリを管理する

Cloud App Security では、既存のオンプレミスのセキュリティ アプライアンスを使用することで、承認されていないアプリへのアクセスをブロックすることができます。 専用のブロック スクリプトを生成して、アプライアンスにインポートできます。 このソリューションでは、組織のすべての Web トラフィックをプロキシにリダイレクトする必要はありません。

1. Cloud Discovery ダッシュボードで、ブロックするすべてのアプリに **[承認されていない]** のタグを付けます。

    ![[承認されていない] のタグを付ける](media/tag-as-unsanctioned.png)

2. タイトル バーで 3 つのドットをクリックして **[Generate block script... (ブロック スクリプトの生成...)]** を選択します。

    ![ブロック スクリプトを生成する](media/generate-block-script.png)

3. **[Generate block script (ブロック スクリプトの生成)]** で、ブロック スクリプトを生成するアプライアンスを選択します。

    ![ブロック スクリプトのポップ アップを生成する](media/generate-block-script-popup.png)

4. その後、[スクリプトの生成] ボタンをクリックして、承認されていないすべてのアプリに対してブロック スクリプトを作成します。 既定では、エクスポートされた日付と選択したアプライアンス タイプを基にファイルの名前が付けられます。 *2017-02-19_CAS_Fortigate_block_script.txt* はファイル名の例です。

   ![ブロック スクリプトのボタンを生成する](media/generate-block-script-button.png)

5. アプライアンスに作成されたファイルをインポートします。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
