---
title: Microsoft 365 IDFix ツールのダウンロードと実行
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Priority
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365E_HRCSetupAADConnectIDFixLM617036
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: Microsoft 365 IDFix ツールをダウンロードして実行し、Active Directory ドメイン サービス (AD DS) をクリーンアップしてから Microsoft 365 に同期する方法について説明します。
ms.openlocfilehash: beef13857ad00806cc3e62aedd7a1b3c48bfe4c0
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502662"
---
# <a name="download-and-run-the-microsoft-365-idfix-tool"></a>Microsoft 365 IDFix ツールのダウンロードと実行

*この記事は、Microsoft 365 Enterprise および Office 365 Enterprise の両方に適用されます。*

IDFix は、Microsoft 365に同期する前に、Active Directory Domain Services (AD DS) ドメイン内にある重複や形式設定の問題などのエラーを特定します。 
  
このタスクを正常に終了するには、AD DS でユーザー、グループ、連絡先のオブジェクトを簡単に操作できる必要があります。
  
このタスクを完了できない場合は、他にいくつか方法があります。 これらの方法はより簡単ですが、時間がかかる場合や、他に不具合が出る場合があります。 以下にその例を示します。
  
- **IDFix を実行せずにディレクトリ同期を実行する** 

  IDFix ツールを使用せずディレクトリを同期できますが、これは推奨されていません。 同期前のエラー修正は短時間で行うことができ、多くの場合、クラウドによりスムーズに移行できるようになります。 

- **コンサルタントを雇う** 

  専門家に援助してもらうと、ユーザーは迅速に実務に使用でき、管理者はディレクトリ同期を完了させることができます。 
    
## <a name="what-you-need-to-run-idfix"></a>IDFix を実行するために必要な事柄

IDFix を実行するための最も簡単な方法は、ご使用の AD DS ドメインに参加しているコンピューターにダウンロードすることです。 希望する場合にはドメイン コントローラーで実行できますが、必須ではありません。
  
### <a name="idfix-hardware-requirements"></a>IDFix のハードウェア要件

IDFix をダウンロードするコンピューターは、以下のハードウェア要件を最低限満たしている必要があります。
  
- 4 GB RAM
- 2 GB のハードディスク容量
   
### <a name="idfix-software-requirements"></a>IDFix のソフトウェア要件

IDFix をダウンロードするコンピューターは、Microsoft 365 に同期するユーザーが存在する AD DS ドメインと同じドメインに参加している必要があります。 

またコンピューターには .NET Framework 4.0 をインストールしておく必要があります。 Windows Server 2008 以降を実行している場合は、.NET Framework が既にインストールされている可能性があります。 表示されていない場合は、[[ダウンロードセンター]](https://go.microsoft.com/fwlink/p/?LinkId=400475) または [Windows Update] から .NET 4.0 をダウンロードしてください。 
  
### <a name="idfix-permissions-requirements"></a>IDFix アクセス許可の要件

IDFix を実行するためのユーザー アカウントには、AD DS ドメインへの読み取り/書き込みアクセス権が必要です。
  
使用しているユーザー アカウントがこうした要件を満たしているかどうか不確かで、その確認方法が分からない場合であっても、IDFix のダウンロードして実行することは可能です。 ユーザー アカウントに正しい許可がない場合、実行を試みると IDFix によってその旨のエラーが表示されます。
  
## <a name="download-and-extract-idfix"></a>IDFix をダウンロードして抽出する

手順は次のとおりです。 
  
1. IDFix ツールを実行するコンピューターにサインインします。
    
2. [IDFix DirSync エラー修復ツール](https://github.com/microsoft/idfix) のサイトに移動します。
    
3. [**ClickOnce 起動**] セクションの [**起動**] をクリックして、zip ファイルをダウンロードします。 Zip ファイルを開きます。
    
4. [**IdFix**] ウィンドウで、[**抽出**] を選択し、**すべて抽出**します。 既定では、IDFix は `C:\Users\<your user name>\Documents\IdFix` に抽出されます。 
    
5. [**展開**] を選択します。

手順は、使用している Windows のバージョンとインターネット ブラウザーによって異なる場合があります。
    
## <a name="run-the-idfix-tool"></a>IDFix ツールの実行

IDFix をダウンロードして抽出したら、それを実行して AD DS ドメインの問題を検索します。
  
1. AD DS ドメインへの読み取り/書き込みアクセス権を持つアカウントを使用して、IDFix をダウンロードしたコンピューターにサインインします。
    
2. ファイル エクスプローラーで、IDFix を抽出した場所に移動します。 抽出中に既定のフォルダーを選択した場合は、`C:\Users\<your user name>\Documents\IdFix` に移動します。 
    
3. **IdFix.exe** をダブルクリックします。 
  
4. 既定では、IDFix はマルチテナントのルール セットを使用して、ディレクトリ内の項目をテストします。 これは、ほとんどの Microsoft 365 のお客様にとって適正なルール セットです。 ただし、Microsoft 365 Dedicated または ITAR (国際武器取引規約) のお客様は、代わりに Dedicated ルールを使用するように IDFix を構成できます。 お客様の種類が分からない場合には、この手順をスキップしても差し支えありません。 Dedicated にルール セットを設定するには、メニュー バーで歯車のアイコンをクリックして **[Dedicated]** を選択します。
    
5. [**クエリ**] を選びます。
    
    ![IDFix でクエリを選択します。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. 既定では、IDFix は、ディレクトリ全体のエラーを検索します。
    
    ディレクトリのサイズによっては、照会の実行にしばらく時間がかかります。 ツールのメイン ウィンドウの下部で進行状況を確認できます。 **[キャンセル]** をクリックする場合、最初からやり直す必要があります。
  
7. IDFix による照会の完了後、ディレクトリにエラーがない場合には、続行してディレクトリを同期できます。 ディレクトリ内にエラーがある場合は、同期する前にそれらを修正することをお勧めします。 詳細については、[「IDFix ツールを使用して Microsoft 365 と同期するためにディレクトリ属性を準備する」](prepare-directory-attributes-for-synch-with-idfix.md) を参照してください。
    
    同期の前にエラーを修正することは必須ではありませんが、IDFix によって戻されたエラーすべてを少なくても確認することを是非お勧めします。
    
    各エラーは、ツールのメイン ウィンドウに別々の行で表示されます。 
    
8. **[更新]** 列の提案されている変更に同意する場合、変更を実装するための IDFix による実行内容を **[アクション]** 列で選択し、**[適用]** をクリックします。 [**適用**] をクリックすると、ツールがディレクトリ内で変更を実行します。
    
    更新のたびに **[適用]** をクリックする必要はありません。 代わりに、**[適用]** をクリックする前に幾つかのエラーを修正すると、IDFix によって同時にすべてが変更されます。 エラーの種類を示している列の上部にある [**エラー**] をクリックすると、エラーを種類ごとに並べることができます。 
    
    1 つの方法として、同じ種類のエラーすべてを修正できます。たとえば、最初に、重複をすべて修正し、それらを適用します。 次に、文字形式のエラーを修正するなどします。 変更を適用するたびに、IDFix ツールによって別のログ ファイルが作成され、ミスが生じた場合にそうした変更を元に戻すために使用できます。 [トランザクション ログ](idfix-transaction-log.md) は、IDFix を抽出したフォルダーに格納されます。これは、既定では _C:\Users\<your user name>\Documents\IdFix_ です。 
    
    ![IDFix でエラーを修復します。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. すべての変更をディレクトリに加えた後、IDFix をもう一度実行し、加えた修正により新しいエラーが生じていないことを確認してください。 これらの手順を必要なだけ繰り返すことができます。 同期する前に、少々時間を取ってこの処理を行うことをお勧めします。
    
## <a name="additional-resources-on-idfix"></a>IDFix のその他のリソース 

- [IDFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性](idfix-excluded-and-supported-objects-and-attributes.md)  
- [Microsoft 365 IDFix トランザクション ログ](idfix-transaction-log.md)
    
