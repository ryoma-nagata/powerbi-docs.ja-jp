---
title: Power BI Premium の購入方法
description: Power BI Premium を購入し、組織全体にコンテンツへのアクセスを可能する方法について説明します。
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/12/2019
LocalizationGroup: Premium
ms.openlocfilehash: b9681b15b0eef4415849b59e903440f9d904b1f6
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "73856877"
---
# <a name="how-to-purchase-power-bi-premium"></a>Power BI Premium の購入方法

> [!NOTE]
> この記事は現在、新機能について追記したり、詳細を提供したり、読みやすくしたりするために更新中です。 

この記事では、組織に Power BI Premium の容量 (P1-P3) を購入する方法について説明します。 Power BI Premium 容量は Microsoft 365 管理センターで購入します。また、ご自分の容量は Power BI 管理ポータルで管理します。 現在の価格と計画については、[Power BI の料金ページ](https://powerbi.microsoft.com/pricing/)および「[Power BI Premium 計算ツール](https://powerbi.microsoft.com/calculator/)」を参照してください。

組織が Power BI Premium を使用する場合でも、コンテンツの作成者には Power BI Pro のライセンスが引き続き必要です。 組織で Power BI Pro ライセンスを少なくとも 1 つ購入してください。

Premium サブスクリプションの有効期限が切れてから 30 日間は、容量への完全なアクセス権があります。 その後、コンテンツは共有された容量に戻ります。 1 GB を超えるモデルは、共有された容量ではサポートされません。

## <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Power BI Premium P1 で新しいテナントを作成する

既存のテナントをお持ちでない場合は、テナントの作成と同時に Power BI Premium も購入することができます。 次のリンクをクリックすると、新しいテナントを作成するプロセスが案内され、Power BI Premium を購入することができます:[Power BI Premium P1 オファー](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1)。 テナントを作成すると、そのテナントの Microsoft 365 の全体管理者ロールに自動的に割り当てられます。

## <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>既存の組織用の Power BI Premium 容量を購入する

既存の組織 (テナント) をお持ちの場合、サブスクリプションとライセンスを購入するには、Microsoft 365 の全体管理者ロールまたは課金管理者ロールである必要があります。 詳細については、[Microsoft 365 の管理者ロールについて](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)のページを参照してください。

Premium 容量を購入するには、以下の手順に従います。

1. Power BI サービス内で、[Microsoft 365 アプリ ピッカー]、 **[管理者]** の順に選択します。

    ![Microsoft 365 アプリ ピッカー](media/service-admin-premium-purchase/o365-app-picker.png)

    または、Microsoft 365 管理センターを参照することができます。 管理センターにアクセスするには、 https://portal.office.com に移動して **[管理者]** を選択します。

1. **[請求]**  >  **[サービスを購入する]** を選択します。

1. **[その他のプラン]** で、Power BI Premium のオファーを探します。 これは P1 ～ P3、EM3、および P1 (月極め) として一覧表示されます。

1. 省略記号 ( **. . .** ) にポインターを合わせ、 **[今すぐ購入する]** を選択します。

    ![今すぐ購入](media/service-admin-premium-purchase/premium-purchase.png)

1. 以下の手順に従って、購入を完了します。

購入を完了すると、 **[サービスを購入する]** ページに購入したアクティブな項目が表示されます。

![Power BI Premium を購入した場合](media/service-admin-premium-purchase/premium-purchased.png)

## <a name="purchase-additional-capacities"></a>追加の容量を購入する

これで容量を購入できたので、ニーズの高まりに合わせてさらに容量を追加できます。 組織内で Premium 容量 SKU の任意の組み合わせ (P1 から P3) を使用できます。 異なる SKU は異なるリソース機能を提供します。

1. Microsoft 365 管理センターで、 **[課金]**  >  **[サービスを購入する]** の順に選択します。

1. **[その他のプラン]** で、追加購入する Power BI Premium の項目を探します。

1. **その他のオプション** (...) にポインターを合わせ、 **[ライセンス数の変更]** を選択します。

    ![ライセンス数の変更](media/service-admin-premium-purchase/premium-purchase-more.png)

1. この項目に必要なインスタンス数を変更します。 完了したら **[送信]** を選択します。

   > [!IMPORTANT]
   > **[送信]** を選択すると、登録されているクレジット カードに課金されます。

**[サービスを購入する]** ページに、所有しているインスタンス数が表示されます。 Power BI 管理ポータルの **[容量の設定]** で、購入した新しい容量が利用可能な仮想コア数に反映されます。

![Power BI Premium 容量の利用可能な仮想コア数](media/service-admin-premium-purchase/premium-capacities.png)

## <a name="cancel-your-subscription"></a>サブスクリプションをキャンセルする

Microsoft 365 管理センターから、ご自分のサブスクリプションをキャンセルすることができます。 Premium サブスクリプションをキャンセルするには、次の操作を行います。

1. Microsoft 365 管理センターを参照します。

1. **[請求]**  >  **[サブスクリプション]** の順に選択します。

1. 一覧から Power BI Premium サブスクリプションを選択します。

1. **[More actions]\(その他の操作\)**  >  **[サブスクリプションのキャンセル]** の順に選択します。

1. **[サブスクリプションのキャンセル]** ページに [中途解約料](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3) を支払う必要があるかどうかが表示されます。 このページでは、サブスクリプションのデータが削除されるタイミングを確認することもできます。

1. 情報に目を通し、続行する場合は、 **[サブスクリプションのキャンセル]** を選択します。

### <a name="when-canceling-or-your-license-expires"></a>キャンセルした場合、またはライセンスが期限切れになった場合

Premium サブスクリプションをキャンセルした場合、または容量のライセンスが期限切れになった場合でも、その日から 30 日間は、Premium 容量に引き続きアクセスできます。 30 日が経過すると、Premium 容量やその中のワークスペースにアクセスできなくなります。

## <a name="next-steps"></a>次の手順

[Power BI Premium で容量を構成および管理する](service-admin-premium-manage.md)\
[Power BI の料金ページ](https://powerbi.microsoft.com/pricing/)\
[Power BI Premium 計算ツール](https://powerbi.microsoft.com/calculator/)\
[Power BI Premium のよくあるご質問](service-premium-faq.md)\
[Power BI のエンタープライズ展開の計画に関するホワイト ペーパー](https://aka.ms/pbienterprisedeploy)

他にわからないことがある場合は、 [Power BI コミュニティで質問してみてください](https://community.powerbi.com/)。
