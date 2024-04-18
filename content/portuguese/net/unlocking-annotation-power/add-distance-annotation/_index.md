---
title: Adicionar anotação de distância ao documento
linktitle: Adicionar anotação de distância ao documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar anotações de distância a documentos usando GroupDocs.Annotation for .NET. Melhore a colaboração e a comunicação sem esforço.
type: docs
weight: 12
url: /pt/net/unlocking-annotation-power/add-distance-annotation/
---
## Introdução
Neste tutorial, você aprenderá como adicionar uma anotação de distância a um documento usando GroupDocs.Annotation for .NET. Siga estas etapas para realizar a tarefa:
## Pré-requisitos

Certifique-se de ter os seguintes pré-requisitos em vigor antes de continuar:

-  Biblioteca GroupDocs.Annotation for .NET: Baixe e instale a biblioteca GroupDocs.Annotation for .NET em[esse link](https://releases.groupdocs.com/annotation/net/).
- Documento para anotar: Prepare o documento (por exemplo, PDF) ao qual deseja adicionar a anotação de distância.
- Ambiente de Desenvolvimento: Configure seu ambiente de desenvolvimento com Visual Studio ou qualquer outro IDE de sua escolha.

## Importar namespaces

Antes de começar, certifique-se de incluir os namespaces necessários em seu código. Esses namespaces são essenciais para acessar as classes e métodos necessários.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


## Etapa 1: inicializar o anotador

 Comece inicializando o`Annotator` objeto com o caminho para o documento que você deseja anotar.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código da anotação irá aqui
}
```

## Etapa 2: criar anotação de distância

 Agora, crie um`DistanceAnnotation` objeto e configurar suas propriedades como dimensões da caixa, mensagem, opacidade, cor da caneta, etc.

```csharp
DistanceAnnotation distance = new DistanceAnnotation
{
    Box = new Rectangle(200, 150, 200, 30),
    CreatedOn = DateTime.Now,
    Message = "This is distance annotation",
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

## Etapa 3: adicionar anotação

 Adicione a anotação de distância criada ao documento usando o`Add` método do objeto anotador.

```csharp
annotator.Add(distance);
```

## Etapa 4: salvar o documento

Salve o documento anotado no local desejado em seu sistema.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
annotator.Save(outputPath);
```

## Etapa 5: Exibir confirmação

Por fim, exiba uma mensagem confirmando o salvamento bem-sucedido do documento anotado.

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão

Adicionar anotações de distância a documentos usando GroupDocs.Annotation for .NET é um processo simples. Seguindo as etapas descritas neste tutorial, você pode aprimorar seus documentos com anotações valiosas, facilitando melhor colaboração e comunicação.

## Perguntas frequentes

### P: Posso personalizar a aparência da anotação de distância?

R: Sim, você pode personalizar várias propriedades, como cor, opacidade, estilo de linha, etc., para atender às suas necessidades.

### P: O GroupDocs.Annotation oferece suporte a anotações em diferentes tipos de documentos?

R: Sim, GroupDocs.Annotation oferece suporte a anotações em uma ampla variedade de formatos de documentos, incluindo PDF, Word, Excel, PowerPoint e muito mais.

### P: Existe uma avaliação gratuita disponível para GroupDocs.Annotation?

 R: Sim, você pode acessar uma avaliação gratuita do GroupDocs.Annotation em[esse link](https://releases.groupdocs.com/).

### P: Onde posso encontrar a documentação do GroupDocs.Annotation for .NET?

 R: Você pode consultar a documentação detalhada disponível[aqui](https://reference.groupdocs.com/annotation/net/).

### P: Como posso obter suporte ou assistência com GroupDocs.Annotation?

 R: Você pode buscar suporte e assistência no fórum da comunidade GroupDocs.Annotation[aqui](https://forum.groupdocs.com/c/annotation/10).