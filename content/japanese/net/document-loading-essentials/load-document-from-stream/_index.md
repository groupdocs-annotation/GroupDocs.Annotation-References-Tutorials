---
title: ストリームからドキュメントをロード
linktitle: ストリームからドキュメントをロード
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation を使用して、.NET のドキュメントに簡単に注釈を付ける方法を学びます。コラボレーションと生産性を強化します。
type: docs
weight: 14
url: /ja/net/document-loading-essentials/load-document-from-stream/
---
## 導入
GroupDocs.Annotation for .NET は、開発者がドキュメントの注釈機能を .NET アプリケーションに簡単に統合できるようにする強力なライブラリです。ドキュメント管理システム、コラボレーション プラットフォーム、または e ラーニング アプリケーションを構築している場合でも、GroupDocs.Annotation は、PDF、Word ドキュメント、Excel シートなどに注釈を付けるための多用途のツール セットを提供します。
## 前提条件
注釈プロセスに入る前に、次の前提条件を満たしていることを確認してください。
1. GroupDocs.Annotation for .NET のインストール: GroupDocs.Annotation for .NET を次からダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/annotation/net/).
2. C# プログラミングの基本的な理解: C# プログラミング言語と .NET Framework に精通していることが不可欠です。
3. 開発環境のセットアップ: .NET Framework をサポートする好みの開発環境をセットアップします。

## 名前空間のインポート
GroupDocs.Annotation for .NET を使用してドキュメントへの注釈付けを開始するには、必要な名前空間を C# プロジェクトにインポートします。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

ここで、アノテーションのプロセスを複数のステップに分けてみましょう。
## ステップ 1: ストリームからドキュメントをロードする
まず、ストリームからドキュメントをロードする必要があります。それを達成する方法は次のとおりです。
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
using (Annotator annotator = new Annotator(File.OpenRead("input.pdf")))
{
```
## ステップ 2: 注釈を追加する
次に、ドキュメントに注釈を追加できます。例としてエリア注釈を作成してみましょう。
```csharp
	AreaAnnotation area = new AreaAnnotation()
	{
		Box = new Rectangle(100, 100, 100, 100),
		BackgroundColor = 65535,
	};
	annotator.Add(area);
```
## ステップ 3: 注釈を付けてドキュメントを保存する
注釈を追加した後、注釈付きドキュメントを保存します。
```csharp
	annotator.Save(File.Create(outputPath));
}
```
## ステップ 4: 確認メッセージを表示する
最後に、注釈付きドキュメントが正常に保存されたことを確認するメッセージを表示します。
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## 結論
結論として、GroupDocs.Annotation for .NET は、.NET アプリケーション内でドキュメントの注釈を付けるための包括的なソリューションを提供します。このチュートリアルで概説されている手順に従うことで、ドキュメントの注釈機能をプロジェクトにシームレスに統合し、コラボレーションと生産性を向上させることができます。
## よくある質問
### GroupDocs.Annotation for .NET はすべてのドキュメント形式と互換性がありますか?
GroupDocs.Annotation は、PDF、Word、Excel、PowerPoint などを含む幅広いドキュメント形式をサポートしています。
### 特定の要件に応じて注釈をカスタマイズできますか?
はい。GroupDocs.Annotation は、色、形状、プロパティなど、注釈の広範なカスタマイズ オプションを提供します。
### GroupDocs.Annotation は共同注釈機能をサポートしていますか?
はい。GroupDocs.Annotation を使用すると、共同での注釈付けが容易になり、複数のユーザーがドキュメントに同時に注釈を付けることができます。
### GroupDocs.Annotation ユーザーはテクニカル サポートを利用できますか?
はい、GroupDocs はフォーラムを通じて専用のテクニカル サポートを提供しています。訪問[ここ](https://forum.groupdocs.com/c/annotation/10)サポートのための。
### 購入する前に GroupDocs.Annotation を試すことはできますか?
はい、利用可能な無料トライアルを通じて GroupDocs.Annotation を探索できます。[ここ](https://releases.groupdocs.com/).