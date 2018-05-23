---
title: オンプレミス ファイル共有の GDPR
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
description: オンプレミスの Windows Server ファイル共有で GDPR の要件に対応する方法について説明します。
ms.openlocfilehash: d9d17f134d77ee03e11208744ba9a2e56d506b1f
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="gdpr-for-on-premises-windows-server-file-shares"></a>オンプレミスの Windows Server ファイル共有の GDPR

ファイル共有のための推奨される基本的なアプローチは、次のとおりです。

-   Azure Information Protection を使用して、機密データにラベルを付けます。

-   Azure Information Protection スキャナーを使用して、データを検索します。

ファイル共有のための推奨されるアプローチには、次の手順が含まれます。

1.  **Azure Information Protection スキャナーをインストールし、構成します。**

    -   使用する機密データの種類を決定します。

    -   使用するローカル フォルダーとネットワーク共有を指定します。

2.  **検出サイクルを完了します。**

    -   検出モードでスキャナーを実行し、検出結果を検証します。

    -   必要に応じて、条件と機密情報の種類を最適化します。

    -   自動的に適用されるラベルの予期される影響を評価します。

3.  **Azure Information Protection スキャナーを実行して、対象となるドキュメントにラベルを適用します**。

4.  **保護のために、**

    -   目的としたラベルのドキュメントを保護するための Exchange データ損失防止ルールを構成します。

    -   アクセス許可を使用して、ファイルにアクセスできるユーザーを制限するようにしてください。

5.  **監視のため、Windows Server のログを SIEM ツールに統合します。**

    -   データ主体要求の個人データを検索するため、Azure Information Protection スキャナーを使用します。また、ファイル共有をクロールするよう、SharePoint Server 検索を構成することもできます。

Azure Information Protection スキャナーを使用して個人データを検索したりラベル付けしたりすることに関する詳細については、[http://aka.ms/gdprpartners](<http://aka.ms/gdprpartners>) にある Microsoft GDPR Data Discovery Toolkit を参照してください。

さまざまな条件でスキャナーを構成すること、また Office 365 データ損失防止 (DLP) のさまざまな機密情報タイプを使用することに関する情報については、「[Azure Information Protection 用の自動および推奨分類の条件を構成する方法](https://docs.microsoft.com/ja-JP/information-protection/deploy-use/configure-policy-classification)」を参照してください。新しいタイプの Office 365 機密情報はスキャナーですぐに利用できるようになるわけではなく、カスタム機密情報タイプはスキャナーで使用できないことに注意ください。
