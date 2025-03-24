---
title: テキスト強調表示注釈をドキュメントに追加
linktitle: テキスト強調表示注釈をドキュメントに追加
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用してドキュメントにテキスト ハイライト注釈を追加する方法を学びます。この包括的な機能により、コラボレーションと生産性が向上します。
weight: 22
url: /ja/net/unlocking-annotation-power/add-text-highlight-annotation/
---

# テキスト強調表示注釈をドキュメントに追加

## 導入
ドキュメント管理とコラボレーションの領域では、GroupDocs.Annotation for .NET が堅牢なソリューションとして登場し、開発者がテキスト ハイライトの注釈をアプリケーションにシームレスに統合できるようになります。このチュートリアルは、GroupDocs.Annotation for .NET を使用してドキュメントにテキスト ハイライト注釈を追加するための包括的なガイドとして機能します。ステップバイステップの指示と詳細な説明を通じて、この強力なライブラリの機能を活用する能力を習得できます。
## 前提条件
テキスト ハイライト注釈の実装を詳しく検討する前に、次の前提条件が満たされていることを確認してください。
1. 環境セットアップ: .NET 開発用に適切な開発環境を構成します。
2.  GroupDocs.Annotation for .NET のインストール: 提供されているから GroupDocs.Annotation for .NET をダウンロードしてインストールします。[ダウンロードリンク](https://releases.groupdocs.com/annotation/net/).
3. C# に関する知識: C# プログラミング言語の基本的な理解。
4. 注釈を付けるドキュメント: 注釈を付ける予定のドキュメント (PDF など) を準備します。

## 名前空間のインポート
まず、GroupDocs.Annotation for .NET の機能を利用するために必要な名前空間を C# コードにインポートします。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
#ここで、テキスト ハイライト注釈を追加するプロセスを複数のステップに分けてみましょう。
## ステップ 1: 出力パスを定義する
注釈付きドキュメントが保存される出力パスを指定します。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ 2: アノテーターを初期化する
のインスタンスを作成します。`Annotator`クラスにドキュメントのファイル名をパラメータとして渡します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## ステップ 3: ハイライト注釈を作成する
インスタンス化する`HighlightAnnotation`オブジェクトを作成し、そのプロパティを設定します。
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
## ステップ 4: 注釈を追加する
作成したハイライト注釈をドキュメントに追加します。
```csharp
annotator.Add(highlight);
```
## ステップ 5: 注釈付きドキュメントを保存する
注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Save(outputPath);
```

## 結論
結論として、GroupDocs.Annotation for .NET は、テキスト ハイライトの注釈をドキュメントに組み込むための合理的なアプローチを提供します。このチュートリアルで概説されている手順に従うことで、開発者はアプリケーション内でのドキュメントのコラボレーションと生産性をシームレスに強化できます。
## よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Annotation for .NET は、PDF、Word、Excel などを含むさまざまなドキュメント形式をサポートしています。完全なリストについてはドキュメントを参照してください。
### 特定の要件に応じて注釈をカスタマイズできますか?
はい、開発者は注釈のプロパティと外観を完全に制御できるため、さまざまなニーズに合わせてカスタマイズできます。
### GroupDocs.Annotation for .NET に利用できる無料試用版はありますか?
はい、提供されている無料トライアル版にアクセスして、GroupDocs.Annotation for .NET の機能を探索できます。[リンク](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET に関連する問題やクエリのサポートを受けるにはどうすればよいですか?
サポートと支援が必要な場合は、GroupDocs.Annotation フォーラムにアクセスしてください。[ここ](https://forum.groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET ではどのようなライセンス オプションが利用できますか?
 GroupDocs.Annotation for .NET は、テスト目的の一時ライセンスや運用環境用の商用ライセンスなど、さまざまなライセンス オプションを提供します。購入ページにアクセスする[ここ](https://purchase.groupdocs.com/buy)詳細については。