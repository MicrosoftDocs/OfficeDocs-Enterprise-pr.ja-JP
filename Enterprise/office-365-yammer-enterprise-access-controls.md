---
title: Office 365 Yammer エンタープライズアクセスコントロール
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
description: '概要: 運用環境での Yammer エンタープライズアクセス制御についての簡単な概要。'
ms.openlocfilehash: 9b88ff0f8c480dd3726246e47714d9468509ef08
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841794"
---
# <a name="yammer-enterprise-access-controls"></a>Yammer Enterprise でのアクセス制御 

Yammer の運用環境への物理的および論理的なアクセスは、少数のユーザー (インフラストラクチャおよび運用) に制限されます。 他の Office 365 エンジニアと同様に、Yammer のエンジニアは顧客データへのアクセスをゼロにします。 承認者の数が限られているロックボックスに似た、承認ベースのジャストインタイムのアクセス制御システムを使用して、アクセスを要求する必要があります。 承認者は、要求を確認します (たとえば、要求が正当であるかどうか、ビジネスケース、時間などに基づいて確認し、要求を承認または拒否するなど)。 要求が承認された場合、JIT アクセスは定義済みの時間に限定されて付与されます。 アクセス時間が超過すると、アクセスは自動的に期限切れになります。

他の Office 365 サービスと同様に、Yammer 運用環境へのすべてのアクセスでは多要素認証が使用されます。 すべてのアクセスおよびコマンド履歴はユーザーに帰属し、Yammer セキュリティチームによって定期的にログおよび確認されます。

Yammer の管理と管理の詳細については、「 [yammer 管理者のヘルプ](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US)」を参照してください。