# Princípios de IA Responsável

## Visão Geral

A prova AIF-C01 dedica 14% das questões a IA responsável. O Exam Guide exige identificar **características de IA responsável**, **riscos legais**, **práticas de escolha de modelo** e **características de datasets**.

---

## Características de IA Responsável

O Exam Guide lista explicitamente estas características:

| Característica | Descrição |
|---------------|-----------|
| **Fairness (Equidade/Imparcialidade)** | IA não deve discriminar grupos ou indivíduos. Resultados devem ser equitativos independente de raça, gênero, idade, etc. |
| **Inclusão (Inclusivity)** | Sistemas de IA devem funcionar para todos os usuários, incluindo pessoas de diferentes origens, habilidades, idiomas e contextos. |
| **Robustez (Robustness)** | Modelo funciona bem em condições variadas, dados ruidosos e cenários adversariais. Não falha catastroficamente. |
| **Segurança (Safety)** | Prevenir danos. Sistema não deve gerar conteúdo prejudicial nem ser usado para causar dano. |
| **Veracidade (Veracity)** | Outputs devem ser factualmente corretos e confiáveis. O sistema não deve inventar ou distorcer informação. |
| **Transparência (Transparency)** | Ser claro sobre o uso de IA, suas capacidades e limitações. Usuários devem saber quando interagem com IA. |
| **Explicabilidade (Explainability)** | Deve ser possível entender por que o modelo tomou determinada decisão. |
| **Privacidade (Privacy)** | Proteger dados pessoais e sensíveis. Minimizar coleta e uso de dados. |

> **DICA PARA A PROVA:** O Exam Guide usa os termos "viés, imparcialidade, inclusão, robustez, segurança e veracidade" juntos. Saiba diferenciá-los — imparcialidade é sobre equidade entre grupos; inclusão é sobre acessibilidade a todos; veracidade é sobre correção factual.

---

## Sustentabilidade e Impacto Ambiental

O Exam Guide exige reconhecer **considerações ambientais e sustentabilidade** como práticas responsáveis na escolha de modelos.

### Por que é relevante

| Aspecto | Impacto |
|---------|---------|
| **Treinamento de FMs** | Consome enormes quantidades de energia (GPUs por semanas/meses) |
| **Inferência** | Cada requisição consome recursos computacionais |
| **Modelos maiores** | Mais parâmetros = mais energia por inferência |
| **Escala** | Milhões de requisições/dia = impacto ambiental significativo |

### Práticas responsáveis

| Prática | Como reduz impacto |
|---------|-------------------|
| **Usar modelo menor quando suficiente** | Menos energia por inferência |
| **Model distillation** | Modelo menor com performance similar ao grande |
| **Prompt caching** | Evita reprocessamento de tokens repetidos |
| **Batch inference** | Otimiza uso de recursos (agrupa processamentos) |
| **Escolher região com energia limpa** | Algumas regiões AWS usam mais energia renovável |
| **Reutilizar modelos pré-treinados** | Evita custo ambiental de treinar do zero |

> **DICA PARA A PROVA:** Se a questão menciona "considerações ambientais" ou "sustentabilidade" na escolha de modelo, a resposta envolve: usar modelo menor quando possível, evitar treinar do zero sem necessidade, e otimizar inferência.

---

## Riscos Legais de Trabalhar com IA Generativa

O Exam Guide exige identificar riscos legais específicos.

| Risco legal | Descrição | Exemplo |
|-------------|-----------|---------|
| **Violação de Propriedade Intelectual (IP)** | Modelo gera conteúdo que replica material protegido por copyright | LLM gera trecho de livro, código proprietário, ou imagem que replica obra de artista |
| **Resultados tendenciosos (outputs com viés)** | Decisões automatizadas discriminam grupos protegidos | Sistema de crédito que nega mais a minorias, recrutamento que favorece um gênero |
| **Perda de confiança do cliente** | Outputs incorretos, ofensivos ou inadequados danificam reputação | Chatbot que ofende clientes, sistema que dá informação falsa sobre saúde |
| **Risco do usuário final** | Outputs incorretos levam o usuário a ações prejudiciais | Informação médica incorreta, conselho financeiro errado, instruções perigosas |
| **Alucinações** | Modelo gera informação factualmente incorreta apresentada como verdade | Inventar referências, citar leis inexistentes, fabricar dados |

### Mitigação de riscos legais

| Risco | Mitigação |
|-------|-----------|
| Violação de IP | Guardrails, filtros de output, políticas de uso, disclaimers |
| Viés/discriminação | SageMaker Clarify, auditorias de fairness, dados diversos |
| Perda de confiança | Guardrails, testes extensivos, monitoring, human-in-the-loop |
| Risco ao usuário | Disclaimers, human review para decisões críticas, limitação de escopo |
| Alucinações | RAG, grounding check, Guardrails, confidence scoring |

> **CUIDADO:** Estes riscos existem mesmo quando o modelo é "bom" — são riscos inerentes ao uso de IA generativa e devem ser gerenciados, não eliminados por completo.

---

## Características de Datasets para IA Responsável

O Exam Guide exige identificar características de datasets que suportam IA responsável.

| Característica | Descrição | Por que importa |
|---------------|-----------|-----------------|
| **Inclusão** | Dataset contém representação de diferentes grupos (gênero, raça, idade, região, idioma) | Modelo treinado em dados inclusivos funciona melhor para todos |
| **Diversidade** | Variedade de cenários, contextos e condições nos dados | Evita que o modelo só funcione em um contexto estreito |
| **Fontes com curadoria** | Dados vêm de fontes confiáveis e foram revisados | Reduz risco de dados incorretos, tendenciosos ou tóxicos contaminarem o modelo |
| **Datasets balanceados** | Representação equilibrada entre classes/grupos | Evita que modelo favoreça grupo majoritário |

### Problemas de datasets inadequados

| Problema no dataset | Consequência no modelo |
|--------------------|----------------------|
| Sub-representação de grupo | Modelo performa mal para esse grupo |
| Dados históricos com viés | Modelo reproduz e amplifica discriminação histórica |
| Fontes não-curadas | Modelo pode aprender desinformação ou conteúdo tóxico |
| Desbalanceamento extremo | Modelo ignora classe minoritária (prevê sempre a majoritária) |
| Falta de diversidade regional/cultural | Modelo funciona apenas em um contexto específico |

> **DICA PARA A PROVA:** Se a questão descreve "modelo funciona mal para um grupo demográfico específico", o problema geralmente é falta de representação/diversidade nos dados de treino.

---

## Ferramentas AWS para IA Responsável

| Ferramenta | O que faz | Quando usar |
|-----------|-----------|-------------|
| **SageMaker Clarify** | Detecta viés (pre/post training), explica previsões (SHAP) | Análise de fairness, explicabilidade |
| **SageMaker Model Monitor** | Monitora drift, qualidade e fairness em produção | Monitoramento contínuo pós-deploy |
| **Amazon A2I** | Human-in-the-loop (revisão humana) | Decisões críticas, baixa confiança |
| **Bedrock Guardrails** | Filtros de conteúdo, PII, grounding | Segurança de outputs de FMs |
| **SageMaker Model Cards** | Documentar modelos (uso pretendido, limitações, métricas) | Governança de modelos customizados |
| **AWS AI Service Cards** | Transparência de serviços de IA da AWS | Entender limitações/fairness de serviços AWS |
| **Bedrock Model Evaluation** | Avaliar modelos em métricas de qualidade e segurança | Comparar modelos, avaliar safety/bias |

---

## Resumo para a Prova

| Cenário | Resposta |
|---------|----------|
| "Modelo discrimina um grupo demográfico" | Viés → SageMaker Clarify (detectar) + dados diversos (mitigar) |
| "Regulador exige justificar decisão ao cliente" | Explicabilidade → SageMaker Clarify (SHAP values) |
| "Chatbot gera conteúdo ofensivo" | Segurança → Bedrock Guardrails |
| "LLM inventa informações" | Veracidade → RAG + Guardrails grounding check |
| "Modelo gera texto com copyright" | Risco de IP → Guardrails + políticas + disclaimers |
| "Escolher modelo com menor impacto ambiental" | Sustentabilidade → modelo menor, distillation, caching |
| "Dataset não representa minorias" | Inclusão/diversidade → coletar dados representativos |
| "Modelo funciona mal para certo idioma" | Inclusão → treinar/avaliar com dados multilíngues |
| "Monitorar fairness após deploy" | SageMaker Model Monitor |
| "Documentar limitações do modelo" | SageMaker Model Cards / AI Service Cards |

---
