---
title: Microsoft Cloud App Security でレポートを生成する方法 | Microsoft Docs
description: このトピックでは、Microsoft Cloud App Security でデータ管理レポートを生成する手順を説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 0dcc3c35-f787-4822-84c6-d4dff897dd6c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 7684e6e3172076d8f7e8a4d69b1ddd70d322a200
ms.sourcegitcommit: 82052a88acbc33893f7b9e0d10cc2e8c652ef003
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349510"
---
*適用対象: Microsoft Cloud App Security*



# <a name="generate-data-management-reports"></a>データ管理レポートを生成する

Microsoft Cloud App Security では、クラウド アプリ内のファイルの概要を提供するレポートを生成することができます。

レポートを生成するには

1. **[ファイル]** に移動します。 
2. 右上隅にある 3 つの点をクリックし、**[データ管理レポート]** の下で以下のいずれかのレポートを選択します。

 ![レポート](./media/reports.png)

## <a name="data-sharing-overview"></a>データ共有の概要 

このレポートには、クラウド アプリに保存されているファイルの数がアクセス許可ごとに表示されます。 クラウド アプリはアクセスが容易でどこからでも利用できるため、ファイルの共有が簡単です。 **個人のファイル**は、その所有者以外とは共有されません。 ファイルが共有されている場合、Cloud App Security は 4 種類の状態に区別します。
- **公開共有 (インターネット)** ファイルは、認証を受けなくても検索エンジンの結果などからアクセスできるファイルです。
 - **公開共有**ファイルは、認証を受けなくてもリンクからアクセスできるファイルです。
 - **外部共有**ファイルは、クラウド アプリの認証を受けると社外のユーザーがアクセスできるファイルです。
- **内部共有**ファイルは、社内のすべてまたは一部のユーザーがアクセスできるファイルです。

## <a name="outbound-sharing-by-domain"></a>ドメイン別の送信共有

このレポートには、従業員が企業ファイルの共有に使用しているドメインのリストが表示されます。 レポートでは、ドメインごとに、どのユーザーがファイルを共有しているかが表示されます。 レポートには、共有されているファイルと、コラボレーター ファイルの共有相手も表示されます。 これらのドメインとの共有を管理することをお勧めします。 共有は、関連する各アプリのページの [ファイル] タブで管理することができます。

## <a name="owners-of-shared-files"></a>共有ファイルの所有者

これには、外部と企業のファイルを共有しているユーザーのリストが表示されます。 外部共有ファイルは、特定の外部の共同作業者と共有されているファイルです。 公開共有ファイルには、プライベート リンクを使用するとインターネット上の誰でもアクセスできます。 これらのファイルは、明示的にリンクを持つユーザーのみが見つけることができます。 公開共有ファイル (インターネット) はインターネット ユーザー全員に公開されていて、検索エンジンの結果からもアクセスできます。 過剰な数のファイルを共有するユーザーが見つかった場合は、その理由を調査することをお勧めします。 調査するには [ファイル] タブを使用し、外部共有の使用状況を詳しく理解するため、該当するユーザーに連絡します。


  
## <a name="next-steps"></a>次の手順 
[制御](control.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  