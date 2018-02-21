---
title: "Office 365 の開発/テスト環境での機密性の高いファイルの保護"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: "概要: は、構成し、不適切な SharePoint Online サイト コレクションに投稿される場合でもに Office 365 の情報権利の管理が、機密性の高いファイルを保護する方法をデモンストレーションします。"
ms.openlocfilehash: 236272a90bb6ff7f310c95f1494b68750e363f40
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2018
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Office 365 の開発/テスト環境での機密性の高いファイルの保護

 **の概要:**構成し、不適切な SharePoint Online サイト コレクションに投稿される場合でもに Office 365 の情報権利の管理が、機密性の高いファイルを保護する方法をデモンストレーションします。
  
Office 365 の Information Rights Management (IRM) は、SharePoint Online ライブラリとリストからダウンロードしたドキュメントを保護する機能のセットです。ダウンロードしたファイルは暗号化されており、格納されていた SharePoint Online ライブラリを反映するアクセス許可 (オープン、コピー、保存、印刷) を含んでいます。
  
この記事の手順に従い、Office 365 試用版のサブスクリプションを使用して、機密性の高い情報を含む可能性のあるファイルに対して Office 365 で IRM を有効にしてテストします。
  
> [!TIP]
> 
            [ここ](http://aka.ms/catlgstack)をクリックして、One Microsoft Cloud のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップをご確認ください。
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>フェーズ 1: Office 365 開発/テスト環境を構築する

最小要件で軽量な方法で機密性の高いファイルの保護をテストする場合は、フェーズ 2 と 3[の開発/テスト環境を Office 365](office-365-dev-test-environment.md)の指示に従います。
  
シミュレートされた企業内の機密性の高いファイルの保護をテストする場合は、 [Office 365 の開発/テスト環境のディレクトリ同期](dirsync-for-your-office-365-dev-test-environment.md)に指示します。
  
> [!NOTE]
> 機密性の高いファイルの保護をテストするのに、インターネットに接続されたシミュレーション イントラネットと Windows Server AD フォレスト用のディレクトリ同期を含めた、シミュレーション エンタープライズの開発/テスト環境は必要ではありません。この指示は、一般的な組織と類似した環境で機密性の高いファイルの保護をテストしてお試しいただけるようオプションとしてここで提供しています。 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>フェーズ 2:アクセス許可で保護されたサイトのドキュメントがどのようにリークされる場合があるのかをデモする

このフェーズでは、何者かによってドキュメントがアクセス許可で保護されたサイトからダウンロードされて、制限が緩いサイトにアップロードされることがあり得るということをデモします。
  
最初に、エグゼクティブを表す 3 つの新しいユーザー アカウントを追加して、Office 365 E5 ライセンスを割り当てます。
  
PowerShell モジュール (必要な場合) をインストールしてから新しい Office 365 サービスに接続するには、 [Office 365 の PowerShell への接続](https://technet.microsoft.com/library/dn975125.aspx)の手順を使用します。
  
- 自分のコンピューター (ライトウェイトの Office 365 開発/テスト環境の場合)。
    
- CLIENT1 仮想マシン (シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合)。
    
**Windows PowerShell の資格情報の要求**] ダイアログ ボックスで、Office 365 グローバル管理者名を入力します (例: jdoe@contosotoycompany.onmicrosoft.com) と、Office 365 の試用版サブスクリプションのパスワードです。
  
組織名 (例: contosotoycompany) と、所属地域に該当する 2 文字の国別コードを入力して、Windows PowerShell 用 Windows Azure Active Directory Module のプロンプトから次のコマンドを実行します。
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**新しい MsolUser**コマンドの表示から、生成されたアカウントのパスワードを最高経営責任者に注意してくださいし、安全な場所に記録します。
  
次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**新しい MsolUser**コマンドの表示、CFO のアカウントのパスワードが生成されたパスワードに注意してくださいし、安全な場所に記録します。
  
次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**新しい MsolUser**コマンドの表示、COO のアカウントのパスワードが生成されたパスワードに注意してくださいし、安全な場所に記録します。
  
次に、プライベート エグゼクティブ グループを作成し、そこに新しいエグゼクティブ アカウントを追加します。
  
1. お使いのブラウザーでは、 [http://portal.office.com](http://portal.office.com)で、Office のポータルに移動し、Office 365 試用版サブスクリプションのグローバル管理者アカウントでサインインします。
    
  - 簡易版の Office 365 開発/テスト環境を使用している場合は、Internet Explorer か任意のブラウザーのプライベート セッションを開いて、ローカル コンピューターからサインインします。
    
  - シミュレーション エンタープライズの Office 365 開発/テスト環境を使用している場合は、Azure ポータルを使用して CLIENT1 仮想マシンに接続し、CLIENT1 からサインインします。
    
2. [ **Microsoft Office のホーム**] タブをクリックして**管理 > グループ > グループ**、**グループの追加**] をクリックします。
    
3. **グループの追加**] グループの種類の**Office 365 のグループ**を選択**役員****名**と**グループ Id**、**プライバシー**、**プライベート**を選択し、入力し、[**所有者の選択**] をクリックします。
    
4. リストで、全体管理者のアカウント名をクリックします。
    
5. **追加**] をクリックし、[**閉じる**] をクリックします。
    
6. グループ] ボックスの一覧で、**経営幹部**をクリックします。
    
7. **メンバーの編集**] をクリックします。
    
8. [**メンバーの追加**] をクリックします。メンバーの一覧で、次のユーザー アカウントを選択します。
    
  - 最高経営責任者
    
  - 最高財務責任者
    
  - 最高執行責任者
    
9. **保存**] をクリックし、[**閉じる**] をクリックします。
    
10. **Office 管理者センター** ] タブを閉じます。
    
次に、エグゼクティブ サイト コレクションを作成し、エグゼクティブ グループのメンバーのみにこのコレクションへのアクセスを許可します。
  
1. **Microsoft Office ホーム**] タブで、**管理者**のタイルをクリックします。
    
2. **Office 管理者センター** ] タブで、クリックして**管理センター > SharePoint**。
    
3. [ **SharePoint 管理センター** ] タブをクリックして**新規 > プライベート サイト コレクション**です。
    
4. 新しいサイト コレクション] ウィンドウで、**タイトル**] に、[URL] ボックスで、経営**幹部**を入力で**管理者**は、グローバル管理者アカウントの名前を指定**]**をクリックします。
    
5. 新しいサイト コレクションが作成されるまで待機します。完了すると、新しい経営陣のサイト コレクションの URL をコピーし、お使いのブラウザーの新しいタブに貼り付けます。
    
6. **経営幹部**のサイト コレクションの右上に設定アイコンをクリック**と共有**] をクリックします。
    
7. **共有 '経営'**の場合は、[**詳細**を] をクリックします。
    
8. SharePoint グループのリストでは、**経営幹部のメンバー**をクリックします。
    
9. **[ユーザーとグループ]** ページで、**[新規]** をクリックします。
    
10. **共有 '経営'**に**経営幹部**を入力、**経営幹部**のグループ、**共有**] をクリックします。
    
11. **ユーザーとグループ**] タブを閉じます。
    
次に、販売サイト コレクションへのアクセスを許可します。
  
1. **SharePoint 管理者センター** ] タブで、販売サイト コレクションの URL をコピーし、ブラウザーの新しいタブに貼り付けます.
    
2. 、右上の設定アイコンをクリックする**と共有**] をクリックします。
    
3. **共有 '販売サイト コレクション'**の場合は、[**詳細**] をクリックします。
    
4. 、SharePoint グループの一覧では、**販売サイトのコレクションのメンバー**をクリックします。
    
5. **[ユーザーとグループ]** ページで、**[新規]** をクリックします。
    
6. **共有 '販売サイト コレクション'**に**Everyone**と入力、**外部のユーザーを除くすべて**] をクリックし、**共有**] をクリックします。
    
7. **販売サイト コレクション**、および**SharePoint**のタブを閉じます。
    
次に、エグゼクティブ アカウントでサインインし、エグゼクティブ サイト コレクションでドキュメントを作成します。
  
1. [場所] タブの [ **Microsoft Office のホーム**右の [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。
    
2. [Http://portal.office.com](http://portal.office.com)に移動します。
    
3. **Office 365 のサインイン**ページで、**別のアカウントを使用**] をクリックします。
    
4. **最高経営責任者**のアカウント名とそのパスワードを入力し、[**サインイン**] をクリックします。
    
5. お使いのブラウザーの新しいタブのエグゼクティブのサイト コレクションの URL を入力します ( **https://**\<組織名 >**.sharepoint.com/sites/executives**)。
    
6. **ドキュメント**] をクリックして、[**新規作成**] をクリックし、[ **Word 文書**] をクリックします。
    
7. タイトル バーをクリックし、 **SensitiveData BeforeIRM**を入力します。
    
8. 文書の本文に、**最新の委員会からの分**を入力をクリック**経営幹部**。
    
     [**ドキュメント**] フォルダー内の**SensitiveData BeforeIRM.docx**を参照してくださいする必要があります。
    
次に、SensitiveData BeforeIRM.docx ドキュメントのローカル コピーをダウンロードして、販売サイト コレクションに誤って投稿します。
  
1. ローカル コンピューターに新しいフォルダーを作成します (たとえば、c:\\TLGs\\SensitiveDataTestFiles)。
    
2. お使いのブラウザーの [**ドキュメント**] タブで**SensitiveData BeforeIRM.docx**のドキュメントを選択して、楕円では、し、[**ダウンロード**] をクリックします。
    
3. 手順 1 で作成したフォルダーに**SensitiveData BeforeIRM.docx**のドキュメントを格納します。
    
4. お使いのブラウザーの新しいタブの販売サイト コレクションの URL を入力します ( **https://**\<組織名 >**.sharepoint.com/sites/sales**)。
    
5. の**販売サイト コレクション**の [**ドキュメント**] フォルダーをクリックします。
    
6. **アップロード**する] をクリックし、手順 1 で作成したフォルダーに**SensitiveData BeforeIRM.docx**のドキュメントを指定し、[ **OK**] をクリックします。
    
7. **SensitiveData BeforeIRM.docx**ドキュメントが、[**ドキュメント**] フォルダーを確認します。
    
8. **販売**および**SharePoint**のタブを閉じます。
    
次に、User5 としてサインインして、販売サイト コレクションのドキュメント noSensitiveData-BeforeIRM.docx を開いてみます。
  
1. [場所] タブの [ **Microsoft Office のホーム**右の [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。
    
2. [Http://portal.office.com](http://portal.office.com)に移動します。
    
3. **Office 365 のサインイン**ページで、**別のアカウントを使用**] をクリックします。
    
4. User5 アカウント名とそのパスワードを入力し、[**サインイン**] をクリックします。
    
5. 、お使いのブラウザーの新しいタブでは、営業サイト コレクションの URL を入力します。
    
6. の**販売サイト コレクション**の [**ドキュメント**] フォルダーでは、 **SensitiveData BeforeIRM.docx**のドキュメントをクリックします。
    
    内容が表示されます。
    
7. **販売サイト コレクション**の**ドキュメント**とタブを閉じます。
    
SensitiveData-BeforeIRM.docx ドキュメントを販売サイト コレクションに誤って投稿することにより、CEO はエグゼクティブ サイト コレクションのアクセス許可セキュリティをバイパスします。
  
Office 365 をフェーズ 3 と 4 のために準備するには、SharePoint Online の IRM を有効にします。
  
1. [場所] タブの [ **Microsoft Office のホーム**右の [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。
    
2. [Http://portal.office.com](http://portal.office.com)に移動します。
    
3. **Office 365 のサインイン**ページで、グローバル管理者のアカウント名をクリックを選択し、そのパスワードを入力し、[**サインイン**] をクリックします。
    
4. [ **Microsoft Office のホーム**] タブをクリックして**管理 > 管理センター > SharePoint**。
    
5. [場所] タブの [ **SharePoint の管理センター**には、[**設定**] をクリックします。
    
6. [**設定**] ページで、**情報権利管理 (IRM)** ] セクションでは、**構成では、指定された IRM サービスを使用して**を選択し、 **IRM 設定の更新**] を選択します。
    
7. **SharePoint 管理者センター** ] タブを閉じます。
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>フェーズ 3：SharePoint Information Rights Management を Office 365 のプライベート グループとともに使用する

このフェーズでは、SharePoint Information Rights Management を Office 365 のプライベート グループとともに使用することにより、機密性の高いドキュメントが制限の緩いサイトに投稿された場合でも、そのドキュメントへのアクセスが保護されるようにします。
  
最初に、エグゼクティブ サイト コレクションのドキュメント ライブラリ用に IRM を有効にして設定します。  
  
1. 、お使いのブラウザーの新しいタブでは、経営幹部のサイト コレクションの URL を入力します。
    
2. [**ドキュメント**] をクリックします。
    
3. 、右に設定アイコンをクリックして**ライブラリの設定**] をクリックします。
    
4. [**設定**] ページで、[**権限と管理**、**情報権利の管理**をクリックします。
    
5. [ **Information Rights Management 設定**] ページ。
    
  - **ダウンロード時にこのライブラリのドキュメントに対するアクセス許可を制限する**を選択します。
    
  - **アクセス許可ポリシーのタイトルの作成**、**経営幹部**を入力します。
    
  - **追加のアクセス許可ポリシーの説明**、**経営幹部の IRM**を入力します。
    
6. **オプションを表示する**] をクリックします。
    
7. **IRM の追加のライブラリの設定を設定**すると、下には、 **IRM をサポートしていないドキュメントのアップロードを許可しない**を選択します。
    
8. **構成ドキュメントのアクセス権**、[**印刷を許可するビューアー**および**ダウンロードされたドキュメントのコピーを作成するのには許可のあるユーザー**を選択します。
    
9. **グループの保護および資格情報の間隔を設定**すると、[**グループの保護を許可する**] を選択しの**既定のグループ**を、**経営幹部**を入力します。
    
10. **[OK]** をクリックします。
    
次に、CEO として新しいドキュメントをエグゼクティブ ドキュメント フォルダーにアップロードし、それをダウンロードして、販売ドキュメント フォルダーに誤ってアップロードします。
  
1. **SensitiveData BeforeIRM.docx**ドキュメントを格納するローカル フォルダーを開きます。
    
2. **SensitiveData BeforeIRM.docx**を右クリックし、[**コピー**] をクリックします。
    
3. フォルダー内を右クリックし、[**貼り付け**] をクリックします。
    
4. **SensitiveData AfterIRM.docx**に新しい**SensitiveData-BeforeIRM - Copy.docx**ファイルの名前を変更します。
    
5. **マイクロソフト オフィス ホーム**] タブからお使いのブラウザーで、右の [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。
    
6. [Http://portal.office.com](http://portal.office.com)に移動します。
    
7. **Office 365 のサインイン**ページで、最高経営責任者のアカウント名をクリックして、そのパスワードを入力し、[**サインイン**] をクリックします。
    
8. 、お使いのブラウザーの新しいタブでは、経営幹部のサイト コレクションの URL を入力します。
    
9. [**ドキュメント**] ページで、[**アップロード**] をクリックを選択し、 **SensitiveData AfterIRM.docx**ドキュメントをローカル フォルダーに指定し、[**開く**] をクリックします。
    
10. **[ドキュメント**] ページで新しい**SensitiveData AfterIRM.docx**ドキュメントを選択、メニュー バーで、省略符号ボタン (...)] をクリックし、[**ダウンロード**] をクリックします。
    
11. ダイアログ ボックスが表示されたら、元のバージョンを上書きする、ローカルのフォルダーに**SensitiveData AfterIRM.docx**のドキュメントを保存します。
    
12. **[ドキュメント**] ページのタブを閉じます。
    
13. 、お使いのブラウザーの新しいタブでは、営業サイト コレクションの URL を入力します。
    
14. [**ドキュメント**] をクリックします。
    
15. [**ドキュメント**] ページで、[**アップロード**] をクリックを選択し、 **SensitiveData AfterIRM.docx**ドキュメントをローカル フォルダーに指定し、[**開く**] をクリックします。
    
16. **販売サイト コレクション**、および**SharePoint**のタブを閉じます。
    
次に、通常のユーザーとして動作しているしようとする販売ドキュメント フォルダー内の**SensitiveData AfterIRM.docx**のドキュメントにアクセスします。
  
1. **マイクロソフト オフィス ホーム**] タブからお使いのブラウザーで、右の [ユーザー] アイコンをクリックし、[**サインアウト**] をクリックします。
    
2. [Http://portal.office.com](http://portal.office.com)に移動します。
    
3. **Office 365 のサインイン**ページで、User5 のアカウント名をクリックを選択し、そのパスワードを入力し、[**サインイン**] をクリックします。
    
4. 、お使いのブラウザーの新しいタブでは、営業サイト コレクションの URL を入力します。
    
5. [**ドキュメント**] をクリックします。
    
6. [**ドキュメント**] ページで、 **SensitiveData AfterIRM.docx**のドキュメントを開きます。
    
    「申し訳ありません。このドキュメントは Information Rights Management (IRM) によって保護されているため、Word Online で開くことはできません。」というメッセージが表示されます。  
    
7. **Word で編集**] をクリックします。場合は、ファイルを開くことが求められます。**[はい]**をクリックします。
    
8. サインインするメッセージが表示されたら、User5 のアカウントのアカウント名を入力し、[**次へ**] をクリックします。
    
9. パスワードの入力を求められます。User5 アカウントのパスワードを入力し、[**サインイン**] をクリックします。 
    
    次のメッセージが表示されます。「このドキュメントを開くための資格情報がありません。」
    
10. [**いいえ**を] をクリックします。
    
IRM による保護を参照する別の方法では、ローカル フォルダー内のファイルを検索します。**SensitiveData AfterIRM.docx** **SensitiveData BeforeIRM.docx**ファイルをはるかに超える必要があります。**SensitiveData AfterIRM.docx**ファイルが暗号化されており、IRM 保護の情報が追加。
  
## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)


