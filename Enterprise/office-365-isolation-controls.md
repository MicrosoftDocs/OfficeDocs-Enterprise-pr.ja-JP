---
title: Microsoft 365 分離コントロール
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
- M365-security-compliance
f1.keywords:
- NOCSH
description: Microsoft 365 で分離コントロールが動作する方法について説明します。これにより、必要に応じてサービス間での相互運用を行うことができます。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: da49d19371c0b7f704bf7cb1c4c83205b9cc9cb0
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605619"
---
# <a name="microsoft-365-isolation-controls"></a>Microsoft 365 分離コントロール 

Microsoft 365 のマルチテナントアーキテクチャが、エンタープライズレベルのセキュリティ、機密性、プライバシー、整合性、ローカル、国際、および可用性の[標準](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)をサポートしていることを確認するために、継続的に作業を行います。 Microsoft によって提供されるサービスの規模と範囲によって、Microsoft 365 を多大な人的介入で管理することは困難で、経済的ではありません。 Microsoft 365 サービスは、グローバルに分散された複数のデータセンターを介して提供され、それぞれ、ユーザーの介入を必要とする操作やお客様のコンテンツへのアクセスを必要とする運用の数が多くなります。 マイクロソフトのスタッフは、自動化ツールおよび高度なセキュリティで保護されたリモートアクセスを使用して、これらのサービスとデータセンターをサポートします。 

Microsoft 365 は、重要なビジネス機能を提供し、Microsoft の365環境全体に貢献する複数のサービスで構成されています。 これらのサービスはそれぞれ独立しており、互いに統合されるように設計されています。

Microsoft 365 は、次の原則を使用して設計されています。

 - **[サービス指向アーキテクチャ](https://docs.microsoft.com/previous-versions/aa480021(v=msdn.10)):** 適切に定義されたビジネス機能を提供する、相互運用可能なサービスという形でソフトウェアを設計し、開発します。
 - **運用時の[セキュリティ保証](https://www.microsoft.com/download/details.aspx?id=40872):** Microsoft の[セキュリティ開発ライフサイクル](https://www.microsoft.com/sdl/default.aspx)、 [microsoft セキュリティレスポンスセンター](https://technet.microsoft.com/library/dn440717.aspx)、cybersecurity の脅威に対する深い認識など、microsoft に固有のさまざまな機能によって得られた知識を組み込むフレームワーク。

Microsoft 365 サービスは相互に連携していますが、相互に依存しない独立したサービスとして展開および運用できるように設計および実装されています。 Microsoft segregates の職務および Microsoft 365 の責任範囲。組織の資産の改ざんまたは誤用の可能性を低減します。 Microsoft 365 teams では、役割ベースの総合的なアクセス制御メカニズムの一部として役割が定義されています。

## <a name="customer-content-isolation"></a>顧客コンテンツの分離

テナント内のすべてのお客様のコンテンツは、他のテナントから分離されています。また、Microsoft 365 の管理で使用されている運用およびシステムデータからは分離されています Microsoft 365 には複数の保護形態が実装されており、Microsoft 365 のサービスやアプリケーションが侵害される危険を最小限に抑えることができます。 複数の形式の保護では、テナントまたは Microsoft 365 システム自体の情報に対する権限のないアクセスも防止できます。

Microsoft 365 内のテナントデータの論理的分離を実装する方法については、「 [microsoft 365 のテナント分離](office-365-tenant-isolation-overview.md)」を参照してください。
