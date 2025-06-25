---
"date": "2025-05-06"
"description": "GroupDocs.Annotation for .NET を使用して、PDF の注釈付きページのみを効率的に保存する方法を学びましょう。この詳細なガイドで、ドキュメント管理とコラボレーションを強化しましょう。"
"title": "GroupDocs.Annotation for .NET を使用して注釈付きページを PDF に保存する方法"
"url": "/ja/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
"weight": 1
---

# GroupDocs.Annotation for .NET を使用して注釈付きページを PDF に保存する方法

## 導入

PDFドキュメントから特定の注釈付きページを保存するのに苦労していませんか？この包括的なガイドでは、GroupDocs.Annotation for .NETを使用して効率的に保存する方法を説明します。注釈機能を活用することで、ドキュメント管理を効率化し、関連コンテンツに焦点を絞ることでコラボレーションを強化します。

このチュートリアルでは、次の内容を学習します。
- GroupDocs.Annotation を使用して開発環境を設定する
- さまざまな種類の注釈を追加する
- 注釈付きページのみを効果的に保存する

始める準備はできましたか？すべての準備が整っていることを確認しましょう。

### 前提条件

始める前に、次のものを用意してください。
- **.NET フレームワーク** (バージョン4.6以降)または **.NET Core/5以上**
- Visual Studioのようなコードエディタ
- C# および .NET プロジェクトのセットアップに関する基礎知識

## GroupDocs.Annotation を .NET 用にセットアップする

GroupDocs.Annotation の使用を開始するには、NuGet 経由でインストールします。

**NuGet パッケージ マネージャー コンソール**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### ライセンス取得

GroupDocsは、ソフトウェアの機能をフルに体験していただくために無料トライアルを提供しています。長期間ご利用いただくには、ライセンスをご購入いただくか、一時ライセンスをリクエストしてください。
- **無料トライアル**最初の期間は制限なく機能を試してください。
- **一時ライセンス**本番環境では GroupDocs.Annotation を一時的に使用します。
- **購入**商用ライセンスで長期的なニーズを満たします。

インストールしたら、次のようにライブラリを初期化します。

```csharp
using GroupDocs.Annotation;

// ドキュメントを読み込んで注釈を付ける基本設定
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## 実装ガイド

### 注釈の追加

#### 概要

注釈は文書内の重要な部分を強調するのに役立ちます。注釈の追加方法を見てみましょう。 `AreaAnnotation` そして `EllipseAnnotation`。

**ステップ1: エリア注釈を作成する**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// エリア注釈を定義する
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 位置とサイズ
    BackgroundColor = 65535,                // ハイライトのARGBカラー値
    PageNumber = 1                          // 特定のページ番号
};
```

その `AreaAnnotation` 文書上の長方形の領域をハイライトします。位置をカスタマイズします（`Box`) と背景色を設定します。

**ステップ2: 楕円注釈を作成する**

```csharp
// 楕円注釈を定義する
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 位置とサイズ
    BackgroundColor = 123456,                // ハイライトのARGBカラー値
    PageNumber = 1                           // 特定のページ番号
};
```

その `EllipseAnnotation` ドキュメント上に楕円を描くことができます。位置とサイズを調整するために `Box` 財産。

**ステップ3: 注釈を追加する**

```csharp
// Annotatorインスタンスに注釈を追加する
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

使用して `Add` メソッドには複数の種類のアノテーションが含まれます。このステップでは、 `AreaAnnotation` そして `EllipseAnnotation`。

### 注釈付きページのみを保存する

#### 概要

注釈を含むページのみを保存するには、保存オプションを適切に設定します。

**ステップ4: 注釈を付けたページを保存する**

```csharp
using GroupDocs.Annotation.Options;

// 注釈付きのページのみを保存するオプションを設定する
annotator.Save("path/to/output/document.pdf\