---
title: "Cloud App Security のエディション間の相違点 | Microsoft ドキュメント"
description: "このトピックでは、Cloud App Security と Office 365 の高度なセキュリティ管理の違いについて説明します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 8/8/2017
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: 49c12f7c-3fb8-46ac-b2ab-59ba6cf2ddfb
ms.reviewer: reutam
ms.suite: ems
ms.openlocfilehash: 68ca6a7a4bacb0e04fddea4c1df36350c0e4c6fb
ms.sourcegitcommit: b446a82c945de6452813aac7780f6a3a264495e1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2017
---
# <a name="what-are-the-differences-between-cloud-app-security-and-office-365-advanced-security-management-asm"></a>Cloud App Security と Office 365 の高度なセキュリティ管理 (ASM) の相違点

> [!NOTE]
> Office 365 の Advanced Security Management と Cloud App Security の詳細については、「[Get started with Advanced Security Management](https://support.office.com/article/Get-started-with-Advanced-Management-Security-d9ee4d67-f2b3-42b4-9c9e-c4529904990a)」(Advanced Security Management の概要) を参照してください。

## <a name="cloud-app-security"></a>Cloud App Security 

Cloud App Security のスタンドアロン バージョンはクロス SaaS ソリューションであり、承認されていないアプリのシャドウ IT 検出を提供すると共に、承認されたアプリについては組織内のクラウド アプリケーション全体の情報保護、脅威検出、条件付きアクセスを提供します。 

## <a name="office-365-advanced-security-management"></a>Office 365 の高度なセキュリティ管理

高度なセキュリティの管理は Cloud App Security のサブセットであり、強化された可視性と制御を Office 365 に提供します。 これには、ユーザー アクティビティ ログに基づく脅威の検出、Office 365 のサービスと同様の機能を持つアプリのシャドウ IT の発見、Office 365 に対するアプリのアクセス許可の制御などが含まれます。

## <a name="feature-support"></a>機能のサポート

|領域|機能|Microsoft Cloud App Security|高度なセキュリティ管理|
|----|----|----|----|
|シャドウ IT の検出||||
||検出されたアプリのサポート|15,000 以上および自動リスク評価|Office 365 と同様の 750 以上のアプリ|
||ログのアップロード|手動および自動|手動|
||ユーザーのプライバシー保護のためのログの匿名化|はい|はい|
||継続的なリスク評価: アプリのリスク スコアと新しいアプリ アラート|はい||
||検出されたアプリのレポート|はい|はい|
||アプリ検出の異常検出|はい||
||すべてのアプリ カタログへのアクセス|はい||
||アプリ、ユーザー、IP アドレスごとの詳細なレポート|はい||
|情報の保護||||
||DLP のサポート|クロス SaaS DLP およびデータ共有制御|Office 365 DLP によって提供され、ASM でインシデントの表示と報告が可能|
||アプリのアクセス許可 - OAuth アプリを識別および制御|はい|はい|
||ポリシーの設定と適用|はい||
||Azure Information Protection の統合|はい||
||サード パーティの DLP ソリューションとの統合|はい||
|脅威の検出||||
||検出のカバレッジ|クロスアプリの包括的なアラート、脅威、違反ダッシュボード|Office 365 の異常検出およびセキュリティ警告|
||手動および自動のアラート修復|はい|はい|
||SIEM コネクタ|アラートとアクティビティ ログ|アラートのみ|
||Microsoft インテリジェント セキュリティ グラフ拡張機能|はい|はい|
||アクティビティ ポリシー|はい|はい|
||異常検出|はい|はい|

## <a name="see-also"></a>参照  

基本については、「[Cloud App Security の使用を開始する](getting-started-with-cloud-app-security.md)」をご覧ください。    
テクニカル サポートが必要な場合は、[Cloud App Security のサポート](http://support.microsoft.com/oas/default.aspx?prid=16031) ページをご利用ください。   
Premier サポートをご利用のお客様も、[Premier ポータル](https://premier.microsoft.com/)から直接 Cloud App Security を選択することができます。   

