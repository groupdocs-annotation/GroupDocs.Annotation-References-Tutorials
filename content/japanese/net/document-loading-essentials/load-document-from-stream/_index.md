---
"description": "GroupDocs.Annotation を使って、.NET ドキュメントに簡単に注釈を付ける方法を学びましょう。コラボレーションと生産性を向上させます。"
"linktitle": "ストリームからドキュメントを読み込む"
"second_title": "GroupDocs.Annotation .NET API"
"title": "ストリームからドキュメントを読み込む"
"url": "/ja/net/document-loading-essentials/load-document-from-stream/"
"weight": 14
---

# ストリームからドキュメントを読み込む

## 導入
GroupDocs.Annotation for .NETは、開発者がドキュメント注釈機能を.NETアプリケーションに簡単に統合できるようにする強力なライブラリです。ドキュメント管理システム、コラボレーションプラットフォーム、eラーニングアプリケーションなど、どのようなシステムを構築する場合でも、GroupDocs.AnnotationはPDF、Word文書、Excelシートなどに注釈を付けるための多用途なツールセットを提供します。
## 前提条件
注釈付けのプロセスに進む前に、次の前提条件が満たされていることを確認してください。
1. GroupDocs.Annotation for .NETのインストール: GroupDocs.Annotation for .NETをダウンロードしてインストールします。 [ここ](https://releases。groupdocs.com/annotation/net/).
2. C# プログラミングの基本的な理解: C# プログラミング言語と .NET フレームワークの知識が必須です。
3. 開発環境のセットアップ: .NET フレームワークをサポートする、希望する開発環境をセットアップします。

## 名前空間のインポート
GroupDocs.Annotation for .NET を使用してドキュメントに注釈を付けるには、必要な名前空間を C# プロジェクトにインポートします。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

ここで、注釈付けプロセスを複数のステップに分解してみましょう。
## ステップ1: ストリームからドキュメントを読み込む
まず、ストリームからドキュメントを読み込む必要があります。その方法は以下の通りです。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator(File.OpenRead("input.pdf")))
{
```
## ステップ2: 注釈を追加する
次に、ドキュメントに注釈を追加します。例として、エリア注釈を作成してみましょう。
```csharp
	AreaAnnotation area = new AreaAnnotation()
	{
		Box = new Rectangle(100, 100, 100, 100),
		BackgroundColor = 65535,
	};
	annotator.Add(area);
```
## ステップ3: 注釈付きのドキュメントを保存する
注釈を追加したら、注釈付きのドキュメントを保存します。
```csharp
	annotator.Save(File.Create(outputPath));
}
```
## ステップ4: 確認メッセージを表示する
最後に、注釈付きドキュメントが正常に保存されたことを確認するメッセージを表示します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
結論として、GroupDocs.Annotation for .NETは、.NETアプリケーションにおけるドキュメントアノテーションのための包括的なソリューションを提供します。このチュートリアルで概説した手順に従うことで、ドキュメントアノテーション機能をプロジェクトにシームレスに統合し、コラボレーションと生産性を向上させることができます。
## よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Annotation は、PDF、Word、Excel、PowerPoint など、幅広いドキュメント形式をサポートしています。
### 特定の要件に応じて注釈をカスタマイズできますか?
はい、GroupDocs.Annotation では、色、形状、プロパティなど、注釈の幅広いカスタマイズ オプションが提供されています。
### GroupDocs.Annotation は共同注釈機能をサポートしていますか?
はい、GroupDocs.Annotation は共同注釈作成を容易にし、複数のユーザーが同時にドキュメントに注釈を付けることを可能にします。
### GroupDocs.Annotation ユーザー向けのテクニカル サポートは提供されますか?
はい、GroupDocsはフォーラムを通じて専用の技術サポートを提供しています。 [ここ](https://forum.groupdocs.com/c/annotation/10) サポートのため。
### 購入前に GroupDocs.Annotation を試すことはできますか?
はい、GroupDocs.Annotationを無料トライアルで試すことができます。 [ここ](https://releases。groupdocs.com/).