---
title: Office 365 PowerShell でライセンスとサービスを確認する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/31/2018
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
ms.openlocfilehash: dab6b8f1828c6be4d32bb2432437d23328653560
ms.sourcegitcommit: 6dd4ac5808d72406578fcc7be6590dd7a99cebea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/31/2018
ms.locfileid: "27466876"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Office 365 PowerShell でライセンスとサービスを確認する

**概要:** Office 365 PowerShell を使ってライセンス プラン、サービス、Office 365 組織で利用可能なライセンスについての情報を確認する方法について説明します。
  
Office 365 サブスクリプションは、すべて以下の要素で構成されます。

- **ライセンス プラン**これらは、Office 365 のプランやライセンスの計画とも呼ばれます。ライセンス プランでは、ユーザーに利用可能な Office 365 サービスを定義します。Office 365 サブスクリプションにはライセンスの複数の計画が含まれます。例のライセンスについては、Office 365 エンタープライズ E3 になります。
    
- **サービス**これらは、サービス プランとも呼ばれます。サービスは、Office 365 の製品、機能、および使用可能な機能で、各ライセンス プランなどの Exchange Online と Office Professional Plus です。ユーザーには、複数のライセンスが割り当てられているさまざまなサービスへのアクセスを許可するさまざまなライセンス プランからことができます。
    
- **ライセンス** すべてのライセンス プランには、購入した数のライセンスが含まれています。ライセンスをユーザーに割り当てると、ライセンス プランで定義した Office 365 サービスが使えるようになります。それぞれのユーザー アカウントに、少なくとも 1 つのライセンス プランからの 1 つのライセンスが必要です。これにより、ユーザーが Office 365 にログオンして、サービスを利用することができます。
    
Office 365 PowerShell を使って、Office 365 組織で利用可能なライセンス プラン、ライセンス、およびサービスに関する詳細を確認することができます。別の Office 365 サブスクリプションで利用可能な製品、機能、サービスについての詳細は、「[Office 365 プランのオプション](https://go.microsoft.com/fwlink/p/?LinkId=691147)」を参照してください。

## <a name="before-you-begin"></a>はじめに

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- PowerShell スクリプトが利用可能なこのトピックで説明する手順を自動化します。具体的には、スクリプトでは、表示し、影響を与えるを含む、Office 365 の組織でサービスを無効にすることができます。詳細については、 [Office 365 の PowerShell で影響を与えるへのアクセスを無効にする](disable-access-to-sway-with-office-365-powershell.md)を参照してください。
    
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

次の表は、Office 365 のサービス プランと、最も一般的なサービスのフレンドリ名を示します。サービス プランの一覧は、異なる場合があります。 
  
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
   
ライセンス プラン (製品の名前とも呼ばれます) が含まれているサービス プラン、および対応するフレンドリ名の一覧については、[製品の名前とライセンスのサービス プランの識別子](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)を参照してください。

特定のライセンス プランで利用可能な Office 365 サービスの詳細を確認するには、次の構文を使用します。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

この例では、litwareinc:ENTERPRISEPACK (Office 365 エンタープライズ E3) ライセンス プランで利用可能な Office 365 サービスを使用します。
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>関連項目

- [ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
- [Office 365 PowerShell を使用してアカウントのライセンスとサービスの詳細を表示する](view-account-license-and-service-details-with-office-365-powershell.md)
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)

