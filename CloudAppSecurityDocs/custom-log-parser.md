---
title: サポートされていないログ用のカスタムログパーサーの Cloud App Security
description: この記事では、カスタム ログ パーサーを使用して、サポートされていないデバイスのログを Cloud App Security にアップロードする方法について説明します。
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
ms.openlocfilehash: 941190ed45518d72dabde02582d0ee19f40f38f5
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719268"
---
# <a name="use-a-custom-log-parser"></a>カスタム ログ パーサーの使用

*適用対象: Microsoft Cloud App Security*

Cloud App Security を使用すると、ログの書式のマッチングと処理を実行するようにカスタム パーサーを構成できるため、Cloud Discovery で使用することができます。 ファイアウォールまたはデバイスが Cloud App Security によって明示的にサポートされていない場合、通常はカスタム パーサーを使用します。 これは、CSV パーサーまたはカスタムのキー値パーサーになります。

カスタム パーサーでこのプロセスに従うと、サポートされていないファイアウォールからログを使用することができます。

カスタム パーサーを構成するには

1. Cloud App Security ポータルで **[探索]** をクリックし、 **[新しいスナップショット レポートの作成]** をクリックします。

    ![新しいスナップショット レポートを作成する](media/create-new-snapshot-report.png)

2. **[レポート名]** と **[説明]** を入力します。

3. **[データ ソース]** で **[Custom log format (カスタム ログの書式)]** を選択します。

    ![新しいスナップショット レポート](media/custom-log-upload.png)

4. 組織のユーザーがインターネット アクセスに使用するファイアウォールとプロキシからログを収集します。 組織内のすべてのユーザー アクティビティを示す、トラフィック ピーク時のログを収集するようにしてください。

5. テキスト エディターで処理するログを開きます。 書式を確認し、ログの列名が **[カスタム ログ形式]** 画面のフィールドに対応することを確認します。

    ![カスタム ログ パーサー](media/log-data.png)

6. 次に、実際のデータに基づいてフィールドに入力し、データのどの列が Cloud App Security の各フィールドに対応するかを示します。 必要に応じて、正しく対応するようにログ ファイルの列名を変更します。

    > [!NOTE]
    > フィールド名は大文字と小文字が区別されます。 Cloud App Security とログ ファイルの列名が同じになるように入力します。 また、選択した日付の書式が同じであることを確認します。

    ![カスタム ログ パーサー](media/custom-log-parser.png)

7. **[Save]** (保存) をクリックします。 構成したカスタム ログの書式は、既定のカスタム パーサーとして保存されます。 いつでも **[編集]** をクリックして編集できます。

8. **[トラフィックのログの選択]** で、変更したログ ファイルを選択してアップロードします。 一度に最大 20 個のファイルをアップロードできます。 圧縮された ZIP 形式のファイルもサポートされます。

9. **[作成]** をクリックします。

10. アップロードが完了すると、ログが正常にアップロードされたことを通知するステータス メッセージが画面右上隅に表示されます。

11. ログ ファイルのアップロード後、ファイルの解析および分析には多少時間がかかります。
    ログ ファイルの処理が完了した後、終了したことを通知する電子メールを受け取ります。

12. **Cloud Discovery ダッシュボード**の上部にあるステータス バーに通知バナーが表示されます。 バナーは、自分のログ ファイルの処理状態で更新されます。
    ![ログ ファイル メニュー バーの処理](media/processing-log-file-menu-bar.png)

13. ログが正常にアップロードされると、ログ ファイルの処理が正常に完了したことを知らせる通知が表示されます。 この時点で、ステータス バーのリンクをクリックするか、設定の歯車アイコンに移動して **[Cloud Discovery の設定]** を選択することで、レポートを表示できます。

    ![Discovery の [設定] タブ](media/discovery-settings-tab.png)
14. **[スナップショット レポートの管理]** を選択し、スナップショット レポートを選択します。

    ![スナップショット レポートの管理](media/snapshot-report-managment.png)

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Cloud Discovery のスナップショット レポートを作成する](create-snapshot-cloud-discovery-reports.md)

> [!div class="nextstepaction"]
> [継続的なレポートのために自動ログ アップロードを構成する](configure-automatic-log-upload-for-continuous-reports.md)

> [!div class="nextstepaction"]
> [Cloud Discovery データでの作業](working-with-cloud-discovery-data.md)

[!INCLUDE [Open support ticket](includes/support.md)]
