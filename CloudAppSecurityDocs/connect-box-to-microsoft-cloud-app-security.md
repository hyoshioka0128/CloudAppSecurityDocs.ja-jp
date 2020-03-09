---
title: Box を Cloud App Security に接続
description: この記事では、使用状況を表示および制御するために、API コネクタを使用して Cloud App Security に Box アプリを接続する方法について説明します。
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
ms.openlocfilehash: e9a2a4ecc10506a992ba4e01ad4fac09eef37275
ms.sourcegitcommit: c303acdcb251c9b15930ab9ed701ab32dcaa6053
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2020
ms.locfileid: "78927943"
---
# <a name="connect-box-to-microsoft-cloud-app-security"></a>Box を Microsoft Cloud App Security に接続

*適用対象: Microsoft Cloud App Security*

この記事では、アプリコネクタ Api を使用して Microsoft Cloud App Security を既存の Box アカウントに接続する手順について説明します。 この接続を使用すると、Box の使用状況を表示したり制御したりできます。 Cloud App Security 保護する方法の詳細については、「 [Protect box](protect-box.md)」を参照してください。

## <a name="how-to-connect-box-to-cloud-app-security"></a>Box を Cloud App Security に接続する方法

> [!NOTE]
> 管理者アカウントではないアカウントを使用してデプロイすると、API テストでエラーが発生し、Cloud App Security が Box 内のすべてのファイルをスキャンできなくなります。 この問題が発生した場合は、すべての特権がオンになっている共同管理者と共にをデプロイできますが、API テストは引き続き失敗し、Box の他の管理者が所有するファイルはスキャンされません。

1. アプリケーションのアクセス許可のアクセスを制限する場合は、次の手順に従います。 それ以外の場合は、手順 2. に進みます。

    1. Box アカウントに管理者アカウントでサインインします。
    1. [**アプリ** > **カスタムアプリ** > **設定**] をクリックします。

         ![box アプリ](media/box-apps.png "box アプリ")

    1. [発行されていない**アプリを既定で無効にする**] が選択されている場合は、[次**を除く**] テキストボックスに Cloud App Security API キーを追加します。

         |データセンター|Cloud App Security API キー|
         |----|----|
         |US1|`nduj1o3yavu30dii7e03c3n7p49cj2qh`|
         |米国|`w0ouf1apiii9z8o0r6kpr4nu1pvyec75`|
         |US3|`dmcyvu1s9284i2u6gw9r2kb0hhve4a0r`|
         |EU1|`me9cm6n7kr4mfz135yt0ab9f5k4ze8qp`|
         |EU2|`uwdy5r40t7jprdlzo85v8suw1l4cdsbf`|

        次に、 **[保存]** をクリックします。 接続している Cloud App Security データセンターを確認する方法については、「[データセンターを表示](network-requirements.md#view-your-data-center)する」を参照してください。

        ![box の設定 (を除く)](media/box-settings-except-for.png)

        > [!NOTE]
        > 既存の Ad合金 m のお客様で、コンソールの URL が Ad合金 m 用であり、Cloud App Security ていない場合は、このアプリのシリアル番号: `bwahmilhdlpbqy2ongkl119o3lrkoshc`を使用します。

2. Cloud App Security ポータルで、 **[調査]** 、 **[接続さ]** れたアプリ の順にクリックします。

3. **[アプリコネクタ]** ページで、プラス記号ボタンをクリックし、 **[Box]** を選択します。

    ![接続ボックス](media/connect-box.png "接続ボックス")

4. [ **Box の設定]** ポップアップで、 **[次のリンクに従う]** をクリックします。

5. ボックスのサインインページが開きます。 チームの Box アプリへの Cloud App Security アクセスを許可するための資格情報を入力します。

6. チーム情報、アクティビティログへの Cloud App Security アクセスを許可し、チームメンバーとしてアクティビティを実行できるようにするかどうかを確認するメッセージが表示されます。 続行するには、 **[許可]** をクリックします。

7. Cloud App Security ポータルに戻ると、Box が正常に接続されたことを示すメッセージが表示されます。

8. **[API のテスト]** をクリックして、正常に接続されたことを確認します。

    テストには数分かかる場合があります。 成功通知を受信したら、 **[閉じる]** をクリックします。

Box が Cloud App Security に接続されました。

Box に接続すると、接続の60日前にイベントを受け取ります。

Box を接続すると、Cloud App Security はフルスキャンを実行します。 ファイルとユーザーの数によっては、フルスキャンの完了にしばらく時間がかかることがあります。 ほぼリアルタイムのスキャンを有効にするために、アクティビティが検出されたファイルはスキャンキューの先頭に移動されます。 たとえば、編集、更新、または共有されたファイルは、通常のスキャンプロセスを待機するのではなく、すぐにスキャンされます。 ほぼリアルタイムのスキャンは、本質的に変更されていないファイルには適用されません。 たとえば、表示、プレビュー、印刷、またはエクスポートされたファイルは、定期的にスケジュールされているスキャンの一部としてスキャンされます。

アプリの接続で問題が発生した場合は、「[アプリコネクタのトラブルシューティング](troubleshooting-api-connectors-using-error-messages.md)」を参照してください。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

[!INCLUDE [Open support ticket](includes/support.md)]
