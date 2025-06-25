---
"description": "GroupDocs.Annotation for .NET を使用して、ドキュメントにテキストハイライト注釈を追加する方法を学びましょう。この包括的なツールで、コラボレーションと生産性を向上させましょう。"
"linktitle": "ドキュメントにテキストハイライト注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントにテキストハイライト注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-text-highlight-annotation/"
"weight": 22
---

# ドキュメントにテキストハイライト注釈を追加する

## 導入
ドキュメント管理とコラボレーションの分野において、GroupDocs.Annotation for .NETは堅牢なソリューションとして登場し、開発者がアプリケーションにテキストハイライト注釈をシームレスに統合することを可能にします。このチュートリアルは、GroupDocs.Annotation for .NETを使用してドキュメントにテキストハイライト注釈を追加するための包括的なガイドです。ステップバイステップの手順と詳細な説明を通して、この強力なライブラリの機能を最大限に活用できるようになります。
## 前提条件
テキストハイライト注釈の実装に進む前に、次の前提条件が満たされていることを確認してください。
1. 環境設定: .NET 開発に適した開発環境を構成します。
2. GroupDocs.Annotation for .NETのインストール: 提供されているサイトからGroupDocs.Annotation for .NETをダウンロードしてインストールします。 [ダウンロードリンク](https://releases。groupdocs.com/annotation/net/).
3. C# の知識: C# プログラミング言語の基本的な理解。
4. 注釈を付けるドキュメント: 注釈を付けるドキュメント (PDF など) を準備します。

## 名前空間のインポート
まず、GroupDocs.Annotation for .NET の機能を利用するために、C# コードに必要な名前空間をインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#では、テキストハイライト注釈を追加するプロセスを複数のステップに分解してみましょう。
## ステップ1: 出力パスを定義する
注釈付きドキュメントを保存する出力パスを指定します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ2: アノテーターを初期化する
インスタンスを作成する `Annotator` クラスにドキュメントファイル名をパラメータとして渡します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## ステップ3: ハイライト注釈を作成する
インスタンス化する `HighlightAnnotation` オブジェクトを作成し、そのプロパティを構成します。
```csharp
HighlightAnnotation highlight = new HighlightAnnotation
{
    BackgroundColor = 65535,
    CreatedOn = DateTime.Now,
    FontColor = 0,
    Message = "This is highlight annotation",
    Opacity = 0.5,
    PageNumber = 0,
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
## ステップ4: 注釈を追加する
作成したハイライト注釈をドキュメントに追加します。
```csharp
annotator.Add(highlight);
```
## ステップ5: 注釈付きドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
```

## 結論
結論として、GroupDocs.Annotation for .NETは、テキストハイライト注釈をドキュメントに組み込むための効率的なアプローチを提供します。このチュートリアルで概説した手順に従うことで、開発者はアプリケーション内でドキュメントの共同作業と生産性をシームレスに向上させることができます。
## よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Annotation for .NETは、PDF、Word、Excelなど、様々なドキュメント形式をサポートしています。完全なリストについては、ドキュメントをご覧ください。
### 特定の要件に応じて注釈をカスタマイズできますか?
はい、開発者は注釈のプロパティと外観を完全に制御できるため、さまざまなニーズに合わせてカスタマイズできます。
### GroupDocs.Annotation for .NET の無料試用版はありますか?
はい、提供されている無料トライアルにアクセスして、GroupDocs.Annotation for .NETの機能を試すことができます。 [リンク](https://releases。groupdocs.com/).
### GroupDocs.Annotation for .NET に関連する問題や質問についてサポートを受けるにはどうすればよいですか?
サポートと援助については、GroupDocs.Annotation フォーラムをご覧ください。 [ここ](https://forum。groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET にはどのようなライセンス オプションがありますか?
GroupDocs.Annotation for .NETは、テスト目的の一時ライセンスから実稼働環境向けの商用ライセンスまで、様々なライセンスオプションをご用意しています。購入ページをご覧ください。 [ここ](https://purchase.groupdocs.com/buy) 詳細についてはこちらをご覧ください。