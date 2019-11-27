---
title: よく寄せられる質問 - Cloud App Security | Microsoft ドキュメント
description: この記事では、Cloud App Security に関するよく寄せられる質問と回答を示します。
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
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 6e2464988eb075e3dd3bd345716b5ec71dec8ba6
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460843"
---
# <a name="frequently-asked-questions"></a>よく寄せられる質問

*適用対象: Microsoft Cloud App Security*

この記事では、Cloud App Security に関するよく寄せられる質問と回答を示します。

## <a name="what-kind-of-permissions-do-i-need-to-access-cloud-app-security"></a>Cloud App Security にアクセスするには、どのようなアクセス許可が必要ですか?

Azure Active Directory での全体管理者、コンプライアンス管理者、またはセキュリティ管理者である必要があります。 Office 365 セキュリティ/コンプライアンス センターでこれらのロールを持っているだけでは十分ではありません。 Azure Active Directory でユーザーを全体管理者、コンプライアンス管理者、またはセキュリティ管理者として設定するには、PowerShell を使用できます。 次のコマンドレットを実行します。

```powershell

 $cred = Get-Credential
 Connect-MsolService -credential $cred
 Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
```

 OR

```powershell
 Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”
```

## <a name="next-steps"></a>次の手順  
クラウド アプリの使用を制御するポリシーを設定して使用する方法については、「[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)」をご覧ください。   

[!INCLUDE [Open support ticket](includes/support.md)]  
