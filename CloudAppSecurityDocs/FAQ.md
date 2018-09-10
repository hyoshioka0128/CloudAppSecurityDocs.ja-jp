---
title: Cloud App Security についてよく寄せられる質問 | Microsoft ドキュメント
description: この記事では、Cloud App Security に関するよく寄せられる質問と回答を示します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 081c2cf4-2750-4546-9490-4b65e87ae48c
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: b53a360b743e80c85dcced8dd2bef7eae8c60f36
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44144008"
---
*適用対象: Microsoft Cloud App Security*


# <a name="frequently-asked-questions"></a>よく寄せられる質問

## <a name="what-kind-of-permissions-do-i-need-to-have-in-order-to-access-cloud-app-security"></a>Cloud App Security にアクセスするには、どのようなアクセス許可が必要ですか?

Azure Active Directory でのグローバル管理者、コンプライアンス管理者、またはセキュリティ管理者である必要があります。 Office 365 セキュリティとコンプライアンス センターでこれらのロールを保持するだけでは十分ではありません。
Azure Active Directory でユーザーをグローバル管理者、コンプライアンス管理者、またはセキュリティ管理者として設定するには、Windows PowerShell で次を実行します。

        $cred = Get-Credential
        Connect-MsolService -credential $cred
        Add-MsolRoleMember -RoleName "Compliance Administrator" -RoleMemberEmailAddress "XX@XX.XX"
 または Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress “XX@XX.XX”

## <a name="see-also"></a>「  
クラウド アプリの使用を制御するポリシーを設定する方法については、「[ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)」を参照してください。   

Premier サポートをご利用のお客様は、[Premier ポータル](https://premier.microsoft.com/)から直接 Cloud App Security を選択することもできます。  
