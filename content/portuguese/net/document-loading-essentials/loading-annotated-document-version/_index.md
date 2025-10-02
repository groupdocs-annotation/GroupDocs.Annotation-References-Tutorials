---
"description": "Aprenda a carregar versões anotadas de documentos sem esforço usando o GroupDocs.Annotation para .NET. Simplifique os processos de colaboração e revisão."
"linktitle": "Carregando a versão do documento anotado"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Carregando a versão do documento anotado"
"url": "/pt/net/document-loading-essentials/loading-annotated-document-version/"
type: docs
"weight": 16
---

# Carregando a versão do documento anotado

## Introdução
Na era digital atual, a anotação em documentos se tornou uma ferramenta essencial para colaboração, revisão e feedback em diversos setores. Seja você um desenvolvedor integrando recursos de anotação em seu aplicativo ou um usuário que busca aproveitar esses recursos, o GroupDocs.Annotation para .NET oferece uma solução poderosa. Neste tutorial, vamos nos aprofundar no processo de carregamento de versões anotadas de documentos usando o GroupDocs.Annotation para .NET.
## Pré-requisitos
Antes de começar, certifique-se de que você tenha os seguintes pré-requisitos:
### 1. Instale o GroupDocs.Annotation para .NET
Você pode baixar os arquivos necessários do [página de lançamentos](https://releases.groupdocs.com/annotation/net/). Siga as instruções de instalação fornecidas para configurar a biblioteca no seu ambiente .NET.
### 2. Obtenha um documento com anotações
Para este tutorial, você precisará de um documento com anotações. Certifique-se de ter um formato de documento compatível (por exemplo, PDF) contendo as anotações que deseja carregar.

## Importando namespaces
Para iniciar o processo, você precisa importar os namespaces necessários para o seu projeto. Esses namespaces fornecem acesso à funcionalidade do GroupDocs.Annotation para .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


Agora que abordamos os pré-requisitos e as importações de namespace, vamos nos aprofundar no processo passo a passo de carregamento de versões de documentos anotados usando o GroupDocs.Annotation para .NET.
## Etapa 1: Definir o caminho de saída
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: especifique as opções de carga
```csharp
LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
```
## Etapa 3: Inicializar o Annotator
```csharp
using (Annotator annotator = new Annotator("annotated_with_versions.pdf", loadOptions))
```
## Etapa 4: recuperar anotações
```csharp
var annotations = annotator.Get();
```
## Etapa 5: Salvar documento com anotações
```csharp
annotator.Save(outputPath);
```
## Etapa 6: Exibir mensagem de confirmação
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Neste tutorial, exploramos como carregar versões anotadas de documentos usando o GroupDocs.Annotation para .NET. Seguindo o guia passo a passo e aproveitando os recursos desta poderosa biblioteca, você pode integrar perfeitamente a funcionalidade de anotação de documentos aos seus aplicativos .NET.
## Perguntas frequentes
### Posso anotar documentos de vários formatos com o GroupDocs.Annotation para .NET?
Sim, o GroupDocs.Annotation suporta anotações em documentos em formatos como PDF, DOCX, PPTX, XLSX e mais.
### Existe uma avaliação gratuita disponível para o GroupDocs.Annotation para .NET?
Sim, você pode acessar a versão de teste gratuita em [aqui](https://releases.groupdocs.com/).
### Onde posso encontrar documentação do GroupDocs.Annotation para .NET?
Você pode consultar a documentação detalhada [aqui](https://tutorials.groupdocs.com/annotation/net/).
### Como posso obter uma licença temporária para o GroupDocs.Annotation para .NET?
Você pode adquirir uma licença temporária em [este link](https://purchase.groupdocs.com/temporary-license/).
### Onde posso buscar suporte ou tirar dúvidas sobre o GroupDocs.Annotation para .NET?
Você pode visitar o fórum GroupDocs.Annotation [aqui](https://forum.groupdocs.com/c/annotation/10).