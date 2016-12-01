---
title: "RegEx エンジンの操作 | Microsoft Docs"
description: "このトピックでは、Cloud App Security ポリシーのパターン マッチングに正規表現を使用する方法について説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: dc8b87e5-e6c1-4a65-ab8c-067fb527fce4
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed4ea71b24767d3602d40894d1cbac7447bcd8a2
ms.openlocfilehash: 77468efb5d4cb62f560c11e624545fc8abe8c99e


---

# <a name="working-with-the-regex-engine"></a>RegEx エンジンの操作
 
Cloud App Security のコンテンツ検査ポリシーでは、パターン マッチングに正規表現が使用されます。 コンテンツ検査は、ファイル ポリシーの一部として適用できます。 正規表現をテストするには、次の Web サイトを使用できます。  
  
-   [http://regexpal.com/](http://regexpal.com/)  
  
     必ず **Case insensitive (大文字と小文字を区別しない)** を選択します。  
  
-   [https://regex101.com/](https://regex101.com/)  
  
     正規表現を詳細に分析できます。  
  
カスタムの正規表現には、次の制限が課せられます。  
  
-   検索では常に大文字と小文字が区別されません。  
   
-   使用できる数量詞: {n, m} n、m < 10  
  
-   すべてのグループは非キャプチャである必要があります。例: (?: xxx)  
  
     (group) の代わりに (?:group) を使用します  
  
-   使用できない数量詞: *、+、{n,}  
  
     * の代わりに {0,9} を使用します  
  
     + の代わりに {1,9} を使用します  
  
-   使用できない逆参照: \\<number\> または \k\<name>  
  
式の例  
  
||||  
|-|-|-|  
|**正規表現**|**データ**|**一致する**|  
|Colou?r (?:black&#124;blue&#124;white)|Color black<br /><br /> Color white<br /><br /> Color red|はい<br /><br /> はい<br /><br /> いいえ|  
|[a-z0-9]{1,9}@[a-z0-9]{1,9}\\.[a-z]{2,3}|Some1@abc.com<br /><br /> user@host.org<br /><br /> @bad.com|はい<br /><br /> はい<br /><br /> いいえ|  
|20\d{2}-(?:0[1-9]&#124;1[0-2])-(?:[0-2][0-9]&#124;30&#124;31)|2015-12-31<br /><br /> 2015-01-09<br /><br /> 1999-12-31|はい<br /><br /> はい<br /><br /> いいえ|  
|d.n't\s{0,10}c.r.|Don't     care<br /><br /> D!n'tcor0<br /><br /> Doesn't care|はい<br /><br /> はい<br /><br /> いいえ|  
 

## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


