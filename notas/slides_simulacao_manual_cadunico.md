# Slides – Simulação Manual e Especificação de Modelos (CadÚnico)

## Slide 1 – Título

**Título:** Simulação Manual e Especificação de Modelos  
**Subtítulo:** Processos de Atendimento Ligados ao CadÚnico

Notas:
> “Nesta aula, vamos pegar um processo ligado ao CadÚnico (por exemplo, atendimento em um CRAS) e descer um nível: especificar o modelo com mais detalhes e simular alguns passos ‘na mão’ para entender o funcionamento.”

---

## Slide 2 – Objetivo da Aula

**Título:** Objetivos

Bullets:
- Especificar formalmente um modelo simples de atendimento ligado ao CadÚnico
- Entender a lógica de eventos e atualização de estado
- Realizar uma **simulação manual** de alguns eventos
- Preparar o terreno para implementação computacional

Notas:
> “A ideia é que, ao final da aula, você saiba pegar um cenário de atendimento (cadastro/atualização) e escrever o modelo e alguns passos de simulação no papel ou na planilha.”

---

## Slide 3 – Modelo Simplificado de Atendimento (CadÚnico)

**Título:** Modelo Simplificado de Atendimento

Bullets:
- Uma fila única de famílias
- Um ou mais atendentes/postos de atendimento
- Disciplina de atendimento: FIFO (por ordem de chegada/senha)
- Eventos principais:
  - CHEGADA_FAMILIA
  - INICIO_ATENDIMENTO (se modelado separado)
  - FIM_ATENDIMENTO
  - (Opcional) DESISTENCIA

Notas:
> “Começamos com uma versão básica. Depois podemos detalhar por tipo de atendimento, prioridades e outras regras.”

---

## Slide 4 – Especificação do Estado

**Título:** Especificação do Estado do Sistema

Bullets:
- Variáveis de estado (exemplo de modelo simples):
  - `t` – tempo de simulação
  - `num_familias_no_sistema`
  - `atendentes[i].estado` (livre/ocupado)
  - `fila` – lista de famílias esperando
  - registrador de tempos de chegada (para estatísticas)
- Essas variáveis devem ser atualizadas em cada evento

Notas:
> “Aqui você define o ‘snapshot’ do sistema em qualquer instante. Na simulação manual, vamos acompanhar essas variáveis linha a linha.”

---

## Slide 5 – Especificação de Eventos

**Título:** Especificação de Eventos

Bullets:
- Para cada evento, definir:
  - quando é agendado
  - efeito sobre o estado
  - novos eventos agendados
- Exemplos:
  - **CHEGADA_FAMILIA**:
    - aumenta `num_familias_no_sistema`
    - se houver atendente livre, inicia atendimento
    - agenda próxima chegada
  - **FIM_ATENDIMENTO**:
    - diminui `num_familias_no_sistema`
    - se houver alguém na fila, inicia próximo atendimento

Notas:
> “Essa é a ‘tabela verdade’ do modelo: evento X acontece → quais variáveis mudam e quais novos eventos entram na lista de eventos futuros.”

---

## Slide 6 – Lista de Eventos Futuros (FEL)

**Título:** Lista de Eventos Futuros (FEL)

Bullets:
- Estrutura ordenada por tempo de ocorrência:
  - (tipo de evento, tempo, dados da família, etc.)
- Em simulação manual:
  - usar uma tabela ordenada por tempo
- Loop básico:
  - pegar o evento com menor tempo
  - avançar `t` até esse tempo
  - processar evento
  - atualizar FEL

Notas:
> “Na mão, a FEL pode ser só uma tabela ordenada, mas a lógica é a mesma que o computador vai usar depois.”

---

## Slide 7 – Cenário para Simulação Manual

**Título:** Cenário Exemplo (1 Atendente)

Bullets:
- Suposições para o exercício:
  - 1 atendente
  - famílias chegam em tempos pré-definidos (ex.: 0, 2, 4, 7, 10 minutos)
  - tempos de atendimento pré-definidos (ex.: 3, 2, 4, 3, 2 minutos)
- Objetivo:
  - simular manualmente a evolução da fila
  - calcular tempo de espera e tempo de permanência

Notas:
> “Para simulação manual, escolhemos números concretos, não sorteios. Depois substituímos isso por tempos gerados aleatoriamente.”

---

## Slide 8 – Tabela de Simulação Manual

**Título:** Tabela de Simulação Manual

Sugestão de colunas:
- Evento nº
- Tipo de evento
- Tempo do evento (t)
- `num_familias_no_sistema`
- Estado do atendente (livre/ocupado)
- Tamanho da fila
- Observações (quem chegou, quem saiu, etc.)

Notas:
> “Essa tabela é o ‘log’ da simulação. Em aula, você pode preencher 5–10 eventos com a turma para que eles vejam a dinâmica.”

---

## Slide 9 – Exemplo Passo a Passo

**Título:** Exemplo – Primeiros Eventos

Bullets (conceito):
- Evento 1: CHEGADA_FAMILIA em t = 0
  - atendente livre → inicia atendimento
  - agenda FIM_ATENDIMENTO em t = 0 + tempo_atendimento_1
- Evento 2: CHEGADA_FAMILIA em t = 2
  - atendente ocupado → entra na fila
- Evento 3: FIM_ATENDIMENTO em t = 3
  - chama próxima família da fila
  - agenda novo FIM_ATENDIMENTO

Notas:
> “Aqui você guia a turma: ‘o que acontece agora?’, ‘quem está na fila?’, ‘quando vamos ter o próximo evento?’. A ideia é internalizar a lógica antes de programar.”

---

## Slide 10 – Especificação de Modelo – Checklist

**Título:** Especificação de Modelo – Checklist

Bullets:
- Definir:
  - objetivo do modelo (ex.: tempo de espera, backlog de atualizações)
  - fronteiras do sistema
- Especificar:
  - variáveis de estado
  - eventos e suas rotinas
  - parâmetros (taxas de chegada, distribuição de tempos de atendimento)
- Planejar:
  - condições de parada (tempo simulado, nº de famílias atendidas)
  - métricas a coletar (espera, utilização, etc.)

Notas:
> “Antes de abrir o editor de código, essa especificação deve estar clara. Esta aula é justamente sobre escrever esse ‘contrato’ do modelo.”

---

## Slide 11 – Ligação com Implementação

**Título:** Da Simulação Manual ao Código

Bullets:
- O que a simulação manual nos dá:
  - entendimento do fluxo de eventos
  - clareza sobre estado e variáveis
- Próximo passo:
  - traduzir a lógica da tabela em código
  - implementar FEL como estrutura de dados
  - substituir tempos fixos por tempos aleatórios

Notas:
> “Quem sabe simular na mão está muito mais preparado para depurar o código depois, porque entende o que o simulador ‘deveria’ estar fazendo.”

---

## Slide 12 – Exercícios – Simulação Manual

**Título:** Exercícios – Simulação Manual

Bullets:
- Especificar formalmente o modelo de atendimento com 1 atendente:
  - estado, eventos e parâmetros
- Simular manualmente os 10 primeiros eventos para um conjunto de tempos de chegada/atendimento dado
- Calcular:
  - tempo de espera de cada família
  - tempo médio de espera
  - utilização aproximada do atendente

Notas:
> “Esses exercícios consolidam a especificação e a simulação manual, preparando para a próxima etapa: implementação e experimentos.”
