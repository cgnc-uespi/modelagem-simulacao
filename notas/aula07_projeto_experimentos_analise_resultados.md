# Aula 7 – Projeto de Experimentos e Análise de Resultados em Simulação

_Disciplina: Modelagem e Simulação de Eventos Discretos_

_Estudo de caso central: **Cadastro Único para Programas Sociais (CadÚnico)**._

## 1. Por que projetar experimentos?

Rodar uma simulação do CadÚnico **uma vez** não basta para tirar conclusões sólidas.

- Em modelos estocásticos, cada execução (replicação) pode gerar resultados diferentes;
- Precisamos planejar **como** vamos experimentar com o modelo do CadÚnico para responder perguntas específicas (ex.: quantos guichês precisamos?).

Projeto de experimentos em simulação = planejar **cenários, parâmetros, replicações e métricas**.

---

## 2. Elementos de um experimento de simulação (CadÚnico)

### 2.1. Cenários

Um **cenário** é uma combinação de parâmetros que desejamos comparar no CadÚnico.

Exemplos:

- número de guichês: 3, 4, 5;
- escala de atendentes por horário (reforço em horários de pico);\
- política de atendimento: fila única vs filas por tipo de serviço.

### 2.2. Fatores e níveis

Na linguagem de experimentos:

- **Fator:** variável que podemos controlar (por exemplo, número de guichês, política de fila);
- **Níveis:** valores possíveis desse fator (por exemplo, 3, 4, 5 guichês).

Definimos quais fatores vamos variar e em quais níveis para o CadÚnico.

### 2.3. Métricas de resposta

São as saídas que queremos analisar no CadÚnico.

Exemplos:

- tempo médio de espera em fila;
- tempo médio de permanência total na central;
- utilização média de cada guichê;
- número médio de famílias atendidas por dia (cadastradas ou com dados atualizados);
- taxa de abandono (se modelada).

---

## 3. Replicações e variabilidade

Como o modelo é estocástico, precisamos de **replicações independentes** para estimar as métricas.

### 3.1. Replicações

- Cada replicação é uma execução completa da simulação do CadÚnico com a mesma configuração de parâmetros, mas com uma sequência diferente de números aleatórios (seeds diferentes);
- Para cada replicação, obtemos um valor para cada métrica (por exemplo, um tempo médio de espera);
- Ao final, podemos calcular a **média** e a **variabilidade** desses valores.

### 3.2. Intervalos de confiança (noção)

Se tivermos `n` replicações com resultados `X₁, X₂, ..., Xₙ` para uma métrica (por exemplo, tempo médio de espera):

- podemos calcular:
  - média amostral `\bar{X}`;
  - desvio padrão amostral `s`;
- com base nisso, é possível construir um **intervalo de confiança** aproximado para a média verdadeira.

Não é necessário entrar em todos os detalhes estatísticos nesta disciplina, mas é importante entender que:

- **um único número** (uma média de uma única replicação) não resume toda a incerteza;
- intervalos de confiança dão uma ideia de **quão confiável** é nossa estimativa.

---

## 4. Período de aquecimento (warm-up)

Em muitas simulações, o sistema não começa em "estado típico".

No CadÚnico:

- se a simulação começa com fila vazia às 7h, mas na vida real pode já haver famílias aguardando atendimento, os primeiros minutos podem não representar bem o regime normal;
- podemos descartar esse período inicial.

### 4.1. Por que isso importa?

- As primeiras observações podem ser **não representativas** do regime permanente;
- Isso pode enviesar as estimativas de tempo médio de espera, por exemplo.

### 4.2. Estratégias

- Descartar um período inicial de tempo (por exemplo, primeiros `T_warmup` minutos da simulação);
- Descartar as primeiras `N` famílias atendidas;
- Rodar simulações exploratórias para observar quando o sistema parece "estabilizar" (número de famílias no sistema, tempos de espera).

---

## 5. Comparação de cenários (CadÚnico)

Depois de definir cenários e rodar replicações, queremos comparar resultados para o CadÚnico.

### 5.1. Exemplo

Suponha dois cenários:

- **Cenário A:** 3 guichês (configuração atual);
- **Cenário B:** 4 guichês nos horários de pico.

Para cada cenário, fazemos `n` replicações e obtemos:

- `\bar{X}_A`, `IC_A` – tempo médio de espera e intervalo de confiança no cenário A;
- `\bar{X}_B`, `IC_B` – idem para o cenário B.

Podemos então:

- comparar as médias;
- verificar se os intervalos de confiança se sobrepõem;
- interpretar se a diferença é relevante para a tomada de decisão (por exemplo, se a redução de espera justifica o custo de um guichê a mais).

### 5.2. Custo vs benefício

Também é importante considerar:

- custo de aumentar recursos (por exemplo, contratar mais agentes sociais ou abrir novos postos de atendimento);
- ganho em desempenho (redução de tempo de espera, redução de abandono).

Simulação ajuda a quantificar esse trade-off para a gestão do CadÚnico.

---

## 6. Apresentação de resultados (CadÚnico)

Resultados de simulação devem ser apresentados de forma **clara e honesta** para gestores públicos.

### 6.1. Boas práticas

- Apresentar:
  - valores médios das métricas (tempo médio de espera, utilização, etc.);
  - medidas de variabilidade (desvio padrão, intervalos de confiança);
  - número de replicações por cenário;
  - principais hipóteses do modelo (distribuições de chegada e serviço, horários de pico, etc.).

- Usar gráficos e tabelas:
  - gráficos de barras com barras de erro (indicando variabilidade);
  - tabelas com métricas por cenário.

- Escrever interpretações em linguagem clara, por exemplo:
  - "Adicionar um guichê nos horários de pico reduz o tempo médio de espera de 25 para 12 minutos, com uma redução de X% na taxa de abandono.".

---

## 7. Atividade proposta (Aula 7)

1. Defina pelo menos **dois cenários** para o CadÚnico, por exemplo:
   - cenário atual (número de guichês e escala de atendentes hoje);
   - cenário com reforço de guichês em horários de pico.
2. Especifique para cada cenário:
   - quais serão as **métricas** de interesse (tempo médio de espera, utilização, etc.);
   - quantas **replicações** você pretende rodar por cenário;
   - se haverá **período de aquecimento** e como será tratado.
3. Desenhe um esboço de tabela de resultados que você gostaria de obter ao final, com linhas para cenários e colunas para métricas (incluindo médias e alguma medida de variabilidade).
4. Escreva um pequeno parágrafo explicando como você **interpretaria** os resultados para recomendar um cenário ao gestor do CadÚnico.
