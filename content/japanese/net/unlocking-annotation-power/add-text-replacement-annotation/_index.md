---
title: テキスト置換注釈をドキュメントに追加
linktitle: テキスト置換注釈をドキュメントに追加
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用して、.NET ドキュメントにテキスト置換注釈を簡単に追加する方法を学びます。ドキュメントの操作能力を強化します。
weight: 24
url: /ja/net/unlocking-annotation-power/add-text-replacement-annotation/
---
## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントにテキスト置換アノテーションを追加するプロセスを説明します。この強力なライブラリを使用すると、開発者はさまざまな種類のドキュメントをプログラムで操作し、注釈を付けることができます。このチュートリアルを終えると、テキスト置換注釈を .NET アプリケーションにシームレスに統合するための知識が身につくでしょう。
## 前提条件
始める前に、次の前提条件がインストールされていることを確認してください。
### 1..NET Frameworkのインストール
開発マシンに .NET Framework がインストールされていることを確認してください。 Microsoft Web サイトからダウンロードできます。
### 2. .NET ライブラリ用の GroupDocs.Annotation
 GroupDocs.Annotation for .NET ライブラリを次の場所からダウンロードしてインストールします。[Webサイト](https://releases.groupdocs.com/annotation/net/)。このライブラリは、さまざまなドキュメント形式の注釈を操作するために必要なツールと機能を提供します。
### 3. 開発環境のセットアップ
Visual Studio などの好みの開発環境をセットアップして、.NET アプリケーションを作成して実行します。

## 名前空間のインポート
コーディング部分に入る前に、GroupDocs.Annotation for .NET の操作に必要な名前空間をインポートしましょう。
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
## ステップ 1: 出力パスを定義する
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ここでは、注釈付きドキュメントが保存される出力パスを定義します。
## ステップ 2: アノテーターを初期化する
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注釈コードはここに配置されます
}
```
リソースが適切に処理されるように、using ブロック内で入力ドキュメント (「input.pdf」) を指定して Annotator オブジェクトを初期化します。
## ステップ 3: 置換アノテーションの作成
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
ここでは、作成日、フォントの色、メッセージ、不透明度、ページ番号、背景色、ポイント (座標)、返信 (コメント)、置換するテキストなどのさまざまなプロパティを持つ ReplacementAnnotation オブジェクトを作成します。
## ステップ 4: 注釈を追加する
```csharp
annotator.Add(replacement);
```
作成した置換アノテーションをアノテーターに追加します。
## ステップ 5: ドキュメントを保存する
```csharp
annotator.Save(outputPath);
```
最後に、注釈付きドキュメントを指定された出力パスに保存します。
## ステップ 6: 成功メッセージを表示する
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
ドキュメントが正常に保存されたことを示す成功メッセージが表示されます。

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントにテキスト置換注釈を追加するプロセスについて説明しました。ステップバイステップのガイドに従い、前提条件を理解することで、この機能を .NET アプリケーションに簡単に統合できます。
## よくある質問
### GroupDocs.Annotation for .NET を使用して、さまざまな形式のドキュメントに注釈を付けることができますか?
はい、GroupDocs.Annotation for .NET は、PDF、DOCX、PPTX、XLSX などのさまざまなドキュメント形式の注釈付けをサポートしています。
### GroupDocs.Annotation for .NET はデスクトップ アプリケーションと Web アプリケーションの両方に適していますか?
はい、GroupDocs.Annotation for .NET はデスクトップ アプリケーションと Web アプリケーションの両方で使用できるため、開発者に柔軟性を提供します。
### GroupDocs.Annotation for .NET を使用して追加された注釈の外観をカスタマイズできますか?
もちろん、色、不透明度、フォントなどのプロパティを変更することで、注釈の外観をカスタマイズできます。
### GroupDocs.Annotation for .NET は共同注釈機能のサポートを提供しますか?
はい。GroupDocs.Annotation for .NET は共同注釈機能を提供し、複数のユーザーがドキュメントに同時に注釈を付けることができます。
### GroupDocs.Annotation for .NET に利用できる無料試用版はありますか?
はい、GroupDocs.Annotation for .NET の無料トライアルを次のサイトから利用できます。[Webサイト](https://releases.groupdocs.com/).