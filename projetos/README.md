# Projetos de Modelagem e Simulação

Este diretório reúne os projetos práticos desenvolvidos na disciplina de **Modelagem e Simulação de Eventos Discretos**.
Cada subpasta corresponde a um contexto/domínio de aplicação distinto.

---

## Estrutura

```
projetos/
├── Cadúnico/                              # Projetos com dados do Cadastro Único
│   ├── base_amostra_cad_201812/           # CSVs amostrais (família e pessoa, dez/2018) — não versionados
│   ├── eda_cadunico.ipynb                 # Análise exploratória geral do CadÚnico
│   ├── eda_sexo.ipynb                     # Análise exploratória por sexo
│   └── projetos_cadunico.md               # Propostas de projetos de simulação – CadÚnico
│
└── Supermercado/                          # Projeto de coleta e análise em supermercado
    ├── Coleta de dados do supermercado.csv  # Base de dados coletada em campo
    └── Coleta_de_dados_no_supermercado.ipynb
```

---

## Projetos

### Cadúnico

Análise exploratória e propostas de simulação aplicadas ao **Cadastro Único para Programas Sociais**.

- **Base de dados:** Microdados amostrais do CadÚnico (dados.gov.br – dez/2018).
- **Notebooks:**
  - `eda_cadunico.ipynb` – distribuição de idade, renda, raça/cor e outras variáveis do conjunto completo.
  - `eda_sexo.ipynb` – comparações e visualizações específicas por sexo.
- **Propostas de simulação** (`projetos_cadunico.md`): dimensionamento de guichês, reforço em horários de pico, fila única vs filas por serviço, impacto de campanhas, abandono de fila, atendimento multicanal.

### Supermercado

Coleta e análise de dados de atendimento em ambiente de supermercado, com foco na caracterização empírica das chegadas e dos tempos de serviço para alimentar modelos de simulação.

- **Base de dados:** `Coleta de dados do supermercado.csv` — dados coletados em campo (tempos entre chegadas e tempos de serviço).
- **Notebook:** `Coleta_de_dados_no_supermercado.ipynb` — análise e visualização dos dados coletados.

---

## Como executar

A forma recomendada é abrir os notebooks diretamente no **Google Colaboratory**, sem necessidade de instalar nada:

1. Acesse [colab.research.google.com](https://colab.research.google.com).
2. Vá em **Arquivo → Abrir notebook → GitHub**, cole a URL deste repositório e selecione o notebook desejado.
3. Caso o notebook leia um arquivo CSV local (ex.: projeto Supermercado), faça o upload do arquivo pela barra lateral do Colab (**ícone de pasta → Fazer upload**).
4. Execute as células em ordem com **Shift + Enter** ou **Executar tudo** no menu.

> Todos os pacotes utilizados (`pandas`, `matplotlib`, `seaborn`, `numpy`) já estão disponíveis no ambiente padrão do Colab.

---

> Este README deve ser mantido atualizado conforme novos projetos ou subpastas sejam adicionados.
