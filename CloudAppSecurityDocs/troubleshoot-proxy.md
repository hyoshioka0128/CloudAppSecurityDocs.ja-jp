---
title: アプリの条件付きアクセス制御のトラブルシューティング
description: この記事では、考えられるアプリの条件付きアクセス制御の問題の一覧を示し、考えられる解決策を示します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: d98721a4ca08b3e415b8b0fff40676af1b3d37e6
ms.sourcegitcommit: 7c93b6f93d2699d466b172590710ed01697bbdad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74720984"
---
# <a name="troubleshooting-conditional-access-app-control"></a>アプリの条件付きアクセス制御のトラブルシューティング

*適用対象: Microsoft Cloud App Security*

この記事では、考えられるアプリの条件付きアクセス制御の問題の一覧を示し、考えられる解決策を示します。

## <a name="troubleshooting-onboarded-apps"></a>オンボードアプリのトラブルシューティング

### <a name="the-sign-in-to-the-app-is-not-working"></a>アプリへのサインインが動作していません

1. Cloud App Security のメニューバーで、[設定] 歯車![設定アイコン](media/settings-icon.png "設定アイコン")をクリックし、 **[アプリの条件付きアクセス制御]** を選択します。
1. アプリの一覧で、構成しているアプリが表示されている行で、行の末尾にある3つの点を選択し、 **[アプリの編集]** を選択します。
1. **[Nonce-処理]** をクリックしてセクションを展開し、 **[Nonce 処理を有効]** にする を選択します。

    ![Nonce 処理オプションのスクリーンショット。](media/troubleshooing-nonce-handling.png)

    > [!NOTE]
    > ホームページ以外のアプリページに移動するときに問題が発生した場合は、「[アプリへの後続のアクセスのトラブルシューティング」を](#unexpected-page)参照してください。

### それ以降のアプリへのアクセスは、予期されたページにアクセスしません<a name="unexpected-page"></a>

次の手順は、トラフィックログツールとして Fiddler を使用することに基づいています。 他のツールでは、エクスペリエンスが異なる場合があります。 Fiddler の使用方法の詳細については、「 [Fiddler log を簡単に収集する方法](https://blogs.msdn.microsoft.com/maheshk/2016/05/03/easy-way-to-collect-fiddler-log-fiddlercap/)」を参照してください。

1. アプリ内のページの URL をコピーします。このページは、予想されるページには表示されません。後で必要になります。

    > [!NOTE]
    > ドメインに Cloud App Security URL サフィックス (例: *us2.cas.ms*) が含まれていないことを確認します。

1. ページを監視するには、Fiddler などのトラフィックログツールを使用します。
1. 前の手順でコピーした URL にアクセスし、必要に応じて認証します。
1. トラフィックログツールで、使用しているプロトコルに基づいて、ドメインとパスに一致する要求を検索します。

    | プロトコル | Domain | パス | 状態フィールド名 |
    | --- | --- | --- | --- |
    | OIDC | `https://login.microsoftonline.com` | /common/oauth2/authorize | state |
    | SAML 2.0 | `https://login.microsoftonline.com` | /*id*/saml2 | RelayState |

1. 要求を選択し、 **[インスペクター]** タブで **[WebForms]** を選択します。
1. に基づく regex 文字列を作成します。 

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [Cloud Discovery の展開](set-up-cloud-discovery.md)

[!INCLUDE [Open support ticket](includes/support.md)]
