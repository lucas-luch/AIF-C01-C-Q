# Conceitos Fundamentais de ML

## Visão Geral

A prova AIF-C01 testa seu entendimento de conceitos que afetam a qualidade dos modelos. Você precisa saber **identificar problemas** (overfitting, underfitting) e **entender os trade-offs** (bias vs variance).

---

## Overfitting (Sobreajuste)

O modelo **memoriza** os dados de treino em vez de aprender padrões generalizáveis. Performa muito bem no treino mas **mal em dados novos**.

### Sinais
- Acurácia altíssima no treino, muito menor no teste
- Modelo muito complexo para a quantidade de dados
- Curva de aprendizado: erro de treino baixo, erro de validação alto e divergente

### Causas
- Modelo muito complexo (muitos parâmetros)
- Poucos dados de treino
- Treino por tempo demais (muitas epochs)
- Features irrelevantes (ruído)

### Soluções
- Mais dados de treino
- Regularização (L1/L2) — penaliza complexidade
- Early stopping — parar o treino quando validação começa a piorar
- Dropout (em redes neurais) — desativa neurônios aleatoriamente
- Reduzir complexidade do modelo
- Cross-validation

### Analogia
Como um aluno que decora as respostas da prova anterior mas não entende a matéria — vai mal numa prova diferente.

---

## Underfitting (Subajuste)

O modelo é **simples demais** para capturar os padrões nos dados. Performa **mal tanto no treino quanto no teste**.

### Sinais
- Acurácia baixa no treino E no teste
- Modelo não consegue capturar relações nos dados
- Curva de aprendizado: ambos os erros altos e próximos

### Causas
- Modelo muito simples para o problema
- Features insuficientes ou irrelevantes
- Pouco tempo de treino
- Regularização excessiva

### Soluções
- Usar modelo mais complexo
- Adicionar mais features relevantes
- Treinar por mais tempo
- Reduzir regularização
- Melhor feature engineering

### Analogia
Como tentar descrever um mapa 3D usando apenas uma linha reta — simples demais para capturar a complexidade.

---

## Comparação: Overfitting vs Underfitting

| Aspecto | Overfitting | Underfitting |
|---------|-------------|--------------|
| Performance no treino | Alta | Baixa |
| Performance no teste | Baixa | Baixa |
| Complexidade do modelo | Muito alta | Muito baixa |
| Problema | Memoriza ruído | Não aprende padrões |
| Solução principal | Simplificar/regularizar | Aumentar complexidade |

---

## Bias vs Variance (Viés vs Variância)

### Bias (Viés)
- Erro introduzido por **suposições simplificadoras** do modelo
- Alto bias = underfitting (modelo simples demais)
- O modelo consistentemente erra na mesma direção
- Exemplo: usar regressão linear para dados com relação curva

### Variance (Variância)
- Sensibilidade do modelo a **flutuações nos dados de treino**
- Alta variância = overfitting (modelo complexo demais)
- Pequenas mudanças nos dados de treino causam grandes mudanças nas previsões
- Exemplo: árvore de decisão muito profunda que muda totalmente com dados ligeiramente diferentes

### Trade-off Bias-Variance
- Modelos simples: alto bias, baixa variância
- Modelos complexos: baixo bias, alta variância
- Objetivo: encontrar o **equilíbrio** (sweet spot) que minimiza o erro total

---

## Hiperparâmetros vs Parâmetros

| Aspecto | Parâmetros | Hiperparâmetros |
|---------|-----------|-----------------|
| **Quem define** | O modelo aprende durante o treino | O humano define antes do treino |
| **Exemplos** | Pesos da rede neural, coeficientes da regressão | Learning rate, número de epochs, batch size |
| **Ajuste** | Automático (pelo algoritmo) | Manual ou por tuning (grid search, random search) |

### Hiperparâmetros comuns
- **Learning rate** — velocidade de aprendizado (muito alto = instável, muito baixo = lento)
- **Epochs** — quantas vezes o modelo vê todos os dados de treino
- **Batch size** — quantos exemplos processar de cada vez
- **Regularização (lambda)** — quanto penalizar complexidade
- **Número de camadas/neurônios** — arquitetura da rede neural

---

## Features e Labels

| Conceito | Descrição | Exemplo (previsão de preço de casa) |
|----------|-----------|--------------------------------------|
| **Features (X)** | Variáveis de entrada | Tamanho, localização, nº quartos |
| **Labels (Y)** | Resposta correta (target) | Preço da casa |
| **Inferência** | Usar modelo treinado em dados novos | Novo imóvel → modelo prevê preço |

---

## Dados de Treino / Validação / Teste

| Conjunto | % típico | Propósito | Quando é usado |
|----------|----------|-----------|----------------|
| Treino | 70-80% | Modelo aprende | Durante treinamento |
| Validação | 10-15% | Ajustar hiperparâmetros | Durante tuning |
| Teste | 10-15% | Avaliação final imparcial | Idealmente uma vez ao final (evitar data leakage) |

**Cross-validation (validação cruzada):** Técnica onde os dados são divididos em K partes (folds). O modelo treina em K-1 partes e valida na restante, repetindo K vezes. Dá uma estimativa mais robusta da performance, especialmente com datasets pequenos.

---

## Resumo para a Prova

| Conceito | Palavra-chave na questão |
|----------|--------------------------|
| Overfitting | "bom no treino, ruim no teste", "memoriza", "complexo demais" |
| Underfitting | "ruim em tudo", "simples demais", "não captura padrões" |
| Alto Bias | "suposições erradas", "simplista", "underfitting" |
| Alta Variância | "sensível a mudanças", "instável", "overfitting" |
| Regularização | "reduzir overfitting", "penalizar complexidade" |
| Early stopping | "parar treino", "evitar overfitting" |
| Cross-validation | "estimativa robusta", "K folds" |

---

*Próximo bloco: Métricas de Avaliação*
