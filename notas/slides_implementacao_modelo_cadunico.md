# Slides – Implementação Computacional do Modelo (CadÚnico)

## Slide 1 – Título

**Título:** Implementação Computacional do Modelo  
**Subtítulo:** Simulador de Atendimento Ligado ao CadÚnico

Notas:
> “Nesta aula vamos pegar o modelo que já especificamos e transformar em código. Não focamos na linguagem, e sim na estrutura do simulador.”

---

## Slide 2 – Objetivo da Aula

**Título:** Objetivos

Bullets:
- Revisar o modelo conceitual do processo de atendimento (CadÚnico)
- Traduzir a lógica de eventos para código
- Discutir estruturas de dados para FEL e estado
- Rodar experimentos simples e coletar métricas

Notas:
> “O foco aqui é arquitetura de código de um simulador de eventos discretos.”

---

## Slide 3 – Recap: Modelo Conceitual

**Título:** Recap: Modelo Conceitual (Simplificado)

Bullets:
- 1 fila única de famílias
- `c` atendentes/postos
- Disciplina FIFO, sem prioridades (na versão inicial)
- Eventos:
  - CHEGADA_FAMILIA
  - FIM_ATENDIMENTO
- Parâmetros:
  - taxa de chegada `λ`
  - taxa de serviço `μ` (ou distribuição de atendimento)

Notas:
> “Esse é o ponto de partida da implementação; mais tarde podemos sofisticar o modelo.”

---

## Slide 4 – Arquitetura Geral do Simulador

**Título:** Arquitetura do Simulador

Bullets:
- Componentes principais:
  - Estado (`estado_sistema`)
  - Lista de eventos futuros (FEL)
  - Clock de simulação (`t`)
  - Módulo de aleatoriedade
  - Coleta de estatísticas
- Loop principal:
  - enquanto não atingir condição de parada:
    - retirar próximo evento da FEL
    - avançar `t`
    - processar evento
    - atualizar estatísticas e FEL

Notas:
> “Independentemente da linguagem, essa arquitetura se repete. O resto é detalhe de sintaxe.”

---

## Slide 5 – Representação do Estado

**Título:** Representação do Estado

Bullets (pseudo-Python):

```python
t = 0.0
num_familias_no_sistema = 0
fila = []  # fila de famílias

# atendentes pode ser uma lista de flags ou objetos
# ex.: atendentes = [False] * c  # False = livre, True = ocupado
```

- Outros elementos:
  - `tempo_chegada[fam_id]` para calcular tempos de espera
  - acumuladores para estatísticas

Notas:
> “O importante é que essas variáveis representem o ‘snapshot’ do sistema a qualquer instante da simulação.”

---

## Slide 6 – Representação da FEL

**Título:** Lista de Eventos Futuros (FEL)

Bullets:
- Cada evento pode ser representado por:

```python
Evento = (tempo, tipo, dados)
```

- FEL como:
  - lista ordenada
  - ou priority queue / heap

- Operações básicas:
  - inserir evento na FEL
  - remover evento com menor tempo

Notas:
> “Em Python, por exemplo, um `heapq` funciona bem para gerenciar a FEL.”

---

## Slide 7 – Loop de Processamento de Eventos

**Título:** Loop Principal de Simulação

Bullets (pseudocódigo):

```pseudo
enquanto (t < T_max):
    evento = FEL.remover_min()
    t = evento.tempo

    se evento.tipo == CHEGADA_FAMILIA:
        tratar_chegada_familia(evento)
    senao se evento.tipo == FIM_ATENDIMENTO:
        tratar_fim_atendimento(evento)
```

Notas:
> “Toda a inteligência está nas funções de tratamento de eventos, que implementam a lógica que você já pensou na simulação manual.”

---

## Slide 8 – Implementando CHEGADA_FAMILIA

**Título:** Função `tratar_chegada_familia`

Bullets (pseudocódigo):

```pseudo
funcao tratar_chegada_familia(evento):
    num_familias_no_sistema += 1
    fam_id = novo_id()
    tempo_chegada[fam_id] = t

    se existe_atendente_livre():
        ocupar_atendente_para(fam_id)
        S = tempo_de_servico()
        agendar(FIM_ATENDIMENTO, t + S, fam_id)
    senao:
        fila.append(fam_id)

    A = tempo_entre_chegadas()
    agendar(CHEGADA_FAMILIA, t + A, dados=None)
```

Notas:
> “Repare que a função atualiza o estado, agenda novos eventos e usa as funções de sorteio de tempos.”

---

## Slide 9 – Implementando FIM_ATENDIMENTO

**Título:** Função `tratar_fim_atendimento`

Bullets (pseudocódigo):

```pseudo
funcao tratar_fim_atendimento(evento):
    fam_id = evento.fam_id
    num_familias_no_sistema -= 1

    W = t - tempo_chegada[fam_id]
    soma_tempos_permanencia += W
    num_familias_atendidas += 1

    se fila não está vazia:
        fam2 = fila.pop(0)
        ocupar_atendente_para(fam2)
        S = tempo_de_servico()
        agendar(FIM_ATENDIMENTO, t + S, fam2)
    senao:
        liberar_atendente(evento.atendente)
```

Notas:
> “Aqui é onde atualizamos as estatísticas de tempo de permanência e gerenciamos a fila.”

---

## Slide 10 – Coleta de Estatísticas

**Título:** Coleta de Estatísticas

Bullets:
- Acumuladores globais:
  - `soma_tempos_permanencia`
  - `num_familias_atendidas`
  - `area_num_familias`
  - `area_ocupacao`
- Atualização em cada evento:

```pseudo
delta_t = t - tempo_ultimo_evento
area_num_familias += num_familias_no_sistema * delta_t
se algum_atendente_ocupado:
    area_ocupacao += delta_t

tempo_ultimo_evento = t
```

- Cálculos finais:
  - `tempo_medio_permanencia = soma_tempos_permanencia / num_familias_atendidas`
  - `num_medio_familias = area_num_familias / tempo_total`
  - `utilizacao_media = area_ocupacao / tempo_total`

Notas:
> “Esse padrão de ‘integrar’ quantidades ao longo do tempo aparece em qualquer simulador de eventos discretos.”

---

## Slide 11 – Controle de Experimentos

**Título:** Rodando Experimentos

Bullets:
- Parâmetros externos:
  - `lambda`, `mu`, número de atendentes
  - tempo total simulado `T_max`
- Experimentos:
  - várias replicações com seeds diferentes
  - comparação de cenários (3, 4, 5 atendentes, por exemplo)
- Saídas:
  - salvar resultados em CSV para análise em Python/R/Excel

Notas:
> “Transformar o simulador em uma ‘fábrica de cenários’ é o que permite fazer estudos de dimensionamento.”

---

## Slide 12 – Exercícios – Implementação

**Título:** Exercícios – Implementação do Modelo

Bullets:
- Implementar um simulador básico com:
  - 1 fila, `c` atendentes
  - eventos CHEGADA_FAMILIA e FIM_ATENDIMENTO
- Rodar pelo menos 2 cenários (diferentes números de atendentes)
- Para cada cenário, obter:
  - tempo médio de espera
  - utilização dos atendentes
- Escrever uma breve interpretação dos resultados

Notas:
> “O objetivo é sair da teoria e ter um programa funcional que simula o processo de atendimento e gera números para análise.”
