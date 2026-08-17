# Agents (Agentes)

## Visão Geral

Agents são Foundation Models que vão além de gerar texto — eles **planejam, decidem e executam ações** em sistemas reais. É um conceito em crescimento na prova AIF-C01.

---

## O que são AI Agents?

Um Agent é um FM equipado com **ferramentas** (tools) que pode:
- Raciocinar sobre um problema
- Decidir quais ações tomar
- Executar ações (chamar APIs, consultar DBs, rodar código)
- Observar o resultado
- Iterar até completar a tarefa

### Diferença: FM puro vs Agent

| Aspecto | FM (só geração) | Agent |
|---------|----------------|-------|
| Saída | Apenas texto | Texto + ações executadas |
| Interação | Single-turn ou multi-turn | Multi-step com ferramentas |
| Acesso a dados | Apenas o que está no prompt | Pode buscar em sistemas reais |
| Ações | Nenhuma | Chamadas de API, Lambda, DB |
| Exemplo | "Qual o status do pedido?" → resposta inventada | "Qual o status do pedido?" → consulta sistema → resposta real |

---

## Bedrock Agents

### Componentes

| Componente | Função |
|-----------|--------|
| **Foundation Model** | Cérebro do agent — raciocina e decide |
| **Instructions** | Regras e persona do agent (system prompt) |
| **Action Groups** | Conjunto de ações disponíveis (Lambda functions, APIs) |
| **Knowledge Bases** | Fontes de informação consultáveis (RAG) |
| **Session** | Contexto da conversa mantido entre turnos |

### Action Groups
- Definem **o que** o agent pode fazer
- Cada action group tem:
  - Descrição (para o FM entender quando usar)
  - API schema (OpenAPI) ou Lambda function
  - Parâmetros necessários

### Fluxo de Execução (ReAct Pattern)
```
1. Usuário: "Cancele meu pedido #12345"
2. Agent RACIOCINA: "Preciso buscar o pedido e depois cancelar"
3. Agent DECIDE ação: chamar API GetOrder(id=12345)
4. EXECUTA: Lambda retorna dados do pedido
5. Agent OBSERVA: "Pedido existe, status=enviado"
6. Agent RACIOCINA: "Não posso cancelar pedido já enviado"
7. Agent RESPONDE: "Seu pedido #12345 já foi enviado e não pode ser cancelado. Posso ajudar com uma devolução?"
```

---

## Casos de Uso

| Caso | O que o Agent faz |
|------|-------------------|
| Atendimento ao cliente | Consulta pedidos, processa devoluções, atualiza dados |
| Assistente de vendas | Consulta estoque, calcula preços, gera propostas |
| Pesquisa | Busca em múltiplas fontes, sintetiza informação |
| Automação de processos | Preenche formulários, dispara workflows |
| DevOps | Consulta logs, identifica problemas, sugere soluções |

---

## Agent vs RAG vs Chatbot Simples

| Capacidade | Chatbot simples | RAG | Agent |
|-----------|----------------|-----|-------|
| Gerar texto | ✅ | ✅ | ✅ |
| Buscar em docs | ❌ | ✅ | ✅ |
| Executar ações | ❌ | ❌ | ✅ |
| Raciocínio multi-step | ❌ | ❌ | ✅ |
| Integrar com sistemas | ❌ | ❌ | ✅ |
| Manter estado entre turnos | Limitado | Limitado | ✅ |

---

## Serviços AWS Envolvidos

| Serviço | Papel no contexto de Agents |
|---------|----------------------------|
| **Amazon Bedrock Agents** | Orquestração do agent |
| **AWS Lambda** | Execução das ações (backend das tools) |
| **Bedrock Knowledge Bases** | Informação consultável pelo agent |
| **Amazon S3** | Armazenamento de dados/documentos |
| **API Gateway** | Expor o agent como API |
| **CloudWatch** | Logs e monitoramento do agent |

---

## Resumo para a Prova

| Conceito | O que lembrar |
|----------|---------------|
| Agent | FM + ferramentas + raciocínio + execução de ações |
| Action Group | Conjunto de ações que o agent pode executar |
| ReAct | Pattern: Reason → Act → Observe → Repeat |
| Knowledge Base | Fonte de dados consultável (RAG integrado) |
| Lambda | Executa as ações do agent no backend |
| Diferença de RAG | RAG só busca info; Agent busca info E executa ações |
| Quando usar Agent | Precisa interagir com sistemas (não apenas informar) |

---

*Próximo bloco: Casos de uso empresariais e otimização*
