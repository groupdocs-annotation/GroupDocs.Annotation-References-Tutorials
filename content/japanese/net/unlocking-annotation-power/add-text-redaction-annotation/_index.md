---
"description": "GroupDocs.Annotation for .NET を使用して、PDF ドキュメントにテキスト編集注釈を追加する方法を学びます。機密情報を簡単に保護します。"
"linktitle": "ドキュメントにテキスト編集注釈を追加する"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ドキュメントにテキスト編集注釈を追加する"
"url": "/ja/net/unlocking-annotation-power/add-text-redaction-annotation/"
"weight": 23
---

# ドキュメントにテキスト編集注釈を追加する

## 導入
ドキュメントにテキスト編集注釈を追加することは、機密情報を安全に管理する上で非常に重要なステップとなります。GroupDocs.Annotation for .NETは、これをシームレスに実現するための堅牢なソリューションを提供します。このチュートリアルでは、ドキュメントにテキスト編集注釈を追加するプロセスを段階的に説明します。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1. GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NETライブラリがインストールされていることを確認してください。ダウンロードは以下から行えます。 [Webサイト](https://releases。groupdocs.com/annotation/net/).
2. 開発環境: Visual Studio などの .NET 互換 IDE を使用して開発環境をセットアップします。

## 名前空間のインポート
まず、プロジェクトに必要な名前空間をインポートしましょう。
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## ステップ1: 出力パスを定義する
注釈付きドキュメントを保存する出力パスを定義します。アクセス可能かつ書き込み可能であることを確認してください。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ2: アノテーターを初期化する
入力文書のパスでアノテーターを初期化します。 `"input.pdf"` ドキュメントへのパスを入力します。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // 注釈コードはここに記入します
}
```
## ステップ3: テキスト編集注釈を作成する
作成する `TextRedactionAnnotation` 必要なプロパティを持つオブジェクト、例えば `PageNumber`、 `FontColor`、 そして `Points`要件に応じて注釈をカスタマイズします。
```csharp
TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
{
    CreatedOn = DateTime.Now,
    Message = "This is text redaction annotation",
    PageNumber = 0,
    FontColor = 16761035,
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
## ステップ4: 注釈を追加して保存する
作成した注釈をアノテーターを使用してドキュメントに追加し、注釈が付けられたドキュメントを指定された出力パスに保存します。
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## ステップ5: 出力を確認する
最後に、ドキュメントが指定された出力パスに正常に保存されたことを確認します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントにテキスト編集注釈を追加する手順を詳しく説明しました。これらの手順により、ドキュメント内の機密情報を安全に管理できるようになります。
## よくある質問
### テキスト編集注釈の外観をカスタマイズできますか?
はい、フォントの色、塗りつぶしの色、不透明度など、さまざまなプロパティを要件に合わせてカスタマイズできます。
### 購入前に試用版はありますか？
はい、無料トライアル版は [Webサイト](https://releases。groupdocs.com/).
### 問題が発生した場合、どうすればサポートを受けることができますか?
GroupDocs.Annotationコミュニティフォーラムからサポートを受けることができます [ここ](https://forum。groupdocs.com/c/annotation/10).
### テスト目的で一時ライセンスは必要ですか?
はい、臨時免許証は [購入ページ](https://purchase.groupdocs.com/temporary-license/) テスト用。
### 1 つのドキュメントに複数の注釈を追加できますか?
はい、GroupDocs.Annotation を使用すると、さまざまな種類の注釈と複数のインスタンスを 1 つのドキュメントに追加できます。