# Aula 2 – Conceitos de Simulação de Eventos Discretos

_Disciplina: Modelagem e Simulação de Eventos Discretos_

_Estudo de caso central: **Cadastro Único para Programas Sociais (CadÚnico)**._

## 1. Relembrando a ideia de evento discreto

Na Aula 1 vimos que em modelos de **eventos discretos** o estado do sistema muda apenas em instantes específicos, chamados **eventos**.

No CadÚnico, exemplos de eventos:

- chegada de uma família à central;
- retirada de uma senha;
- início de atendimento em um guichê;
- término de atendimento;
- possível desistência (abandono da fila).

Entre um evento e outro, o estado do sistema (quantas famílias na fila, quais guichês ocupados) é considerado **constante**.

Nesta aula, vamos detalhar como um simulador de eventos discretos é organizado internamente, usando o CadÚnico como exemplo principal.

---

## 2. Componentes básicos de um modelo de eventos discretos

Um modelo de simulação de eventos discretos costuma ser descrito em termos de alguns componentes fundamentais:

1. **Estado do sistema**
2. **Relógio de simulação**
3. **Eventos**
4. **Lista de eventos futuros (Future Event List – FEL)**
5. **Rotinas de inicialização e coleta de estatísticas**

Vamos ver cada um, pensando no CadÚnico.

### 2.1. Estado do sistema

O **estado** é o conjunto de variáveis que descrevem o sistema em um dado instante.

No CadÚnico, exemplos de variáveis de estado:

- número de famílias na fila (ou nas filas, se houver filas separadas por tipo de serviço);
- estado de cada guichê (livre/ocupado, e eventualmente "fechado");
- (opcional) informações associadas a cada família em fila (tipo de serviço, tempo de chegada).

Em uma versão mais detalhada, poderíamos ter:

- `num_familias_fila_cadastramento`, `num_familias_fila_atualizacao`, etc.;
- um vetor representando o estado de cada atendente.

Ao longo da simulação, o estado é atualizado quando eventos ocorrem.

### 2.2. Relógio de simulação

O **relógio de simulação** é uma variável que representa o tempo dentro do mundo simulado.

- Não é o relógio do computador real, mas sim uma variável lógica (por exemplo, `t_sim` em minutos a partir da abertura do dia no CadÚnico);
- Em simulação de eventos discretos, o tempo **salta** de um evento para o próximo relevante.

### 2.3. Eventos

Um **evento** é algo que ocorre em um instante específico e que pode alterar o estado do sistema.

No CadÚnico, podemos definir tipos de evento, como:

- `CHEGADA_CIDADAO`: uma nova família chega à central (e possivelmente retira uma senha);
- `INICIO_ATENDIMENTO`: uma família é chamada de uma fila para um guichê;
- `FIM_ATENDIMENTO`: atendimento termina, liberando o guichê;
- `DESISTENCIA`: uma família desiste e vai embora.

Cada tipo de evento tem:

- um **nome**;
- uma **rotina de tratamento** (o que fazer quando esse evento ocorre);
- um **tempo de ocorrência** (quando vai acontecer, no relógio de simulação).

### 2.4. Lista de eventos futuros (Future Event List – FEL)

A **lista de eventos futuros** é uma estrutura de dados que mantém todos os eventos já agendados para ocorrer **no futuro**, ordenados pelo tempo de ocorrência.

- Pode ser implementada como uma lista ordenada, fila de prioridade, heap, etc.
- Em termos do CadÚnico, a FEL conterá coisas como:
  - a próxima chegada de família;
  - o próximo término de atendimento;
  - (se modelado) o momento em que uma família abandona a fila.

O simulador sempre:

1. Remove o evento com **menor tempo de ocorrência** da FEL;
2. Avança o relógio de simulação para esse tempo;
3. Executa a rotina correspondente ao evento;
4. (Durante a execução) pode agendar novos eventos, inserindo-os na FEL.

### 2.5. Estatísticas e métricas

Além do estado "instantâneo", normalmente queremos medir:

- tempo médio de espera em fila no CadÚnico;
- tempo médio de permanência total (desde a chegada até o fim do atendimento);
- utilização de cada guichê/atendente;
- número médio de famílias no sistema;
- eventualmente, taxa de abandono.

Para isso, mantemos **variáveis de estatística** que são atualizadas conforme a simulação avança (por exemplo, acumulando áreas sob curvas, contadores, somas de tempos, etc.).

---

## 3. Mecanismo de avanço de tempo (next-event time advance)

A forma mais comum de operar um simulador de eventos discretos é o mecanismo de **avanço por próximo evento (next-event time advance)**.

A ideia é:

1. Inicializar o relógio de simulação e o estado do CadÚnico;
2. Agendar os eventos iniciais (por exemplo, a primeira chegada de família após a abertura);
3. Repetir até atingir uma condição de parada:
   - retira-se o **próximo evento** da lista de eventos futuros (o de menor tempo);
   - avança-se o relógio de simulação para o tempo desse evento;
   - executa-se a lógica associada ao evento (atualizando o estado e estatísticas);
   - agenda-se novos eventos futuros (se necessário);
4. Ao fim, calcula-se as métricas de interesse com base nas estatísticas coletadas.

### Comparação com avanço em passo fixo

- **Passo fixo:** o tempo avança em incrementos constantes (por exemplo, 1 minuto) e em cada passo verificamos o que acontece.
  - Mais usado em simulações contínuas.
  - Pode ser ineficiente em sistemas de eventos discretos como o CadÚnico, pois passamos por muitos instantes em que nada acontece.

- **Próximo evento:** o tempo salta diretamente para o próximo instante relevante.
  - Evita desperdício de processamento com períodos "vazios";
  - É o padrão para simulação de eventos discretos.

---

## 4. Esqueleto de um simulador de eventos discretos (CadÚnico simplificado)

A seguir, um esboço em pseudocódigo de um simulador usando avanço por próximo evento para uma versão simples do CadÚnico (fila única + um tipo de atendimento):

```pseudo
inicializar_estado_cadunico()
inicializar_estatisticas()
relogio <- 0

inserir_evento(FEL, tipo = CHEGADA_FAMILIA, tempo = gerar_tempo_primeira_chegada())

enquanto (nao_atingiu_condicao_parada()):
    evento <- remover_evento_com_menor_tempo(FEL)
    relogio <- evento.tempo

    se evento.tipo == CHEGADA_CIDADAO:
        tratar_chegada_cidadao()
    senao se evento.tipo == FIM_ATENDIMENTO:
        tratar_fim_atendimento()
    senao se evento.tipo == DESISTENCIA:
        tratar_desistencia()

calcular_metricas()
exibir_resultados()
```

Onde cada rotina de tratamento de evento pode:

- atualizar o estado das filas e guichês;
- atualizar estatísticas (tempo de espera, utilização, etc.);
- agendar novos eventos (por exemplo, próxima chegada, término de atendimento).

---

## 5. Exemplo conceitual: CadÚnico com um único guichê

Considere uma versão muito simplificada do CadÚnico:

- uma fila única;
- um único guichê de atendimento;
- disciplina de atendimento FIFO.

### Estado

- `num_cidadaos_no_sistema` (inclui fila + em atendimento);
- `guiche_ocupado` (verdadeiro/falso).

### Eventos

- `CHEGADA_CIDADAO`;
- `FIM_ATENDIMENTO`.

### Lógica (intuitiva)

- Quando ocorre **CHEGADA_CIDADAO**:
  - `num_cidadaos_no_sistema <- num_cidadaos_no_sistema + 1`;
  - se o guichê estiver **livre**:
    - marcar `guiche_ocupado <- verdadeiro`;
    - agendar um evento `FIM_ATENDIMENTO` para `relogio + tempo_de_servico()`;
  - agendar a **próxima chegada** (por exemplo, `CHEGADA_CIDADAO` em `relogio + tempo_entre_chegadas()`).

- Quando ocorre **FIM_ATENDIMENTO**:
  - `num_cidadaos_no_sistema <- num_cidadaos_no_sistema - 1`;
  - se `num_cidadaos_no_sistema > 0` (ainda há famílias esperando):
    - agendar novo `FIM_ATENDIMENTO` para `relogio + tempo_de_servico()`;
  - senão:
    - `guiche_ocupado <- falso`.

### Coleta de estatísticas

- Podemos medir, por exemplo:
  - tempo médio de permanência de uma família no CadÚnico;
  - utilização do guichê;
  - tamanho médio da fila.

Isso exige guardar tempos de chegada das famílias, acumular áreas sob curvas de "número de famílias no sistema" etc. (detalhes em aulas posteriores).

---

## 6. Condições de parada

Uma simulação precisa de um critério que indica quando devemos **parar**.

Algumas opções comuns, aplicadas ao CadÚnico:

- **Tempo máximo de simulação:**
  - simular um dia inteiro de funcionamento (por exemplo, 8 horas).

- **Número de famílias atendidas:**
  - parar após atender um certo número de famílias.

- **Estabilidade das estatísticas:**
  - parar quando estimativas (por exemplo, do tempo médio de espera) mudarem pouco com o tempo (mais avançado).

A escolha da condição de parada depende do problema (por exemplo, dimensionar o CadÚnico para um dia típico ou para dias de pico).

---

## 7. Atividade proposta (Aula 2)

Usando o **CadÚnico** como estudo de caso:

1. Liste as variáveis de estado que você considera necessárias para descrever o CadÚnico em um dado instante (por exemplo, número de famílias em cada fila, estado dos guichês).
2. Defina pelo menos 3 tipos de eventos relevantes (por exemplo, chegada, início de atendimento, fim de atendimento, desistência) e explique, em texto, como cada evento altera o estado.
3. Opcional: esboce um pseudocódigo, no estilo do esqueleto apresentado, para o CadÚnico simplificado (uma fila, um tipo de atendimento), com:
   - inicialização;
   - loop principal (remover próximo evento, avançar relógio, tratar evento);
   - condição de parada.

Essa atividade ajuda a transformar a descrição intuitiva do CadÚnico (Aula 1) em uma visão mais estruturada, já alinhada com a implementação de um simulador de eventos discretos.
