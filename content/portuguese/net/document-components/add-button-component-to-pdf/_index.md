---
title: Adicionar componente de botão ao documento PDF
linktitle: Adicionar componente de botão ao documento PDF
second_title: API GroupDocs.Annotation .NET
description: Aprimore seus documentos PDF com componentes de botões interativos usando Groupdocs.Annotation for .NET. Siga nosso tutorial passo a passo para uma integração perfeita.
type: docs
weight: 10
url: /pt/net/document-components/add-button-component-to-pdf/
---
## Introdução
Neste tutorial, orientaremos você no processo de adição de um componente de botão a um documento PDF usando Groupdocs.Annotation for .NET. Este guia passo a passo garantirá que você possa integrar facilmente esse recurso ao seu projeto.
## Pré-requisitos
Antes de começar, certifique-se de ter os seguintes pré-requisitos em vigor:
1.  Groupdocs.Annotation for .NET: certifique-se de ter instalado a biblioteca Groupdocs.Annotation for .NET. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente de Desenvolvimento: Tenha um ambiente de desenvolvimento adequado configurado com o .NET framework instalado.

## Importar namespaces
Antes de continuar, importe os namespaces necessários para o seu projeto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```
## Etapa 1: inicializar o caminho de saída
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: adicionar componente de botão
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100),
        PenColor = 65535,
        Style = BorderStyle.Dashed,
        BorderWidth = 0,
        BorderColor = 0,
        AlternateName = "Name",
        PartialName = "Patial Name",
        NormalCaption = "Caption",
        ButtonColor = 16761035,
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
    annotator.Add(button);
    annotator.Save("result.pdf");
}
```
## Etapa 3: Exibir caminho de saída
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```
Parabéns! Você adicionou com êxito um componente de botão a um documento PDF usando Groupdocs.Annotation for .NET.

## Conclusão
Neste tutorial, demonstramos como incorporar componentes de botão em documentos PDF usando Groupdocs.Annotation for .NET. Seguindo estas etapas, você pode aprimorar seus documentos PDF com recursos interativos.
## Perguntas frequentes
### Posso personalizar a aparência do botão?
Sim, você pode personalizar várias propriedades, como tamanho, cor e estilo do componente do botão, de acordo com suas necessidades.
### O Groupdocs.Annotation for .NET é compatível com todas as versões de PDF?
Groupdocs.Annotation for .NET oferece suporte a uma ampla variedade de versões de PDF, garantindo compatibilidade com a maioria dos documentos.
### Posso adicionar vários componentes de botão a um único documento PDF?
Com certeza, você pode adicionar quantos componentes de botão forem necessários a um documento PDF usando Groupdocs.Annotation for .NET.
### O Groupdocs.Annotation for .NET oferece suporte para outros formatos de arquivo?
Sim, além de PDF, Groupdocs.Annotation for .NET oferece suporte a vários outros formatos de documento, incluindo DOCX, PPTX e XLSX.
### Existe uma versão de teste disponível para fins de teste?
 Sim, você pode acessar uma avaliação gratuita do Groupdocs.Annotation for .NET em[aqui](https://releases.groupdocs.com/).