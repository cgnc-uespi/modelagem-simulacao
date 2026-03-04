# Atividades de Análise de Dados — CadÚnico
## Disciplina: Modelagem e Simulação de Eventos Discretos

---

## 📊 Contexto da Base de Dados

**Fonte:** Microdados Amostrais — CadÚnico dez/2018

**Arquivos disponíveis:**
- `base_amostra_pessoa_201812.csv` (~12.8M linhas)
  - Dados demográficos, educacionais, ocupacionais e de renda de pessoas
  - Colunas: sexo, idade, raça/cor, escolaridade, deficiência, renda, emprego, etc.

- `base_amostra_familia_201812.csv` (~4.8M linhas)
  - Dados de famílias, renda familiar, acesso a serviços
  - Colunas: renda média, tamanho, Bolsa Família, água, lixo, energia, etc.

---

## 📌 Atividade 1: Limpeza e Preparação de Dados
**Objetivo:** Compreender a qualidade dos dados antes de modelar

### Tarefas:
1. **Carregue as duas bases** e identifique:
   - Dimensões de cada tabela
   - Colunas com valores ausentes (missing values)
   - Percentual de falta por coluna

2. **Tratamento de dados:**
   - Documente as estratégias de imputação (remover vs. substituir)
   - Verifique duplicatas (há pessoas/famílias repetidas?)
   - Identifique outliers (valores impossíveis ou muito extremos)

3. **Visualização:**
   - Crie gráficos de missing values por coluna
   - Mostre a distribuição de dados ausentes por tipo

---

## 📈 Atividade 2: Análise Demográfica
**Objetivo:** Entender a composição populacional no CadÚnico

### Tarefas:
1. **Distribuição por sexo**
   - Qual é a proporção Masculino/Feminino?
   - Como varia por faixa etária?

2. **Pirâmide etária**
   - Construa uma pirâmide etária clássica (sexo vs. idade)
   - Quais faixas etárias têm mais concentração?
   - Isso sugere uma população jovem ou envelhecida?

3. **Raça e cor**
   - Qual a distribuição de raça/cor na amostra?
   - Há diferenças de renda entre grupos raciais?

4. **Escolaridade**
   - Que proporção tem "Sem instrução"?
   - Qual o nível máximo mais frequente?
   - Como escolaridade correlaciona com idade?

---

## 💼 Atividade 3: Análise de Renda e Emprego
**Objetivo:** Modelar padrões econômicos das famílias

### Tarefas:
1. **Análise univariada:**
   - Histograma da remuneração de emprego (excluindo zeros)
   - Quartis de renda por tipo de ocupação
   - Proporção de pessoas com renda zero

2. **Análise por família:**
   - Distribuição de renda média familiar
   - Relação entre tamanho da família e renda per capita
   - Existe correlação negativa entre filhos e renda?

3. **Desigualdade:**
   - Calcule índices (Gini, razão 80/20, coeficiente de Palma)
   - Em qual faixa de renda está a mediana?
   - Qual % das rendas concentra 50% da renda total?

---

## 🏠 Atividade 4: Análise de Serviços Básicos
**Objetivo:** Compreender acesso a infraestrutura (desigualdade)

### Tarefas:
1. **Abastecimento de água:**
   - % de famílias com rede geral vs. outras fontes
   - Relação entre tipo de água e renda média familiar
   - Há regiões com acesso diferente? (use cd_ibge)

2. **Destino do lixo:**
   - Que proporção tem coleta vs. queimado/enterrado?
   - Como lixo coletado correlaciona com renda?

3. **Energia elétrica (se disponível):**
   - % com acesso a energia
   - Diferença de renda entre com/sem acesso?

4. **Visualização:**
   - Tabela cruzada: tipo de água × faixa de renda
   - Gráfico de acesso a serviços por quintil de renda

---

## 🎯 Atividade 5: Teste de Hipóteses Estatísticos
**Objetivo:** Validar pressupostos antes de simular

### Tarefas:
1. **Escolha 3 hipóteses** (exemplos):
   - H0: Não há diferença de renda entre homens e mulheres
   - H0: Idade não influencia escolaridade
   - H0: Tamanho da família é independente da renda

2. **Para cada hipótese:**
   - Defina a estatística de teste apropriada (t-test, chi-square, etc.)
   - Calcule p-value
   - Tome decisão (rejeitar ou não rejeitar H0)
   - Interprete em linguagem não técnica

3. **Documente:**
   - Pressupostos (normalidade, homocedasticidade, etc.)
   - Tamanho do efeito (Cohen's d, eta-squared)

---

## 🔗 Atividade 6: Matriz de Correlação
**Objetivo:** Identificar relacionamentos multivariados

### Tarefas:
1. **Crie matriz de correlação** de variáveis numéricas (família):
   - Renda média, tamanho da família, idade média, etc.
   - Visualize com heatmap

2. **Identifique:**
   - Maiores correlações positivas
   - Maiores correlações negativas
   - Pares de variáveis não correlacionadas (por que?)

3. **Análise de multicolinearidade:**
   - Hay redundância entre variáveis?
   - Quais seriam críticas para um modelo preditivo?

---

## 📊 Atividade 7: Segmentação (Clustering)
**Objetivo:** Classificar famílias em grupos homogêneos

### Tarefas:
1. **Prepare dados normalizados:**
   - Selecione 5-7 variáveis principais
   - Normalize (z-score ou min-max)

2. **Aplique K-means:**
   - Teste k = 2, 3, 4, 5, 6
   - Calcule inércia para cada k
   - Use cotovelo (elbow method) para escolher k ótimo

3. **Caracterize clusters:**
   - Perfil demográfico/econômico de cada cluster
   - Tamanho e proporção
   - Crie tabela resumida

4. **Interpretação:**
   - Esses clusters fazem sentido socioeconômico?
   - Poderiam representar grupos para simulação?

---

## 🎲 Atividade 8: Ajuste de Distribuição Probabilística
**Objetivo:** Preparar dados para simulação estocástica

### Tarefas:
1. **Escolha 3 variáveis contínuas:**
   - Renda de emprego
   - Renda média familiar
   - Idade (discreta, mas pode ser contínua)

2. **Para cada variável:**
   - Teste 5 distribuições (Normal, Lognormal, Gamma, Weibull, Exponencial)
   - Calcule estatísticas de aderência (KS, AD, chi-square)
   - Faça Q-Q plots

3. **Seleção:**
   - Qual distribuição melhor se ajusta?
   - Estime parâmetros da distribuição

4. **Validação:**
   - Gere amostra sintética da distribuição ajustada
   - Sobreponha histogramas (dados reais vs. simulados)

---

## 🔄 Atividade 9: Análise de Processos (Cadeias de Markov)
**Objetivo:** Modelar transições entre estados

### Tarefas:
1. **Crie estados de escolaridade:**
   - Agrupe em: Sem instrução, Fundamental, Médio, Superior
   - Considere apenas pessoas ≥ 15 anos

2. **Matriz de transição:**
   - Para cada pessoa, identifique escolaridade atual
   - Assuma que essa é uma distribuição estacionária

3. **Pergunta de simulação:**
   - Se governo investe em educação, qual taxa de transição mudaria?
   - Como evoluiria a educação em 5, 10, 20 anos?

---

## 📈 Atividade 10: Projeto Integrado — Simulação de Dinâmica Familiar
**Objetivo:** Aplicar tudo aprendido em um modelo simulado

### Tarefas:
1. **Defina o sistema:**
   - Popule simulação com 1.000 famílias (amostra da base real)
   - Cada família tem: tamanho, renda, composição etária

2. **Eventos de simulação:**
   - Nascimento (novo membro, taxas por faixa etária)
   - Saída (morte, migração — taxas empíricas)
   - Mudança de emprego (probabilidades de renda)
   - Acesso a Bolsa Família (critério de renda)

3. **Métricas durante simulação:**
   - Evolução de renda média familiar
   - Crescimento/redução de população
   - % de famílias com Bolsa Família
   - Indicador de desigualdade (Gini)

4. **Experimentos:**
   - Cenário 1: Sem intervenção (linha base)
   - Cenário 2: Expansão de emprego (+20% nas oportunidades)
   - Cenário 3: Programa de renda básica (R$ 200/pessoa)
   - Compare resultados após 5 anos de simulação

5. **Relatório:**
   - Documentar modelo conceitual
   - Código comentado
   - Gráficos de evolução temporal
   - Análise de sensibilidade (qual parâmetro mais afeta resultado?)

---

## 🛠️ Ferramentas Recomendadas

| Atividade | Ferramenta | Biblioteca Python |
|-----------|-----------|-------------------|
| 1-3 | Python + Jupyter | pandas, numpy, matplotlib |
| 4 | Python + Jupyter | pandas, seaborn |
| 5 | Python + Jupyter | scipy.stats |
| 6 | Python + Jupyter | pandas, seaborn |
| 7 | Python + Jupyter | scikit-learn |
| 8 | Python + Jupyter | scipy.stats, statsmodels |
| 9 | Python + Jupyter | pandas, numpy |
| 10 | SimPy ou Python puro | simpy, pandas, matplotlib |

---

## 📋 Critérios de Avaliação

- **Corretude:** Análises estatísticas corretas?
- **Clareza:** Código comentado e bem estruturado?
- **Interpretação:** Insights além de números?
- **Visualizações:** Gráficos informativos e bem formatados?
- **Documentação:** Explicações do que foi feito e por quê?

---

## 📚 Referências

- CadÚnico: https://aplicacoes.cidadania.gov.br/
- Dicionário de dados disponível no workspace
- Exemplos: `eda_cadunico.py`
