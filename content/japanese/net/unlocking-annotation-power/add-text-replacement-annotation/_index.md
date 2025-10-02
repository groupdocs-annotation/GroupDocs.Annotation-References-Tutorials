---
"description": "GroupDocs.Annotation for .NET を使用して、.NET ドキュメントにテキスト置換注釈を簡単に追加する方法を学びましょう。ドキュメント操作機能を強化します。"
"linktitle": "ドキュメントにテキスト置換注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントにテキスト置換注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-text-replacement-annotation/"
type: docs
"weight": 24
---

# ドキュメントにテキスト置換注釈を追加する

## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用して、ドキュメントにテキスト置換注釈を追加する手順を説明します。この強力なライブラリを使用すると、開発者はさまざまな種類のドキュメントをプログラムで操作および注釈付けできます。このチュートリアルを完了すると、テキスト置換注釈を .NET アプリケーションにシームレスに統合するための知識が身に付きます。
## 前提条件
始める前に、次の前提条件がインストールされていることを確認してください。
### 1. .NET Frameworkがインストールされている
開発マシンに.NET Frameworkがインストールされていることを確認してください。Microsoftのウェブサイトからダウンロードできます。
### 2. .NET ライブラリの GroupDocs.Annotation
GroupDocs.Annotation for .NETライブラリを以下のサイトからダウンロードしてインストールします。 [Webサイト](https://releases.groupdocs.com/annotation/net/)このライブラリは、さまざまなドキュメント形式の注釈を操作するために必要なツールと機能を提供します。
### 3. 開発環境のセットアップ
.NET アプリケーションを作成して実行するには、Visual Studio などの好みの開発環境をセットアップします。

## 名前空間のインポート
コーディング部分に進む前に、GroupDocs.Annotation for .NET を操作するために必要な名前空間をインポートしましょう。
```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
using Point = GroupDocs.Annotation.Models.Point;
```
## ステップ1: 出力パスを定義する
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ここで、注釈が付けられたドキュメントが保存される出力パスを定義します。
## ステップ2: アノテーターを初期化する
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注釈コードはここに配置されます
}
```
リソースが適切に破棄されるように、using ブロック内で入力ドキュメント (「input.pdf」) を指定して Annotator オブジェクトを初期化します。
## ステップ3: 置換注釈を作成する
```csharp
ReplacementAnnotation replacement = new ReplacementAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = Color.Blue.ToArgb(),
    Message = "This is replacement annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = Color.Red.ToArgb(),
    Points = new List<Point>
    {
        new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = "First comment",
            RepliedOn = DateTime.Now
        },
        new Reply
        {
            Comment = "Second comment",
            RepliedOn = DateTime.Now
        }
    },
    TextToReplace = "replaced text"
};
```
ここでは、作成日、フォント色、メッセージ、不透明度、ページ番号、背景色、ポイント (座標)、返信 (コメント)、置換するテキストなどのさまざまなプロパティを持つ ReplacementAnnotation オブジェクトを作成します。
## ステップ4: 注釈を追加する
```csharp
annotator.Add(replacement);
```
作成した置換アノテーションをアノテーターに追加します。
## ステップ5: ドキュメントを保存する
```csharp
annotator.Save(outputPath);
```
最後に、注釈付きのドキュメントを指定された出力パスに保存します。
## ステップ6: 成功メッセージを表示する
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
ドキュメントが正常に保存されたことを示す成功メッセージが表示されます。

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントにテキスト置換注釈を追加する手順を説明しました。ステップバイステップガイドに従い、前提条件を理解することで、この機能を.NETアプリケーションに簡単に統合できます。
## よくある質問
### GroupDocs.Annotation for .NET を使用して、異なる形式のドキュメントに注釈を付けることはできますか?
はい、GroupDocs.Annotation for .NET は、PDF、DOCX、PPTX、XLSX などのさまざまなドキュメント形式への注釈付けをサポートしています。
### GroupDocs.Annotation for .NET はデスクトップ アプリケーションと Web アプリケーションの両方に適していますか?
はい、GroupDocs.Annotation for .NET はデスクトップ アプリケーションと Web アプリケーションの両方で使用できるため、開発者に柔軟性を提供します。
### GroupDocs.Annotation for .NET を使用して追加された注釈の外観をカスタマイズできますか?
はい、色、不透明度、フォントなどのプロパティを変更することで、注釈の外観をカスタマイズできます。
### GroupDocs.Annotation for .NET は共同注釈機能をサポートしていますか?
はい、GroupDocs.Annotation for .NET は共同注釈機能を提供しており、複数のユーザーが同時にドキュメントに注釈を付けることができます。
### GroupDocs.Annotation for .NET の無料試用版はありますか?
はい、GroupDocs.Annotation for .NETの無料トライアルをこちらからご利用いただけます。 [Webサイト](https://releases。groupdocs.com/).