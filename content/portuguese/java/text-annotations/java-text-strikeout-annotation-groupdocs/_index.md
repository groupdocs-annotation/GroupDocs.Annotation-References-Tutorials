---
categories:
- Java Development
date: '2026-03-30'
description: Aprenda como adicionar anotação de tachado em Java usando o GroupDocs.Annotation.
  Guia passo a passo com exemplos de código, dicas de solução de problemas e melhores
  práticas para marcação de documentos.
keywords: Java strikeout annotation tutorial, GroupDocs annotation Java guide, text
  markup Java, document annotation Java, how to add strikeout annotation java
lastmod: '2026-03-30'
linktitle: Add Strikeout Annotation Java Tutorial
tags:
- java-annotations
- groupdocs
- document-processing
- pdf-manipulation
title: Adicionar Anotação de Tachado Tutorial Java com GroupDocs
type: docs
url: /pt/java/text-annotations/java-text-strikeout-annotation-groupdocs/
weight: 1
---

# Adicionar Anotação de Tachado Java - Guia Completo do GroupDocs

Já se pegou olhando para um documento pensando: “Preciso riscar este texto, mas não posso simplesmente pegar uma caneta vermelha”? Você não está sozinho. Seja construindo um sistema de revisão de documentos, criando um fluxo de edição ou apenas precisando marcar texto para exclusão em sua aplicação Java, **add strikeout annotation java** é uma habilidade essencial. Neste tutorial vamos percorrer tudo que você precisa saber para implementar a funcionalidade de tachado de texto que realmente funciona em produção.

## Respostas Rápidas
- **Qual biblioteca suporta anotações de tachado em Java?** GroupDocs.Annotation for Java  
- **Qual palavra‑chave principal devo focar para SEO?** add strikeout annotation java  
- **Preciso de uma licença para executar o código de exemplo?** Um teste gratuito ou licença temporária funciona para desenvolvimento; uma licença completa é necessária para produção.  
- **Posso usar isso com arquivos PDF, DOCX e PPTX?** Sim – GroupDocs.Annotation suporta todos os principais formatos de documento.  
- **Qual versão do Java é necessária?** JDK 8 ou superior (JDK 11+ recomendado).

## O que é add strikeout annotation java?
Uma anotação de tachado desenha uma linha através do texto selecionado, indicando visualmente que o conteúdo deve ser removido ou ignorado. É uma forma não destrutiva de sugerir exclusões enquanto mantém o texto original intacto para trilhas de auditoria ou revisões colaborativas.

## Por que usar anotações de tachado em aplicações Java?
- **Fluxos de revisão de documentos** – revisores podem sinalizar texto indesejado sem alterar a fonte.  
- **Edição colaborativa** – membros da equipe veem sugestões de exclusão instantaneamente.  
- **Legal e conformidade** – mantém uma trilha de auditoria clara das alterações.  
- **Migração de conteúdo** – marca seções obsoletas antes de mover conteúdo entre sistemas.  

## Pré‑requisitos e Configuração do Ambiente
Você precisará do seguinte antes de mergulhar no código:

- **Java Development Kit (JDK)** 8+ (JDK 11+ recomendado)  
- **Maven ou Gradle** para gerenciamento de dependências  
- **IDE** – IntelliJ IDEA, Eclipse ou VS Code com extensões Java  
- **GroupDocs.Annotation library** – usaremos a versão 25.2 nos exemplos  

*Bom ter:* conhecimento básico de anotações Java e manipulação de PDF.

## Configurando GroupDocs.Annotation para Java

### Configuração Maven que Realmente Funciona
Adicione o repositório e a dependência ao seu `pom.xml` exatamente como mostrado:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/annotation/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-annotation</artifactId>
      <version>25.2</version>
   </dependency>
</dependencies>
```

### Obtendo sua Licença
GroupDocs oferece várias opções de licenciamento:

- **Teste gratuito** – perfeito para testes (sem necessidade de cartão de crédito)  
- **Licença temporária** – ideal para desenvolvimento e testes  
- **Licença completa** – necessária para uso em produção; veja a [purchase page](https://purchase.groupdocs.com/buy)

> **Dica profissional:** Comece com o teste gratuito para explorar a API, depois troque para uma licença temporária quando estiver pronto para construir um recurso real.

### Configuração Rápida de Verificação
Execute este programa mínimo para verificar se a biblioteca carrega corretamente:

```java
import com.groupdocs.annotation.Annotator;

public class DocumentSetup {
    public static void main(String[] args) {
        try {
            Annotator annotator = new Annotator("path/to/your/document.pdf");
            System.out.println("GroupDocs.Annotation is ready to use!");
            annotator.dispose();
        } catch (Exception e) {
            System.out.println("Setup issue: " + e.getMessage());
        }
    }
}
```

## Como adicionar add strikeout annotation java

A seguir está uma implementação completa, pronta para produção, dividida em etapas claras.

### Etapa 1 – Inicializar o Annotator
Crie uma instância `Annotator` que aponta para o documento fonte:

```java
Annotator annotator = new Annotator("YOUR_DOCUMENT_DIRECTORY/dev_sample.pdf");
```

> **Por que isso importa:** Usar um caminho absoluto ou relativo resolvido corretamente evita exceções “arquivo não encontrado”.

### Etapa 2 – (Opcional) Preparar Respostas de Comentário
Adicionar respostas torna a anotação colaborativa:

```java
Reply reply1 = new Reply();
reply1.setComment("First comment");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Second comment");
reply2.setRepliedOn(Calendar.getInstance().getTime());

List<Reply> replies = Arrays.asList(reply1, reply2);
```

Esses comentários aparecem quando um usuário passa o mouse sobre o tachado.

### Etapa 3 – Definir a Área de Tachado
Especifique o retângulo que envolve o texto que você deseja riscar:

```java
Point point1 = new Point(80, 730);
Point point2 = new Point(240, 730);
Point point3 = new Point(80, 650);
Point point4 = new Point(240, 650);

List<Point> points = Arrays.asList(point1, point2, point3, point4);
```

> **Dica de coordenadas:** A origem (0,0) é o canto superior esquerdo da página; X cresce para a direita, Y cresce para baixo. Use um visualizador de PDF que mostre coordenadas para ajustar esses valores com precisão.

### Etapa 4 – Configurar a Anotação de Tachado
Defina a aparência, número da página e anexe os comentários:

```java
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setCreatedOn(Calendar.getInstance().getTime());
strikeout.setFontColor(65535);  // Yellow color
strikeout.setMessage("This is a strikeout annotation");
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);
strikeout.setPoints(points);
strikeout.setReplies(replies);
```

*Nota de cor:* `65535` corresponde ao amarelo no formato inteiro RGB. Altere o valor para usar outras cores.

### Etapa 5 – Aplicar a Anotação e Salvar
Adicione a anotação ao documento e escreva o arquivo de saída:

```java
annotator.add(strikeout);
annotator.save("YOUR_OUTPUT_DIRECTORY/dev.pdf");
```

### Etapa 6 – Limpar Recursos (Crítico!)
Sempre descarte o annotator para liberar recursos nativos:

```java
if (annotator != null) {
    annotator.dispose();
}
```

Em produção, envolva o uso em um bloco try‑with‑resources ou em uma construção `try/finally`.

## Problemas Comuns e Como Corrigi‑los

| Problema | Sintoma | Correção |
|----------|----------|----------|
| **File Not Found** | `Annotator` lança uma exceção | Use caminhos absolutos, verifique permissões de leitura, assegure que nenhum outro processo bloqueie o arquivo |
| **Wrong Coordinates** | O tachado aparece longe do texto desejado | Verifique novamente o sistema de coordenadas do visualizador de PDF; ajuste os pontos conforme necessário |
| **Annotation Invisible** | Nenhum tachado visível após salvar | Aumente `opacity` (ex.: `0.9`), verifique `pageNumber` (base 0), assegure que os pontos formem um retângulo adequado |
| **OutOfMemoryError** | Aplicação trava em PDFs grandes | Aumente o heap da JVM (`-Xmx2048m`), processe documentos em lotes, sempre chame `dispose()` |

## Melhores Práticas de Performance para Produção

### Gerenciamento de Memória
```java
// Good: try‑with‑resources (Java 7+)
try (Annotator annotator = new Annotator(documentPath)) {
    // annotation logic here
} // annotator automatically disposed

// Alternative: explicit disposal
Annotator annotator = null;
try {
    annotator = new Annotator(documentPath);
    // annotation logic here
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```

### Estratégia de Processamento em Lote
Quando precisar anotar dezenas ou centenas de arquivos:

- Processar 10‑20 documentos por lote.  
- Registrar sucesso/falha para cada arquivo.  
- Re‑inicializar o `Annotator` para cada documento para evitar vazamentos de memória.  

### Dicas de Cache
- Cachear modelos de documentos usados com frequência.  
- Armazenar mapas de coordenadas pré‑calculados para layouts padrão.  

## Casos de Uso no Mundo Real

1. **Sistemas de Revisão de Documentos** – Editores sugerem exclusões sem alterar o contrato original.  
2. **Emendas Legais** – Advogados rastreiam remoções de cláusulas enquanto preservam a redação original para auditoria.  
3. **Revisão Acadêmica por Pares** – Revisores marcam seções para remoção e adicionam comentários inline.  
4. **Migração de Conteúdo** – Durante migrações de CMS, tachados destacam cópias desatualizadas que precisam ser substituídas.  

## Personalização Avançada

### Estilização Personalizada
```java
// Red for critical errors
strikeout.setFontColor(16711680);
// Blue for style suggestions
strikeout.setFontColor(255);
// Adjust opacity based on confidence
strikeout.setOpacity(0.9); // high confidence
strikeout.setOpacity(0.5); // tentative suggestion
```

### Adicionando Metadados
```java
strikeout.setMessage("Deleted by: " + username + " on " + timestamp);
strikeout.setSubject("Content Review – Q1 2026");
```

## Lista de Verificação de Solução de Problemas
- ✅ Você consegue abrir o arquivo fonte manualmente?  
- ✅ Todas as dependências do GroupDocs estão presentes no classpath?  
- ✅ Os pontos formam um retângulo válido?  
- ✅ O número da página está correto (base 0)?  
- ✅ Há memória heap suficiente?  
- ✅ Você tem permissão de escrita para a pasta de saída?  
- ✅ O formato do documento é suportado (PDF, DOCX, PPTX, etc.)?  

## Perguntas Frequentes

**Q: Posso usar GroupDocs.Annotation dentro de um serviço Spring Boot?**  
A: Sim. Adicione a dependência Maven, injete uma classe de serviço que cria o `Annotator` e gerencie seu ciclo de vida com os escopos de bean do Spring.

**Q: Quais formatos de documento suportam anotações de tachado?**  
A: PDF, DOCX, PPTX e muitos outros formatos suportados pelo GroupDocs.Annotation. O PDF oferece o manuseio de coordenadas mais preciso.

**Q: Como lidar com documentos de tamanhos de página variados?**  
A: Recupere as dimensões da página via `annotator.getPageInfo(pageNumber)` e escale suas coordenadas de acordo.

**Q: É possível editar ou excluir uma anotação de tachado existente?**  
A: Absolutamente. Use `annotator.getAnnotations(pageNumber)` para buscar, então `annotator.update(updatedAnnotation)` ou `annotator.delete(annotationId)`.

**Q: Qual é o impacto de performance ao adicionar muitas anotações?**  
A: Adicionar centenas de anotações geralmente é aceitável, mas monitore o uso de memória. Para conjuntos muito grandes de anotações, considere paginar a visualização ou carregar anotações sob demanda.

## Conclusão
Agora você tem um guia completo, pronto para produção, de **add strikeout annotation java** usando GroupDocs.Annotation. Comece com o exemplo de verificação simples, depois escale para processamento em lote, estilização personalizada e enriquecimento de metadados. Lembre‑se de testar as coordenadas cuidadosamente, gerenciar recursos de forma responsável e escolher o modelo de licenciamento adequado ao seu ambiente.

Pronto para explorar mais? Confira outros tipos de anotação — realce, nota, imagem, seta e marca d’água — para construir uma suíte completa de colaboração em documentos.

---

**Última atualização:** 2026-03-30  
**Testado com:** GroupDocs.Annotation 25.2 for Java  
**Autor:** GroupDocs  

**Recursos Adicionais**

- [Documentação do GroupDocs Annotation](https://docs.groupdocs.com/annotation/java/)  
- [Guia de Referência da API](https://reference.groupdocs.com/annotation/java/)  
- [Baixar a Versão Mais Recente](https://releases.groupdocs.com/annotation/java/)  
- [Comprar Licença Completa](https://purchase.groupdocs.com/buy)  
- [Iniciar Teste Gratuito](https://releases.groupdocs.com/annotation/java/)  
- [Obter Licença Temporária](https://purchase.groupdocs.com/temporary-license/)  
- [Fórum de Suporte da Comunidade](https://forum.groupdocs.com/c/annotation/)