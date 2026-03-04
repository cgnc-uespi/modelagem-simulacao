# Sequência Pedagógica Completa — Modelagem e Simulação de Eventos Discretos (60h)
## Disciplina: Modelagem e Simulação de Eventos Discretos

**Duração:** 10 semanas | **Carga:** 60 horas totais (10h aula, 24h lab, 26h casa)

---

## 📊 ESTRUTURA DE PROGRESSÃO

```
FASE 1: Fundamentos e Conceitos (Semanas 1-2)
    ↓
FASE 2: Modelagem Conceitual (Semana 3)
    ↓
FASE 3: Implementação de Simuladores (Semanas 4-6)
    ↓
FASE 4: Análise e Experimentos (Semanas 7-8)
    ↓
FASE 5: Projeto Integrado (Semanas 9-10)
```

---

## 📅 TIMELINE SEMANAL DETALHADO

```
SEMANA  │ FASE  │ ATIVIDADES                              │ TEMPO      │ FORMATO
────────┼───────┼─────────────────────────────────────────┼────────────┼──────────
   1-2  │ FUND. │ 1.1 Componentes (fila bancária)        │ 2h         │ Aula + ex.
        │       │ 1.2 EDA — CadÚnico (amostra menor)     │ 3h         │ Lab
        │       │ 1.3 Modelagem conceitual CadÚnico      │ 2h         │ Ex + casa
────────┼───────┼─────────────────────────────────────────┼────────────┼──────────
   3    │ MOD.  │ 2.1 Pseudocódigo genérico (M/M/1)     │ 2h         │ Aula
        │       │ 2.2 Pseudocódigo CadÚnico             │ 2h         │ Aula + ex
        │       │ 2.3 Estruturas de dados (heap)         │ 2h         │ Lab
        │       │ 2.4 Diagramas UML                      │ 1h         │ Ex + casa
        │ ✅    │ CHECKPOINT: Pseudocódigo correto       │ -          │ Avaliação
────────┼───────┼─────────────────────────────────────────┼────────────┼──────────
   4    │ IMP.  │ 3.1 Distribuições e ajuste             │ 3h         │ Lab
        │       │ 3.2 Mini-projeto fila bancária         │ 5h         │ Lab + casa
────────┼───────┼─────────────────────────────────────────┼────────────┼──────────
   5-6  │ IMP.  │ 3.3 Simulador CadÚnico completo        │ 6h         │ Lab + casa
        │ ✅    │ CHECKPOINT: Código funcional           │ -          │ Avaliação
────────┼───────┼─────────────────────────────────────────┼────────────┼──────────
   7    │ ANÁ.  │ 4.1 Verificação e validação            │ 2h         │ Lab
        │       │ 4.2 Análise exploratória resultados    │ 2h         │ Lab + casa
        │       │ 4.3 Sensibilidade                      │ 2h         │ Lab
────────┼───────┼─────────────────────────────────────────┼────────────┼──────────
   8    │ ANÁ.  │ 4.4 Comparação de cenários             │ 2h         │ Lab + casa
        │ ✅    │ CHECKPOINT: Insights validados         │ -          │ Avaliação
────────┼───────┼─────────────────────────────────────────┼────────────┼──────────
   9    │ PROJ. │ 5.1 Seleção + especificação            │ 3h         │ Casa + dúvidas
        │ PROJ. │ 5.2 Modelagem conceitual               │ 3h         │ Casa + revisão
────────┼───────┼─────────────────────────────────────────┼────────────┼──────────
   10   │ PROJ. │ 5.3 Implementação do simulador         │ 6h         │ Lab + casa
        │ PROJ. │ 5.4 Experimentos e análise             │ 4h         │ Casa
        │ PROJ. │ 5.5 Apresentação final                │ 0.25h      │ Apresentação
        │ ✅    │ CHECKPOINT: Projeto completo          │ -          │ Avaliação final

TOTAL: ~60 horas (10h aula + 24h lab + 26h casa)
```

---

## FASE 1: FUNDAMENTOS E CONCEITOS
### (Semanas 1-2) | Módulos 1-2 da Disciplina

**Objetivo:** Construir vocabulário e reconhecer componentes de sistemas discretos

---

### 📌 **Atividade 1.1: Identificação de Componentes em Sistemas Reais**
**Arquivo:** `atividades_modelagem_conceitual_discreto.md` → Atividade 1
**Duração:** 2 horas (em classe + casa)

**O que faz:** Analisa sistema real (fila bancária) e identifica:
- Estado do sistema
- Eventos
- Variáveis de entrada e saída
- Diagrama de transição de estados

**Entregável:** 1 página com definição + diagrama

---

### 📊 **Atividade 1.2: Análise Exploratória de Dados — CadÚnico**
**Arquivo:** `atividades_analise_dados_cadunico.md` → Atividades 1-2
**Duração:** 3 horas (laboratório)

**O que faz:**
- Carrega amostra menor de dados (100k linhas)
- Identifica qualidade dos dados
- Explora distribuições demográficas

**Ferramentas:** Python (pandas, matplotlib)

**Entregável:** Jupyter notebook com 5-8 gráficos

---

### 🎯 **Atividade 1.3: Modelagem Conceitual do CadÚnico**
**Arquivo:** `atividades_modelagem_conceitual_discreto.md` → Atividade 2
**Duração:** 2 horas

**O que faz:**
- Define CadÚnico como sistema de eventos discretos
- Descreve eventos (nascimento, morte, mudança renda)
- Desenha diagrama de fluxo

**Entregável:** Estrutura de dados + diagrama de eventos

---

### ✅ **Checkpoint Fase 1**
Antes de prosseguir, o aluno deve:
- [ ] Identificar estado e eventos em um sistema novo
- [ ] Justificar por que simulação é necessária
- [ ] Entender relação: dados → eventos → simulação

---

## FASE 2: MODELAGEM CONCEITUAL
### (Semana 3) | Módulos 2-5 da Disciplina

**Objetivo:** Desenhar modelos discretos em pseudocódigo

---

### 🔄 **Atividade 2.1: Pseudocódigo de Simulador Genérico**
**Arquivo:** `atividades_modelagem_conceitual_discreto.md` → Atividade 3 (Versão 1)
**Duração:** 2 horas

**O que faz:**
- Estuda pseudocódigo de simulador M/M/1
- Entende: lista de eventos, avanço por próximo evento

**Entregável:** Pseudocódigo comentado + diagrama de fluxo

---

### 📈 **Atividade 2.2: Pseudocódigo CadÚnico**
**Arquivo:** `atividades_modelagem_conceitual_discreto.md` → Atividade 3 (Versão 2)
**Duração:** 2 horas

**O que faz:**
- Adapta estrutura genérica para CadÚnico
- Mostra como atualizar estado e reagendar eventos

**Entregável:** Pseudocódigo completo + fluxograma

---

### 🛠️ **Atividade 2.3: Estruturas de Dados — Lista de Eventos Futuros**
**Arquivo:** `atividades_modelagem_conceitual_discreto.md` → Atividade 4
**Duração:** 2 horas (laboratório)

**O que faz:**
- Implementa ListaEventosFuturos com heap
- Testa: inserção e extração em ordem

**Entregável:** Código Python + testes passando

---

### 📊 **Atividade 2.4: Diagramas UML para Arquitetura**
**Arquivo:** `atividades_modelagem_conceitual_discreto.md` → Atividade 6
**Duração:** 1 hora

**O que faz:**
- Desenha diagrama de classes para simulador
- Especifica atributos e métodos

**Entregável:** Diagrama UML (draw.io ou papel)

---

### ✅ **Checkpoint Fase 2**
Antes de prosseguir, o aluno deve:
- [ ] Escrever pseudocódigo correto
- [ ] Entender conceito de "lista de eventos futuros"
- [ ] Desenhar diagrama UML de sistema próprio

---

## FASE 3: IMPLEMENTAÇÃO DE SIMULADORES
### (Semanas 4-6) | Módulos 4-5 da Disciplina

**Objetivo:** Codificar e testar simuladores funcionais

---

### 💻 **Atividade 3.1: Geração de Números Aleatórios e Variáveis Aleatórias**
**Arquivo:** `atividades_analise_dados_cadunico.md` → Atividade 8
**Duração:** 3 horas (laboratório)

**O que faz:**
- Ajusta distribuições (Normal, Lognormal, Gamma) a dados reais
- Testa aderência com testes estatísticos
- Estima parâmetros

**Entregável:** Jupyter notebook com distribuições recomendadas

---

### 🎲 **Atividade 3.2: Mini-Projeto — Simulador de Atendimento (Bancário)**
**Arquivo:** `atividades_modelagem_conceitual_discreto.md` → Atividade 8
**Duração:** 5 horas (laboratório + casa)

**O que faz:**
- Implementa simulador de banco com 2 caixas
- Eventos: chegada, serviço, saída
- 20% de famílias prioritárias
- Coleta: tempo médio na fila, utilização

**Entregável:**
- Código Python (300-400 linhas)
- 2-3 gráficos (fila, histograma, utilização)
- Relatório de 1 página

---

### 📈 **Atividade 3.3: Simulador CadÚnico (Versão Simplificada)**
**Arquivo:** Customizado
**Duração:** 6 horas (laboratório + casa)

**O que faz:**
- Implementa simulador de 1000 famílias por 5 anos
- Eventos: nascimento, morte, renda, Bolsa Família
- Usa distribuições ajustadas
- Coleta: renda média, Gini, % com Bolsa

**Entregável:**
- Código Python (500-600 linhas)
- 3 gráficos de evolução temporal
- Teste de reprodutibilidade (3 sementes)

---

### ✅ **Checkpoint Fase 3**
Antes de prosseguir, o aluno deve:
- [ ] Implementar simulador funcional sem erros
- [ ] Coleta corretamente estatísticas
- [ ] Gera resultados reproduzíveis

---

## FASE 4: ANÁLISE E EXPERIMENTOS
### (Semanas 7-8) | Módulos 6-7 da Disciplina

**Objetivo:** Validar, analisar e comparar cenários

---

### 🔍 **Atividade 4.1: Verificação e Validação de Modelos**
**Arquivo:** Customizado
**Duração:** 2 horas

**O que faz:**
- Verifica se simulador está correto
- Valida contra teoria (M/M/1 ou dados reais)

**Entregável:**
- Checklist de verificação
- Tabela: Analítico vs. Simulado

---

### 📊 **Atividade 4.2: Análise Exploratória de Resultados**
**Arquivo:** Customizado
**Duração:** 2 horas

**O que faz:**
- Analisa saída de simulador CadÚnico
- Cria distribuições finais
- Identifica padrões e anomalias

**Entregável:**
- Jupyter com 4-6 visualizações
- Texto descritivo para cada achado

---

### 🧪 **Atividade 4.3: Análise de Sensibilidade**
**Arquivo:** `atividades_modelagem_conceitual_discreto.md` → Atividade 7
**Duração:** 2 horas (laboratório)

**O que faz:**
- Testa impacto de variações em 3 parâmetros chave
- Cria tabela e gráfico tornado

**Entregável:**
- Tabela de Sensibilidade
- Gráfico tornado
- Ranking de parâmetros críticos

---

### 📈 **Atividade 4.4: Comparação de Cenários**
**Arquivo:** Customizado
**Duração:** 2 horas

**O que faz:**
- Executa simulador em 3 cenários:
  1. Baseline (sem intervenção)
  2. Emprego (+20% oportunidades)
  3. Renda Básica (R$ 200/pessoa)

**Entregável:**
- Tabela de resultados comparativos
- Gráficos sobrepostos
- Análise: qual política é melhor?

---

### ✅ **Checkpoint Fase 4**
Antes de prosseguir, o aluno deve:
- [ ] Validar simulador contra dados conhecidos
- [ ] Interpretar resultados em linguagem natural
- [ ] Identificar parâmetros críticos

---

## FASE 5: PROJETO INTEGRADO
### (Semanas 9-10) | Módulos 7-8 da Disciplina

**Objetivo:** Aplicar tudo em projeto original

---

### 🎓 **Atividade 5.1: Seleção de Sistema e Especificação**
**Duração:** 3 horas

**O que faz:**
Aluno escolhe um dos 3 sistemas:
1. **Healthcare:** Pronto-socorro ou clínica
2. **Logística:** Centro de distribuição
3. **Social:** Sistema similar ao CadÚnico

**Entregável:** Especificação (1-2 páginas)
- Descrição do sistema
- Limites (o que entra/sai)
- 5-7 eventos
- Perguntas de simulação

**Aprovação:** Professor revisa e aprova

---

### 🔧 **Atividade 5.2: Modelagem Conceitual do Projeto**
**Duração:** 3 horas

**O que faz:**
Desenvolve modelo completo antes de código

**Entregável:** Relatório de modelagem (3-4 páginas)
- Diagrama de transição de estados
- Pseudocódigo de 2-3 processos chave
- Diagrama UML simplificado
- Estimativas de distribuições

---

### 💻 **Atividade 5.3: Implementação do Simulador**
**Duração:** 6 horas (laboratório + casa)

**O que faz:**
Codifica simulador em Python

**Requisitos:**
- Mínimo 500 linhas de código
- Estrutura clara (classes, funções)
- Comentários explicando lógica
- 3-5 testes de unidade
- Execução sem erros

**Entregável:**
- Código-fonte (GitHub ou compartilhado)
- Testes automatizados
- README.md

---

### 📊 **Atividade 5.4: Experimentos e Análise**
**Duração:** 4 horas (casa)

**O que faz:**
Executa simulador e analisa resultados

**Experimentos obrigatórios:**
1. Validação (vs. dados reais ou teoria)
2. Sensibilidade (3+ parâmetros)
3. Cenários (3+ alternativas)

**Entregável:** Relatório (5-8 páginas)
- Seção 1: Introdução (sistema)
- Seção 2: Modelo (resumo, distribuições)
- Seção 3: Implementação (arquitetura)
- Seção 4: Resultados (tabelas + gráficos)
- Seção 5: Conclusões (respostas a perguntas)

---

### 🎤 **Atividade 5.5: Apresentação Final**
**Duração:** 15 minutos + 5 minutos Q&A

**O que apresentar:**
1. Sistema (visão geral, 2 min)
2. Modelo (diagrama, 2 min)
3. Implementação (arquitetura, 2 min)
4. Resultados (gráficos, 4 min)
5. Insights e recomendações (3 min)
6. Q&A (5 min)

---

### ✅ **Checkpoint Final**
Aluno entrega:
- [ ] Código comentado
- [ ] Relatório técnico (5-8 páginas)
- [ ] Apresentação com slides
- [ ] Demonstração de compreensão profunda em Q&A

---

## 📊 MAPA DE ALINHAMENTO COM MÓDULOS

| Módulo | Objetivo | Atividades |
|--------|----------|-----------|
| **1** | Sistemas, modelos, simulação | 1.1, 1.2 |
| **2** | Eventos discretos | 1.3, 2.1, 2.2 |
| **3** | Processos de chegada/atendimento | 1.2, 3.1, 3.2 |
| **4** | Números e distribuições | 3.1, 3.2 |
| **5** | Construção de modelos | 2.1, 2.2, 3.2, 3.3 |
| **6** | Verificação e validação | 2.3, 4.1 |
| **7** | Projetos de experimentos | 4.2, 4.3, 4.4 |
| **8** | Aplicações e projetos | 5.1-5.5 |

---

## 📋 DISTRIBUIÇÃO DE HORAS (60h total)

| ATIVIDADE | AULA | LAB | CASA | TOTAL |
|-----------|------|-----|------|-------|
| 1.1 Componentes | 1.5 | 0 | 0.5 | 2.0 |
| 1.2 Dados CadÚnico | 0 | 3 | 0 | 3.0 |
| 1.3 Modelagem | 1 | 0 | 1 | 2.0 |
| 2.1 Pseudo Genérico | 2 | 0 | 0 | 2.0 |
| 2.2 Pseudo CadÚnico | 0 | 1 | 1 | 2.0 |
| 2.3 Estruturas | 0 | 2 | 0 | 2.0 |
| 2.4 UML | 0 | 0 | 1 | 1.0 |
| 3.1 Distribuições | 0 | 3 | 0 | 3.0 |
| 3.2 Fila Bancária | 0 | 3 | 2 | 5.0 |
| 3.3 CadÚnico Sim. | 0 | 3 | 3 | 6.0 |
| 4.1 Validação | 0 | 2 | 0 | 2.0 |
| 4.2 EDA Resultados | 0 | 1 | 1 | 2.0 |
| 4.3 Sensibilidade | 0 | 2 | 0 | 2.0 |
| 4.4 Cenários | 0 | 1 | 1 | 2.0 |
| 5.1 Seleção | 0 | 0 | 3 | 3.0 |
| 5.2 Modelagem Proj | 0 | 0 | 3 | 3.0 |
| 5.3 Implementação | 0 | 3 | 3 | 6.0 |
| 5.4 Experimentos | 0 | 0 | 4 | 4.0 |
| 5.5 Apresentação | 0 | 0 | 0 | 0.25 |
|-----------|------|-----|------|-------|
| **TOTAL** | **10.5** | **24** | **26** | **60.5** |

**Distribuição:**
- Aula teórica: 17% (conceitos)
- Laboratório: 40% (prática guiada)
- Casa: 43% (prática independente)

---

## 🏆 CRITÉRIOS DE AVALIAÇÃO

### Avaliação Contínua (50%)

```
Fase 1 (Semanas 1-2): 5%
Fase 2 (Semana 3): 10%
Fase 3 (Semanas 4-6): 15%
Fase 4 (Semanas 7-8): 20%
```

### Projeto Integrado (50%)

```
Especificação (5.1): 5%
Modelagem (5.2): 5%
Implementação (5.3): 20%
Análise (5.4): 15%
Apresentação (5.5): 5%
```

### Pesos por Critério

- Corretude técnica: 40%
- Clareza e documentação: 30%
- Interpretação e insights: 20%
- Originalidade: 10%

---

## 🎓 CHECKLIST FINAL DO ALUNO

Ao terminar a disciplina, você deve:

- [ ] Diferenciar entre sistema, modelo e simulação
- [ ] Identificar estado, eventos, variáveis em qualquer sistema
- [ ] Desenhar diagrama de transição correto
- [ ] Escrever pseudocódigo legível e funcional
- [ ] Implementar simulador em Python
- [ ] Ajustar distribuições a dados reais
- [ ] Validar simulador contra dados/teoria
- [ ] Executar análise de sensibilidade
- [ ] Comparar cenários e fazer recomendações
- [ ] Comunicar resultados em relatório profissional

