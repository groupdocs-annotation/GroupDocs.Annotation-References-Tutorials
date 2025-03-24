---
title: Definir licença limitada
linktitle: Definir licença limitada
second_title: API GroupDocs.Annotation .NET
description: Saiba como configurar uma licença limitada para GroupDocs.Annotation .NET para uso de recursos e recursos de anotação de documentos em seus aplicativos .NET.
weight: 12
url: /pt/net/applying-licenses/set-metered-license/
---
## Introdução
GroupDocs.Annotation for .NET é uma biblioteca poderosa que permite aos desenvolvedores adicionar recursos de anotação de documentos aos seus aplicativos .NET sem esforço. Esteja você construindo um sistema de gerenciamento de documentos, uma plataforma de colaboração ou qualquer aplicativo que envolva revisão e marcação de documentos, o GroupDocs.Annotation for .NET fornece um conjunto abrangente de ferramentas para agilizar o processo.
Neste tutorial, nos aprofundaremos no processo de configuração de uma licença limitada para GroupDocs.Annotation .NET. Uma licença limitada permite que você pague apenas pelos recursos consumidos, tornando-a uma solução econômica para projetos de qualquer escala. Seguindo as etapas descritas abaixo, você poderá integrar perfeitamente o GroupDocs.Annotation ao seu aplicativo .NET enquanto otimiza o uso de recursos e mantém o controle orçamentário.
## Pré-requisitos
Antes de mergulhar no tutorial, certifique-se de ter os seguintes pré-requisitos:
1.  GroupDocs.Annotation for .NET Library: Baixe a biblioteca do[local na rede Internet](https://releases.groupdocs.com/annotation/net/).
2. Acesso à conta GroupDocs: você precisará de uma conta GroupDocs para obter as chaves públicas e privadas necessárias para configurar a licença medida. Se você ainda não tem uma conta, você pode se inscrever para um teste gratuito[aqui](https://releases.groupdocs.com/).
3. Compreensão básica de C# e .NET Framework: A familiaridade com a linguagem de programação C# e .NET Framework será benéfica para implementar as etapas descritas neste tutorial.

## Importar namespaces
Para começar, certifique-se de importar os namespaces necessários para o seu projeto C#. Esses namespaces são essenciais para interagir com a funcionalidade GroupDocs.Annotation.
```csharp
using System;
```
## Etapa 1: Obtenha chaves públicas e privadas
Antes de configurar a licença limitada, você precisa obter suas chaves públicas e privadas no painel da sua conta GroupDocs.
1. Faça login em sua conta GroupDocs.
2. Navegue até a seção de gerenciamento de licenças.
3. Copie suas chaves públicas e privadas fornecidas pelo GroupDocs.
## Etapa 2: definir licença limitada
Depois de obter suas chaves públicas e privadas, você poderá configurar a licença limitada em seu aplicativo .NET.
```csharp
string publicKey = "*****"; // Substitua ***** pela sua chave pública
string privateKey = "*****"; // Substitua ***** pela sua chave privada
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

## Conclusão
Concluindo, configurar uma licença limitada para GroupDocs.Annotation .NET é um processo simples que garante a utilização eficiente de recursos e economia para seus projetos de anotação de documentos. Seguindo as etapas descritas neste tutorial, você pode integrar perfeitamente o GroupDocs.Annotation ao seu aplicativo .NET e aprimorar os recursos de colaboração e revisão de documentos.
## Perguntas frequentes
### Posso usar GroupDocs.Annotation for .NET em projetos comerciais?
Sim, GroupDocs.Annotation for .NET pode ser usado em projetos comerciais e não comerciais. No entanto, você precisa adquirir uma licença apropriada com base nos requisitos do seu projeto.
### Existe uma versão de teste disponível para GroupDocs.Annotation for .NET?
 Sim, você pode aproveitar uma avaliação gratuita do GroupDocs.Annotation for .NET visitando[esse link](https://releases.groupdocs.com/).
### Como posso obter suporte técnico para GroupDocs.Annotation for .NET?
 Você pode buscar suporte técnico visitando o fórum GroupDocs[aqui](https://forum.groupdocs.com/c/annotation/10).
### Há alguma opção de licença temporária disponível?
 Sim, você pode obter uma licença temporária do GroupDocs para uso de curto prazo ou para fins de avaliação. Visita[esse link](https://purchase.groupdocs.com/temporary-license/) Para maiores informações.
### Posso personalizar os recursos de anotação de acordo com os requisitos do meu projeto?
Sim, o GroupDocs.Annotation for .NET oferece amplas opções de personalização, permitindo adaptar os recursos de anotação para atender às necessidades específicas do seu projeto.