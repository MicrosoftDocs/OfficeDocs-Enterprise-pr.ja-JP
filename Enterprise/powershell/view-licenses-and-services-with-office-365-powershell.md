---
title: Office 365 PowerShell でライセンスとサービスを確認する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/20/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Office 365 PowerShell を使ってライセンス プラン、サービス、Office 365 組織で利用可能なライセンスについての情報を確認する方法について説明します。
ms.openlocfilehash: 4ee4a5d0173f97520075f146e50bd234e767cc95
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319258"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Office 365 PowerShell でライセンスとサービスを確認する

**概要:** Office 365 PowerShell を使ってライセンス プラン、サービス、Office 365 組織で利用可能なライセンスについての情報を確認する方法について説明します。
  
Office 365 サブスクリプションは、すべて以下の要素で構成されます。

- **ライセンス プラン**ライセンス プランまたは Office 365 プランとも呼ばれます。ライセンス プランでは、ユーザーが利用可能な Office 365 サービスを定義します。Office 365 サブスクリプションには、複数のライセンス プランが含まれる場合があります。たとえば、Office 365 Enterprise E3 というライセンス プランがあります。
    
- **サービス**サービス プランとも呼ばれます。サービスとは、各ライセンス プランで利用可能な Office 365 製品および機能のことで、たとえば、Exchange Online や Office Professional Plus があります。ユーザーは、さまざまなサービスへのアクセスを許可するさまざまなライセンス プランから割り当てられた複数のライセンスを持つことができます。
    
- **ライセンス** すべてのライセンス プランには、購入した数のライセンスが含まれています。ライセンスをユーザーに割り当てると、ライセンス プランで定義した Office 365 サービスが使えるようになります。それぞれのユーザー アカウントに、少なくとも 1 つのライセンス プランからの 1 つのライセンスが必要です。これにより、ユーザーが Office 365 にログオンして、サービスを利用することができます。
    
Office 365 PowerShell を使って、Office 365 組織で利用可能なライセンス プラン、ライセンス、およびサービスに関する詳細を確認することができます。別の Office 365 サブスクリプションで利用可能な製品、機能、サービスについての詳細は、「[Office 365 プランのオプション](https://go.microsoft.com/fwlink/p/?LinkId=691147)」を参照してください。

## <a name="before-you-begin"></a>はじめに

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- このトピックで説明されている手順を自動化する PowerShell スクリプトが利用可能です。具体的に言うと、このスクリプトにより、Office 365 組織のサービス (Sway を含む) を表示し、無効化できます。詳細については、「[Office 365 PowerShell を使った Sway へのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)」をご覧ください。
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a>ライセンス プランと利用可能なライセンスに関する情報を確認する

現在のライセンス プランおよび各プランで利用可能なライセンスについての概要を確認するには、Office 365 PowerShell で以下のコマンドを実行します。
  
```
Get-MsolAccountSku
```

結果には次の情報が含まれます。
  
- **AccountSkuId:** 構文 `<CompanyName>:<LicensingPlan>` を使用して、組織で利用可能なライセンス プランを表示します。_<CompanyName>_ は Office 365 に登録するときに指定した値で、組織に対して一意です。_<LicensingPlan>_ の値は、すべてのユーザーに対して同じです。たとえば、値 `litwareinc:ENTERPRISEPACK` では、会社名が `litwareinc`、ライセンス プラン名が `ENTERPRISEPACK` で、これが Office 365 Enterprise E3 のシステム名になります。
    
- **ActiveUnits** 特定のライセンス プランで購入したライセンスの数。
    
- **WarningUnits:** 更新していないライセンス プランのライセンスの数。30 日の猶予期間を過ぎると有効期限切れになります。
    
- **ConsumedUnits:** 特定のライセンス プランでユーザーに割り当てたライセンスの数。
    
すべてのライセンス プランで利用できる Office 365 サービスの詳細を参照するには、次のコマンドを実行します。
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

次の表は、Office 365 のサービス プランと、最も一般的なサービスのフレンドリ名を示します。サービス プランの一覧は、異なる場合があります。名とサービス プランの一覧は、[ビジネス ユーザー向けのサポート ・ オプション](https://support.microsoft.com/gp/support-options-for-business)にお問い合わせください。
  
|**サービス プラン**|**説明**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype for Business Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online プラン 2  <br/> |
   
特定のライセンス プランで利用可能な Office 365 サービスの詳細を確認するには、次の構文を使用します。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

この例は、litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3) サービス プランで使用可能な Office 365 サービスを示しています。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>関連項目

- [ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する](view-account-license-and-service-details-with-office-365-powershell.md)
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)

