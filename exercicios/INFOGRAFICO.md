# Infográfico: Sequência Pedagógica 60h
## Modelagem e Simulação de Eventos Discretos

**Duração:** 10 semanas | **Total:** 60 horas (10h aula + 24h lab + 26h casa)

---

## 📊 DIAGRAMA DE PROGRESSÃO GERAL

```
┌─────────────────────────────────────────────────────────────────────┐
│           MODELAGEM E SIMULAÇÃO (10 SEMANAS, 60 HORAS)              │
└─────────────────────────────────────────────────────────────────────┘

    FASE 1                FASE 2                FASE 3               FASE 4                FASE 5
  FUNDAMENTOS          MODELAGEM            IMPLEMENTAÇÃO           ANÁLISE              PROJETO
  (Semanas 1-2)        (Semana 3)           (Semanas 4-6)         (Semanas 7-8)       (Semanas 9-10)

    ┌─────┐               ┌─────┐               ┌─────┐               ┌─────┐              ┌──────┐
    │  1  │               │  2  │               │  3  │               │  4  │              │  5   │
    │ 📚  │               │ 🔧  │               │ 💻  │               │ 📈  │              │ 🎓   │
    │ 7h  │               │ 7h  │               │ 14h │               │ 8h  │              │ 16h  │
    └──┬──┘               └──┬──┘               └──┬──┘               └──┬──┘              └──┬───┘
       │                     │                     │                     │                    │
       │◄──── PRÉ-REQ. ────►│◄──── PRÉ-REQ. ────►│◄──── PRÉ-REQ. ────►│◄──── PRÉ-REQ. ────►│
       │                     │                     │                     │                    │
    ✅ CONCEITOS         ✅ PSEUDOCÓDIGO        ✅ CÓDIGO             ✅ VALIDAÇÃO         ✅ SÍNTESE
       ENTENDIDOS           CORRETO               FUNCIONAL            E INSIGHTS          FINAL


RESULTADO ESPERADO:
┌────────────────────────────────────────────────────────────────────┐
│                   SIMULADOR COMPLETO DE SISTEMAS                    │
│                                                                    │
│  • Modelo conceitual validado                                     │
│  • Código Python funcional (500-600 linhas)                       │
│  • Experimentos com 3+ cenários                                   │
│  • Relatório técnico (5-8 páginas)                                │
│  • Recomendações baseadas em dados                                │
└────────────────────────────────────────────────────────────────────┘
```

---

## 📅 TIMELINE SEMANAL COMPACTA

```
SEMANA  │ FASE │ ATIVIDADES                              │ HORAS │ FORMATO
────────┼─────┼─────────────────────────────────────────┼───────┼──────────
  1-2   │  1  │ 1.1-1.3: Conceitos + EDA + Modelagem    │ 7h    │ Aula+Lab
        │     │ (Componentes, dados reais, eventos)     │       │
────────┼─────┼─────────────────────────────────────────┼───────┼──────────
   3    │  2  │ 2.1-2.4: Pseudocódigo + Estruturas + UML│ 7h    │ Aula+Lab
        │     │ (Genérico, CadÚnico, heap, diagramas)   │       │
────────┼─────┼─────────────────────────────────────────┼───────┼──────────
   4    │  3  │ 3.1-3.2: Distribuições + Fila bancária  │ 8h    │ Lab+Casa
        │     │ (Ajuste, mini-projeto)                  │       │
────────┼─────┼─────────────────────────────────────────┼───────┼──────────
  5-6   │  3  │ 3.3: Simulador CadÚnico completo        │ 6h    │ Lab+Casa
        │     │ (1000 famílias × 5 anos)                │       │
────────┼─────┼─────────────────────────────────────────┼───────┼──────────
   7    │  4  │ 4.1-4.3: Validação, EDA, Sensibilidade  │ 6h    │ Lab+Casa
        │     │ (Verificar, análise, parâmetros)        │       │
────────┼─────┼─────────────────────────────────────────┼───────┼──────────
   8    │  4  │ 4.4: Comparação de cenários             │ 2h    │ Lab+Casa
        │     │ (3 políticas, recomendações)            │       │
────────┼─────┼─────────────────────────────────────────┼───────┼──────────
   9    │  5  │ 5.1-5.2: Especificação + Modelagem      │ 6h    │ Casa
        │     │ (Sistema novo, design)                  │       │
────────┼─────┼─────────────────────────────────────────┼───────┼──────────
   10   │  5  │ 5.3-5.5: Código + Análise + Apresentação│ 10h   │ Lab+Casa
        │     │ (Implementação, resultados, 15min talk) │       │

TOTAL: ~60 horas (10h aula + 24h lab + 26h casa)
```

---

## 🧵 FIO VERMELHO: CadÚnico em Todas as Fases

```
┌─────────────────────────────────────────────────────────────────────────┐
│                                                                         │
│                     CADUNICO: EXEMPLO UNIFICADOR                        │
│                                                                         │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │ FASE 1: DADOS (Semanas 1-2)                                     │   │
│  │ • 12.8M pessoas reais, 4.8M famílias                           │   │
│  │ • Distribuições: idade, renda, escolaridade                    │   │
│  │ • Padrão: desigualdade (Gini 0.5+)                             │   │
│  └──────────────────────────────┬────────────────────────────────┘   │
│                                  │                                     │
│  ┌──────────────────────────────v────────────────────────────────┐   │
│  │ FASE 2: MODELO (Semana 3)                                       │   │
│  │ • Entidade: Família                                            │   │
│  │ • Eventos: Nascimento, Morte, Renda, Bolsa Família             │   │
│  │ • Estado: tamanho, renda_média, acesso_água, etc.              │   │
│  └──────────────────────────────┬────────────────────────────────┘   │
│                                  │                                     │
│  ┌──────────────────────────────v────────────────────────────────┐   │
│  │ FASE 3: CÓDIGO (Semanas 4-6)                                    │   │
│  │ • 1000 famílias × 5 anos                                       │   │
│  │ • Distribuições ajustadas aos dados reais                      │   │
│  │ • Coleta: renda_média, Gini, % com Bolsa, tamanho_médio       │   │
│  └──────────────────────────────┬────────────────────────────────┘   │
│                                  │                                     │
│  ┌──────────────────────────────v────────────────────────────────┐   │
│  │ FASE 4: ANÁLISE (Semanas 7-8)                                   │   │
│  │ • Simulado vs. Real: renda final ≈ dados?                      │   │
│  │ • Sensibilidade: qual parâmetro mais afeta Gini?               │   │
│  │ • Cenários: Emprego +20% vs. Renda Básica vs. Baseline        │   │
│  └──────────────────────────────┬────────────────────────────────┘   │
│                                  │                                     │
│  ┌──────────────────────────────v────────────────────────────────┐   │
│  │ FASE 5: PROJETO (Semanas 9-10)                                  │   │
│  │ • Sistema diferente (Healthcare, Logística, ou Social)          │   │
│  │ • Mesma metodologia: dados → modelo → código → análise         │   │
│  │ • Recomendação prática: "Use 3 médicos em vez de 2"            │   │
│  └─────────────────────────────────────────────────────────────┘   │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘

       DADO REAL → MODELO → CÓDIGO → VALIDAÇÃO → AÇÃO
             (Tudo aplicado ao mesmo caso)
```

---

## 📊 DISTRIBUIÇÃO DE HORAS

```
AULA TEÓRICA
──────────
  10.5h (17%)

  ├─ Semana 1-2: 2.5h (conceitos)
  ├─ Semana 3: 2h (pseudocódigo)
  └─ Outras: 6h (integrado nas atividades)


LABORATÓRIO
──────────
  24h (40%)

  ├─ Semana 1-2: 3h (EDA CadÚnico)
  ├─ Semana 3: 4h (pseudocódigo + heap)
  ├─ Semana 4: 3h (distribuições + mini-fila)
  ├─ Semanas 5-6: 3h (CadÚnico)
  ├─ Semana 7: 5h (validação, EDA, sensibilidade)
  ├─ Semana 8: 2h (cenários)
  └─ Semana 10: 3h (projeto)


CASA (AUTÔNOMO)
────────────────
  26h (43%)

  ├─ Semana 1-2: 3.5h (exercícios + leitura)
  ├─ Semana 3: 2h (pseudocódigo)
  ├─ Semana 4: 2h (mini-projeto casa)
  ├─ Semanas 5-6: 3h (simulador)
  ├─ Semana 7: 2h (análise)
  ├─ Semana 8: 2h (relatório)
  ├─ Semana 9: 6h (especificação + modelagem)
  └─ Semana 10: 7h (implementação + análise)
```

---

## 🎯 MAPA DE CONCEITOS POR FASE

```
FASE 1: FUNDAMENTOS (7h)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  • Sistema vs. Modelo vs. Simulação
  • Estado, Entidades, Eventos
  • Variáveis entrada/saída
  • Diagramas de estado
  • Dados reais e padrões

FASE 2: MODELAGEM (7h)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  • Próximo evento (next-event time advance)
  • Lista de eventos futuros (FEL)
  • Processamento de eventos
  • Heap (estrutura eficiente)
  • Diagramas UML

FASE 3: IMPLEMENTAÇÃO (14h)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  • Geração de números aleatórios
  • Transformação em distribuições
  • Testes de aderência
  • Coleta de estatísticas
  • Código robusto em Python

FASE 4: ANÁLISE (8h)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  • Verificação (código correto?)
  • Validação (modelo é real?)
  • Sensibilidade (qual parâmetro?)
  • Comparação de cenários
  • Interpretação de resultados

FASE 5: SÍNTESE (16h)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  • Integração de aprendizagens
  • Modelagem de novo sistema
  • Implementação completa
  • Comunicação profissional
  • Recomendações baseadas em dados
```

---

## 📈 PROGRESSÃO DE COMPLEXIDADE

```
COMPLEXIDADE
    │
  5 │                                             ■ FASE 5 (Projeto)
    │                                          ■
  4 │                                      ■   ■
    │                                  ■       FASE 4 (Análise)
  3 │                            ■  ■
    │                        ■       FASE 3 (Código)
  2 │                    ■   ■
    │                ■       FASE 2 (Modelagem)
  1 │            ■
    │        ■   FASE 1 (Fundamentos)
  0 │
    │
    └──────────────────────────────────────────────→ SEMANA
      1  2  3  4  5  6  7  8  9  10

OBSERVAÇÃO: Crescimento gradual, pico na semana 4-5 (código),
reduz para análise, volta pico na semana 10 (projeto).
```

---

## 🎓 CHECKPOINTS DE QUALIDADE

```
FIM FASE 1: "Entendo Conceitos" (Semana 2)
├─ [ ] Diagrama de transição correto
├─ [ ] Identifiquei estado × eventos
└─ [ ] Sei por que simulação é necessária

FIM FASE 2: "Consigo Desenhar" (Semana 3)
├─ [ ] Pseudocódigo é legível
├─ [ ] UML é preciso
└─ [ ] Entendo avanço por próximo evento

FIM FASE 3: "Consigo Programar" (Semana 6)
├─ [ ] 2 simuladores funcionais (fila + CadÚnico)
├─ [ ] Testes passam
└─ [ ] Resultados reproduzíveis

FIM FASE 4: "Consigo Interpretar" (Semana 8)
├─ [ ] Simulado vs. Real: validado
├─ [ ] Sensibilidade: ranking claro
└─ [ ] Cenários: recomendação fundamentada

FIM FASE 5: "Sou Especialista" (Semana 10)
├─ [ ] Sistema original modelado corretamente
├─ [ ] Código robusto e documentado
├─ [ ] Relatório profissional (5-8 páginas)
└─ [ ] Respondo perguntas técnicas com segurança
```

---

## 💾 ESTRUTURA DE ARQUIVOS

```
/disciplinas/modelagem-simulacao/
│
├── README.md (guia geral da disciplina)
│
├── exercicios/
│   ├── README.md (guia do professor — 60h)
│   │
│   ├── SEQUENCIA_PEDAGOGICA.md (este é o guia!)
│   │
│   ├── atividades_analise_dados_cadunico.md
│   │   └─ 10 atividades com dados reais
│   │
│   ├── atividades_modelagem_conceitual_discreto.md
│   │   └─ 8 atividades de pseudocódigo
│   │
│   ├── INFOGRAFICO.md (visualizações — este arquivo)
│   │
│   ├── listas_exercicios_cadunico.md (extra)
│   │
│   └── [arquivos antigos mantidos para referência]
│
├── notas/ (aulas — 8 módulos)
│   ├── aula01_introducao_modelagem_simulacao.md
│   ├── aula02_conceitos_simulacao_eventos_discretos.md
│   ├── ... (6 mais)
│   └── slides_*_cadunico.md (slides prontos)
│
├── projetos/
│   └── projetos_cadunico.md
│
└── dados/
    └── base_amostra_cad_201812/
        ├── base_amostra_pessoa_201812.csv
        └── base_amostra_familia_201812.csv
```

---

## 🚀 COMO COMEÇAR

**PROFESSOR:**
1. Leia `/exercicios/README.md` (orientações gerais)
2. Leia `/exercicios/SEQUENCIA_PEDAGOGICA.md` (este plano)
3. Prepare Semana 1 usando `atividades_modelagem_conceitual_discreto.md` (Atividade 1)
4. Configure ambiente Python + dados CadÚnico
5. Inicie aula com alunos na Semana 1

**ALUNO:**
1. Leia `/exercicios/README_ALUNO.md` (se existir)
2. Acompanhe cronograma de Semana 1
3. Estude Atividade 1.1 (Componentes)
4. Participe de laboratório (Atividade 1.2)
5. Faça exercício de casa (Atividade 1.3)

---

## ✨ DESTAQUES DA ESTRUTURA 60h

✅ **Compacto:** 10 semanas (vs. 14 originais)
✅ **Focado:** Mantém essência, remove redundâncias
✅ **Prático:** 40% laboratório + 43% casa (83% prático)
✅ **Integrado:** CadÚnico em todas as fases
✅ **Viável:** Distribuição equilibrada de carga
✅ **Profissional:** Relatório final 5-8 páginas + apresentação 15min

---

**Última atualização:** 2026-02-22
**Versão:** 2.0 (60 horas)
**Status:** Pronto para implementação em 10 semanas

