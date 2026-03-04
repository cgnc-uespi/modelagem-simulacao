# Disciplina: Modelagem e Simulação de Eventos Discretos

_Estudo de Caso Central: Cadastro Único para Programas Sociais (CadÚnico)_

Este diretório reúne materiais da disciplina, organizados para uso como professor (notas, slides, exercícios e projetos). A disciplina está dimensionada para **60 horas (10 semanas)**.

---

## Estrutura de Pastas

- `ppt/` — Slides de referência em PowerPoint (.pptx) para estudo e suporte a quizes
- `notas/` — Notas teóricas por aula e roteiros de slides em Markdown
- `exercicios/` — Atividades práticas, guia do professor e sequência pedagógica
- `projetos/` — Dados CadÚnico, scripts de EDA e propostas de projetos

---

## Slides de Referência (PowerPoint)

Slides das aulas em formato `.pptx`, disponíveis para estudo e suporte a quizes:

- `ppt/Sobre a Disciplina.pptx`
- `ppt/Introdução à Modelagem e Simulação.pptx`
- `ppt/Simulação Manual e Especificação de Modelos.pptx`
- `ppt/ACD do supermercado.pptx`
- `ppt/Abstração e Diagrama de Ciclos.pptx`
- `ppt/Implementação Computacional do Modelo.pptx`
- `ppt/Modelagem e Coleta de Dados.pptx`
- `ppt/Tratamento de Dados.pptx`
- `ppt/Ajuste de Dados.pptx`
- `ppt/Teste de Aderência.pptx`
- `ppt/Verificação e Validação de Modelos.pptx`
- `ppt/Dimensionamento e Análise de Resultados - Parte I.pptx`
- `ppt/Dimensionamento e Análise de Resultados - Parte II.pptx`

---

## Notas de Aula (Teoria)

Notas principais, usando CadÚnico como estudo de caso:

- `notas/aula01_introducao_modelagem_simulacao.md`
- `notas/aula02_conceitos_simulacao_eventos_discretos.md`
- `notas/aula03_processos_chegada_atendimento_filas.md`
- `notas/aula04_numeros_pseudoaleatorios_variaveis_aleatorias.md`
- `notas/aula05_modelos_filas_simulacao.md`
- `notas/aula06_verificacao_validacao_modelos.md`
- `notas/aula07_projeto_experimentos_analise_resultados.md`
- `notas/aula08_aplicacoes_projetos.md`

Resumo geral:

- `notas/slides_resumo_cadunico.md` — visão de alto nível das aulas e do uso do CadÚnico.

---

## Slides (Roteiros para PowerPoint)

Cada arquivo abaixo contém um esqueleto de slides (títulos, bullets e notas do apresentador):

- `notas/slides_introducao_cadunico.md` → Introdução à Modelagem e Simulação
- `notas/slides_simulacao_manual_cadunico.md` → Simulação Manual e Especificação de Modelos
- `notas/slides_simulador_atendimento_cadunico.md` → Introdução ao Simulador de Atendimento
- `notas/slides_implementacao_modelo_cadunico.md` → Implementação Computacional do Modelo
- `notas/slides_dimensionamento_analise_cadunico.md` → Dimensionamento e Análise de Resultados
- `notas/slides_ajuste_aderencia_cadunico.md` → Ajuste de Dados e Testes de Aderência
- `notas/slides_modelagem_coleta_cadunico.md` → Modelagem e Coleta de Dados
- `notas/slides_tratamento_dados_cadunico.md` → Tratamento de Dados
- `notas/slides_abstracao_diagramas_cadunico.md` → Abstração e Diagrama de Ciclos

---

## Exercícios e Atividades

Guia completo do professor (60h, 10 semanas) — **comece por aqui:**

- `exercicios/INDEX.md` — Índice de todos os materiais (leia primeiro)
- `exercicios/README_PROFESSOR.md` — Guia completo do professor
- `exercicios/SEQUENCIA_PEDAGOGICA.md` — Plano semana a semana (10 semanas)
- `exercicios/INFOGRAFICO.md` — Visualizações da sequência (para mostrar aos alunos)

Atividades práticas:

- `exercicios/atividades_modelagem_conceitual_discreto.md` — 8 atividades de modelagem e pseudocódigo (~20h)
- `exercicios/atividades_analise_dados_cadunico.md` — 10 atividades com dados reais (~20h)
- `exercicios/listas_exercicios_cadunico.md` — Listas complementares por aula

---

## Projetos

Propostas de projetos aplicados ao CadÚnico:

- `projetos/projetos_cadunico.md`

Projetos incluídos:
- dimensionamento de atendimento em CRAS;
- impacto de campanhas de regularização cadastral;
- análise de backlog de atualizações;
- priorização de perfis de família;
- CadÚnico multicanal (presencial + online).

Dados disponíveis:
- `projetos/base_amostra_cad_201812/` — Microdados CadÚnico (dezembro/2018)
- `projetos/Dicionário_de_Dados_-_CadÚnico_-_Divulgação.xlsx`
- `projetos/eda_cadunico.py` — Script EDA base
- `projetos/eda_output/` — Visualizações geradas pelo EDA

---

## Planejamento / Roadmap

Dois arquivos ajudam a planejar o semestre:

- `plano_disciplina_modelagem_simulacao_eventos_discretos.md` — Estrutura geral dos módulos
- `plano_rodadas_aula_cadunico.md` — Roadmap semana a semana (10 semanas, 60h)

---

## Fontes de Dados CadÚnico

- Microdados: <https://dados.gov.br/dados/conjuntos-dados/microdados-amostrais-do-cadastro-unico>
- Observatório: <https://paineis.mds.gov.br/public/extensions/observatorio-do-cadastro-unico/index.html>
- Data Explorer: <https://aplicacoes.cidadania.gov.br/vis/data3/data-explorer.php>

---

## Como Usar

1. **Planejamento:** Leia `exercicios/INDEX.md` para visão completa do curso
2. **Slides de referência:** Use `ppt/` para apresentar em sala e compartilhar com os alunos para estudo e quizes
3. **Preparar slides:** Abrir `notas/slides_*_cadunico.md` e criar `.pptx` correspondente
4. **Estudar notas:** Arquivos `aula0X_*.md` como referência em sala
5. **Aplicar atividades:** Usar `exercicios/atividades_*.md` conforme a semana (veja `exercicios/SEQUENCIA_PEDAGOGICA.md`)
6. **Orientar projetos:** Pedir que grupos escolham tema em `projetos/projetos_cadunico.md`

Esse setup permite dar a disciplina inteira com um fio condutor único (CadÚnico), mantendo a flexibilidade para adaptar profundidade conforme o andamento da turma.
