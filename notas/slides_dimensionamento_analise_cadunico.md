# Slides – Dimensionamento e Análise de Resultados (CadÚnico)

## Slide 1 – Título

**Título:** Dimensionamento e Análise de Resultados  
**Subtítulo:** Simulação de Atendimento Ligado ao CadÚnico

Notas:
> “Agora vamos usar o simulador para responder perguntas de dimensionamento e analisar os resultados em termos de atendimento a famílias.”

---

## Slide 2 – Objetivos

**Título:** Objetivos da Aula

Bullets:
- Definir problemas de dimensionamento em processos de atendimento ligados ao CadÚnico
- Planejar experimentos de simulação (cenários, replicações, métricas)
- Analisar resultados: espera, utilização, atendimentos/dia
- Discutir trade-offs custo vs serviço

Notas:
> “Vamos ver como transformar resultados de simulação em recomendações de gestão.”

---

## Slide 3 – Problema de Dimensionamento

**Título:** Problema de Dimensionamento

Bullets:
- Filas longas em períodos de maior demanda (prazos de atualização, campanhas)
- Recursos (atendentes) e orçamento limitados
- Pergunta central:
  - quantos atendentes e qual escala de atendimento atenderiam bem as famílias?

Notas:
> “É o clássico problema de capacidade: quanto recurso é suficiente sem desperdiçar dinheiro público?”

---

## Slide 4 – Métricas de Desempenho

**Título:** Métricas de Desempenho

Bullets:
- Tempo médio de espera em fila
- Tempo médio de permanência no sistema
- Utilização média dos atendentes
- Número médio de famílias atendidas por dia/período
- (Opcional) Taxa de abandono

Notas:
> “São essas métricas que vamos usar para comparar cenários.”

---

## Slide 5 – Definição de Cenários

**Título:** Definição de Cenários – N.º de Atendentes

Bullets:
- Fatores:
  - número de atendentes ativos
  - distribuição de atendentes por horário
- Exemplos de cenários:
  - A: 3 atendentes o período todo (atual)
  - B: 4 atendentes o período todo
  - C: 3 atendentes padrão, 5 no pico da manhã
  - D: 3 atendentes padrão, 5 no pico da manhã e tarde

Notas:
> “Cenários precisam ser realistas do ponto de vista operacional.”

---

## Slide 6 – Plano de Experimentos

**Título:** Plano de Experimentos de Simulação

Bullets:
- Para cada cenário:
  - rodar `n` replicações independentes
  - usar seeds diferentes
- Tratar warm-up:
  - descartar primeiro período de simulação ou primeiros N atendimentos
- Para cada replicação, registrar:
  - tempo médio de espera
  - utilização
  - atendimentos/dia

Notas:
> “Sem replicações, um único resultado pode ser puro acaso.”

---

## Slide 7 – Estrutura dos Resultados

**Título:** Estrutura de Dados de Saída

Bullets:
- Tabela de resultados:

| Cenário | Replicação | Tempo_médio_espera | Utilização | Atendimentos_dia |
|---------|------------|--------------------|------------|------------------|

- Agregação por cenário:
  - média das replicações
  - desvio padrão
  - (opcional) intervalo de confiança

Notas:
> “Essa tabela pode ser exportada para CSV e analisada em Python, R ou Excel.”

---

## Slide 8 – Análise do Tempo de Espera

**Título:** Analisando Tempo Médio de Espera

Bullets:
- Comparar tempo médio de espera entre cenários
- Perguntas:
  - todos os cenários atendem a meta (ex.: ≤ 20 min)?
  - quanto um atendente a mais reduz o tempo de espera?
  - o reforço só no pico é suficiente?

Notas:
> “Um gráfico de barras com tempo médio de espera por cenário ajuda muito a visualização.”

---

## Slide 9 – Análise da Utilização

**Título:** Analisando Utilização dos Atendentes

Bullets:
- Verificar se atendentes:
  - estão subutilizados (ex.: < 50%)
  - estão saturados (ex.: > 90%)
- Meta típica:
  - utilização em faixa saudável (ex.: 70–85%)

Perguntas:
- cenário com mais atendentes reduziu demais a utilização?
- isso é aceitável em termos de custo?

Notas:
> “Utilização muito baixa indica excesso de capacidade; muito alta indica risco de filas explosivas.”

---

## Slide 10 – Custo vs Serviço

**Título:** Trade-offs Custo vs Nível de Serviço

Bullets:
- Cada atendente adicional:
  - tem custo (salário, infraestrutura)
- Em contrapartida:
  - reduz tempo de espera
  - reduz abandono
- Pergunta de gestão:
  - vale a pena pagar por mais atendentes para ganhar X minutos a menos de espera?

Notas:
> “Aqui entra a conversa com gestão: a simulação quantifica o ganho; a decisão final é política/gerencial.”

---

## Slide 11 – Exemplo de Conclusão

**Título:** Exemplo de Conclusão de Estudo

Bullets (exemplo):
- Cenário A (3 atendentes):
  - tempo médio ≈ 30 min, utilização ≈ 95%
- Cenário B (4 atendentes):
  - tempo médio ≈ 18 min, utilização ≈ 80%
- Cenário C (5 atendentes no pico):
  - tempo médio no pico ≈ 12 min, utilização ≈ 75%

Possível recomendação:
- adotar Cenário C em períodos de alta demanda

Notas:
> “Esse tipo de conclusão é o que você leva para uma reunião com a gestão da política social.”

---

## Slide 12 – Exercícios – Dimensionamento

**Título:** Exercícios – Estudo de Dimensionamento

Bullets:
- Escolher 2–3 cenários de configuração de atendentes
- Rodar experimentos de simulação com replicações
- Construir tabela com:
  - tempo médio de espera
  - utilização dos atendentes
- Escrever mini-relatório:
  - contexto
  - metodologia
  - resultados
  - recomendação

Notas:
> “Essa atividade já pode ser usada como trabalho avaliativo, simulando um relatório de consultoria.”
