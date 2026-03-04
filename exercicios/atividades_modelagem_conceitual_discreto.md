# Atividades de Modelagem Conceitual — Eventos Discretos
## Disciplina: Modelagem e Simulação de Eventos Discretos

---

## 📌 Atividade 1: Identificação de Componentes em Sistemas Reais
**Objetivo:** Reconhecer estado, eventos e variáveis em sistemas discretos

### Sistema: Fila de Atendimento (Banco, Farmácia, Etc.)

#### 1.1 Defina:

**Estado do Sistema:**
- O que muda ao longo do tempo? (liste as variáveis)
  - Exemplo: número de famílias na fila, número de atendentes ocupados, tempo total aguardado, etc.

**Eventos:**
- Quais mudanças abruptas de estado ocorrem?
  - Exemplo: chegada de família, início de atendimento, término de atendimento

**Variáveis de Entrada (Parâmetros):**
- Taxa de chegada (famílias por hora)
- Tempo médio de atendimento
- Número de caixas disponíveis

**Variáveis de Saída (Métricas de Interesse):**
- Tempo médio na fila
- Tempo máximo na fila
- Utilização do caixa (%)
- Número médio na fila

#### 1.2 Desenhe um Diagrama de Transição de Estados:
```
Exemplo estrutura (você preenche os estados):

    [0 na fila] --chegada--> [1 na fila] --chegada--> [2 na fila] ...
         |                        |                        |
         +--término--> [0]        +--término--> [1]       ...

Legenda:
  - Retângulos = estados
  - Setas = eventos
  - Rótulos = tipo de evento
```

#### 1.3 Tabela de Eventos:

| Evento | Condição | Atualização de Estado |
|--------|----------|----------------------|
| Chegada | - | Incrementar fila, agendar próximo evento |
| Início de Serviço | Caixa disponível | Decrementar fila, marcar caixa ocupado |
| Término de Serviço | - | Liberar caixa, coletar estatísticas |

---

## 📊 Atividade 2: Modelagem do CadÚnico como Sistema Discreto
**Objetivo:** Aplicar conceitos de eventos discretos a dados sociais

### Contexto:
O CadÚnico é um sistema dinâmico onde famílias sofrem mudanças:
- Nascimentos, mortes
- Mudanças de emprego/renda
- Acesso a programas (Bolsa Família)
- Mudanças de residência

#### 2.1 Defina Componentes:

**Entidade Principal:** Família

**Estado de uma Família:**
```
Família {
  id: int
  tamanho: int (número de pessoas)
  renda_media: float (R$)
  acesso_agua: string (rede, poço, cisterna, etc.)
  tem_bolsa_familia: bool
  regiao: string (IBGE)
  composicao_etaria: list [idade1, idade2, ...]
}
```

**Eventos Possíveis:**
1. Nascimento de membro
   - Trigger: tempo aleatório (distribuição por idade da mãe)
   - Atualização: +1 no tamanho, recalcular renda per capita

2. Morte de membro
   - Trigger: tempo aleatório (distribuição por idade)
   - Atualização: -1 no tamanho, recalcular renda

3. Mudança de emprego
   - Trigger: tempo aleatório (taxa de desemprego/recolocação)
   - Atualização: nova renda, recalcular elegibilidade Bolsa Família

4. Migração para outra região
   - Trigger: tempo aleatório
   - Atualização: alterar região, possivelmente acesso a serviços

5. Inclusão/Exclusão de Bolsa Família
   - Trigger: evento de renda ou verificação trimestral
   - Atualização: flag de elegibilidade

#### 2.2 Desenhe Diagrama de Eventos:

```
                    [Simulação Iniciada]
                            |
                    Agendar Eventos Iniciais:
                    - Próxima chegada
                    - Próximo nascimento
                    - Próxima morte
                    - Próxima mudança de renda
                            |
                    +--------v--------+
                    | Loop Principal  |
                    +--------+--------+
                             |
            Selecionar próximo evento com menor tempo
                             |
          +--Nascimento--+  +--Morte--+  +--Renda--+  ...
          |              |  |         |  |         |
          v              v  v         v  v         v
    [Atualizar]    [Atualizar]  [Recalcular] [...]
         |              |          |
         +--Reagendar--Eventos--+
                    |
        Tempo_Simulação < Tempo_Final?
          /                        \
        SIM                         NÃO
        |                            |
    [Voltar ao Loop]        [Fim da Simulação]
        |                            |
        +----> Coletar Estatísticas <+
```

---

## 🔄 Atividade 3: Pseudocódigo de Simulador de Eventos Discretos
**Objetivo:** Entender estrutura básica antes de implementar

### Versão 1: Simulador Genérico de Fila M/M/1

```pseudocode
ALGORITMO SimuladorFila

VARIÁVEIS GLOBAIS:
  relógio ← 0
  lista_eventos ← fila vazia ordenada por tempo
  num_clientes_fila ← 0
  caixa_ocupado ← FALSO
  tempo_total_fila ← 0
  num_atendimentos ← 0

FUNÇÃO AgendeEvento(tipo, tempo_evento):
  CRIE evento = {tipo: tipo, tempo: tempo_evento}
  INSIRA evento em lista_eventos (mantendo ordem crescente)

FUNÇÃO ProximoEvento():
  RETORNE evento com menor tempo em lista_eventos
  REMOVA evento de lista_eventos

FUNÇÃO ProcessaChegada():
  relógio ← relógio + tempo_até_próxima_chegada
  num_clientes_fila ← num_clientes_fila + 1

  SE caixa_ocupado = FALSO:
    ProcessaInícioServiço()

  AgendeEvento("CHEGADA", relógio + TempoInterchegada())

FUNÇÃO ProcessaInícioServiço():
  SE num_clientes_fila > 0 E caixa_ocupado = FALSO:
    caixa_ocupado ← VERDADEIRO
    num_clientes_fila ← num_clientes_fila - 1
    AgendeEvento("TÉRMINO", relógio + TempoAtendimento())

FUNÇÃO ProcessaTermino():
  caixa_ocupado ← FALSO
  num_atendimentos ← num_atendimentos + 1

  SE num_clientes_fila > 0:
    ProcessaInícioServiço()

PROGRAMA PRINCIPAL:
  LEIA tempo_simulação, taxa_chegada, tempo_médio_serviço

  // Inicialização
  AgendeEvento("CHEGADA", TempoInterchegada())

  // Loop de simulação
  ENQUANTO relógio < tempo_simulação:
    evento ← ProximoEvento()
    relógio ← evento.tempo

    ESCOLHA evento.tipo:
      CASO "CHEGADA":
        ProcessaChegada()
      CASO "INÍCIO_SERVIÇO":
        ProcessaInícioServiço()
      CASO "TÉRMINO":
        ProcessaTermino()

  // Cálculos finais
  tempo_médio_fila ← tempo_total_fila / num_atendimentos
  utilização_caixa ← (tempo_simulação - tempo_caixa_livre) / tempo_simulação

  ESCREVA "Tempo médio na fila: ", tempo_médio_fila
  ESCREVA "Utilização: ", utilização_caixa * 100, "%"
```

### Versão 2: Simulador CadÚnico (Dinâmica Familiar)

```pseudocode
ALGORITMO SimuladorCadUnico

VARIÁVEIS GLOBAIS:
  relógio ← 0
  lista_eventos ← fila vazia
  população ← lista de famílias
  estatísticas ← {renda_média, pop_total, bolsa_familia_count}

ESTRUTURA Família:
  id: inteiro
  tamanho: inteiro
  renda: real
  membros: lista de {idade, ativo}
  região: string
  tem_bolsa: booleano

FUNÇÃO AgendeEvento(familia_id, tipo_evento, tempo):
  evento ← {familia_id, tipo, tempo}
  INSIRA em lista_eventos (ordenado por tempo)

FUNÇÃO ProcessaNascimento(familia_id):
  familia ← população[familia_id]

  // Verifica se há mulher em idade fértil
  SE ExisteMulherFértil(familia):
    // Adiciona novo membro
    INSIRA {idade: 0, ativo: VERDADEIRO} em familia.membros
    familia.tamanho ← familia.tamanho + 1

    // Recalcula renda per capita
    familia.renda ← familia.renda / (familia.tamanho - 1) * familia.tamanho

    // Reagenda próximo nascimento
    tempo_próximo_nascimento ← relógio + AmostraDistribuicaoBirthRate()
    AgendeEvento(familia_id, "NASCIMENTO", tempo_próximo_nascimento)

FUNÇÃO ProcessaMorte(familia_id):
  familia ← população[familia_id]

  // Seleciona membro aleatório por probabilidade de idade
  membro ← SelecionaMembroPorIdade(familia)

  SE membro ≠ NULO:
    REMOVA membro de familia.membros
    familia.tamanho ← familia.tamanho - 1

    // Recalcula renda per capita
    SE familia.tamanho > 0:
      familia.renda ← familia.renda * (familia.tamanho + 1) / familia.tamanho
    SENÃO:
      REMOVA familia de população

  // Reagenda próxima morte
  tempo_próxima_morte ← relógio + AmostraDistribuicaoMortalidade()
  AgendeEvento(familia_id, "MORTE", tempo_próxima_morte)

FUNÇÃO ProcessaMudançaRenda(familia_id):
  familia ← população[familia_id]

  // Simula mudança de emprego/oportunidade
  mudanca ← AmostraDistribuicaoRendaChange()
  familia.renda ← familia.renda * (1 + mudanca)

  // Verifica elegibilidade Bolsa Família
  SE familia.renda < LIMITE_BOLSA E não tem_bolsa:
    familia.tem_bolsa ← VERDADEIRO
    familia.renda ← familia.renda + BOLSA_VALOR_MENSAL
  SENÃO SE familia.renda >= LIMITE_BOLSA E tem_bolsa:
    familia.tem_bolsa ← FALSO
    familia.renda ← familia.renda - BOLSA_VALOR_MENSAL

  // Reagenda próxima mudança
  tempo_próxima_mudança ← relógio + INTERVALO_MUDANÇA_RENDA
  AgendeEvento(familia_id, "MUDANÇA_RENDA", tempo_próxima_mudança)

PROGRAMA PRINCIPAL:
  LEIA população_inicial, tempo_simulação, cenário

  // Inicialização: agenda eventos para cada família
  PARA CADA familia EM população_inicial:
    AgendeEvento(familia.id, "NASCIMENTO", relógio + AmostraRate())
    AgendeEvento(familia.id, "MORTE", relógio + AmostraRate())
    AgendeEvento(familia.id, "MUDANÇA_RENDA", relógio + AmostraRate())

  // Loop de simulação
  ENQUANTO relógio < tempo_simulação:
    evento ← ProximoEvento()
    relógio ← evento.tempo

    ESCOLHA evento.tipo:
      CASO "NASCIMENTO":
        ProcessaNascimento(evento.familia_id)
      CASO "MORTE":
        ProcessaMorte(evento.familia_id)
      CASO "MUDANÇA_RENDA":
        ProcessaMudançaRenda(evento.familia_id)
      CASO "VERIFICAÇÃO_CENÁRIO":
        AplicaCenarioIntervencao(cenário)

  // Coleta estatísticas finais
  renda_média ← CalculaRendaMedia(população)
  gini ← CalculaGini(população)
  pop_com_bolsa ← ContaComBolsa(população)

  ESCREVA "Relatório Final:"
  ESCREVA "  Renda média: R$", renda_média
  ESCREVA "  Gini: ", gini
  ESCREVA "  Com Bolsa: ", pop_com_bolsa, "%"
```

---

## 🎯 Atividade 4: Estruturas de Dados para Lista de Eventos
**Objetivo:** Implementar eficientemente a lista de eventos

### 4.1 Estrutura de Evento:

```python
# Em Python (pseudocódigo real)

class Evento:
    def __init__(self, tempo, tipo, entidade_id, dados=None):
        self.tempo = tempo          # Quando o evento ocorre
        self.tipo = tipo            # "CHEGADA", "TÉRMINO", etc.
        self.entidade_id = entidade_id  # Qual família
        self.dados = dados or {}    # Dados adicionais

    def __lt__(self, outro):
        # Comparação para ordenação
        return self.tempo < outro.tempo

class ListaEventosFuturos:
    def __init__(self):
        import heapq
        self.eventos = []  # Min-heap por tempo

    def agenda(self, evento):
        heapq.heappush(self.eventos, evento)

    def proximo(self):
        if self.eventos:
            return heapq.heappop(self.eventos)
        return None

    def vazia(self):
        return len(self.eventos) == 0
```

### 4.2 Exercício Prático:

**Tarefa:** Implemente a lista de eventos em Python e teste:

```python
# Código a ser completado pelos alunos

def teste_lista_eventos():
    lista = ListaEventosFuturos()

    # TODO: Insira 5 eventos em tempos desordenados
    # lista.agenda(Evento(...))

    # TODO: Extraia eventos em ordem crescente de tempo
    # e verifique se saem na ordem correta

    print("Teste passou!")
```

---

## 📈 Atividade 5: Coleta e Cálculo de Estatísticas
**Objetivo:** Instrumentar simulador para coleta de métricas

### 5.1 Exemplo: Fila M/M/1

```pseudocode
CLASSE ColeturEstatísticas:

  VARIÁVEIS:
    tempo_entradas: lista de tempos de chegada
    tempo_saídas: lista de tempos de saída
    tamanho_fila: lista de (tempo, tamanho)

  MÉTODO Registra_Entrada(tempo):
    INSIRA tempo em tempo_entradas

  MÉTODO Registra_Saída(tempo):
    INSIRA tempo em tempo_saídas

  MÉTODO Calcula_Tempo_Médio_Sistema():
    PARA i = 1 ATÉ tamanho(tempo_saídas):
      tempo_sistema[i] ← tempo_saídas[i] - tempo_entradas[i]
    RETORNE média(tempo_sistema)

  MÉTODO Calcula_Tempo_Médio_Fila():
    // Tempo em fila = Tempo no sistema - Tempo de serviço
    tempo_fila ← tempo_sistema - tempo_serviço
    RETORNE média(tempo_fila)

  MÉTODO Calcula_Utilização(tempo_total):
    tempo_serviço_total ← soma(tempo_saídas - tempo_entradas)
    RETORNE tempo_serviço_total / tempo_total
```

### 5.2 Exercício: Calcule Estatísticas de Cenários CadÚnico

**Dado:**
- Simulação com 1000 famílias por 10 anos
- Cenário 1: sem intervenção
- Cenário 2: com Bolsa Família

**Calcule:**

| Métrica | Cenário 1 | Cenário 2 | Diferença |
|---------|-----------|-----------|-----------|
| Renda média inicial | ? | ? | ? |
| Renda média final | ? | ? | ? |
| Gini inicial | ? | ? | ? |
| Gini final | ? | ? | ? |
| % com Bolsa final | ? | ? | ? |

---

## 🔗 Atividade 6: Diagramas UML para Modelagem
**Objetivo:** Usar notação formal para definir estrutura

### 6.1 Diagrama de Classes (Fila):

```
┌──────────────┐        ┌────────────────┐
│   Família    │        │    Servidor    │
├──────────────┤        ├────────────────┤
│ id: int      │        │ id: int        │
│ chegada: tim │        │ disponível: bool│
│ serviço: tim │        │ familia_atual  │
│ saída: time  │        │ tempo_livre    │
└──────────────┘        └────────────────┘
       │                        │
       │ "atendido_por"         │
       └────────────────────────┘

┌──────────────────────┐
│    Simulador         │
├──────────────────────┤
│ relógio: float       │
│ familias: list       │
│ servidores: list     │
│ eventos: FEL         │
├──────────────────────┤
│ processa_chegada()   │
│ processa_saída()     │
│ coleta_stats()       │
└──────────────────────┘
```

### 6.2 Seu Turno: Desenhe Diagrama para CadÚnico

**Classe:** Família, Membro, SimuladorCadUnico, ColeturEstatísticas

---

## 🧪 Atividade 7: Análise de Sensibilidade
**Objetivo:** Entender como parâmetros afetam resultados

### Exemplo: Fila M/M/1

```pseudocode
ALGORITMO AnaliseSegibilidade

PARA taxa_chegada DE 0.1 ATÉ 0.9 PASSO 0.1:
  PARA tempo_médio_serviço DE 0.5 ATÉ 3.0 PASSO 0.5:

    resultado ← SimulaFila(taxa_chegada, tempo_médio_serviço)

    ESCREVA taxa_chegada, ",", tempo_médio_serviço, ",", resultado.tempo_fila
```

### Para CadÚnico:

Teste impacto de cada parâmetro em Gini:
- Taxa de natalidade: +20%, +50%, -20%
- Taxa de desemprego: +10%, +30%
- Valor da Bolsa Família: R$ 0, R$ 100, R$ 300, R$ 500

**Resultado:** Tabela com Gini para cada combinação

---

## 📋 Atividade 8: Mini-Projeto — Simulador de Atendimento (Bancário)
**Objetivo:** Integrar conceitos em código funcional

### Especificação:

**Sistema:** Banco com 2 caixas

**Eventos:**
- Chegada de cliente (Poisson, média 5 min)
- Início de atendimento (1º disponível)
- Término (normal: 10 min, prioritário: 5 min)

**Prioridade:** 20% dos clientes são prioritários

**Simulação:** 8 horas

**Métricas:**
- Tempo médio na fila (comum e prioritário)
- Tempo máximo na fila
- Utilização dos caixas
- % de clientes prioritários que esperam < 2 min

### Entregável:

1. Diagrama de eventos e fluxo
2. Pseudocódigo comentado
3. Código Python/Java completo
4. Relatório com gráficos de:
   - Tamanho da fila ao longo do tempo
   - Histograma de tempos de espera
   - Utilização por caixa

---

## 📚 Checklist de Aprendizado

Após completar estas atividades, você deve ser capaz de:

- [ ] Identificar estado, eventos e variáveis em um sistema
- [ ] Desenhar diagrama de transição de estados
- [ ] Escrever pseudocódigo de simulador de eventos discretos
- [ ] Implementar lista de eventos futuros (FEL)
- [ ] Coletar e calcular estatísticas de simulação
- [ ] Diferenciar "verificação" de "validação"
- [ ] Realizar análise de sensibilidade
- [ ] Modelar sistema real com eventos discretos

---

## 🎓 Dicas Pedagógicas

1. **Comece com exemplo simples** (fila M/M/1) antes de CadÚnico
2. **Desenhe antes de programar** — pseudocódigo previne erros
3. **Use nomes descritivos** para eventos: CHEGADA_CLIENTE, não EVENTO_1
4. **Incremente complexidade**: 1 caixa → 2 caixas → múltiplos servidores
5. **Valide com cálculo analítico** (se possível) antes de confiabilidade simulação

