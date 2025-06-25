---
"description": "GroupDocs.Annotation for .NET を使用して、プログラムで PDF ドキュメントに注釈を付ける方法を学びます。コード例を使ったステップバイステップのチュートリアルです。"
"linktitle": "URLからドキュメントを読み込む"
"second_title": "GroupDocs.Annotation .NET API"
"title": "URLからドキュメントを読み込む"
"url": "/ja/net/document-loading-essentials/load-document-from-url/"
"weight": 15
---

# URLからドキュメントを読み込む

## 導入
GroupDocs.Annotation for .NETは、開発者が.NETアプリケーションに簡単に注釈機能を追加できる機能豊富なライブラリです。GroupDocs.Annotationを使用すると、PDFドキュメントにプログラムで注釈を付けることができ、ユーザーはテキストのハイライト、コメントの追加、図形の描画などを行うことができます。このチュートリアルでは、GroupDocs.Annotation for .NETを使用してURLからドキュメントを読み込み、注釈を追加し、注釈付きドキュメントを保存する手順を詳しく説明します。
## 前提条件
始める前に、次の前提条件が満たされていることを確認してください。
1. Visual Studio: 開発マシンに Visual Studio がインストールされていることを確認してください。
2. GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NETを以下のサイトからダウンロードしてインストールします。 [Webサイト](https://releases。groupdocs.com/annotation/net/).
3. C# の基礎知識: C# プログラミング言語について理解を深めます。
4. インターネット接続: 外部リソースにアクセスし、サンプル ファイルをダウンロードするには、インターネット接続が必要です。

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間をインポートしましょう。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## ステップ1: URLからドキュメントを読み込む
URL から PDF ドキュメントに注釈を付けるには、次の手順に従います。
### ステップ1.1: 出力パスを定義する
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### ステップ1.2: URLを指定する
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### ステップ1.3: ドキュメントの読み込み
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    // ここに注釈を追加
    annotator.Save(outputPath);
}
```
## ステップ2: 注釈を追加する
それでは、読み込んだドキュメントに注釈を追加してみましょう。この例では、エリア注釈を追加します。
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## ステップ3: 注釈付きドキュメントを保存する
最後に、注釈を付けたドキュメントを指定された出力パスに保存します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用してPDFドキュメントに注釈を付ける方法を学習しました。ステップバイステップガイドに従うことで、注釈機能を.NETアプリケーションにシームレスに統合し、ユーザーがPDFファイルで効果的に共同作業できるようになります。

## よくある質問
### GroupDocs.Annotation for .NET はすべての .NET フレームワークと互換性がありますか?
はい、GroupDocs.Annotation for .NET は、.NET Framework、.NET Core、.NET Standard などのさまざまな .NET フレームワークと互換性があります。
### 注釈の外観をカスタマイズできますか?
もちろんです! GroupDocs.Annotation for .NET には広範なカスタマイズ オプションが用意されており、要件に応じて注釈の外観や動作を変更できます。
### GroupDocs.Annotation for .NET の無料試用版はありますか?
はい、GroupDocs.Annotation for .NETの無料トライアルをこちらからダウンロードできます。 [Webサイト](https://releases。groupdocs.com/).
### GroupDocs.Annotation for .NET のテクニカル サポートを受けるにはどうすればよいですか?
GroupDocs.Annotation for .NET に関して技術的な問題や質問がある場合は、 [サポートフォーラム](https://forum。groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET のライセンスはどこで購入できますか?
GroupDocs.Annotation for .NETのライセンスは、 [購入ページ](https://purchase。groupdocs.com/buy).