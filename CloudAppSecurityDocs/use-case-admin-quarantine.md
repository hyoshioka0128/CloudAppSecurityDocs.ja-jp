---
title: Cloud App Security 管理者検疫によるファイルの保護
description: このチュートリアルでは、管理者検疫を使用してデータ侵害を制御するシナリオについて説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 7/30/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 83bb7ac4d1b75a98f426f97f09d6019befc221ad
ms.sourcegitcommit: 288c279a0d2dd62a8ad8d7425c3e9e98857bf5f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2020
ms.locfileid: "80666422"
---
# <a name="tutorial-protect-files-with-admin-quarantine"></a>チュートリアル:管理者検疫によるファイルの保護

*適用対象:Microsoft Cloud App Security*

[ファイル ポリシー](data-protection-policies.md)は、情報保護ポリシーに対する脅威を検出するための優れたツールです。 たとえば、ユーザーが機密情報、クレジット カード番号、サード パーティの ICAP ファイルをクラウドに格納した場所を見つけるファイル ポリシーを作成します。

このチュートリアルでは、Microsoft Cloud App Security を使用して、クラウドに格納された脆弱性をもたらす望ましくないファイルを検出し、早急に対処してそれらを中断させ、**管理者検疫**を使用して脅威を引き起こすそれらのファイルをロックし、クラウド内のファイルの保護、問題の修復、今後のリークの発生の防止を行う方法について説明します。

> [!div class="checklist"]
>
> * 検疫のしくみを理解する
> * 管理者検疫を設定する

## <a name="understand-how-quarantine-works"></a>検疫のしくみを理解する

>[!NOTE]
>
> * 管理者検疫をサポートするアプリの一覧については、[ガバナンス アクション](governance-actions.md)の一覧を参照してください。
> * SharePoint または OneDrive 内のファイルがマルウェアとして検出された場合、それは Cloud App Security ポータルで検疫されません。
> * ラベルの付いたファイルは検疫できません。

1. ファイルがポリシーに一致すると、ファイルに対して **[管理者検疫]** オプションを使用できるようになります。

2. ファイルを検疫するために、次のいずれかのアクションを行います。

    * **[管理者検疫]** アクションを手動で適用します。

    ![検疫アクション](media/quarantine-action.png)

    * これをポリシーの自動検疫アクションとして設定します。

    ![自動で検疫](media/quarantine-automated.png)

3. **[管理者検疫]** が適用されると、バックグラウンドで次の処理が行われます。

    1. 元のファイルが、設定した管理者検疫フォルダーに移動されます。
    2. 元のファイルが削除されます。
    3. 元のファイルの場所に、廃棄標識ファイルがアップロードされます。

    ![検疫の廃棄標識](media/quarantine-tombstone.png)

    4. ユーザーは、廃棄標識ファイルにしかアクセスできません。 ユーザーはこのファイルで、ファイルを解放するための IT によって提供されるカスタム ガイドラインと、IT に提供する関連付け ID を確認できます。

4. ファイルが検疫されたことを示すアラートを受け取ったら、Cloud App Security の **[アラート]** ページでそのファイルを調査します。

    ![検疫のアラート](media/quarantine-alerts.png)

5. また、 **[検疫済み]** タブの**ポリシー レポート**でも調査します。

    ![検疫のレポート](media/quarantine-report.png)

6. ファイルが検疫されたら、次のプロセスを使用して、脅威のある状況を修復します。

    1. SharePoint Online 上の検疫済みフォルダーでそのファイルを調べます。
    2. 監査ログを参照して、ファイルのプロパティを詳細に調べることもできます。
    3. ファイルが企業のポリシーに違反していることがわかった場合は、組織のインシデント応答 (IR) プロセスを実行します。
    4. ファイルが無害であることがわかった場合は、検疫からそのファイルを復元できます。 その時点で元のファイルは解放されます。つまり、元の場所にコピーされ、廃棄標識が削除され、ユーザーがファイルにアクセスできるようになります。

      ![検疫の復元](media/quarantine-restore.png)

7. ポリシーがスムーズに実行されることを検証します。 次に、ポリシーの自動ガバナンス アクションを使用して今後のリークを防止し、ポリシーが一致したときに自動的に管理者検疫を適用することができます。

> [!NOTE]
> ファイルを復元した場合:
>
> * 元の共有は復元されず、既定のフォルダー継承が適用されます。
> * 復元されたファイルには、最新のバージョンのみが含まれます。
> * 検疫フォルダーのサイト アクセス管理は、お客様の責任です。

## <a name="set-up-admin-quarantine"></a>管理者検疫を設定する

1. 侵害を検出するファイル ポリシーを設定します。 このような種類のポリシーの例を次に示します。

    - SharePoint Online の分類ラベルなど、メタデータのみのポリシー
    - クレジット カード番号を検索するポリシーなど、ネイティブ DLP ポリシー
    - Vontu を検索するポリシーなど、ICAP サードパーティ ポリシー

2. 検疫の場所を設定します。
   1. Office 365 SharePoint または OneDrive for Business では、設定するまで、ポリシーの一部として管理者検疫にファイルを配置することはできません: ![検疫の設定](media/quarantine-warning.png)

      管理者検疫を設定するには、設定の歯車の下で **[設定]** に移動します。 検疫済みファイル用の場所と、ユーザーのファイルが検疫されたときにそのユーザーが受け取るユーザー通知を指定します。
      ![検疫の設定](media/quarantine-settings.png)

   2. Box では、検疫フォルダーの場所とユーザー メッセージをカスタマイズすることはできません。 フォルダーの場所は、Box を Cloud App Security に接続した管理者のドライブです。ユーザー メッセージは次のようになります:このファイルは会社のセキュリティとコンプライアンスのポリシーに違反している可能性があるため、管理者のドライブに隔離されました。 サポートが必要であれば、IT 管理者にお問い合わせください。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)]
