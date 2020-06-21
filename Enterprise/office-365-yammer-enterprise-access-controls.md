---
title: Microsoft 365 Yammer エンタープライズアクセスコントロール
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
description: '概要: 運用環境での Yammer エンタープライズアクセス制御についての簡単な概要。'
ms.openlocfilehash: 0da479eb36359ec6b795a8e4323441edc4678f1a
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "44775116"
---
# <a name="yammer-enterprise-access-controls"></a>Yammer エンタープライズアクセスコントロール 

Yammer の運用環境への物理的および論理的なアクセスは、少数のユーザー (インフラストラクチャおよび運用) に制限されます。 他の Microsoft 365 エンジニアと同様に、Yammer のエンジニアは顧客データへのアクセスをゼロにします。 承認者の数が限られているロックボックスに似た、承認ベースのジャストインタイムのアクセス制御システムを使用して、アクセスを要求する必要があります。 承認者は、要求を確認します (たとえば、要求が正当であるかどうか、ビジネスケース、時間などに基づいて確認し、要求を承認または拒否するなど)。 要求が承認された場合、JIT アクセスは定義済みの時間に限定されて付与されます。 アクセス時間が超過すると、アクセスは自動的に期限切れになります。

他の Microsoft 365 サービスと同様に、Yammer 運用環境へのすべてのアクセスでは多要素認証が使用されます。 すべてのアクセスおよびコマンド履歴はユーザーに帰属し、Yammer セキュリティチームによって定期的にログおよび確認されます。

Yammer の管理と管理の詳細については、「 [yammer 管理者のヘルプ](https://docs.microsoft.com/yammer/yammer-landing-page)」を参照してください。