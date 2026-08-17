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
