# Aula 1 – Introdução à Modelagem e Simulação de Eventos Discretos

_Disciplina: Modelagem e Simulação de Eventos Discretos_

_Estudo de caso central: **Cadastro Único para Programas Sociais (CadÚnico)**._

## 1. Motivação: por que modelar e simular?

Na prática de Engenharia e Computação, lidamos com sistemas que são complexos demais para serem analisados apenas "no olho" ou com contas simples. Exemplos:

- filas em bancos, hospitais, call centers;
- linhas de produção em fábricas;
- redes de computadores e sistemas distribuídos;
- sistemas de transporte, logística, tráfego;
- sistemas financeiros, mercados, estoques;
- **postos de atendimento do CadÚnico** (CRAS – Centro de Referência de Assistência Social).

No caso do CadÚnico, algumas perguntas típicas são:

- Quantos atendentes (guichês) são necessários para manter o **tempo médio de espera** abaixo de um certo valor?
- O que acontece em dias de pico (ex.: vencimento de prazos de atualização cadastral, campanhas de cadastramento)? O sistema "colapsa"?
- Vale a pena abrir mais guichês apenas em certos horários ou dias?

Nem sempre existe uma **fórmula analítica fechada** para responder a essas perguntas. E, mesmo quando existe, o modelo matemático pode ficar muito complexo ou assumir hipóteses irreais.

É aí que entram a **modelagem** e a **simulação**.

---

## 2. Conceitos básicos: sistema, modelo, simulação

### 2.1. Sistema

Um **sistema** é um conjunto de elementos que interagem entre si para cumprir algum propósito.

Exemplo central desta disciplina:

- **Cadastro Único para Programas Sociais (CadÚnico)**:
  - elementos: famílias, atendentes (agentes sociais), guichês, senhas, filas, sistema de gestão de atendimento;
  - propósito: atender demandas das famílias (cadastramento, atualização cadastral, consultas, informações, etc.) em tempo razoável.

Outros exemplos:

- Um pronto-socorro: pacientes, médicos, enfermeiros, leitos, equipamentos, regras de atendimento.
- Uma rede de computadores: roteadores, switches, enlaces, protocolos, pacotes.

Em modelagem, é importante **definir as fronteiras do sistema**:

- O que está **dentro** do sistema?  
  Ex.: dentro do CadÚnico – guichês, atendentes, filas internas, sistema de senhas.  
- O que é considerado **ambiente**?  
  Ex.: famílias chegando de fora, políticas do MDS/SAGI, horários de funcionamento, feriados.

### 2.2. Modelo

Um **modelo** é uma representação (mais simples e manejável) de um sistema real.

- Ele **não é** o sistema real: é uma forma de capturar os aspectos mais relevantes para o objetivo da análise.
- Dependendo do objetivo, diferentes modelos podem ser construídos para o **mesmo** sistema real.

Exemplo (sistema: CadÚnico):

- Se o objetivo é estudar o **tempo de espera em fila**, podemos focar em:
  - taxa de chegada de famílias em cada horário;
  - número de guichês e tempos de atendimento por tipo de serviço;
  - regras de fila (fila única, filas por tipo de serviço, prioridades).

Talvez não seja necessário modelar detalhes internos do sistema de informação, apenas a lógica de atendimento.

### 2.3. Simulação

**Simulação** é o processo de executar um modelo ao longo do tempo para observar o seu comportamento.

- Em vez de resolver equações analíticas, **deixamos o modelo “rodar”** (no computador) e coletamos resultados.
- Esses resultados são usados para estimar métricas de interesse (por exemplo, no CadÚnico: tempo médio em fila, utilização dos atendentes, número de famílias atendidas por dia).

De forma simplificada:

> Sistema real (CadÚnico) → construímos um **modelo** → rodamos esse modelo (simulação) → analisamos os resultados para entender ou melhorar o CadÚnico.

---

## 3. Tipos de modelos: determinístico vs estocástico

### 3.1. Modelo determinístico

Um modelo é **determinístico** quando, dadas as mesmas condições iniciais e parâmetros, o resultado é sempre o mesmo.

- Não há "sorte" ou "azar" no modelo: tudo é determinado por equações ou regras fixas.

Exemplo:

- Um modelo que calcula o tempo de atendimento assumindo que cada família leva exatamente 10 minutos, sem variação.

### 3.2. Modelo estocástico

Um modelo é **estocástico** quando inclui variáveis aleatórias (incerteza).

- Mesmo com as mesmas condições iniciais, diferentes execuções do modelo podem produzir resultados diferentes.
- Isso é típico do CadÚnico real, onde há variação em:
  - horários de chegada das famílias;
  - tempo que cada atendimento leva;
  - tipos de demanda.

Exemplo:

- Um modelo do CadÚnico em que tempos entre chegadas e tempos de atendimento são aleatórios.

### 3.3. Observação

A maioria dos modelos de simulação de eventos discretos usados em engenharia de sistemas são **estocásticos**, justamente porque queremos capturar a variabilidade do mundo real (como no CadÚnico).

---

## 4. Tempo: modelos contínuos vs discretos

### 4.1. Modelos de tempo contínuo

Em um modelo **contínuo**, o estado do sistema pode mudar a qualquer instante do tempo, e o tempo é tratado como uma variável contínua (por exemplo, em equações diferenciais).

Exemplo:

- Crescimento populacional representado por uma equação diferencial.
- Variação da temperatura em um processo químico ao longo do tempo.

### 4.2. Modelos de eventos discretos

Em um modelo de **eventos discretos**, o estado do sistema muda apenas em instantes específicos, chamados **eventos**.

No CadÚnico, exemplos de eventos:

- chegada de uma família à central;
- retirada de uma senha;
- início de atendimento em um guichê;
- término de atendimento;
- desistência/abandono da fila.

Entre eventos, o estado do sistema (quantas pessoas na fila, quais guichês ocupados) é considerado **constante**.

### 4.3. Por que eventos discretos são importantes?

Muitos sistemas de interesse em Computação e Engenharia podem ser descritos como **sequências de eventos**:

- Redes de computadores (chegada/saída de pacotes);
- Sistemas de filas (como o CadÚnico: chegadas, inícios e términos de atendimento);
- Sistemas de manufatura (início e fim de processamento de peças).

A simulação de eventos discretos é, portanto, uma técnica natural para estudar sistemas como o CadÚnico.

---

## 5. Modelos analíticos vs simulação

### 5.1. Modelos analíticos

Modelos analíticos usam fórmulas matemáticas para descrever o comportamento do sistema e, idealmente, produzem soluções fechadas (ou aproximadas) para métricas de interesse.

Exemplo clássico:

- Teoria de filas (como modelos M/M/1) em que conseguimos fórmulas para tempo médio em fila, tamanho médio da fila, utilização etc.

No contexto do CadÚnico, um modelo analítico simples poderia aproximar a fila de um tipo de atendimento como um M/M/1 ou M/M/c.

Vantagens:

- Resultados exatos (dentro das hipóteses do modelo);
- Computação rápida: uma vez que a fórmula está pronta, é só calcular.

Limitações:

- Muitas vezes exigem hipóteses simplificadoras fortes (por exemplo, chegadas e serviços exponenciais, ausência de prioridades);
- Para sistemas complexos como o CadÚnico real (vários tipos de serviço, filas diferentes, prioridades), as equações podem não existir ou ser impraticáveis.

### 5.2. Simulação

Simulação não busca uma fórmula fechada, mas sim **replicar o comportamento do sistema** via modelo computacional.

Vantagens:

- Lida melhor com sistemas complexos e regras complicadas (ex.: diferentes filas no CadÚnico, regras de prioridade, horários de pico);
- Pode incorporar distribuições de tempo mais realistas.

Limitações:

- Resultados são aproximados (estimativas com incerteza);
- Demanda tempo computacional e planejamento de experimentos (número de replicações, tempo de simulação, etc.).

### 5.3. Quando usar qual?

- Se existir um modelo analítico razoável e manejável → vale a pena tentar primeiro (mais simples, rápido e exato dentro das hipóteses);
- Quando o sistema real é complexo demais ou foge das hipóteses dos modelos analíticos → **simulação** é uma alternativa poderosa.

No caso do CadÚnico, a simulação permite testar cenários de número de atendentes, regras de fila e horários de pico com mais realismo.

---

## 6. Exemplos de sistemas para simulação de eventos discretos

Além do CadÚnico, outros exemplos típicos de sistemas que podem ser modelados por eventos discretos são:

1. **Filas em serviços** (bancos, hospitais, call centers);
2. **Manufatura** (linhas de produção com máquinas, robôs, buffers);
3. **Redes de computadores e sistemas distribuídos** (roteadores, filas de pacotes);
4. **Sistemas de transporte** (ônibus, metrô, aeroportos);
5. **Sistemas de saúde** (pronto-socorros, UTIs, clínicas).

Na disciplina, contudo, o **CadÚnico será o estudo de caso central**.

---

## 7. Atividade proposta (Aula 1)

Para fixar os conceitos básicos, considere o **Cadastro Único para Programas Sociais (CadÚnico)**:

1. Descreva, em poucas linhas:
   - qual é o **objetivo** de desempenho que poderia ser estudado (tempo médio de espera, tempo máximo de fila, utilização dos atendentes, número de famílias atendidas por dia, taxa de abandono);
   - quais são as **fronteiras do sistema** (o que está dentro – guichês, atendentes, filas internas – e o que está fora – famílias chegando, calendário de vencimentos, etc.);
   - quais seriam as **entradas** (chegadas de famílias por hora, tipo de serviço, escala de atendentes) e as **saídas** (métricas de desempenho);
   - identifique alguns possíveis **eventos** discretos (chegadas, retirada de senha, início/fim de atendimento, desistência).

Essa atividade serve como ponte para as próximas aulas, em que vamos formalizar mais a ideia de **simulação de eventos discretos** e começar a construir modelos específicos para o CadÚnico.
