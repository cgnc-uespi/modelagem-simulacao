# Projetos de Modelagem e Simulação

Este diretório contém scripts e materiais relacionados à análise exploratória (EDA) do CadÚnico.

## Estrutura

- `base_amostra_cad_201812/` - Pasta com arquivos CSV de amostra do CadÚnico (familia e pessoa, 2018-12).
- `Dicionário_de_Dados_-_CadÚnico_-_Divulgação.xlsx` - Planilha com o dicionário de variáveis do CadÚnico.
- `eda_cadunico.py` - Script principal para realizar análise exploratória geral no conjunto de dados do CadÚnico.
- `eda_sexo.py` - Script focado na análise por sexo dos indivíduos.
- `eda_output/` - Diretório de saída onde gráficos e resultados gerados pelos scripts são salvos.
- `projetos_cadunico.md` - Documentação adicional ou notas de projetos (pode conter histórico, ideias ou anotações).

## Instruções de Uso

1. **Pré-requisitos**
   - Python 3.10+
   - Bibliotecas: pandas, matplotlib, seaborn, numpy (instaláveis via `requirements.txt` ou `pip install ...`).

2. **Configurar o ambiente**
   - Certifique-se de ter os CSVs de entrada em `base_amostra_cad_201812`.
   - O dicionário de dados pode ser útil para entender as variáveis.

3. **Executar análise geral**
   ```bash
   python eda_cadunico.py
   ```
   Isso produzirá gráficos e tabelas em `eda_output/`, incluindo distribuição de idade, renda, raça/cor, etc.

4. **Executar análise por sexo**
   ```bash
   python eda_sexo.py
   ```
   Este script gera visualizações específicas comparando dados entre sexos e salvando os resultados em `eda_output/`.

5. **Outras notas**
   - Limpe a pasta `eda_output/` se quiser regenerar os arquivos do zero.
   - Atualize os scripts conforme novas necessidades de análise.

---

Este README deve ser mantido atualizado conforme novas ferramentas ou dados sejam adicionados aos projetos.