---
title: テキスト墨消し注釈をドキュメントに追加
linktitle: テキスト墨消し注釈をドキュメントに追加
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用して PDF ドキュメントにテキスト編集注釈を追加する方法を学びます。機密情報を簡単に保護します。
weight: 23
url: /ja/net/unlocking-annotation-power/add-text-redaction-annotation/
---

# テキスト墨消し注釈をドキュメントに追加

## 導入
文書にテキスト編集注釈を追加することは、機密情報を安全に管理するための重要なステップとなる可能性があります。 GroupDocs.Annotation for .NET は、これをシームレスに実現するための堅牢なソリューションを提供します。このチュートリアルでは、文書にテキスト編集注釈を追加するプロセスを段階的に説明します。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1.  GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET ライブラリがインストールされていることを確認してください。からダウンロードできます。[Webサイト](https://releases.groupdocs.com/annotation/net/).
2. 開発環境: Visual Studio などの .NET 互換 IDE を使用して開発環境をセットアップします。

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
## ステップ 1: 出力パスを定義する
注釈付きドキュメントを保存する出力パスを定義します。アクセス可能で書き込み可能であることを確認してください。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## ステップ 2: アノテーターを初期化する
入力ドキュメント パスを使用してアノテーターを初期化します。交換する`"input.pdf"`ドキュメントへのパスを含めます。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    //注釈コードがここに挿入されます
}
```
## ステップ 3: テキスト墨消し注釈を作成する
を作成します`TextRedactionAnnotation`次のような必要なプロパティを持つオブジェクト`PageNumber`, `FontColor`、 そして`Points`。要件に応じて注釈をカスタマイズします。
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
## ステップ 4: 注釈を追加して保存する
アノテーターを使用して作成した注釈をドキュメントに追加し、注釈付きドキュメントを指定された出力パスに保存します。
```csharp
annotator.Add(textRedaction);
annotator.Save(outputPath);
```
## ステップ 5: 出力を確認する
最後に、ドキュメントが指定した出力パスに正常に保存されたことを確認します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してドキュメントにテキスト編集注釈を追加するプロセスを説明しました。これらの手順により、ドキュメント内の機密情報を安全に管理できるようになります。
## よくある質問
### テキスト墨消し注釈の外観をカスタマイズできますか?
はい、要件に合わせてフォントの色、塗りつぶしの色、不透明度などのさまざまなプロパティをカスタマイズできます。
### 購入前に利用できる試用版はありますか?
はい、次のサイトから無料試用版にアクセスできます。[Webサイト](https://releases.groupdocs.com/).
### 問題が発生した場合、どうすればサポートを受けられますか?
 GroupDocs.Annotation コミュニティ フォーラムからサポートを受けることができます。[ここ](https://forum.groupdocs.com/c/annotation/10).
### テスト目的で一時ライセンスが必要ですか?
はい、次のサイトから一時ライセンスを取得できます。[購入ページ](https://purchase.groupdocs.com/temporary-license/)テスト用。
### 1 つのドキュメントに複数の注釈を追加できますか?
確かに、GroupDocs.Annotation を使用すると、さまざまなタイプの注釈と複数のインスタンスを 1 つのドキュメントに追加できます。