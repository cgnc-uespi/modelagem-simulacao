# Slides – Introdução ao Simulador de Atendimento (CadÚnico)

## Slide 1 – Título

**Título:** Introdução ao Simulador de Atendimento  
**Subtítulo:** Processos de Atendimento Ligados ao CadÚnico

Notas:
> “Nesta aula vamos sair do papel e olhar para um simulador ‘de verdade’ de atendimento, baseado no modelo de processos ligados ao CadÚnico (por exemplo, atendimento em um CRAS).”

---

## Slide 2 – Objetivo da Aula

**Título:** Objetivos

Bullets:
- Apresentar um simulador de filas baseado em um modelo de atendimento ao CadÚnico
- Entender a interface: entradas (parâmetros) e saídas (resultados)
- Relacionar cada parte da interface com o modelo de eventos discretos
- Rodar pequenos experimentos guiados

Notas:
> “Não é aula de programação; é aula de como usar e interpretar um simulador de atendimento.”

---

## Slide 3 – Do Modelo ao Simulador

**Título:** Do Modelo Conceitual ao Simulador

Bullets:
- Modelo conceitual:
  - filas, atendentes, chegadas, atendimentos
- Implementação computacional:
  - código que executa o loop de eventos
- Simulador de atendimento:
  - interface para configurar parâmetros
  - motor de simulação por baixo

Notas:
> “O simulador é um ‘casaco bonito’ vestido no modelo que estava em pseudocódigo.”

---

## Slide 4 – Entradas do Simulador

**Título:** Entradas do Simulador

Bullets:
- Parâmetros de chegada:
  - taxa média de chegadas (λ)
  - padrão por hora (se existir)
- Parâmetros de atendimento:
  - média de tempo de serviço (1/μ)
  - escolha da distribuição (exponencial, lognormal, etc.)
- Configuração:
  - número de atendentes/postos
  - tempo/horário de simulação
- Opções de execução:
  - número de replicações
  - seed (opcional)

Notas:
> “Cada campo da interface corresponde a algo que você conhece do modelo: λ, μ, número de servidores, tempo de simulação.”

---

## Slide 5 – Saídas do Simulador

**Título:** Saídas do Simulador

Bullets:
- Métricas numéricas:
  - tempo médio de espera
  - tempo médio de permanência
  - utilização dos atendentes
  - número de famílias atendidas
- Visualizações:
  - evolução do número de famílias no sistema
  - distribuição de tempos de espera
- Resumo por cenário:
  - comparação de diferentes configurações de atendentes

Notas:
> “Esses números são as respostas para as perguntas de gestão: ‘quanto tempo as famílias esperam?’ e ‘como nossos recursos estão sendo usados?’.”

---

## Slide 6 – Entradas ↔ Modelo

**Título:** Entradas ↔ Modelo de Eventos Discretos

Bullets:
- `taxa_chegada` → função `tempo_entre_chegadas()`
- `tempo_servico` médio + distribuição → `tempo_de_servico()`
- `num_atendentes` → tamanho do vetor de servidores
- `tempo_simulacao` → condição de parada do loop

Notas:
> “Quando você mexe no número de atendentes na interface, o que muda na prática é quantos servidores existem na simulação e quantos FIM_ATENDIMENTO podem estar ativos.”

---

## Slide 7 – Saídas ↔ Estatísticas

**Título:** Saídas ↔ Estatísticas do Modelo

Bullets:
- `tempo_medio_espera`:
  - calculado a partir dos tempos de chegada e saída
- `utilizacao`:
  - derivada de `area_ocupacao / tempo_total`
- `num_medio_familias`:
  - derivado de `area_num_familias / tempo_total`
- `atendimentos_dia`:
  - contador de eventos FIM_ATENDIMENTO

Notas:
> “Nada ‘mágico’: o simulador está só contabilizando, ao longo do tempo, as mesmas grandezas que você definiu no papel.”

---

## Slide 8 – Demo – Cenário Base

**Título:** Demonstração – Cenário Base

Bullets:
- Parâmetros exemplo:
  - `λ` = X famílias/hora
  - `1/μ` = Y minutos por atendimento
  - N atendentes (configuração atual)
  - 1 dia de simulação (ex.: 8 horas)
- Executar:
  - algumas replicações
- Observar:
  - tempo médio de espera
  - utilização dos atendentes

Notas:
> “Rodar na frente da turma: ‘com 3 atendentes e essas médias, qual o tempo de espera?’.”

---

## Slide 9 – Demo – Comparando Atendentes

**Título:** Demonstração – Comparando N.º de Atendentes

Bullets:
- Cenário A: 3 atendentes
- Cenário B: 4 atendentes
- Cenário C: 5 atendentes
- Para cada cenário:
  - rodar replicações
  - registrar tempo médio de espera e utilização

Notas:
> “Mostrar como o simulador permite comparar rapidamente diferentes configurações, sempre com foco em processos ligados ao CadÚnico.”

---

## Slide 10 – Experimentos Rápidos

**Título:** Experimentos Rápidos de Sensibilidade

Bullets:
- Dobrar a taxa de chegada (simular período de campanha ou prazo de atualização)
- Reduzir tempo de serviço (simular melhoria de processo)
- Perguntas:
  - o sistema aguenta?
  - a fila explode?
  - qual é o gargalo?

Notas:
> “Isso aproxima a disciplina de uma análise de capacidade: ‘até que nível de demanda o sistema se sustenta com a configuração atual?’.”

---

## Slide 11 – Limitações do Simulador

**Título:** Limitações e Cuidados

Bullets:
- Modelo simplificado:
  - pode não incluir prioridades, vários tipos de atendimento, abandono (no início)
- Dados:
  - parâmetros podem ser suposições, não dados observados
- Interpretação:
  - resultados são estimativas, não garantias

Boas práticas:
- documentar simplificações
- não usar o simulador como “bola de cristal”
- sempre contextualizar com a realidade dos serviços ligados ao CadÚnico

Notas:
> “Simulador é ferramenta de apoio à decisão, não oráculo.”

---

## Slide 12 – Exercícios – Simulador

**Título:** Exercícios – Uso do Simulador

Bullets:
- Escolher um cenário base (configuração de atendimento)
- Definir dois cenários alternativos (mais/menos atendentes, por exemplo)
- Para cada cenário:
  - rodar `n` replicações
  - registrar métricas principais (espera, utilização)
- Escrever uma breve interpretação:
  - qual cenário você recomendaria e por quê?

Notas:
> “Essa atividade é o ‘aquecimento’ para estudos mais completos de dimensionamento e análise de resultados.”
