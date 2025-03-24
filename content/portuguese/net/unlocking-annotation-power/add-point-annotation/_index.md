---
title: Adicionar anotação de ponto ao documento
linktitle: Adicionar anotação de ponto ao documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar anotação de ponto a PDFs usando GroupDocs.Annotation for .NET. Guia passo a passo para integração perfeita.
weight: 17
url: /pt/net/unlocking-annotation-power/add-point-annotation/
---

# Adicionar anotação de ponto ao documento

## Introdução
GroupDocs.Annotation for .NET é uma ferramenta poderosa que permite aos desenvolvedores adicionar vários tipos de anotações a documentos de forma programática. Neste tutorial, vamos nos concentrar em adicionar uma anotação de ponto a um documento usando C#.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
1. Compreensão básica da linguagem de programação C#.
2. Visual Studio instalado em seu sistema.
3.  Biblioteca GroupDocs.Annotation para .NET instalada. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/annotation/net/).

## Importando Namespaces Necessários
Para começar, você precisa importar os namespaces necessários para o seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```
## Etapa 1: definir o caminho de saída
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
Nesta etapa definimos o caminho de saída onde o documento anotado será salvo.
## Etapa 2: inicializar o anotador
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
```
 Aqui inicializamos o`Annotator` objeto com o documento de entrada ("input.pdf").
## Etapa 3: Criar anotação de ponto
```csharp
PointAnnotation point = new PointAnnotation
{
    Box = new Rectangle(100, 100, 0, 0),
    CreatedOn = DateTime.Now,
    Message = "This is point annotation",
    PageNumber = 0,
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
 Nesta etapa, criamos um`PointAnnotation` objeto e especifique suas propriedades, como posição, mensagem, número da página e respostas.
## Etapa 4: adicionar anotação
```csharp
annotator.Add(point);
```
Aqui, adicionamos a anotação do ponto criado ao documento.
## Etapa 5: Salvar documento
```csharp
annotator.Save(outputPath);
```
Finalmente, salvamos o documento anotado no caminho de saída especificado.

## Conclusão
Neste tutorial, aprendemos como adicionar uma anotação de ponto a um documento usando GroupDocs.Annotation for .NET. Com esta poderosa biblioteca, você pode aprimorar seus aplicativos de gerenciamento de documentos incorporando funcionalidades de anotação.
## Perguntas frequentes
### O GroupDocs.Annotation for .NET é compatível com todos os formatos de documentos?
Sim, GroupDocs.Annotation for .NET oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, Microsoft Word, Excel, PowerPoint e muito mais.
### Posso personalizar a aparência das anotações?
Absolutamente! GroupDocs.Annotation for .NET oferece diversas opções para personalizar a aparência das anotações para atender às necessidades do seu aplicativo.
### Existe uma avaliação gratuita disponível para GroupDocs.Annotation for .NET?
 Sim, você pode aproveitar um teste gratuito em[aqui](https://releases.groupdocs.com/).
### Como posso obter suporte para quaisquer problemas ou dúvidas relacionadas ao GroupDocs.Annotation for .NET?
 Você pode obter suporte no fórum GroupDocs.Annotation[aqui](https://forum.groupdocs.com/c/annotation/10).
### Posso obter uma licença temporária para fins de teste?
 Sim, você pode obter uma licença temporária de[aqui](https://purchase.groupdocs.com/temporary-license/).