---
title: Cloud App Security アクセス ポリシーを作成し、アクセスを許可またはブロックする
description: この記事では、Cloud App Security のアプリの条件付きアクセス制御のアクセス ポリシーを設定し、リバース プロキシ機能を使用して Azure AD 経由で接続されているアプリへのアクセスを許可またはブロックする手順について説明します。
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
ms.assetid: 9095cff1-f8b0-44a7-b1df-a83e674abbc6
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 9a74d63d62809860479110c26def76873c66c8dd
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460985"
---
# <a name="access-policies"></a>アクセス ポリシー

*適用対象: Microsoft Cloud App Security*

>[!div class="step-by-step"]
[« 戻る: セッション ポリシーを作成する方法](session-policy-aad.md)<br>
[次へ: 人気のあるユース ケースを参照する »](use-case-proxy-block-session-aad.md)

Microsoft Cloud App Security アクセス ポリシーでは、ユーザー、場所、デバイス、アプリを基準に、クラウド アプリへのアクセスをリアルタイムで監視し、制御できます。 マネージド デバイスにクライアント証明書をロールアウトしたり、サードパーティの MDM 証明書など、既存の証明書を使用したりすることで、ドメインに参加していないデバイスや Windows Intune で管理されていないデバイスを含め、あらゆるデバイスを対象にアクセス ポリシーを作成できます。 たとえば、マネージド デバイスにクライアント証明書を展開し、その後、証明書のないデバイスからのアクセスをブロックできます。 

> [!NOTE]
> [セッション ポリシー](session-policy-aad.md)では、アクセスを完全に許可またはブロックするのではなく、セッションを監視しながらアクセスを許可したり、特定のセッション アクティビティを制限したりできます。 

## <a name="prerequisites-to-using-access-policies"></a>アクセス ポリシーを使うための前提条件

- Azure AD Premium P1 のライセンス
- 関連するアプリを [Conditional Access App Control と共にデプロイ](proxy-deployment-aad.md)する必要があります。
- 以下の説明のとおり、Microsoft Cloud App Security にユーザーをリダイレクトする [Azure AD 条件付きアクセス ポリシー](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)を設定する必要があります。

> [!NOTE]
> - アクセス ポリシーは、Azure AD 以外の ID プロバイダーで構成されたアプリにも対応しています。 詳細については、mcaspreview@microsoft.com に電子メールをお送りください。

## <a name="create-an-azure-ad-conditional-access-policy"></a>Azure AD 条件付きアクセス ポリシーを作成する

Azure Active Directory の条件付きアクセス ポリシーと Cloud App Security のセッション ポリシーは連携して動作し、各ユーザー セッションを調べて、各アプリに関するポリシーの決定を行います。 Azure AD で条件付きアクセス ポリシーを設定するには、次の手順のようにします。

1. ユーザーまたはユーザー グループに対する割り当てと、Conditional Access App Control で制御するアプリを指定して、[Azure AD 条件付きアクセス ポリシー](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)を構成します。 

   > [!NOTE]
   > このポリシーが適用されるのは、[Conditional Access App Control と共にデプロイ](proxy-deployment-aad.md)されたアプリだけです。 

2. **[セッション]** の **[Use Conditional Access App Control enforced restrictions]\(アプリの条件付きアクセス制御によって適用される制限を使用する\)** を選択して、Microsoft Cloud App Security にユーザーをルーティングします。
 
## <a name="create-a-cloud-app-security-access-policy"></a>Cloud App Security アクセス ポリシーを作成する 

新しいアクセス ポリシーを作成するには、次の手順を実行します。

1. ポータルで、 **[制御]** 、 **[ポリシー]** の順に選びます。
2. **[ポリシー]** ページで、 **[ポリシーの作成]** をクリックし、 **[アクセス ポリシー]** を選択します。  

3. **[アクセス ポリシー]** ウィンドウで、*Block access from unmanaged devices* のような名前をポリシーに付けます。

4. **[次のすべてに一致するアクティビティ]** セクションの **[アクティビティ ソース]** で、ポリシーに適用する追加のアクティビティ フィルターを選択します。 フィルターには次のオプションがあります。 
     
   - **[デバイス タグ]** : 管理されていないデバイスを識別するには、このフィルターを使います。

   - **[場所]** : 不明な (したがって危険な) 場所を識別するには、このフィルターを使います。 

   - **[IP アドレス]** : IP アドレスでフィルター処理するか、前に割り当てた IP アドレス タグを使うには、このフィルターを使います。 

   - **[ユーザー エージェント タグ]** : モバイル アプリまたはデスクトップ アプリを識別するためにヒューリスティックを有効にするには、このフィルターを使います。 このフィルターは、"等しい" または "等しくない" に設定できます。 値は、各クラウド アプリのモバイル アプリとデスクトップ アプリに対してテストする必要があります。
  
5. **[アクション]** で、次のいずれかのオプションを選択します。 

    - **[許可]** : 設定したポリシー フィルターに従ってアクセスを明示的に許可するには、このアクションを設定します。

    - **[ブロック]** : 設定したポリシー フィルターに従ってアクセスを明示的にブロックするには、このアクションを設定します。 

6. **一致するイベントごとにポリシー重要度に応じたアラートを作成**し、アラート制限を設定して、アラートをメールとテキスト メッセージのどちらか一方または両方にするかどうかを選ぶことができます。



>[!div class="step-by-step"]
[« 戻る: セッション ポリシーを作成する方法](session-policy-aad.md)<br>
[次へ: 人気のあるユース ケースを参照する »](use-case-proxy-block-session-aad.md)

 
## <a name="next-steps"></a>次の手順  
[Azure AD の Conditional Access App Control 機能を使って管理されていないデバイスでのダウンロードをブロックする](use-case-proxy-block-session-aad.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
  
  
