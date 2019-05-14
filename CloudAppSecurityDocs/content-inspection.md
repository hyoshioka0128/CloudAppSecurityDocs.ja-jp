---
title: Cloud App Security でコンテンツの検査を実施する方法
description: この記事では、クラウド内のデータに対して DLP コンテンツ検査を実行する場合に Cloud App Security が従うプロセスについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: rkarlin
ms.date: 1/6/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: c67a387f-8c88-4018-9e80-0fb1455cf768
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: b0fcd13550d62d5ff96462b7d3f9f4a7437c1a44
ms.sourcegitcommit: 9f0c562322394a3dfac7f1d84286e673276a28b1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65568050"
---
# <a name="content-inspection"></a>コンテンツ検査

*適用対象:Microsoft Cloud App Security*


コンテンツ検査を有効にすると、現在の式を使用するか、またはそれ以外のカスタマイズされた式を検索することを選択できます。  

また、正規表現を指定して、結果からファイルを除外することもできます。 このオプションは、内部分類キーワード標準をポリシーから除外する場合に非常に便利です。  
   
ファイルが違反と見なされる前に、一致する必要のあるコンテンツ違反の最小数を設定できます。 たとえば、最低 10 個のクレジット カード番号が検出されたファイルについてアラートを受け取る場合は、10 を選択します。  

選択された式とコンテンツが一致すると、違反テキストが "X" 文字に置き換えられます。 既定では、違反はマスクされており、コンテキストの違反の前後の 100 文字が示されています。 式のコンテキスト内の数字は "#" 文字に置き換えられ、Cloud App Security 内に保存されることはありません。 **[Unmask the last 4 characters of a violation]** \(違反の最後の 4 文字のマスクを解除する) オプションを選択すると、違反自体の最後の 4 文字のマスクを解除することができます。 正規表現で検索するデータ型 (コンテンツ、メタデータ、またはファイル名) を設定する必要があります。 既定では、コンテンツとメタデータが検索されます。 


## <a name="content-inspection-for-protected-files"></a>保護されたファイルのコンテンツ検査

Cloud App Security を利用して、管理者は Cloud App Security のアクセス許可を付与して、暗号化されたファイルの暗号化を解除し、違反についてコンテンツをスキャンできます。

Cloud App Security の必要なアクセス許可を付与するには、次の手順を実行します。

1.  **[設定]**、**[Azure Information Protection]** の順に移動します。
2.  **[保護されたファイルを検査する]** を有効にします。
3. プロンプトに従って Azure Active Directory 内で必要なアクセス許可を付与します。
4. ファイル ポリシーごとに設定を構成して、保護されたファイルをどのポリシーによってスキャンするかを指定できます。



## <a name="next-steps"></a>次の手順
[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
