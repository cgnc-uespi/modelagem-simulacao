# Slides – Abstração e Diagrama de Ciclos (CadÚnico)

## Slide 1 – Título

**Título:** Abstração e Diagrama de Ciclos  
**Subtítulo:** Fluxos de Atendimento e Processos Ligados ao CadÚnico

Notas:
> “Vamos representar graficamente o ciclo de vida de famílias e atendentes em processos ligados ao CadÚnico (por exemplo, atendimento em um CRAS).”

---

## Slide 2 – Objetivos

**Título:** Objetivos da Aula

Bullets:
- Praticar a abstração de sistemas com ciclos de vida
- Construir diagramas de ciclo para famílias e atendentes
- Conectar esses diagramas com o modelo de simulação de eventos discretos

Notas:
> “É uma forma visual de garantir que não esquecemos estados e transições importantes nos processos de atendimento e atualização cadastral.”

---

## Slide 3 – Família como Entidade

**Título:** Família como Entidade

Bullets:
- Estados possíveis (exemplo):
  - fora do posto de atendimento
  - aguardando atendimento / senha
  - em fila
  - em atendimento
  - atendida (cadastro/atualização concluída)
  - (opcional) desistiu / não compareceu

Notas:
> “Seguimos a família ao longo do seu ‘ciclo de vida’ dentro do processo escolhido (ex.: atualização cadastral).”

---

## Slide 4 – Ciclo Básico da Família

**Título:** Ciclo de Vida – Família no Processo de Atendimento

Bullets (para diagrama):
- Fora do posto → Chega → Retira senha / registra chegada → Entra na fila
- Fila → É chamada → Atendimento → Sai do posto (cadastro/atualização feita)
- (Opcional) Fila → Desiste → Sai sem atendimento

Notas:
> “Isso vira um grafo com estados como nós e eventos como setas entre eles, servindo de base para o modelo de eventos discretos.”

---

## Slide 5 – Tipos de Atendimento

**Título:** Tipos de Atendimento

Bullets:
- Após a chegada, a família pode seguir para diferentes fluxos, por exemplo:
  - novo cadastro
  - atualização cadastral
  - orientação/documentação complementar
- Cada tipo de atendimento pode ter:
  - ciclo semelhante, com tempos diferentes
  - regras específicas (prioridades, exigências)

Notas:
> “Mostra como o diagrama escala para múltiplos tipos de atendimento sem perder a lógica básica de estados e eventos.”

---

## Slide 6 – Ciclo do Atendente

**Título:** Ciclo de Vida – Atendente/Posto

Bullets:
- Estados do atendente/posto:
  - livre
  - atendendo
  - (opcional) indisponível/pausa
- Ciclo:
  - livre → recebe família → atendendo → termina atendimento → volta a livre

Notas:
> “Esse diagrama é complementar ao da família e ajuda a pensar na utilização dos recursos de atendimento.”

---

## Slide 7 – Conexão com Eventos

**Título:** Diagramas ↔ Eventos de Simulação

Bullets:
- Cada transição de ciclo ↔ um evento na simulação:
  - ‘chegada de família’ ↔ CHEGADA_FAMILIA
  - ‘entra em atendimento’ ↔ INICIO_ATENDIMENTO
  - ‘sai do sistema’ ↔ FIM_ATENDIMENTO
  - ‘desiste’ ↔ DESISTENCIA
- Diagramas ajudam a:
  - listar todos os eventos necessários
  - evitar esquecer estados ou transições importantes

Notas:
> “É um checklist visual para comparar com a especificação de eventos do modelo implementado.”

---

## Slide 8 – Exercícios – Diagramas

**Título:** Exercícios – Abstração e Diagramas

Bullets:
- Desenhar o diagrama de ciclo para:
  - família com 2 tipos de atendimento distintos (ex.: novo cadastro e atualização)
  - atendente que pode ficar indisponível (pausa, reunião)
- Marcar em cada seta qual evento da simulação corresponde
- Identificar:
  - estados que podem ter loops (por exemplo, fila)
  - caminhos que representam abandono do processo

Notas:
> “Ao forçar o mapeamento entre diagrama e eventos, o aluno reforça a ligação entre representação visual e implementação do simulador.”
