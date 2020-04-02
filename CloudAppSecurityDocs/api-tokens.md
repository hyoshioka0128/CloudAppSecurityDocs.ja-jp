---
title: Cloud App Security での API トークンの管理
description: この記事では、Cloud App Security 用の API トークンの生成に関する情報を提供します。
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
ms.openlocfilehash: fcde5b08363a790cf18cf873c0dfde183ec6ddcd
ms.sourcegitcommit: 9165220189564860d74a255a5c0be1ed362ba152
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2020
ms.locfileid: "80522552"
---
# <a name="api-tokens"></a>API トークン

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security API を使用すると、REST API エンドポイントを介して、プログラムで Cloud App Security にアクセスできます。 アプリケーションでは、API を使用して Cloud App Security のデータとオブジェクトに対して読み取りおよび更新操作を実行できます。 たとえば、Cloud App Security API は、ユーザーオブジェクトに対して次の一般的な操作をサポートします。

- Cloud Discovery のログファイルのアップロード
- ブロックスクリプトの生成
- 活動、アラート、およびポリシーレポートを一覧表示する
- アラートを破棄または解決する

API の完全なドキュメントについては、Cloud App Security ポータルで、[ヘルプ] > **api ドキュメント**を参照してください。

API にアクセスするには、API トークンを作成し、それをソフトウェアで使用して Cloud App Security API に接続する必要があります。

[API トークン] タブを使用すると、テナントのすべての API トークンを管理できます。

## <a name="generate-a-token"></a>トークンを生成する

1. **[設定]** メニューで、 **[セキュリティ拡張機能]** 、 **[API トークン]** の順に選択します。

2. プラスアイコンをクリックし、 **[新しいトークンの生成]** をクリックして、後でトークンを識別する名前を指定し、 **[次へ]** をクリックします。
  ![Cloud App Security によって API トークンが生成され](media/api-token-gen.png)

3. トークン値をコピーし、復旧のためにどこかに保存します。これを紛失した場合は、トークンを再生成する必要があります。 トークンには、それを発行したユーザーの特権があります。 たとえば、セキュリティ閲覧者は、データを変更できるトークンを発行することはできません。

4. トークンをフィルター処理するには、状態 (アクティブ、非アクティブ、生成済み) を使用します。

    - 生成されたトークンは、一度も使用されていません。
    - アクティブとは、過去7日以内に生成され、使用されたトークンです。
    - 非アクティブなが使用されましたが、過去7日間のアクティビティはありませんでした。

5. 新しいトークンを生成すると、Cloud App Security ポータルへのアクセスに使用する新しい URL が提供されます。

    ![Cloud App Security API トークン](media/generate-api-token.png)

    汎用ポータル URL は引き続き機能しますが、トークンによって提供されるカスタム URL に比べてかなり遅くなります。 いつでも URL を忘れた場合は、「」にアクセスして確認でき**ます。** アイコンをクリックし、 **[バージョン情報]** を選択します。

> [!NOTE]
> Azure Active Directory Privileged Identity Management ロールのアクティブ化を使用している場合は、ロールがアクティブになると、API トークンが有効になります。 詳細については、「 [PIM での Azure AD ロールのアクティブ化](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-activate-role)」を参照してください。

## <a name="api-token-management"></a>API トークンの管理

[API トークン] ページには、生成されたすべての API トークンのテーブルが含まれています。

完全な管理者は、このテナントに対して生成されたすべてのトークンを表示します。 他のユーザーには、自身が生成したトークンだけが表示されます。

このテーブルは、トークンが生成された日時と最後に使用された日時に関する詳細を提供し、トークンを取り消すことができます。

トークンが失効すると、そのトークンはテーブルから削除され、それを使用していたソフトウェアは、新しいトークンが提供されるまで API を呼び出すことができません。

> [!NOTE]
>
> - SIEM コネクタとログコレクターも API トークンを使用します。 これらのトークンは、ログコレクターおよび SIEM エージェントのセクションから管理する必要があり、この表には記載されていません。
> - プロビジョニング解除 users API トークンは Cloud App Security に保持されますが、使用することはできません。 これらを使用しようとすると、アクセス許可の拒否応答が返されます。 ただし、このようなトークンは **[API トークン]** ページで取り消すことをお勧めします。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [SIEM の統合に関する問題のトラブルシューティング](troubleshooting-siem.md)

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>こちらのビデオをご覧ください。

[Microsoft Cloud App Security – REST API とトークン](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
