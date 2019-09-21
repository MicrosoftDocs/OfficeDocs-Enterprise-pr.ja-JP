---
title: Office 365 でのテナントの分離
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
description: Microsoft が Office 365 のテナント分離を強制する方法の概要。
ms.openlocfilehash: 4859fd5feec50159e71ca2ca8968388c5ab82d64
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067608"
---
# <a name="tenant-isolation-in-office-365"></a>Office 365 でのテナントの分離

クラウドコンピューティングの主な利点の1つは、同時に多数のお客様に共通する共有インフラストラクチャの概念で、スケールの経済につながることです。 この概念を*マルチテナント*と呼びます。 Microsoft は、クラウドサービスのマルチテナントアーキテクチャがエンタープライズレベルのセキュリティ、機密性、プライバシー、整合性、および可用性の標準をサポートするように継続的に取り組みます。

[信頼できるコンピューティング](https://www.microsoft.com/en-us/twc/default.aspx)および[セキュリティ開発ライフサイクル](http://www.microsoft.com/security/sdl/default.aspx)から得られる重要な投資と実績に基づいて、Microsoft cloud services はすべてのテナントがすべてに悪影響を与える可能性があるという前提で設計されていました。その他のテナント。また、1つのテナントのアクションが別のテナントのセキュリティまたはサービスに影響を与えたり、別のテナントのコンテンツにアクセスしたりしないようにセキュリティ対策を実装しています。

マルチテナント環境でテナントの分離を維持するための主な目標は次の2つです。
1.  テナント間での顧客コンテンツの漏洩、または不正アクセスを防止する。そして
2.  あるテナントのアクションが別のテナントのサービスに悪影響を及ぼすことを防ぐ

Office 365 には複数の形式の保護が実装されており、お客様が Office 365 のサービスまたはアプリケーションを侵害したり、他のテナントまたは Office 365 システム自体の情報に無許可でアクセスしたりすることを防ぐことができます。
- Office 365 サービス用の各テナント内の顧客コンテンツの論理的分離は、Azure Active Directory の承認と役割ベースのアクセス制御によって実現されます。
- SharePoint Online は、データ分離メカニズムをストレージレベルで提供します。
- Microsoft は、厳密な物理的なセキュリティ、背景審査、および複数層の暗号化戦略を使用して、顧客のコンテンツの機密性と整合性を保護しています。 すべての Office 365 データセンターには、バイオメトリクスアクセスコントロールがあり、ほとんどの場合、物理的なアクセスを得るために palm 印刷が要求されています。 また、米国のすべての Microsoft の従業員は、雇用プロセスの一環として、標準のバックグラウンドチェックを正常に完了する必要があります。 Office 365 の管理アクセスに使用されるコントロールの詳細については、「 [office 365 管理アクセス制御](office-365-administrative-access-controls-overview.md)」を参照してください。
- Office 365 は、BitLocker、ファイル暗号化、トランスポート層セキュリティ (TLS)、インターネットプロトコルセキュリティ (IPsec) など、お客様のコンテンツを保存し、送信中で暗号化するサービス側のテクノロジを使用しています。 Office 365 での暗号化の詳細については、「 [office 365 のデータ暗号化テクノロジ](/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview.md)」を参照してください。

これらの保護によって、物理的な分離だけで提供される脅威の保護と軽減対策を提供する、堅牢な論理的分離コントロールが提供されます。

## <a name="related-links"></a>関連リンク
- [Azure Active Directory での分離とアクセス制御](office-365-isolation-in-azure-active-directory.md)
- [Office Graph と Delve でのテナントの分離](office-365-isolation-in-graph-and-delve.md)
- [Office 365 の検索でのテナントの分離](office-365-isolation-in-office-365-search.md)
- [Office 365 でのテナントの分離のビデオ](office-365-isolation-in-office-365-video.md)
- [リソースの制限](office-365-resource-limits.md)
- [テナント境界の監視とテスト](office-365-monitoring-and-testing.md)
- [Office 365 での分離とアクセス制御](office-365-isolation-in-office-365.md)