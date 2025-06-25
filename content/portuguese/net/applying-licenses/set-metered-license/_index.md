---
"description": "Aprenda a configurar uma licença medida para o GroupDocs.Annotation .NET para uso de recursos e recursos de anotação de documentos em seus aplicativos .NET."
"linktitle": "Definir licença medida"
"second_title": "API .NET do GroupDocs.Annotation"
"title": "Definir licença medida"
"url": "/pt/net/applying-licenses/set-metered-license/"
"weight": 12
---

# Definir licença medida

## Introdução
GroupDocs.Annotation para .NET é uma biblioteca poderosa que permite aos desenvolvedores adicionar recursos de anotação de documentos às suas aplicações .NET sem esforço. Seja para criar um sistema de gerenciamento de documentos, uma plataforma de colaboração ou qualquer aplicação que envolva revisão e marcação de documentos, o GroupDocs.Annotation para .NET oferece um conjunto abrangente de ferramentas para agilizar o processo.
Neste tutorial, vamos nos aprofundar no processo de configuração de uma licença limitada para o GroupDocs.Annotation .NET. Uma licença limitada permite que você pague apenas pelos recursos que consome, tornando-a uma solução econômica para projetos de qualquer porte. Seguindo os passos descritos abaixo, você poderá integrar perfeitamente o GroupDocs.Annotation ao seu aplicativo .NET, otimizando o uso de recursos e mantendo o controle orçamentário.
## Pré-requisitos
Antes de começar o tutorial, certifique-se de ter os seguintes pré-requisitos:
1. GroupDocs.Annotation para biblioteca .NET: Baixe a biblioteca do [site](https://releases.groupdocs.com/annotation/net/).
2. Acesso à conta do GroupDocs: você precisará de uma conta do GroupDocs para obter as chaves pública e privada necessárias para configurar a licença limitada. Se ainda não tiver uma conta, inscreva-se para um teste gratuito. [aqui](https://releases.groupdocs.com/).
3. Noções básicas de C# e .NET Framework: A familiaridade com a linguagem de programação C# e o .NET Framework será benéfica para implementar as etapas descritas neste tutorial.

## Importar namespaces
Para começar, certifique-se de importar os namespaces necessários para o seu projeto C#. Esses namespaces são essenciais para interagir com a funcionalidade GroupDocs.Annotation.
```csharp
using System;
```
## Etapa 1: Obtenha chaves públicas e privadas
Antes de configurar a licença medida, você precisa obter suas chaves públicas e privadas no painel da sua conta do GroupDocs.
1. Entre na sua conta do GroupDocs.
2. Navegue até a seção de gerenciamento de licenças.
3. Copie suas chaves públicas e privadas fornecidas pelo GroupDocs.
## Etapa 2: definir licença medida
Depois de obter suas chaves públicas e privadas, você pode configurar a licença medida em seu aplicativo .NET.
```csharp
string publicKey = "*****"; // Substitua ***** pela sua chave pública
string privateKey = "*****"; // Substitua ***** pela sua chave privada
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Conclusão
Concluindo, configurar uma licença limitada para o GroupDocs.Annotation .NET é um processo simples que garante a utilização eficiente de recursos e a relação custo-benefício para seus projetos de anotação de documentos. Seguindo os passos descritos neste tutorial, você poderá integrar perfeitamente o GroupDocs.Annotation ao seu aplicativo .NET e aprimorar os recursos de colaboração e revisão de documentos.
## Perguntas frequentes
### Posso usar o GroupDocs.Annotation para .NET em projetos comerciais?
Sim, o GroupDocs.Annotation para .NET pode ser usado em projetos comerciais e não comerciais. No entanto, você precisa adquirir uma licença apropriada com base nos requisitos do seu projeto.
### Existe uma versão de teste disponível para o GroupDocs.Annotation para .NET?
Sim, você pode aproveitar uma avaliação gratuita do GroupDocs.Annotation para .NET visitando [este link](https://releases.groupdocs.com/).
### Como posso obter suporte técnico para o GroupDocs.Annotation para .NET?
Você pode buscar suporte técnico visitando o fórum do GroupDocs [aqui](https://forum.groupdocs.com/c/annotation/10).
### Há alguma opção de licença temporária disponível?
Sim, você pode obter uma licença temporária do GroupDocs para uso de curto prazo ou para fins de avaliação. Visite [este link](https://purchase.groupdocs.com/temporary-license/) para maiores informações.
### Posso personalizar os recursos de anotação de acordo com os requisitos do meu projeto?
Sim, o GroupDocs.Annotation para .NET oferece amplas opções de personalização, permitindo que você adapte os recursos de anotação para atender às necessidades específicas do seu projeto.