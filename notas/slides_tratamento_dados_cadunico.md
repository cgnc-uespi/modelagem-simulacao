# Slides – Tratamento de Dados (CadÚnico)

## Slide 1 – Título

**Título:** Tratamento de Dados  
**Subtítulo:** Preparando Dados para Simulação (CadÚnico)

Notas:
> “Agora que sabemos o que coletar, vamos tratar esses dados (observacionais + microdados) para que possam ser usados no modelo de simulação.”

---

## Slide 2 – Objetivos

**Título:** Objetivos da Aula

Bullets:
- Limpar e organizar dados brutos de atendimento
- Identificar e tratar outliers e inconsistências
- Construir séries de tempos entre chegadas e tempos de atendimento

Notas:
> “Sem dados limpos, qualquer simulação é questionável.”

---

## Slide 3 – Problemas Comuns

**Título:** Problemas Comuns em Dados

Bullets:
- Registros incompletos
- Horários invertidos (fim antes do início)
- Tempos zero ou negativos
- Outliers extremos (tempos muito curtos ou muito longos)

Notas:
> “É importante ensinar o aluno a desconfiar e investigar dados suspeitos.”

---

## Slide 4 – Limpeza Básica

**Título:** Limpeza Básica

Bullets:
- Remover linhas com campos essenciais faltando
- Corrigir formatos de data/hora
- Eliminar registros claramente inválidos
- Verificar consistência de IDs

Notas:
> “São as primeiras etapas de qualquer pipeline de dados.”

---

## Slide 5 – Cálculo de Tempos

**Título:** Cálculo de Tempos

Bullets:
- Tempos de atendimento:
  - `tempo_servico = hora_fim - hora_inicio`
- Tempos entre chegadas:
  - ordenar por `hora_chegada`
  - `interarrival_i = chegada_i - chegada_{i-1}`

Notas:
> “Essas séries são a matéria-prima dos ajustes de distribuição.”

---

## Slide 6 – Identificação de Outliers

**Título:** Outliers

Bullets:
- Métodos visuais:
  - boxplot
  - histograma
- Regras simples:
  - valores acima de certo quantil (ex.: > 99%)
  - valores abaixo de um mínimo plausível (ex.: < 1 minuto)

Exemplos:
- atendimento de 0 segundos?  
- atendimento de 8 horas?

Notas:
> “Discutir se cada outlier é erro ou um caso extremo real.”

---

## Slide 7 – Segmentação dos Dados

**Título:** Segmentação dos Dados

Bullets:
- Por tipo de atendimento:
  - novo cadastro, atualização, orientação, etc.
- Por horário:
  - pico vs fora de pico
- Benefícios:
  - modelos mais precisos para cada segmento

Notas:
> “Muitas vezes, um único ajuste global mascara comportamentos muito diferentes entre segmentos.”

---

## Slide 8 – Arquivos ‘limpos’

**Título:** Arquivos Limpos para Análise

Bullets:
- Criar arquivos pós-limpeza:
  - `tempos_servico_limpos.csv`
  - `tempos_interchegadas_limpos.csv`
- Estrutura:
  - uma observação por linha
  - colunas de identificação mínima (tipo, horário, etc.)

Notas:
> “São esses arquivos que vão alimentar notebooks de ajuste e o simulador.”

---

## Slide 9 – Exercícios – Tratamento

**Título:** Exercícios – Tratamento de Dados

Bullets:
- Dada uma base bruta (real ou fictícia):
  - identificar registros problemáticos
  - propor regras de limpeza
  - gerar uma versão ‘limpa’ dos tempos de serviço e interchegadas
- Documentar:
  - decisões de limpeza
  - impactos previstos no modelo

Notas:
> “O aluno aprende a justificar suas escolhas de tratamento de dados, e não apenas apertar botões.”
