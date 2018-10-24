---
title: Cloud App Security アクセス ポリシーを作成し、アクセスを許可またはブロックする | Microsoft Docs
description: このトピックでは、Cloud App Security Conditional Access App Control アクセス ポリシーを設定し、リバース プロキシ機能を使用して Azure AD 経由で接続されているアプリへのアクセスを許可またはブロックする手順について説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 6/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 9095cff1-f8b0-44a7-b1df-a83e674abbc6
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 0c6f6a8139996cadde78f5378b84d82210d70ade
ms.sourcegitcommit: da651fb36d26d0dfe796b988e86205f41f7dc5de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251389"
---
*適用対象: Microsoft Cloud App Security*

# <a name="access-policies"></a>アクセス ポリシー 



>[!div class="step-by-step"]
[« 戻る: セッション ポリシーを作成する方法](session-policy-aad.md)<br>
[次へ: 人気のあるユース ケースを参照する »](use-case-proxy-block-session-aad.md)


Microsoft Cloud App Security アクセス ポリシーでは、ユーザー、場所、デバイス、アプリを基準に、クラウド アプリへのアクセスをリアルタイムで監視し、制御できます。 マネージド デバイスにクライアント証明書をロールアウトしたり、サードパーティの MDM 証明書など、既存の証明書を活用したりすることで、ドメインに参加していないデバイスや Windows Intune で管理されていないデバイスを含め、あらゆるデバイスを対象にアクセス ポリシーを作成できます。 たとえば、マネージド デバイスにクライアント証明書を展開し、その後、証明書のないデバイスからのアクセスをブロックできます。 

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

2. **[セッション]** ブレードで **[Use Conditional Access App Control enforced restrictions]\(Conditional Access App Control によって適用される制限を使用する\)** を選んで、Microsoft Cloud App Security にユーザーをルーティングします。
 
## <a name="create-a-cloud-app-security-access-policy"></a>Cloud App Security アクセス ポリシーを作成する 

新しいアクセス ポリシーを作成するには、次の手順を実行します。

1. ポータルで、**[制御]**、**[ポリシー]** の順に選びます。
2. **[ポリシー]** ページで、**[ポリシーの作成]** をクリックし、**[アクセス ポリシー]** を選択します。  

3. **[アクセス ポリシー]** ウィンドウで、*Block access from unmanaged devices* のような名前をポリシーに付けます。

4. **[次のすべてに一致するアクティビティ]** セクションの **[アクティビティ ソース]** で、ポリシーに適用する追加のアクティビティ フィルターを選びます。 次のオプションを指定できます。 
     
   - **[デバイス タグ]**: 管理されていないデバイスを識別するには、このフィルターを使います。

   - **[場所]**: 不明な (したがって危険な) 場所を識別するには、このフィルターを使います。 

   - **[IP アドレス]**: IP アドレスでフィルター処理するか、前に割り当てた IP アドレス タグを使うには、このフィルターを使います。 

   - **[ユーザー エージェント タグ]**: モバイル アプリまたはデスクトップ アプリを識別するためにヒューリスティックを有効にするには、このフィルターを使います。 このフィルターは、**ネイティブ クライアント**と等しくなるように、または等しくならないように設定でき、各クラウド アプリについてモバイル アプリとデスクトップ アプリに対してテストする必要があります。
  
5. **[アクション]** ウィンドウで、次のいずれかを選びます。 

    - **[許可]**: 設定したポリシー フィルターに従ってアクセスを明示的に許可するには、このアクションを設定します。

    - **[ブロック]**: 設定したポリシー フィルターに従ってアクセスを明示的にブロックするには、このアクションを設定します。 

6. **一致するイベントごとにポリシー重要度に応じたアラートを作成**し、アラート制限を設定して、アラートをメールとテキスト メッセージのどちらか一方または両方にするかどうかを選ぶことができます。



>[!div class="step-by-step"]
[« 戻る: セッション ポリシーを作成する方法](session-policy-aad.md)<br>
[次へ: 人気のあるユース ケースを参照する »](use-case-proxy-block-session-aad.md)

 
## <a name="see-also"></a>参照  
[Azure AD の Conditional Access App Control 機能を使って管理されていないデバイスでのダウンロードをブロックする](use-case-proxy-block-session-aad.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  