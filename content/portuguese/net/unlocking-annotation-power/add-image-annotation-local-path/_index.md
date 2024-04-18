---
title: Adicionar anotação de imagem ao documento (caminho local)
linktitle: Adicionar anotação de imagem ao documento (caminho local)
second_title: API GroupDocs.Annotation .NET
description: Aprenda como adicionar anotações de imagem a documentos usando GroupDocs.Annotation for .NET. Aprimore os recursos de processamento de documentos com facilidade.
type: docs
weight: 14
url: /pt/net/unlocking-annotation-power/add-image-annotation-local-path/
---
## Introdução
GroupDocs.Annotation for .NET é uma biblioteca poderosa que permite aos desenvolvedores adicionar vários tipos de anotações a documentos de forma programática. Neste tutorial, aprenderemos como adicionar anotações de imagem a um documento usando um caminho local.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos:
1. Conhecimento básico da linguagem de programação C#.
2. Visual Studio instalado em seu sistema.
3. Biblioteca GroupDocs.Annotation for .NET instalada ou referenciada em seu projeto.
4. Um documento de entrada (por exemplo, PDF) e um arquivo de imagem para anotação.
## Importar namespaces
Primeiro, você precisa importar os namespaces necessários para o seu arquivo C#. Esses namespaces fornecem acesso às classes e métodos necessários para trabalhar com GroupDocs.Annotation.
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```

## Etapa 1: definir o caminho de saída
Defina o caminho de saída onde o documento anotado será salvo.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: inicializar o anotador
Inicialize o anotador fornecendo o caminho para o documento de entrada.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código da anotação vai aqui
}
```
## Etapa 3: criar anotação de imagem
 Crie uma instância do`ImageAnnotation`class e especifique suas propriedades, como posição, opacidade, número da página e caminho da imagem.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png"
};
```
## Etapa 4: adicionar anotação
 Adicione a anotação da imagem criada ao documento usando o`Add` método do anotador.
```csharp
annotator.Add(image);
```
## Etapa 5: Salvar documento
Salve o documento anotado no caminho de saída.
```csharp
annotator.Save(outputPath);
```
## Etapa 6: Exibir caminho de saída
Exiba uma mensagem indicando o salvamento bem-sucedido do documento e a localização do arquivo de saída.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Neste tutorial, aprendemos como adicionar anotações de imagem a um documento usando GroupDocs.Annotation for .NET. Seguindo estas etapas simples, você pode aprimorar seus recursos de processamento de documentos com poderosos recursos de anotação.
## Perguntas frequentes
### Posso anotar documentos que não sejam PDF?
Sim, GroupDocs.Annotation oferece suporte a vários formatos de documento, incluindo Word, Excel, PowerPoint e muito mais.
### O GroupDocs.Annotation é compatível com o .NET Core?
Sim, GroupDocs.Annotation é compatível com .NET Framework e .NET Core.
### Posso personalizar a aparência das anotações?
Com certeza, você pode personalizar a aparência, o tamanho, a cor e outras propriedades das anotações de acordo com suas necessidades.
### O GroupDocs.Annotation oferece suporte para anotações colaborativas?
Sim, GroupDocs.Annotation oferece recursos de anotação colaborativa que permitem que vários usuários façam anotações em documentos simultaneamente.
### Onde posso encontrar ajuda ou suporte adicional?
Você pode visitar o fórum GroupDocs.Annotation para obter assistência e suporte da comunidade.