# Known Pitfalls — Erros Conceituais Comuns (AIF-C01)

*Última atualização: 2026-08-22*

Este arquivo documenta erros conceituais e confusões comuns que podem levar a respostas erradas na prova AIF-C01. Todos os pitfalls são tecnicamente validados.

---

## 1. RAG e Alucinações

❌ **ERRADO:** "RAG garante que o modelo não vai alucinar."

✅ **CORRETO:** RAG **reduz significativamente** alucinações ao fornecer contexto factual, mas **não elimina** por completo. O modelo pode ignorar o contexto fornecido, interpretar incorretamente, ou extrapolar além do que está nos documentos. Complementar com Guardrails (grounding check) e validação de output.

---

## 2. Agent vs FM com Tools

❌ **ERRADO:** "Um Agent é simplesmente um Foundation Model com ferramentas (tools)."

✅ **CORRETO:** Um Agent é um **sistema** que utiliza um FM como componente de raciocínio, combinado com **planejamento, memória, ferramentas e orquestração**. O FM sozinho gera texto — o agente planeja, decide, executa e itera até completar uma tarefa.

---

## 3. Serverless Inference vs Lambda

❌ **ERRADO:** "Serverless inference é basicamente Lambda."

✅ **CORRETO:** SageMaker Serverless Inference é uma **modalidade de endpoint gerenciada** que escala automaticamente (incluindo para zero) sem infraestrutura provisionada. É um conceito diferente de AWS Lambda — são serviços distintos com propósitos diferentes, embora ambos sejam "serverless".

---

## 4. Top-P e Aleatoriedade

❌ **ERRADO:** "Top-P mais alto = mais aleatoriedade sempre."

✅ **CORRETO:** O efeito de Top-P depende da distribuição de probabilidade. Se o modelo está muito confiante em um token (ex: 95% de probabilidade), mesmo Top-P = 0.99 resultará em output focado. Top-P controla o pool de candidatos, não a aleatoriedade diretamente — essa é mais controlada pela temperature.

---

## 5. Fine-tuning vs RAG para Dados Atualizados

❌ **ERRADO:** "Fine-tuning é a melhor forma de ensinar dados novos ao modelo."

✅ **CORRETO:** Fine-tuning muda **comportamento/estilo** do modelo, não é ideal para dados que mudam frequentemente. Para dados atualizados/proprietários, **RAG** é geralmente mais apropriado — atualiza a base sem retreinar o modelo. Fine-tuning é estático: dados novos exigem novo fine-tuning.

---

## 6. LGPD e Residência de Dados

❌ **ERRADO:** "LGPD obriga que dados de brasileiros fiquem armazenados no Brasil."

✅ **CORRETO:** A LGPD **não exige** que dados sejam armazenados no Brasil. Exige **proteção adequada** dos dados pessoais, independentemente de onde estejam. Transferências internacionais são permitidas sob condições (país com nível adequado de proteção, cláusulas contratuais, consentimento). Manter dados no Brasil (sa-east-1) é decisão de negócio, não imposição legal absoluta.

---

## 7. Guardrails vs System Prompt

❌ **ERRADO:** "Guardrails substitui o system prompt."

✅ **CORRETO:** Guardrails é uma **camada adicional** de proteção, não substituto do system prompt. System prompt define o comportamento desejado do modelo; Guardrails **bloqueia** violações independentemente do que o prompt diz. Ambos devem ser usados juntos — system prompts podem ser contornados via prompt injection, Guardrails atua como camada independente.

---

## 8. Modelo Maior = Sempre Melhor

❌ **ERRADO:** "Para obter a melhor qualidade, sempre use o modelo maior disponível."

✅ **CORRETO:** Modelos maiores são mais capazes mas também mais caros e lentos. Se a tarefa é simples (classificação, extração), um modelo menor pode atender igualmente com **menor custo e latência**. A escolha deve considerar a complexidade da tarefa, não apenas maximizar tamanho.

---

## 9. Bedrock é o Único Serviço para FMs

❌ **ERRADO:** "Para usar Foundation Models na AWS, precisa usar Amazon Bedrock."

✅ **CORRETO:** Bedrock é o serviço **serverless** para acessar FMs via API. Mas também é possível usar **SageMaker JumpStart** para deployar modelos open-source na sua conta (com controle total da infra) ou até deployar modelos em EC2/ECS diretamente. Bedrock é a opção mais simples mas não a única.

---

## 10. Acurácia como Métrica Universal

❌ **ERRADO:** "Acurácia alta = modelo bom."

✅ **CORRETO:** Em datasets **desbalanceados**, acurácia é enganosa. Ex: se 99% das transações são legítimas, um modelo que sempre diz "legítima" tem 99% de acurácia mas é inútil para detectar fraude. Para dados desbalanceados, use **F1 Score, AUC-ROC ou métricas por classe**.

---

## 11. Amazon SageMaker vs Amazon SageMaker AI

❌ **ERRADO:** Referir ao serviço como "Amazon SageMaker" (nome antigo).

✅ **CORRETO:** O nome atual do serviço é **Amazon SageMaker AI**. Features individuais mantêm seus nomes (SageMaker Clarify, SageMaker Pipelines, SageMaker Model Monitor, etc.), mas o serviço como um todo agora é "Amazon SageMaker AI".

---

## 12. MCP é Exclusivo do Bedrock

❌ **ERRADO:** "MCP (Model Context Protocol) é uma feature do Amazon Bedrock."

✅ **CORRETO:** MCP é um **protocolo aberto** (criado pela Anthropic) que padroniza como agentes se conectam a sistemas externos. Não é exclusivo de nenhum provedor — funciona com qualquer agente/IDE compatível (Kiro, Claude, etc.). Na AWS, é usado pelo Kiro IDE e pode ser utilizado por agentes construídos com Strands Agents.

---

## 13. Knowledge Bases = Busca Simples

❌ **ERRADO:** "Knowledge Bases for Amazon Bedrock é basicamente um mecanismo de busca."

✅ **CORRETO:** Knowledge Bases implementa **RAG completo**: chunking de documentos → embedding → armazenamento vetorial → busca semântica → injeção no contexto do FM → geração com citações. É muito mais que busca — inclui geração de resposta fundamentada. Para busca apenas (retornar documentos), use Amazon Kendra.

---

## 14. Todos os Dados de Treino de LLMs São Públicos

❌ **ERRADO:** "LLMs são treinados apenas com dados públicos, então não há risco de copyright."

✅ **CORRETO:** Os dados de pré-treinamento de muitos LLMs incluem conteúdo da internet que pode estar protegido por copyright. Existe risco real de **violação de propriedade intelectual** quando o modelo reproduz trechos de material protegido. Este é um dos riscos legais que o Exam Guide cita explicitamente.

---

## 15. Avaliação de Modelo = Avaliação da Aplicação

❌ **ERRADO:** "Se o modelo teve boa performance nos benchmarks, a aplicação vai funcionar bem."

✅ **CORRETO:** Avaliar o **modelo** (BLEU, ROUGE, BERTScore) é diferente de avaliar a **aplicação** (RAG, agents, workflows). Uma aplicação tem múltiplos componentes (retrieval, geração, pós-processamento, UX) — problemas em qualquer um afetam o resultado final. Métricas de aplicação incluem: task completion rate, user satisfaction, groundedness.

---

## Uso deste Arquivo

- Revisar antes da prova como checklist de "armadilhas"
- Se encontrar um conceito que contradiga algo aqui, verificar na documentação oficial
- Este arquivo NÃO substitui o estudo completo — é um complemento

---
