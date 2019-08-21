---
title: アラートを自動化してエンドポイントを保護する | Microsoft Docs
description: このチュートリアルでは、Microsoft Flow を使用して Microsoft Defender アクションを実行するための Microsoft Cloud App Security アラートの構成プロセスについて説明します。
author: ShlomoSagir-MS
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: tutorial
ms.date: 8/15/2019
ms.openlocfilehash: bfec590f92172773bf263dbb5b84832329c63488
ms.sourcegitcommit: 12dfc4c0b8d72aad8cfae9c70f0014ca312b9e4e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037426"
---
# <a name="tutorial-automate-alerts-to-protect-endpoints"></a>チュートリアル: アラートを自動化してエンドポイントを保護する

Cloud App Security 単体で、ポリシーを定義するときに、ユーザーの停止やファイルを非公開にするなどの定義済みのガバナンス オプションを提供します。 Cloud App Security コネクタを使用して Microsoft Flow でプレイブックを作成すると、ワークフローを作成してポリシー用にカスタマイズしたエンドポイント アクションを Microsoft Defender Advanced Threat Protection (ATP) を使用して有効にすることができます。 Flow でプレイブックが作成されたら、それを Cloud App Security でポリシーと関連付けて、アラートを Flow に送信するだけです。 Microsoft Flow では、組織用にカスタマイズされたワークフローを作成するために複数のコネクタと条件が用意されています。

Flow の [Cloud App Security コネクタ](https://docs.microsoft.com/connectors/cloudappsecurity/)は、自動化されたトリガーとアクションをサポートします。 Flow は Cloud App Security がアラートを生成するときに自動的にトリガーされます。 アクションには、Cloud App Security でのアラートの状態の変更が含まれます。

このチュートリアルでは、次のアラートを自動化する方法について学習します。

> [!div class="checklist"]
> * Microsoft Defender ATP を使用してウイルス対策スキャンを実行する
> * Microsoft Defender ATP を使用してマシンを分離する

このチュートリアルでは、Microsoft Defender ATP を使用してウイルス対策スキャンを実行するアラートを自動化する手順について説明します。 コンピューターを分離するアラートを自動化する場合は、同じ手順を使用して、ウイルス対策フローと分離フローに入れ替えます。

> [!NOTE]
> これらのフローは、ユーザー アクティビティを含むポリシーにのみ関連します。 たとえば、Discovery や OAuth のポリシーでこれらのフローを使用することはできません。

Flow プランがない場合は、[無料試用版アカウントにサインアップ](https://flow.microsoft.com/pricing)します。

## <a name="prerequisites"></a>必要条件

* 有効な [Microsoft Flow プラン](https://flow.microsoft.com/pricing)が必要
* Flow 環境が Azure AD と同期され、Defender ATP の監視対象で、ドメイン参加済みである

## <a name="run-an-antivirus-scan-using-microsoft-defender-atp"></a>Microsoft Defender ATP を使用してウイルス対策スキャンを実行する

この次の手順では、ウイルス対策スキャンを実行するフローを作成し、これを疑わしい動作を検出するポリシーに追加します。 ユーザーに対して疑わしい動作のアラートが発生すると、侵害されている可能性があるユーザーが使用しているマシンでウイルス対策スキャンを実行するフローがトリガーされます。

### <a name="step-1-create-a-flow-to-run-an-antivirus-scan"></a>手順 1.ウイルス対策スキャンを実行するフローを作成する

> [!NOTE]
> Defender ATP コネクタを使用してフローを作成したことがある場合は、Flow によってコネクタが自動的に再利用されるため、**サインイン**の手順を省略できます。

1. [Microsoft Flow ポータル](https://flow.microsoft.com/)にアクセスし、[テンプレート] を選択してください。
    ![[テンプレート] の選択を示す Flow のメイン ページのスクリーンショット。](media/tutorial-flow-templates.png)
1. "Cloud App Security" を検索し、 **[Run antivirus scan using Windows Defender upon a Cloud App Security alert]\(Cloud App Security アラート時に Windows Defender を使用してウイルス対策スキャンを実行する\)** を選択します。
    ![検索結果を示す Flow のテンプレート ページのスクリーンショット。](media/tutorial-flow-templates-search.png)
1. **[サインイン]** をクリックして Microsoft Defender ATP コネクタで使用する管理者の資格情報を入力します。
    ![サインイン プロセスを示す Flow のテンプレート ページのスクリーンショット。](media/tutorial-flow-templates-signin.png)

> [!TIP]
> このページは後で必要になるため、開いたままにしておいてください。

### <a name="step-2-create-a-cloud-app-security-connector"></a>手順 2: Cloud App Security コネクタを作成する

> [!NOTE]
> Cloud App Security コネクタを使用してフローを作成したことがある場合は、Flow によってトークンが自動的に再利用されるため、この手順を省略できます。

1. Cloud App Security のメニュー バーで設定の歯車 ![設定アイコン](./media/settings-icon.png "設定アイコン") をクリックし、 **[セキュリティ拡張機能]** を選択します。
1. **[セキュリティ拡張機能]** ページで [+] ボタンをクリックして新しい API トークンを生成します。
1. **[新しいトークンの生成]** ポップアップ ウィンドウに、トークン名 (たとえば "Flow-Token") を入力し、 **[生成]** をクリックします。
    ![名前入力と [生成] ボタンを示すトークンのウィンドウのスクリーンショット。](media/tutorial-flow-token-generate.png)
1. トークンが生成されたら、生成されたトークンの右側にあるコピー アイコンをクリックして、 **[閉じる]** をクリックします。 このトークンは後で必要になります。
    ![トークンとコピー プロセスを示すトークンのウィンドウのスクリーンショット。](media/tutorial-flow-token-copy.png)

### <a name="step-3-configure-the-flow"></a>手順 3: フローを構成する

> [!NOTE]
> Azure AD コネクタを使用してフローを作成したことがある場合は、Flow によってトークンが自動的に再利用されるため、この手順を省略できます。

1. Microsoft Flow ポータルに戻り、 **[作成]** をクリックします。
    ![作成プロセスを示す Flow のテンプレート ページのスクリーンショット。](media/tutorial-flow-templates-create.png)
1. **Cloud App Security** のポップアップ ウィンドウで、接続名 (たとえば "Cloud App Security トークン") を入力し、コピーした API トークンを貼り付けて、 **[作成]** をクリックします。
    ![名前とキーの入力、作成ボタンを示す [Cloud App Security] ウィンドウのスクリーンショット。](media/tutorial-flow-token-generate.png)
1. アプリの一覧で **[Azure AD を使用する HTTP]** が表示される行の末尾の 3 つのドットを選択し、 **[新しい接続の追加]** をクリックします。
1. **[Azure AD を使用する HTTP]** のポップアップ ウィンドウで **[基本リソース URL]** と **[Azure AD リソース URI]** の両方のフィールドに「`https://graph.microsoft.com`」を入力し、 **[サインイン]** をクリックして、Azure AD コネクタを使用した HTTP で使用する管理者の資格情報を入力します。
    ![リソースのフィールドと [サインイン] ボタンを示す [Azure AD を使用する HTTP] ウィンドウのスクリーンショット。](media/tutorial-flow-templates-azure.png)
1. **[続行]** をクリックします。
    ![完了したアクションと [続行] ボタンを示す Flow のテンプレート ウィンドウのスクリーンショット。](media/tutorial-flow-templates-continue.png)
1. すべてのコネクタが正常に接続されたら、フローのページの **[Apply to each machine]\(各マシンに適用\)** で、必要に応じてコメントとスキャンの種類を変更し、 **[保存]** をクリックします。
    ![スキャン設定のセクションを示す、フローのページのスクリーンショット。](media/tutorial-flow-templates-scan.png)

### <a name="step-4-apply-the-flow-to-a-policy"></a>手順 4:ポリシーにフローを適用する

1. Cloud App Security でウイルス対策フローを追加するポリシーを編集し、 **[アラート]** で **[Flow にアラートを送信する]** 、 **[Run antivirus scan using Windows Defender upon a Cloud App Security alert]\(Cloud App Security アラート時に Windows Defender を使用してウイルス対策スキャンを実行する\)** の順に選択します。
    ![アラート設定のセクションを示すポリシー ページのスクリーンショット。](media/tutorial-flow-templates-alerts.png)

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
[カスタム アラート オートメーションのための Flow との統合](flow-integration.md)
