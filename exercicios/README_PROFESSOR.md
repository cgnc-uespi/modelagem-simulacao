# Guia do Professor: Modelagem e Simulação de Eventos Discretos (60h)
## Como Usar os Materiais Pedagógicos

**Versão:** 2.0 (60 horas, 10 semanas)
**Última atualização:** 2026-02-22
**Status:** Pronto para implementação

---

## 📚 Visão Geral

Este pacote contém **materiais integrados** que cobrem uma disciplina de **10 semanas (60 horas)** sobre Modelagem e Simulação de Eventos Discretos, com aplicação prática usando dados do CadÚnico.

### Documentos Principais

```
1. SEQUENCIA_PEDAGOGICA.md
   └─ Guia semana-a-semana (10 semanas, 60 horas)

2. INFOGRAFICO.md
   └─ 10 visualizações (timeline, checkpoints, distribuição)

3. atividades_analise_dados_cadunico.md
   └─ 10 atividades com dados reais (CadÚnico)

4. atividades_modelagem_conceitual_discreto.md
   └─ 8 atividades de pseudocódigo e arquitetura

5. README_PROFESSOR.md (este arquivo)
   └─ Instruções de implementação e adaptação
```

---

## 🎯 Para Começar: Roteiro de 5 Dias

### Dia 1: Revise os Documentos
- [ ] Leia `SEQUENCIA_PEDAGOGICA.md` (entenda progressão 10 semanas)
- [ ] Leia `INFOGRAFICO.md` (veja estrutura visual)
- [ ] Nota: Tudo cabe em 10 semanas (vs. 14 originais)

### Dia 2: Prepare o Ambiente
- [ ] Verifique acesso aos dados (`base_amostra_pessoa_201812.csv`, `base_amostra_familia_201812.csv`)
- [ ] Configure Python + Jupyter (pandas, scipy, matplotlib, numpy)
- [ ] Teste com amostra pequena (100k linhas)

### Dia 3: Prepare Semana 1
- [ ] Estude `atividades_modelagem_conceitual_discreto.md` (Atividade 1)
- [ ] Prepare exemplo prático (fila bancária)
- [ ] Prepare slides ou apresentação para primeira aula

### Dia 4: Configure Entrega
- [ ] Setup GitHub Classroom (se usar versionamento)
- [ ] Crie pasta compartilhada para dados e templates
- [ ] Comunique calendário aos alunos

### Dia 5: Comece a Aula
- [ ] Mostre `INFOGRAFICO.md` (diagrama de progressão)
- [ ] Apresente disciplina: 10 semanas, progressão clara
- [ ] Comece Atividade 1.1 (Identificação de Componentes)

---

## 📖 Como Usar Cada Documento

### 1️⃣ `SEQUENCIA_PEDAGOGICA.md` — Seu Guia Principal

**Propósito:** Roteiro semana-a-semana (10 semanas)

**Como usar:**

```
Cada semana:
1. Abra a seção da semana em SEQUENCIA_PEDAGOGICA.md
2. Leia "Atividade X.Y", "Duração", "Objetivo"
3. Abra arquivo referenciado (atividades_*.md)
4. Prepare material (slides, exemplos)
5. Execute em aula/laboratório com alunos
6. Verifique Checkpoint ao fim da fase
```

**Exemplo — Semana 1:**

```markdown
### 📌 **Atividade 1.1: Identificação de Componentes**
Duração: 2 horas (em classe + casa)
Arquivo: atividades_modelagem_conceitual_discreto.md → Atividade 1

→ Professor faz:
  1. Abre documento atividades_modelagem_conceitual_discreto.md
  2. Apresenta exemplo: "Fila de banco"
  3. Guia alunos a preencherem: Estado, Eventos, Variáveis
  4. Alunos desenham diagrama de transição
  5. Entrega: 1 página + diagrama
```

### 2️⃣ `atividades_modelagem_conceitual_discreto.md` — Conteúdo Prático

**Propósito:** 8 atividades de pseudocódigo e modelagem

**Quando usar:**

- **Semana 1:** Atividade 1 (identificação de componentes)
- **Semana 3:** Atividades 2-6 (pseudocódigo, UML, estruturas)
- **Semana 7-8:** Atividades 7-8 (sensibilidade, projetos)

**Como adaptar:**

- Substitua exemplo "banco" por "hospital", "supermercado", etc.
- Use dados locais (sua região)
- Crie versões simplificadas para turmas iniciantes

### 3️⃣ `atividades_analise_dados_cadunico.md` — Dados Reais

**Propósito:** 10 atividades com dados CadÚnico

**Quando usar:**

- **Semana 1-2:** Atividades 1-3 (exploração, distribuições demográficas)
- **Semana 4:** Atividade 8 (ajuste de distribuições para simulação)
- **Semana 7-8:** Atividades 4-7 (análise de resultados)

**Como adaptar:**

- Use **amostra menor** (100k linhas) para máquinas lentas
- Substitua CadÚnico por outro dataset público (ENEM, Saúde, etc.)
- Reduza número de gráficos se tempo for limitado

### 4️⃣ `INFOGRAFICO.md` — Visualizações

**Propósito:** 10 visualizações da sequência

**Como usar:**

```
COM ALUNOS:
• Semana 1: Mostre "Diagrama de Progressão" (motivação)
• Semana 3: Mostre "Timeline Semanal" (expectations)
• Semana 6: Mostre "Progressão de Complexidade" (célébrazione progresso)
• Semana 10: Mostre "Checkpoints" (consolidação)

COM STAKEHOLDERS:
• Coordenação: "Distribuição de Horas" (justifique carga)
• Pais: "Mapa de Conceitos" (mostre o que aprenderão)
```

---

## 🔄 Sequência de Implementação Semana-a-Semana

### SEMANA 1-2: FUNDAMENTOS (7 horas)

**Objetivo:** Construir vocabulário, reconhecer componentes de sistemas

#### Aula 1 (2h)
- Apresente disciplina usando `INFOGRAFICO.md`
- Defina: sistema, modelo, simulação (use exemplos locais)
- Mostre CadÚnico como caso unificador
- **Tarefa:** Atividade 1.1 — Componentes de fila bancária

#### Laboratório 1 (3h)
- Execute Atividade 1.2 — Análise Exploratória CadÚnico
- Alunos carregam dados (100k linhas)
- Criam 5-8 gráficos (sexo, idade, renda, escolaridade)
- **Entrega:** Jupyter notebook

#### Casa (2h)
- Atividade 1.3 — Modelagem conceitual
- Aluno descreve CadÚnico como sistema (estado, eventos)
- Desenha diagrama de fluxo

**Checkpoint 1:**
- [ ] Aluno identifica estado × eventos em novo sistema
- [ ] Diagrama está correto
- [ ] Entende relação: dados reais → eventos → simulação

---

### SEMANA 3: MODELAGEM CONCEITUAL (7 horas)

**Objetivo:** Desenhar modelos em pseudocódigo antes de programar

#### Aula 2 (2h)
- Apresente pseudocódigo genérico (Atividade 2.1)
- Explique: inicialização, loop principal, finalização
- Faça trace manual de 5 eventos (projetor)

#### Laboratório 2 (4h)
- Atividade 2.2: Pseudocódigo CadÚnico específico
- Atividade 2.3: Estruturas de dados (ListaEventosFuturos com heap)
- Alunos implementam e testam em Python

#### Casa (1h)
- Atividade 2.4: Diagrama UML simplificado
- Especifique: classes, atributos, métodos

**Checkpoint 2:**
- [ ] Pseudocódigo é correto
- [ ] UML é preciso
- [ ] Aluno faz trace manual sem erros

---

### SEMANA 4: DISTRIBUIÇÕES (8 horas)

**Objetivo:** Ajustar distribuições a dados reais

#### Laboratório 3 (3h)
- Atividade 3.1: Ajuste de distribuições
- Use dados CadÚnico (renda, idade, tamanho família)
- Teste 5 distribuições, Q-Q plots
- Escolha melhor ajuste

#### Casa (5h)
- Atividade 3.2: Mini-projeto fila bancária
- Implementar simulador com 2 caixas
- 20% de famílias prioritárias
- Coleta: tempo média, histogramas

**Entrega:** Código Python + 2-3 gráficos + relatório 1 pág

---

### SEMANAS 5-6: SIMULADOR CADUNICO (6 horas)

**Objetivo:** Implementar simulador completo

#### Laboratório 4-5 (3h)
- Atividade 3.3: Simulador CadÚnico
- 1000 famílias × 5 anos
- Distribuições ajustadas
- Eventos: nascimento, morte, renda, Bolsa Família

#### Casa (3h)
- Debugging, melhorias, testes
- Código comentado, 3-5 testes unitários
- Teste com 3 sementes (reprodutibilidade)

**Entrega:** Código robusto (500-600 linhas) + 3 gráficos

**Checkpoint 3:**
- [ ] Código executa sem erro
- [ ] Resultados reproduzíveis
- [ ] Testes passam

---

### SEMANA 7: VALIDAÇÃO E SENSIBILIDADE (6 horas)

**Objetivo:** Validar modelo, analisar sensibilidade

#### Laboratório 6 (5h)
- Atividade 4.1: Validação (simulado vs. real/analítico)
- Atividade 4.2: Análise exploratória de resultados
- Atividade 4.3: Sensibilidade de parâmetros

#### Casa (1h)
- Consolidação de análises

**Entregáveis:**
- Tabela de validação
- 4-6 gráficos de análise
- Ranking de parâmetros críticos

---

### SEMANA 8: CENÁRIOS (2 horas)

**Objetivo:** Comparar alternativas, fazer recomendações

#### Laboratório 7 (1h)
- Atividade 4.4: Comparação de 3 cenários
- Baseline vs. Emprego (+20%) vs. Renda Básica (R$ 200/pessoa)

#### Casa (1h)
- Relatório consolidado (1-2 páginas)
- Qual política é melhor e por quê?

**Checkpoint 4:**
- [ ] Validação completa
- [ ] Sensibilidade clara
- [ ] Recomendação fundamentada

---

### SEMANA 9: PROJETO — ESPECIFICAÇÃO (6 horas)

**Objetivo:** Aluno escolhe novo sistema e modela

#### Orientação (0.5h)
- Apresente 3 temas: Healthcare, Logística, Social
- Alunos escolhem em grupo (até 3) ou individual

#### Casa (5.5h)
- Atividade 5.1: Especificação (1-2 páginas)
  - Descrição do sistema
  - Limites (entrada/saída)
  - 5-7 eventos
  - Perguntas de simulação

- Atividade 5.2: Modelagem conceitual (3-4 páginas)
  - Diagrama de transição
  - Pseudocódigo 2-3 processos
  - UML simplificado
  - Distribuições estimadas

**Entrega:** Relatório de modelagem (4-5 páginas)
**Aprovação:** Professor revisa e aprova antes de codificação

---

### SEMANA 10: PROJETO — IMPLEMENTAÇÃO (10 horas)

**Objetivo:** Implementar, analisar e apresentar

#### Laboratório 8 (3h)
- Atividade 5.3: Implementação do simulador
- Orientação em dúvidas
- Testes

#### Casa (7h)
- Atividade 5.3 (cont.): Código robusto (500+ linhas)
- Atividade 5.4: Experimentos e análise (4h)
  - Validação
  - Sensibilidade
  - Comparação de cenários
- Atividade 5.4 (cont.): Relatório final (5-8 páginas)

#### Apresentação (0.25h)
- Atividade 5.5: Apresentação final (15 min + 5 min Q&A)
- Sistema, modelo, implementação, resultados, recomendações

---

## 📊 Checklist de Preparação do Professor

### Infraestrutura
- [ ] Laboratório com Python 3.10+
- [ ] Jupyter Notebook/JupyterLab instalado
- [ ] Bibliotecas: pandas, scipy, matplotlib, numpy, scikit-learn (opção)
- [ ] Dados CadÚnico baixados e testados
- [ ] GitHub Classroom configurado (opção)

### Documentação
- [ ] Imprima ou compartilhe os 5 documentos com alunos
- [ ] Crie pasta compartilhada (Google Drive/OneDrive) para dados
- [ ] Prepare templates de Jupyter notebook
- [ ] Crie rubrics de avaliação para cada fase

### Exemplos
- [ ] Prepare exemplo completo de fila bancária (funcionando)
- [ ] Crie slides para Semana 1 (motivação)
- [ ] Grave 1-2 vídeos tutoriais (opcional)

### Comunicação
- [ ] Defina dias/horários de laboratório
- [ ] Configure horário de dúvidas (presencial ou Discord/Slack)
- [ ] Crie calendário de entregas (10 semanas)
- [ ] Comunique prazos aos alunos na Semana 1

---

## 📋 Critérios de Avaliação (60 horas, 10 semanas)

### Avaliação Contínua (50%)

```
Fase 1 (Semanas 1-2): 5%
├─ Atividade 1.1: Componentes (1%)
├─ Atividade 1.2: EDA (2%)
└─ Atividade 1.3: Modelagem (2%)

Fase 2 (Semana 3): 10%
├─ Atividades 2.1-2.2: Pseudocódigo (5%)
├─ Atividade 2.3: Estruturas (3%)
└─ Atividade 2.4: UML (2%)

Fase 3 (Semanas 4-6): 15%
├─ Atividade 3.1: Distribuições (3%)
├─ Atividade 3.2: Fila (6%)
└─ Atividade 3.3: CadÚnico (6%)

Fase 4 (Semanas 7-8): 20%
├─ Atividade 4.1: Validação (5%)
├─ Atividade 4.2: EDA (5%)
├─ Atividade 4.3: Sensibilidade (5%)
└─ Atividade 4.4: Cenários (5%)
```

### Projeto Integrado (50%)

```
Atividades 5.1-5.2 (Especificação + Modelagem): 10%
├─ Clareza da descrição (5%)
└─ Qualidade da modelagem (5%)

Atividade 5.3 (Implementação): 20%
├─ Código funcional e robusto (12%)
├─ Testes e documentação (5%)
└─ Estrutura e design (3%)

Atividade 5.4 (Análise): 15%
├─ Validação (3%)
├─ Sensibilidade (4%)
├─ Cenários (4%)
└─ Interpretação e insights (4%)

Atividade 5.5 (Apresentação): 5%
├─ Clareza (2%)
├─ Completude (2%)
└─ Respostas a perguntas (1%)
```

### Pesos por Critério

- **Corretude técnica:** 40% (código funciona? lógica está correta?)
- **Clareza e documentação:** 30% (código comentado? relatório claro?)
- **Interpretação e insights:** 20% (entende resultados? vai além dos números?)
- **Originalidade:** 10% (sistema é interessante? análises customizadas?)

---

## 🔧 Adaptações Possíveis

### Para Turmas Menores (< 15 alunos)
- Mais discussão em classe (trace pseudocódigo, questione)
- Orientação individual nos projetos
- Roda de apresentações (todos apresentam)

### Para Turmas Maiores (> 30 alunos)
- Projetos em grupos de 3-4
- Use GitHub Classroom para gestão de código
- Crie sistema de plantão de dúvidas
- Use rubricas automatizadas se possível

### Para Turmas com Pouca Experiência em Programação
- Comece Semana 1 com "Python Crash Course" (30 min)
- Use templates de código mais estruturados
- Estenda Semana 4 para 1.5 semanas
- Foco em lógica antes de otimizações

### Para Turmas Avançadas
- Desafie com otimizações (paralelização, performance)
- Peça análises avançadas (regressão, ML)
- Considere framework SimPy (simulação mais avançada)
- Desafie projeto com dados ainda maiores

### Para Substituir CadÚnico
- Mantenha mesma estrutura, datasets diferentes
- Opções: ENEM, Saúde, Imigração, E-commerce
- Adapte distribuições e eventos específicos
- Mesma metodologia, contexto diferente

---

## 📞 FAQ do Professor

**P: Os alunos precisam de experiência prévia em programação?**
R: Recomenda-se Python básico. Se não tiverem, adicione "Python Crash Course" na Semana 1 (30 min).

**P: 60 horas é pouco? Tinha 80 antes...**
R: Sim, foi comprimido para 10 semanas. Mantém essência, remove redundâncias e materiais opcionais.

**P: Quanto tempo devo gastar em cada atividade?**
R: Siga `SEQUENCIA_PEDAGOGICA.md` — cada atividade tem duração definida.

**P: E se um aluno ficar para trás?**
R: Identifique em Checkpoints 1-2. Ofereça tutoria individual ou reduza escopo do projeto.

**P: Alunos podem fazer projeto em grupo?**
R: Sim, até 3 por grupo. Mas código deve ser rastreável (Git commits individuais).

**P: Posso omitir algumas fases?**
R: Não recomendado. Cada fase é pré-requisito para próxima. Máximo: reduzir algumas atividades opcionais.

**P: Como justificar 60 horas aos alunos?**
R: Mostre `INFOGRAFICO.md` — 10h aula, 24h lab, 26h casa. Distribuição clara.

---

## 🚀 Próximos Passos Imediatos

1. **Esta semana:** Revise `SEQUENCIA_PEDAGOGICA.md` e `INFOGRAFICO.md`
2. **Semana que vem:** Configure ambiente Python + dados + GitHub Classroom
3. **Antes da Semana 1:** Prepare exemplo de fila bancária (completo, funcionando)
4. **Semana 1:** Mostre `INFOGRAFICO.md` aos alunos, comece Atividade 1.1

---

## 📁 Estrutura Final de Arquivos

```
/disciplinas/modelagem-simulacao/

├── README.md (guia geral)

├── exercicios/
│   ├── README_PROFESSOR.md (VOCÊ ESTÁ AQUI)
│   │
│   ├── SEQUENCIA_PEDAGOGICA.md (guia 10 semanas)
│   │
│   ├── INFOGRAFICO.md (visualizações)
│   │
│   ├── atividades_analise_dados_cadunico.md (10 atividades)
│   │
│   ├── atividades_modelagem_conceitual_discreto.md (8 atividades)
│   │
│   └── [outros arquivos para referência]
│
├── notas/ (aulas 8 módulos — podem complementar)
│
├── projetos/ (referência de projetos passados)
│
└── dados/ (base CadÚnico — 12.8M pessoas, 4.8M famílias)
```

---

## ✨ Destaques desta Versão 60h

✅ **Compacto:** Cabe em 10 semanas (vs. 14 originais)
✅ **Integrado:** CadÚnico em todas as fases (fio vermelho)
✅ **Prático:** 83% de prática (40% lab + 43% casa)
✅ **Viável:** Distribuição equilibrada de carga semanal
✅ **Profissional:** Projeto final robusto (5-8 pág + 15min apresentação)
✅ **Flexível:** Fácil de adaptar a contextos diferentes

---

**Última atualização:** 2026-02-22
**Versão:** 2.0 (60 horas, 10 semanas)
**Status:** Pronto para implementação em sala de aula

