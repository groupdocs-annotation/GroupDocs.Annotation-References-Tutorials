---
title: Adicionar anotação de elipse ao documento
linktitle: Adicionar anotação de elipse ao documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar anotações de elipse a documentos em .NET usando GroupDocs.Annotation. Melhore a colaboração e a comunicação sem esforço.
weight: 13
url: /pt/net/unlocking-annotation-power/add-ellipse-annotation/
---

# Adicionar anotação de elipse ao documento

## Introdução
Neste tutorial, você aprenderá como adicionar uma anotação de elipse a um documento usando GroupDocs.Annotation for .NET. Este guia passo a passo orientará você durante o processo, garantindo que você entenda cada etapa claramente.
## Pré-requisitos
Antes de começar, certifique-se de ter o seguinte:
1.  GroupDocs.Annotation for .NET: certifique-se de ter baixado e instalado o GroupDocs.Annotation for .NET. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/annotation/net/).
2. IDE (Ambiente de Desenvolvimento Integrado): Você precisará de um IDE instalado em seu sistema, como o Visual Studio, para escrever e executar o código.

## Importar namespaces
Primeiro, importe os namespaces necessários para o seu projeto:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Etapa 1: definir caminho de saída
Defina o caminho de saída onde o documento anotado será salvo:
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: inicializar o anotador
Inicialize o anotador fornecendo o caminho do documento de entrada:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
```
## Etapa 3: criar anotação de elipse
 Crie uma instância do`EllipseAnnotation` classe e defina suas propriedades:
```csharp
EllipseAnnotation ellipse = new EllipseAnnotation
{
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is ellipse annotation",
    Opacity = 0.7,
    PageNumber = 0,
    PenColor = 65535,
    PenStyle = PenStyle.Dot,
    PenWidth = 3,
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
```
## Etapa 4: adicionar anotação
Adicione a anotação de elipse ao documento:
```csharp
annotator.Add(ellipse);
```
## Etapa 5: Salvar documento
Salve o documento anotado no caminho de saída:
```csharp
annotator.Save(outputPath);
```

## Conclusão
Parabéns! Você adicionou com êxito uma anotação de elipse a um documento usando GroupDocs.Annotation for .NET. Agora você pode integrar essa funcionalidade em seus aplicativos .NET para aprimorar a colaboração e a comunicação de documentos.
## Perguntas frequentes
### Posso personalizar a aparência da anotação da elipse?
Sim, você pode personalizar várias propriedades, como cor de fundo, cor da borda, opacidade, etc., de acordo com suas necessidades.
### O GroupDocs.Annotation for .NET é compatível com todos os formatos de documentos?
GroupDocs.Annotation for .NET oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, DOCX, PPTX, XLSX e muito mais.
### Posso adicionar várias anotações a um único documento?
Sim, você pode adicionar várias anotações, incluindo elipses, retângulos, texto, etc., a um único documento.
### Existe uma versão de teste disponível para fins de teste?
 Sim, você pode baixar uma versão de avaliação gratuita em[aqui](https://releases.groupdocs.com/) para avaliar suas características.
### Onde posso obter suporte técnico para GroupDocs.Annotation for .NET?
 Você pode obter suporte técnico no fórum da comunidade GroupDocs.Annotation[aqui](https://forum.groupdocs.com/c/annotation/10).