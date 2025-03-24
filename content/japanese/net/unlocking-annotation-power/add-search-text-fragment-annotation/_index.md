---
title: 検索テキストフラグメントの注釈をドキュメントに追加
linktitle: 検索テキストフラグメントの注釈をドキュメントに追加
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET の機能を活用し、ドキュメントの注釈機能をアプリケーションに簡単に追加します。
weight: 20
url: /ja/net/unlocking-annotation-power/add-search-text-fragment-annotation/
---
## 導入
.NET 開発の分野では、GroupDocs.Annotation はドキュメントにシームレスに注釈を付けるための強力なツールとして際立っています。経験豊富な開発者であっても、.NET の世界に足を踏み入れたばかりであっても、この包括的なチュートリアルでは、名前空間のインポートから、検索テキスト フラグメントの注釈を検索テキスト フラグメントに追加する複雑な操作の習得に至るまで、GroupDocs.Annotation for .NET を使用するための基本事項を説明します。書類。
## 導入
GroupDocs.Annotation for .NET を使用すると、開発者はドキュメントの注釈機能をアプリケーションに簡単に組み込むことができます。直感的な API と堅牢な機能により、開発者は PDF、Microsoft Office ドキュメント、画像などを含むさまざまなドキュメント形式に注釈を付けることができます。
## 前提条件
GroupDocs.Annotation for .NET に入る前に、次の前提条件が満たされていることを確認してください。

## 名前空間のインポート
まず、.NET プロジェクトの GroupDocs.Annotation クラスとメソッドにアクセスするために必要な名前空間をインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ステップ 1: 出力パスを定義する
まず、注釈付きドキュメントが保存される出力パスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ 2: アノテーターを初期化する
次に、のインスタンスを初期化します。`Annotator`注釈を付けたいドキュメントへのパスを指定してクラスを作成します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## ステップ 3: 検索テキストフラグメントの注釈を作成する
を作成します`SearchTextFragment`検索するテキスト、フォント サイズ、フォント ファミリー、フォントの色、背景色などの必要なプロパティを持つオブジェクト:
```csharp
SearchTextFragment searchText = new SearchTextFragment()
{
    Text = "Welcome to GroupDocs",
    FontSize = 10,
    FontFamily = "Calibri",
    FontColor = 65535,
    BackgroundColor = 16761035,
};
```
## ステップ 4: 注釈を追加する
作成した検索テキスト フラグメントの注釈をドキュメントに追加します。`Add`アノテーターのメソッド:
```csharp
annotator.Add(searchText);
```
## ステップ 5: 注釈付きドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
```
## ステップ 6: 成功メッセージを表示する
ドキュメントが正常に保存されたことをユーザーに通知します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
結論として、GroupDocs.Annotation for .NET はドキュメントに注釈を追加するプロセスを簡素化し、コラボレーションとドキュメント レビューのプロセスを強化します。このガイドで概説されている手順に従うことで、ドキュメントの注釈機能を .NET アプリケーションにシームレスに統合できます。
## よくある質問
### GroupDocs.Annotation はすべてのドキュメント形式と互換性がありますか?
はい、GroupDocs.Annotation は、PDF、Microsoft Office ドキュメント、画像などを含む幅広いドキュメント形式をサポートしています。
### 注釈の外観をカスタマイズできますか?
絶対に！ GroupDocs.Annotation は、注釈の広範なカスタマイズ オプションを提供し、フォント サイズ、色、スタイルなどのプロパティを調整できます。
### GroupDocs.Annotation に利用できる無料トライアルはありますか?
はい、GroupDocs.Annotation の無料トライアルにアクセスして、購入する前にその機能を調べることができます。[ここ](https://releases.groupdocs.com/)..
### GroupDocs.Annotation のサポートはどこで見つけられますか?
 GroupDocs.Annotation のサポートと支援については、GroupDocs にアクセスしてください。[フォーラム](https://forum.groupdocs.com/c/annotation/10)注釈関連の質問とディスカッション専用です。
### GroupDocs.Annotation の一時ライセンスを取得するにはどうすればよいですか?
 GroupDocs.Annotation の一時ライセンスは、GroupDocs から取得できます。[Webサイト](https://purchase.groupdocs.com/temporary-license/)、製品を完全に評価できるようになります。