---
"description": "GroupDocs.Annotation for .NET を使用して、ドキュメントにテキストの下線注釈を追加する方法を学びます。コラボレーションとコミュニケーションを簡単に強化できます。"
"linktitle": "ドキュメントにテキスト下線注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントにテキスト下線注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-text-underline-annotation/"
"weight": 27
---

# ドキュメントにテキスト下線注釈を追加する

## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用して、ドキュメントにテキスト下線注釈を追加する手順を説明します。テキスト下線注釈は、重要な箇所や要点など、ドキュメントの特定の部分を強調するのに役立ちます。
## 前提条件
始める前に、次の前提条件がインストールされていることを確認してください。
1. GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NETをダウンロードしてインストールします。 [ここ](https://releases。groupdocs.com/annotation/net/).
2. .NET Framework: システムに .NET Framework がインストールされていることを確認してください。

## 名前空間のインポート
まず、必要な名前空間をプロジェクトにインポートしましょう。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

ここで、例を複数のステップに分解してみましょう。
## ステップ1: 出力パスを定義する
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
このステップでは、注釈が付けられたドキュメントが保存される出力パスを定義します。
## ステップ2: アノテーターを初期化する
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
ここでは、 `Annotator` 入力ドキュメントのパスを指定してクラスを作成します。
## ステップ3: 下線注釈を作成する
```csharp
UnderlineAnnotation underline = new UnderlineAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is underline annotation",
    Opacity = 0.7,
    PageNumber = 0,
    BackgroundColor = 16761035,
    UnderlineColor = 1422623, // 作品はWordとPDF文書のみサポートされます
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
    }
};
```
このステップでは、 `UnderlineAnnotation` フォント色、メッセージ、不透明度、ページ番号、背景色、下線の色、ポイント、返信などのさまざまなプロパティを持つオブジェクト。
## ステップ4: ドキュメントに注釈を追加する
```csharp
annotator.Add(underline);
```
ここでは、ドキュメントに下線注釈を追加します。
## ステップ5: 注釈付きドキュメントを保存する
```csharp
annotator.Save(outputPath);
```
最後に、注釈付きのドキュメントを指定された出力パスに保存します。

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用して、ドキュメントにテキストの下線注釈を追加する方法を学習しました。この強力なライブラリは、ドキュメントの共同作業とコミュニケーションを強化するためのさまざまな注釈オプションを提供します。
## よくある質問
### 下線注釈の外観をカスタマイズできますか?
はい、色、不透明度、位置などのプロパティを要件に応じてカスタマイズできます。
### GroupDocs.Annotation はさまざまなドキュメント形式と互換性がありますか?
はい、GroupDocs.Annotation は、Word や PDF を含む幅広いドキュメント形式をサポートしています。
### 1 つのドキュメントに複数の注釈を追加できますか?
はい、GroupDocs.Annotation を使用すると、異なるタイプの複数の注釈をドキュメントに追加できます。
### GroupDocs.Annotation の無料トライアルはありますか?
はい、無料トライアル版は以下からアクセスできます。 [ここ](https://releases。groupdocs.com/).
### GroupDocs.Annotation のサポートはどこで受けられますか?
GroupDocs.Annotationコミュニティフォーラムからサポートを受けることができます [ここ](https://forum。groupdocs.com/c/annotation/10).