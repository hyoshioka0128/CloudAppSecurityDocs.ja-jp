---
title: 検出されたアプリのブロック | Microsoft Docs
description: このトピックでは、検出されたアプリのブロック スクリプトをエクスポートする手順について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: e451031e-4764-411a-b366-73a49d4f25df
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: e6976c39a644fe96f1d9ec431df08c9737026ffd
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143041"
---
*適用対象: Microsoft Cloud App Security*


## <a name="govern-discovered-apps"></a>検出されたアプリの管理

お使いの環境で検出されたアプリの一覧を確認したら、次の方法で、望ましくないアプリの使用から環境を守ることができます。


### <a name="sanctioningunsanctioning-an-app"></a>アプリの承認/非承認 

特定の危険なアプリを非承認にすることができます。行の終わりにある 3 つの点をクリックし、**[Unsanction]** \(非承認\) を選択します。
アプリを却下しても使用がブロックされることはありませんが、Cloud Discovery フィルターで使用状況を監視する作業が簡単になります。 非承認にした後、非承認にしたことをアプリのユーザーに通知し、代わりに安全なアプリの使用を提案できます。

![[承認されていない] のタグを付ける](./media/tag-as-unsanctioned.png)  

承認または非承認にするアプリが一覧になっている場合、チェックボックスを利用し、管理するすべてのアプリを選択し、アクションを選択できます。

承認されていないアプリの一覧を照会するには、[Cloud App Security API を使用してブロック スクリプトを生成](https://mod636914.us.portal.cloudappsecurity.com/api-docs/#generate-block-script)します。

> [!NOTE]
> テナントで Zscaler NSS を使用している場合、承認されていないとマークされているアプリはすべて自動的に Cloud App Security によってブロックされます。このため、ブロッキング スクリプトの作成に関する以下のセクションは必要ありません。 詳細については、[Zscaler との統合](zscaler-integration.md)に関するページをご覧ください。

## <a name="export-a-block-script-to-govern-discovered-apps"></a>ブロック スクリプトをエクスポートして検出されたアプリを管理する

Cloud App Security では、既存のオンプレミスのセキュリティ アプライアンスを活用することで、承認されていないアプリへのアクセスをブロックすることができます。 専用のブロック スクリプトを生成して、アプライアンスにインポートします。
このソリューションでは、組織のすべての Web トラフィックをプロキシにリダイレクトする必要はありません。

1. Cloud Discovery ダッシュボードで、ブロックするすべてのアプリに **[承認されていない]** のタグを付けます。

   ![[承認されていない] のタグを付ける](./media/tag-as-unsanctioned.png)  

2. タイトル バーで 3 つのドットをクリックして **[Generate block script... (ブロック スクリプトの生成...)]** を選択します。 

   ![ブロック スクリプトを生成する](./media/generate-block-script.png)  

3. **[Generate block script (ブロック スクリプトの生成)]** で、ブロック スクリプトを生成するアプライアンスを選択します。 

   ![ブロック スクリプトのポップ アップを生成する](./media/generate-block-script-popup.png)  

4. 次に [スクリプトの生成] ボタンをクリックします。 これにより、承認されていないすべてのアプリのブロック スクリプトが作成されます。 既定では、エクスポートされた日付と選択したアプライアンス タイプを基にファイルの名前が付けられます (例: *2017-02-19_CAS_Fortigate_block_script.txt*) 

   ![ブロック スクリプトのボタンを生成する](./media/generate-block-script-button.png)  

5. アプライアンスに作成されたファイルをインポートします。



## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  