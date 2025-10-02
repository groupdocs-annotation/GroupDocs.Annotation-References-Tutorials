---
"date": "2025-05-06"
"description": "了解如何使用 GroupDocs.Annotation for .NET 高效地仅保存 PDF 中带注释的页面。本指南详尽，助您增强文档管理和协作。"
"title": "如何使用 GroupDocs.Annotation for .NET 将带注释的页面保存为 PDF"
"url": "/zh/net/document-saving/mastering-groupdocs-annotation-save-annotated-pdf-pages/"
type: docs
"weight": 1
---

# 如何使用 GroupDocs.Annotation for .NET 将带注释的页面保存为 PDF

## 介绍

还在为保存 PDF 文档中带注释的特定页面而苦恼吗？本指南将演示如何使用 GroupDocs.Annotation for .NET 高效地实现这一目标。利用注释功能，您可以专注于相关内容，从而简化文档管理并增强协作。

在本教程中，您将学习：
- 使用 GroupDocs.Annotation 设置您的开发环境
- 添加各种类型的注释
- 有效地保存带注释的页面

准备好开始了吗？让我们确保您一切就绪。

### 先决条件

开始之前，请确保您已具备以下条件：
- **.NET 框架** （4.6 或更高版本）或 **.NET Core/5+**
- 像 Visual Studio 这样的代码编辑器
- C# 和 .NET 项目设置的基础知识

## 为 .NET 设置 GroupDocs.Annotation

要开始使用 GroupDocs.Annotation，请通过 NuGet 安装它。

**NuGet 包管理器控制台**

```plaintext
Install-Package GroupDocs.Annotation -Version 25.4.0
```

**\.NET CLI**

```bash
dotnet add package GroupDocs.Annotation --version 25.4.0
```

### 许可证获取

GroupDocs 提供免费试用，方便用户全面探索其软件。如需长期使用，请购买许可证或申请临时许可证：
- **免费试用**：在初始阶段探索不受限制的功能。
- **临时执照**：在生产中暂时使用 GroupDocs.Annotation。
- **购买**：使用商业许可证来保障您的长期需求。

安装后，按如下方式初始化库：

```csharp
using GroupDocs.Annotation;

// 加载和注释文档的基本设置
Annotator annotator = new Annotator("path/to/your/document.pdf");
```

## 实施指南

### 添加注释

#### 概述

注释有助于突出显示文档中的重要区域。让我们来探索如何添加 `AreaAnnotation` 和一个 `EllipseAnnotation`。

**步骤 1：创建区域注释**

```csharp
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

// 定义区域注释
AreaAnnotation area = new AreaAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 位置和大小
    BackgroundColor = 65535,                // 高亮的 ARGB 颜色值
    PageNumber = 1                          // 具体页码
};
```

这 `AreaAnnotation` 突出显示文档中的矩形区域。自定义其位置（`Box`）和背景颜色。

**步骤 2：创建椭圆注释**

```csharp
// 定义椭圆注释
EllipseAnnotation ellipse = new EllipseAnnotation()
{
    Box = new Rectangle(100, 100, 100, 100), // 位置和大小
    BackgroundColor = 123456,                // 高亮的 ARGB 颜色值
    PageNumber = 1                           // 具体页码
};
```

这 `EllipseAnnotation` 允许在文档上绘制椭圆形。使用 `Box` 财产。

**步骤 3：添加注释**

```csharp
// 向 Annotator 实例添加注释
annotator.Add(new List<AnnotationBase>() { area, ellipse });
```

使用 `Add` 方法，包括多种类型的注释。此步骤同时添加了 `AreaAnnotation` 和 `EllipseAnnotation`。

### 仅保存带注释的页面

#### 概述

要仅保存包含注释的页面，请相应地配置保存选项。

**步骤 4：保存带注释的页面**

```csharp
using GroupDocs.Annotation.Options;

// 设置保存选项以仅包含带注释的页面
annotator.Save("path/to/output/document.pdf\