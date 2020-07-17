---
title: ディレクトリ同期のために非ルーティング ドメインの準備を整える
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_SetupDirSyncLocalDir
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: Microsoft 365 と同期する前に、オンプレミスのユーザーに関連付けられた非ルーティングドメインがある場合の対処方法について説明します。
ms.openlocfilehash: 148d7e1abdeeeea11c838697bbc957e2937ea7f8
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736015"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>ディレクトリ同期のために非ルーティング ドメインの準備を整える
オンプレミスのディレクトリを Microsoft 365 と同期する場合は、Azure Active Directory (Azure AD) で確認済みのドメインを用意する必要があります。 オンプレミスのドメインに関連付けられているユーザープリンシパル名 (UPN) のみが同期されます。 ただし、ルーティング可能ではないドメイン (たとえば billa@contoso ローカル) を含む任意の UPN は、onmicrosoft.com ドメイン (billa@contoso.onmicrosoft.com など) に同期されます。 

現在、Active Directory ドメインサービス (AD DS) のユーザーアカウントにローカルドメインを使用している場合は、Microsoft 365 ドメインと適切に同期するために、確認済みのドメイン (billa@contoso.com など) を使用するように変更することをお勧めします。
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>オンプレミス ドメインが .local のみの場合について

AD DS を Azure AD に同期するために使用できる最新のツールは、Azure AD Connect という名前です。 詳細については、「[オンプレミス id と AZURE AD を統合する](https://docs.microsoft.com/azure/architecture/reference-architectures/identity/azure-ad)」を参照してください。
  
Azure AD Connect は、ユーザーの UPN とパスワードを同期して、ユーザーがオンプレミスで使用したものと同じ資格情報でサインインできるようにします。 ただし、Azure AD Connect は、Microsoft 365 によって検証されるドメインに対してのみユーザーを同期します。 これは、Microsoft 365 の id が Azure AD によって管理されているため、ドメインも Azure AD によって検証されることを意味します。 言い換えると、ドメインは有効なインターネットドメインである必要があります (例: .com、.org、.net、. us など)。 内部 AD DS がルーティング可能ではないドメイン (たとえば、...) のみを使用している場合、これは Microsoft 365 の確認済みドメインと一致しない可能性があります。 この問題を解決するには、オンプレミスの AD DS でプライマリドメインを変更するか、1つ以上の UPN サフィックスを追加します。
  
### <a name="change-your-primary-domain"></a>**プライマリ ドメインを変更する**

プライマリドメインを Microsoft 365 で確認したドメインに変更します。たとえば、contoso.com のようにします。 ドメイン contoso. local を持つすべてのユーザーが contoso.com に更新されます。 手順については、「[ドメイン名の変更のしくみ](https://go.microsoft.com/fwlink/p/?LinkId=624174)」を参照してください。 ただし、これは非常に複雑なプロセスであり、次のセクションではより簡単な解決方法について説明します。
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>**UPN サフィックスを追加してユーザーを更新する**

ローカルの問題を解決するには、Microsoft 365 で検証したドメイン (またはドメイン) に一致するように、AD DS に新しい UPN サフィックスまたはサフィックスを登録します。 新しいサフィックスを登録した後、ユーザーの Upn を更新して、を新しいドメイン名に置き換えます。たとえば、ユーザーアカウントが billa@contoso.com のように見えるようにします。
  
認証済みドメインを使用するように Upn を更新すると、オンプレミスの AD DS を Microsoft 365 と同期することができます。
  
 **手順 1: 新しい UPN サフィックスを追加する**
  
1. AD DS ドメインコントローラーのサーバーマネージャーで、[**ツール**] [ \> **Active Directory ドメインと信頼関係**] の順に選択します。
    
    **または (Windows Server 2012 を所有していない場合)**
    
    **Windows キー + R** を押して **[実行]** ダイアログ開き、「Domain.msc」と入力してから **[OK]** を選択します。
    
    ![[Active Directory ドメインと信頼関係] を選択します。](media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. **[Active Directory ドメインと信頼関係]** ウィンドウで、**[Active Directory ドメインと信頼関係]** を右クリックして **[プロパティ]** を選択します。
    
    ![[Active Directory ドメインと信頼関係] を右クリックし、[プロパティ] を選択します。](media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. **[UPN サフィックス]** タブの **[代替の UPN サフィックス]** ボックスに、新しいサフィックスを入力して **[追加]** \> **[適用]** を選択します。
    
    ![新しい UPN サフィックスを追加します](media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    サフィックスの追加が完了したら、**[OK]** を選択します。 
    
 **手順 2: 既存のユーザーの UPN サフィックスを変更する**
  
1. AD DS ドメインコントローラーで、サーバーマネージャーの [**ツール**] [ \> **Active Directory ユーザーとコンピューター**] を選択します。
    
    **または (Windows Server 2012 を所有していない場合)**
    
    **Windows キー + R** を押して **[実行]** ダイアログ開き、「Dsa.msc」と入力してから **[OK]** を選択します。
    
2. ユーザーを選択し、右クリックして **[プロパティ]** を選択します。
    
3. **[アカウント]** タブの UPN サフィックス ドロップダウン リストで、新しい UPN サフィックスを選択してから **[OK]** をクリックします。
    
    ![ユーザーの新しい UPN サフィックスを追加する](media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. すべてのユーザに対して、ここまでの手順を実行します。
    
   
### <a name="you-can-also-use-windows-powershell-to-change-the-upn-suffix-for-all-users"></a>**すべてのユーザーの UPN サフィックスを変更するために Windows PowerShell を使用する**

更新するユーザー数が大量になる場合は、Windows PowerShell を使用すると作業が簡単になります。次の例では、コマンドレット [Get-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624312) と [Set-ADUser](https://go.microsoft.com/fwlink/p/?LinkId=624313) を使用して、すべての contoso.local サフィックスを contoso.com に変更します。 

用の例では、次の Windows PowerShell コマンドを実行して、すべての contoso. ローカルサフィックスを contoso.com に更新することができます。
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

AD DS での Windows PowerShell の使用の詳細については、「 [Active Directory Windows powershell モジュール](https://go.microsoft.com/fwlink/p/?LinkId=624314)」を参照してください。 

