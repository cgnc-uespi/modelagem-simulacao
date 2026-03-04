# Listas de Exercícios – Modelagem e Simulação de Eventos Discretos

_Foco: Cadastro Único para Programas Sociais (CadÚnico) – atendimento nos CRAS_

Cada seção abaixo corresponde a uma **lista de exercícios para casa** vinculada a uma aula.

---

## Lista de Exercícios – Aula 1 (Introdução)

### Exercício 1 – Fronteiras do CadÚnico
Descreva, em um texto de 1–2 parágrafos:
- quais elementos você considera **dentro** do sistema CadÚnico (recursos, processos, regras);
- quais elementos estão **fora** (ambiente);
- qual é, na sua visão, o principal **objetivo de desempenho** que deveria ser monitorado (ex.: tempo médio de espera, número de atendimentos por dia, taxa de abandono).

### Exercício 2 – Sistema, modelo e simulação
Explique, com suas palavras, usando o CadÚnico como exemplo:
- o que é o **sistema**;
- o que é o **modelo**;
- o que significa **simular** esse modelo;
- dê um exemplo de pergunta que poderia ser respondida com simulação e que seria difícil responder apenas com "opinião".

### Exercício 3 – Tipos de modelos
Dê **um exemplo de modelo determinístico** e **um de modelo estocástico** para o CadÚnico, deixando claro:
- que variáveis seriam determinísticas ou aleatórias;
- quais simplificações você estaria fazendo em cada caso.

---

## Lista de Exercícios – Aula 2 (Conceitos de eventos discretos)

### Exercício 1 – Variáveis de estado
Liste, pelo menos, 5 variáveis de estado que seriam importantes para descrever o CadÚnico em um dado instante de tempo. Justifique brevemente por que cada uma é relevante.

### Exercício 2 – Tipos de eventos
Defina, para o CadÚnico, pelo menos 4 tipos de eventos. Para cada um:
- dê um **nome** (por exemplo, `CHEGADA_FAMILIA`);
- descreva **quando** ele ocorre;
- explique **como altera** o estado do sistema CadÚnico.

### Exercício 3 – Esqueleto de simulador (texto)
Em texto (pode ser pseudocódigo informal), descreva o ciclo principal de um simulador de eventos discretos para o CadÚnico, mencionando explicitamente:
- inicialização;
- como o **próximo evento** é escolhido;
- como o relógio de simulação avança;
- quando a simulação é encerrada.

---

## Lista de Exercícios – Aula 3 (Chegadas e atendimentos)

### Exercício 1 – Padrão de chegadas
Considere um dia típico de atendimento no CRAS:
- descreva qualitativamente como você acha que é o padrão de **chegadas de famílias** ao longo do dia (por exemplo: pico de manhã, queda à tarde, outro pico antes de fechar);
- esboce um gráfico (tempo x taxa de chegadas) mostrando sua hipótese.

### Exercício 2 – Tempos de atendimento por tipo de serviço
Escolha pelo menos **dois tipos de serviço** no CadÚnico (ex.: cadastramento inicial e atualização cadastral). Para cada um:
- descreva se o tempo de atendimento típico é "curto", "médio" ou "longo";
- proponha uma distribuição plausível para esse tempo (por exemplo, exponencial, lognormal ou empírica) e justifique.

### Exercício 3 – Disciplina de fila
Descreva a disciplina de fila que você acredita existir no CadÚnico hoje (ou que faria sentido existir):
- fila única vs filas por tipo de serviço;
- regras de prioridade (gestantes, idosos, famílias com crianças pequenas, etc.);
- comente como uma mudança de disciplina poderia afetar o tempo de espera.

---

## Lista de Exercícios – Aula 4 (Números pseudoaleatórios)

### Exercício 1 – Uniforme(0,1) na prática
Usando qualquer linguagem/planilha:
- gere 100 ou mais valores Uniforme(0,1);
- calcule a **média** aproximada e verifique se está próxima de 0,5;
- comente se os valores "parecem" bem espalhados no intervalo.

### Exercício 2 – Função `tempo_entre_chegadas_cadunico`
Escreva (em pseudocódigo) uma função `tempo_entre_chegadas_cadunico(lambda)` que:
- use um gerador Uniforme(0,1);
- retorne um tempo entre chegadas exponencial com taxa `lambda`;
- explique como essa função seria usada para agendar o próximo evento `CHEGADA_FAMILIA`.

### Exercício 3 – Reprodutibilidade
Explique, em 1 parágrafo:
- o que é uma **seed** (semente) para o gerador de números aleatórios;
- por que é importante controlar a seed em experimentos de simulação (especialmente ao comparar cenários no CadÚnico).

---

## Lista de Exercícios – Aula 5 (Modelo de fila simples do CadÚnico)

### Exercício 1 – Modelo de 1 guichê
Reescreva, com suas palavras, o modelo de CadÚnico com **um único guichê** e fila única. Inclua:
- variáveis de estado;
- eventos;
- parâmetros (taxas de chegada e serviço);
- métricas de interesse.

### Exercício 2 – Fluxograma
Desenhe um **fluxograma** (à mão, se preferir) para o ciclo de simulação do CadÚnico com um guichê, mostrando:
- início;
- escolha do próximo evento;
- tratamento de `CHEGADA_FAMILIA` e `FIM_ATENDIMENTO`;
- atualização de estatísticas;
- condição de parada;
- fim.

### Exercício 3 – Limitações do modelo simples
Liste pelo menos **três limitações** do modelo de CadÚnico com um único guichê em relação ao sistema real. Para cada limitação, explique brevemente como um modelo mais avançado poderia corrigi-la.

---

## Lista de Exercícios – Aula 6 (Verificação e validação)

### Exercício 1 – Testes de verificação
Para o modelo do CadÚnico (mesmo o simplificado), proponha pelo menos **3 testes de verificação** específicos, como:
- verificar se o número de famílias no sistema nunca fica negativo;
- testar um cenário manual (poucas chegadas) e verificar o comportamento passo a passo;
- verificar se o somatório de atendimentos confere com o esperado.

### Exercício 2 – Dados para validação
Liste os tipos de **dados reais do CadÚnico** que seriam mais importantes para validar seu modelo (por exemplo: tempo médio de espera medido, distribuição de chegadas por hora, tempos médios de atendimento por serviço). Explique por que cada um é importante.

### Exercício 3 – Plausibilidade
Descreva um experimento de plausibilidade: 
- escolha um parâmetro do modelo (por exemplo, taxa de chegada ou número de guichês);
- explique como você esperaria que o tempo médio de espera **mudasse** ao aumentar/diminuir esse parâmetro;
- comente como isso te ajudaria a confiar (ou não) no modelo.

---

## Lista de Exercícios – Aula 7 (Projeto de experimentos)

### Exercício 1 – Definição de cenários
Defina pelo menos **dois cenários** para o CadÚnico:
- descreva os valores dos fatores (por exemplo, número de guichês, política de fila);
- indique claramente o que difere entre um cenário e outro.

### Exercício 2 – Plano de replicações
Para os cenários definidos no Exercício 1:
- escolha um número de replicações `n` por cenário (justifique se é pequeno, médio ou grande para sua realidade);
- descreva quais métricas serão coletadas em cada replicação;
- explique como você calcularia média e alguma noção de variabilidade.

### Exercício 3 – Warm-up
Explique como você trataria o **período de aquecimento** na simulação do CadÚnico:
- você descartaria um tempo inicial? Quantos minutos/hora aproximadamente?;
- ou descartaria os primeiros N atendimentos?;
- justifique com base em como o CRAS funciona logo após abrir.

---

## Lista de Exercícios – Aula 8 (Projetos)

### Exercício 1 – Mini-proposta de projeto
Escreva uma mini-proposta (1–2 páginas) de projeto de simulação para o CadÚnico contendo:
- descrição do sistema (parte do atendimento que será estudada);
- objetivos do estudo (o que você quer descobrir/otimizar);
- visão inicial do modelo conceitual (entidades, filas, eventos, guichês);
- dados necessários (e se você imagina obtê-los reais ou por suposição);
- cenários que pretende comparar.

### Exercício 2 – Critérios de sucesso
Defina, para o seu projeto do CadÚnico:
- pelo menos **dois critérios de sucesso** (por exemplo, reduzir tempo médio de espera para menos de X minutos, manter utilização de guichês abaixo de Y%);
- explique como a simulação pode te ajudar a verificar se esses critérios foram atingidos.

### Exercício 3 – Limitações e extensões
Discuta, em 1–2 parágrafos:
- quais limitações você espera que seu modelo do CadÚnico tenha (falta de dados, simplificações);
- que extensões futuras poderiam torná-lo mais realista (por exemplo, incluir abandono de fila, agendamento prévio, diferentes perfis de famílias como gestantes e idosos).
