---
"description": "GroupDocs.Annotation for .NET を使用して PDF にポイント注釈を追加する方法を学びます。シームレスな統合のためのステップバイステップガイドです。"
"linktitle": "ドキュメントにポイント注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントにポイント注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-point-annotation/"
"weight": 17
---

# ドキュメントにポイント注釈を追加する

## 導入
GroupDocs.Annotation for .NETは、開発者がプログラム的にドキュメントに様々な種類の注釈を追加できる強力なツールです。このチュートリアルでは、C#を使用してドキュメントにポイント注釈を追加する方法に焦点を当てます。
## 前提条件
始める前に、以下のものを用意してください。
1. C# プログラミング言語の基本的な理解。
2. Visual Studio がシステムにインストールされています。
3. GroupDocs.Annotation for .NETライブラリがインストールされています。ダウンロードはこちらから。 [ここ](https://releases。groupdocs.com/annotation/net/).

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
## ステップ1: 出力パスを定義する
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
このステップでは、注釈が付けられたドキュメントが保存される出力パスを定義します。
## ステップ2: アノテーターを初期化する
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
ここで、 `Annotator` 入力ドキュメント ("input.pdf") を含むオブジェクト。
## ステップ3: ポイント注釈を作成する
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
このステップでは、 `PointAnnotation` オブジェクトを作成し、位置、メッセージ、ページ番号、返信などのプロパティを指定します。
## ステップ4: 注釈を追加する
```csharp
annotator.Add(point);
```
ここで、作成したポイント注釈をドキュメントに追加します。
## ステップ5: ドキュメントを保存する
```csharp
annotator.Save(outputPath);
```
最後に、注釈付きのドキュメントを指定された出力パスに保存します。

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントにポイント注釈を追加する方法を学習しました。この強力なライブラリを使用すると、注釈機能を組み込むことで、ドキュメント管理アプリケーションを強化できます。
## よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
はい、GroupDocs.Annotation for .NET は、PDF、Microsoft Word、Excel、PowerPoint など、幅広いドキュメント形式をサポートしています。
### 注釈の外観をカスタマイズできますか?
もちろんです! GroupDocs.Annotation for .NET には、アプリケーションのニーズに合わせて注釈の外観をカスタマイズするための幅広いオプションが用意されています。
### GroupDocs.Annotation for .NET の無料試用版はありますか?
はい、無料トライアルをご利用いただけます [ここ](https://releases。groupdocs.com/).
### GroupDocs.Annotation for .NET に関連する問題や質問についてサポートを受けるにはどうすればよいですか?
GroupDocs.Annotationフォーラムからサポートを受けることができます [ここ](https://forum。groupdocs.com/c/annotation/10).
### テスト目的で一時ライセンスを取得できますか?
はい、臨時免許証は以下から取得できます。 [ここ](https://purchase。groupdocs.com/temporary-license/).