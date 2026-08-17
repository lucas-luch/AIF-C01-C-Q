# Princípios de IA Responsável da AWS

## Visão Geral

A AWS define princípios para uso ético e seguro de IA. A prova AIF-C01 dedica 14% das questões a este tema — foco em identificar problemas e soluções.

---

## Princípios Fundamentais

| Princípio | Descrição |
|-----------|-----------|
| **Fairness (Equidade)** | IA não deve discriminar grupos ou indivíduos |
| **Explainability (Explicabilidade)** | Deve ser possível entender por que o modelo tomou uma decisão |
| **Transparency (Transparência)** | Ser claro sobre o uso de IA e suas limitações |
| **Robustness (Robustez)** | Modelo funciona bem em condições variadas e adversas |
| **Privacy (Privacidade)** | Proteger dados pessoais e sensíveis |
| **Safety (Segurança)** | Prevenir danos e uso malicioso |
| **Governance (Governança)** | Controles organizacionais e processos para IA |

---

## Fairness e Equidade

### O que é viés em IA
Quando o modelo trata grupos de forma desigual ou produz resultados discriminatórios.

### Fontes de viés
| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| Viés nos dados | Dados de treino não-representativos | Sistema treinado só com fotos de pessoas brancas |
| Viés de seleção | Amostragem tendenciosa | Recrutar apenas de universidades de elite |
| Viés de medição | Métricas inadequadas para certos grupos | Teste de crédito baseado em CEP (proxy racial) |
| Viés de automação | Confiar demais no output da IA | Aceitar todas as decisões sem revisar |
| Viés histórico | Dados refletem discriminações passadas | Dados de contratação com viés de gênero |

### Mitigação
- Dados de treino diversos e representativos
- Auditorias regulares de fairness por grupo demográfico
- Métricas de fairness (demographic parity, equalized odds)
- Monitoramento contínuo em produção
- **SageMaker Clarify** — ferramenta da AWS para detectar e medir viés

---

## Explicabilidade e Interpretabilidade

### Diferença
- **Interpretabilidade:** entender COMO o modelo funciona internamente
- **Explicabilidade:** entender POR QUE uma decisão específica foi tomada

### Modelos "caixa-preta" vs interpretáveis
| Tipo | Exemplos | Explicabilidade |
|------|----------|----------------|
| Interpretável | Regressão linear, Árvore de decisão | Alta — fácil ver as regras |
| Caixa-preta | Redes neurais profundas, LLMs | Baixa — precisa de técnicas extras |

### Técnicas de explicabilidade
| Técnica | O que faz |
|---------|-----------|
| **Feature importance** | Quais variáveis mais influenciam as decisões |
| **SHAP values** | Contribuição de cada feature para uma previsão específica |
| **Partial Dependence Plots** | Como uma feature afeta a previsão isoladamente |
| **Counterfactual explanations** | "Se X fosse diferente, a decisão mudaria?" |

### Quando explicabilidade é crítica
- Decisões de crédito (regulamentação)
- Diagnósticos médicos
- Decisões judiciais
- Qualquer decisão que afete direitos de pessoas

### Serviço AWS
- **SageMaker Clarify** — gera explicações (SHAP) e feature importance

---

## Transparência

### AWS AI Service Cards
- Documentação pública de transparência para serviços de IA da AWS
- Cada card descreve:
  - Caso de uso pretendido
  - Limitações conhecidas
  - Métricas de performance e fairness
  - Design choices
  - Melhores práticas de uso

### Práticas de transparência
- Informar usuários que estão interagindo com IA
- Documentar limitações do modelo
- Publicar relatórios de avaliação
- Ser honesto sobre incertezas

---

## Robustez e Segurança

### Robustez
- Modelo funciona bem com dados ruidosos ou adversariais
- Não falha catastroficamente com inputs inesperados
- Performance consistente em diferentes contextos

### Segurança (Safety)
- Prevenir geração de conteúdo prejudicial
- Resistir a prompt injection e jailbreaks
- Human-in-the-loop para decisões críticas
- Guardrails para filtrar outputs indesejados

---

## Resumo para a Prova

| Conceito | Ferramenta/Abordagem AWS |
|----------|--------------------------|
| Detectar viés em dados | SageMaker Clarify (pre-training bias) |
| Detectar viés em modelos | SageMaker Clarify (post-training bias) |
| Detectar viés em texto gerado (GenAI) | SageMaker Clarify (toxicity/bias em FMs) |
| Explicar previsões | SageMaker Clarify (SHAP values) |
| Filtrar conteúdo perigoso | Bedrock Guardrails |
| Transparência sobre serviços | AWS AI Service Cards |
| Revisão humana | Amazon Augmented AI (A2I) |
| Monitorar fairness em produção | SageMaker Model Monitor |

---

## Cenários de Prova — Como Aparecem

| Cenário descrito | O que estão testando | Resposta |
|-----------------|---------------------|----------|
| "Regulador exige justificar negativa de crédito ao cliente" | Explicabilidade individual | SageMaker Clarify → SHAP values |
| "Modelo de RH aprova mais homens que mulheres para promoção" | Viés pós-treinamento por subgrupo | SageMaker Clarify (post-training bias) |
| "Chatbot gerou resposta com estereótipos raciais" | Conteúdo tóxico em GenAI | Bedrock Guardrails (content filter) + Red teaming preventivo |
| "Empresa quer publicar limitações do modelo para clientes" | Transparência | AI Service Cards (serviços AWS) ou Model Cards (modelo próprio) |
| "Modelo de diagnóstico com 70% de confiança — precisa de médico" | Human-in-the-loop | Amazon A2I com threshold de confiança |
| "LLM inventa referências bibliográficas" | Alucinação | RAG + Guardrails (grounding check) |
| "Modelo treinado só com dados de SP funciona mal em Manaus" | Viés de seleção | Coletar dados representativos de todas as regiões |

---

*Próximo bloco: Viés em IA e mitigação*
