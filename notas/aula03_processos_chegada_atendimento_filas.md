# Aula 3 – Processos de Chegada e Atendimento (Fundamentos de Filas)

_Disciplina: Modelagem e Simulação de Eventos Discretos_

_Estudo de caso central: **Cadastro Único para Programas Sociais (CadÚnico)**._

## 1. Motivação

Grande parte dos modelos de eventos discretos envolve **filas**. No caso do CadÚnico, isso é evidente:

- famílias chegando ao longo do dia;
- atendentes (guichês) prestando serviço;
- regras de espera e atendimento (senhas, filas, prioridades).

Para modelar sistemas como o CadÚnico, precisamos entender minimamente **como as chegadas e os tempos de atendimento se comportam**.

---

## 2. Processos de chegada

### 2.1. Chegadas determinísticas vs aleatórias

No CadÚnico, as chegadas de famílias podem ter padrões sazonais e picos, mas do ponto de vista individual, são em grande parte **aleatórias**.

- **Determinísticas:** as famílias chegariam em instantes totalmente previsíveis (pouco realista nesse contexto).  
- **Aleatórias:** as famílias chegam em tempos imprevisíveis, com variação, mas podemos observar padrões médios (por hora, por dia, por período de campanha).

Exemplo de observação prática:

- pico de chegadas logo após a abertura;
- picos próximos a campanhas de cadastramento ou prazo de atualização cadastral;
- menor fluxo em certos dias/horários.

### 2.2. Processo de Poisson (intuição)

Um modelo clássico para chegadas aleatórias é o **processo de Poisson**:

- Em média, ocorrem `λ` chegadas por unidade de tempo (taxa de chegada);
- Chegadas são independentemente distribuídas ao longo do tempo;
- Os **tempos entre chegadas** (interarrivals) seguem distribuição exponencial (em muitos casos teóricos).

No CadÚnico, em um intervalo curto de tempo (por exemplo, uma faixa horária em dia típico), pode ser razoável aproximar as chegadas por um processo desse tipo – ou usar uma taxa λ(t) que muda ao longo do dia.

### 2.3. Distribuições genéricas de tempo entre chegadas

Nem sempre a exponencial é adequada. Em simulação, podemos usar **qualquer distribuição** que pareça razoável para o comportamento observado:

- distribuição não homogênea (taxa variável por hora);
- distribuição empírica (com base em dados históricos de contagens por minuto/hora);
- aproximações simplificadas (por exemplo, supondo exponencial em um primeiro modelo, depois refinando).

O importante é: o **tempo entre chegadas no CadÚnico** é uma variável aleatória que será **amostrada** durante a simulação.

---

## 3. Tempos de serviço (atendimento)

### 3.1. Serviço determinístico vs aleatório

No CadÚnico, o tempo de atendimento varia de família para família:

- tipo de serviço (atualização simples vs cadastramento inicial complexo);
- necessidade de consultar sistemas externos;
- experiência do atendente.

Logo, faz mais sentido tratá-lo como **aleatório**.

### 3.2. Distribuições típicas

De forma semelhante às chegadas, podemos assumir várias distribuições para o tempo de serviço no CadÚnico:

- exponencial (modelo simples, sem memória);
- lognormal (quando há caudas longas – alguns atendimentos muito demorados);
- empírica (com base em amostras de tempos de atendimento medidos).

Em simulação, a escolha da distribuição é uma **hipótese de modelagem** que deve refletir, na medida do possível, o comportamento real da central.

---

## 4. Elementos básicos de um sistema de filas (CadÚnico)

Um sistema de filas, visto a partir do CadÚnico, pode ser descrito por:

- **Fontes de famílias** (chegadas ao longo do dia);
- **Fila(s)** onde famílias esperam (fila única ou filas por tipo de serviço);
- **Servidores** (atendentes/guichês);
- **Disciplina de atendimento** (por exemplo, ordem de chegada por senha, prioridades por tipo de serviço);
- **Capacidade do sistema** (ex.: número máximo de pessoas no interior da central);
- **População de famílias** (praticamente infinita em termos de modelagem).

### 4.1. Disciplina de atendimento

No CadÚnico, disciplinas comuns podem ser:

- **FIFO (First-In, First-Out)**: famílias são atendidas na ordem de chegada (por senha);
- **Prioridades:** alguns tipos de atendimento podem ter prioridade (por exemplo, atendimento preferencial, idosos, gestantes);
- **Filas separadas por tipo de serviço:** senhas diferentes para cadastramento, atualização cadastral, consultas, etc.

### 4.2. Capacidade do sistema

- O CadÚnico pode ter limite físico de capacidade (número máximo de pessoas dentro da central).  
- Se o sistema estiver cheio, novas famílias podem ter de esperar do lado de fora ou desistir.

Esses aspectos podem ser incluídos no modelo de simulação através de **capacidade máxima** do sistema e **eventos de bloqueio/abandono**.

---

## 5. Ligação com modelos analíticos de filas (visão rápida)

Na teoria de filas, é comum usar a notação **Kendall** para descrever sistemas, por exemplo:

- M/M/1, M/M/c, M/G/1 etc., onde:
  - M = chegadas/serviço Markovianos (exponenciais);
  - G = distribuição geral;
  - 1, c = número de servidores.

Para um CadÚnico simplificado:

- uma fila única,
- chegadas exponenciais com taxa λ,
- tempos de serviço exponenciais com média `1/μ`,
- `c` guichês de atendimento,

poderíamos pensar em um modelo M/M/c analítico.

Na disciplina, porém, o objetivo é usar **simulação** para lidar também com casos mais complexos (vários tipos de serviço, prioridades, horários de pico, etc.).

---

## 6. Como isso entra na simulação de eventos discretos (CadÚnico)

Em um simulador de eventos discretos do CadÚnico, usamos **geradores de variáveis aleatórias** para:

- determinar o tempo até a **próxima chegada de família** (`tempo_entre_chegadas_cadunico()`);
- determinar o **tempo de atendimento** (`tempo_de_servico_cadunico()`), possivelmente variando por tipo de serviço.

Esses tempos definem os **instantes de ocorrência dos eventos**:

- `CHEGADA_FAMILIA` em `relogio + tempo_entre_chegadas_cadunico()`;
- `FIM_ATENDIMENTO` em `relogio + tempo_de_servico_cadunico()`.

Assim, os processos de chegada e de serviço alimentam diretamente a **lista de eventos futuros** da simulação.

---

## 7. Atividade proposta (Aula 3)

Considere o **CadÚnico**:

1. Descreva, com base em sua experiência ou em suposições razoáveis:
   - se as **chegadas** de famílias parecem mais determinísticas ou aleatórias;
   - se há horários de pico claros (manhã, início do mês, véspera de vencimentos, etc.);
   - se os **tempos de atendimento** parecem mais ou menos variáveis (e o que influencia essa variação).
2. Identifique a disciplina de atendimento praticada no CRAS:
   - fila única com senhas?
   - filas por tipo de serviço?
   - prioridades (preferencial, idoso, etc.)?
3. Sugira, mesmo que qualitativamente:
   - uma distribuição plausível para os tempos **entre chegadas**;
   - uma distribuição plausível para os tempos de **atendimento**, podendo ser diferente por tipo de serviço.

Essa atividade prepara a base para, em aulas posteriores, transformar essas hipóteses em código de simulação e análise de desempenho para o CadÚnico.
