---
title: サービス中断の通知
description: Power BI サービスの中断または低下が発生したときに、電子メール通知を受信する方法について学習します。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/17/2020
ms.author: kfollis
ms.openlocfilehash: 85b26b68c4943e0bc100be7a298730cec34cfc78
ms.sourcegitcommit: d43761104f7daf4b2f297648855bb573b53e6d8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2020
ms.locfileid: "81637770"
---
# <a name="service-interruption-notifications"></a>サービス中断の通知

ミッション クリティカルなビジネス アプリケーションの可用性についての分析情報を得ることが重要です。 サービスの中断や低下がある場合に、必要に応じて電子メールを受け取ることができるように、Power BI でインシデント通知が提供されます。 Power BI の 99.9% のサービス レベル アグリーメント (SLA) では、これらはめったに発生しませんが、常に確実に通知されるようにする必要があります。 次のスクリーンショットは、通知を有効にした場合に受信する電子メールの種類を示しています。

![通知用電子メールの更新](media/service-interruption-notifications/refresh-notification-email.png)

現時点では、次の_信頼性のシナリオ_について電子メールを送信しています。

- レポートを開くの信頼性
- モデルの更新の信頼性
- クエリの更新の信頼性

通知は、レポートの表示、データセットの更新、クエリの実行といった操作で "_長い待ち時間_" が生じると送信されます。 インシデントが解決されると、フォローアップの電子メールを受信します。

> [!NOTE]
> 現在、この機能は Power BI Premium の専用容量に対してのみ使用できます。 共有や埋め込み容量には使用できません。





## <a name="enable-notifications"></a>通知を有効にする

Power BI テナント管理者は、管理ポータルで通知を有効にします。

1. 通知を受信する電子メールが有効なセキュリティ グループを特定または作成します。

1. 管理ポータルで、 **[テナント設定]** を選択します。 **[ヘルプとサポートの設定]** で、 **[サービスの停止またはインシデントに関する電子メール通知を受け取る]** を展開します。

1. 通知を有効にし、セキュリティ グループを入力して、 **[適用]** を選択します。

    ![サービスの通知を有効にする](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> Power BI では、アカウント no-reply-powerbi@microsoft.com から通知が送信されます。 通知は迷惑メール フォルダーに入らないように、確実にこのアカウントをホワイトリストに登録してください。

## <a name="next-steps"></a>次の手順

[Power BI Pro と Power BI Premium のサポート オプション](service-support-options.md)

他にわからないことがある場合は、 [Power BI コミュニティを利用してください](https://community.powerbi.com/)。
