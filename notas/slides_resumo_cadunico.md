# Slides – Resumo da Disciplina (CadÚnico como Estudo de Caso)

_Esqueleto de slides em formato de tópicos para uso em aula._

---

## Slide 1 – Título da Disciplina

- **Disciplina:** Modelagem e Simulação de Eventos Discretos
- **Estudo de Caso Central:** Processos Ligados ao CadÚnico (Cadastro Único para Programas Sociais)
- Foco: aplicar conceitos de modelagem/simulação para entender e melhorar processos de atendimento e uso do CadÚnico.

---

## Slide 2 – Panorama do Módulo

- Introdução a sistemas, modelos e simulação
- Simulação de eventos discretos
- Filas e processos de chegada/atendimento
- Números aleatórios e variáveis aleatórias
- Construção de modelos de filas (atendimento simplificado)
- Verificação e validação
- Projeto de experimentos e análise de resultados
- Projetos aplicados a processos ligados ao CadÚnico

---

## Slide 3 – Aula 1 (Introdução)

**Tópicos-chave:**
- Sistema, modelo, simulação
- Modelos determinísticos vs estocásticos
- Tempo contínuo vs eventos discretos

**CadÚnico:**
- Processos de atendimento/cadastro como sistema
- Objetivos: tempo de espera, número de atendimentos, backlog de atualizações

**Exercício principal:**
- Definir fronteiras do sistema e objetivos de desempenho.

---

## Slide 4 – Aula 2 (Eventos Discretos)

**Tópicos-chave:**
- Estado do sistema
- Relógio de simulação
- Eventos
- Lista de eventos futuros (FEL)

**CadÚnico:**
- Estado: famílias em fila, atendentes ocupados/livres
- Eventos: chegada, início de atendimento, fim de atendimento, desistência

**Exercício principal:**
- Listar variáveis de estado e eventos e descrever o efeito de cada evento.

---

## Slide 5 – Aula 3 (Chegadas e Atendimentos)

**Tópicos-chave:**
- Processos de chegada (determinístico vs aleatório)
- Intuição de processo de Poisson
- Tempos de serviço
- Elementos de um sistema de filas

**CadÚnico:**
- Padrões de chegada por horário/período
- Tempos de atendimento por tipo de atendimento
- Disciplina de fila (senhas, prioridades)

**Exercício principal:**
- Descrever padrão de chegadas e propor distribuições para tempos entre chegadas e tempos de atendimento.

---

## Slide 6 – Aula 4 (Números Pseudoaleatórios)

**Tópicos-chave:**
- Geradores pseudoaleatórios e seed
- Uniforme(0,1)
- Transformação para outras distribuições (ex.: exponencial)

**Aplicação:**
- Uso de `tempo_entre_chegadas()` e `tempo_de_servico()`
- Reprodutibilidade para comparar cenários de configuração de atendentes

**Exercício principal:**
- Escrever função `tempo_entre_chegadas(lambda)` em pseudocódigo e explicar o uso.

---

## Slide 7 – Aula 5 (Modelo de Fila Simples)

**Tópicos-chave:**
- Modelo M/M/1 conceitual
- Variáveis de estado e eventos
- Coleta de estatísticas (tempo de permanência, utilização, número médio no sistema)

**Aplicação:**
- Versão simplificada com 1 atendente
- Fluxograma do simulador

**Exercício principal:**
- Construir fluxograma/pseudocódigo e discutir limitações.

---

## Slide 8 – Aula 6 (Verificação e Validação)

**Tópicos-chave:**
- Verificação ("o programa está certo?")
- Validação ("estamos modelando a coisa certa?")
- Técnicas: revisão, testes, comparação com dados, plausibilidade

**Aplicação:**
- Testes de invariantes (nunca ter entidades negativas)
- Comparação de tempos médios de espera com dados observados (quando houver)

**Exercício principal:**
- Propor testes de verificação e dados necessários para validar o modelo.

---

## Slide 9 – Aula 7 (Projeto de Experimentos)

**Tópicos-chave:**
- Cenários, fatores e níveis
- Replicações e variabilidade
- Período de aquecimento (warm-up)
- Comparação de cenários

**Aplicação:**
- Cenários: diferentes números de atendentes, escalas de horário, políticas de fila
- Métricas: tempo médio de espera, utilização, taxa de abandono

**Exercício principal:**
- Definir cenários e plano de replicações.

---

## Slide 10 – Aula 8 (Projetos e Aplicações)

**Tópicos-chave:**
- Estrutura de um projeto de simulação
- Aplicações em políticas sociais e serviços públicos

**CadÚnico:**
- Projetos sugeridos: dimensionamento de equipe de atendimento, impacto de campanhas de atualização, análise de backlog, priorização de perfis de famílias

**Exercício principal:**
- Escrever mini-proposta de projeto de simulação aplicada a um processo ligado ao CadÚnico.

---

## Slide 11 – Encerramento

- Revisão dos conceitos principais
- Importância de simulação para gestão de políticas sociais
- Próximos passos:
  - aprofundar implementação (ferramentas);
  - desenvolver projetos com dados reais;
  - explorar outros sistemas (saúde, educação, etc.).
