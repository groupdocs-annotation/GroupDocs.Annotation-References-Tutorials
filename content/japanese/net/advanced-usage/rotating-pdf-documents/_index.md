---
title: PDF ドキュメントの回転
linktitle: PDF ドキュメントの回転
second_title: GroupDocs.Annotation .NET API
description: Groupdocs.Annotation for .NET を使用して PDF ドキュメントを簡単に回転する方法を学びます。文書管理の効率を向上させます。
weight: 22
url: /ja/net/advanced-usage/rotating-pdf-documents/
---

# PDF ドキュメントの回転

## 導入
PDF ドキュメントの回転は、別の方法で表示または処理する必要があるファイルを処理する場合に重要なタスクとなることがあります。このチュートリアルでは、Groupdocs.Annotation for .NET を使用して PDF ドキュメントを回転する方法を段階的に説明します。
## 前提条件
チュートリアルに入る前に、次の前提条件を満たしていることを確認してください。
1.  Groupdocs.Annotation for .NET ライブラリ: Groupdocs.Annotation for .NET ライブラリをダウンロードしてインストールしていることを確認します。からダウンロードできます[ここ](https://releases.groupdocs.com/annotation/net/).
2. C# プログラミングの基本知識: このチュートリアルは、C# プログラミング言語と .NET ライブラリの操作方法についての基本を理解していることを前提としています。

## 名前空間のインポート
まず、Groupdocs.Annotation ライブラリが提供する機能にアクセスするには、必要な名前空間を C# プロジェクトにインポートする必要があります。
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Options;
```
## ステップ 1: PDF ドキュメントをロードする
まず、回転したい PDF ドキュメントをロードします。`Annotator`クラス。
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
## ステップ 2: 回転を設定し、ページを処理する
回転角度と回転するページを指定します。この例では、最初のページを時計回りに 90 度回転します。
```csharp
annotator.ProcessPages = 1;
annotator.Rotation = RotationDocument.on90;
```
## ステップ 3: 回転したドキュメントを保存する
指定した変更を加えて回転した PDF ドキュメントを保存します。
```csharp
annotator.Save("result.pdf");
```
## ステップ4: 確認を表示する
ドキュメントが正常に回転されたことをユーザーに通知します。
```csharp
Console.WriteLine($"\nThe document is rotated 90 degrees");
```

## 結論
PDF ドキュメントの回転は基本的な操作ですが、Groupdocs.Annotation for .NET を使用すると、これがシンプルかつ効率的になります。このチュートリアルで概説されている手順に従うことで、要件に応じて PDF ファイルを簡単に回転できます。
## よくある質問
### Groupdocs.Annotation for .NET を使用して PDF ドキュメント内の複数のページを回転できますか?
はい、回転する複数のページを指定するには、`ProcessPages`それに応じてプロパティ。
### Groupdocs.Annotation for .NET は、.NET Framework のすべてのバージョンと互換性がありますか?
Groupdocs.Annotation for .NET は、幅広い .NET Framework バージョンをサポートし、ほとんどの開発環境との互換性を保証します。
### Groupdocs.Annotation for .NET には、PDF ドキュメントをさまざまな方向に回転するオプションが用意されていますか?
はい、PDF ドキュメントを時計回り、反時計回り、または要件に基づいてカスタム角度で回転できます。
### Groupdocs.Annotation for .NET を既存のドキュメント管理システムに統合できますか?
もちろん、Groupdocs.Annotation for .NET はシームレスな統合オプションを提供しており、ドキュメント管理機能を簡単に強化できます。
### Groupdocs.Annotation for .NET で利用できる試用版はありますか?
はい、以下から無料試用版を入手できます。[ここ](https://releases.groupdocs.com/).