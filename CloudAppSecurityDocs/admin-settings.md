---
title: 管理者の基本設定を設定する - Cloud App Security | Microsoft Docs
description: この記事では、Cloud App Security で管理者の基本設定を設定する方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/10/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9f687be6ba51bf7d1fb64803aaabd8397de02db7
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720824"
---
# <a name="admin-user-settings"></a>管理者ユーザー設定

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security では、ご利用の管理者ユーザー設定をカスタマイズすることができます。 通知設定により、管理者はアラートに対して電子メールまたはテキスト通知のいずれの受信を希望するかを指定できます。

## <a name="Adminsettings"></a>管理者の設定をカスタマイズする

Microsoft Cloud App Security の管理者としての設定をセットアップする場合、ポータルのメニュー バーでユーザー名をクリックしてから **[ユーザー設定]** を選択し、次の項目を設定します。

1. **[アカウント設定]** をクリックします。 ここで、Cloud App Security ポータルにアクセスするためのパスワードを設定または更新できます。

    ![カスタムユーザー設定](media/custom-user-settings.png "カスタム ユーザー設定")

2. **[通知]** をクリックすると、システムから送信される電子メールやテキスト通知の受信設定を変更できます。  重要度を設定して、電子メールで受信するアラートや違反を決めることができます。 重大度はポリシーごとに設定されます。 違反がトリガーされると、ここでの設定および違反が発生したポリシー内の重大度設定に基づいて、電子メール通知が届きます。 電子メールは、Cloud App Security へのサインインに使用する管理者のユーザー アカウントに関連付けられたエイリアスに送信されます。 電話番号を入力してアラートや通知が送信された場合に Cloud App Security からテキスト メッセージを受信できるようにし、テキスト メッセージで通知を受信する重要度レベルを設定します。

    > [!NOTE]
    > テキスト メッセージで送信されるアラートの最大数は、1 つの電話番号につき 1 日あたり 10 件です。 日は UTC タイム ゾーンに従って計算されます。

    ![通知の設定](media/notification-settings.png "通知の設定")

3. 完了したら **[保存]** をクリックします。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Cloud Discovery のセットアップ](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
