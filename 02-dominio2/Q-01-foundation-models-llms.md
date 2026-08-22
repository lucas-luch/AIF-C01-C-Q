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



---

### Questão 7

Uma empresa quer usar um Foundation Model para seu produto SaaS. O CTO precisa escolher entre um modelo proprietário via API (como Claude via Bedrock) e um modelo open-weight (como Llama). O principal requisito é manter controle total sobre onde os dados são processados e poder customizar o modelo internamente sem depender de terceiros. Qual opção é MAIS alinhada com esses requisitos?

A) Modelo proprietário via API — mais fácil de implementar e manter  
B) Modelo open-weight — permite execução em infraestrutura própria com controle total sobre dados e customização  
C) Treinar um modelo do zero — única forma de ter controle total  
D) Usar PartyRock — gratuito e sem dependência de API  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) Modelo open-weight — permite execução em infraestrutura própria com controle total sobre dados e customização**

✅ **Por que B está correta:** Open-weight (Llama, Mistral) permite baixar os pesos e executar onde quiser (sua VPC, on-premises, edge). Controle total sobre dados (não saem da sua infra) e customização (fine-tuning sem depender do provedor).

❌ **Por que as outras estão erradas:**
- **A)** API proprietária envia dados para infraestrutura de terceiros — menos controle sobre processamento.
- **C)** Treinar do zero é possível mas impraticável (custo de milhões de dólares, meses de treino). Open-weight atende sem esse custo.
- **D)** PartyRock é playground gratuito sem qualquer controle empresarial — não é para produção.

</details>

---

### Questão 8

Uma equipe está avaliando Foundation Models para um assistente de código. O requisito principal é que o modelo gere código funcional em Python, Java e TypeScript com capacidade de entender e completar código existente. Quais características tornam um FM adequado para essa tarefa? **(Selecione DUAS)**

A) O modelo foi pré-treinado com grandes volumes de código-fonte nessas linguagens  
B) O modelo tem a menor context window possível para focar nas instruções  
C) O modelo suporta geração autoregressiva token por token  
D) O modelo usa apenas encoder (como BERT) para melhor compreensão  
E) O modelo foi treinado exclusivamente em texto em inglês  

<details>
<summary>🔍 Ver resposta</summary>

**Respostas: A e C**

✅ **Por que A está correta:** Para gerar código funcional, o FM precisa ter sido exposto a grandes volumes de código durante o pré-treinamento. Modelos como Codex, Code Llama e Claude foram treinados com repositórios de código.

✅ **Por que C está correta:** Geração de código requer gerar sequências token por token (completar funções, gerar implementações). Modelos autoregressivos (decoder-only) são projetados para essa tarefa de geração.

❌ **Por que as outras estão erradas:**
- **B)** Context window MAIOR é melhor para código — precisa ver arquivos inteiros e dependências.
- **D)** Encoder-only (BERT) é para COMPREENSÃO, não geração. Geração de código requer decoder.
- **E)** Código usa múltiplas linguagens e inglês em comentários/docs — treinar só em inglês limitaria compreensão de código.

</details>

---

### Questão 9

Um gerente de produto pergunta por que a empresa deveria usar um Foundation Model pré-treinado em vez de treinar um modelo específico para cada tarefa. Qual é a principal vantagem econômica de FMs pré-treinados para empresas?

A) FMs pré-treinados são sempre gratuitos para uso comercial  
B) FMs eliminam completamente a necessidade de dados proprietários  
C) FMs permitem adaptar um único modelo para múltiplas tarefas via prompt engineering ou fine-tuning, sem treinar do zero cada vez  
D) FMs não requerem nenhum tipo de computação para funcionar  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: C) FMs permitem adaptar um único modelo para múltiplas tarefas sem treinar do zero cada vez**

✅ **Por que C está correta:** O valor econômico central de FMs é o "pré-treinamento uma vez, adaptar muitas vezes". Em vez de gastar tempo e dinheiro treinando modelos separados para sumarização, classificação, geração, etc., um FM faz tudo via prompt engineering ou fine-tuning leve.

❌ **Por que as outras estão erradas:**
- **A)** Muitos FMs têm custo (via API como Bedrock) ou restrições de licença comercial.
- **B)** FMs reduzem necessidade de dados mas NÃO eliminam — fine-tuning e RAG ainda usam dados proprietários.
- **D)** Inferência em FMs requer computação significativa (GPUs) — é um dos principais custos.

</details>

---

### Questão 10

Uma empresa de e-commerce quer usar IA generativa para criar descrições de produtos, responder perguntas de clientes, e traduzir conteúdo para 5 idiomas. A equipe avalia se um ÚNICO Foundation Model pode fazer tudo ou se precisa de modelos separados. Qual afirmação é CORRETA sobre as capacidades de FMs modernos?

A) FMs são single-task — cada tarefa requer um modelo separado treinado especificamente  
B) FMs modernos são multi-task e multimodais — um único modelo pode gerar, responder, traduzir e mais, adaptado via prompts  
C) FMs só funcionam em inglês e requerem Amazon Translate para outros idiomas  
D) FMs não conseguem fazer tradução — essa tarefa requer modelos especializados  

<details>
<summary>🔍 Ver resposta</summary>

**Resposta: B) FMs modernos são multi-task e multimodais — um único modelo pode gerar, responder, traduzir e mais**

✅ **Por que B está correta:** FMs como Claude, GPT, e Llama são treinados em dados massivos multilíngues e multi-tarefa. Um único modelo gera texto, responde perguntas, traduz, resume, classifica — tudo via instrução no prompt. Isso é o poder dos Foundation Models.

❌ **Por que as outras estão erradas:**
- **A)** O oposto — FMs são MULTI-task por design. É a principal vantagem sobre ML tradicional.
- **C)** FMs modernos são multilíngues nativamente — treinados em dezenas de idiomas.
- **D)** FMs conseguem traduzir com qualidade — são treinados em corpus multilíngue.

</details>
