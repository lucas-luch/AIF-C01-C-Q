# Fine-tuning vs Prompt Engineering vs RAG

## Visão Geral

A prova AIF-C01 frequentemente apresenta cenários onde você precisa escolher entre essas três abordagens. Este bloco consolida as diferenças e cria um framework de decisão.

---

## Prompt Engineering

### O que é
Formular a instrução (prompt) de forma otimizada para obter a melhor resposta do FM, sem alterar o modelo.

### Vantagens
- ✅ Sem custo adicional (apenas tokens de inferência)
- ✅ Implementação imediata
- ✅ Fácil de iterar e testar
- ✅ Não requer dados de treinamento

### Limitações
- ❌ Limitado pela context window
- ❌ Não adiciona conhecimento novo ao modelo
- ❌ Pode ser inconsistente em escala
- ❌ Difícil manter estilo consistente em respostas longas

### Quando usar
- **Primeiro recurso sempre** — tente antes de RAG ou fine-tuning
- Tarefas que o modelo já sabe fazer (apenas precisa de direção)
- Prototipagem rápida
- Quando dados de treinamento não estão disponíveis

---

## RAG (Retrieval-Augmented Generation)

### O que é
Buscar informação relevante em bases de dados externas e injetar como contexto para o FM.

### Vantagens
- ✅ Informação sempre atualizada (base é atualizável)
- ✅ Reduz significativamente alucinações
- ✅ Não requer re-treinamento
- ✅ Citações rastreáveis (auditável)
- ✅ Escala com volume de dados

### Limitações
- ❌ Requer infraestrutura de busca (vector database)
- ❌ Qualidade depende da indexação e chunking
- ❌ Adiciona latência (busca + geração)
- ❌ Não muda o estilo/tom do modelo

### Quando usar
- Dados proprietários da empresa
- Informação que muda frequentemente
- Quando alucinações são inaceitáveis
- Base de conhecimento grande (não cabe no prompt)

---

## Fine-tuning

### O que é
Re-treinar parcialmente os pesos do FM com dados específicos para ajustar seu comportamento.

### Vantagens
- ✅ Muda o estilo, tom e formato das respostas
- ✅ Pode aprender vocabulário de domínio
- ✅ Respostas mais consistentes para padrões específicos
- ✅ Não precisa de prompts longos em produção

### Limitações
- ❌ Caro (computação de treinamento)
- ❌ Precisa de dataset de qualidade (pares input/output)
- ❌ Demorado (dias/semanas)
- ❌ Conhecimento pode ficar desatualizado
- ❌ Risco de catastrophic forgetting (perder capacidades gerais)

### Quando usar
- Estilo/tom muito específico que prompt engineering não resolve
- Domínio com jargão e padrões únicos
- Formato de saída altamente padronizado
- Após validar que PE e RAG não são suficientes

---

## Continued Pre-training

### O que é
Treinar o FM com **grandes volumes de texto** do seu domínio (não pares input/output). Ensina vocabulário e conhecimento novo.

### Diferença vs Fine-tuning
| Aspecto | Fine-tuning | Continued Pre-training |
|---------|-------------|----------------------|
| Dados | Pares (pergunta, resposta) | Texto corrido do domínio |
| Objetivo | Mudar comportamento/formato | Ensinar conhecimento novo |
| Volume | Centenas a milhares de exemplos | Milhões de tokens |
| Custo | Alto | Muito alto |

### Quando usar
- Domínio muito especializado (médico, jurídico, científico)
- Terminologia que o modelo base não conhece
- Quando fine-tuning sozinho não é suficiente

---

## Model Distillation (Destilação de Modelo)

### O que é
Treinar um modelo **menor** (student) para imitar o comportamento de um modelo **maior** (teacher), obtendo performance próxima com custo e latência menores.

### Como funciona
1. Modelo grande (teacher) gera outputs de alta qualidade para um conjunto de exemplos
2. Esses outputs são usados como dados de treinamento para o modelo menor (student)
3. Modelo menor aprende a reproduzir o comportamento do maior

### Quando usar
- Modelo grande funciona bem mas é **caro demais** para produção em escala
- Precisa de **latência menor** que o modelo grande oferece
- Volume alto onde o **custo por token** é crítico
- Tarefa específica que não requer capacidade completa do modelo grande

### Trade-offs
| Aspecto | Modelo grande (teacher) | Modelo destilado (student) |
|---------|------------------------|---------------------------|
| Qualidade | 100% | ~90-95% em tarefas específicas |
| Custo por token | Alto | Significativamente menor |
| Latência | Alta | Menor |
| Generalização | Ampla | Mais limitada (focada na tarefa) |

> **DICA PARA A PROVA:** Se a questão descreve "modelo funciona bem mas é caro/lento para produção" + "precisa manter qualidade similar", a resposta é model distillation.

---

## Transfer Learning (Aprendizado por Transferência)

### O que é
Reaproveitar o **conhecimento** que um modelo aprendeu em uma tarefa/domínio para aplicar em outra tarefa/domínio relacionado.

### No contexto de FMs
- Todo fine-tuning de FM é uma forma de transfer learning: o modelo transfere o conhecimento do pré-treinamento para a tarefa específica
- O modelo pré-treinado já "sabe" linguagem, raciocínio, mundo — o fine-tuning transfere isso para o domínio alvo

### Quando reconhecer na prova
- "Aproveitar modelo existente para nova tarefa" → transfer learning
- "Adaptar modelo pré-treinado para domínio específico" → transfer learning (via fine-tuning)
- "Não treinar do zero" → transfer learning

> **DICA PARA A PROVA:** Fine-tuning, continued pre-training e até prompt engineering com few-shot são formas de aproveitar o conhecimento transferido pelo pré-treinamento. Transfer learning é o conceito que embasa todas elas.

---

## Preparação de Dados para Fine-tuning

O Exam Guide exige saber como preparar dados para ajuste fino de um FM.

### Elementos da preparação

| Elemento | Descrição | Por que importa |
|----------|-----------|-----------------|
| **Curadoria de dados** | Selecionar dados de alta qualidade e relevância | Garbage in, garbage out — dados ruins = modelo ruim |
| **Governança** | Garantir conformidade, licenciamento e privacidade dos dados | Dados proprietários de terceiros podem ter restrições legais |
| **Tamanho** | Volume adequado de exemplos (centenas a milhares para fine-tuning) | Pouco dado = underfitting; muito dado de baixa qualidade = ruído |
| **Rotulagem** | Anotação correta dos pares input/output | Rótulos incorretos ensinam o modelo a errar |
| **Representatividade** | Dados devem cobrir a diversidade de cenários reais | Se treinar só com exemplos de um tipo, modelo falha nos outros |
| **RLHF** | Reinforcement Learning from Human Feedback — humanos classificam outputs para alinhar o modelo | Alinha o modelo com preferências humanas (útil, seguro, honesto) |

### Processo típico

```
1. Definir tarefa/comportamento desejado
        ↓
2. Coletar dados representativos (diversidade de cenários)
        ↓
3. Curar e limpar (remover duplicatas, erros, dados sensíveis)
        ↓
4. Formatar (pares input/output no formato esperado pelo modelo)
        ↓
5. Validar qualidade (revisão humana de amostra)
        ↓
6. Dividir (treino/validação)
        ↓
7. Treinar e avaliar
```

### Riscos de preparação inadequada

| Problema nos dados | Consequência no modelo |
|-------------------|----------------------|
| Viés nos exemplos | Modelo reproduz e amplifica vieses |
| Dados desatualizados | Modelo aprende padrões obsoletos |
| PII nos dados | Risco de o modelo memorizar e expor dados pessoais |
| Baixa diversidade | Modelo funciona mal em cenários não representados |
| Formato inconsistente | Modelo gera outputs inconsistentes |

> **DICA PARA A PROVA:** Se a questão menciona "preparar dados para fine-tuning" e uma opção envolve "garantir diversidade e representatividade", essa tende a ser correta. Se menciona "riscos de fine-tuning", pense em viés nos dados e catastrophic forgetting.

---

## Framework de Decisão

```
O modelo base já consegue fazer a tarefa?
├── SIM → Prompt Engineering é suficiente
│
└── NÃO → O problema é falta de dados/conhecimento?
    ├── SIM → RAG (buscar informação externa)
    │   └── Dados mudam frequentemente? → Definitivamente RAG
    │
    └── NÃO → O problema é estilo/formato/comportamento?
        └── SIM → Fine-tuning
            └── O modelo não entende o domínio? → Continued Pre-training + Fine-tuning
```

---

## Cenários de Prova

| Cenário | Resposta |
|---------|----------|
| "Responder perguntas sobre manuais internos atualizados" | RAG |
| "Gerar emails no tom corporativo específico" | Fine-tuning |
| "Resumir um documento fornecido pelo usuário" | Prompt Engineering |
| "Chatbot com FAQ que muda semanalmente" | RAG |
| "Modelo que entende vocabulário jurídico especializado" | Continued Pre-training |
| "Classificar tickets de suporte por categoria" | Prompt Engineering (few-shot) ou Fine-tuning |
| "Responder com dados sempre atualizados do estoque" | RAG |
| "Gerar relatórios médicos com formato padronizado" | Fine-tuning |
| "Primeira tentativa para melhorar qualidade" | Prompt Engineering |

---

## Combinações

Em produção, essas técnicas são frequentemente **combinadas**:

| Combinação | Exemplo |
|-----------|---------|
| PE + RAG | Prompt otimizado + busca em docs (mais comum) |
| Fine-tuning + RAG | Modelo com tom específico + dados atualizados |
| PE + Guardrails | Prompt + filtros de segurança |
| Fine-tuning + Guardrails | Modelo customizado + proteção |

---

## Resumo para a Prova

| Palavra-chave no cenário | Abordagem |
|--------------------------|-----------|
| "Dados atualizados", "muda frequentemente" | RAG |
| "Documentos internos", "base de conhecimento" | RAG |
| "Reduzir alucinações" | RAG |
| "Tom específico", "estilo corporativo" | Fine-tuning |
| "Formato padronizado" | Fine-tuning |
| "Vocabulário especializado", "jargão" | Continued Pre-training |
| "Sem custo adicional", "mais rápido" | Prompt Engineering |
| "Primeiro passo", "abordagem inicial" | Prompt Engineering |
| "Sem re-treinamento" | RAG ou Prompt Engineering |

---

*Próximo bloco: Agents (Bedrock Agents, Lambda, ações)*
