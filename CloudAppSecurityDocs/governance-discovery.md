---
title: 検出されたアプリのブロック-Cloud App Security |Microsoft Docs
description: この記事では、検出されたアプリのブロックスクリプトをエクスポートする手順について説明します。
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
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285526"
---
# <a name="govern-discovered-apps"></a>検出されたアプリの管理

*適用対象: Microsoft Cloud App Security*

環境内で検出されたアプリの一覧を確認したら、次の方法で安全な**アプリ (承認** **済み) を**承認するか、望ましくないアプリを禁止することで、環境をセキュリティで保護することができます。

## <a name="BKMK_SanctionApp"></a>アプリの承認/却下

行の末尾にある3つのドットをクリックすると、特定の危険なアプリを却下できます。 次に、 **[却下]** を選択します。 却下アプリでは使用をブロックしませんが、Cloud Discovery フィルターでの使用をより簡単に監視できます。 その後、承認されていないアプリのユーザーに通知し、使用するための代替のセーフアプリを提案することができます。

![未承認としてタグ付け](media/tag-as-unsanctioned.png)

承認または却下するアプリの一覧がある場合は、チェックボックスを使用して、管理するアプリを選択し、アクションを選択します。

承認されていないアプリの一覧を照会するには、 [Cloud App Security api を使用してブロックスクリプトを生成](https://us.portal.cloudappsecurity.com/api-docs/#generate-block-script)します。

> [!NOTE]
> テナントが Microsoft Defender Advanced Threat Protection (ATP)、Zscaler NSS、または iboss を使用している場合は、承認されていないものとしてマークしたすべてのアプリが Cloud App Security によって自動的にブロックされ、ブロックしているスクリプトの作成に関する以下のセクションは不要です。 詳細については、「 [Microsoft DEFENDER ATP との統合](wdatp-integration.md)」、「 [Zscaler と](zscaler-integration.md)の統合」、および「 [iboss との](iboss-integration.md)統合」を参照してください。

## <a name="export-a-block-script-to-govern-discovered-apps"></a>ブロックスクリプトをエクスポートして検出されたアプリを管理する

Cloud App Security を使用すると、既存のオンプレミスのセキュリティアプライアンスを使用して、承認されていないアプリへのアクセスをブロックできます。 専用ブロックスクリプトを生成し、それをアプライアンスにインポートすることができます。 このソリューションでは、組織のすべての web トラフィックをプロキシにリダイレクトする必要はありません。

1. Cloud Discovery ダッシュボードで、ブロックするすべてのアプリに対して、承認されていないものとしてタグ**付けします**。

    ![未承認としてタグ付け](media/tag-as-unsanctioned.png)

2. タイトルバーで、3つのドットをクリックし、 **[ブロックスクリプトの生成...]** を選択します。

    ![ブロックスクリプトの生成](media/generate-block-script.png)

3. **[ブロックスクリプトの生成]** で、ブロックスクリプトを生成するアプライアンスを選択します。

    ![ブロックスクリプトポップアップを生成します](media/generate-block-script-popup.png)

4. 次に、[スクリプトの生成] ボタンをクリックして、承認されていないすべてのアプリのブロックスクリプトを作成します。 既定では、ファイルの名前は、エクスポートされた日付と選択したアプライアンスの種類になります。 *2017-02-19_CAS_Fortigate_block_script .txt*はファイル名の例です。

   ![[ブロックスクリプトの生成] ボタン](media/generate-block-script-button.png)

5. 作成したファイルをアプライアンスにインポートします。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
