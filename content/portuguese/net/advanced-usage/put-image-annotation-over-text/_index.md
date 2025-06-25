---
"description": "Aprenda como adicionar anotações de imagem sobre texto no .NET usando o GroupDocs.Annotation para gerenciamento eficiente de documentos e colaboração."
"linktitle": "Coloque a anotação da imagem sobre o texto"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Coloque a anotação da imagem sobre o texto"
"url": "/pt/net/advanced-usage/put-image-annotation-over-text/"
"weight": 21
---

# Coloque a anotação da imagem sobre o texto

## Introdução
No mundo do desenvolvimento .NET, o GroupDocs.Annotation oferece uma solução poderosa para adicionar anotações a documentos, tornando a colaboração e o gerenciamento de documentos mais eficientes. Um requisito comum é inserir anotações de imagem sobre texto, o que pode ser feito perfeitamente usando o GroupDocs.Annotation para .NET.
## Pré-requisitos
Antes de começar o processo de inserir anotações de imagem sobre texto usando o GroupDocs.Annotation for .NET, certifique-se de ter o seguinte:
1. GroupDocs.Annotation para biblioteca .NET: Baixe e instale a biblioteca em [aqui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente de desenvolvimento: configure um ambiente de desenvolvimento adequado, como o Visual Studio ou qualquer outro IDE .NET.
3. Arquivos de documentos e imagens: prepare o arquivo de documento (PDF, DOCX, etc.) e o arquivo de imagem que deseja usar para anotações.
4. Noções básicas de C#: familiaridade com a linguagem de programação C# é necessária para implementar os trechos de código fornecidos neste tutorial.

## Importar namespaces
Antes de prosseguir com o processo de anotação, certifique-se de importar os namespaces necessários no seu projeto C#:
```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Etapa 1: Definir o caminho de saída
Primeiro, defina o caminho de saída onde o documento anotado será salvo:
```csharp
string outputPath = Path.Combine("Your Document Directory", "annotated_document.pdf");
```
## Etapa 2: Inicializar o Annotator
Inicializar o `Annotator` objeto fornecendo o caminho do documento de entrada:
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código de anotação irá aqui
}
```
## Etapa 3: Criar anotação de imagem
Criar um `ImageAnnotation` objeto com as propriedades desejadas, como dimensões da caixa, opacidade, número da página, caminho da imagem e índice z:
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "image.png",
    ZIndex = 3
};
```
## Etapa 4: Adicionar anotação
Adicione a anotação da imagem ao documento usando o `Add` método do `Annotator` objeto:
```csharp
annotator.Add(image);
```
## Etapa 5: Salvar documento anotado
Salve o documento anotado no caminho de saída especificado:
```csharp
annotator.Save(outputPath);
```
## Etapa 6: Exibir mensagem de sucesso
Exibir uma mensagem de sucesso com o caminho para o documento anotado:
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Concluindo, adicionar anotações de imagem sobre texto em aplicativos .NET usando o GroupDocs.Annotation é um processo simples. Seguindo o guia passo a passo fornecido neste tutorial, você poderá anotar documentos com eficiência e aprimorar os recursos de colaboração e gerenciamento de documentos em seus projetos .NET.
## Perguntas frequentes
### Posso fazer anotações em documentos que não sejam PDFs?
Sim, o GroupDocs.Annotation suporta vários formatos de documento, como DOCX, XLSX, PPTX e mais.
### Existe um teste gratuito disponível para o GroupDocs.Annotation?
Sim, você pode baixar uma versão de teste gratuita em [aqui](https://releases.groupdocs.com/).
### Como posso obter suporte para o GroupDocs.Annotation?
Você pode obter suporte no fórum da comunidade GroupDocs.Annotation [aqui](https://forum.groupdocs.com/c/annotation/10).
### Preciso de uma licença temporária para fins de testes?
Sim, você pode obter uma licença temporária em [aqui](https://purchase.groupdocs.com/temporary-license/) para fins de teste.
### Posso personalizar a aparência das anotações?
Sim, o GroupDocs.Annotation oferece várias opções para personalizar a aparência das anotações, como cor, opacidade, tamanho da fonte, etc.