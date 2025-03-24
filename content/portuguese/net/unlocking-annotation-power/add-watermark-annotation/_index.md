---
title: Adicionar anotação de marca d'água ao documento
linktitle: Adicionar anotação de marca d'água ao documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar anotações de marca d'água aos seus documentos sem esforço usando GroupDocs.Annotation for .NET. Melhore a clareza e a segurança dos documentos.
weight: 28
url: /pt/net/unlocking-annotation-power/add-watermark-annotation/
---
## Introdução
Neste tutorial, percorreremos o processo de adição de uma anotação de marca d’água a um documento usando GroupDocs.Annotation for .NET. As anotações de marca d'água são úteis para indicar o status de um documento, marcá-lo como confidencial ou adicionar qualquer outra informação relevante.

## Pré-requisitos

Antes de começarmos, certifique-se de ter o seguinte:

1.  GroupDocs.Annotation para .NET: você pode baixá-lo em[aqui](https://releases.groupdocs.com/annotation/net/).
2. Visual Studio: certifique-se de ter o Visual Studio instalado em seu sistema.
3. Conhecimento básico de C#: É necessária familiaridade com a linguagem de programação C# para compreender e implementar os exemplos de código.

## Importar namespaces

Antes de começarmos a codificar, vamos importar os namespaces necessários:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

Agora, vamos dividir o processo de adição de uma anotação de marca d'água em várias etapas:

## Etapa 1: definir o caminho de saída

 Primeiro, precisamos definir o caminho de saída onde o documento anotado será salvo. Usaremos o`Path` aula de`System.IO` namespace para combinar o caminho do diretório de saída com o nome do arquivo.

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Etapa 2: inicializar o anotador

seguir, inicializaremos o anotador fornecendo o caminho do documento de entrada. Isso nos permitirá adicionar anotações ao documento.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código da anotação irá aqui
}
```

## Etapa 3: criar anotação de marca d'água

Agora, vamos criar um objeto de anotação de marca d’água com as propriedades desejadas como ângulo, posição, texto, cor da fonte, opacidade, etc.

```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
{
    Angle = 75,
    Box = new Rectangle(200, 200, 100, 50),
    CreatedOn = DateTime.Now,
    Text = "Watermark",
    FontColor = 65535,
    FontSize = 12,
    Message = "This is watermark annotation",
    Opacity = 0.7,
    PageNumber = 0,
    AutoScale = true,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
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

## Etapa 4: adicionar anotação de marca d'água

 Agora, adicionaremos a anotação de marca d'água ao documento usando o`Add` método do objeto anotador.

```csharp
annotator.Add(watermark);
```

## Etapa 5: Salvar documento

Finalmente, salvaremos o documento anotado no caminho de saída especificado.

```csharp
annotator.Save(outputPath);
```

## Conclusão

Neste tutorial, aprendemos como adicionar uma anotação de marca d'água a um documento usando GroupDocs.Annotation for .NET. As anotações de marca d'água são uma ferramenta valiosa para marcar documentos com informações relevantes ou indicar seu status.

## Perguntas frequentes

### P: Posso personalizar a aparência da anotação da marca d'água?

R: Sim, você pode personalizar várias propriedades, como texto, tamanho da fonte, cor, opacidade, posição, etc., para personalizar a marca d'água de acordo com suas necessidades.

### P: O GroupDocs.Annotation for .NET é compatível com diferentes formatos de documentos?

R: Sim, GroupDocs.Annotation oferece suporte a uma ampla variedade de formatos de documentos, incluindo PDF, Microsoft Word, Excel, PowerPoint e formatos de imagem.

### P: Posso adicionar várias anotações a um único documento?

R: Com certeza, GroupDocs.Annotation permite adicionar várias anotações de diferentes tipos a um único documento, permitindo uma marcação abrangente do documento.

### P: O GroupDocs.Annotation oferece suporte para anotações colaborativas?

R: Sim, o GroupDocs.Annotation facilita a anotação colaborativa, permitindo que os usuários adicionem comentários, respostas e anotações, promovendo a colaboração eficaz entre os membros da equipe.

### P: Existe uma versão de avaliação disponível para GroupDocs.Annotation for .NET?

 R: Sim, você pode baixar uma versão de avaliação gratuita em[aqui](https://releases.groupdocs.com/).