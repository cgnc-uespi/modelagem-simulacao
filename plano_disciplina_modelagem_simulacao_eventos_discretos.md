# Disciplina: Modelagem e Simulação de Eventos Discretos

_Esboço de plano em nível de graduação – foco em fundamentos teóricos + prática aplicada._

---

## Módulo 1 – Introdução: sistemas, modelos e simulação

**Objetivo:** construir o vocabulário e o contexto da disciplina.

### Tópicos

- Conceitos básicos:
  - sistema, modelo, simulação
  - modelo determinístico vs estocástico
  - modelo contínuo vs discreto
- Modelos analíticos vs simulação:
  - quando a solução analítica é possível
  - quando a simulação é mais adequada
- Exemplos de sistemas reais que podem ser modelados:
  - filas (bancos, hospitais, call centers)
  - manufatura (linhas de produção)
  - redes de computadores e sistemas distribuídos

### Atividade sugerida

- Pedir a cada aluno/grupo que descreva (em texto ou diagrama) um sistema real e identifique:
  - fronteiras do sistema
  - entradas, saídas
  - variáveis de estado
  - objetivos de desempenho que poderiam ser avaliados por simulação.

---

## Módulo 2 – Conceitos de simulação de eventos discretos

**Objetivo:** entender o que caracteriza um modelo de eventos discretos.

### Tópicos

- O que é um **evento discreto**:
  - mudanças de estado em instantes específicos (chegadas, partidas, falhas, reparos etc.)
- Tempo em simulação de eventos discretos:
  - tempo avançando por eventos (next-event time advance)
  - comparação com simulação em passo fixo
- Componentes de um modelo de eventos discretos:
  - estado do sistema
  - eventos e relógio de simulação
  - lista de eventos futuros (future event list)

### Atividade sugerida

- Construir, em pseudocódigo ou diagrama, o esqueleto de um simulador de eventos discretos usando avanço por próximo evento.

---

## Módulo 3 – Processos de chegada e atendimento (fundamentos de filas)

**Objetivo:** introduzir os blocos de chegada/atendimento que aparecem em muitos modelos.

### Tópicos

- Processos de chegada:
  - chegadas determinísticas vs aleatórias
  - ideia de processos de Poisson (sem formalismo pesado)
- Tempos de serviço/atendimento:
  - determinísticos vs aleatórios
  - noções básicas de distribuições (exponencial, normal, uniforme etc.)
- Noções iniciais de filas:
  - famílias/usuários, servidores, disciplina de atendimento (FIFO, prioridade etc.)

### Atividade sugerida

- Definir um sistema simples de fila (por exemplo, um guichê de atendimento) e descrever:
  - como são as chegadas
  - como é o serviço
  - quais variáveis de interesse (tempo médio em fila, utilização, etc.).

---

## Módulo 4 – Geração de números aleatórios e variáveis aleatórias

**Objetivo:** preparar o terreno para implementar simulações estocásticas.

### Tópicos

- Números pseudoaleatórios:
  - ideia geral de geradores
  - propriedades desejáveis (período, uniformidade, independência)
- Transformação de números uniformes em outras distribuições:
  - inversa da função de distribuição (conceito)
  - mapeamento para distribuições comuns usadas em simulação
- Cuidados práticos:
  - seeds, reprodutibilidade
  - bibliotecas vs implementação manual

### Atividade sugerida

- Usar alguma linguagem (ou mesmo planilha) para gerar sequências pseudoaleatórias e verificar empiricamente médias/variâncias aproximadas.

---

## Módulo 5 – Construção de modelos de filas em simulação de eventos discretos

**Objetivo:** aplicar os conceitos para modelar sistemas de filas completos.

### Tópicos

- Estrutura de um modelo de fila simples (por exemplo, M/M/1 ou equivalente conceitual):
  - estado (número de famílias no sistema)
  - eventos (chegada, início de serviço, término de serviço)
- Implementação conceitual:
  - como agendar eventos
  - como atualizar o estado
  - coleta de estatísticas (tempo em fila, tempo de resposta, utilização)

### Atividade sugerida

- Desenhar o fluxograma de uma simulação de fila simples e/ou escrever pseudocódigo comentado.

---

## Módulo 6 – Verificação e validação de modelos

**Objetivo:** distinguir entre "o programa está certo" e "o modelo representa bem o sistema real".

### Tópicos

- Verificação (verification):
  - conferir se o modelo foi implementado corretamente
- Validação (validation):
  - conferir se o modelo é adequado para representar o sistema real
- Técnicas comuns:
  - comparação com dados históricos
  - revisão de modelo com especialistas
  - análise de sensibilidade

### Atividade sugerida

- Propor um cenário de simulação e perguntar:
  - como você verificaria o modelo?
  - como você o validaria com o gestor/usuário do CadÚnico?

---

## Módulo 7 – Projeto de experimentos e análise de resultados

**Objetivo:** ensinar a planejar estudos de simulação e interpretar saídas.

### Tópicos

- Projeto de experimentos em simulação:
  - definição de cenários e fatores
  - número de replicações
  - período de aquecimento (warm-up)
- Coleta e análise de resultados:
  - médias, variâncias, intervalos de confiança (noções)
  - comparação de cenários
- Apresentação de resultados:
  - tabelas, gráficos, interpretação textual

### Atividade sugerida

- Dar um pequeno conjunto de resultados simulados e pedir aos alunos que escrevam um mini-relatório explicando qual cenário é melhor e por quê.

---

## Módulo 8 – Aplicações e projetos

**Objetivo:** conectar a disciplina com áreas de interesse dos alunos.

### Tópicos

- Exemplos de aplicação:
  - manufatura e logística
  - saúde (pronto-socorro, leitos)
  - redes de computadores e sistemas distribuídos
  - sistemas financeiros (filas de ordens, atendimentos, etc.)
- Orientação de projeto final:
  - definição de um sistema real
  - construção de modelo conceitual
  - implementação (com ferramenta escolhida)
  - análise de cenários

### Atividade sugerida

- Definir temas/projetos possíveis e pedir que cada grupo escolha um, descrevendo em 1–2 páginas o sistema, os objetivos da simulação e as métricas de interesse.

---

## Observações

- Este plano é intencionalmente **agnóstico de ferramenta** (pode ser adaptado para Arena, SimPy, AnyLogic, etc.).
- Nos próximos passos, podemos criar:
  - `notas/` detalhadas por módulo (uma "aula" por arquivo). 
  - listas de exercícios em `exercicios/modelagem-simulacao/`.
  - orientações de projeto em `projetos/modelagem-simulacao/`.
