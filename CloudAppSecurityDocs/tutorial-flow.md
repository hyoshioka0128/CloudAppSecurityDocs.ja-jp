---
title: エンドポイントの修復までガバナンスを拡張する | Microsoft Docs
description: このチュートリアルでは、Microsoft Flow をトリガーして Microsoft Defender Advanced Threat Protection 修復アクションを実行するために、Microsoft Cloud App Security ポリシー アラートを構成する手順について説明します。
author: ShlomoSagir-MS
ms.author: shsagir
ms.service: cloud-app-security
ms.topic: tutorial
ms.date: 8/22/2019
ms.openlocfilehash: 8aad8262baf985c25b4443d90c1e6ac2ba3b4725
ms.sourcegitcommit: 33257c7a1017ee0a4ff8f4f8cc7ef018c9be00e5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/01/2019
ms.locfileid: "70206540"
---
# <a name="tutorial-extending-governance-to-endpoint-remediation"></a>チュートリアル: エンドポイントの修復までガバナンスを拡張する

Cloud App Security には、ユーザーを停止したり、ファイルを非公開にするなどの定義済みのポリシーのガバナンス オプションがあります。 ネイティブに統合されている Microsoft Flow を使用すると、サービスとしてのソフトウェア (SaaS) コネクタの大規模なエコシステムを使用して、修復などのプロセスを自動化するワークフローを構築できます。

たとえば、危険なマルウェアである可能性の兆候が検出された場合、ワークフローを使用して、ウイルス対策スキャンの実行やエンドポイントの分離などの Microsoft Defender Advanced Threat Protection (ATP) 修復アクションを開始できます。

このチュートリアルでは、ワークフローを使用するポリシー ガバナンス アクションを構成して、ユーザーが疑わしい動作をしているエンドポイントでウイルス対策スキャンを実行する方法について説明します。

> [!NOTE]
> これらのワークフローは、ユーザー アクティビティを含むポリシーにのみ該当します。 たとえば、Discovery や OAuth のポリシーではこれらのワークフローは使用できません。

Microsoft Flow プランがない場合は、[無料試用版アカウントにサインアップ](https://flow.microsoft.com/pricing)します。

## <a name="prerequisites"></a>必要条件

* 有効な [Microsoft Flow プラン](https://flow.microsoft.com/pricing)が必要
* 有効な Microsoft Defender ATP プランが必要
* Microsoft Flow 環境が Azure AD と同期され、Defender ATP の監視対象で、ドメイン参加済みである

## <a name="to-configure-an-antivirus-scan-remediation-action"></a>ウイルス対策スキャンの修復アクションを構成するには

### <a name="step-1-generate-a-cloud-app-security-api-token"></a>手順 1.Cloud App Security の API トークンを生成する

> [!NOTE]
> Cloud App Security コネクタを使用してフローを作成済みである場合は、Microsoft Flow がトークンを自動的に再利用するため、この手順を省略できます。

1. Cloud App Security のメニュー バーで設定の歯車 ![設定アイコン](./media/settings-icon.png "設定アイコン") をクリックし、 **[セキュリティ拡張機能]** を選択します。

1. **[セキュリティ拡張機能]** ページで [+] ボタンをクリックして新しい API トークンを生成します。
1. **[新しいトークンの生成]** ポップアップ ウィンドウに、トークン名 (たとえば "Flow-Token") を入力し、 **[生成]** をクリックします。

    ![名前入力と [生成] ボタンを示すトークンのウィンドウのスクリーンショット。](media/tutorial-flow-token-generate.png)
1. トークンが生成されたら、生成されたトークンの右側にあるコピー アイコンをクリックして、 **[閉じる]** をクリックします。 このトークンは後で必要になります。

    ![トークンとコピーの手順を示すトークン ウィンドウのスクリーンショット。](media/tutorial-flow-token-copy.png)

### <a name="step-2-create-a-flow-to-run-an-antivirus-scan"></a>手順 2: ウイルス対策スキャンを実行するフローを作成する

> [!NOTE]
> Defender ATP コネクタを使用してフローを作成したことがある場合は、Flow によってコネクタが自動的に再利用されるため、**サインイン**の手順を省略できます。

1. [Microsoft Flow ポータル](https://flow.microsoft.com/)にアクセスし、[テンプレート] を選択してください。
    ![[テンプレート] が選択されている Microsoft Flow のメイン ページのスクリーンショット。](media/tutorial-flow-templates.png)

1. "Cloud App Security" を検索し、 **[Run antivirus scan using Windows Defender upon a Cloud App Security alert]\(Cloud App Security アラート時に Windows Defender を使用してウイルス対策スキャンを実行する\)** を選択します。

    ![検索結果を示す Microsoft Flow のテンプレート ページのスクリーンショット。](media/tutorial-flow-templates-search.png)

1. **[サインイン]** をクリックして Microsoft Defender ATP コネクタで使用する管理者の資格情報を入力します。

    ![サインイン手順を示す Microsoft Flow のテンプレート ページのスクリーンショット。](media/tutorial-flow-templates-signin.png)

### <a name="step-3-configure-the-flow"></a>手順 3: フローを構成する

> [!NOTE]
> Azure AD コネクタを使用してフローを作成済みである場合は、Microsoft Flow がトークンを自動的に再利用するため、この手順を省略できます。

1. **[作成]** をクリックします。

    ![Cloud App Security の [作成] ボタンを示す Microsoft Flow のテンプレート ページのスクリーンショット。](media/tutorial-flow-templates-create.png)

1. **Cloud App Security** のポップアップ ウィンドウで、接続名 (たとえば "Cloud App Security トークン") を入力し、コピーした API トークンを貼り付けて、 **[作成]** をクリックします。

    ![名前とキーが入力された、[作成] ボタンがある [Cloud App Security] ウィンドウのスクリーンショット。](media/tutorial-flow-templates-create-window.png)

1. アプリの一覧で **[Azure AD を使用する HTTP]** が表示される行の末尾の 3 つのドットを選択し、 **[新しい接続の追加]** をクリックします。

1. **[Azure AD を使用する HTTP]** のポップアップ ウィンドウで **[基本リソース URL]** と **[Azure AD リソース URI]** の両方のフィールドに「`https://graph.microsoft.com`」を入力し、 **[サインイン]** をクリックして、Azure AD コネクタを使用した HTTP で使用する管理者の資格情報を入力します。

    ![リソースのフィールドと [サインイン] ボタンがある [Azure AD を使用する HTTP] ウィンドウのスクリーンショット。](media/tutorial-flow-templates-azure.png)

1. **[続行]** をクリックします。

    ![完了したアクションと [続行] ボタンがある、Microsoft Flow のテンプレート ウィンドウのスクリーンショット。](media/tutorial-flow-templates-continue.png)

1. すべてのコネクタが正常に接続されたら、フローのページの **[Apply to each machine]\(各マシンに適用\)** で、必要に応じてコメントとスキャンの種類を変更し、 **[保存]** をクリックします。

    ![スキャンの設定セクションがある Flow ページのスクリーンショット。](media/tutorial-flow-templates-scan.png)

### <a name="step-4-configure-the-policy-to-run-the-flow"></a>手順 4:フローを実行するポリシーを設定する

1. Cloud App Security で **[制御]** 、 **[ポリシー]** の順にクリックします。

1. ポリシー一覧の、該当するポリシーが表示されている行の行末の 3 つの点を選択し、 **[ポリシーの編集]** を選択します。

1. **[アラート]** の下の **[Flow にアラートを送信する]** を選択し、次いで **[Run antivirus scan using Windows Defender upon a Cloud App Security alert]** \(Cloud App Security アラート時に Windows Defender を使用してウイルス対策スキャンを実行する\) を選択します。

    ![アラート設定のセクションを示すポリシー ページのスクリーンショット。](media/tutorial-flow-templates-alerts.png)

これで、このポリシーに対して生成されたすべてのアラートで、ウイルス対策スキャンを実行するフローが開始されます。

このチュートリアルの手順を使用すると、Cloud App Security の修復機能を拡張するさまざまなワークフローを使用したアクションを作成できます。これには、その他の Defender ATP アクションも含まれます。 Microsoft Flow に定義済みの Cloud App Security ワークフローの一覧を表示するには、[「Cloud App Security」を検索](https://go.microsoft.com/fwlink/?linkid=2102574)してください。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
[カスタム アラート オートメーションのための Microsoft Flow との統合](flow-integration.md)
