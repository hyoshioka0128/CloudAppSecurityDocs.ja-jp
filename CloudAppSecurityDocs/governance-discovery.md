---
title: 検出されたアプリのブロック | Microsoft Docs
description: この記事では、検出されたアプリのブロック スクリプトをエクスポートする手順について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 11/15/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: e451031e-4764-411a-b366-73a49d4f25df
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7664ad859d0fb069c524b8fa61f5e7c2cbd3b3ec
ms.sourcegitcommit: 79e5aa5a5f90223a5963eb8f6df81a80578e9ce9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2018
ms.locfileid: "51644299"
---
# <a name="govern-discovered-apps"></a>検出されたアプリの管理

*適用対象: Microsoft Cloud App Security*

お使いの環境で検出されたアプリの一覧を確認したら、次の方法で、望ましくないアプリの使用から環境を守ることができます。


## <a name="BKMK_SanctionApp"></a> アプリの承認/非承認 

特定の危険なアプリを非承認にすることができます。それには、行の終わりにある 3 つの点をクリックします。 次に、**[Unsanction]\(非承認\)** を選択します。 アプリを却下しても使用がブロックされることはありませんが、Cloud Discovery フィルターで使用状況を監視する作業が簡単になります。 非承認にしたアプリのユーザーに通知し、代わりに安全なアプリの使用を提案できます。

![[承認されていない] のタグを付ける](./media/tag-as-unsanctioned.png)  

承認または非承認にするアプリが一覧になっている場合、チェックボックスを使用して管理するアプリを選択してから、アクションを選択します。

承認されていないアプリの一覧を照会するには、[Cloud App Security API を使用してブロック スクリプトを生成](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script)します。

> [!NOTE]
> テナントで Zscaler NSS を使用している場合、承認されていないとマークされているアプリはすべて自動的に Cloud App Security によってブロックされます。このため、ブロッキング スクリプトの作成に関する以下のセクションは必要ありません。 詳細については、[Zscaler との統合](zscaler-integration.md)に関するページをご覧ください。

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



## <a name="next-steps"></a>次の手順  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  