---
title: "Cloud Discovery の異常検出ポリシー | Microsoft Docs"
description: "このトピックでは、Cloud Discovery の異常検出ポリシーの使用方法に関する情報を提供します。"
keywords: 
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: cloud-app-security
ms.technology: 
ms.assetid: eaf73af0-7610-4903-b656-8d90b1d2b18c
ms.reviewer: reutam
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 400741713d40422a3b1c7680663a572d18e9c692
ms.openlocfilehash: 132b4d296b26dd187418734b40d08ecb243692da


---

# <a name="cloud-discovery-anomaly-detection-policy"></a>Cloud Discovery 異常検出ポリシー
この記事は、ポリシーに関する参照の詳細です。各ポリシーの種類、およびポリシーごとに設定できるフィールドについて詳しく説明します。  
  
## <a name="cloud-discovery-anomaly-detection-policy-reference"></a>Cloud Discovery の異常検出ポリシーの参照  
Cloud Discovery の異常検出ポリシーを使用すると、クラウド アプリケーションの使用量の異常な増加を継続的に監視する機能をセットアップおよび構成できます。 各クラウド アプリケーションでのデータのダウンロードやアップロード、トランザクション数、ユーザー数の増加が対象となります。 いずれかが増加した場合、過去の使用状況から学習した通常の使用パターンと比較します。 特に極端に増加した場合は、セキュリティ アラートがトリガーされます。  
  
各ポリシーは、次の部分で構成されます。  
  
-   フィルター - アプリケーション フィルターやデータ ビュー、開始日を選択すると、アプリケーションの使用状況を選択的に監視できます。  
  
-   感度 - アラートによりポリシーがトリガーされるまでの回数を設定できます。  
  
### <a name="activity-filters"></a>アクティビティ フィルター  
アクティビティ フィルターのリストについては、「[アクティビティ](activity-filters.md)」を参照してください。  
  
### <a name="apply-to"></a>[適用先]  
監視対象の使用状況にフィルターを適用する方法は 2 つあります。  
  
-   データ ビュー: すべてのデータ ビューを監視するか (既定)、または特定のデータ ビューを選択して監視します。  
  
    -   **すべてのデータ ビュー**を選択すると、それぞれの使用量が増加した場合、すべてのデータ ビューから学習した通常の使用パターンと比較されます。  
  
    -   特定のデータ ビューを選択すると、それぞれの使用量が増加した場合、増加が見られたものと同じデータ ビューから学習した通常の使用パターンと比較されます。  
  
-   ユーザーと IP アドレス: それぞれのクラウド アプリケーションの使用状況は、ユーザーか IP アドレス、またはその両方に関連付けられています。  
  
    -   **ユーザー**を選択すると、アプリケーションの使用状況と IP アドレスが関連付けられていても無視されます。  
  
    -   **IP アドレス**を選択すると、アプリケーションの使用状況とユーザーが関連付けられていても無視されます。  
  
    -   **ユーザーと IP アドレス**を選択すると、この両方が対象となります。ユーザーと IP アドレスが緊密に対応している場合は、アラートが重複して生成されることがあります。  
  
指定の日付後に生じた疑わしいアクティビティに関してのみアラートを出す - いずれかのアプリケーションの使用量が増加しても、選択した日付よりも前であった場合は無視されます。 ただし、選択した日付より前のアクティビティも、通常の使用パターンを確立するための学習に使用されます。  
  
### <a name="sensitivity"></a>秘密度  
ポリシーでトリガーされるアラートの数を制御する方法は、2 つあります。  
  
-   感度スライダー - 1 週間、ユーザー数 1,000 人あたり何回のアラートがトリガーされるかを選択します。 特にリスクが高いアクティビティが検出されるとアラートがトリガーされます。  
  
-   日次アラート制限 - 1 日に発生するアラートの数を制限します。  
  
## <a name="see-also"></a>参照  
[クラウド環境を保護するための日常的な作業](daily-activities-to-protect-your-cloud-environment.md)   
[テクニカル サポートが必要な場合は、Cloud App Security のサポート ページをご利用ください。](http://support.microsoft.com/oas/default.aspx?prid=16031)   
[Premier サポートをご利用のお客様は、Premier ポータルから直接 Cloud App Security を選択することもできます。](https://premier.microsoft.com/)  
  
  


<!--HONumber=Nov16_HO5-->


