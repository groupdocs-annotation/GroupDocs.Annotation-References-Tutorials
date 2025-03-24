---
title: Carregando versão anotada do documento
linktitle: Carregando versão anotada do documento
second_title: API GroupDocs.Annotation .NET
description: Aprenda como carregar facilmente versões de documentos anotados usando GroupDocs.Annotation for .NET. Simplifique os processos de colaboração e revisão.
weight: 16
url: /pt/net/document-loading-essentials/loading-annotated-document-version/
---

# Carregando versão anotada do documento

## Introdução
Na era digital de hoje, a anotação de documentos tornou-se uma ferramenta essencial para colaboração, revisão e feedback em vários setores. Quer você seja um desenvolvedor que integra recursos de anotação em seu aplicativo ou um usuário que deseja aproveitar esses recursos, o GroupDocs.Annotation for .NET oferece uma solução poderosa. Neste tutorial, nos aprofundaremos no processo de carregamento de versões anotadas de documentos usando GroupDocs.Annotation for .NET.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos em vigor:
### 1. Instale GroupDocs.Annotation para .NET
 Você pode baixar os arquivos necessários no[página de lançamentos](https://releases.groupdocs.com/annotation/net/). Siga as instruções de instalação fornecidas para configurar a biblioteca em seu ambiente .NET.
### 2. Obtenha um documento com anotações
Para este tutorial, você precisará de um documento com anotações. Certifique-se de ter um formato de documento compatível (por exemplo, PDF) contendo anotações que deseja carregar.

## Importando Namespaces
Para iniciar o processo, você precisa importar os namespaces necessários para o seu projeto. Esses namespaces fornecem acesso à funcionalidade do GroupDocs.Annotation for .NET.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Text;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Options;
```


Agora que cobrimos os pré-requisitos e as importações de namespace, vamos nos aprofundar no processo passo a passo de carregamento de versões anotadas de documentos usando GroupDocs.Annotation for .NET.
## Etapa 1: definir o caminho de saída
```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```
## Etapa 2: especificar opções de carregamento
```csharp
LoadOptions loadOptions = new LoadOptions { Version = "FIRST" };
```
## Etapa 3: inicializar o anotador
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
## Etapa 6: exibir mensagem de confirmação
```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

## Conclusão
Neste tutorial, exploramos como carregar versões anotadas de documentos usando GroupDocs.Annotation for .NET. Seguindo o guia passo a passo e aproveitando os recursos desta poderosa biblioteca, você pode integrar perfeitamente a funcionalidade de anotação de documentos em seus aplicativos .NET.
## Perguntas frequentes
### Posso anotar documentos de vários formatos com GroupDocs.Annotation for .NET?
Sim, GroupDocs.Annotation oferece suporte à anotação de documentos em formatos como PDF, DOCX, PPTX, XLSX e muito mais.
### Existe uma avaliação gratuita disponível para GroupDocs.Annotation for .NET?
 Sim, você pode acessar a versão de avaliação gratuita em[aqui](https://releases.groupdocs.com/).
### Onde posso encontrar documentação para GroupDocs.Annotation for .NET?
 Você pode consultar a documentação detalhada[aqui](https://tutorials.groupdocs.com/annotation/net/).
### Como posso obter uma licença temporária do GroupDocs.Annotation for .NET?
 Você pode adquirir uma licença temporária em[esse link](https://purchase.groupdocs.com/temporary-license/).
### Onde posso procurar suporte ou fazer perguntas sobre GroupDocs.Annotation for .NET?
 Você pode visitar o fórum GroupDocs.Annotation[aqui](https://forum.groupdocs.com/c/annotation/10).