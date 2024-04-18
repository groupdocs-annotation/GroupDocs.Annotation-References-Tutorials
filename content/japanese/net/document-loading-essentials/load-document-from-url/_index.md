---
title: URLからドキュメントをロード
linktitle: URLからドキュメントをロード
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation for .NET を使用してプログラムで PDF ドキュメントに注釈を付ける方法を学びます。コード例を含むステップバイステップのチュートリアル。
type: docs
weight: 15
url: /ja/net/document-loading-essentials/load-document-from-url/
---
## 導入
GroupDocs.Annotation for .NET は、開発者が .NET アプリケーションに注釈機能を簡単に追加できる機能豊富なライブラリです。 GroupDocs.Annotation を使用すると、PDF ドキュメントにプログラムで注釈を付けることができ、ユーザーがテキストを強調表示したり、コメントを追加したり、図形を描画したりできるようになります。このチュートリアルでは、GroupDocs.Annotation for .NET を使用して、URL からドキュメントをロードし、注釈を追加し、注釈付きドキュメントを保存する手順を説明します。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1. Visual Studio: 開発マシンに Visual Studio がインストールされていることを確認してください。
2.  GroupDocs.Annotation for .NET: GroupDocs.Annotation for .NET を次の場所からダウンロードしてインストールします。[Webサイト](https://releases.groupdocs.com/annotation/net/).
3. C# の基本知識: C# プログラミング言語に慣れておきます。
4. インターネット接続: 外部リソースにアクセスし、サンプル ファイルをダウンロードするには、インターネット接続が必要です。

## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートしましょう。
```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using System;
using System.IO;
using System.Net;
```
## ステップ 1: URL からドキュメントをロードする
URL から PDF ドキュメントに注釈を付けるには、次の手順に従います。
### ステップ 1.1: 出力パスを定義する
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
### ステップ 1.2: URL を指定する
```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";
```
### ステップ 1.3: ドキュメントをロードする
```csharp
using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
    //ここに注釈を追加します
    annotator.Save(outputPath);
}
```
## ステップ 2: 注釈を追加する
次に、読み込んだドキュメントに注釈を追加してみましょう。この例では、領域の注釈を追加します。
```csharp
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100),
    BackgroundColor = 65535,
};
annotator.Add(area);
```
## ステップ 3: 注釈付きドキュメントを保存する
最後に、注釈付きドキュメントを指定した出力パスに保存します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
このチュートリアルでは、GroupDocs.Annotation for .NET を使用して PDF ドキュメントに注釈を付ける方法を学習しました。ステップバイステップのガイドに従うことで、注釈機能を .NET アプリケーションにシームレスに統合し、ユーザーが PDF ファイルで効果的に共同作業できるようになります。

## よくある質問
### GroupDocs.Annotation for .NET はすべての .NET フレームワークと互換性がありますか?
はい。GroupDocs.Annotation for .NET は、.NET Framework、.NET Core、.NET Standard などのさまざまな .NET フレームワークと互換性があります。
### 注釈の外観をカスタマイズできますか?
絶対に！ GroupDocs.Annotation for .NET には広範なカスタマイズ オプションが用意されており、要件に応じて注釈の外観と動作を変更できます。
### GroupDocs.Annotation for .NET に利用できる無料試用版はありますか?
はい、GroupDocs.Annotation for .NET の無料試用版を次からダウンロードできます。[Webサイト](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET のテクニカル サポートを受けるにはどうすればよいですか?
技術的な問題が発生した場合、または GroupDocs.Annotation for .NET について質問がある場合は、[サポートフォーラム](https://forum.groupdocs.com/c/annotation/10).
### GroupDocs.Annotation for .NET のライセンスはどこで購入できますか?
 GroupDocs.Annotation for .NET のライセンスは、[購入ページ](https://purchase.groupdocs.com/buy).