---
title: "検出されたアプリのブロック | Microsoft Docs"
description: "このトピックでは、検出されたアプリのブロック スクリプトをエクスポートする手順について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 2/21/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: e451031e-4764-411a-b366-73a49d4f25df
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: ca4a10f64429c481f49c75740f651302b1c7d1ef
ms.sourcegitcommit: 7493d88e4fe7c827f870b81e2090ffcc77f1408a
translationtype: HT
---
# <a name="governing-discovered-apps"></a>検出されたアプリを管理する
Cloud App Security では、既存のオンプレミスのセキュリティ アプライアンスを活用することで、承認されていないアプリへのアクセスをブロックすることができます。 専用のブロック スクリプトを生成して、アプライアンスにインポートします。
このソリューションでは、組織のすべての Web トラフィックをプロキシにリダイレクトする必要はありません。


## <a name="export-a-block-script-to-govern-discovered-apps"></a>ブロック スクリプトをエクスポートして検出されたアプリを管理する

1. Cloud Discovery ダッシュボードで、ブロックするすべてのアプリに **[承認されていない]** のタグを付けます。

   ![[承認されていない] のタグを付ける](./media/tag-as-unsanctioned.png)  

2. タイトル バーで&3; つのドットをクリックして **[Generate block script... (ブロック スクリプトの生成...)]** を選択します。 

   ![ブロック スクリプトを生成する](./media/generate-block-script.png)  

3. **[Generate block script (ブロック スクリプトの生成)]** で、ブロック スクリプトを生成するアプライアンスを選択します。 

   ![ブロック スクリプトのポップ アップを生成する](./media/generate-block-script-popup.png)  

4. 次に [スクリプトの生成] ボタンをクリックします。 これにより、承認されていないすべてのアプリのブロック スクリプトが作成されます。 既定では、エクスポートされた日付と選択したアプライアンス タイプを基にファイルの名前が付けられます (例: *2017-02-19_CAS_Fortigate_block_script.txt*) 

   ![ブロック スクリプトのボタンを生成する](./media/generate-block-script-button.png)  

5. アプライアンスに作成されたファイルをインポートします。



## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  