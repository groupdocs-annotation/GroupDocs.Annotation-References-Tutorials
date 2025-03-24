---
title: Gerar visualização sem comentários
linktitle: Gerar visualização sem comentários
second_title: API GroupDocs.Annotation .NET
description: Aprenda como integrar perfeitamente recursos de anotação de documentos em seus aplicativos .NET usando GroupDocs.Annotation for .NET.
weight: 14
url: /pt/net/advanced-usage/generate-preview-without-comments/
---

# Gerar visualização sem comentários

## Introdução
GroupDocs.Annotation for .NET é uma ferramenta poderosa que permite aos desenvolvedores incorporar recursos de anotação em seus aplicativos .NET de maneira integrada. Esteja você trabalhando em um sistema de gerenciamento de documentos, plataforma de colaboração ou qualquer outro aplicativo que exija recursos de anotação de documentos, o GroupDocs.Annotation fornece um conjunto abrangente de ferramentas para aprimorar a funcionalidade do seu aplicativo.
## Pré-requisitos
Antes de começar a usar GroupDocs.Annotation for .NET, certifique-se de ter os seguintes pré-requisitos configurados:
### 1. Instale GroupDocs.Annotation para .NET
 Para começar, você precisa baixar e instalar GroupDocs.Annotation for .NET. Você pode encontrar o link para download[aqui](https://releases.groupdocs.com/annotation/net/). Siga as instruções de instalação fornecidas na documentação para um processo de configuração tranquilo.
### 2. Obtenha licença
 GroupDocs.Annotation for .NET requer uma licença para uso comercial. Você pode adquirir uma licença de[aqui](https://purchase.groupdocs.com/buy) ou opte por uma licença temporária[aqui](https://purchase.groupdocs.com/temporary-license/) para fins de teste.
### 3. Familiaridade com .NET Framework
O conhecimento básico do .NET Framework e da linguagem de programação C# é essencial para utilizar efetivamente o GroupDocs.Annotation for .NET.

## Importar namespaces
Agora que você configurou os pré-requisitos, vamos importar os namespaces necessários para seu aplicativo .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Options;
```

Siga estas instruções passo a passo para gerar uma visualização sem comentários usando GroupDocs.Annotation for .NET:
## Etapa 1: inicializar o anotador
```csharp
using (Annotator annotator = new Annotator("annotated.pdf"_DOCX))
{
```
## Etapa 2: configurar opções de visualização
```csharp
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result{pageNumber}.png";
        return File.Create(pagePath);
    });
```
## Etapa 3: especifique o formato de visualização e os números de página
```csharp
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4, 5, 6 };
```
## Etapa 4: desativar a renderização de comentários
```csharp
    previewOptions.RenderComments = false;
```
## Etapa 5: gerar visualização
```csharp
    annotator.Document.GeneratePreview(previewOptions);
}
```
Depois de seguir essas etapas, seu aplicativo .NET poderá gerar uma visualização das páginas especificadas do documento sem renderizar comentários.

## Conclusão
Incorporar recursos de anotação em seus aplicativos .NET nunca foi tão fácil graças ao GroupDocs.Annotation for .NET. Seguindo as etapas descritas neste tutorial, você pode integrar perfeitamente recursos de anotação de documentos em seus aplicativos, aprimorando a colaboração e o gerenciamento de documentos.
## Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todos os formatos de documentos?
GroupDocs.Annotation for .NET oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, DOCX, PPTX, XLSX e muito mais.
### Posso personalizar a aparência das anotações geradas usando GroupDocs.Annotation for .NET?
Sim, o GroupDocs.Annotation for .NET oferece amplas opções de personalização, permitindo personalizar a aparência das anotações para atender às necessidades do seu aplicativo.
### GroupDocs.Annotation for .NET oferece suporte à colaboração multiusuário?
Sim, o GroupDocs.Annotation for .NET oferece recursos de anotação colaborativa, permitindo que vários usuários façam anotações em documentos simultaneamente.
### O suporte técnico está disponível para GroupDocs.Annotation for .NET?
 Sim, o suporte técnico para GroupDocs.Annotation for .NET está disponível através do[Fórum de suporte](https://forum.groupdocs.com/c/annotation/10).
### Posso experimentar o GroupDocs.Annotation for .NET gratuitamente antes de comprar?
 Sim, você pode explorar os recursos do GroupDocs.Annotation for .NET baixando a versão de avaliação gratuita[aqui](https://releases.groupdocs.com/).