---
title: Cloud App Security で OAuth アプリを制御するポリシーを作成する
description: この記事では、Microsoft Cloud App Security でアプリのアクセス許可ポリシーを作成して使用する手順について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 11/27/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9d007c4760ace7a4337e4738406016576fa04171
ms.sourcegitcommit: 4f3883a9e85d0aaf2802b10433b221c3f1838d88
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/13/2020
ms.locfileid: "79285306"
---
# <a name="oauth-app-policies"></a>OAuth アプリのポリシー

*適用対象: Microsoft Cloud App Security*

お使いの環境に接続されている[oauth アプリの既存の調査](manage-app-permissions.md)に加えて、アクセス許可ポリシーをに設定して、oauth アプリが特定の条件を満たしたときに自動通知を受け取るようにすることができます。 たとえば、高いアクセス許可レベルを必要とし、50 人を超えるユーザーによって承認されたアプリがある場合、自動的にアラートを受け取ることができます。

OAuth アプリポリシーを使用すると、各アプリが要求したアクセス許可と、Office 365、G Suite、Salesforce に対してユーザーが承認したユーザーを調べることができます。 これらのアクセス許可は、承認済みまたは禁止済みとしてマークすることもできます。 禁止済みとしてマークすると、承認したユーザーごとに各アプリのアクセス許可が取り消されます。

## <a name="create-a-new-oauth-app-policy"></a>新しい OAuth アプリポリシーを作成する

新しい OAuth アプリポリシーを作成するには、次の2つの方法があります。 最初の方法は**調査**対象であり、2番目の方法は**制御**下にあります。

新しい OAuth アプリポリシーを作成するには:

1. **[調査]** で **[OAuth アプリ]** を選択します。

1. 必要に応じてアプリをフィルター処理します。たとえば、**メールボックス内のカレンダーを変更**する**アクセス許可**を要求するすべてのアプリを表示できます。
1. **[検索に基づく新しいポリシー]** ボタンをクリックします。
    検索](media/app-permissions-filter.png) から新しいポリシーを ![する
1. **コミュニティ使用**フィルターを使用して、このアプリに対するアクセス許可を許可するかどうかに関する情報を取得できます。 このフィルターは、まれなアプリがあり、重要度レベルが高い (または多くのユーザーからのアクセス許可を要求する) アクセス許可を要求する場合に役立ちます。
1. アプリを承認したユーザーのグループメンバーシップに基づいてポリシーを設定できます。 たとえば、管理者は、アクセス許可を承認したユーザーが Administrators グループのメンバーである場合にのみ、一般的ではないアプリが高いアクセス許可を要求した場合にそれらを失効させるポリシーを設定することができます。

または、 **[制御]** 、 **[ポリシー]** の順にクリックしてポリシーを作成することもできます。 次に、 **[ポリシーの作成]** 、 **[OAuth アプリポリシー]** の順にクリックします。

   ![新しい OAuth アプリポリシー](media/app-permissions-policy.png)

## <a name="oauth-app-anomaly-detection-policies"></a>OAuth アプリの異常検出ポリシー

作成できる OAuth アプリポリシーに加えて、次のようなすぐに使用できる異常検出ポリシーがあります。これは、悪意のある可能性があるものを識別するために OAuth アプリのメタデータをプロファイルします。

| ポリシー名 | ポリシーの説明 |
| --- | --- |
| 紛らわしい OAuth アプリ名 | 環境に接続されている OAuth アプリをスキャンし、誤った名前のアプリが検出されたときにアラートをトリガーします。 ラテン文字に似た形式でない名前は、悪意のあるアプリを既知の信頼できるアプリとして偽装しようとしている可能性があります。 |
| OAuth アプリの発行者名の誤用 | 環境に接続されている OAuth アプリをスキャンし、発行者名が誤っているアプリが検出されたときにアラートをトリガーします。 ラテン文字に似た外部文字などの正規の発行者名は、信頼されている既知の発行元からのアプリとして悪意のあるアプリを偽装しようとしている可能性があります。 |
| 悪意のある OAuth アプリの同意 | 環境に接続されている OAuth アプリをスキャンし、悪意のある可能性があるアプリが承認されたときにアラートをトリガーします。 悪意のある OAuth アプリは、ユーザーを侵害するために、フィッシングキャンペーンの一部として使用することができます。 この検出では、Microsoft のセキュリティ研究と脅威インテリジェンスの専門知識が利用されて、悪意のあるアプリが特定されます。 |

<!--| Suspicious OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a suspicious name is detected. Suspicious names, such as names of known apps published by unknown publishers, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Non-secure redirect URL is used by an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app uses a non-secure redirect URL (for example, does not use the HTTPS protocol), which exposes sensitive data to interception. |-->

> [!NOTE]
> 異常検出ポリシーは、Azure Active Directory で承認されている OAuth アプリでのみ使用できます。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [データ保護ポリシー](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
