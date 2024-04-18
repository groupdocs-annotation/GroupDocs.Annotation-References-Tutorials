---
title: ドキュメントにリンク注釈を追加する
linktitle: ドキュメントにリンク注釈を追加する
second_title: GroupDocs.Annotation .NET API
description: Groupdocs.Annotation for .NET を使用してドキュメントにリンク注釈を追加する方法を学びます。コラボレーションと対話性を簡単に強化します。
type: docs
weight: 16
url: /ja/net/unlocking-annotation-power/add-link-annotation/
---
## 導入
Groupdocs.Annotation for .NET は、開発者が包括的な注釈機能を .NET アプリケーションに簡単に統合できるようにする強力なライブラリです。これが提供する主な機能の 1 つは、ドキュメントにリンク注釈を追加して、コラボレーションと対話性を強化する機能です。
## 前提条件
リンク注釈を追加するプロセスに入る前に、次の前提条件を満たしていることを確認してください。
- C# プログラミング言語の基本的な理解。
- .NET ライブラリ用の Groupdocs.Annotation がインストールされました。
- 注釈を付けたいドキュメントにアクセスします。

## 名前空間のインポート
まず、Groupdocs.Annotation for .NET 機能を利用するために必要な名前空間をインポートする必要があります。これにより、アプリケーションはドキュメントに注釈を付けるために必要なクラスとメソッドにアクセスできるようになります。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ステップ 1: 出力パスを設定する
注釈付きドキュメントを保存するパスを定義します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ 2: アノテーターを初期化する
のインスタンスを作成します。`Annotator`注釈を付けたいドキュメントのパスを指定してクラスを作成します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注釈コードがここに挿入されます
}
```
## ステップ 3: リンク注釈を作成する
を定義します`LinkAnnotation`オブジェクトを作成し、メッセージ、不透明度、ページ番号、背景色、ポイント、返信、URL などのプロパティを指定します。
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
    Url = "https://www.google.com」
};
```
## ステップ 4: 注釈を追加する
作成したリンク注釈をドキュメントに追加します。`Add`アノテーター インスタンスのメソッド。
```csharp
annotator.Add(link);
```
## ステップ 5: ドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
```
## ステップ 6: 成功メッセージを表示する
注釈付きドキュメントが正常に保存されたことをユーザーに通知します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
結論として、上記の手順に従うことで、Groupdocs.Annotation for .NET を使用してドキュメントにリンク アノテーションをシームレスに追加できます。これにより、ドキュメントのコラボレーションが強化され、ユーザーにインタラクティブな機能が提供されます。
## よくある質問
### Groupdocs.Annotation for .NET はあらゆる種類のドキュメントと互換性がありますか?
Groupdocs.Annotation for .NET は、PDF、Word、Excel などを含む幅広いドキュメント形式をサポートしています。
### 注釈の外観をカスタマイズできますか?
はい、要件に合わせて色、不透明度、サイズなどの注釈のさまざまなプロパティをカスタマイズできます。
### Groupdocs.Annotation for .NET はリアルタイム コラボレーション機能を提供しますか?
はい。Groupdocs.Annotation for .NET は、複数のユーザーが同時にドキュメントに注釈を付けることを可能にするリアルタイム コラボレーション機能を提供します。
### Groupdocs 製品のテクニカル サポートは利用できますか?
はい、Groupdocs 製品のテクニカル サポートはフォーラムとサポートを通じて利用できます。[ここ](https://forum.groupdocs.com/c/annotation/10).
### 購入する前に Groupdocs.Annotation for .NET を試すことはできますか?
はい、Groupdocs.Annotation for .NET の無料トライアルを利用して、購入前にその機能を調べることができます。[ここ](https://purchase.groupdocs.com/temporary-license/).