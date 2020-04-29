---
title: Cloud App Security アクセス ポリシーを作成し、アクセスを許可またはブロックする
description: この記事では、Cloud App Security のアプリの条件付きアクセス制御のアクセス ポリシーを設定し、リバース プロキシ機能を使用して Azure AD 経由で接続されているアプリへのアクセスを許可またはブロックする手順について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 03/31/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 23763911724e802d31e848ee1f8d6c42e346ffa4
ms.sourcegitcommit: ecb1835d1cd880de38f32ce7a7031b0015f3cae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81232474"
---
# <a name="access-policies"></a>アクセス ポリシー

*適用対象:Microsoft Cloud App Security*

Microsoft Cloud App Security アクセス ポリシーでは、ユーザー、場所、デバイス、アプリを基準に、クラウド アプリへのアクセスをリアルタイムで監視し、制御できます。 管理対象デバイスにクライアント証明書を展開したり、サードパーティの MDM 証明書などの既存の証明書を使用したりすることによって、Microsoft Intune によって管理されていないデバイス (Hybrid Azure AD Join ていないデバイスを含む) のアクセスポリシーを作成できます。 たとえば、マネージド デバイスにクライアント証明書を展開し、その後、証明書のないデバイスからのアクセスをブロックできます。

> [!NOTE]
> [セッション ポリシー](session-policy-aad.md)では、アクセスを完全に許可またはブロックするのではなく、セッションを監視しながらアクセスを許可したり、特定のセッション アクティビティを制限したりできます。

## <a name="prerequisites-to-using-access-policies"></a>アクセス ポリシーを使うための前提条件

- Azure AD Premium P1 ライセンス、または id プロバイダー (IdP) ソリューションに必要なライセンス
- 関連するアプリを [Conditional Access App Control と共にデプロイ](proxy-deployment-aad.md)する必要があります。
- 次のように、Cloud App Security を使用するように IdP ソリューションを構成していることを確認します。
  - [Azure AD 条件付きアクセス](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)については、「 [Azure AD との統合の構成](proxy-deployment-aad.md#configure-integration-with-azure-ad)」を参照してください。
  - その他の IdP ソリューションについては、「[他の IdP ソリューションとの統合の構成](proxy-deployment-aad.md#configure-integration-with-other-idp-solutions)」を参照してください。

## <a name="create-a-cloud-app-security-access-policy"></a>Cloud App Security アクセス ポリシーを作成する

新しいアクセス ポリシーを作成するには、次の手順を実行します。

1. ポータルで、**[制御]**、**[ポリシー]** の順に選びます。
2. **[ポリシー]** ページで、**[ポリシーの作成]** をクリックし、**[アクセス ポリシー]** を選択します。

3. **[アクセス ポリシー]** ウィンドウで、*Block access from unmanaged devices* のような名前をポリシーに付けます。

4. **[次のすべてに一致するアクティビティ]** セクションの **[アクティビティ ソース]** で、ポリシーに適用する追加のアクティビティ フィルターを選択します。 フィルターには次のオプションがあります。

    - **[デバイス タグ]**: 管理されていないデバイスを識別するには、このフィルターを使います。

    - **[場所]**: 不明な (したがって危険な) 場所を識別するには、このフィルターを使います。

    - **[IP アドレス]**: IP アドレスでフィルター処理するか、前に割り当てた IP アドレス タグを使うには、このフィルターを使います。

    - **[ユーザー エージェント タグ]**: モバイル アプリまたはデスクトップ アプリを識別するためにヒューリスティックを有効にするには、このフィルターを使います。 このフィルターは、"等しい" または "等しくない" に設定できます。 値は、各クラウド アプリのモバイル アプリとデスクトップ アプリに対してテストする必要があります。

5. **[アクション]** で、次のいずれかのオプションを選択します。

    - **テスト**: 設定したポリシーフィルターに従って明示的にアクセスを許可するには、このアクションを設定します。

    - **[ブロック]**: 設定したポリシー フィルターに従ってアクセスを明示的にブロックするには、このアクションを設定します。

6. **一致するイベントごとにポリシー重要度に応じたアラートを作成**し、アラート制限を設定して、アラートをメールとテキスト メッセージのどちらか一方または両方にするかどうかを選ぶことができます。

## <a name="next-steps"></a>次のステップ

> [!div class="nextstepaction"]
> [« 戻る: セッション ポリシーを作成する方法](session-policy-aad.md)

> [!div class="nextstepaction"]
> [次へ: 人気のあるユース ケースを参照する »](use-case-proxy-block-session-aad.md)

## <a name="see-also"></a>関連項目

> [!div class="nextstepaction"]
> [セッション制御を使用したアンマネージドデバイスでのダウンロードのブロック](use-case-proxy-block-session-aad.md)

[!INCLUDE [Open support ticket](includes/support.md)]
