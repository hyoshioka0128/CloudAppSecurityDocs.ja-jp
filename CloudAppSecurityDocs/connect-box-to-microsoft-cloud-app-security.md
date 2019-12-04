---
title: Box を Cloud App Security に接続する
description: この記事では、使用状況を視覚化して制御できるように、API コネクタを使用して Cloud App Security に Box アプリを接続する方法に関する情報を提供します。
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
ms.openlocfilehash: 9bd1b5af5d57327434874d7b7694cea1cad397dc
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720213"
---
# <a name="connect-box-to-microsoft-cloud-app-security"></a>Box を Microsoft Cloud App Security に接続する

*適用対象: Microsoft Cloud App Security*

この記事では、App Connector API を使用して Microsoft Cloud App Security を既存の Box アカウントに接続する方法を説明します。 この接続により、Box の使用状況を視覚化して制御できるようになります。

## <a name="how-to-connect-box-to-cloud-app-security"></a>Box を Cloud App Security に接続する方法

> [!NOTE]
> 管理者アカウントではないアカウントを使用してデプロイすると、API テストでエラーが発生し、Cloud App Security が Box のすべてのファイルをスキャンできません。 この問題が発生する場合は、すべての特権を所有する共同管理者に協力を依頼してデプロイすることができます。しかし、引き続き API テストではエラーが発生し、他の管理者が所有している Box のファイルはスキャンできません。

1. アプリケーションへのアクセス許可を制限する場合は、この手順を実行します。 それ以外の場合は手順 2 に進みます。

    - Box 管理コンソールで設定アイコンをクリックし、次に **[Business settings]\(ビジネス設定\)** または **[エンタープライズ設定]** をクリックします。

         ![box のビジネス設定](media/box-business-settings.png "Box のビジネス設定")

    - **[アプリ]** タブをクリックします。

         ![box アプリ](media/box-apps.png "Box アプリ")

    - **[Unpublished Applications]\(未公開のアプリケーション\)** が選択されている場合は、 **[Except for]\(次を除く\)** テキスト ボックスに Cloud App Security アプリのシリアル番号を追加します。

         |データ センター|Microsoft Cloud App Security のシリアル番号|
         |----|----|
         |US1| `nduj1o3yavu30dii7e03c3n7p49cj2qh`|
         |US2|`w0ouf1apiii9z8o0r6kpr4nu1pvyec75`|
         |US3|`dmcyvu1s9284i2u6gw9r2kb0hhve4a0r`|
         |EU1|`me9cm6n7kr4mfz135yt0ab9f5k4ze8qp`|
         |EU2|`uwdy5r40t7jprdlzo85v8suw1l4cdsbf`|

        次に、 **[保存]** をクリックします。 接続先の Cloud App Security データ センターの確認方法については、「[API トークン](api-tokens.md)」を参照してください。

    ![Box の次を除くの設定](media/box-settings-except-for.png)

    > [!NOTE]
    > 既存の Adallom ユーザーの方でコンソールの URL が Cloud App Security ではなく Adallom のものである場合、このアプリのシリアル番号には bwahmilhdlpbqy2ongkl119o3lrkoshc を使用します。

2. Cloud App Security ポータルで、 **[調査]** 、 **[接続アプリ]** の順にクリックします。

3. **[アプリ コネクター]** ページで、[+]、 **[Box]** の順にクリックします。

    ![接続ボックス](media/connect-box.png "Box を接続する")

4. **[Box の設定]** ポップアップで、 **[リンクに移動]** をクリックします。

5. Box のサインイン ページが開きます。 Cloud App Security がチームの Box アプリにアクセスできるように、資格情報を入力します。

6. Cloud App Security からチームの情報やアクティビティ ログにアクセスし、チーム メンバーと同様にアクティビティを実行することを許可するかどうかを確認するメッセージが Box で表示されます。 続行するには、 **[許可]** をクリックします。

7. Cloud App Security ポータルに戻ると、Box と正常に接続されたことを示すメッセージが届いています。

8. **[API のテスト]** をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。

これで、Box が Cloud App Security に接続されました。

Box を接続すると、接続までの 60 日間のイベントを受け取ります。

Box を接続すると、Cloud App Security がフル スキャンを実行します。 所有するファイルとユーザーの数に応じて、フル スキャンの実行に時間がかかる場合があります。 ほぼリアルタイムのスキャンを有効にするために、アクティビティが検出されたファイルはスキャン キューの先頭に移動されます。 たとえば、編集、更新、または共有するファイルは、通常のスキャン プロセスを待たずにすぐスキャンされます。 ほぼリアルタイムのスキャンは、本質的に変更されていないファイルには適用されません。 たとえば、表示、プレビュー、印刷、またはエクスポートされたファイルは、定期的にスケジュールされたスキャンの一部としてスキャンされます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
