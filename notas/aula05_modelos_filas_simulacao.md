# Aula 5 – Construção de Modelos de Filas em Simulação de Eventos Discretos

_Disciplina: Modelagem e Simulação de Eventos Discretos_

_Estudo de caso central: **Cadastro Único para Programas Sociais (CadÚnico)**._

## 1. Objetivo da aula

Aplicar os conceitos de:

- eventos discretos (Aula 2),
- chegadas/serviços (Aula 3),
- geração de variáveis aleatórias (Aula 4)

para construir um modelo simples de **fila com um único servidor**, interpretado como uma versão muito simplificada do CadÚnico.

---

## 2. Modelo conceitual: CadÚnico com um guichê (tipo M/M/1)

Considere uma versão simplificada do CadÚnico com:

- chegadas de famílias ao longo do tempo;
- um único guichê (servidor);
- disciplina de atendimento FIFO (ordem de chegada por senha);
- capacidade infinita de fila (ninguém é perdido).

Essa simplificação é útil para entender a lógica básica antes de lidar com vários guichês e tipos de serviço.

### 2.1. Variáveis de estado

- `num_familias_no_sistema` – número de famílias na fila + em atendimento;
- `guiche_ocupado` – verdadeiro/falso.

Opcionalmente:

- registro do **tempo de chegada** de cada família, para cálculo de tempo de permanência.

### 2.2. Eventos

- `CHEGADA_CIDADAO`;  
- `FIM_ATENDIMENTO` (término de atendimento no guichê).

### 2.3. Parâmetros

- `lambda` – taxa média de chegadas de famílias (para gerar tempos entre chegadas);
- `mu` – taxa média de serviço (para gerar tempos de atendimento).

---

## 3. Lógica dos eventos (CadÚnico simplificado)

### 3.1. Evento CHEGADA_CIDADAO

Quando um evento `CHEGADA_CIDADAO` ocorre em `t = relogio`:

1. `num_familias_no_sistema <- num_familias_no_sistema + 1`.
2. Registrar o tempo de chegada da família (para estatísticas futuras).
3. Se o guichê estiver **livre** (`guiche_ocupado == falso`):
   - definir `guiche_ocupado <- verdadeiro`;
   - gerar um tempo de serviço `S = tempo_de_servico_cadunico()`;
   - agendar evento `FIM_ATENDIMENTO` para `t + S`.
4. Agendar a **próxima chegada**:
   - gerar um tempo entre chegadas `A = tempo_entre_chegadas_cadunico()`;
   - agendar novo `CHEGADA_CIDADAO` para `t + A`.

### 3.2. Evento FIM_ATENDIMENTO

Quando um evento `FIM_ATENDIMENTO` ocorre em `t = relogio`:

1. `num_familias_no_sistema <- num_familias_no_sistema - 1`.
2. Atualizar estatísticas de tempo de permanência (usando o tempo de chegada da família atendido).
3. Se `num_familias_no_sistema > 0` (ainda há famílias esperando):
   - gerar novo tempo de serviço `S = tempo_de_servico_cadunico()`;
   - agendar próximo `FIM_ATENDIMENTO` para `t + S`.
4. Senão (fila ficou vazia):
   - `guiche_ocupado <- falso`.

---

## 4. Coleta de estatísticas (CadÚnico)

### 4.1. Tempo de permanência no sistema

Para cada família, armazenamos o tempo de chegada `t_chegada`. Quando ele sai em `t_saida`, o tempo de permanência é:

- `W = t_saida - t_chegada`.

Mantemos acumuladores, por exemplo:

- `soma_tempos_permanencia`;
- `num_familias_atendidas`.

Ao final da simulação:

- `tempo_medio_permanencia = soma_tempos_permanencia / num_cidadaos_atendidos`.

### 4.2. Utilização do guichê

Uma forma de estimar a **utilização** do guichê é acumular o tempo em que ele esteve ocupado:

- Sempre que o guichê muda de estado (livre ↔ ocupado), atualizamos um acumulador com base na diferença de tempo desde a última atualização.

Por exemplo:

- `tempo_ultimo_evento` – último instante em que atualizamos estatísticas;
- `area_ocupacao` – acumula o produto "estado do guichê" × tempo.

Em cada evento:

1. `delta_t = relogio - tempo_ultimo_evento`;
2. Se o guichê estava ocupado nesse intervalo, `area_ocupacao += delta_t`;
3. Atualizar `tempo_ultimo_evento <- relogio`.

Ao final, a utilização aproximada é:

- `utilizacao = area_ocupacao / tempo_total_simulado`.

### 4.3. Número médio de famílias no sistema

De forma análoga, podemos acumular a "área" do número de famílias no sistema ao longo do tempo:

- `area_num_familias` – acumulador da integral do número de famílias no sistema.

Em cada evento:

1. `delta_t = relogio - tempo_ultimo_evento`;
2. `area_num_familias += num_familias_no_sistema * delta_t`;
3. Atualizar `tempo_ultimo_evento <- relogio`.

Ao final:

- `num_medio_cidadaos = area_num_familias / tempo_total_simulado`.

---

## 5. Esboço de pseudocódigo

```pseudo
inicializar_estado_cadunico()
inicializar_estatisticas()
relogio <- 0

inserir_evento(FEL, CHEGADA_CIDADAO, tempo = relogio + tempo_entre_chegadas_cadunico())

enquanto (relogio < T_max):
    evento <- remover_evento_com_menor_tempo(FEL)
    delta_t <- evento.tempo - relogio

    area_num_familias += num_familias_no_sistema * delta_t
    se guiche_ocupado:
        area_ocupacao += delta_t

    relogio <- evento.tempo

    se evento.tipo == CHEGADA_CIDADAO:
        tratar_chegada_cidadao()
    senao se evento.tipo == FIM_ATENDIMENTO:
        tratar_fim_atendimento()

calcular_estatisticas_finais()
exibir_resultados()
```

As funções `tratar_chegada_cidadao()` e `tratar_fim_atendimento()` seguem a lógica descrita nas seções anteriores.

---

## 6. Condições de parada e período de aquecimento (introdução)

Nesta aula, podemos usar uma condição simples, como **tempo máximo de simulação** (por exemplo, um dia de funcionamento do CadÚnico) ou **número de famílias atendidas**.

No entanto, em modelos estocásticos, existe o conceito de **período de aquecimento (warm-up)**:

- No início da simulação, o sistema pode estar em um estado "artificial" (por exemplo, fila vazia ao abrir, quando na realidade pode haver gente esperando antes da abertura);
- Muitas vezes descartamos as observações iniciais para evitar viés;
- Esse tema será aprofundado quando falarmos de **projeto de experimentos**.

---

## 7. Atividade proposta (Aula 5)

1. Baseado nas aulas anteriores e nesta, escreva um **fluxograma** ou pseudocódigo completo para o modelo de CadÚnico com um guichê:
   - definindo claramente: estado, eventos, lógica de chegada/saída, coleta de estatísticas.
2. Identifique quais variáveis você precisa armazenar **por família** (por exemplo, tempo de chegada) e quais podem ser mantidas como **acumuladores globais** (áreas, somas, contadores).
3. (Opcional, se estiver usando uma linguagem de programação): implemente uma primeira versão do simulador dessa CadÚnico simplificado e gere resultados básicos (tempo médio de espera, utilização do guichê), mesmo que sem análise estatística completa.
