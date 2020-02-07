---
title: Office 365 での分離コントロール
ms.author: robmazz
author: robmazz
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
description: '概要: Office 365 内の分離コントロールについて説明します。'
ms.openlocfilehash: e5ce9f2b581c49f3c08803034bc526b2fdb91a9a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844448"
---
# <a name="office-365-isolation-controls"></a>Office 365 での分離コントロール 

Microsoft は、Office 365 のマルチテナントアーキテクチャが、エンタープライズレベルのセキュリティ、機密性、プライバシー、整合性、ローカル、国際、および可用性の[標準](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)をサポートしていることを継続的に実現しています。 Microsoft によって提供されるサービスの規模と範囲によって、Office 365 を多大な人的介入で管理することが困難で、経済的ではありません。 Office 365 サービスは、グローバルに分散された複数のデータセンターを通じて提供され、それぞれ、ユーザーの介入を必要とする操作やお客様のコンテンツへのアクセスを必要とする操作の数が多くなります。 マイクロソフトのスタッフは、自動化ツールおよび高度なセキュリティで保護されたリモートアクセスを使用して、これらのサービスとデータセンターをサポートします。 大規模サービスが Office 365 でどのように動作するかに関する詳細については、「 [office 365 FOR IT 担当者向けの背景](https://channel9.msdn.com/Events/SharePoint-Conference/2014/SPC202)」を参照してください。

Office 365 は、重要なビジネス機能を提供し、Office 365 環境全体に貢献する複数のサービスで構成されています。 これらのサービスはそれぞれ独立しており、互いに統合されるように設計されています。

Office 365 は、次の原則に従って設計されています。

 - **[サービス指向アーキテクチャ](https://msdn.microsoft.com/library/aa480021.aspx):** 適切に定義されたビジネス機能を提供する、相互運用可能なサービスという形でソフトウェアを設計し、開発します。
 - **運用時の[セキュリティ保証](https://www.microsoft.com/download/details.aspx?id=40872):** Microsoft の[セキュリティ開発ライフサイクル](https://www.microsoft.com/sdl/default.aspx)、 [microsoft セキュリティレスポンスセンター](https://technet.microsoft.com/library/dn440717.aspx)、cybersecurity の脅威に対する深い認識など、microsoft に固有のさまざまな機能によって得られた知識を組み込むフレームワーク。

Office 365 サービス間で相互運用されていますが、相互に依存しない独立したサービスとして展開および運用できるように設計および実装されています。 Microsoft segregates の職務および Office 365 の責任範囲によって、組織の資産の改ざんまたは誤用の可能性を低減します。 Office 365 teams は、役割ベースの総合的なアクセス制御メカニズムの一部として役割を定義しています。

## <a name="customer-content-isolation"></a>顧客コンテンツの分離

テナント内のすべてのお客様のコンテンツは、他のテナントから分離されています。また、Office 365 の管理で使用されている運用およびシステムデータから分離されています。 Office 365 には複数の形式の保護が実装されており、Office 365 サービスまたはアプリケーションの侵害のリスクを最小限に抑えることができます。 複数の形式の保護では、テナントまたは Office 365 システム自体の情報に対する権限のないアクセスも防止できます。

Microsoft が Office 365 内のテナントデータの論理的分離を実装する方法については、「 [office 365 のテナント分離](office-365-tenant-isolation-overview.md)」を参照してください。
