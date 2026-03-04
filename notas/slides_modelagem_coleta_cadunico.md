# Slides – Modelagem e Coleta de Dados (CadÚnico)

## Slide 1 – Título

**Título:** Modelagem e Coleta de Dados  
**Subtítulo:** Processos Ligados ao CadÚnico

Notas:
> “Nesta aula vamos detalhar o modelo conceitual de um processo ligado ao CadÚnico (por exemplo, atendimento em um CRAS) e pensar em quais dados precisamos coletar para alimentar a simulação.”

---

## Slide 2 – Objetivos

**Título:** Objetivos da Aula

Bullets:
- Detalhar o modelo conceitual do processo de atendimento/cadastro
- Identificar variáveis que precisam ser medidas
- Discutir fontes e estratégias de coleta de dados (incluindo microdados do CadÚnico)

Notas:
> “A ligação entre ‘quero simular’ e ‘preciso de dados’ fica explícita aqui.”

---

## Slide 3 – Modelo Conceitual (Visão Geral)

**Título:** Modelo Conceitual – Visão Geral

Bullets:
- Entidades:
  - famílias, indivíduos, atendentes
- Recursos:
  - postos/CRAS, sistemas de informação
- Processos:
  - chegada, registro/retirada de senha, fila, atendimento, saída
- Regras:
  - disciplina de fila, prioridades, horários de funcionamento, prazos de atualização

Notas:
> “Um diagrama de blocos ajuda a visualizar esse fluxo de atendimento/atualização cadastral.”

---

## Slide 4 – Variáveis de Interesse

**Título:** Variáveis a Medir

Bullets:
- Tempos:
  - chegada da família
  - início de atendimento
  - fim de atendimento
- Contagens:
  - nº de famílias por hora/dia
  - nº de atendimentos por dia/tipo de atendimento
- Estados:
  - nº de famílias na fila ao longo do tempo
  - atendentes livres/ocupados

Notas:
> “Tudo que a simulação quer reproduzir vem dessas medidas.”

---

## Slide 5 – Dados de Chegadas

**Título:** Dados de Chegadas

Bullets:
- Registros desejados:
  - horário de chegada ou retirada de senha
  - tipo de atendimento (novo cadastro, atualização, orientação, etc.)
- Derivar:
  - tempos entre chegadas
  - taxa de chegada por hora/dia

Notas:
> “Idealmente esses dados vêm de sistemas eletrônicos; se não houver, trabalhar com amostragens ou aproximações.”

---

## Slide 6 – Dados de Atendimentos

**Título:** Dados de Atendimentos

Bullets:
- Registros desejados:
  - horário de início e fim de atendimento
  - tipo de atendimento e atendente/posto
- Derivar:
  - tempos de atendimento por tipo
  - distribuição de carga entre atendentes

Notas:
> “Esses dados alimentam diretamente as funções de tempo de serviço do simulador.”

---

## Slide 7 – Fontes de Dados

**Título:** Fontes de Dados

Bullets:
- Sistemas de fila/agendamento
- Logs de aplicações de atendimento
- Sistemas de gestão (quando registram tempos)
- Observação manual (quando não há registro eletrônico)
- Microdados do CadÚnico:
  - para caracterizar a população de famílias (perfis, tamanhos, renda, etc.)

Notas:
> “Os microdados do CadÚnico ajudam a caracterizar a população e perfis de demanda, enquanto outros sistemas dão tempos de operação.”

---

## Slide 8 – Estruturação em Tabelas

**Título:** Organização em Tabelas

Bullets:
- `chegadas.csv`:
  - id_familia, hora_chegada, tipo_atendimento
- `atendimentos.csv`:
  - id_familia, hora_inicio, hora_fim, atendente, tipo_atendimento
- Possível tabela de perfis (a partir dos microdados):
  - id_familia (sintético), tamanho, renda_per_capita, composição etária, etc.

Boas práticas:
- usar formatos padronizados de data/hora
- garantir chaves consistentes

Notas:
> “Uma estrutura limpa facilita muito a análise exploratória, o ajuste de distribuições e a geração de populações sintéticas.”

---

## Slide 9 – Exercícios – Coleta e Modelagem

**Título:** Exercícios – Coleta de Dados

Bullets:
- Desenhar um esquema de dados para o processo de atendimento escolhido:
  - quais colunas e tipos em cada tabela
- Propor um plano de coleta:
  - o que seria automático
  - o que precisaria de amostragem manual
- Construir uma pequena tabela fictícia com alguns registros para testar o pipeline de análise

Notas:
> “Mesmo com dados fictícios, o aluno pratica o desenho da base de dados que alimenta a simulação.”
