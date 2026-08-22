# Agents — Implementação e Serviços AWS

## Visão Geral

Agents são sistemas de IA que vão além de gerar texto — eles **planejam, decidem e executam ações** em sistemas reais. Este bloco foca na **implementação prática** com serviços AWS.

*(Para conceitos fundamentais de IA agêntica — definição, componentes, MCP, multiagente, memória, orquestração — ver D2 C-01.)*

---

## O que é um Agente de IA (Resumo)

Um sistema que combina um foundation model com capacidades de:
- **Planejamento** — decompor tarefas complexas em etapas
- **Raciocínio** — decidir qual ação tomar a cada etapa
- **Uso de ferramentas** — invocar APIs, consultar bancos, executar código
- **Memória** — manter contexto entre interações
- **Orquestração** — coordenar execução até completar a tarefa

> **CUIDADO:** Um agente NÃO é simplesmente "um FM com tools". É um **sistema** que usa o FM como componente de raciocínio, combinado com ferramentas, memória e lógica de orquestração. O FM sozinho gera texto — o agente executa tarefas.

---

## Agent vs RAG vs Chatbot Simples

| Capacidade | Chatbot simples | RAG | Agent |
|-----------|----------------|-----|-------|
| Gerar texto | ✅ | ✅ | ✅ |
| Buscar em docs | ❌ | ✅ | ✅ |
| Executar ações | ❌ | ❌ | ✅ |
| Raciocínio multi-step | ❌ | ❌ | ✅ |
| Integrar com sistemas | ❌ | ❌ | ✅ |

**Regra simples:** Se a aplicação precisa apenas **informar** → RAG. Se precisa **agir** (executar, modificar, criar) → Agent.

---

## Agentes do Amazon Bedrock

Serviço gerenciado para criar agentes que executam ações usando FMs.

### Componentes

| Componente | Função |
|-----------|--------|
| **Foundation Model** | Cérebro — raciocina e decide ações |
| **Instructions** | System prompt com regras e persona do agent |
| **Action Groups** | Conjunto de ações executáveis (Lambda functions, APIs) |
| **Knowledge Bases** | Fontes de informação consultáveis (RAG integrado) |
| **Session** | Contexto da conversa mantido entre turnos |
| **Guardrails** | Filtros de segurança aplicados ao agent |

### Action Groups
- Definem **o que** o agent pode fazer
- Cada action group tem:
  - Descrição (para o FM entender quando usar)
  - API schema (OpenAPI) ou Lambda function
  - Parâmetros necessários

### Fluxo de Execução (ReAct Pattern)
```
1. Usuário: "Cancele meu pedido #12345"
2. Agent RACIOCINA: "Preciso buscar o pedido e verificar status"
3. Agent DECIDE ação: chamar GetOrder(id=12345)
4. EXECUTA: Lambda retorna dados do pedido
5. Agent OBSERVA: "Pedido existe, status=enviado"
6. Agent RACIOCINA: "Não posso cancelar pedido já enviado"
7. Agent RESPONDE: "Seu pedido já foi enviado. Posso ajudar com uma devolução?"
```

### Quando usar Bedrock Agents
- Precisa de agente **gerenciado** (sem construir orquestração)
- Integração com ecossistema Bedrock (Knowledge Bases, Guardrails)
- Ações via Lambda/API
- Ambiente enterprise com governança AWS nativa

---

## Strands Agents

Framework **open-source** da AWS para construir agentes de IA com controle total.

| Aspecto | Bedrock Agents | Strands Agents |
|---------|---------------|----------------|
| **Tipo** | Serviço gerenciado | Framework/SDK open-source |
| **Controle** | Limitado ao que o serviço oferece | Total (código customizado) |
| **Infraestrutura** | AWS gerencia | Você gerencia |
| **Customização** | Via configuração | Via código |
| **Quando usar** | Quer simplicidade e integração Bedrock | Precisa de controle total, lógica complexa |

---

## Amazon Bedrock AgentCore

Infraestrutura gerenciada para **deploy, segurança e governança** de agentes em produção.

*(Detalhes dos componentes no D2 C-05. Resumo contextualizado:)*

| Componente | Função para Agents em produção |
|-----------|-------------------------------|
| **Runtime** | Ambiente de execução gerenciado |
| **Identity** | Autenticação e identidade do agente (quem o agente "é") |
| **Gateway** | Ponto de entrada e roteamento |
| **Memory** | Memória de curto e longo prazo gerenciada |
| **Observability** | Monitoramento, logging e tracing |
| **Policy** | Regras sobre o que o agente pode/não pode fazer |

### Quando usar AgentCore
- Agentes em produção que precisam de **segurança enterprise**
- Controle de **o que o agente pode acessar/fazer** (Policy)
- **Auditoria** de ações do agente (Observability)
- Gerenciamento de **identidade** do agente em diferentes sistemas (Identity)

> **DICA PARA A PROVA:** "Criar um agente que executa ações" → Agentes do Amazon Bedrock. "Garantir segurança e governança de agentes em produção" → Amazon Bedrock AgentCore. "Construir agente customizado com código" → Strands Agents.

---

## Model Context Protocol (MCP) na Prática

*(Conceitos fundamentais de MCP no D2 C-01. Aqui: aplicação prática.)*

MCP padroniza como agentes se conectam a ferramentas e dados externos.

### Papel no ecossistema de agentes AWS

| Sem MCP | Com MCP |
|---------|---------|
| Cada integração é código customizado | Interface padrão para todas as ferramentas |
| Mudança de ferramenta = reescrever integração | Trocar ferramenta = apontar para outro MCP server |
| Difícil compartilhar integrações | Integrações reutilizáveis entre projetos |

### Exemplo prático
- Kiro (IDE) usa MCP para conectar-se a ferramentas externas (documentação AWS, Git, etc.)
- Agentes podem usar MCP servers para acessar bancos de dados, APIs, arquivos
- Um MCP server de documentação AWS permite que qualquer agente compatível consulte docs oficiais

---

## Serviços AWS no Contexto de Agents

| Serviço | Papel |
|---------|-------|
| **Agentes do Amazon Bedrock** | Criar e orquestrar agents (gerenciado) |
| **Amazon Bedrock AgentCore** | Segurança, identidade e governança de agents |
| **Strands Agents** | Framework open-source para agents customizados |
| **AWS Lambda** | Backend das tools/ações do agent |
| **Bedrock Knowledge Bases** | RAG — informação consultável pelo agent |
| **Bedrock Guardrails** | Segurança e filtros para o agent |
| **Amazon S3** | Armazenamento de dados/documentos |
| **Amazon CloudWatch** | Logs e monitoramento |
| **Kiro** | IDE com IA que usa MCP para conectar ferramentas |

---

## Resumo para a Prova

| Cenário | Solução |
|---------|---------|
| "FM que executa ações em sistemas" | Agentes do Amazon Bedrock |
| "Segurança e governança de agentes em produção" | Amazon Bedrock AgentCore |
| "Construir agente com controle total do código" | Strands Agents |
| "Conectar agente a ferramentas de forma padronizada" | MCP (Model Context Protocol) |
| "Agent precisa consultar documentos antes de agir" | Bedrock Agent + Knowledge Bases |
| "Apenas responder perguntas com docs internos" | Knowledge Bases (RAG) — agent não necessário |
| "Limitar o que o agent pode fazer" | AgentCore Policy + Guardrails |
| "Monitorar ações do agent" | AgentCore Observability + CloudWatch |

---
