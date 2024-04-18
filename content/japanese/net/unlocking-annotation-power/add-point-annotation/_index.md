---
title: ドキュメントにポイント注釈を追加
linktitle: ドキュメントにポイント注釈を追加
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用して PDF にポイント アノテーションを追加する方法を学びます。シームレスな統合のためのステップバイステップのガイド。
type: docs
weight: 17
url: /ja/net/unlocking-annotation-power/add-point-annotation/
---
## 導入
GroupDocs.Annotation for .NET は、開発者がプログラムによってドキュメントにさまざまな種類の注釈を追加できる強力なツールです。このチュートリアルでは、C# を使用してドキュメントにポイント注釈を追加することに焦点を当てます。
## 前提条件
始める前に、以下のものがあることを確認してください。
1. C# プログラミング言語の基本的な理解。
2. Visual Studio がシステムにインストールされている。
3.  .NET ライブラリの GroupDocs.Annotation がインストールされています。からダウンロードできます[ここ](https://releases.groupdocs.com/annotation/net/).

## 必要な名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートする必要があります。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ステップ 1: 出力パスを定義する
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
このステップでは、注釈付きドキュメントが保存される出力パスを定義します。
## ステップ 2: アノテーターを初期化する
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
ここでは、`Annotator`オブジェクトと入力ドキュメント (「input.pdf」)。
## ステップ 3: ポイントの注釈を作成する
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
このステップでは、`PointAnnotation`オブジェクトを作成し、位置、メッセージ、ページ番号、返信などのプロパティを指定します。
## ステップ 4: 注釈を追加する
```csharp
annotator.Add(point);
```
ここでは、作成したポイントアノテーションをドキュメントに追加します。
## ステップ 5: ドキュメントを保存する
```csharp
annotator.Save(outputPath);
```
最後に、注釈付きドキュメントを指定された出力パスに保存します。

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントにポイント アノテーションを追加する方法を学習しました。この強力なライブラリを使用すると、注釈機能を組み込んで文書管理アプリケーションを強化できます。
## よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
はい、GroupDocs.Annotation for .NET は、PDF、Microsoft Word、Excel、PowerPoint などを含む幅広いドキュメント形式をサポートしています。
### 注釈の外観をカスタマイズできますか?
絶対に！ GroupDocs.Annotation for .NET は、アプリケーションのニーズに合わせて注釈の外観をカスタマイズするための広範なオプションを提供します。
### GroupDocs.Annotation for .NET に利用できる無料試用版はありますか?
はい、以下から無料トライアルを利用できます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET に関連する問題やクエリのサポートを受けるにはどうすればよいですか?
 GroupDocs.Annotation フォーラムからサポートを受けることができます。[ここ](https://forum.groupdocs.com/c/annotation/10).
### テスト目的で一時ライセンスを取得できますか?
はい、次から一時ライセンスを取得できます。[ここ](https://purchase.groupdocs.com/temporary-license/).