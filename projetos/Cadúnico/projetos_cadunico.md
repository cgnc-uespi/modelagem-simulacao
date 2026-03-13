# Projetos de Simulação – Processos Ligados ao CadÚnico

_Disciplina: Modelagem e Simulação de Eventos Discretos_

Este arquivo reúne propostas de projetos de simulação aplicados a **processos de atendimento e uso do Cadastro Único para Programas Sociais (CadÚnico)**.

Base de dados oficial utilizada na disciplina:
- Microdados amostrais do CadÚnico – dados.gov.br
  <https://dados.gov.br/dados/conjuntos-dados/microdados-amostrais-do-cadastro-unico>
- Observatório do CadÚnico
  <https://paineis.mds.gov.br/public/extensions/observatorio-do-cadastro-unico/index.html>
- Data Explorer CadÚnico
  <https://aplicacoes.cidadania.gov.br/vis/data3/data-explorer.php>

Cada projeto pode ser adaptado em profundidade conforme a carga horária (trabalho de disciplina, IC, TCC).

---

## Projeto 1 – Dimensionamento de Guichês em Dia Típico

### Objetivo

Determinar o número de guichês de atendimento necessário para manter o **tempo médio de espera** das famílias abaixo de um alvo (por exemplo, 15 ou 20 minutos) em um dia típico de funcionamento do CadÚnico.

### Descrição

1. **Sistema:** CadÚnico em um dia sem campanhas especiais (dia útil comum).
2. **Modelagem:**
   - Chegadas de famílias ao longo do dia (por exemplo, taxa média por hora);
   - Tempos de atendimento (por tipo de serviço ou agregados: cadastramento inicial, atualização cadastral, consulta de benefícios);
   - Fila única ou filas por tipo de serviço (definir claramente);
   - Guichês idênticos (agentes sociais com desempenho semelhante).
3. **Cenários:**
   - Cenário A: configuração atual (número de guichês hoje);
   - Cenário B: +1 guichê;
   - Cenário C: +2 guichês (ou outras variações relevantes).
4. **Métricas:**
   - tempo médio de espera em fila;
   - tempo médio de permanência no CadÚnico;
   - utilização média de cada guichê.
5. **Entregáveis:**
   - modelo conceitual + modelo computacional;
   - comparação de cenários (médias, variabilidade);
   - recomendação de número de guichês.

---

## Projeto 2 – Reforço em Horários de Pico

### Objetivo

Avaliar o impacto de adicionar guichês **apenas em horários de pico** sobre o desempenho do CadÚnico.

### Descrição

1. **Sistema:** CadÚnico em um dia com picos claros (por exemplo, manhã e início de tarde).
2. **Modelagem:**
   - Taxa de chegada variável por hora (λ(t));
   - Tempos de atendimento (podem ou não depender do tipo de serviço: cadastramento, atualização ou consulta);
   - Escala de agentes sociais por horário (guichês ativos em cada período).
3. **Cenários:**
   - Cenário A: escala atual (guichês constantes ao longo do dia);
   - Cenário B: reforço de guichês apenas no pico da manhã;
   - Cenário C: reforço no pico da manhã e da tarde.
4. **Métricas:**
   - tempo médio de espera em cada período;
   - tempo máximo de espera observado (por período);
   - utilização média dos guichês em cada cenário.
5. **Entregáveis:**
   - gráficos de desempenho por hora/período;
   - análise de custo-benefício (tempo reduzido vs maior uso de pessoal).

---

## Projeto 3 – Fila Única vs Filas por Tipo de Serviço

### Objetivo

Comparar o desempenho do CadÚnico quando se adota **fila única** de famílias versus **filas específicas por tipo de serviço** (ex.: cadastramento inicial, atualização cadastral, consulta de benefícios).

### Descrição

1. **Sistema:** CadÚnico com pelo menos dois tipos de serviço bem definidos.
2. **Modelagem:**
   - Chegadas de famílias por tipo de serviço (taxas específicas para cada tipo);
   - Tempos de atendimento diferenciados por tipo;
   - Duas políticas de fila:
     - Política 1 (fila única): todas as famílias entram na mesma fila, atendidas na ordem de chegada; guichês atendem qualquer tipo de serviço;
     - Política 2 (filas por serviço): filas separadas por tipo; guichês podem ser dedicados ou compartilhados (definir configuração).
3. **Cenários:**
   - Cenário A: fila única;
   - Cenário B: filas por serviço (configuração 1);
   - (Opcional) Cenário C: filas por serviço com guichês parcialmente especializados.
4. **Métricas:**
   - tempo médio de espera por tipo de serviço;
   - equilíbrio de utilização entre guichês;
   - percepção de equidade entre diferentes perfis de demanda (gestantes, idosos, famílias com crianças pequenas).
5. **Entregáveis:**
   - análise comparativa de políticas de fila;
   - discussão sobre trade-offs entre simplicidade operacional e desempenho.

---

## Projeto 4 – Impacto de Campanhas de Cadastramento

### Objetivo

Estudar como campanhas de cadastramento ou recadastramento (que atraem muitas famílias) impactam o desempenho do CadÚnico, e como a simulação pode apoiar o planejamento dessas campanhas.

### Descrição

1. **Sistema:** CadÚnico durante uma campanha de cadastramento (aumento temporário de demanda).
2. **Modelagem:**
   - Aumento temporário na taxa de chegada de famílias (por exemplo, durante algumas semanas ou dias específicos);
   - Possível aumento na complexidade dos atendimentos (tempos de serviço maiores em cadastramentos iniciais completos);
   - Opções de reforço temporário de equipe.
3. **Cenários:**
   - Cenário A: campanha sem reforço (situação de referência);
   - Cenário B: campanha com reforço de guichês em determinados horários;
   - Cenário C: campanha com ampliação de horário de funcionamento (abrir mais cedo ou fechar mais tarde).
4. **Métricas:**
   - tempo médio e máximo de espera durante a campanha;
   - número de famílias atendidas por dia;
   - taxa estimada de abandono de fila.
5. **Entregáveis:**
   - recomendações para dimensionamento de pessoal e horário durante campanhas;
   - discussões sobre viabilidade operacional.

---

## Projeto 5 – Abandono de Fila (Desistência)

### Objetivo

Modelar e analisar o **abandono de fila** no CadÚnico (famílias que desistem de esperar) e avaliar estratégias para reduzi-lo.

### Descrição

1. **Sistema:** CadÚnico considerando que famílias podem desistir após esperar "demais".
2. **Modelagem:**
   - Tempos de espera individuais;
   - Regras de abandono (por exemplo, a família abandona se o tempo de espera exceder um limiar aleatório);
   - Geração de tempos até abandono (por exemplo, distribuição empírica ou assumida).
3. **Cenários:**
   - Cenário A: configuração atual de guichês e política de fila;
   - Cenário B: aumento de guichês em horários críticos;
   - Cenário C: estratégia alternativa (por exemplo, triagem rápida para informar tempo estimado de espera, priorização de gestantes e idosos).
4. **Métricas:**
   - taxa de abandono;
   - tempos médios de espera das famílias que ficam vs das que abandonam;
   - impacto do abandono na percepção de qualidade do serviço.
5. **Entregáveis:**
   - análise de como mudanças na capacidade e na política de fila afetam o abandono;
   - sugestões de medidas para reduzir o abandono.

---

## Projeto 6 – CadÚnico Multicanal (Presencial + Agendamento Online)

_(para disciplinas/projetos mais avançados)_

### Objetivo

Estender o modelo do CadÚnico para considerar múltiplos canais de atendimento (presencial sem agendamento, presencial com agendamento prévio, atendimento remoto) e avaliar o impacto de incentivar o agendamento digital na redução de filas presenciais.

### Descrição

1. **Sistema:** CadÚnico com atendimentos presenciais e com agendamento prévio.
2. **Modelagem:**
   - Diferentes fluxos de chegada para cada canal;
   - Tempos de atendimento diferentes por canal (famílias com agendamento chegam com documentação mais organizada);
   - Possível migração de parte da demanda espontânea para o canal com agendamento (cenários de adoção);
   - Capacidade distinta em cada canal (vagas agendadas vs atendimentos por ordem de chegada).
3. **Cenários:**
   - Cenário A: situação atual (pouco uso de agendamento);
   - Cenário B: incentivo moderado ao agendamento (x% das famílias agendam);
   - Cenário C: incentivo forte ao agendamento (y% das famílias agendam).
4. **Métricas:**
   - tempo médio de espera presencial;
   - tempo médio de resposta para famílias com agendamento;
   - distribuição de carga entre canais.
5. **Entregáveis:**
   - análise de como o agendamento pode aliviar filas presenciais;
   - recomendações de metas de adoção do agendamento digital.

---

## Observações Gerais

- Cada projeto deve seguir a estrutura de:
  1. Definição do problema e objetivos;
  2. Coleta/estimativa de dados;
  3. Modelo conceitual;
  4. Modelo computacional;
  5. Verificação e validação;
  6. Projeto de experimentos;
  7. Análise de resultados e recomendações.
- Dependendo do escopo (disciplina vs TCC), o nível de detalhamento e a quantidade de cenários/replicações podem ser ajustados.
