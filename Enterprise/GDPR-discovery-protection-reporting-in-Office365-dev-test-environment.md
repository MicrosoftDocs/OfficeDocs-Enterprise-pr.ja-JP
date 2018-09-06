---
title: Office 365 開発/テスト環境における GDPR の検出、保護、および報告
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: ''
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.custom: ''
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: Office 365 の GDPR 機能をデモします。
ms.openlocfilehash: e58ddc36bf85d791451e2f8097ad65bef4c463e3
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915092"
---
# <a name="gdpr-discovery-protection-and-reporting-in-the-office-365-devtest-environment"></a>Office 365 開発/テスト環境における GDPR の検出、保護、および報告

 **概要:** Office 365 の GDPR 機能をデモします。 
  
この記事では、Office 365 開発/テスト環境で一般データ保護規則 (GDPR) 用に個人を特定できる情報 (PII) の検出、保護、および報告を構成してデモする方法について説明します。
  
## <a name="phase-1-create-and-configure-your-trial-office-365-subscription"></a>フェーズ 1: 試用版の Office 365 サブスクリプションを作成して構成する

まず、「[Office 365 開発/テスト環境のフェーズ 2](office-365-dev-test-environment.md#phase-2-create-an-office-365-trial-subscription)」の記事内の手順を実行します。

次に、以下の手順を使用して、電子情報開示マネージャーを構成します。

1. 全体管理者アカウントを使用して、Office 365 試用版テナントにサインインします。
2. Office 365 のホーム ページで、**[セキュリティとコンプライアンス]** をクリックします。
3. 新しい [セキュリティとコンプライアンス] タブで、**[アクセス許可]** > **[電子情報開示マネージャー]** をクリックします。
4. 電子情報開示マネージャーの **[編集]** をクリックしてから、**[電子情報開示マネージャーの選択]** をクリックします。
5. **[+ 追加]** をクリックして、自分の全体管理者アカウント名を探し、そのアカウントを電子情報開示マネージャーとして追加します。
6. **[完了]** > **[保存]** > **[閉じる]** をクリックします。
  
## <a name="phase-2-add-personally-identifiable-information-to-your-tenant"></a>フェーズ 2: 個人を特定できる情報をテナントに追加する

このフェーズでは、国際銀行口座番号 (IBAN) の事例用として PII を含むドキュメントを作成し、Office 365 開発/テスト環境内の SharePoint Online サイトに保存します。

1. ローカル コンピューターで、Microsoft Word を開きます。
2. Word ファイルに次の表を貼り付け、そのファイルを 'IBANs.docx' としてローカル コンピューターに保存します。
    
    番号  |国  |コード |IBAN  |
    |---------|---------|---------|---------|
    |1     |  オーストリア SEPA      | AT            |AT611904300234573201       |
    |2     |  ブルガリア SEPA       |BG    |BG80BNBG96611020345678      |
    |3     |  デンマーク SEPA      |   DK      |DK5000400440116243      |
    |4     |  フィンランド SEPA      |   FI      |FI2112345600000785         |
    |5     |  フランス SEPA       |   FR      |FR1420041010050500013M02606         |
    |6     |  ドイツ SEPA      |   DE      |DE89370400440532013000         |
    |7     |  ギリシャ SEPA       |   GR      |GR1601101250000000012300695         |
    |8     |  イタリア SEPA       |    IT     |GR1601101250000000012300695         |
    |9     |  オランダ SEPA      |   NL      |    NL91ABNA0417164300     |
    |10     | ポーランド SEPA       |  PL       | PL27114020040000300201355387        |

メモ:- このサンプル データ セットは、公開されている情報から得られたもので、テスト目的でのみ使用することを意図しています。

3. ブラウザーの新しいタブで、「**https://**\<YourTenantName\>**.sharepoint.com**」と入力します。
4. **[ドキュメント]** をクリックして、このサイトのドキュメント ライブラリを開きます。新しいリスト エクスペリエンス ツアーのプロンプトが表示されたら、終了するまで **[次へ]** をクリックします。
5.  **[アップロード]** > **[ファイル]** をクリックして、手順 2 で作成した IBANs.docx を選択します。

  
## <a name="phase-3-demonstrate-data-discovery"></a>フェーズ 3: データ検出をデモする

このフェーズでは、IBAN を含むコンテンツに基づいて、フェーズ 2 で作成して保存したドキュメントを検索するデモを示します。

1. [セキュリティとコンプライアンス] タブで、**[ホーム]** をクリックしてから、**[検索と調査]** > **[コンテンツ検索]** をクリックします。
2. **+** をクリックすることで、新しい検索項目を作成します。
3. 新しいウィンドウで、次の情報を指定します。  
    a. 名前: IBAN 検索  
    b. 何を検索しますか?: **検索する特定のサイトを選択** (**+** をクリック) してから、サイトの URL (**https://**\<YourTenantName\>**.sharepoint.com/**) を入力します。  
    c. **[追加]** をクリックしてから、**[OK]** をクリックします。警告が表示されたら、**[OK]** をクリックします。  
    d. **[新しい検索]** ウィンドウで、**[次へ]** をクリックします。  
    e. **何を検索しますか?**: **SensitiveType:"国際銀行口座番号 (IBAN)"** に対して、**[検索]** をクリックします。

4. **IBAN 検索**の結果に少なくとも 1 つの項目が表示されていることを確認します。


## <a name="phase-4-create-a-custom-sensitive-information-type-via-powershell"></a>フェーズ 4: PowerShell 経由でカスタムの機密情報の種類を作成する

このフェーズでは、Microsoft PowerShell を使用して、架空の Contoso 社のカスタムの機密情報の種類を作成します。Contoso 社では、Contoso 顧客番号 (CCN) を使用して、顧客データベース内の各顧客を識別しています。CCN の構造は次のとおりです。
- レコードが作成された年を表す 2 桁の数字。
    - Contoso 社は 2002 年に設立されました。そのため、最小値は 02 です。 
- レコードを作成したパートナー代理店を表す 3 桁の数字。
    - 使用可能な代理店の値の範囲は 000 ～ 999 です。 
- 基幹業務を表す英字。
    - 使用可能な値は a ～ z で、大文字と小文字を区別する必要があります。
- 4 桁のシリアル番号。 
    - 使用可能なシリアル番号の値の範囲は、0000 ～ 9999 です。   

Contoso では、必ず、内部対応、外部対応、ドキュメント、およびその他の形式で CCN を使用して顧客を参照しています。また、この形式の個人を識別できる情報の使用に対して保護が適用されるように、Office 365 コンテンツ内の CCN の使用を検出するためのカスタムの機密項目の種類が必要です。

1. 「[多要素認証を使用して Office 365 セキュリティ/コンプライアンス センターの PowerShell に接続する](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/mfa-connect-to-scc-powershell?view=exchange-ps)」の手順を使用して、全体管理者アカウントの UPN でセキュリティ/コンプライアンス センターに接続します。
2. 次の PowerShell コマンドを実行します。

     ```
    #Create & start search for sample data
    $searchName = "Sample Customer Information Search"
    $searchQuery = "15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118"
    New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery
    Start-ComplianceSearch -Identity $searchName#Create & start search for sample data
    $searchName = "Sample Customer Information Search"
    $searchQuery = "15080P9562 OR 14040O1119 OR 15020J8317 OR 14050E2330 OR 16050E2166 OR 17040O1118"
    New-ComplianceSearch -Name $searchName -SharePointLocation All -ExchangeLocation All -ContentMatchQuery $searchQuery
    Start-ComplianceSearch -Identity $searchName
    ```
3. 次の PowerShell コマンドを実行して、生成された GUID を表示順にコンピューター上で開いているメモ帳のインスタンスにコピーします。
    ```
    #Generate three unique GUIDs
    Write-Host "GUID1 = "([guid]::NewGuid().Guid)
    Write-Host "GUID2 = "([guid]::NewGuid().Guid)
    Write-Host "GUID3 = "([guid]::NewGuid().Guid)
    ```
4. ローカル コンピューターで、メモ帳の別のインスタンスを開いて、次の内容を貼り付けます。

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <RulePackage xmlns="http://schemas.microsoft.com/office/2011/mce"> 
    <RulePack id="GUID1">
    <Version major="1" minor="0" build="0" revision="0" />
    <Publisher id="GUID2" />
    <Details defaultLangCode="en"> 
    <LocalizedDetails langcode="en"> 
    <PublisherName>Contoso Ltd.</PublisherName> 
    <Name>Contoso Rule Package</Name> 
    <Description>Defines Contoso's custom set of classification rules</Description>
    </LocalizedDetails>
    </Details>
    </RulePack>
    <Rules>
    <!-- Contoso Customer Number (CCN) -->
    <Entity id="GUID3" patternsProximity="300" recommendedConfidence="85">
    <Pattern confidenceLevel="85">
    <IdMatch idRef="Regex_contoso_ccn" />
    <Match idRef="Keyword_contoso_ccn" />
    <Match idRef="Regex_eu_date" />
    </Pattern>
    </Entity>
    <Regex id="Regex_contoso_ccn">[0-1][0-9][0-9]{3}[A-Za-z][0-9]{4}</Regex>
    <Keyword id="Keyword_contoso_ccn">
    <Group matchStyle="word">
    <Term caseSensitive="false">customer number</Term>
    <Term caseSensitive="false">customer no</Term>
    <Term caseSensitive="false">customer #</Term>
    <Term caseSensitive="false">customer#</Term>
    <Term caseSensitive="false">Contoso customer</Term>
    </Group>
    </Keyword>
    <Regex id="Regex_eu_date"> (0?[1-9]|[12][0-9]|3[0-1])[\/-](0?[1-9]|1[0-2]|j\x00e4n(uar)?|jan(uary|uari|uar|eiro|vier|v)?|ene(ro)?|genn(aio)? |feb(ruary|ruari|rero|braio|ruar|br)?|f\x00e9vr(ier)?|fev(ereiro)?|mar(zo|o|ch|s)?|m\x00e4rz|maart|apr(ile|il)?|abr(il)?|avril |may(o)?|magg(io)?|mai|mei|mai(o)?|jun(io|i|e|ho)?|giugno|juin|jul(y|io|i|ho)?|lu(glio)?|juil(let)?|ag(o|osto)?|aug(ustus|ust)?|ao\x00fbt|sep|sept(ember|iembre|embre)?|sett(embre)?|set(embro)?|oct(ober|ubre|obre)?|ott(obre)?|okt(ober)?|out(ubro)? |nov(ember|iembre|embre|embro)?|dec(ember)?|dic(iembre|embre)?|dez(ember|embro)?|d\x00e9c(embre)?)[ \/-](19|20)?[0-9]{2}</Regex>
    <LocalizedStrings>
    <Resource idRef="GUID3">
    <Name default="true" langcode="en-us">Contoso Customer Number (CCN)</Name>
    <Description default="true" langcode="en-us">Contoso Customer Number (CCN) that looks for additional keywords and EU formatted date</Description>
    </Resource>
    </LocalizedStrings>
    </Rules>
    </RulePackage>
    ```
5. 手順 4 の XML テキスト内の GUID1、GUID2、および GUID3 の値を手順 3 の値に置換し、その内容を ContosoCCN.xml という名前でローカル コンピューターに保存します。
6. ContosoCCN.xml ファイルへのパスを入力して、次のコマンドを実行します。
    ```
    #Create new Sensitive Information Type
    $path="<path to the ContosoCCN.xml file, such as C:\Scripts\ContosoCCN.xml>"
    New-DlpSensitiveInformationTypeRulePackage -FileData (Get-Content -Path $path -Encoding Byte -ReadCount 0)
    ```
7. [セキュリティとコンプライアンス] タブで、**[分類]** > **[機密情報の種類]** をクリックします。リストに Contoso 顧客番号 (CCN) が表示されるはずです。

## <a name="phase-5-demonstrate-data-protection"></a>フェーズ 5: データ保護をデモする

Office 365 の個人情報の保護には、データ損失防止 (DLP) 機能の使用が含まれます。Office 365 セキュリティ/コンプライアンス センターで DLP ポリシーを使用することにより、Office 365 全体で機密情報を自動的に保護することができます。

保護を適用するための複数の方法があります。環境内の EU 居住者データの保存場所と従業員によるその処理方法の教育と認識の向上は、Office 365 DLP を使用した情報保護の 1 つのレベルを表しています。

このフェーズでは、新しい DLP ポリシーを作成して、フェーズ 2 で SharePoint Online に保存した IBANs.docx ファイルに適用する方法と IBAN を含む電子メールを送信するタイミングをデモします。

1. ブラウザーの [セキュリティとコンプライアンス] タブで、**[ホーム]** をクリックします。
2. **[データ損失防止]** > **[ポリシー]** をクリックします。
3. **[+ ポリシーの作成]** をクリックします。
4. **[テンプレートで開始またはカスタム ポリシーの作成]** で、**[カスタム]** > **[カスタム ポリシー]** > **[次へ]** をクリックします。
5. **[ポリシーに名前を付ける]** で、次の詳細を入力してから、**[次へ]** をクリックします。a. 名前: **EU 市民 PII ポリシー** b. 説明: **欧州市民の個人を特定できる情報を保護する**
6. **[場所の選択]** で、**[Office 365 のすべての場所]** を選択します。これに、Exchange 電子メール、OneDrive ドキュメント、および SharePoint ドキュメントの内容が追加されます。その後で、**[次へ]** をクリックします。
7. **[保護するコンテンツの種類のカスタマイズ]** で、**[含まれているコンテンツを検索する:]** をクリックしてから、**[編集]** をクリックします。
8. **[保護するコンテンツの種類の選択]** で、**[追加]** > **[機密情報の種類]** をクリックします。
9. **[機密情報の種類]** で、**[+ 追加]** をクリックします。
10. **[機密情報の種類]** で、**IBAN** を検索して、**[国際銀行口座番号 (IBAN)]** チェック ボックスをオンにしてから、**[追加]** をクリックします。
11. **国際銀行口座番号 (IBAN)** 機密情報の種類が追加されたことを確認してから、**[完了]** をクリックします。
12. **[含まれるコンテンツ]** で、機密情報の種類が追加されたことを確認してから、**[保存]** をクリックします。
13. **[保護するコンテンツの種類のカスタマイズ]** で、**[含まれているコンテンツを検索する:]** に **国際銀行口座番号 (IBAN)** が含まれていることを確認してから、**[次へ]** をクリックします。
14. **[共有されているコンテンツが含まれる時期の検出:（Detect when content that's being shared contains:）]** で、値を **10** から **1** に変更してから、**[次へ]** をクリックします。
15. **[ポリシーを有効にしますか、または最初にテストしますか?]** で、次の設定を選択してから、**[次へ]** をクリックします。  
    a. **[最初にテストする]** のオプションを選択する  
    b. **[テスト モードでポリシー ヒントを表示する]** チェック ボックスをオンにする 
16. **[設定の確認]** で、設定の確認後に **[作成]** をクリックします。メモ: 新しい DLP ポリシーを作成したら、それが有効になるまでしばらく時間がかかります。
17. ローカル コンピューター上で、ブラウザーのプライベート インスタンスを開きます。
18. アドレス バーに、「**https://**\<YourTenantName\>**.sharepoint.com**」と入力して、全体管理者アカウントを使用してサインインします。
19. **[ドキュメント]** をクリックします。
20. 'IBANs.docx' という名前のファイルをクリックします。'IBANs.docx のポリシー ヒント' が表示されるはずです。IBANs.docx ファイルは、DLP ポリシーに違反している外部の受信者と共有されています。 
21. アドレス バーに、「**https://outlook.office365.com**」と入力します。
22. **[新規]** - **[電子メール メッセージ]** をクリックして、次の項目を入力します。  
    - **宛先:** \<個人用電子メール アドレス\>  
    - **件名:** GDPR テスト  
    - **本文:** 下に示す値の表にコピーしてください。
  
        |番号  |国  |コード |IBAN  |
        |---------|---------|---------|---------|
        |1     |  オーストリア SEPA      | AT            |AT611904300234573201       |
        |2     |  ブルガリア SEPA       |BG    |BG80BNBG96611020345678      |
        |3     |  デンマーク SEPA      |   DK      |DK5000400440116243      |
        |4     |  フィンランド SEPA      |   FI      |FI2112345600000785         |
        |5     |  フランス SEPA       |   FR      |FR1420041010050500013M02606         |
        |6     |  ドイツ SEPA      |   DE      |DE89370400440532013000         |
        |7     |  ギリシャ SEPA       |   GR      |GR1601101250000000012300695         |
        |8     |  イタリア SEPA       |    IT     |GR1601101250000000012300695         |
        |9     |  オランダ SEPA      |   NL      |   NL91ABNA0417164300      |
        |10     | ポーランド SEPA       |  PL       | PL27114020040000300201355387        |

メモ:- このサンプル データ セットは、公開されている情報から得られたもので、テスト目的でのみ使用することを意図しています。

23. 電子メールの本文に IBAN が含まれ、メッセージ ウィンドウの上部にポリシー ヒントが表示されることが DLP ポリシーで認識されたことが表示されます。
24. ブラウザーのプライベート インスタンスを閉じます。


## <a name="phase-6-demonstrate-reporting"></a>フェーズ 6: レポート機能をデモする
 
このフェーズでは、フェーズ 5 で構成した DLP ポリシーに基づいて Office 365 のレポート機能をデモします。

   1. ブラウザーの [セキュリティとコンプライアンス] タブで、**[ホーム]** をクリックします。
   2. **[レポート]** > **[ダッシュボード]** > **[DLP ポリシー一致]** をクリックします。
   3. DLP ポリシーは、組織の機密情報の特定と保護に役立ちます。たとえば、レポートには、SharePoint Online に保存された IBAN を含むドキュメントがポリシーで特定されたことが表示されます。
  
## <a name="see-also"></a>関連項目

[GDPR のための Office 365 の情報保護](office-365-information-protection-for-gdpr.md)

[Microsoft 365 に関する GDPR](https://docs.microsoft.com/microsoft-365/compliance/gdpr?toc=/microsoft-365/enterprise/toc.json)
