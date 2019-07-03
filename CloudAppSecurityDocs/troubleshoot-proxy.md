---
title: Conditional Access App Control をトラブルシューティングします。
description: この記事では、Conditional Access App Control の考えられる問題の一覧を示し、考えられる解決策を提供します。
keywords: ''
author: ShlomoSagir-MS
ms.author: shsagir
manager: ShlomoSagir-MS
ms.date: 6/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.suite: ems
ms.openlocfilehash: e051d00c118b8e41142f8c0d9cc726675dcea27d
ms.sourcegitcommit: ee00e0033bf45a5f795bfd3e1d71fa1f70f97acb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67515043"
---
# <a name="troubleshooting-conditional-access-app-control"></a>Conditional Access App Control のトラブルシューティング

*適用対象:Microsoft Cloud App Security*

この記事で prohvides 可能の Conditional Access App Control の一覧は、問題し、考えられる解決策を提供します。

## <a name="troubleshooting-onboarded-apps"></a>オンボードのアプリのトラブルシューティング

### <a name="the-sign-in-to-the-app-is-not-working"></a>アプリへのサインインが動作していません

1. Cloud App Security では、メニュー バーで設定の歯車アイコンをクリックして![設定アイコン](./media/settings-icon.png "設定アイコン")選択**Conditional Access App Control**します。
1. 構成しているアプリが表示されて、アプリの一覧で 行の最後に 3 つのドットを選択し、**編集アプリ**します。
1. クリックして**Nonce 処理**」セクションを展開し、選択**nonce の処理を有効にする**します。

    ![Nonce 処理オプションのスクリーン ショット。](media/troubleshooing-nonce-handling.png)

    > [!NOTE]
    > ホーム ページ以外のアプリ ページに移動する問題が発生した場合は、次を参照してください[アプリへの後続アクセスのトラブルシューティングが目的のページに進まないように。](#unexpected-page)

### アプリにアクセスする際は、予想されるページに進まないように<a name="unexpected-page"></a>

次の手順は、Fiddler を使用したトラフィックのログ記録のツールとしてに基づいています。 エクスペリエンスは、その他のツールは異なる場合があります。 Fiddler の使用方法の詳細については、次を参照してください。 [fiddler のログを収集する簡単な方法](https://blogs.msdn.microsoft.com/maheshk/2016/05/03/easy-way-to-collect-fiddler-log-fiddlercap/)します。

1. 予想されるページに移動しないアプリでページの URL をコピーする-後で必要です。

    > [!NOTE]
    > ドメインに、Cloud App Security URL サフィックスが含まれていないことを確認します (例: *. us2.cas.ms*)

1. Fiddler などのトラフィックのログ記録ツールを使用すると、ページを監視できます。
1. 先ほどコピーした URL に移動し、必要な場合を認証します。
1. トラフィックのログ記録ツールでは、ドメインおよびパスを使用するプロトコルに基づく一致する要求を検索します。

    | プロトコル | [ドメイン] | パス | 状態のフィールド名 |
    | --- | --- | --- | --- |
    | OIDC | `https://login.microsoftonline.com` | /common/oauth2/authorize | state |
    | SAML 2.0 | `https://login.microsoftonline.com` | /*id*/saml2 | RelayState |

1. 要求を選択し、**インスペクター** ] タブで [ **WebForms**します。
1. に基づいて、正規表現文字列を作成します 

## <a name="next-steps"></a>次の手順

[Cloud Discovery の展開](set-up-cloud-discovery.md)

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)
