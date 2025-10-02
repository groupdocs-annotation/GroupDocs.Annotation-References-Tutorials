---
"description": "Aprenda a adicionar anotações de imagem a documentos usando o GroupDocs.Annotation para .NET. Aprimore o gerenciamento de documentos com recursos avançados de anotação."
"linktitle": "Adicionar anotação de imagem ao documento (caminho remoto)"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Adicionar anotação de imagem ao documento (caminho remoto)"
"url": "/pt/net/unlocking-annotation-power/add-image-annotation-remote-path/"
type: docs
"weight": 15
---

# Adicionar anotação de imagem ao documento (caminho remoto)

## Introdução
Neste tutorial, abordaremos o processo de adição de anotações de imagem a um documento usando o GroupDocs.Annotation para .NET. Esta biblioteca fornece ferramentas poderosas para anotar vários tipos de documentos programaticamente.
## Pré-requisitos
Antes de começar, certifique-se de ter o seguinte:
1. GroupDocs.Annotation para .NET: Baixe e instale a biblioteca de [aqui](https://releases.groupdocs.com/annotation/net/).
2. Ambiente de desenvolvimento: certifique-se de ter um ambiente de desenvolvimento funcional configurado para desenvolvimento .NET.
3. Documento: Prepare o documento que deseja anotar. Para este tutorial, vamos supor que você tenha um documento PDF chamado `input.pdf`.
4. Imagem para anotação: Escolha a imagem que deseja usar para anotação. Certifique-se de ter o URL da imagem ou o caminho local em mãos.

## Importar namespaces
Antes de começar a codificar, vamos importar os namespaces necessários:
```csharp
using System;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
```
## Etapa 1: definir caminho de saída
Primeiro, defina o caminho de saída onde o documento anotado será salvo.
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: Inicializar o Annotator
Crie uma instância do `Annotator` classe e especifique o documento de entrada.
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    // O código de anotação irá aqui
}
```
## Etapa 3: Adicionar anotação de imagem
Agora, vamos adicionar a anotação de imagem ao documento. Especificaremos as propriedades da anotação de imagem, como posição, opacidade, número da página e caminho da imagem.
```csharp
ImageAnnotation image = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100), // Especifique a posição da anotação
    CreatedOn = DateTime.Now, // Defina a data de criação
    Opacity = 0.7, // Definir opacidade (0 a 1)
    PageNumber = 0, // Especifique o número da página
    ImagePath = "https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png" // Forneça o URL da imagem
};
annotator.Add(image); // Adicionar a anotação da imagem
```
## Etapa 4: Salvar documento
Salve o documento anotado no caminho de saída especificado.
```csharp
annotator.Save(outputPath);
```
## Etapa 5: Exibir caminho de saída
Informa o usuário sobre a operação bem-sucedida de salvamento do documento e exibe o caminho de saída.
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Neste tutorial, aprendemos como adicionar anotações de imagem a um documento usando o GroupDocs.Annotation para .NET. Seguindo esses passos, você pode aprimorar seus aplicativos de gerenciamento de documentos com poderosos recursos de anotação.
## Perguntas frequentes
### O GroupDocs.Annotation pode ser usado com outros formatos de documento além de PDF?
Sim, o GroupDocs.Annotation suporta vários formatos de documento, incluindo Word, Excel, PowerPoint e muito mais.
### O GroupDocs.Annotation é compatível com o .NET Core?
Sim, o GroupDocs.Annotation é compatível com o .NET Framework e o .NET Core.
### Posso personalizar a aparência das anotações?
Sim, você pode personalizar a aparência das anotações, como cor, opacidade e tamanho.
### O GroupDocs.Annotation oferece suporte a recursos de anotação colaborativa?
Sim, o GroupDocs.Annotation oferece recursos de anotação colaborativa para colaboração em tempo real em documentos.
### Existe uma versão de teste disponível para testes?
Sim, você pode obter uma avaliação gratuita do GroupDocs.Annotation em [aqui](https://releases.groupdocs.com/).