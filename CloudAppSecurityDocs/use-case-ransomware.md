---
title: 脅威保護シナリオの概要 | Microsoft Docs
description: このトピックでは、クラウド環境における脅威から組織を保護するシナリオについて説明します。
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 4/29/2018
ms.topic: conceptual
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 7a06a243-9ec2-4a11-8db2-bc065cdfef64
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 5fd6cf54012d148261e98f0058109420cb55e9fa
ms.sourcegitcommit: 0ac08ca7b3140b79f1d36ff7152476c188fa12b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2018
ms.locfileid: "44143872"
---
*適用対象: Microsoft Cloud App Security*


# <a name="protecting-your-organization-from-ransomware"></a>ランサムウェアから組織を保護する

最近の大規模なランサムウェア攻撃で、サイバー世界は WannaCry の大きな打撃を受け、150 か国で推定 200,000 台のコンピューターが感染しました。 過去数年間のランサムウェア攻撃の増加により、毎月平均で 2015 年は 25,000 件、2016 年は 56,000 件の攻撃がありました。ネットワークとクラウドが危険な状態にならないように事前に対処することがサイバーセキュリティの必須事項になっています。 この記事では、Cloud App Security を使用してクラウドを監視し、脅威を軽減し、ベスト プラクティスを適用して、ランサムウェアから環境を保護する方法について説明します。

## <a name="what-is-ransomware"></a>ランサムウェアとは
ランサムウェアは、ユーザーが自分のコンピューターにアクセスできなくなり、ユーザーのファイルを暗号化する機能を持つファイルを攻撃者が送信するサイバー攻撃です。 場合によっては、身代金のためにファイルが保持され、攻撃者に身代金を支払い、コンピューター、ファイル、重要な LOB アプリケーションへのアクセスを復元するまで、ファイルは復号化されません。 ランサムウェア攻撃は、コンピューター、家庭、オフィス、ネットワーク、またはサーバーに影響する可能性があります。 実際のところ、大規模な組織は多数のユーザーが在籍するため、誰かが誤ってファイルを開くと、社内ネットワーク全体にランサムウェアが蔓延する可能性があります。組織の場合、ランサムウェアを止め、コンピューターまたはファイルへのアクセスを復元するために、攻撃者に身代金を支払わざるを得なくなるリスクが高くなります。

>[!NOTE]
> このユース ケースは、Office 365、G Suite、Box、Dropbox に適用されます。

## <a name="the-threat"></a>脅威の内容
組織内のユーザーがランサムウェア攻撃の対象です。 ユーザーは電子メールが感染しているとは知らずに開き、ランサムウェアを実行してしまう可能性があります。その結果、クラウドと同期されているファイルを含め、そのユーザーのすべてのファイルが感染します。

## <a name="the-solution"></a>解決策
疑わしいアクティビティが検出されたときに更新するポリシーを作成して、クラウド環境のランサムウェアと疑わしいものを検出します。また、ランサムウェア ファイルがクラウドに保存されないようにする自動アクションを設定します。

## <a name="out-of-the-box-protection"></a>そのまま利用可能できる保護

少なくとも 1 つのクラウド アプリ (Office 365、G Suite、Box、Dropbox) を Cloud App Security に[接続](enable-instant-visibility-protection-and-governance-actions-for-your-apps.md)します。

1.  既定では、Cloud App Security はネットワークをスキャンして基準を確立し、クラウドでユーザーが通常行う動作、タイミング、よく行う動作のパターンを学習します。 

2. Cloud App Security の自動化された[脅威検出ポリシー](anomaly-detection-policy.md)は、接続した時点からバックグラウンドで実行を開始します。 これらのポリシーの 1 つが、ランサムウェアのアクティビティを検索して、高度なランサムウェア攻撃に対する包括的な防御を保証します。 Cloud App Security は、弊社のセキュリティ調査の専門技術を使用して、ランサムウェア アクティビティを反映する行動パターンを識別し、総体的で堅牢な保護を実現します。 たとえば、Cloud App Security によってファイル アップロードまたはファイル削除のアクティビティが高い確率で識別される場合、それは暗号化プロセスを表している可能性があります。 このデータは、接続された API から受け取ってログに収集され、その後、学習した行動パターンおよび脅威インテリジェンス (既知のランサムウェアの拡張子など) と組み合わされます。 




   ## <a name="see-also"></a>参照  
   [クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   

[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  