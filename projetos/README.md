# Projetos de Modelagem e Simulação

Este diretório reúne os projetos práticos desenvolvidos na disciplina de **Modelagem e Simulação de Eventos Discretos**.
Cada subpasta corresponde a um contexto/domínio de aplicação distinto.

---

## Estrutura

```
projetos/
├── Cadúnico/                         # Projetos com dados do Cadastro Único
│   ├── base_amostra_cad_201812/      # CSVs amostrais (família e pessoa, dez/2018)
│   ├── eda_cadunico.ipynb            # Análise exploratória geral do CadÚnico
│   ├── eda_sexo.ipynb                # Análise exploratória por sexo
│   └── projetos_cadunico.md          # Propostas de projetos de simulação – CadÚnico
│
└── Supermercado/                     # Projeto de coleta e análise em supermercado
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

**Pré-requisitos**

```bash
pip install pandas matplotlib seaborn numpy jupyter
```

### Supermercado

Coleta e análise de dados de atendimento em ambiente de supermercado, com foco na caracterização empírica das chegadas e dos tempos de serviço para alimentar modelos de simulação.

- **Notebook:** `Coleta_de_dados_no_supermercado.ipynb`

---

## Como executar

1. Clone o repositório e acesse a pasta do projeto desejado.
2. Instale as dependências (veja os pré-requisitos de cada projeto).
3. Abra o notebook com `jupyter notebook` ou `jupyter lab`.
4. Execute as células em ordem.

---

> Este README deve ser mantido atualizado conforme novos projetos ou subpastas sejam adicionados.
