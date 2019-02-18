---
title: レポートを生成する - Microsoft Cloud App Security | Microsoft Docs
description: この記事では、Microsoft Cloud App Security でデータ管理レポートを生成する手順を説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: barbkess
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 0dcc3c35-f787-4822-84c6-d4dff897dd6c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 0f3889a51db5abcf2c4e979456bcb2f01f5bb162
ms.sourcegitcommit: 8ef0438fa35916c48625ff750cb85e9628d202f2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2019
ms.locfileid: "56281204"
---
# <a name="generate-data-management-reports"></a>データ管理レポートを生成する

*適用対象:Microsoft Cloud App Security*

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

[Premier サポートをご利用のお客様は、Premier ポータルから直接新しいサポート要求を作成することもできます。](https://premier.microsoft.com/)  
  
  
