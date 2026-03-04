# Roadmap da Disciplina – Modelagem e Simulação (CadÚnico)

_Estrutura de 10 semanas (60h) usando o CadÚnico como estudo de caso central._

**Versão:** 2.0 (60 horas, 10 semanas)
**Carga horária:** 10h aula + 24h laboratório + 26h casa

---

## Visão Geral

- Estudo de caso: **Cadastro Único para Programas Sociais (CadÚnico)** — atendimento em CRAS, inclusão e atualização cadastral, elegibilidade para benefícios.
- Dados reais: microdados amostrais do CadÚnico (dados.gov.br).
- 5 fases progressivas: Fundamentos → Modelagem → Implementação → Análise → Projeto.

Referências:
- <https://dados.gov.br/dados/conjuntos-dados/microdados-amostrais-do-cadastro-unico>
- Observatório: <https://paineis.mds.gov.br/public/extensions/observatorio-do-cadastro-unico/index.html>
- Data Explorer: <https://aplicacoes.cidadania.gov.br/vis/data3/data-explorer.php>

Consulte `exercicios/SEQUENCIA_PEDAGOGICA.md` para o guia detalhado semana a semana.

---

## FASE 1 — Fundamentos (Semanas 1–2, ~7h)

### Semana 1 – Conceitos de Eventos Discretos + CadÚnico

**Objetivos:**
- Apresentar a disciplina, sistemas, modelos e simulação de eventos discretos.
- Contextualizar o CadÚnico como estudo de caso.

**Materiais:**
- Deck: `notas/slides_introducao_cadunico.md`
- Deck: `notas/slides_abstracao_diagramas_cadunico.md`
- Notas: `notas/aula01_introducao_modelagem_simulacao.md`, `notas/aula02_conceitos_simulacao_eventos_discretos.md`

**Atividades (exercicios/):**
- Atividade 1.1 → `atividades_modelagem_conceitual_discreto.md` (Atividade 1 — Componentes)
- Atividade 1.2 → `atividades_analise_dados_cadunico.md` (Atividades 1–2 — Exploração inicial)

**Exercícios complementares:** `listas_exercicios_cadunico.md` — Lista Aulas 1–2

---

### Semana 2 – Processos de Chegada, Filas e Dados CadÚnico

**Objetivos:**
- Modelar chegadas e atendimentos; disciplina de fila.
- Primeira exploração dos microdados (EDA básica).

**Materiais:**
- Deck: `notas/slides_simulacao_manual_cadunico.md`
- Deck: `notas/slides_modelagem_coleta_cadunico.md`
- Notas: `notas/aula03_processos_chegada_atendimento_filas.md`

**Atividades (exercicios/):**
- Atividade 1.3 → `atividades_modelagem_conceitual_discreto.md` (Atividade 2 — Pseudocódigo básico)
- `atividades_analise_dados_cadunico.md` (continuação Atividades 1–2)

**Exercícios complementares:** `listas_exercicios_cadunico.md` — Lista Aula 3

---

## FASE 2 — Modelagem (Semana 3, ~7h)

### Semana 3 – Pseudocódigo, UML e Especificação de Modelos

**Objetivos:**
- Escrever pseudocódigo para eventos discretos.
- Usar diagramas UML/atividades para especificar o modelo CadÚnico.
- Modelar variáveis aleatórias (chegadas, atendimentos).

**Materiais:**
- Notas: `notas/aula04_numeros_pseudoaleatorios_variaveis_aleatorias.md`
- Notas: `notas/aula05_modelos_filas_simulacao.md`
- Deck: `notas/slides_ajuste_aderencia_cadunico.md` (parte introdutória)

**Atividades (exercicios/):**
- Atividades 2.1–2.4 → `atividades_modelagem_conceitual_discreto.md` (Atividades 3–6)

**Exercícios complementares:** `listas_exercicios_cadunico.md` — Listas Aulas 4–5

---

## FASE 3 — Implementação (Semanas 4–6, ~14h)

### Semana 4 – Distribuições e Mini-Fila

**Objetivos:**
- Ajustar distribuições a dados reais de tempo.
- Implementar geração de variáveis aleatórias.
- Mini-simulador de fila com 1 servidor.

**Materiais:**
- Deck: `notas/slides_tratamento_dados_cadunico.md`
- Deck: `notas/slides_ajuste_aderencia_cadunico.md`
- Notas: `notas/aula04_numeros_pseudoaleatorios_variaveis_aleatorias.md`

**Atividades (exercicios/):**
- Atividade 3.1 → `atividades_analise_dados_cadunico.md` (Atividade 8 — Distribuições)
- Atividade 3.2 → `atividades_modelagem_conceitual_discreto.md` (Atividade 8 — Mini-fila)

**Exercícios complementares:** `listas_exercicios_cadunico.md` — Lista Aula 4

---

### Semanas 5–6 – Implementação do Simulador Completo

**Objetivos:**
- Implementar simulador de eventos discretos completo para atendimento CadÚnico.
- Integrar dados reais como parâmetros.

**Materiais:**
- Deck: `notas/slides_implementacao_modelo_cadunico.md`
- Deck: `notas/slides_simulador_atendimento_cadunico.md`
- Notas: `notas/aula05_modelos_filas_simulacao.md`

**Atividades (exercicios/):**
- Atividade 3.3 → `exercicios/SEQUENCIA_PEDAGOGICA.md` (guia de codificação — Fase 3)

**Exercícios complementares:** `listas_exercicios_cadunico.md` — Lista Aula 5

---

## FASE 4 — Análise e Validação (Semanas 7–8, ~8h)

### Semana 7 – Verificação, Validação e Análise de Resultados

**Objetivos:**
- Verificar e validar o simulador.
- Analisar resultados: tempos de espera, utilização de servidores, métricas de desempenho.

**Materiais:**
- Notas: `notas/aula06_verificacao_validacao_modelos.md`
- Notas: `notas/aula07_projeto_experimentos_analise_resultados.md`
- Deck: `notas/slides_dimensionamento_analise_cadunico.md`

**Atividades (exercicios/):**
- Atividades 4.1–4.3 → `atividades_modelagem_conceitual_discreto.md` (Atividade 7) + `SEQUENCIA_PEDAGOGICA.md` (Verificação + EDA)

**Exercícios complementares:** `listas_exercicios_cadunico.md` — Listas Aulas 6–7

---

### Semana 8 – Cenários e Análise de Sensibilidade

**Objetivos:**
- Projetar e executar experimentos com cenários alternativos (ex.: aumento de demanda, mudança de atendentes).
- Comparar cenários e extrair recomendações.

**Materiais:**
- Notas: `notas/aula07_projeto_experimentos_analise_resultados.md`

**Atividades (exercicios/):**
- Atividade 4.4 → `exercicios/SEQUENCIA_PEDAGOGICA.md` (Cenários)

**Exercícios complementares:** `listas_exercicios_cadunico.md` — Lista Aula 7

---

## FASE 5 — Projeto Integrado (Semanas 9–10, ~16h)

### Semana 9 – Design e Especificação do Projeto Final

**Objetivos:**
- Cada grupo define seu problema de simulação usando dados CadÚnico.
- Especificar modelo, métricas e plano de experimentos.

**Materiais:**
- Notas: `notas/aula08_aplicacoes_projetos.md`
- Projetos: `projetos/projetos_cadunico.md`
- Guia: `exercicios/SEQUENCIA_PEDAGOGICA.md` (seção FASE 5 — especificação)

**Atividades (exercicios/):**
- Atividades 5.1–5.2 → `exercicios/SEQUENCIA_PEDAGOGICA.md`

**Temas sugeridos:**
- Dimensionamento de equipe em CRAS em pico de demanda
- Impacto de mudança de critério de elegibilidade sobre o backlog
- Priorização de famílias vulneráveis no atendimento
- Análise de cenários de expansão de postos de atendimento

---

### Semana 10 – Implementação, Resultados e Apresentações

**Objetivos:**
- Finalizar implementação do simulador do projeto.
- Analisar resultados e preparar relatório/apresentação.
- Apresentações dos grupos (15 min + 5 min perguntas).

**Materiais:**
- Deck: `notas/slides_resumo_cadunico.md`
- Guia: `exercicios/SEQUENCIA_PEDAGOGICA.md` (seção FASE 5 — implementação e apresentação)

**Atividades (exercicios/):**
- Atividades 5.3–5.5 → `exercicios/SEQUENCIA_PEDAGOGICA.md`

**Entregável esperado:** Relatório 5–8 páginas + apresentação 15 min
_(Ver detalhes em `exercicios/SEQUENCIA_PEDAGOGICA.md`, seção "Atividade 5.4")_

---

## Distribuição de Horas

```
SEMANA  │ FASE  │ AULA  │ LAB   │ CASA  │ TOTAL
────────┼───────┼───────┼───────┼───────┼───────
  1–2   │   1   │  2.5h │  3.0h │  3.5h │   7h
   3    │   2   │  2.0h │  4.0h │  2.0h │   7h (+ pendência)
   4    │   3   │  1.0h │  3.0h │  2.0h │   8h
  5–6   │   3   │  1.0h │  3.0h │  3.0h │   6h (+ pendência)
   7    │   4   │  1.5h │  5.0h │  2.0h │   6h (+ pendência)
   8    │   4   │  0.5h │  2.0h │  2.0h │   2h (+ relatório)
   9    │   5   │  1.0h │  0.0h │  6.0h │   6h (projeto)
  10    │   5   │  1.0h │  3.0h │  7.0h │  10h (entrega)
────────┼───────┼───────┼───────┼───────┼───────
TOTAL   │       │  10h  │  24h  │  26h  │  60h
```

---

## Observações

- O CadÚnico serve como fio condutor; outros exemplos (supermercado, hospital, redes) podem aparecer pontualmente para comparação.
- A Fase 3 (Implementação) pode ser ajustada conforme o nível da turma — o simulador pode ser fornecido pronto se o foco for análise, não programação.
- Para o projeto final, orientar os grupos a escolher um tema factível com os dados disponíveis em `projetos/base_amostra_cad_201812/`.
- Guia completo do professor: `exercicios/README_PROFESSOR.md`
