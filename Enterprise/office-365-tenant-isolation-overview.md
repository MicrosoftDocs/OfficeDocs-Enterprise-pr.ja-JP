---
title: Microsoft 365 でのテナントの分離
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
description: Microsoft 365 でテナントの分離を適用する方法の概要について説明します。
ms.openlocfilehash: 891fdb9bebb500c40a9658d170942ca396facfd1
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998646"
---
# <a name="tenant-isolation-in-microsoft-365"></a>Microsoft 365 でのテナントの分離

クラウドコンピューティングの主な利点の1つは、同時に多数のお客様に共通する共有インフラストラクチャの概念で、スケールの経済につながることです。 この概念を*マルチテナント*と呼びます。 Microsoft は、クラウドサービスのマルチテナントアーキテクチャがエンタープライズレベルのセキュリティ、機密性、プライバシー、整合性、および可用性の標準をサポートするように継続的に取り組みます。

[信頼できるコンピューティング](https://www.microsoft.com/trust-center)および[セキュリティ開発ライフサイクル](https://www.microsoft.com/securityengineering/sdl/)から得られる重要な投資と経験に基づいて、Microsoft cloud services は、すべてのテナントが他のすべてのテナントに悪影響を与える可能性があることを前提として設計されており、1つのテナントのアクションが別のテナントのセキュリティまたはサービスに影響を与えたり、別のテナントのコンテンツ

マルチテナント環境でテナントの分離を維持するための主な目標は次の2つです。

1.  テナント間での顧客コンテンツの漏洩、または不正アクセスを防止する。そして
2.  あるテナントのアクションが別のテナントのサービスに悪影響を及ぼすことを防ぐ

Microsoft 365 には複数の形式の保護が実装されており、お客様が Microsoft 365 のサービスまたはアプリケーションを侵害したり、他のテナントまたは Microsoft 365 システム自体の情報に無許可でアクセスしたりすることを防ぐことができます。

- Microsoft 365 サービス用の各テナント内の顧客コンテンツの論理的分離は、Azure Active Directory の承認と役割ベースのアクセス制御によって実現されます。
- SharePoint Online は、データ分離メカニズムをストレージレベルで提供します。
- Microsoft は、厳密な物理的なセキュリティ、背景審査、および複数層の暗号化戦略を使用して、顧客のコンテンツの機密性と整合性を保護しています。 すべての Microsoft 365 データセンターには、バイオメトリクスアクセスコントロールがあり、ほとんどの場合、物理的なアクセスを得るために palm 印刷が要求されています。 また、米国のすべての Microsoft の従業員は、雇用プロセスの一環として、標準のバックグラウンドチェックを正常に完了する必要があります。 Microsoft 365 での管理アクセスに使用されるコントロールの詳細については、「 [microsoft 365 管理アクセス制御](office-365-administrative-access-controls-overview.md)」を参照してください。
- Microsoft 365 は、BitLocker、ファイル暗号化、トランスポート層セキュリティ (TLS)、およびインターネットプロトコルセキュリティ (IPsec) を含む、お客様のコンテンツを保存し、送信中で暗号化するサービス側のテクノロジを使用しています。 Microsoft 365 での暗号化の詳細については、「 [microsoft 365 のデータ暗号化テクノロジ](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview)」を参照してください。

これらの保護によって、物理的な分離だけで提供される脅威の保護と軽減対策を提供する、堅牢な論理的分離コントロールが提供されます。

## <a name="related-links"></a>関連リンク

- [Azure Active Directory での分離とアクセス制御](office-365-isolation-in-azure-active-directory.md)
- [Office Graph と Delve でのテナントの分離](office-365-isolation-in-graph-and-delve.md)
- [Microsoft 365 検索でのテナントの分離](office-365-isolation-in-office-365-search.md)
- [Office 365 でのテナントの分離のビデオ](office-365-isolation-in-office-365-video.md)
- [リソースの制限](office-365-resource-limits.md)
- [テナント境界の監視とテスト](office-365-monitoring-and-testing.md)
- [Microsoft 365 での分離とアクセス制御](office-365-isolation-in-office-365.md)
