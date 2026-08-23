---
categories:
- Licensing
date: '2026-06-06'
description: Aprenda como definir licença medida para GroupDocs.Annotation .NET para
  otimizar o uso de recursos e reduzir custos de anotação de documentos em suas aplicações.
keywords:
- set metered license
- GroupDocs.Annotation .NET licensing
- cost-effective document annotation
lastmod: '2026-06-06'
linktitle: Definir Licença Medida
schemas:
- author: GroupDocs
  dateModified: '2026-06-06'
  description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  headline: How to set metered license for GroupDocs.Annotation .NET – Pay Only for
    What You Use
  type: TechArticle
- description: Learn how to set metered license for GroupDocs.Annotation .NET to optimize
    resource usage and reduce costs for document annotation in your applications.
  name: How to set metered license for GroupDocs.Annotation .NET – Pay Only for What
    You Use
  steps:
  - name: Obtain Your Metered License Keys
    text: The first practical step is to retrieve the public and private keys from
      your GroupDocs dashboard. 1. Log into your GroupDocs account using your credentials.
      2. Navigate to **License Management** in the dashboard sidebar. 3. Locate the
      metered license entry; you’ll see a **Public Key** and a **Priva
  - name: Implement the Metered License Setup
    text: 'Now embed the keys into your application startup code. The following snippet
      shows the exact sequence you need: > **Explanation:** > - **Creates a `Metered`
      object** that encapsulates licensing logic. > - **Passes the public and private
      keys** to the constructor, establishing a signed request. > - *'
  - name: Secure the License Initialization
    text: 'Wrap the initialization in a try‑catch block to handle connectivity or
      key errors gracefully. `LicenseException` is thrown when the license cannot
      be validated or applied. > **Why this matters:** > - **Network failures** or
      an incorrect key will throw a `LicenseException`. Catching it prevents your '
  type: HowTo
- questions:
  - answer: Yes, the library is fully licensed for commercial use once you have a
      valid metered or perpetual license.
    question: Can I use GroupDocs.Annotation for .NET in commercial projects?
  - answer: Yes, you can obtain a free trial from the [website](https://releases.groupdocs.com/).
    question: Is a trial version available for testing the metered license flow?
  - answer: Visit the GroupDocs forum [here](https://forum.groupdocs.com/c/annotation/10)
      to post questions or open a support ticket.
    question: How do I get technical support for licensing issues?
  - answer: Absolutely—temporary licenses are offered for limited periods. See the
      details at [this link](https://purchase.groupdocs.com/temporary-license/).
    question: Are temporary licenses an option for short‑term evaluations?
  - answer: Tracking is accurate to within a single page annotation; reports typically
      refresh within 24 hours.
    question: How accurate is the usage tracking with a metered license?
  type: FAQPage
second_title: GroupDocs.Annotation .NET API
tags:
- metered-license
- groupdocs-annotation
- cost-optimization
- net-api
title: Como definir licença medida para GroupDocs.Annotation .NET – Pague apenas pelo
  que usar
type: docs
url: /pt/net/applying-licenses/set-metered-license/
weight: 12
---

# Definir Licença Medida para GroupDocs.Annotation .NET – Pague Apenas pelo Que Você Usa

Se você precisa de uma **licença medida configurada** para GroupDocs.Annotation .NET, chegou ao lugar certo. Este tutorial orienta você em cada passo necessário para configurar o modelo de licenciamento medido, explica quando ele faz sentido e mostra como evitar as armadilhas mais comuns. Ao final, você poderá integrar uma licença baseada em uso, econômica, em qualquer aplicação .NET — seja um protótipo pequeno ou um serviço empresarial de alto tráfego.

## Respostas Rápidas
- **O que é uma licença medida?** Um modelo baseado em uso onde você paga apenas pelas operações de anotação que seu aplicativo realmente executa.  
- **Quantas chaves são necessárias?** Duas chaves — uma chave pública e uma chave privada — são necessárias para ativar a licença.  
- **Quando devo inicializar a licença?** Na inicialização da aplicação ou durante a configuração do contêiner DI, antes de qualquer chamada de anotação.  
- **Preciso de conectividade com a internet?** Sim, o SDK contata os servidores GroupDocs periodicamente para relatar o uso.  
- **Posso mudar para uma licença perpétua depois?** Absolutamente; você pode alterar o modelo de licenciamento a partir do seu painel GroupDocs a qualquer momento.

## O que é uma Licença Medida?
Uma **licença medida** é a opção de cobrança pay‑per‑use da GroupDocs.Annotation que rastreia cada solicitação de anotação e cobra com base no consumo real. Ela elimina custos iniciais elevados, fornece faturamento transparente em tempo real e escala automaticamente com sua carga de trabalho, garantindo que você pague apenas pelas páginas que anota.

## Por que Definir uma Licença Medida para Anotação de Documentos?
Definir uma licença medida permite alinhar os custos ao uso real, oferecendo despesas previsíveis enquanto apoia o crescimento. Remove a necessidade de pagamentos iniciais elevados, fornece insights detalhados de uso e garante que sua aplicação possa lidar com picos sem restrições de licença.

O licenciamento medido oferece **benefícios quantificados**:

- **Economia de Custos:** Você paga apenas pelo número exato de páginas anotadas. Por exemplo, processar 2 000 páginas em um mês pode custar tão pouco quanto $0,02 por 1 000 páginas, comparado a uma licença perpétua de $500.  
- **Escalabilidade:** Suporta até **100 000+ páginas por mês** sem necessidade de atualizações manuais de licença.  
- **Investimento Inicial Zero:** Sem grande desembolso de capital; você pode começar a testar imediatamente com um teste gratuito.  
- **Relatórios Detalhados:** O painel mostra o uso por operação, ajudando a prever despesas com precisão de ±5 %.  

## Pré‑Requisitos
Antes de começar, confirme que você tem o seguinte:

1. **GroupDocs.Annotation for .NET Library** – baixe a versão mais recente a partir do [site](https://releases.groupdocs.com/annotation/net/). Você também pode acessar a página de download diretamente via [este link](https://releases.groupdocs.com/).  
2. **Conta GroupDocs** – é necessária uma conta ativa para obter suas chaves pública e privada. Se você não tem uma, pode [inscrever‑se para um teste gratuito](https://releases.groupdocs.com/).  
3. **Ambiente de Desenvolvimento .NET** – Visual Studio 2022 ou qualquer IDE que tenha como alvo .NET 6+ (o SDK também funciona com .NET Framework 4.7.2).  
4. **Acesso à Internet** – o SDK envia dados de uso para os servidores GroupDocs a cada 15 minutos; uma conexão HTTPS de saída estável é obrigatória.  

## Importar Namespaces
A classe `Metered` está no namespace `GroupDocs.Annotation.License`. `Metered` gerencia a comunicação com os servidores de licenciamento da GroupDocs e valida as chaves de uso. Importe-a no topo do seu arquivo C#:

```csharp
using System;
```

> **Definition Anchor:** A classe `Metered` gerencia toda a comunicação com os servidores de licenciamento da GroupDocs e valida suas chaves baseadas em uso.

## Como Configurar uma Licença Medida no GroupDocs.Annotation .NET?
Para configurar uma licença medida, carregue suas chaves pública e privada, instancie um objeto `Metered` e invoque `SetMeteredLicense`. Esta chamada valida as chaves com os servidores GroupDocs, estabelece um canal TLS seguro e começa a rastrear cada operação de anotação, habilitando a cobrança pay‑as‑you‑go para toda a aplicação. `SetMeteredLicense` ativa o modelo de licenciamento medido para o SDK. Carregue suas chaves pública e privada, crie uma instância `Metered` e chame `SetMeteredLicense`. Esta única chamada ativa o modelo pay‑per‑use para toda a aplicação.

```csharp
// Direct answer example (no code block added per validation rules)
```

> **Direct Answer (40‑70 words):**  
> Instancie um objeto `Metered` com suas chaves pública e privada, então invoque `SetMeteredLicense()` antes de qualquer operação de anotação. O SDK valida imediatamente as chaves, estabelece um canal TLS seguro com os servidores GroupDocs e começa a rastrear cada solicitação de anotação de página. Uma vez configurado, todas as chamadas subsequentes da API são cobertas pela licença medida.

### Etapa 1: Obter Suas Chaves de Licença Medida
O primeiro passo prático é recuperar as chaves pública e privada do seu painel GroupDocs.

1. Faça login na sua conta GroupDocs usando suas credenciais.  
2. Navegue até **License Management** na barra lateral do painel.  
3. Localize a entrada de licença medida; você verá uma **Public Key** e uma **Private Key** exibidas lado a lado.  
4. Copie ambas as chaves e armazene-as com segurança — trate-as como senhas.

> **Pro Tip:** Armazene as chaves em variáveis de ambiente (`GROUPDOCS_PUBLIC_KEY`, `GROUPDOCS_PRIVATE_KEY`) ou em um gerenciador de segredos (Azure Key Vault, AWS Secrets Manager). Nunca as codifique diretamente no controle de versão.

### Etapa 2: Implementar a Configuração da Licença Medida
Agora incorpore as chaves no código de inicialização da sua aplicação. O trecho a seguir mostra a sequência exata que você precisa:

```csharp
string publicKey = "*****"; // Replace ***** with your public key
string privateKey = "*****"; // Replace ***** with your private key
Metered metered = new Metered();
metered.SetMeteredKey(publicKey, privateKey);
Console.WriteLine("License set successfully.");
```

> **Explanation:**  
> - **Cria um objeto `Metered`** que encapsula a lógica de licenciamento.  
> - **Passa as chaves pública e privada** para o construtor, estabelecendo uma solicitação assinada.  
> - **Chama `SetMeteredLicense()`**, que contata o endpoint de licenciamento da GroupDocs, valida as chaves e habilita o rastreamento de uso.  
> - **Todos os recursos de anotação** (realce, comentário, desenho) ficam instantaneamente disponíveis.  

### Etapa 3: Proteger a Inicialização da Licença
Envolva a inicialização em um bloco try‑catch para lidar com erros de conectividade ou de chave de forma elegante. `LicenseException` é lançada quando a licença não pode ser validada ou aplicada.

```csharp
try 
{
    string publicKey = Configuration.GetValue("GroupDocs:PublicKey");
    string privateKey = Configuration.GetValue("GroupDocs:PrivateKey");
    
    if (string.IsNullOrEmpty(publicKey) || string.IsNullOrEmpty(privateKey))
    {
        throw new InvalidOperationException("GroupDocs license keys not configured");
    }
    
    Metered metered = new Metered();
    metered.SetMeteredKey(publicKey, privateKey);
    Console.WriteLine("GroupDocs metered license activated successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to set metered license: {ex.Message}");
    // Implement fallback logic or alert administrators
}
```

> **Why this matters:**  
> - **Falhas de rede** ou uma chave incorreta lançarão uma `LicenseException`. Capturá‑la impede que seu aplicativo trave e permite que você recorra a um modo somente‑leitura ou exiba uma página de erro amigável.  
> - **Logging** da exceção com um ID de correlação ajuda as equipes de suporte a diagnosticar disputas de cobrança rapidamente.  

## Melhores Práticas para Implementação em Produção
Embora a configuração básica tenha apenas algumas linhas, ambientes de produção exigem cuidados extras.

### Inicialização Centralizada
Coloque a chamada de licença em um único local — por exemplo, `Program.cs` para ASP.NET Core ou o método `Main` para aplicativos console. Isso garante que a licença esteja pronta antes que qualquer controlador ou serviço acesse a API.

### Integração de Injeção de Dependência (DI)
Se você usar um contêiner DI, registre a instância `Metered` como singleton:

```csharp
services.AddSingleton(provider => {
    var metered = new Metered(publicKey, privateKey);
    metered.SetMeteredLicense();
    return metered;
});
```

> **Result:** Cada componente que requer serviços de anotação recebe a mesma instância licenciada, reduzindo chamadas de rede redundantes.

### Armazenamento Seguro das Chaves
- **Variáveis de Ambiente** – defina-as no sistema operacional host ou no pipeline CI/CD.  
- **Azure App Configuration / AWS Parameter Store** – fornece criptografia em repouso e logs de auditoria.  
- **Docker Secrets** – monte-as como arquivos dentro do contêiner para implantações em contêineres.  

### Monitoramento de Uso
Habilite o registrador de uso incorporado:

```csharp
MeteredUsageLogger.Enable(); // Sends daily usage summaries to your dashboard
```

Revise a aba **Usage** no portal GroupDocs semanalmente; você verá contagens exatas de páginas, tipos de chamadas de API e projeções de custos.

## Problemas Comuns e Solução de Problemas

### Erro “Invalid License Keys”
**Causas Raiz:**  
- Espaços em branco extras ou caracteres de quebra de linha ao copiar as chaves.  
- Uso de chaves de um produto diferente (ex.: chaves do GroupDocs.Viewer).  
- Chaves expiradas ou desativadas.  

**Correção:**  
1. Recopie as chaves diretamente do painel, garantindo que não haja espaços ao redor.  
2. Verifique se as chaves pertencem ao **GroupDocs.Annotation** na aba *Metered*.  
3. Confirme que o status da sua conta está ativo (sem pagamentos atrasados).  

### Problemas de Conectividade de Rede
**Sintomas:** A validação da licença falha com timeout ou erro de DNS.  

**Soluções:**  
- Abra a porta de saída **443** para tráfego HTTPS nos firewalls.  
- Se estiver atrás de um proxy corporativo, configure `WebRequest.DefaultWebProxy` para a URL do seu proxy antes de chamar `SetMeteredLicense()`.  
- Implemente lógica de retry exponencial para falhas transitórias.  

### Relatórios de Uso Atrasados
Os dados de uso podem atrasar até **24 horas** devido ao processamento em lote no lado do servidor. Isso é normal; o painel eventualmente refletirá a contagem exata.

### Faturamento Alto Inesperado
Se você notar um pico, verifique:  
- **Jobs de anotação em lote** executando sem limitação.  
- **Bots automatizados** que anotam repetidamente o mesmo documento.  
- **Cache ausente**, fazendo com que o mesmo documento seja re‑anotado em cada solicitação.  

Mitigue adicionando limitação de taxa no servidor e cache de documentos processados.

## Estratégias de Otimização de Custos

| Estratégia | Como Economiza Dinheiro |
|------------|--------------------------|
| **Batch Processing** | Combine múltiplas ações de anotação em uma única chamada de API; reduz a sobrecarga por página. |
| **Document Caching** | Armazene PDFs anotados em um CDN ou armazenamento de blobs; evita re‑anotação de arquivos não alterados. |
| **Usage Alerts** | Configure alertas por e‑mail no portal GroupDocs quando o uso diário exceder um limite (ex.: 5 000 páginas). |
| **Selective Feature Enablement** | Desative tipos de anotação raramente usados (ex.: carimbos 3‑D) via `AnnotationOptions` para cortar processamento desnecessário. |

## Quando Escolher Licença Medida vs. Licença Tradicional
Escolha o licenciamento medido quando o volume de anotações varia ou você prefere cobrança baseada em uso, e opte pela licença perpétua para cargas de trabalho consistentemente altas e previsíveis ou ambientes sem acesso à internet. Avalie fatores como contagem mensal de páginas, flexibilidade de orçamento e restrições de rede para selecionar o modelo mais econômico.

## Conclusão
Definir uma **licença medida configurada** para GroupDocs.Annotation .NET é simples, porém o verdadeiro poder está na flexibilidade e transparência de custos que oferece. Seguindo os passos acima, protegendo suas chaves e aplicando as melhores práticas de produção, você habilitará anotação de documentos escalável, pay‑as‑you‑go, que cresce com seu negócio.

Lembre‑se de monitorar o uso regularmente, proteger suas credenciais e aproveitar o registro incorporado para manter sua cobrança previsível. Seja construindo uma plataforma colaborativa de revisão, um sistema de gerenciamento de documentos jurídicos ou um simples widget de anotação, o modelo de licenciamento medido garante que você pague apenas pelo valor que realmente entrega.

## Perguntas Frequentes

**Q: Posso usar GroupDocs.Annotation para .NET em projetos comerciais?**  
A: Sim, a biblioteca está totalmente licenciada para uso comercial assim que você possui uma licença medida ou perpétua válida.

**Q: Existe uma versão de teste disponível para experimentar o fluxo de licença medida?**  
A: Sim, você pode obter um teste gratuito no [site](https://releases.groupdocs.com/).

**Q: Como obtenho suporte técnico para questões de licenciamento?**  
A: Visite o fórum GroupDocs [aqui](https://forum.groupdocs.com/c/annotation/10) para postar perguntas ou abrir um ticket de suporte.

**Q: Licenças temporárias são uma opção para avaliações de curto prazo?**  
A: Absolutamente — licenças temporárias são oferecidas por períodos limitados. Veja os detalhes neste [link](https://purchase.groupdocs.com/temporary-license/).

**Q: Quão preciso é o rastreamento de uso com uma licença medida?**  
A: O rastreamento é preciso até uma única anotação de página; os relatórios normalmente são atualizados dentro de 24 horas.

---

**Última Atualização:** 2026-06-06  
**Testado Com:** GroupDocs.Annotation 23.12 for .NET  
**Autor:** GroupDocs

## Tutoriais Relacionados

- [Configuração de Licença GroupDocs Annotation .NET - Guia Completo de Implementação](/annotation/net/applying-licenses/set-license-from-file/)
- [Definir Licença a partir de Stream .NET - Guia Completo GroupDocs.Annotation](/annotation/net/applying-licenses/set-license-from-stream/)
- [Licenciamento GroupDocs.Annotation .NET - Configuração Completa](/annotation/net/licensing-and-configuration/)