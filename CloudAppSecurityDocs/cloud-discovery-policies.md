---
title: Cloud Discovery アプリに対するポリシーを作成する - Cloud App Security | Microsoft ドキュメント
description: この記事では、Cloud Discovery ポリシーの使用に関する情報を提供します。
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
ms.assetid: 45446111-ed1a-4699-9df5-840cc6664a6b
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 274dace6a7d6c4b1e083f689568d4e9247f3c44a
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2019
ms.locfileid: "74461237"
---
# <a name="cloud-discovery-policies"></a>Cloud Discovery ポリシー

*適用対象: Microsoft Cloud App Security*

新しいアプリが検出されたときに通知する、アプリの検出ポリシーを作成できます。 Cloud App Security では、Cloud Discovery 内のすべてのログの異常も検索されます。 

## <a name="creating-an-app-discovery-policy"></a>アプリの検出ポリシーの作成  
検出ポリシーを使用すると、組織内で新しいアプリが検出されたことを知らせる警告を設定することができます。  
  
1. コンソールで、 **[制御]** 、 **[ポリシー]** の順にクリックします。  
  
2. **[ポリシーの作成]** をクリックしてから **[アプリの検出]** ポリシーを選択します。  
  
     ![アプリ検出ポリシーメニュー](./media/app-discovery-policy-menu.png "アプリ検出ポリシーのメニュー")  
  
3. ポリシーに名前と説明を指定します。 必要に応じて、テンプレートを使用することができます。 ポリシー テンプレートの詳細については、「[Control cloud apps with policies](control-cloud-apps-with-policies.md)」(ポリシーによるクラウド アプリの制御) を参照してください。  
  
4. ポリシーの **[重要度]** を設定します。

5. どのアプリが検出されたらこのポリシーをトリガーするか設定するには、フィルターを追加します。  
  
6. ポリシーの感度については、しきい値を設定できます。 **[Trigger a policy match if all the following occur on the same day]** \(以下のすべてが同じ日に起こった場合にポリシーの一致をトリガーする\) を有効にします。 ポリシーに一致するにはアプリが毎日超えなくてはならない条件を設定できます。 次のいずれかの条件を選択します。 
     - 毎日のトラフィック
     - ダウンロードされたデータ
     - IP アドレスの数
     - トランザクション数
     - ユーザー数
     - アップロードされたデータ

  
7. **[アラート]** の **[日次アラート制限]** を設定します。 アラートを電子メール、テキスト メッセージ、またはその両方で送信するかどうかを選択します。 その後、必要に応じて、電話番号とメール アドレスを入力します。
     - **[Save alert settings as the default for your organization]** \(アラートの設定を組織の既定として保存\) をクリックすると、設定を使用するための将来のポリシーが有効になります。
     - 既定の設定がある場合は、 **[Use your organization's default settings]** \(組織の既定の設定を使用する\) を選択できます。
  
8. アプリがこのポリシーと一致したときに適用する、**ガバナンス** アクションを選択します。 これによって、ポリシーに **[承認された]** 、 **[承認されていない]** 、またはカスタム タグを付けることができます。 

9. **[作成]** をクリックします。  
  
たとえば、クラウド環境内における危険なホスティング アプリを検出することに関心がある場合には、次のようにポリシーを設定します。  
  
**[ホスティング サービス]** カテゴリで発見された、高い危険性を示すリスク スコア 1 のサービスを検出するポリシー フィルターを設定します。

 下部にある特定の検出されたアプリに対してアラートをトリガーするしきい値を設定します。 たとえば、環境内でアプリを使用したユーザーが 100 名を超えた場合や、サービスから特定のデータ量がダウンロードされた場合にのみ通知することができます。
さらに、1 日に受信するアラート数を設定することもできます。  
  
![アプリ検出ポリシーの例](./media/app-discovery-policy-example.png "アプリ検出ポリシーの例")  
  
## <a name="cloud-discovery-anomaly-detection"></a>Cloud Discovery の異常検出

Cloud App Security では、Cloud Discovery 内のすべてのログを対象に異常が検索されます。 たとえば、これまでに Dropbox を使用したことのないユーザーが突然 600 GB のファイルを Dropbox にアップロードしたり、特定のアプリで通常よりもはるかに多くのトランザクションが発生していたりする場合などに通知します。 異常検出ポリシーは、既定で有効になっています。 新しいポリシーを構成しなくても動作します。 ただし、既定のポリシーの通知する異常の種類を微調整することができます。  
  
1. コンソールで、 **[制御]** 、 **[ポリシー]** の順にクリックします。  
  
2. **[ポリシーの作成]** をクリックしてから **[Cloud Discovery 異常検出ポリシー]** を選択します。  
  
     ![cloud discovery 異常検出ポリシーメニュー](./media/cloud-discovery-anomaly-detection-policy-menu.png "Cloud Discovery 異常検出ポリシーのメニュー")  
  
3. ポリシーに名前と説明を指定します。 必要に応じて、ポリシー テンプレートを使用することもできます。ポリシー テンプレートの詳細については、「[Control cloud apps with policies](control-cloud-apps-with-policies.md)」(ポリシーによるクラウド アプリの制御) を参照してください。  
  
4. どのアプリが検出されたらこのポリシーがトリガーされるかを設定するには、 **[フィルターの追加]** をクリックします。  
  
     フィルターをドロップダウン リストから選択します。 フィルターを追加するには、[+] ボタンをクリックします。 フィルターを削除するには、[X] をクリックします。 
  
5. **[Apply to]** \(適用の対象\) で、このポリシーを **[All continuous reports]** \(すべての継続的レポート\) と **[Specific continuous reports]** \(特定の継続的レポート\) のどちらに適用するかを選択します。 ポリシーを **[ユーザー]** 、 **[IP アドレス]** 、またはその両方に適用するかどうかを選択します。  
  
6. **[指定の日付後に生じた疑わしいアクティビティに関してのみアラートを出す]** で、異常なアクティビティに対してアラートをトリガーする期間を選択します。  
  
7. **[アラート]** の **[日次アラート制限]** を設定します。 アラートを電子メール、テキスト メッセージ、またはその両方で送信するかどうかを選択します。 その後、必要に応じて、電話番号とメール アドレスを入力します。
     - **[Save alert settings as the default for your organization]** \(アラートの設定を組織の既定として保存\) をクリックすると、設定を使用するための将来のポリシーが有効になります。
     - 既定の設定がある場合は、 **[Use your organization's default settings]** \(組織の既定の設定を使用する\) を選択できます。
  
8. **[作成]** をクリックします。  
  
![新しい検出異常ポリシー](./media/new-discovery-anomaly-policy.png "新しい異常検出ポリシー")  
  
## <a name="next-steps"></a>次の手順 
[ユーザー アクティビティ ポリシー](user-activity-policies.md)   

[!INCLUDE [Open support ticket](includes/support.md)]  
  
  
