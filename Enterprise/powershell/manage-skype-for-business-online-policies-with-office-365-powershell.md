---
title: PowerShell を使用して Skype for Business Online のポリシーを管理する
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: '概要: PowerShell を使用して、ポリシーを使用して Skype for Business Online のユーザーアカウントのプロパティを管理します。'
ms.openlocfilehash: 4310de23d47025468ea78a597f6379b51deaaa96
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230433"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a><span data-ttu-id="4215e-103">PowerShell を使用して Skype for Business Online のポリシーを管理する</span><span class="sxs-lookup"><span data-stu-id="4215e-103">Manage Skype for Business Online policies with PowerShell</span></span>

<span data-ttu-id="4215e-104">*この記事は、Microsoft 365 Enterprise と Office 365 Enterprise の両方に適用されます。*</span><span class="sxs-lookup"><span data-stu-id="4215e-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="4215e-105">Skype for Business Online のユーザーアカウントの多数のプロパティを管理するには、Microsoft 365 の PowerShell を使用してポリシーのプロパティとして指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4215e-105">To manage many properties of user account for Skype for Business Online, you must specify them as properties of policies with PowerShell for Microsoft 365.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="4215e-106">はじめに</span><span class="sxs-lookup"><span data-stu-id="4215e-106">Before you begin</span></span>

<span data-ttu-id="4215e-107">次の手順にしたがってコマンドを実行するためのセットアップを行います (すでに終わっている場合はこれらの手順は省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="4215e-107">Use these instructions to get set up to run the commands (skip the steps you have already completed):</span></span>
  
1. <span data-ttu-id="4215e-108">[Skype for Business Online Connector モジュール](https://www.microsoft.com/download/details.aspx?id=39366)をダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="4215e-108">Download and install the [Skype for Business Online Connector module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span>
    
2. <span data-ttu-id="4215e-109">Windows PowerShell コマンド プロンプトを開いて次のコマンドを実行します:</span><span class="sxs-lookup"><span data-stu-id="4215e-109">Open a Windows PowerShell command prompt and run the following commands:</span></span> 
    
```powershell
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

<span data-ttu-id="4215e-110">ダイアログ ボックスが表示されたら、Skype for Business Online 管理者のアカウント名とパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="4215e-110">When prompted, enter your Skype for Business Online administrator account name and password.</span></span>
    
## <a name="manage-user-account-policies"></a><span data-ttu-id="4215e-111">ユーザー アカウント ポリシーの管理</span><span class="sxs-lookup"><span data-stu-id="4215e-111">Manage user account policies</span></span>

<span data-ttu-id="4215e-p101">多くの Skype for Business Online ユーザー アカウント プロパティは、ポリシーを使用して設定します。ポリシーは、1 人以上のユーザーに適用可能な設定の集合に過ぎません。ポリシーの構成方法については、FederationAndPICDefault ポリシーに関するサンプル コマンドを実行して確認できます。</span><span class="sxs-lookup"><span data-stu-id="4215e-p101">Many Skype for Business Online user account properties are configured by using policies. Policies are simply collections of settings that can be applied to one or more users. To take a look at how the a policy has been configured, you can run this example command for the FederationAndPICDefault policy:</span></span>
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

<span data-ttu-id="4215e-115">これにより、次のように表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="4215e-115">In turn, you should get back something similar to this:</span></span>
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

<span data-ttu-id="4215e-p102">この例では、このポリシー内の値によって、フェデレーションユーザーとの通信に使用できる、またはできない処理を決定します。たとえば、ユーザーが組織外のユーザーと通信できるようにするには、EnableOutsideAccess プロパティを True に設定する必要があります。このプロパティは、Microsoft 365 管理センターには表示されないことに注意してください。代わりに、その他の選択に基づいて、プロパティは自動的に True または False に設定されます。その他の重要なプロパティは次の2つです。</span><span class="sxs-lookup"><span data-stu-id="4215e-p102">In this example, the values within this policy determine what a use can or cannot do when it comes to communicating with federated users. For example, the EnableOutsideAccess property must be set to True for a user to be able to communicate with people outside the organization. Note that this property does not appear in the Microsoft 365 admin center. Instead, the property is automatically set to True or False based on the other selections that you make. The other two properties of interest are:</span></span>
  
- <span data-ttu-id="4215e-121">**EnableFederationAccess** は、ユーザーがフェデレーション ドメインからのユーザーと通信できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4215e-121">**EnableFederationAccess** indicates whether the user can communicate with people from federated domains.</span></span>
    
- <span data-ttu-id="4215e-122">**EnablePublicCloudAccess** は、ユーザーが Windows Live ユーザーと通信できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4215e-122">**EnablePublicCloudAccess** indicates whether the user can communicate with Windows Live users.</span></span>
    
<span data-ttu-id="4215e-p103">つまり、ユーザー アカウント上のフェデレーション関連プロパティを直接変更したわけではなく (**Set-CsUser -EnableFederationAccess $True** など)、必要なプロパティ値が事前に構成された外部アクセス ポリシーをアカウントに割り当てただけです。ユーザーがフェデレーション ユーザーおよび Windows Live ユーザーと通信できるようにするには、ユーザー アカウントにこれらの種類の通信を可能にするポリシーを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4215e-p103">Therefore, you don't directly change federation-related properties on user accounts (for example, **Set-CsUser -EnableFederationAccess $True**). Instead, you assign an account an external access policy that has the desired property values preconfigured. If we want a user to be able to communicate with federated users and with Windows Live users, that user account must be assigned a policy that allows those types of communication.</span></span>
  
<span data-ttu-id="4215e-126">特定のユーザーが組織外部のユーザーと通信できるかどうかを知りたい場合は、次のようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4215e-126">If you want to know whether or not someone can communicate with users from outside the organization, you have to:</span></span>
  
- <span data-ttu-id="4215e-127">そのユーザーに割り当てられている外部アクセス ポリシーを特定します。</span><span class="sxs-lookup"><span data-stu-id="4215e-127">Determine which external access policy has been assigned to that user.</span></span>
    
- <span data-ttu-id="4215e-128">そのポリシーで許可または禁止されている機能を特定します。</span><span class="sxs-lookup"><span data-stu-id="4215e-128">Determine which capabilities are or are not allowed by that policy.</span></span>
    
<span data-ttu-id="4215e-129">設定するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4215e-129">For example, you can do that by using this command:</span></span>
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

<span data-ttu-id="4215e-130">このコマンドでは、ユーザーに割り当てられたポリシーを探してから、そのポリシー内で有効または無効になっている機能を探します。</span><span class="sxs-lookup"><span data-stu-id="4215e-130">This command finds the policy assigned to the user, then finds the capabilities enabled or disabled within that policy.</span></span>
  
<span data-ttu-id="4215e-131">PowerShell を使用して Skype for Business Online のポリシーを管理するには、次のコマンドレットを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4215e-131">To manage Skype for Business Online policies with PowerShell, see the cmdlets for:</span></span>

- <span data-ttu-id="4215e-132">[クライアント ポリシー](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="4215e-132">[Client policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)</span></span>
- <span data-ttu-id="4215e-133">[会議ポリシー](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="4215e-133">[Conferencing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)</span></span>
- <span data-ttu-id="4215e-134">[モバイルポリシー](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="4215e-134">[Mobile policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)</span></span>
- <span data-ttu-id="4215e-135">[オンラインボイスメールポリシー](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="4215e-135">[Online Voicemail policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)</span></span>
- <span data-ttu-id="4215e-136">[音声ルーティングポリシー](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span><span class="sxs-lookup"><span data-stu-id="4215e-136">[Voice Routing policy](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)</span></span>


> [!NOTE]
> <span data-ttu-id="4215e-p104">Skype for Business Online ダイヤル プランは、名前以外はポリシーそのものです。「ダイヤル プラン」という名前は、Office Communications Server と Exchange との下位互換性を維持するために「ダイヤル ポリシー」の代わりに選択されたものです。</span><span class="sxs-lookup"><span data-stu-id="4215e-p104">A Skype for Business Online dial plan is a policy in every respect except the name. The name "dial plan" was chosen instead of, say, "dialing policy" in order to provide backward compatibility with Office Communications Server and with Exchange.</span></span> 
  
<span data-ttu-id="4215e-139">たとえば、用途に使用可能なすべての音声ポリシーを調べるには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4215e-139">For example, to look at all the voice policies available for your use, run this command:</span></span>
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> <span data-ttu-id="4215e-p105">このコマンドは、使用可能なすべての音声ポリシーのリストを返します。ただし、すべてのポリシーをすべてのユーザーに割り当てられるとは限らない点に注意してください。これは、ライセンスや地理的な位置など、さまざまな制限によります (いわゆる「[使用場所](https://msdn.microsoft.com/library/azure/dn194136.aspx)」のことです)。特定のユーザーに割り当てることが可能な外部アクセス ポリシーと会議ポリシーを知りたい場合は、次のようなコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4215e-p105">That returns a list of all the voice policies available to you. Keep in mind, however, that not all policies can be assigned to all users. This is due to various restrictions involving licensing and geographic location. (The so-called "[usage location](https://msdn.microsoft.com/library/azure/dn194136.aspx).") If you want to know the external access policies and the conferencing policies that can be assigned to a particular user, use commands similar to these:</span></span> 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

<span data-ttu-id="4215e-p106">ApplicableTo パラメーターは、返すデータを、指定されたユーザー (Alex Darrow など) に割り当てることが可能なポリシーに限定します。ライセンスと利用場所の制限によっては、使用可能なすべてのポリシーの一部しか表示しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="4215e-p106">The ApplicableTo parameter limits the returned data to policies that can be assigned to the specified user (for example, Alex Darrow). Depending on licensing and usage location restrictions, that might represent a subset of all the available policies.</span></span> 
  
<span data-ttu-id="4215e-146">場合によっては、ポリシーのプロパティは Microsoft 365 では使用されず、Microsoft サポート担当者のみが管理できるものがあります。</span><span class="sxs-lookup"><span data-stu-id="4215e-146">In some cases, properties of policies are not used with Microsoft 365, while others can only be managed by Microsoft support personnel.</span></span> 
  
<span data-ttu-id="4215e-p107">Skype for Business Online を使用している場合は、何らかのポリシーによってユーザーを管理する必要があります。有効なポリシーに関連するプロパティが空白の場合、当該ユーザーには、ユーザーごとのポリシーが割り当てられていない場合に自動的に適用されるグローバル ポリシーによって管理されていることを意味します。ユーザー アカウントではクライアント ポリシーが表示されていないため、グローバル ポリシーによって管理されています。グローバル クライアント ポリシーを設定するには次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4215e-p107">With Skype for Business Online, users must be managed by a policy of some kind. If a valid policy-related property is blank, that means that the user in question is being managed by a global policy, which is a policy that is automatically applied to a user unless he or she is specifically assigned a per-user policy. Because we don't see a client policy listed for a user account, it is managed by the global policy. You can determine the global client policy with this command:</span></span>
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a><span data-ttu-id="4215e-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="4215e-151">See also</span></span>

[<span data-ttu-id="4215e-152">PowerShell を使用して Skype for Business Online を管理する</span><span class="sxs-lookup"><span data-stu-id="4215e-152">Manage Skype for Business Online with PowerShell</span></span>](manage-skype-for-business-online-with-office-365-powershell.md)
  
[<span data-ttu-id="4215e-153">PowerShell を使用して Microsoft 365 を管理する</span><span class="sxs-lookup"><span data-stu-id="4215e-153">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="4215e-154">Microsoft 365 の PowerShell の概要</span><span class="sxs-lookup"><span data-stu-id="4215e-154">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

