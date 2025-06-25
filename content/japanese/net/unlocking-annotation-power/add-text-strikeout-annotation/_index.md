---
"description": "GroupDocs.Annotation for .NET を使用して、ドキュメントにテキスト取り消し線注釈を追加する方法を学びます。共同作業とドキュメントレビューのプロセスを効率的に強化します。"
"linktitle": "文書にテキスト取り消し線注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "文書にテキスト取り消し線注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-text-strikeout-annotation/"
"weight": 26
---

# 文書にテキスト取り消し線注釈を追加する

## 導入
このチュートリアルでは、GroupDocs.Annotation for .NET を使用して、ドキュメントにテキスト取り消し線注釈を追加する方法を説明します。このライブラリは、さまざまな種類のドキュメントに注釈を付け、共同作業やドキュメントレビューのプロセスを強化するための強力なツールを提供します。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1. GroupDocs.Annotation for .NET: ライブラリをインストールします。ダウンロードはこちらから。 [ここ](https://releases。groupdocs.com/annotation/net/).
2. 開発環境: .NET 開発に適した開発環境をセットアップします。
3. ドキュメント: PDF ファイルなど、注釈を付けるドキュメントを用意します。

## 名前空間のインポート
まず、GroupDocs.Annotation の機能にアクセスするために必要な名前空間をインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```

ここで、テキスト取り消し線注釈を追加するプロセスを複数のステップに分解してみましょう。
## ステップ1: 出力パスを定義する
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
ここで、注釈が付けられたドキュメントが保存される出力パスを定義します。
## ステップ2: アノテーターを初期化する
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
入力ドキュメント (この場合は PDF ファイル) へのパスを指定して、Annotator オブジェクトを初期化します。
## ステップ3: 取り消し線注釈を作成する
```csharp
StrikeoutAnnotation strikeout = new StrikeoutAnnotation
{
    CreatedOn = DateTime.Now,
    FontColor = 65535,
    Message = "This is strikeout annotation",
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
    }
};
```
メッセージ、不透明度、ページ番号、背景色、ポイント (座標)、返信などの必要なプロパティを持つ StrikeoutAnnotation オブジェクトを作成します。
## ステップ4: 注釈を追加する
```csharp
annotator.Add(strikeout);
```
作成した取り消し線注釈をドキュメントに追加します。
## ステップ5: ドキュメントを保存する
```csharp
annotator.Save(outputPath);
```
注釈付きドキュメントを指定された出力パスに保存します。

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用して、ドキュメントに取り消し線付きのテキスト注釈を追加する方法を学習しました。この強力なライブラリは、ドキュメントへの注釈の効率的な追加を可能にし、共同作業とドキュメントレビューのプロセスを強化します。
## よくある質問
### GroupDocs.Annotation はさまざまなドキュメント形式と互換性がありますか?
はい、GroupDocs.Annotation は、PDF、Word、Excel、PowerPoint など、幅広いドキュメント形式をサポートしています。
### 注釈の外観をカスタマイズできますか?
もちろんです。色、不透明度、フォント サイズなどの注釈プロパティを、要件に応じてカスタマイズできます。
### GroupDocs.Annotation はコラボレーション機能を提供しますか?
はい、GroupDocs.Annotation では、ユーザーがドキュメントにコメント、返信、注釈を追加できるようにすることで共同作業が容易になります。
### 無料トライアルはありますか？
はい、無料トライアルをご利用いただけます [ここ](https://releases。groupdocs.com/).
### GroupDocs.Annotation のサポートはどこで受けられますか?
サポートを受けるには [GroupDocs.Annotation フォーラム](https://forum。groupdocs.com/c/annotation/10).