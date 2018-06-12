---
title: Microsoft Cloud App Security でレポートを生成する方法 | Microsoft Docs
description: このトピックでは、Microsoft Cloud App Security でデータ管理レポートを生成する手順を説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/10/2018
ms.topic: article
ms.prod: ''
ms.app: cloud-app-security
ms.technology: ''
ms.assetid: 0dcc3c35-f787-4822-84c6-d4dff897dd6c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 3265f1fe6d5a75ac65ec89142c571583cb5e098a
ms.sourcegitcommit: 41fbc8e235befd240ad7a1eed52339cfafb5d906
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2018
ms.locfileid: "35251703"
---
*適用対象: Microsoft Cloud App Security*



# <a name="generate-data-management-reports"></a>データ管理レポートを生成する

Microsoft Cloud App Security では、クラウド アプリ内のファイルの概要を提供するレポートを生成することができます。

レポートを生成するには

1. **[ファイル]** に移動します。 
2. 右上隅にある 3 つの点をクリックし、**[データ管理レポート]** の下で以下のいずれかのレポートを選択します。

   ![レポート](./media/reports.png) I
## <a name="data-sharing-overview"></a>データ共有の概要 

これには、クラウド アプリに保存されているファイルの数がアクセス許可ごとに表示されます。 クラウド アプリはアクセスが容易でどこからでも利用できるため、共有が簡単です。 ファイルの所有者以外のユーザーと共有されていないファイルは、プライベート ファイルと呼ばれます。 ファイルが共有されている場合、Cloud App Security は 4 種類の状態に区別します。 <br> - 公開共有 (Web) ファイルは、認証を受けなくても検索エンジンの結果などからアクセスできるファイルです。<br> - 公開共有ファイルは、認証を受けなくてもリンクからアクセスできるファイルです。<br> - 外部共有ファイルは、クラウド アプリの認証を受けると社外のユーザーがアクセスできるファイルです。<br> - 内部共有ファイルは、社内のすべてまたは一部のユーザーがアクセスできるファイルです。

## <a name="outbound-sharing-by-domain"></a>ドメイン別の送信共有

これには、従業員が企業ファイルの共有に使用しているドメインのリストが表示されます。 レポートには、ドメインごとに、そのドメインを使用してファイルを共有している企業ユーザー、共有しているファイル、ファイルの共有相手の共同作業者が含まれます。 これらのドメインを使用した共有は、関連する各アプリのページの [ファイル] タブで管理することをお勧めします。

## <a name="owners-of-shared-files"></a>共有ファイルの所有者

これには、外部と企業のファイルを共有しているユーザーのリストが表示されます。 外部共有ファイルは、特定の外部の共同作業者と共有されています。 公開共有ファイルは、プライベート リンクからアクセスできるインターネット ユーザー全員に公開されています。ただし、明示的に示されているリンクからしかアクセスできません。 公開共有ファイル (インターネット) はインターネット ユーザー全員に公開されていて、検索エンジンの結果からもアクセスできます。 過度な数のファイルを共有しているユーザーを発見した場合、[ファイル] タブを使用して過度な共有アクセス許可の内容を調査し、ユーザーに連絡して外部共有の使用状況の詳細について確認することをお勧めします。


  
## <a name="see-also"></a>参照 
[制御](control.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  