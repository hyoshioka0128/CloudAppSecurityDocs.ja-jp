---
title: Cloud App Security での API トークンの管理
description: この記事では、Cloud App Security 用の API トークンの生成に関して説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/27/2020
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: 933c2beb8285f4f76f61406ab4981153b81913cc
ms.sourcegitcommit: 286f8d5d940d1bb9a09daa3070ac4fc3768208f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84505421"
---
# <a name="managing-api-tokens"></a>API トークンの管理

*適用対象:Microsoft Cloud App Security*

Cloud App Security API にアクセスするには、api トークンを作成し、それをソフトウェアで使用して API に接続する必要があります。 このトークンは、Cloud App Security が API 要求を行うときにヘッダーに含まれます。

[API トークン] タブでは、テナントのすべての API トークンを管理できます。

## <a name="generate-a-token"></a>トークンを生成する

1. **[設定]** メニューから **[セキュリティ拡張機能]**、**[API トークン]** の順に選びます。

2. プラス アイコン **[新しいトークンの生成]** をクリックし、後でトークンの識別に使う名前を指定して、**[次へ]** をクリックします。

    ![Cloud App Security が API トークンを生成する](media/api-token-gen.png)

3. トークンの値をコピーし、回復するときのためにどこかに保存します。トークンを紛失した場合、再生成する必要があります。 トークンには、それを発行したユーザーの特権が設定されます。 たとえば、セキュリティ閲覧者は、データを変更できるトークンを発行することはできません。

4. 状態 (アクティブ、非アクティブ、生成済み) でトークンをフィルター処理できます。

    - **生成された:** 使用されていないトークン。
    - **アクティブ:** 生成され、過去7日以内に使用されたトークン。
    - **非アクティブ:** トークンが使用されましたが、過去7日間はアクティビティがありませんでした。

5. 新しいトークンを生成すると、Cloud App Security ポータルへのアクセスに使用する新しい URL が与えられます。

    ![Cloud App Security API トークン](media/generate-api-token.png)

    ジェネリック ポータル URL は引き続き機能しますが、トークンで与えられるカスタム URL に比べてかなり遅くなります。 URL を忘れた場合、メニューの **?** アイコンに移動し、 **[バージョン情報]** を選択すると表示できます。

> [!NOTE]
> Azure Active Directory Privileged Identity Management ロールのアクティブ化を使用している場合は、ロールがアクティブになると、API トークンが有効になります。 詳細については、「 [PIM での Azure AD ロールのアクティブ化](https://docs.microsoft.com/azure/active-directory/privileged-identity-management/pim-how-to-activate-role)」を参照してください。

## <a name="api-token-management"></a>API トークンの管理

[API トークン] ページには、生成されたすべての API トークンの表が含まれます。

完全な権限を持つ管理者には、このテナントに対して生成されたすべてのトークンが表示されます。 他のユーザーには、自分で生成したトークンだけが表示されます。

表では、トークンが生成された日時と最後に使われた日時に関する詳細がわかり、トークンを取り消すこともできます。

取り消されたトークンは表から削除され、そのトークンを使っていたソフトウェアは、新しいトークンが提供されるまで API を呼び出すことができません。

> [!NOTE]
> SIEM コネクタとログ コレクターも API トークンを使います。 これらのトークンは、ログ コレクターおよび SIEM エージェントのセクションから管理する必要があり、この表には表示されません。

[!INCLUDE [Open support ticket](includes/support.md)]

## <a name="check-out-this-video"></a>このビデオをご覧ください。

[Microsoft Cloud App Security – REST API とトークン](https://channel9.msdn.com/Shows/Microsoft-Security/Microsoft-Cloud-App-Security--REST-APIs-and-Tokens)
