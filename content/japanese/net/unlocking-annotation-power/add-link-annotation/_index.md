---
"description": "Groupdocs.Annotation for .NET を使用してドキュメントにリンク注釈を追加する方法を学びましょう。コラボレーションとインタラクティブ性を簡単に強化できます。"
"linktitle": "ドキュメントにリンク注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントにリンク注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-link-annotation/"
"weight": 16
---

# ドキュメントにリンク注釈を追加する

## 導入
Groupdocs.Annotation for .NETは、開発者が包括的な注釈機能を.NETアプリケーションに容易に統合できるようにする強力なライブラリです。主な機能の一つは、ドキュメントにリンク注釈を追加することで、共同作業とインタラクティブ性を向上させることです。
## 前提条件
リンク注釈を追加するプロセスに進む前に、次の前提条件が満たされていることを確認してください。
- C# プログラミング言語の基本的な理解。
- Groupdocs.Annotation for .NET ライブラリをインストールしました。
- 注釈を付けるドキュメントにアクセスします。

## 名前空間のインポート
まず、Groupdocs.Annotation for .NETの機能を利用するために必要な名前空間をインポートする必要があります。これにより、アプリケーションはドキュメントへの注釈付けに必要なクラスとメソッドにアクセスできるようになります。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ステップ1: 出力パスを設定する
注釈付きドキュメントを保存するパスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ2: アノテーターを初期化する
インスタンスを作成する `Annotator` 注釈を付けるドキュメントのパスを指定してクラスを作成します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注釈コードはここに記入します
}
```
## ステップ3: リンク注釈を作成する
定義する `LinkAnnotation` オブジェクトを作成し、メッセージ、不透明度、ページ番号、背景色、ポイント、返信、URL などのプロパティを指定します。
```csharp
LinkAnnotation link = new LinkAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is link annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
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
    Url = "https://www.google.com
};
```
## ステップ4: 注釈を追加する
作成したリンク注釈をドキュメントに追加するには、 `Add` アノテーター インスタンスのメソッド。
```csharp
annotator.Add(link);
```
## ステップ5: ドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
```
## ステップ6: 成功メッセージを表示する
注釈付きドキュメントが正常に保存されたことをユーザーに通知します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
結論として、上記の手順に従うことで、Groupdocs.Annotation for .NET を使用してドキュメントにリンク注釈をシームレスに追加できます。これにより、ドキュメントの共同作業が強化され、ユーザーにインタラクティブな機能が提供されます。
## よくある質問
### Groupdocs.Annotation for .NET はすべての種類のドキュメントと互換性がありますか?
Groupdocs.Annotation for .NET は、PDF、Word、Excel など、幅広いドキュメント形式をサポートしています。
### 注釈の外観をカスタマイズできますか?
はい、注釈の色、不透明度、サイズなどのさまざまなプロパティを要件に合わせてカスタマイズできます。
### Groupdocs.Annotation for .NET はリアルタイムのコラボレーション機能を提供していますか?
はい、Groupdocs.Annotation for .NET は、複数のユーザーが同時にドキュメントに注釈を付けることができるリアルタイムのコラボレーション機能を提供します。
### Groupdocs 製品にはテクニカル サポートが提供されますか?
はい、Groupdocs製品のテクニカルサポートはフォーラムとサポートを通じてご利用いただけます。 [ここ](https://forum。groupdocs.com/c/annotation/10).
### 購入前に Groupdocs.Annotation for .NET を試すことはできますか?
はい、Groupdocs.Annotation for .NET の無料トライアルを利用して、購入前に機能を試すことができます。[ここ](https://purchase。groupdocs.com/temporary-license/).