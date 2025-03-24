---
title: 従量制ライセンスの設定
linktitle: 従量制ライセンスの設定
second_title: GroupDocs.Annotation .NET API
description: GroupDocs.Annotation .NET の従量制ライセンスを設定して、.NET アプリケーションのリソース使用量とドキュメント注釈機能を設定する方法について説明します。
weight: 12
url: /ja/net/applying-licenses/set-metered-license/
---

# 従量制ライセンスの設定

## 導入
GroupDocs.Annotation for .NET は、開発者がドキュメントの注釈機能を .NET アプリケーションに簡単に追加できるようにする強力なライブラリです。ドキュメント管理システム、コラボレーション プラットフォーム、またはドキュメント レビューとマークアップを伴うアプリケーションを構築している場合でも、GroupDocs.Annotation for .NET はプロセスを合理化するための包括的なツール セットを提供します。
このチュートリアルでは、GroupDocs.Annotation .NET の従量制ライセンスをセットアップするプロセスを詳しく説明します。従量制ライセンスでは、消費したリソースに対してのみ料金を支払うことができるため、あらゆる規模のプロジェクトにとってコスト効率の高いソリューションとなります。以下に概説する手順に従うことで、リソース使用量を最適化し、予算管理を維持しながら、GroupDocs.Annotation を .NET アプリケーションにシームレスに統合できます。
## 前提条件
チュートリアルに進む前に、次の前提条件を満たしていることを確認してください。
1.  GroupDocs.Annotation for .NET ライブラリ: からライブラリをダウンロードします。[Webサイト](https://releases.groupdocs.com/annotation/net/).
2. GroupDocs アカウントへのアクセス: 従量制ライセンスの設定に必要な公開キーと秘密キーを取得するには、GroupDocs アカウントが必要です。まだアカウントをお持ちでない場合は、無料トライアルにサインアップできます[ここ](https://releases.groupdocs.com/).
3. C# と .NET Framework の基本的な理解: C# プログラミング言語と .NET Framework に精通していると、このチュートリアルで概説されている手順を実装するのに役立ちます。

## 名前空間のインポート
まず、必要な名前空間を C# プロジェクトにインポートしてください。これらの名前空間は、GroupDocs.Annotation 機能と対話するために不可欠です。
```csharp
using System;
```
## ステップ 1: 公開キーと秘密キーを取得する
従量制ライセンスを設定する前に、GroupDocs アカウント ダッシュボードから公開キーと秘密キーを取得する必要があります。
1. GroupDocs アカウントにログインします。
2. ライセンス管理セクションに移動します。
3. GroupDocs から提供された公開キーと秘密キーをコピーします。
## ステップ 2: 従量制ライセンスを設定する
公開キーと秘密キーを取得したら、.NET アプリケーションで従量制ライセンスを設定できます。
```csharp
string publicKey = "*****"; // ***** を公開鍵に置き換えます
string privateKey = "*****"; //***** を秘密鍵に置き換えます
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## 結論
結論として、GroupDocs.Annotation .NET の従量制ライセンスのセットアップは簡単なプロセスであり、ドキュメント アノテーション プロジェクトの効率的なリソース利用とコスト効率を確保します。このチュートリアルで概説されている手順に従うことで、GroupDocs.Annotation を .NET アプリケーションにシームレスに統合し、ドキュメントの共同作業とレビュー機能を強化できます。
## よくある質問
### GroupDocs.Annotation for .NET を商用プロジェクトで使用できますか?
はい、GroupDocs.Annotation for .NET は商用プロジェクトと非商用プロジェクトの両方で使用できます。ただし、プロジェクトの要件に基づいて適切なライセンスを取得する必要があります。
### GroupDocs.Annotation for .NET で利用できる試用版はありますか?
はい、次のサイトにアクセスして、GroupDocs.Annotation for .NET の無料トライアルを利用できます。[このリンク](https://releases.groupdocs.com/).
### GroupDocs.Annotation for .NET のテクニカル サポートを受けるにはどうすればよいですか?
 GroupDocs フォーラムにアクセスして技術サポートを求めることができます。[ここ](https://forum.groupdocs.com/c/annotation/10).
### 利用可能な一時ライセンスのオプションはありますか?
はい、短期間の使用または評価の目的で、GroupDocs から一時ライセンスを取得できます。訪問[このリンク](https://purchase.groupdocs.com/temporary-license/)詳細については。
### プロジェクトの要件に応じてアノテーション機能をカスタマイズできますか?
はい、GroupDocs.Annotation for .NET は広範なカスタマイズ オプションを提供しており、特定のプロジェクトのニーズに合わせて注釈機能を調整できます。