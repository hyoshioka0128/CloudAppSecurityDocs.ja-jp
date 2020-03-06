---
title: Microsoft Defender ATP を Cloud App Security に統合する
description: この記事では、Microsoft Defender Advanced Threat Protection を Cloud App Security に統合して、シャドウ IT およびリスク管理の可視性を向上させる方法について説明します。
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 12/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: d45711d5dfd5f0a7a3ae30df1e5e90425ff631ff
ms.sourcegitcommit: be2c558eee71de02ec29632fc58256d49de0f86f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78304882"
---
# <a name="microsoft-defender-advanced-threat-protection-integration-with-microsoft-cloud-app-security"></a>Microsoft Defender Advanced Threat Protection と Microsoft Cloud App Security の統合

*適用対象: Microsoft Cloud App Security*

Microsoft Cloud App Security は、Microsoft Defender Advanced Threat Protection (ATP) とネイティブに統合されます。 統合により、Cloud Discovery のロールアウトが簡略化され、企業ネットワークを超えた Cloud Discovery 機能が拡張され、コンピューターベースの調査が可能になります。 [Microsoft DEFENDER ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)は、インテリジェントな保護、検出、調査、および対応を行うためのセキュリティプラットフォームです。 Microsoft Defender ATP は、サイバー脅威からのエンドポイントを保護し、高度な攻撃とデータ侵害を検出し、セキュリティインシデントを自動化し、セキュリティ体制を強化します。

Cloud App Security は、IT が管理する Windows 10 コンピューターからアクセスされるクラウドアプリとサービスについて、Microsoft Defender ATP によって収集されたトラフィック情報を使用します。 ネイティブ統合を使用すると、企業ネットワーク内の任意のコンピューターで、パブリック Wi-fi、ローミング中、およびリモートアクセス経由で Cloud Discovery を実行できます。 また、コンピューターベースの調査も有効にします。

統合では、追加のデプロイは不要であり、すぐに使用できます。 エンドポイントからのトラフィックをルーティングまたはミラー化したり、複雑な統合手順を実行したりする必要はありません。 Cloud App Security に送信されたエンドポイントからのログは、トラフィックアクティビティのユーザー情報を提供します。 Microsoft Defender ATP ネットワークアクティビティは、デバイスコンテキストを提供します。 デバイスコンテキストとユーザー名をペアリングすると、ネットワーク全体で全体像が得られるため、どのユーザーがどのコンピューターからどの操作を行ったかを特定できます。

さらに、危険なユーザーを特定するときに、ユーザーがアクセスしたすべてのコンピューターを確認して、潜在的なリスクを検出することができます。 危険なコンピューターを特定した場合は、それを使用しているすべてのユーザーを確認し、潜在的なリスクをさらに検出します。

トラフィック情報が収集されると、組織での[クラウドアプリの使用を詳細に把握](discovered-apps.md#deep-dive-into-discovered-apps)することができます。 Cloud App Security は、Microsoft Defender ATP ネットワーク保護機能を利用して、エンドポイントデバイスからクラウドアプリへのアクセスをブロックします。 ポータルで承認され[ていないものとしてタグ付け](governance-discovery.md#BKMK_SanctionApp)することで、アプリをブロックできます。 承認されていない各アプリの包括的な使用状況とリスクの評価に基づいて、アプリのドメインを使用して、Microsoft Defender ATP ポータルで[ドメインインジケーター](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview)を作成します。 エンドポイントデバイスで実行されている Windows Defender ウイルス対策は、ドメインインジケーターを使用して、これらのアプリへのアクセスをブロックします。

> [!NOTE]
> Microsoft Defender ATP を体験する場合は、 [無料試用版にサインアップして](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)ください。

## <a name="prerequisites"></a>前提条件

- Microsoft Cloud App Security ライセンス
- Microsoft Defender ATP ライセンス
- Windows 10 バージョン 1709 (OS Build 16299.1085 with KB4493441)、Windows 10 version 1803 (OS Build 17134.704 with KB4493464)、Windows 10 version 1809 (OS Build 17763.379 with KB4489899)、またはそれ以降のバージョンの Windows 10
- Windows Defender ウイルス対策
  - [リアルタイム保護が有効](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/configure-real-time-protection-windows-defender-antivirus)
  - [クラウドで提供される保護の有効化](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/enable-cloud-protection-windows-defender-antivirus)
  - [ネットワーク保護が有効になっており、ブロックモードに構成されています](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)

## <a name="how-it-works"></a>しくみ

Cloud App Security は、[アップロードしたログ](create-snapshot-cloud-discovery-reports.md)を使用するか、[自動ログアップロードを構成](discovery-docker.md)することにより、エンドポイントからログを収集します。 ネイティブ統合を使用すると、Windows で実行されるときに Microsoft Defender ATP のエージェントが作成するログを利用し、ネットワークトランザクションを監視できます。 この情報は、ネットワーク上の Windows コンピューター全体のシャドウ IT 検出に使用します。

他のプラットフォーム間で Cloud Discovery を実行できるようにするには、Windows 10 コンピューターを監視するために、Cloud App Security [log collector](discovery-docker.md)と MICROSOFT Defender ATP 統合の両方を使用することをお勧めします。

## <a name="how-to-integrate-microsoft-defender-atp-with-cloud-app-security"></a>Microsoft Defender ATP を Cloud App Security に統合する方法

Cloud App Security との Microsoft Defender ATP 統合を有効にするには:

1. Microsoft Defender ATP ポータルのナビゲーションウィンドウで、設定 **セットアップ** の順番に選択します。
2. **[設定]** メニューの **[全般]** で、 **[高度な機能]** を選択します。
3. **Microsoft Cloud App Security**を**On**に切り替えます。
4. **[設定の保存]** をクリックします。

>[!NOTE]
> データが Cloud App Security に表示されるようにするには、統合を有効にした後最大2時間かかります。
>

![WD ATP の設定](media/wdatp-settings.png)

## <a name="investigate-machines-in-cloud-app-security"></a>Cloud App Security 内のマシンを調査する

Microsoft Defender ATP を Cloud App Security に統合したら、Cloud Discovery ダッシュボードで検出されたマシンデータを調査できます。

1. Cloud App Security ポータルで、 **Cloud Discovery**をクリックし、ダッシュボード を**Cloud Discovery**します。
2. 上部のナビゲーションバーの **[継続的なレポート]** で、 **[Win10 endpoint users]** を選択します。
  ![WD ATP レポート](media/win10-dashboard-report.png)
3. 上部には、統合後に検出されたコンピューターの数が表示されます。
4. **[マシン]** タブをクリックします。
5. 一覧に表示されている各コンピューターにドリルダウンし、そのタブを使用して調査データを表示できます。 インシデントに関係していたコンピューター、ユーザー、IP アドレス、アプリ間の相関関係を見つけます。

    - **概要**
        - トランザクション: 選択した期間にコンピューターで発生したトランザクションの数に関する情報。
        - 合計トラフィック数: 選択した期間のトラフィックの総量 (MB 単位) に関する情報。
        - アップロード: 選択した期間にマシンによってアップロードされたトラフィックの総量 (MB 単位) に関する情報。
        - ダウンロード: 選択した期間にコンピューターによってダウンロードされたトラフィックの総量 (MB 単位) に関する情報。
    - **検出されたアプリ**  
  コンピューターによってアクセスされた、検出されたすべてのアプリを一覧表示します。
    - **ユーザーの履歴**  
    コンピューターにサインインしているすべてのユーザーを一覧表示します。
    - **IP アドレスの履歴**  
    コンピューターに割り当てられているすべての IP アドレスを一覧表示します。
 ![マシンの概要](media/machines-overview.png)

他の Cloud Discovery ソースと同様に、Win10 エンドポイントユーザーレポートからデータをエクスポートして、さらなる調査を行うことができます。

> [!NOTE]
>
> - Microsoft Defender ATP は、最大 4 MB のチャンク単位で Cloud App Security にデータを転送します (約4000エンドポイントトランザクション)
> - 1時間以内に 4 MB の制限に達していない場合、Microsoft Defender ATP は、過去1時間に実行されたすべてのトランザクションを報告します。
> - エンドポイントデバイスがフォワードプロキシの背後にある場合、トラフィックの量は Microsoft Defender ATP に表示されないため、Cloud Discovery レポートには含まれません。 詳細については、「[転送プロキシの背後にあるネットワーク接続の監視](https://techcommunity.microsoft.com/t5/Microsoft-Defender-ATP/MDATP-Monitoring-network-connection-behind-forward-proxy-Public/ba-p/758274)」を参照してください。

## <a name="block-access-to-unsanctioned-cloud-apps"></a>承認されていないクラウドアプリへのアクセスをブロックする

Cloud App Security は、組み込みの承認されてい[**ないアプリタグ**](governance-discovery.md#BKMK_SanctionApp)を使用して、クラウドアプリを使用禁止としてマークします。これは、Cloud Discovery とクラウドアプリカタログの両方のページで使用できます。 Microsoft Defender ATP との統合を有効にすることで、Cloud App Security ポータルで1回クリックするだけで、承認されていないアプリへのアクセスをシームレスにブロックできます。

### <a name="how-it-works"></a>しくみ

Cloud App Security で未承認**とマーク**されているアプリは、通常数分以内に MICROSOFT Defender ATP に自動的に同期されます。 具体的には、承認されていないアプリによって使用されるドメインは、ネットワーク保護の SLA 内で Windows Defender ウイルス対策によってブロックされるエンドポイントデバイスに伝達されます。

### <a name="how-to-enable-cloud-app-blocking-with-microsoft-defender-atp"></a>Microsoft Defender ATP を使用してクラウドアプリのブロックを有効にする方法

クラウドアプリのアクセス制御を有効にするには、次の手順に従います。

1. Cloud App Security の設定歯車で、**設定** を選択し、 **Cloud Discovery** **Microsoft Defender ATP** を選択し、承認されていない**アプリをブロック**する を選択します。

    ![Microsoft Defender ATP を使用してブロックを有効にする方法を示すスクリーンショット](media/defender-atp-integration.png)

1. Microsoft Defender Security Center で、 **[設定]** [ > の**詳細機能**] の順に選択し、 **[カスタムネットワークインジケーター]** を選択します。 ネットワークインジケーターの詳細については、「 [ip および url/ドメインのインジケーターを作成](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/manage-indicators#create-indicators-for-ips-and-urlsdomains-preview)する」を参照してください。

    これにより、Windows Defender ウイルス対策ネットワーク保護機能を利用して、特定のアプリに[アプリタグ](governance-discovery.md#BKMK_SanctionApp)を手動で割り当てるか、[アプリ検出ポリシー](cloud-discovery-policies.md#creating-an-app-discovery-policy)を自動的に使用することで、Cloud App Security を使用して事前定義された一連の url へのアクセスをブロックできます。

    ![Microsoft Defender ATP でカスタムネットワークインジケーターを有効にする方法を示すスクリーンショット](media/defender-atp-custom-network-indicators.png)

## <a name="investigate-unsanctioned-apps-in-microsoft-defender-security-center"></a>Microsoft Defender Security Center で未承認のアプリを調査する

承認されていないアプリにアクセスしようとするたびに、Microsoft Defender Security Center のアラートがトリガーされ、セッション全体の詳細が表示されます。 これにより、承認されていないアプリへのアクセスをさらに詳細に調査したり、エンドポイントデバイスの調査に使用する追加の関連情報を提供したりできます。

エンドポイントデバイスが正しく構成されていない場合、または強制ポリシーがエンドポイントにまだ反映されていない場合は、承認されていないアプリへのアクセスがブロックされないことがあります。 このインスタンスでは、Microsoft Defender ATP 管理者は、承認されていないアプリがブロックされていないことを Security Center Microsoft Defender にアラートを受け取ります。

![Microsoft Defender ATP の承認されていないアプリの警告を示すスクリーンショット](media/defender-atp-unsanctioned-app-alert.png)

> [!NOTE]
>
> - アプリをエンドポイントデバイスに伝達するためにアプリドメイン**に対して**承認されていないとして、アプリにタグを付けると、最大2時間かかります。
> - 既定では、Cloud App Security で未承認とマークされ**ているアプリ**とドメインは、組織内のすべてのエンドポイントデバイスに対してブロックされます。
> - 現時点では、承認されていないアプリでは完全な Url はサポートされていません。 そのため、完全な Url で構成されたアプリを却下する場合、それらは Microsoft Defender ATP に反映されず、ブロックされません。 たとえば、`google.com/drive` はサポートされていませんが、`drive.google.com` はサポートされています。
> - ブラウザー間の通知は、ブラウザーによって異なる場合があります。

## <a name="next-steps"></a>次のステップ:

> [!div class="nextstepaction"]
> [ポリシーによるクラウド アプリの制御](control-cloud-apps-with-policies.md)

## <a name="related-videos"></a>関連ビデオ

> [!div class="nextstepaction"]
> [企業ネットワークを超えたシャドウ IT 検出](https://www.youtube.com/watch?v=f8hbvbY1Hnc)

[!INCLUDE [Open support ticket](includes/support.md)]
