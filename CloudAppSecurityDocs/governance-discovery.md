---
title: 検出されたアプリのブロック - Cloud App Security | Microsoft Docs
description: この記事では、検出されたアプリのブロック スクリプトをエクスポートする手順について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/06/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 8464851432d8fce81baa624738c6f73da1d68413
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461357"
---
# <a name="govern-discovered-apps"></a>検出されたアプリの管理

*適用対象: Microsoft Cloud App Security*

After you've reviewed the list of discovered apps in your environment, you can secure your environment by approving safe apps (**Sanctioned**) or prohibiting unwanted apps (**Unsanctioned**) in the following ways.

## <a name="BKMK_SanctionApp"></a> アプリの承認/非承認

特定の危険なアプリを非承認にすることができます。それには、行の終わりにある 3 つの点をクリックします。 次に、 **[Unsanction]\(非承認\)** を選択します。 アプリを却下しても使用がブロックされることはありませんが、Cloud Discovery フィルターで使用状況を監視する作業が簡単になります。 非承認にしたアプリのユーザーに通知し、代わりに安全なアプリの使用を提案できます。

![[承認されていない] のタグを付ける](./media/tag-as-unsanctioned.png)

承認または非承認にするアプリが一覧になっている場合、チェックボックスを使用して管理するアプリを選択してから、アクションを選択します。

承認されていないアプリの一覧を照会するには、[Cloud App Security API を使用してブロック スクリプトを生成](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script)します。

> [!NOTE]
> If your tenant uses Zscaler NSS or iboss, any app you mark as unsanctioned is automatically blocked by Cloud App Security, and the following sections regarding creating blocking scripts are unnecessary. For more information, see [Integrating with Zscaler](zscaler-integration.md) and [Integrate Cloud App Security with iboss](iboss-integration.md) respectively.

## <a name="export-a-block-script-to-govern-discovered-apps"></a>ブロック スクリプトをエクスポートして検出されたアプリを管理する

Cloud App Security では、既存のオンプレミスのセキュリティ アプライアンスを使用することで、承認されていないアプリへのアクセスをブロックすることができます。 専用のブロック スクリプトを生成して、アプライアンスにインポートできます。 このソリューションでは、組織のすべての Web トラフィックをプロキシにリダイレクトする必要はありません。

1. Cloud Discovery ダッシュボードで、ブロックするすべてのアプリに **[承認されていない]** のタグを付けます。

    ![[承認されていない] のタグを付ける](./media/tag-as-unsanctioned.png)

2. タイトル バーで 3 つのドットをクリックして **[Generate block script... (ブロック スクリプトの生成...)]** を選択します。

    ![ブロック スクリプトを生成する](./media/generate-block-script.png)

3. **[Generate block script (ブロック スクリプトの生成)]** で、ブロック スクリプトを生成するアプライアンスを選択します。

    ![ブロック スクリプトのポップ アップを生成する](./media/generate-block-script-popup.png)

4. その後、[スクリプトの生成] ボタンをクリックして、承認されていないすべてのアプリに対してブロック スクリプトを作成します。 既定では、エクスポートされた日付と選択したアプライアンス タイプを基にファイルの名前が付けられます。 *2017-02-19_CAS_Fortigate_block_script.txt* はファイル名の例です。

   ![ブロック スクリプトのボタンを生成する](./media/generate-block-script-button.png)

5. アプライアンスに作成されたファイルをインポートします。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
