---
title: Cloud App Security で OAuth アプリを制御するポリシーを作成する
description: この記事では、Microsoft Cloud App Security でアプリのアクセス許可ポリシーを作成し、操作するための手順について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9f68302c-bb3d-450c-bbf5-f8130cb163e3
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 1822ce576b71a196917a3f8d2b94122b88eac163
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461129"
---
# <a name="oauth-app-policies"></a>OAuth アプリに関するポリシー

*適用対象: Microsoft Cloud App Security*

ご利用の環境に接続されている [OAuth アプリの既存の調査](manage-app-permissions.md)に加え、OAuth アプリが特定の条件を満たした場合に自動通知を受け取るようにアクセス許可ポリシーを設定することができます。 たとえば、高いアクセス許可レベルが必要であり、50 人を超えるユーザーによって承認されているアプリがある場合、自動的にアラートを表示させることができます。 

OAuth アプリに関するポリシーでは、Office 365、G Suite、Salesforce について、各アプリで要求されたアクセス許可とそれを承認したユーザーを調査することができます。 これらのアクセス許可は、承認されているものまたは禁止されているものとしてマークすることもできます。 禁止されているものとしてマークすると、アプリを承認した各ユーザーのそれぞれのアプリのアクセス許可が取り消されます。 

## <a name="create-a-new-oauth-app-policy"></a>新しい OAuth アプリ ポリシーを作成する

新しい OAuth アプリ ポリシーを作成するには、2 つの方法があります。 1 番目の方法は **[調査]** の下で行われ、2 番目の方法は **[コントロール]** の下で行われます。 

新しい OAuth アプリ ポリシーを作成するには:

1. **[調査]** で、 **[OAuth アプリ]** を選択します。
2. 必要に応じてアプリをフィルター処理します。たとえば、**メールボックスの予定表を変更**するための**アクセス許可**を要求するすべてのアプリを表示することができます。
3. **[検索に基づく新しいポリシー]** ボタンをクリックします。 
    ![検索に基づく新しいポリシー](./media/app-permissions-filter.png)
4. **[コミュニティの利用状況]** フィルターを使用して、アプリに対するアクセス許可が一般的であるか、一般的でないか、あるいはまれであるかに関する情報を取得することができます。 このフィルターは、珍しいアプリで、重大度レベルが高いアクセス許可か、多くのユーザーからのアクセス許可を要求する場合に便利です。 
5. アプリを承認したユーザーのグループ メンバーシップに基づいてポリシーを設定できます。 たとえば、管理者は、アクセス許可を承認したユーザーが管理者グループのメンバーである場合にのみ、アプリで高いアクセス許可を求める場合に一般的ではないアプリを無効にするポリシーを設定するように決定することができます。

また、 **[コントロール]** 、 **[ポリシー]** の順にクリックして、ポリシーを作成することもできます。 その後、 **[ポリシーの作成]** 、 **[OAuth app policy]\(OAuth アプリ ポリシー\)** の順にクリックします。

   ![新しい OAuth アプリ ポリシー](./media/app-permissions-policy.png)

## <a name="oauth-app-anomaly-detection-policies"></a>OAuth app anomaly detection policies

In addition to OAuth app policies you can create, there are the following out-of-the-box anomaly detection policies that profile metadata of OAuth apps to identify ones that are potentially malicious:

| ポリシー名 | ポリシーの説明 |
| --- | --- |
| Misleading OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a misleading name is detected. Misleading names, such as foreign letters that resemble Latin letters, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Suspicious OAuth app name | Scans OAuth apps connected to your environment and triggers an alert when an app with a suspicious name is detected. Suspicious names, such as names of known apps published by unknown publishers, could indicate an attempt to disguise a malicious app as a known and trusted app. |
| Non-secure redirect URL is used by an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app uses a non-secure redirect URL (for example, does not use the HTTPS protocol), which exposes sensitive data to interception. |
| Misleading publisher name for an OAuth app | Scans OAuth apps connected to your environment and triggers an alert when an app with a misleading publisher name is detected. Misleading publisher names, such as foreign letters that resemble Latin letters, could indicate an attempt to disguise a malicious app as an app coming from a known and trusted publisher. |

> [!NOTE]
> Anomaly detection policies are only available for OAuth apps that are authorized in your Azure Active Directory.

  ## <a name="next-steps"></a>次のステップ 
  [データ保護ポリシー](data-protection-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]