---
title: "Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- DecEntMigration
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "ライセンスのないユーザーに Office 365 のライセンスの Office 365 の PowerShell の割り当てを使用する方法について説明します。"
ms.openlocfilehash: 7120b5d61b98f401f9ec1830598f20fbcbecdb66
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2017
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Office 365 PowerShell を使用してライセンスをユーザー アカウントに割り当てる

**の概要:** ライセンスのないユーザーに Office 365 のライセンスの Office 365 の PowerShell の割り当てを使用する方法について説明します。
  
Office 365 のユーザー アカウントのライセンスは重要なユーザーは自分のアカウントのライセンスを取得するまで、Office 365 サービスを使用できません。効率的にライセンスをライセンスのないアカウント、特に複数のアカウントに割り当てるには、Office 365 の PowerShell を使用できます。 

## <a name="before-you-begin"></a>開始する前に
<a name="RTT"> </a>

- このトピックの手順では、Office 365 PowerShell に接続する必要があります。手順については、「[Office 365 PowerShell への接続](connect-to-office-365-powershell.md)」を参照してください。
    
- それぞれの計画、組織内で使用可能なライセンス プランと利用可能なライセンスの数を表示するのには、 **Get MsolAccountSku**コマンドレットを使用します。各プランで利用可能なライセンスの数は、 **ActiveUnits** - **WarningUnits** - **ConsumedUnits**。計画、ライセンス、およびサービスのライセンスの詳細については、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)を参照してください。
    
- 組織内のライセンスのないアカウントを検索するには、コマンド  `Get-MsolUser -All -UnlicensedUsersOnly` を実行します。
    
- **UsageLocation**プロパティが有効な ISO 3166-1 アルファ 2 国コードに設定されているユーザー アカウントに対してのみライセンスを割り当てることができます。たとえば、アメリカ合衆国およびフランスの FR のことです。いくつかの Office 365 サービスは、特定の国では使用できません。詳細については、[ライセンスによる使用制限の詳細](https://go.microsoft.com/fwlink/p/?LinkId=691730)を参照してください。
    
    **UsageLocation** 値のないアカウントを検索するには、コマンド `Get-MsolUser -All | where {$_.UsageLocation -eq $null}` を実行します。アカウントに **UsageLocation** 値を設定するには、構文 `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>` を使用します。例: `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`。
    
- 使用せず、 **Get MsolUser**コマンドレットを使用するかどうか、`-All`パラメーターでは、最初の 500 個のアカウントのみが返されます。
    
## <a name="the-short-version-instructions-without-explanations"></a>簡略版 (説明なしの手順)
<a name="ShortVersion"> </a>

ここでは、詳細な説明のない手順を示します。ご質問があるか、詳細情報を表示した場合は、トピックの残りの部分を読み取ることができます。
  
ユーザーにライセンスを割り当てるには、Office 365 PowerShell で次の構文を使用します。
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

この例では、ライセンスの`litwareinc:ENTERPRISEPACK`(Office 365 エンタープライズ E3) のライセンスについて、ライセンスのないユーザーに`belindan@litwareinc.com`。
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

ライセンスのない多数のユーザーにライセンスを割り当てるには、次の構文を使用します。
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **注**
  
- 複数のライセンスを同じライセンス プランのユーザーに割り当てることはできません。
    
- 十分な数の利用可能なライセンスをお持ちでない場合は、使用可能なライセンスがなくなるまで、ライセンスは **Get-MsolUser** コマンドレットによって返される順序でユーザーに割り当てられます。
    
次の使用例からのライセンスの割り当て、 `litwareinc:ENTERPRISEPACK` (Office 365 エンタープライズ E3) のライセンスについてすべてのライセンスのないユーザーにします。
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

この例では、これらの同じライセンスを米国内にある営業部のライセンスのないユーザーに割り当てます。
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>詳細版 (詳細な説明付きの手順)
<a name="LongVersion"> </a>

「[ライセンスのあるユーザーとライセンスのないユーザーを Office 365 PowerShell で表示する](view-licensed-and-unlicensed-users-with-office-365-powershell.md)」で説明しているように、有効な Office 365 ユーザー アカウントを所有していても、Office 365 のライセンスが発行されていないユーザーが存在する可能性があります。ライセンスのないユーザーは、有効なアカウントがあるかどうかにかかわらず、Office 365 にログオンできません。そしてログオンできなければ、Office 365 のサービスを利用できません。
  
前述の記事では、次のコマンドを実行すると、ライセンスのないユーザー アカウントの一覧を取得できると説明しています。
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

このコマンドは、Office 365 のライセンスを現在所有していないユーザーに関する情報を返します。
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

ご覧のように、ライセンスのないユーザーが 1 人表示されています。それは Belinda Newman です。Belinda に Office 365 のライセンスを割り当てるには、どのような方法がありますか?
  
まず、[ライセンスを表示し Office 365 の PowerShell を使用してサービス](view-licenses-and-services-with-office-365-powershell.md)の記事で説明されている**Get MsolAccountSku**コマンドレットを実行していきます。
  
```
Get-MsolAccountSku
```

このコマンドを実行すると、以下のようなデータが返されます。
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

なぜ **Get-MsolAccountSku** を実行するのでしょうか? (念のために付け加えますが、"Sku" は "Stock Keeping Unit" (最小在庫管理単位) の略です。ここでは、"製品" に対応する業界用語だと思っていただければ十分です。) **Get-MsolAccountSku** を実行する理由は 2 つあります。まず、Belinda に割り当てるライセンスが実際にあるかどうかを確認する必要があります。Belinda に割り当てられるライセンスはありますか?これを確認するには、 **ActiveUnits** プロパティ値 (25) から、 **WarningUnits** プロパティ値 (0) と **ConsumedUnits** プロパティ値 (24) を差し引きます。
  
 `25 - 0 - 24 = 1`
  
**ActiveUnits** プロパティは購入したライセンスの数を示し、 **WarningUnits** と **ConsumedUnits** の合計値は現在使用されているライセンスの数を示します。購入したライセンス数から配布済みのライセンス数を引くと、現在の利用可能なライセンス数が得られます。幸いにも、配布できるライセンスが 1 つあります。
  
 `25 - 0 - 24 = 1`
  
次に、Belinda に新しいライセンスを割り当てるには、ライセンス プランの名前を知る必要があります (つまり、 **AccountSkuId** を知る必要があります)。これは簡単です。ライセンス プランは 1 つしかありません ( `litwareinc:ENTERPRISEPACK`)。ただし、組織が複数のライセンス プランを持っている場合もあります。この場合、 **Get-MsolAccountSku** は 2 つの異なる **AccountSkuIds** を返し、ライセンスを割り当てるときは適切なライセンス プランを選択する必要があります。ただしここでは、最も単純なケースにこだわり、1 つのライセンス プランだけを所有しているものとします。
  
では、Belinda Newman に新しいライセンスを割り当てるには、どうすればよいでしょうか?以下のようにします。
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

さらに、 **Set-MsolUserLicense** コマンドレットを呼び出して、ユーザーの _UserPrincipalName_ パラメーターと適切なライセンス プランを指定していることを確認する必要があります。
  
**Set-MsolUserLicense** の実行が完了すると、次のような画面が表示されます。
  
 `PS C:\\windows\\system32>`
  
別の言い方をすれば、何も実行されなかったかのように見えます。ユーザーにライセンスが割り当てられていることを確認するには、次のようなコマンドを実行します。
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

すべてが想定どおりに動作した場合、Belinda の isLicensed プロパティが True に設定されていることを確認できるはずです。
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [!SECURITY NOTE] おそらく次のような疑問を抱かれるでしょう。すでにライセンスを所有しているユーザーに間違ってライセンスを割り当てようとしたらどうなりますか?1 人のユーザーに 2 つのライセンスを割り当てることになりますか? > この疑問の簡潔な答えは、「いいえ」です。Office 365 は同じユーザーに 2 つ以上のライセンスを割り当てることはありません。(同じライセンス プランから複数のライセンスを割り当てることはあります。)そうしようとすると、次のエラー メッセージが表示されてコマンドは失敗します。 >  `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.`> このエラー メッセージは、少し誤解を与える可能性があります。実際はライセンスが無効なのではなく、ライセンスをすでに *所有している*  ユーザーに割り当てようとしているだけです。エラー メッセージはともかくとして、重要な点は、1 人のユーザーに複数のライセンスが割り当てられることはないという点です。
  
今確認したように、Office 365 PowerShell を使用して 1 つのライセンスを 1 人のユーザーに割り当てることはとても簡単です。しかし、次のような疑問を抱かれるでしょう。Office 365 管理センター を使用すれば、1 つのライセンスを 1 人のユーザーに割り当てる作業が同じように、あるいはもっと簡単でしょうか? そうかもしれません。それは Windows PowerShell を使い慣れているか、Office 365 管理センター を使い慣れているかによっても異なります。ただし、Windows PowerShell が本当に役に立つのは、複数のライセンスを複数のユーザーに割り当てる必要がある場合です。たとえば、次のコマンドは、まだライセンスを所有していないユーザーに、Office 365 のライセンスを割り当てます。
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

前のコマンドでは、 **Get-MsolUser** パラメーターと _UnlicensedUsersOnly_ パラメーターを使用して、ライセンスのないすべてのユーザー アカウントのコレクションを返します。それから、このコレクションを **Set-MsolUserLicense** コマンドレットに渡します。次に、 **Set-MsolUserLicense** が ( `litwareinc:ENTERPRISEPACK` ライセンス プランから取り出した) ライセンスをコレクションの各ユーザーに割り当てます。
  
しかし、ライセンスのないユーザーが 5 人いるのに、利用できるライセンスが 1 つしかない場合はどうすればよいでしょうか? この場合、 **Set-MsolUserLicense** は利用可能なライセンスを **Get-MsolUser** によって返された最初のユーザーに付与します。 **Set-MsolUserLicense** は他の 4 人のユーザーにもライセンスを割り当てようとしますが、その 4 人分の試行はすべて失敗し、次のエラー メッセージが表示されます。
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
言い換えると、Set-MsolUserLicense はただ失敗するだけではなく、できるだけ多くのライセンスを割り当てようとします。そのあとで、コマンドは失敗します。
  
別の例を試してみましょう。セールス部門のユーザー全員にライセンスを割り当てようとすることもあるでしょう。その場合は、次のようにします。
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

あるいは、エラー メッセージとコンピューティング プロセスを最小限に抑えたい場合は、次のようにしてライセンスをセールス部門のうちライセンスのないユーザーに割り当てます。
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

つまり、ライセンスをすでに所有しているユーザーにライセンスを付与しようとしても意味がありません。前述のように、その操作はうまくいきません。
  
別の例を考えましょう。現在 Office 365 のライセンスを所有していない米国のすべてのユーザーにライセンスを付与するとします。その場合は、次のようにします。
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

このようにやっていきます。
  
> [!NOTE]
> では、ライセンスのないのユーザーすべてにライセンスを発行するコマンドを実行するには、どのくらい時間がかかるでしょうか? これは答えるのが難しい質問です。これは、ユーザーの数からネットワーク接続の速度に至るまで、あらゆる要素に依存します。ライセンスを付与するユーザーが数百人なら、かなり短時間で終わります (1 - 2 分以下)。ライセンスを付与するユーザーが 10,000 人の場合は、明らかにもう少し時間がかかります。ただし、Office 365 管理センター を使用して 10,000 人のユーザーにライセンスを割り当てる場合ほど長くはありません。 
  
この件に関する限り、ライセンスの割り当てでは次の点に注意する必要があります。ユーザーの **UsageLocation** プロパティの値が設定されていない場合、Office 365 のライセンスをそのユーザーに割り当てることはできません。代わりに、次のようなエラー メッセージが表示されます。
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
このエラー メッセージは、やや間接的ですが、対象のユーザーに **UsageLocation** が割り当てられていないことを示しています。ご想像のとおり、(ユーザーが通常 Office 365 を使用する地域や国を示す) **UsageLocation** プロパティは、非常に重要です。その理由は、ユーザーが利用できるサービスは、購入したライセンス パックだけでなく、ユーザーの居住地によっても異なるからです。地域の法律や規制により、一部のサービスを利用できないユーザーもいます。ユーザーの **UsageLocation** がない場合、Office 365 はそのユーザーに対してどのサービスを合法的に公開できるのかがわかりません。このため、Office 365 はそのユーザーに対して、少なくとも **UsageLocation** が指定されるまではサービスをまったく提供できません。
  
> [!NOTE]
> ユーザー アカウントを構成するときことがわかりますすぐに世界中の指定したパーツに関連付けられているライセンスによる使用制限があるかどうか。イランにライセンスを受けたユーザーの**UsageLocation**を変更した場合の例 ( `IR`)、コマンドは、このエラー メッセージで失敗します: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.`> Office 365 がイランのユーザーには現在利用できないためにです。詳細については、[ライセンスによる使用制限の詳細](https://go.microsoft.com/fwlink/p/?LinkId=691730)を参照してください。ちなみに、Office 365 は、標準化機構 (ISO) の国際組織によって生成される 2 文字の国コードを使用します。[ISO の web サイト](https://go.microsoft.com/fwlink/p/?LinkId=84073)でこれらのコードが表示されます。 
  
特定のユーザーに **UsageLocation** が指定されているかどうかを確認するには、次のようなコマンドを利用できます。
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

または、次のコマンドを使用して、 **UsageLocation** のないすべてのユーザーの一覧を取得することもできます。
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> 割り当てると、ライセンスをユーザーにそのユーザーを既定では、アクセスが与えられます、組織へのアクセスにはすべての Office 365 サービスにします。などの Office 365 エンタープライズ E3 のライセンスを購入した場合、新たにライセンスを受けたユーザーは自動的に付与されます Exchange Online、Skype のようなサービスへのアクセスをビジネス オンライン、および SharePoint Online の。かどうかこれらのサービスへのユーザーのアクセスを制限する場合は (たとえば、*されません*が、SharePoint Online にアクセスするユーザーをする可能性がありますを Exchange のオンライン ビジネスのオンラインの Skype) を参照し、[と Office 365 サービスへのアクセスを無効にします。PowerShell](disable-access-to-services-with-office-365-powershell.md)。 
  
## <a name="new-to-office-365"></a>Office 365 を初めて使用する場合

||
|:-----|
|![LinkedIn Learning の小さいアイコン](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **Office 365 を初めて使用する場合は、**         LinkedIn Learning が提供する [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5) のための無料のビデオ コースをご覧ください。 |
   
## <a name="see-also"></a>See Also
<a name="SeeAlso"> </a>

Office 365 PowerShell でのユーザー管理に関する次の追加のトピックをご覧ください。
  
- [Office 365 PowerShell を使用してユーザー アカウントを作成する](create-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用したユーザー アカウントの削除と復元](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell でユーザー アカウントをブロックする](block-user-accounts-with-office-365-powershell.md)
    
- [Office 365 PowerShell を使用してユーザー アカウントからライセンスを削除する](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
これらの手順で使用するコマンドレットの詳細については、次のトピックをご覧ください。
  
- [Get MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [セット MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach オブジェクト](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

