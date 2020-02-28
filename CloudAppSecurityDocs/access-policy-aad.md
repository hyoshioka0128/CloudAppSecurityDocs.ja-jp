---
title: アクセスを許可またはブロックするための Cloud App Security アクセスポリシーを作成する
description: この記事では、リバースプロキシ機能を使用して Azure AD 経由で接続されているアプリへのアクセスを許可またはブロックする Cloud App Security アプリの条件付きアクセス制御アクセスポリシーを設定する手順について説明します。
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
ms.openlocfilehash: 4f0fc4fa4bef878f6b248357f8c9bae97e52bbce
ms.sourcegitcommit: 11ae264d365e403f7761e880e82aad80afc31228
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2020
ms.locfileid: "77674597"
---
# <a name="access-policies"></a>アクセス ポリシー

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security アクセスポリシーを使用すると、ユーザー、場所、デバイス、アプリに基づいて、クラウドアプリへのアクセスをリアルタイムで監視および制御することができます。 管理対象デバイスにクライアント証明書を展開したり、サードパーティの MDM 証明書などの既存の証明書を使用したりすることによって、ドメインに参加していないデバイスや、Windows Intune で管理されていないデバイスなど、任意のデバイスのアクセスポリシーを作成できます。 たとえば、管理対象デバイスにクライアント証明書を展開し、証明書のないデバイスからのアクセスをブロックすることができます。

> [!NOTE]
> [セッションポリシー](session-policy-aad.md)を使用してアクセスを完全に許可またはブロックするのではなく、セッションを監視しながらアクセスを許可したり、特定のセッションアクティビティを制限したりすることができます。

## <a name="prerequisites-to-using-access-policies"></a>アクセスポリシーを使用するための前提条件

- Azure AD Premium P1 ライセンス
- 関連するアプリは、[アプリの条件付きアクセス制御で展開](proxy-deployment-aad.md)する必要があります。
- 次に説明するように、 [Azure AD 条件付きアクセスポリシー](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)を使用して、ユーザーを Microsoft Cloud App Security にリダイレクトする必要があります。

> [!NOTE]
> - アクセスポリシーでは、Azure AD 以外の id プロバイダーで構成されたアプリもサポートされます。 詳細については、mcaspreview@microsoft.comに電子メールを送信してください。

## <a name="create-an-azure-ad-conditional-access-policy"></a>Azure AD 条件付きアクセスポリシーを作成する

条件付きアクセスポリシーと Cloud App Security セッションポリシーを連携させる Azure Active Directory、各ユーザーセッションを確認し、各アプリのポリシーの決定を行います。 Azure AD で条件付きアクセスポリシーを設定するには、次の手順に従います。

1. ユーザーまたはユーザーグループの割り当てと、アプリの条件付きアクセス制御で制御するアプリを使用して、 [Azure AD 条件付きアクセスポリシー](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)を構成します。

    > [!NOTE]
    > このポリシーの影響を受けるのは、[アプリの条件付きアクセス制御で展開](proxy-deployment-aad.md)されたアプリのみです。

2. **[セッション]** で **[使用アプリの条件付きアクセス制御強制]** された制限を使用する を選択して Microsoft Cloud App Security にユーザーをルーティングします。

## <a name="create-a-cloud-app-security-access-policy"></a>Cloud App Security アクセスポリシーを作成する

新しいアクセスポリシーを作成するには、次の手順を実行します。

1. ポータルで、 **[制御]** 、 **[ポリシー]** の順に選択します。
2. **[ポリシー]** ページで、 **[ポリシーの作成]** をクリックし、 **[アクセスポリシー]** を選択します。

3. **[アクセスポリシー]** ウィンドウで、管理されていない*デバイスからのアクセスをブロック*するなど、ポリシーの名前を割り当てます。

4. **次のすべての**セクションに一致するアクティビティの **[アクティビティソース]** で、ポリシーに適用する追加のアクティビティフィルターを選択します。 フィルターには、次のオプションがあります。

    - **デバイスタグ**: 管理されていないデバイスを識別するには、このフィルターを使用します。

    - **[場所]** : このフィルターを使用して、不明な (またはリスクのある) 場所を特定します。

    - **Ip アドレス**: ip アドレスごとにフィルター処理する場合、または以前に割り当てた ip アドレスタグを使用する場合は、このフィルターを使用します。

    - **ユーザーエージェントタグ**: このフィルターを使用して、モバイルアプリとデスクトップアプリを特定するヒューリスティックを有効にします。 このフィルターは、equals に設定することも、等しくないように設定することもできます。 これらの値は、各クラウドアプリのモバイルアプリとデスクトップアプリに対してテストする必要があります。

5. **[アクション]** で、次のいずれかのオプションを選択します。

    - **テスト**: 設定したポリシーフィルターに従って明示的にアクセスを許可するには、このアクションを設定します。

    - **ブロック**: 設定したポリシーフィルターに従ってアクセスを明示的にブロックするには、このアクションを設定します。

6. 一致する**イベントごとに、ポリシーの重要度でアラートを作成**し、アラート制限を設定して、アラートを電子メール、テキストメッセージ、またはその両方として使用するかどうかを選択できます。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [セッション制御を使用したアンマネージドデバイスでのダウンロードのブロック](use-case-proxy-block-session-aad.md)

## <a name="see-also"></a>参照

> [!div class="nextstepaction"]
> [セッションポリシーを作成する方法](session-policy-aad.md)

> [!div class="nextstepaction"]
> [人気のあるユースケースを調べる»](use-case-proxy-block-session-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
