---
title: Office 365 IdFix ツールをインストールして実行する
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: get-started-article
f1_keywords:
- O365E_HRCSetupAADConnectIDFixLM617036
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: f4bd2439-3e41-4169-99f6-3fabdfa326ac
description: office 365 idfix ツールをインストールして実行し、office 365 に同期する前に active directory をクリーンアップする方法について説明します。
ms.openlocfilehash: a35b2a476f2b30eccc955b980eda6315b146af27
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085406"
---
# <a name="install-and-run-the-office-365-idfix-tool"></a>Office 365 IdFix ツールをインストールして実行する

idfix を使用すると、Office 365 と同期する前に、ディレクトリ内の重複や書式設定の問題などのエラーが識別されます。 
  
このタスクを正常に完了するには、Active Directory 内のユーザー、グループ、および連絡先オブジェクトに慣れている必要があります。
  
このタスクを完了できない場合は、他にもいくつかの操作を実行できます。これらのメソッドは簡単になる場合もありますが、時間がかかる場合や他の欠点がある場合もあります。次のようになります。
  
- **idfix を実行せずにディレクトリ同期を実行します。** idfix ツールを実行せずにディレクトリを同期することはできますが、お勧めしません。同期の前にエラーを修正するには時間がかかり、多くの場合、クラウドへの移行がよりスムーズになります。 
- **コンサルタントを雇います。**  専門家に援助してもらうと、ユーザーは迅速に実務に使用でき、管理者はディレクトリ同期を完了させることができます。 
    
## <a name="what-you-need-to-run-idfix"></a>IdFix を実行するために必要な事柄

idfix を入手して実行する最も簡単な方法は、ドメインに参加しているコンピューターにインストールすることです。必要であれば、ドメインコントローラー上で実行できますが、これは必須ではありません。
  
### <a name="idfix-hardware-requirements"></a>IdFix のハードウェア要件

idfix をインストールするコンピューターは、以下の最小ハードウェア要件を満たす必要があります。
  
- 4 GB RAM
- 2 GB のハードディスク容量
    
### <a name="idfix-software-requirements"></a>IdFix のソフトウェア要件

idfix をインストールするコンピューターは、ユーザーを Office 365 に同期するのと同じ Active Directory ドメインに参加させる必要があります。また、コンピューターには .net Framework 4.0 がインストールされている必要があります。 
  
windows server 2008 または windows server 2012 を実行している場合は、.net Framework が既にインストールされている可能性があります。それ以外の場合は、ダウンロードセンターから、または Windows Update を通じ[て .net 4.0 をダウンロード](https://go.microsoft.com/fwlink/p/?LinkId=400475)することができます。 
  
### <a name="idfix-permissions-requirements"></a>IdFix アクセス許可の要件

IdFix を実行するためのユーザー アカウントには、ディレクトリへの読み取り/書き込みアクセス権が必要です。
  
ユーザーアカウントがこれらの要件を満たしているかどうかを確認できず、確認する方法がわからない場合でも、idfix をインストールして実行することができます。ユーザーアカウントが適切なアクセス許可を持っていない場合、idfix は、実行しようとしたときにエラーを表示するだけです。
  
## <a name="install-idfix"></a>IdFix のインストール

idfix をインストールするには、次のようにして、 **idfix .exe**をダウンロードして解凍します。 
  
1. IdFix ツールをインストールするコンピューターにログオンします。
    
2. [idfix DirSync エラー修復ツール](https://go.microsoft.com/fwlink/?linkid=867219)の Microsoft ダウンロードサイトに移動します。
    
3. [**Download**] を選択します。
    
4. メッセージが表示されたら、[**実行**] を選択します。
    
5. [ **WinZip 自己抽出**機能] ダイアログボックスの [**フォルダーに解凍**] テキストボックスに、idfix ツールをインストールする場所を入力または参照します。既定では、idfix はに`C:\Deployment Tools\`インストールされます。 
    
6. [ **Unzip**] を選択します。
    
## <a name="run-the-idfix-tool"></a>IdFix ツールの実行

IdFix をインストールした後、次のようにツールを実行してディレクトリでの問題を検索します。
  
1. ディレクトリへの読み取り/書き込みアクセス権を持つアカウントを使用して、IdFix をインストールしたコンピューターにログオンします。
    
2. エクスプローラーで、idfix をインストールした場所に移動します。インストール時に既定のフォルダーを選択した場合`C:\Deployment Tools\IdFix`は、に移動します。
    
3. **IdFix.exe** をダブルクリックします。 
    
    ![idfix .exe ファイルを選択します。](media/a9387bbc-991f-41c2-a500-45e3ce574285.JPG)
  
4. 既定では、idfix はマルチテナントルールセットを使用して、ディレクトリ内のエントリをテストします。これは、ほとんどの Office 365 お客様のための適切なルールセットです。ただし、Office 365 専用または ITAR (肘掛けされた国際トラフィック) のお客様の場合は、idfix を構成して、代わりに専用のルールセットを使用することができます。お客様の種類がわからない場合は、この手順を省略しても問題ありません。ルールセットを専用に設定するには、メニューバーの歯車アイコンをクリックして、[**専用**] を選択します。
    
5. [**クエリ**] を選択します。
    
    ![idfix で [クエリ] を選択します。](media/a07a7aa7-d0ac-4817-8757-946019813a57.JPG)
  
6. 既定では、IdFix は、ディレクトリ全体のエラーを検索します。
    
    ディレクトリのサイズによっては、クエリの実行に時間がかかることがあります。ツールのメインウィンドウの下部にある進捗状況を確認できます。[**キャンセル**] をクリックした場合は、最初から再起動する必要があります。
    
    ![idfix クエリとエラーカウント。](media/da0198a0-7d4d-4afe-a256-e82f1330ada5.JPG)
  
7. idfix がクエリを完了したら、エラーがない場合にディレクトリを同期することができます。ディレクトリにエラーがある場合は、同期する前にそれらを修正することをお勧めします。エラーの種類や、それぞれの問題を解決するための推奨事項についてのより詳細な情報が必要な場合は、このトピックの最後にあるリンクを参照してください。 
    
    同期の前にエラーを修正することは必須ではありませんが、IdFix によって戻されたエラーすべてを少なくても確認することを是非お勧めします。
    
    各エラーは、ツールのメインウィンドウの独立した行に表示されます。 
    
8. **[UPDATE]** 列の提案されている変更に同意する場合、変更を実装するための IdFix による実行内容を **[ACTION]** 列で選択し、**[Apply]** をクリックします。**[Apply]** をクリックすると、ツールによってディレクトリに変更が加えられます。
    
    更新のたびに [**適用**] をクリックする必要はありません。その代わりに、[**適用**] をクリックする前にいくつかのエラーを修正し、idfix によってすべて同時に変更することができます。エラーの種類を一覧表示する列の上部にある [**エラー** ] をクリックすると、エラーの種類別にエラーを並べ替えることができます。 
    
    1つの方法は、同じ種類のすべてのエラーを修正することです。たとえば、最初にすべての重複を修正して適用します。次に、文字書式エラーなどを修正します。変更を適用するたびに、idfix ツールによって別のログファイルが作成されます。このファイルを使用すると、誤った変更を行った場合に、変更を元に戻すことができます。[トランザクションログ](idfix-transaction-log.md)は、インストールした idfix のフォルダーに格納されます。 既定では、 _c:\windows 展開ツール \ 修正プログラム_が適用されます。 
    
    ![idfix で修復エラーが発生しました。](media/5f051070-652c-4be7-98bf-312295e32371.png)
  
9. ディレクトリにすべての変更が加えられたら、idfix を再度実行して、作成した修正プログラムで新しいエラーが発生していないことを確認してください。必要な回数だけこれらの手順を繰り返すことができます。同期する前に、このプロセスを何度か実行することをお勧めします。
    
## <a name="i-want-to-refine-my-search-or-dig-deeper-into-the-errors-what-else-can-i-do-with-idfix"></a>検索を絞り込むか、エラーをさらに掘り下げるには、IdFix でさらに何を行えますか?

詳細な情報は以下のトピックに記載されています。
  
- [idfix ツールを使用して、Office 365 と同期するディレクトリ属性を準備](prepare-directory-attributes-for-synch-with-idfix.md)します。ツールをインストールしたら、このトピックに移動して、ツールの実行方法、発生する一般的なエラー、推奨される修正、例、および多数のエラーが発生した場合の対処方法について説明します。 
- [リファレンス: IdFix で除外されるオブジェクトと属性、およびサポートされるオブジェクトと属性](idfix-excluded-and-supported-objects-and-attributes.md)  
- [リファレンス: Office 365 IdFix トランザクション ログ](idfix-transaction-log.md)
    
## <a name="video-training"></a>ビデオ トレーニング

詳細については、レッスン「[インストールと使用](https://support.office.com/article/install-and-use-the-idfix-tool-4d81d73c-f172-4fd5-8542-f601c0c96aa9?ui=en-US&rs=en-US&ad=US)」を参照してください。このツールは、LinkedIn Learning によって提供されています。
  

