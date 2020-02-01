---
title: Dropbox を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に Dropbox アプリを接続する方法に関する情報を提供します。
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
ms.openlocfilehash: cc1d0b563d7d155fdd9f0aab55b4fe117ddfd6bc
ms.sourcegitcommit: 00599ac6c64a4c62ed9ebdda3edb58f90f92c24d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912091"
---
# <a name="connect-dropbox-to-microsoft-cloud-app-security"></a>Dropbox を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、コネクタ API を使用して Microsoft Cloud App Security を既存の Dropbox アカウントに接続する方法を説明します。 この接続により、Dropbox の使用状況を視覚化して制御できるようになります。 Cloud App Security が Dropbox を保護する方法については、「 [Protect dropbox](protect-dropbox.md)」を参照してください。

Dropbox ではサインインしなくても共有リンクからファイルにアクセスできるため、Cloud App Security はこのようなユーザーを非認証ユーザーとして登録します。 Dropbox の非認証ユーザーが表示された場合、組織外のユーザーであることを示しているか、あるいは組織内のサインインしていないユーザーと認識されている可能性があります。

## <a name="how-to-connect-dropbox-to-cloud-app-security"></a>Dropbox を Cloud App Security に接続する方法

1. Cloud App Security コンソールで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

2. **[アプリ コネクタ]** ページで、[+] ボタン、 **[Dropbox]** の順にクリックします。

    ![dropbox の接続](media/connect-dropbox.png "Dropbox を接続する")

3. ポップアップで、管理者アカウントの電子メール アドレスを入力します。

4. **[リンクを生成]** をクリックします。

5. **[リンクに移動]** をクリックします。

    Dropbox のサインイン ページが開きます。 Cloud App Security がチームの Dropbox インスタンスにアクセスできるように、資格情報を入力します。

6. Cloud App Security がチームの情報やアクティビティ ログにアクセスし、チーム メンバーと同様にアクティビティを実行することを許可するかどうか確認するメッセージが Dropbox で表示されます。 続行するには、 **[許可]** をクリックします。

7. Cloud App Security コンソールに戻ると、Dropbox が正常に接続されたことを通知するメッセージが届いています。

8. **[API のテスト]** をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。

Dropbox を接続すると、接続までの 60 日間のイベントを受け取ります。

> [!NOTE]
> ファイルを追加する Dropbox のすべてのイベントは、アップロード ファイルとして Cloud App Security に表示され、Cloud App Security に接続された他のすべてのアプリと並べられます。

アプリの接続で問題が発生した場合は、「[アプリコネクタのトラブルシューティング](troubleshooting-api-connectors-using-error-messages.md)」を参照してください。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
