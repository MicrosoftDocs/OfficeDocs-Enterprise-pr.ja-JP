---
title: Office 365 管理アクティビティ API
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-analytics
f1.keywords:
- NOCSH
description: Office 365 Management Activity API についての簡単な概要。
ms.openlocfilehash: 8c7e4723ffb1792847c4b4eca0ec8285b8848c98
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998676"
---
# <a name="office-365-management-activity-api"></a>Office 365 管理アクティビティ API

Microsoft では、Office 365 テナントに関する集計されたトランザクション情報を取得するために使用できるレポートサービスを提供しています。 [Office 365 Management ACTIVITY API](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview#office-365-management-activity-api)は、業界標準の RESTful 設計および OAuth v2 を使用して認証を行います。 これにより、データの取得や、視覚エフェクトのツールやアプリケーションへの取り込むを簡単に実行できるようになります。 API は、Office 365 のユーザー、管理者、操作、およびセキュリティアクティビティに関する情報をデータフィードに提供します。 このデータは、規制目的のため、またはオンプレミスのインフラストラクチャまたは他のソースから調達されたログデータと組み合わせて保持できます。 これにより、企業全体にわたる運用、セキュリティ、およびコンプライアンスの監視ソリューションを構築できます。

Office 365 管理アクティビティ API は、Office 365 と Azure Active Directory のアクティビティ ログからの、ユーザー、管理者、システム、およびポリシー アクションとポリシー イベントについての情報を提供します。 この API は、すべてのサービスに共通の10個を超えるフィールドを持つ一貫性のある監査スキーマを提供します。 この API を使用すると、組織はイベント間の簡単な接続を確立し、新しい方法でデータを理由にすることができます。

多数の独立系ソフトウェアベンダー (Isv) が Microsoft と提携しており、API に基づくソリューションを構築しています。 一部のソリューションでは、Office 365 データと、複数のクラウドプロバイダーおよびオンプレミスシステムからのソースデータのみに焦点を合わせて、運用、セキュリティ、コンプライアンスに関連するアクティビティの統合されたビューを作成します。 

詳細については、「 [Office 365 Management ACTIVITY API リファレンス](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference)」を参照してください。
