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
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 043615ccdde609f77f6804ee9040e1df55a321f4
ms.sourcegitcommit: 6eff466c7a6817b14a60d8c3b2c201c7ae4c2e2c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74719861"
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

 または

```powershell
 Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”
```

## <a name="next-steps"></a>次のステップ

クラウド アプリの使用を制御するポリシーを設定して使用する方法については、「[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)」をご覧ください。

[!INCLUDE [Open support ticket](includes/support.md)]
