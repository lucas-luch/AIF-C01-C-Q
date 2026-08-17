# Questões — Foundation Models e LLMs

---

### Questão 1

Qual das seguintes afirmações descreve melhor um Foundation Model?

A) Um modelo treinado exclusivamente para uma única tarefa específica  
B) Um modelo de grande escala pré-treinado que pode ser adaptado para múltiplas tarefas  
C) Um modelo que requer dados rotulados específicos para cada tarefa que executa  
D) Um modelo que só funciona com dados de texto  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Um modelo de grande escala pré-treinado que pode ser adaptado para múltiplas tarefas**

✅ **Por que B está correta:** Foundation Models são pré-treinados em enormes quantidades de dados e podem ser adaptados (via prompt engineering, fine-tuning ou RAG) para diversas tarefas sem treinar do zero.

❌ **Por que as outras estão erradas:**
- **A)** O oposto — FMs são multi-propósito, não single-task.
- **C)** FMs são pré-treinados com aprendizado auto-supervisionado, não requerem dados rotulados para cada tarefa.
- **D)** FMs podem ser de texto, imagem, multimodal — não apenas texto.

</details>

---

### Questão 2

Qual é a principal diferença entre ML tradicional e IA Generativa?

A) ML tradicional é mais caro que IA Generativa  
B) ML tradicional produz saídas estruturadas (classe, valor); IA Generativa cria conteúdo novo não-estruturado  
C) IA Generativa não requer dados para treinamento  
D) ML tradicional não pode ser usado na AWS  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) ML tradicional produz saídas estruturadas (classe, valor); IA Generativa cria conteúdo novo não-estruturado**

✅ **Por que B está correta:** ML tradicional prediz, classifica ou agrupa (saída estruturada: sim/não, 42.5, cluster A). IA Generativa cria conteúdo novo: texto, imagens, código, áudio (saída não-estruturada).

❌ **Por que as outras estão erradas:**
- **A)** Custo depende do caso — não é uma distinção fundamental.
- **C)** IA Generativa requer enormes volumes de dados para pré-treinamento.
- **D)** Falso — SageMaker é a plataforma de ML tradicional na AWS.

</details>

---

### Questão 3

Uma empresa quer usar um Foundation Model para gerar conteúdo de marketing em um tom específico da marca. O modelo base não captura esse tom. Qual abordagem é mais adequada?

A) Usar prompt engineering com zero-shot  
B) Fazer fine-tuning do modelo com exemplos no tom desejado  
C) Usar RAG com documentos de marketing antigos  
D) Aumentar a temperature para mais criatividade  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Fazer fine-tuning do modelo com exemplos no tom desejado**

✅ **Por que B está correta:** Fine-tuning é a abordagem ideal quando o modelo precisa adotar um estilo/tom consistente que não consegue manter apenas com prompts. Ajusta os pesos do modelo para esse comportamento.

❌ **Por que as outras estão erradas:**
- **A)** Zero-shot sem exemplos dificilmente captura um tom de marca específico.
- **C)** RAG traz informação factual, mas não muda o estilo de escrita do modelo.
- **D)** Temperature aumenta aleatoriedade, não direciona para um tom específico.

</details>

---

### Questão 4

O que significa um modelo ser "open-weight"?

A) O modelo é gratuito para qualquer uso comercial sem restrições  
B) Os pesos treinados do modelo estão disponíveis para download e execução em sua própria infraestrutura  
C) O modelo permite que qualquer pessoa modifique seu código-fonte  
D) O modelo pode ser acessado apenas via API pública  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Os pesos treinados do modelo estão disponíveis para download e execução em sua própria infraestrutura**

✅ **Por que B está correta:** Open-weight significa que os pesos (parâmetros aprendidos) estão disponíveis publicamente. Você pode baixar e rodar em sua infraestrutura. Exemplos: Llama (Meta), Mistral.

❌ **Por que as outras estão erradas:**
- **A)** Open-weight não significa sem restrições de licença — cada modelo tem sua licença (pode ter restrições comerciais).
- **C)** Open-weight refere-se aos pesos treinados, não ao código de treinamento (que seria open-source).
- **D)** Isso descreve modelos proprietários (como GPT via API) — o oposto de open-weight.

</details>

---

### Questão 5

Qual processo é usado para alinhar LLMs com preferências humanas, tornando-os mais úteis e seguros?

A) Transfer Learning  
B) Continued Pre-training  
C) RLHF (Reinforcement Learning from Human Feedback)  
D) Data Augmentation  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) RLHF (Reinforcement Learning from Human Feedback)**

✅ **Por que C está correta:** RLHF usa feedback humano para treinar um modelo de recompensa, que então guia o LLM a gerar respostas mais alinhadas com preferências humanas (úteis, verdadeiras, inofensivas).

❌ **Por que as outras estão erradas:**
- **A)** Transfer learning é reaproveitar conhecimento de um modelo em outra tarefa — conceito geral, não específico de alinhamento.
- **B)** Continued pre-training ensina conhecimento novo, não alinha com preferências.
- **D)** Data augmentation aumenta a variedade dos dados de treino, não alinha respostas.

</details>

---

### Questão 6 (Múltipla Resposta)

Quais são características de Large Language Models (LLMs)? **(Selecione DUAS)**

A) Requerem dados rotulados específicos para cada tarefa  
B) São treinados em grandes corpora de texto usando aprendizado auto-supervisionado  
C) Podem realizar múltiplas tarefas como geração, resumo e tradução  
D) Funcionam apenas com dados em inglês  
E) Precisam ser re-treinados do zero para cada novo caso de uso  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: B e C**

✅ **Por que B está correta:** LLMs são pré-treinados com self-supervised learning (ex: prever próximo token) em enormes volumes de texto sem necessidade de rotulagem humana.

✅ **Por que C está correta:** LLMs são multi-tarefa — um único modelo pode gerar texto, resumir, traduzir, programar, raciocinar, sem treino específico para cada tarefa.

❌ **Por que as outras estão erradas:**
- **A)** LLMs são pré-treinados sem rótulos (auto-supervisionado). Podem ser adaptados com prompt engineering.
- **D)** LLMs modernos são multilíngues (treinados em texto de múltiplos idiomas).
- **E)** Adaptáveis via prompt engineering ou fine-tuning — não precisa re-treinar do zero.

</details>

