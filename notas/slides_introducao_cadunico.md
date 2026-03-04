# Slides – Introdução à Modelagem e Simulação (CadÚnico)

## Slide 1 – Título

**Título:** Introdução à Modelagem e Simulação de Eventos Discretos  
**Subtítulo:** Estudo de Caso: Cadastro Único para Programas Sociais (CadÚnico)

Notas:
> “Hoje começamos a disciplina vendo o que é modelagem, o que é simulação e por que isso importa.  
> Nosso estudo de caso principal será o CadÚnico, usando a base oficial de microdados amostrais como fonte para entender famílias, demanda e processos de atendimento.”

---

## Slide 2 – Objetivos da Disciplina

**Título:** Objetivos da Disciplina

Bullets:
- Entender o que são:
  - sistemas, modelos, simulação
- Aprender os fundamentos de:
  - simulação de eventos discretos
  - sistemas de filas
- Desenvolver modelos de simulação aplicados a:
  - processos ligados ao CadÚnico (atendimento, cadastro, atualização)
- Apoiar decisões em políticas públicas e serviços sociais:
  - dimensionamento de equipes e recursos
  - análise de cenários de demanda e elegibilidade

Notas:
> “A ideia não é só aprender a teoria abstrata, mas conseguir construir modelos que ajudem a responder perguntas reais, como quantos atendentes são necessários num CRAS ou quanto tempo as famílias esperam para atualizar o cadastro.”

---

## Slide 3 – Motivação

**Título:** Por que Modelagem e Simulação?

Bullets:
- Muitos sistemas são complexos:
  - filas em bancos, hospitais, repartições públicas
  - redes de computadores
  - linhas de produção, logística
- Perguntas típicas:
  - Quantos servidores/atendentes são suficientes?
  - O que acontece se a demanda dobrar?
  - Como comparar políticas diferentes?

**CadÚnico (exemplo):**
- Filas e espera para cadastro/atualização em CRAS  
- Equipes limitadas, orçamento limitado  
- Decisões de priorização e dimensionamento com impacto direto nas famílias

Notas:
> “No contexto do CadÚnico, por exemplo, muitas famílias precisam ser atendidas com recursos limitados. A simulação entra como ferramenta para explorar cenários antes de mudar a forma como o atendimento funciona na prática.”

---

## Slide 4 – Estudo de Caso: CadÚnico

**Título:** Estudo de Caso: CadÚnico

Bullets:
- Sistema de informação social que registra famílias de baixa renda:
  - base para vários programas (ex.: benefícios de transferência de renda)
- Processos associados:
  - cadastro inicial
  - atualização periódica
  - verificação de elegibilidade
- Do ponto de vista de simulação:
  - chegadas de famílias aos postos de atendimento (CRAS, unidades cadastradoras)
  - tempos de atendimento
  - regras de priorização (grupos específicos, prazos de atualização)

Notas:
> “Tudo que vamos ver na disciplina pode ser enxergado dentro dos processos ligados ao CadÚnico: chegadas, filas, servidores, políticas de atendimento. Ele é o nosso laboratório conceitual, apoiado por dados reais.”

---

## Slide 5 – Conceito de Sistema

**Título:** O que é um Sistema?

Bullets:
- Conjunto de elementos que interagem para um propósito
- Exemplos:
  - pronto-socorro, rede de computadores, linha de produção
- No nosso estudo de caso:
  - Sistema = processo de atendimento e manutenção cadastral ligado ao CadÚnico

**CadÚnico – componentes (exemplos):**
- Famílias, indivíduos, atendentes, postos/CRAS  
- Sistemas de informação, formulários, regras de elegibilidade  
- Ambiente: legislação, calendário de prazos, campanhas de atualização

Notas:
> “O primeiro passo é enxergar o CadÚnico não só como um banco de dados, mas como um sistema de processos: quem são as famílias, quem atende, quais são as regras e restrições.”

---

## Slide 6 – Fronteiras do Sistema (CadÚnico)

**Título:** Fronteiras do Sistema

Bullets:
- Dentro do sistema (no nosso modelo):
  - filas internas de atendimento
  - atendentes e postos de cadastro
  - lógica de priorização e regras de atendimento
- Fora do sistema (tratado como entrada/ambiente):
  - contexto socioeconômico das famílias
  - decisões de alto nível de política pública
  - outros sistemas/órgãos que usam o CadÚnico

Perguntas:
- O que eu vou **modelar explicitamente** (eventos, filas, recursos)?
- O que vou tratar como **entrada** (dados dos microdados, parâmetros de demanda)?

Notas:
> “Não dá para modelar o universo inteiro. Escolhemos um recorte: por exemplo, o fluxo de atendimento em um CRAS. Os perfis das famílias vêm dos microdados; as regras de política mais amplas entram como parâmetros.”

---

## Slide 7 – Sistema, Modelo e Simulação

**Título:** Sistema, Modelo e Simulação

Bullets:
- Sistema real:
  - processos reais de atendimento e uso do CadÚnico
- Modelo:
  - representação simplificada desses processos
  - foca em aspectos relevantes (fila, tempo, capacidade, regras)
- Simulação:
  - execução do modelo ao longo do tempo
  - observação de resultados (métricas)

Fluxo:
> Processos reais ligados ao CadÚnico → Modelo de atendimento/uso → Simulação → Decisões

Notas:
> “O modelo não é o CadÚnico inteiro. É uma versão simplificada focada em responder perguntas específicas, como: ‘quantos atendentes preciso para manter o tempo médio de atendimento abaixo de X minutos?’.”

---

## Slide 8 – Determinístico vs Estocástico

**Título:** Determinístico vs Estocástico

Bullets:
- Determinístico:
  - mesmas entradas → mesmos resultados
  - sem ‘sorte’ ou ‘azar’
- Estocástico:
  - inclui variáveis aleatórias
  - resultados mudam a cada execução

**No contexto CadÚnico:**
- Determinístico (simplificado):
  - todo atendimento dura exatamente 10 minutos, chegadas perfeitamente regulares
- Estocástico (mais realista):
  - tempos de atendimento variam entre famílias
  - chegadas variam ao longo do dia e por época (campanhas, prazos)

Notas:
> “Na prática, processos ligados ao CadÚnico são estocásticos: nem toda família leva o mesmo tempo para ser atendida, nem chegam de forma perfeitamente regular. A disciplina foca principalmente nesse tipo de modelo.”

---

## Slide 9 – Tempo Contínuo vs Eventos Discretos

**Título:** Modelos Contínuos vs Eventos Discretos

Bullets:
- Contínuos:
  - estado pode mudar a qualquer instante
  - típicos em sistemas físicos (equações diferenciais)
- Eventos discretos:
  - estado muda em pontos específicos no tempo
  - entre eventos, o estado é constante

**Eventos em processos ligados ao CadÚnico:**
- chegada de família ao posto de atendimento  
- início de atendimento  
- término de atendimento  
- agendamento de retorno/atualização  
- abandono da fila

Notas:
> “Aqui faz muito sentido pensar em eventos discretos: o que nos importa são as chegadas, inícios e finais de atendimento e outras mudanças pontuais de estado, não o que acontece ‘no meio’ do atendimento.”

---

## Slide 10 – Analítico vs Simulação

**Título:** Analítico vs Simulação

Bullets:
- Modelos analíticos:
  - equações e fórmulas fechadas (quando existem)
  - úteis para casos simples (filas clássicas)
- Simulação:
  - executa o modelo computacional
  - lida melhor com regras e estruturas complexas

**No contexto CadÚnico:**
- Analítico:
  - fila simples com chegadas e serviços exponenciais
- Simulado:
  - diferentes tipos de atendimento
  - múltiplos atendentes/postos
  - prioridades para certos grupos
  - padrões de chegada que variam com o tempo

Notas:
> “Quando o processo encaixa num modelo clássico de teoria de filas, ótimo. Mas o uso real do CadÚnico envolve múltiplos serviços, regras e prioridades – aí a simulação se torna a ferramenta principal.”

---

## Slide 11 – O que Vamos Fazer com o CadÚnico

**Título:** O que Vamos Fazer com o CadÚnico

Bullets:
- Identificar e modelar:
  - chegadas de famílias, filas, recursos de atendimento, regras de prioridade
- Construir modelos de eventos discretos:
  - de versões simples até versões mais ricas, usando microdados como inspiração/parametrização
- Simular cenários:
  - variação do número de atendentes
  - mudanças em regras de atendimento/priorização
  - impactos de mudanças de demanda
- Gerar recomendações:
  - metas de tempo de espera
  - dimensionamento de equipes
  - avaliação de efeitos de políticas

Notas:
> “O CadÚnico e seus processos vão aparecer em várias aulas. A ideia é que, no final do semestre, vocês consigam propor alterações concretas em processos de atendimento ou uso da base, baseadas em simulação.”

---

## Slide 12 – Exercícios – Aula 1 (CadÚnico)

**Título:** Exercícios – Aula 1 (CadÚnico)

Bullets:
- Definir fronteiras do sistema a ser modelado:
  - exemplo: atendimento de famílias em um CRAS
- Descrever objetivos de desempenho:
  - tempo de espera, atendimentos/dia, backlog de atualizações
- Explicar sistema, modelo e simulação usando o CadÚnico como contexto

Notas:
> “Esses exercícios vão forçar vocês a tirar o sistema da cabeça e colocar no papel. Não é para programar ainda, é para enxergar processos ligados ao CadÚnico como sistemas a serem modelados.”
