---
title: Office 365 の開発/テスト環境での機密性の高いファイルの保護
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- SPO_Content
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 27ecff45-06a6-4629-bc45-9dab4eef3a21
description: '概要: Office 365 Information Rights Management が、誤った SharePoint Online サイトコレクションに投稿された場合でも、機密ファイルを保護する方法を構成し、デモンストレーションします。'
ms.openlocfilehash: b8cb56a69a04133b2863c31da9e359c2272d4fc5
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2019
ms.locfileid: "38078126"
---
# <a name="sensitive-file-protection-in-the-office-365-devtest-environment"></a>Office 365 の開発/テスト環境での機密性の高いファイルの保護

 **概要:** Office 365 Information Rights Management が、誤った SharePoint Online サイトコレクションに投稿された場合でも、機密ファイルを保護する方法を構成し、デモンストレーションします。
  
Office 365 の Information Rights Management (IRM) は、SharePoint Online ライブラリとリストからダウンロードしたドキュメントを保護する機能のセットです。ダウンロードしたファイルは暗号化されており、格納されていた SharePoint Online ライブラリを反映するアクセス許可 (オープン、コピー、保存、印刷) を含んでいます。
  
この記事の手順に従い、Office 365 試用版のサブスクリプションを使用して、機密性の高い情報を含む可能性のあるファイルに対して Office 365 で IRM を有効にしてテストします。
  
> [!TIP]
> [ここ](https://aka.ms/catlgstack)をクリックして、Office 365 のテスト ラボ ガイド スタックに含まれるすべての記事のビジュアル マップを確認してください。
  
## <a name="phase-1-build-out-your-office-365-devtest-environment"></a>フェーズ 1: Office 365 開発/テスト環境を構成する

最小要件で機密性の高いファイル保護を簡易な方法でテストする場合は、[Office 365 dev/test environment](office-365-dev-test-environment.md)のフェーズ 2 と 3 の指示に従ってください。
  
シミュレーション エンタープライズで機密性の高いファイル保護をテストする場合は、[DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md)の指示に従ってください。
  
> [!NOTE]
> 機密ファイル保護のテストでは、シミュレートされたエンタープライズ開発/テスト環境を使用する必要はありません。これには、インターネットに接続されたシミュレートされたイントラネットと Active Directory ドメインサービス (AD DS) フォレストのディレクトリ同期が含まれます。 この指示は、一般的な組織と類似した環境で機密性の高いファイルの保護をテストしてお試しいただけるようオプションとしてここで提供しています。 
  
## <a name="phase-2-demonstrate-how-documents-from-permissions-protected-sites-can-be-leaked"></a>フェーズ 2:アクセス許可で保護されたサイトのドキュメントがどのようにリークされる場合があるのかをデモする

このフェーズでは、何者かによってドキュメントがアクセス許可で保護されたサイトからダウンロードされて、制限が緩いサイトにアップロードされることがあり得るということをデモします。
  
最初に、エグゼクティブを表す 3 つの新しいユーザー アカウントを追加して、Office 365 E5 ライセンスを割り当てます。
  
「 [Office 365 powershell に接続](https://technet.microsoft.com/library/dn975125.aspx)する」の手順を使用して、powershell モジュールをインストールし (必要な場合)、新しい Office 365 サブスクリプションに接続します。
  
- 自分のコンピューター (軽量の Office 365 開発/テスト環境の場合)。
    
- CLIENT1 仮想マシン (シミュレーションのエンタープライズ Office 365 開発/テスト環境の場合)。
    
**[Windows PowerShell 資格情報の要求]** ダイアログ ボックスで、Office 365 全体管理者名 (例: jdoe@contosotoycompany.onmicrosoft.com) と Office 365 試用版のサブスクリプションのパスワードを入力します。
  
組織名 (例: contosotoycompany) と、所属地域に該当する 2 文字の国別コードを入力して、Windows PowerShell 用 Windows Azure Active Directory Module のプロンプトから次のコマンドを実行します。
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "ceo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CEO" -FirstName "Chief" -LastName "Executive Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**New-MsolUser** コマンドの表示から、CEO アカウント用に生成されたパスワードを見つけて、安全な場所に記録しておきます。
  
次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。
  
```
$userName= "cfo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "CFO" -FirstName "Chief" -LastName "Financial Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**New-MsolUser** コマンドの表示から、CFO アカウント用に生成されたパスワードを見つけて、安全な場所に記録しておきます。
  
次に示すコマンドを Windows PowerShell 用 Microsoft Azure Active Directory モジュールのプロンプトから実行します。
  
```
$userName= "coo@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "COO" -FirstName "Chief" -LastName "Operations Officer" -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment

```

**New-MsolUser** コマンドの表示から、COO アカウント用に生成されたパスワードを見つけて、安全な場所に記録しておきます。
  
次に、プライベート エグゼクティブ グループを作成し、そこに新しいエグゼクティブ アカウントを追加します。
  
1. ブラウザーで、Office ポータルに移動[https://admin.microsoft.com](https://admin.microsoft.com)し、全体管理者アカウントを使用して office 365 試用版サブスクリプションにサインインします。
    
  - 簡易版の Office 365 開発/テスト環境を使用している場合は、Internet Explorer か任意のブラウザーのプライベート セッションを開いて、ローカル コンピューターからサインインします。
    
  - シミュレーション エンタープライズの Office 365 開発/テスト環境を使用している場合は、Azure ポータルを使用して CLIENT1 仮想マシンに接続し、CLIENT1 からサインインします。
    
2. **[Microsoft Office Home]** タブで、**[管理]、[グループ]、[グループ]** の順にクリックして、**[グループを追加する]** をクリックします。
    
3. **[グループを追加]** で、グループの種類は **[Office 365 グループ]** を選びます。**[名前]** と **[グループ ID]** に「**エグゼクティブ**」と入力します。**[プライバシー]** は **[プライベート]** を選び、**[所有者の選択]** をクリックします。
    
4. リストで、全体管理者のアカウント名をクリックします。
    
5. **[追加]** をクリックして、**[閉じる]** をクリックします。
    
6. グループ リストで、**[エグゼクティブ]** をクリックします。
    
7. **[メンバー用に編集]** をクリックします。
    
8. **[メンバーの追加]** をクリックします。メンバー リストで、次のユーザー アカウントを選びます。
    
  - 最高経営責任者
    
  - 最高財務責任者
    
  - 最高執行責任者
    
9. **[保存]** をクリックし、**[閉じる]** をクリックします。
    
10. **[Office 管理センター]** タブを閉じます。
    
次に、エグゼクティブ サイト コレクションを作成し、エグゼクティブ グループのメンバーのみにこのコレクションへのアクセスを許可します。
  
1. **[Microsoft Office Home]** タブで、**[管理者]** タイルをクリックします。
    
2. [ **Office 管理センター** ] タブで、[**管理センター > SharePoint**] をクリックします。
    
3. [ **SharePoint 管理センター** ] タブで、[**新しい > [プライベートサイトコレクション**] をクリックします。
    
4. [サイト**コレクションの新規**作成] ウィンドウの [URL] ボックスに「**役職」と入力し**、**管理者**のグローバル管理者アカウントの名前を指定して、[ **OK]** をクリックします。
    
5. 新しいサイトコレクションが作成されるまで待機します。 完了したら、新しい重役サイトコレクションの URL をコピーして、ブラウザーの新しいタブに貼り付けます。
    
6. **エグゼクティブ** サイト コレクションの右上部分にある [設定] アイコンをクリックし、**[共有アイテム]** をクリックします。
    
7. [**共有 ' エグゼクティブ '**] で、[**詳細設定**] をクリックします。
    
8. SharePoint グループの一覧で、**[エグゼクティブ メンバー]** をクリックします。
    
9. **[ユーザーとグループ]** ページで、 **[新規]** をクリックします。
    
10. [**共有 ' エグゼクティブ '**] で、「**エグゼクティブ**」と入力し、[**重役**] グループをクリックして、[**共有**] をクリックします。
    
11. [**ユーザーとグループ**] タブを閉じます。
    
次に、販売サイト コレクションへのアクセスを許可します。
  
1. [ **SharePoint 管理センター** ] タブから、Sales サイトコレクションの URL をコピーして、ブラウザーの新しいタブに貼り付けます。
    
2. 右上部分で [設定] アイコンをクリックし、**[共有アイテム]** をクリックします。
    
3. [**共有 ' 販売サイトコレクション '**] で、[**詳細設定**] をクリックします。
    
4. SharePoint グループの一覧で、**[販売サイト コレクション メンバー]** をクリックします。
    
5. **[ユーザーとグループ]** ページで、**[新規]** をクリックします。
    
6. [**共有 ' 販売サイトコレクション '**] に「 **everyone**」と入力し、[**外部ユーザー以外のすべてのユーザー**] をクリックして、[**共有**] をクリックします。
    
7. **[販売サイト コレクション]** と **[SharePoint]** のタブを閉じます。
    
次に、エグゼクティブ アカウントでサインインし、エグゼクティブ サイト コレクションでドキュメントを作成します。
  
1. **[Microsoft Office Home]** タブで、右上部分にある [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。
    
2. [https://admin.microsoft.com](https://admin.microsoft.com) に移動します。
    
3. **Office 365 のサインイン** ページで、**[別のアカウントを使用する]** をクリックします。
    
4. **CEO** アカウント名とパスワードを入力し、**[サインイン]** をクリックします。
    
5. ブラウザーの新しいタブで、エグゼクティブサイトコレクションの URL を入力します ( **https://**\<organization name>**sharepoint.com/sites/executives**)。
    
6. [**ドキュメント**]、[**新規作成**]、[ **Word 文書**] の順にクリックします。
    
7. タイトル バーをクリックして、「**SensitiveData BeforeIRM**」と入力します。
    
8. ドキュメント本文をクリックして、「**取締役会の最新の会議メモ**」と入力し、**[エグゼクティブ]** をクリックします。
    
     **[ドキュメント]** フォルダーに、**SensitiveData BeforeIRM.docx** が表示されます。
    
次に、SensitiveData BeforeIRM.docx ドキュメントのローカル コピーをダウンロードして、販売サイト コレクションに誤って投稿します。
  
1. ローカルコンピューターで、新しいフォルダーを作成します (たとえば、C:\\tlgs\\SensitiveDataTestFiles)。
    
2. ブラウザーの **[ドキュメント]** タブで、**SensitiveData BeforeIRM.docx** ドキュメントを選び、省略記号をクリックして、**[ダウンロード]** をクリックします。
    
3. **SensitiveData BeforeIRM.docx** ドキュメントをステップ 1 で作成したフォルダーに格納します。
    
4. ブラウザーの新しいタブで、Sales サイトコレクションの URL を入力します ( **https://**\<organization name>**sharepoint.com/sites/sales**)。
    
5. **販売サイト コレクション** の **[ドキュメント]** フォルダーをクリックします。
    
6. **[アップロード]** をクリックし、ステップ 1 で作成したフォルダーの **SensitiveData BeforeIRM.docx** ドキュメントを指定して、**[OK]** をクリックします。
    
7. **[ドキュメント]** フォルダーに、**SensitiveData BeforeIRM.docx** ドキュメントが表示されていることを確認します。
    
8. **[販売]** と **[SharePoint]** のタブを閉じます。
    
次に、User5 としてサインインして、販売サイト コレクションのドキュメント noSensitiveData-BeforeIRM.docx を開いてみます。
  
1. **[Microsoft Office Home]** タブで、右上部分にある [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。
    
2. [https://admin.microsoft.com](https://admin.microsoft.com) に移動します。
    
3. **Office 365 のサインイン** ページで、**[別のアカウントを使用する]** をクリックします。
    
4. User5 アカウント名とパスワードを入力して、**[サインイン]** をクリックします。
    
5. ブラウザーの新しいタブで、Sales サイトコレクションの URL を入力します。
    
6. **販売サイト コレクション**の **[ドキュメント]** フォルダーで、**SensitiveData-BeforeIRM.docx** ドキュメントをクリックします。 
    
    内容が表示されます。
    
7. **[ドキュメント]** と **[販売サイト コレクション]** タブを閉じます。
    
SensitiveData-BeforeIRM.docx ドキュメントを販売サイト コレクションに誤って投稿することにより、CEO はエグゼクティブ サイト コレクションのアクセス許可セキュリティをバイパスします。
  
Office 365 をフェーズ 3 と 4 のために準備するには、SharePoint Online の IRM を有効にします。
  
1. **[Microsoft Office Home]** タブで、右上部分にある [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。
    
2. [https://admin.microsoft.com](https://admin.microsoft.com) に移動します。
    
3. **Office 365 のサインイン** ページで、全体管理者のアカウント名をクリックし、パスワードを入力して、**[サインイン]** をクリックします。
    
4. **[Microsoft Office Home]** タブで、**[管理者]、[管理センター]、[SharePoint]** の順にクリックします。
    
5. **[SharePoint 管理センター]** タブで、**[設定]** をクリックします。
    
6. ページの [ **Information Rights Management (irm)** ] セクションで、[**構成で指定された Irm サービスを使用する**] を選択し、[ **irm 設定の更新**] を選択します。
    
7. **[SharePoint 管理センター]** タブを閉じます。
    
## <a name="phase-3-use-sharepoint-information-rights-management-with-an-office-365-private-group"></a>フェーズ 3：SharePoint Information Rights Management を Office 365 のプライベート グループとともに使用する

このフェーズでは、SharePoint Information Rights Management を Office 365 のプライベート グループとともに使用することにより、機密性の高いドキュメントが制限の緩いサイトに投稿された場合でも、そのドキュメントへのアクセスが保護されるようにします。
  
最初に、エグゼクティブ サイト コレクションのドキュメント ライブラリ用に IRM を有効にして設定します。  
  
1. ブラウザーの新しいタブで、エグゼクティブサイトコレクションの URL を入力します。
    
2. **[ドキュメント]** をクリックします。
    
3. 右上部分にある [設定] アイコンをクリックし、**[ライブラリ設定]** をクリックします。
    
4. **[設定]** ページの **[権限と管理]** で、**[Information Rights Management]** をクリックします。
    
5. **[Information Rights Management 設定]** ページで、次のようにします。
    
  - **[このライブラリのドキュメントへのアクセスをダウンロード時に制限する]** を選択します。
    
  - **[アクセス許可ポリシーのタイトルを作成]** に、「**サポート**」と入力します。
    
  - **[アクセス許可ポリシーの説明を追加]** に、「**エグゼクティブ用の IRM**」と入力します。
    
6. [**オプションの表示**] をクリックします。
    
7. **[IRM ライブラリの追加設定]** で、**[ユーザーに IRM をサポートしないドキュメントのアップロードを許可しない]** を選択します。
    
8. **[ドキュメントのアクセス権の構成]** で、**[閲覧者に印刷を許可する]** と **[ダウンロードしたドキュメントのコピーに対する書き込みを閲覧者に許可する]** を選択します。
    
9. [**グループ保護と資格情報の設定間隔**] で、[グループ保護の許可] を選択し**ます。[既定のグループ**] をクリックし、「**役職**者」と入力します。
    
10. [**OK**] をクリックします。
    
次に、CEO として新しいドキュメントをエグゼクティブ ドキュメント フォルダーにアップロードし、それをダウンロードして、販売ドキュメント フォルダーに誤ってアップロードします。
  
1. **SensitiveData BeforeIRM.docx** ドキュメントを格納したローカル フォルダーを開きます。
    
2. **SensitiveData-BeforeIRM.docx** を右クリックして、**[コピー]** をクリックします。
    
3. フォルダー内を右クリックして、**[貼り付け]** をクリックします。
    
4. 新しい**SensitiveData-BeforeIRM-.docx**ファイルの名前を**sensitivedata-afterirm.docx**に変更します。
    
5. ブラウザーの **[Microsoft Office Home]** タブから、右上部分の [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。
    
6. [https://admin.microsoft.com](https://admin.microsoft.com) に移動します。
    
7. **Office 365 のサインイン** ページで、CEO アカウント名をクリックし、パスワードを入力して、**[サインイン]** をクリックします。
    
8. ブラウザーの新しいタブで、エグゼクティブサイトコレクションの URL を入力します。
    
9. **[ドキュメント]** ページで、**[アップロード]** をクリックし、ローカル フォルダーの **SensitiveData-AfterIRM.docx** ドキュメントを指定して、**[開く]** をクリックします。
    
10. **[ドキュメント]** ページで新しい **SensitiveData-AfterIRM.docx** ドキュメントを選び、メニュー バーの省略記号 (...) をクリックして、**[ダウンロード]** をクリックします。
    
11. 画面の指示に従って **SensitiveData-AfterIRM.docx** ドキュメントをローカル フォルダーに保存して、元のバージョンを上書きします。
    
12. **[ドキュメント]** ページのタブを閉じます。
    
13. ブラウザーの新しいタブで、Sales サイトコレクションの URL を入力します。
    
14. **[ドキュメント]** をクリックします。
    
15. **[ドキュメント]** ページで、**[アップロード]** をクリックし、ローカル フォルダーの **SensitiveData-AfterIRM.docx** ドキュメントを指定して、**[開く]** をクリックします。
    
16. **[販売サイト コレクション]** と **[SharePoint]** のタブを閉じます。
    
次に、通常のユーザーとして販売ドキュメント フォルダーの **SensitiveData-AfterIRM.docx** ドキュメントにアクセスします。
  
1. ブラウザーの **[Microsoft Office Home]** タブから、右上部分の [ユーザー] アイコンをクリックし、**[サインアウト]** をクリックします。
    
2. [https://admin.microsoft.com](https://admin.microsoft.com) に移動します。
    
3. **Office 365 のサインイン**ページで、User5 のアカウント名をクリックし、パスワードを入力して、[**サインイン**] をクリックします。
    
4. ブラウザーの新しいタブで、Sales サイトコレクションの URL を入力します。
    
5. **[ドキュメント]** をクリックします。
    
6. **[ドキュメント]** ページで、**SensitiveData-AfterIRM.docx** を開きます。 
    
    "申し訳ございません。この文書は Information Rights Management (IRM) で保護されているため、Word で開くことができません。" というメッセージが表示されます。 
    
7. **[Word で編集]** をクリックします。ファイルを開くかどうかを尋ねられます。**[はい]** をクリックします。
    
8. サインインするように要求されます。User5 アカウントのアカウント名を入力し、**[次へ]** をクリックします。
    
9. パスワードを入力するように要求されます。User5 アカウント用のパスワードを入力して、**[サインイン]** をクリックします。  
    
    次のメッセージが表示されます。「このドキュメントを開くための資格情報がありません。」
    
10. **[いいえ]** をクリックします。
    
IRM 保護を確認する別の方法として、ローカル フォルダー内のファイルを確認することもできます。**SensitiveData-AfterIRM.docx** ファイルは、**SensitiveData-BeforeIRM.docx** ファイルより大きいはずです。**SensitiveData-AfterIRM.docx** ファイルは暗号化されており、IRM 保護情報が追加されています。
  
## <a name="see-also"></a>関連項目

[クラウド導入のテスト ラボ ガイド (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[基本構成開発/テスト環境](base-configuration-dev-test-environment.md)
  
[Office 365 開発/テスト環境](office-365-dev-test-environment.md)
  
[クラウド導入およびハイブリッド ソリューション](cloud-adoption-and-hybrid-solutions.md)


