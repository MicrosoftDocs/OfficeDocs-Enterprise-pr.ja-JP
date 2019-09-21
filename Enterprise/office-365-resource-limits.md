---
title: Office 365 リソースの制限
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
description: '概要: Office 365 内のさまざまなアプリケーションのリソース制限についての情報。'
ms.openlocfilehash: ece25deece5a0f2eec7ab0295a2af68f47e1c50c
ms.sourcegitcommit: 55a046bdf49bf7c62ab74da73be1fd1cf6f0ad86
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "37067607"
---
# <a name="resource-limits"></a>リソースの制限

リソースの制限は、クォータ (制限) と調整を使用して適用されます。 Azure Active Directory と個別の Office 365 サービスは両方を使用します。 新しい機能が追加されると、制限はサービスに依存し、時間の経過と共に変化します。 さまざまなサービスの現在の制限の詳細については、以下のトピックを参照してください。
- [Azure Active Directory サービスの制限と制限事項](https://msdn.microsoft.com/en-us/library/azure/dn764971.aspx)
- [Exchange Online の制限](https://technet.microsoft.com/en-us/library/exchange-online-limits.aspx)
- [Exchange Online Protection の制限](https://technet.microsoft.com/en-us/library/exchange-online-protection-limits.aspx)
- [SharePoint Online ソフトウェアの境界と制限](https://support.office.com/article/SharePoint-Online-software-boundaries-and-limits-8F34FF47-B749-408B-ABC0-B605E1F6D498)
- [Skype for Business の制限](https://technet.microsoft.com/en-us/library/skype-for-business-online-limits.aspx)
- [Yammer REST API とレート制限](https://developer.yammer.com/docs/rest-api-rate-limits)
- [Sway でのファイルサイズの制限](https://support.office.com/article/File-size-limits-in-Sway-4db21bc6-b42b-499f-9272-66e089db109f)

これらの制限に加えて、Azure Active Directory と Office 365 の間では、いくつかの調整メカニズムが使用されています。 Microsoft のデータセンター内のネットワークリソースが、サービスを使用する幅広い顧客向けに最適化されているため、サービス内の調整は特に重要です。 調整メカニズムは次のとおりです。
- Azure Active Directory と Office 365 のユーザーレベルの調整。単一のユーザーが実行できるトランザクションまたは同時呼び出し (スクリプトまたはコード) の数を制限します。
- テナントの作成時に、各テナントに既定の PowerShell 調整ポリシーが割り当てられます。 これらの設定は、1人の管理者が開くことのできる同時 PowerShell セッションの最大数など、他のアイテムに影響を与えます。
- 各 Exchange Online の顧客には、EWS クライアントの操作用に調整された既定の Exchange Web サービス (EWS) ポリシーと、すべての Outlook クライアントに適用される調整があります。
