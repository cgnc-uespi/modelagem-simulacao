# Slides – Ajuste de Dados e Testes de Aderência (CadÚnico)

## Slide 1 – Título

**Título:** Ajuste de Dados e Testes de Aderência  
**Subtítulo:** Distribuições de Tempos em Processos Ligados ao CadÚnico

Notas:
> “Aqui vamos usar dados de chegadas/atendimentos (quando disponíveis) para ajustar distribuições e testar aderência, conectando estatística com simulação.”

---

## Slide 2 – Objetivos

**Título:** Objetivos da Aula

Bullets:
- Trabalhar com dados de tempos de chegada e atendimento
- Ajustar distribuições de probabilidade
- Aplicar testes de aderência (visuais e formais)
- Integrar distribuições ajustadas ao simulador

Notas:
> “É a ponte entre estatística e simulação.”

---

## Slide 3 – Por que Ajustar Distribuições?

**Título:** Motivação

Bullets:
- Tempos de serviço e de chegada são variáveis aleatórias
- Simulação precisa de distribuições razoáveis
- Distribuições ‘chutadas’ podem distorcer resultados

Contexto:
- tempos de atendimento podem ter cauda longa
- chegadas variam por horário e período (campanhas, prazos)

Notas:
> “Quanto mais o modelo depende de tempos, mais importante ajustar bem as distribuições.”

---

## Slide 4 – Coleta de Dados de Tempo

**Título:** Coleta de Dados

Bullets:
- Registros necessários:
  - horário de chegada/registro
  - hora de início e fim de atendimento
  - tipo de atendimento
- Derivar:
  - tempos entre chegadas
  - tempos de atendimento

Notas:
> “Pode vir de sistemas de fila, logs, ou coleta manual se necessário.”

---

## Slide 5 – Exploração Inicial

**Título:** Exploração dos Dados

Bullets:
- Estatísticas descritivas:
  - média, mediana, desvio padrão
  - mínimos/máximos
- Visualizações:
  - histogramas
  - boxplots
  - gráficos de densidade

Notas:
> “Antes de falar em ‘distribuição teórica’, é preciso olhar para os dados.”

---

## Slide 6 – Escolha de Candidatas

**Título:** Escolha de Distribuições Candidatas

Bullets:
- Distribuições comuns:
  - exponencial, normal, lognormal, gama, Weibull
  - empíricas
- Critérios:
  - forma do histograma
  - conhecimento do processo (não-negatividade, cauda longa)

Notas:
> “Não há uma ‘única’ distribuição certa; escolhemos candidatas plausíveis.”

---

## Slide 7 – Ajuste de Parâmetros

**Título:** Ajuste de Parâmetros

Bullets:
- Métodos:
  - momentos
  - máxima verossimilhança (via software)
- Ferramentas:
  - Python (SciPy), R, softwares estatísticos

Notas:
> “Em prática, o software ajusta; nossa preocupação é interpretar se faz sentido.”

---

## Slide 8 – Testes Visuais

**Título:** Testes de Aderência – Visuais

Bullets:
- Histogramas + curva da distribuição ajustada
- QQ-plot
- Perguntas:
  - a curva ‘acompanha’ o histograma?
  - há grandes desvios nas caudas?

Notas:
> “Se o ajuste visual estiver muito ruim, provavelmente aquela distribuição não é adequada.”

---

## Slide 9 – Teste KS

**Título:** Teste de Aderência – Kolmogorov-Smirnov

Bullets:
- Compara CDF empírica vs teórica
- Usa maior desvio entre as duas curvas
- Saída:
  - estatística KS
  - p-valor

Interpretação simplificada:
- p-valor alto → não há evidência forte contra a distribuição
- p-valor baixo → má aderência

Notas:
> “O KS é mais natural para distribuições contínuas; é um bom primeiro teste formal.”

---

## Slide 10 – Teste Qui-quadrado

**Título:** Teste de Aderência – Qui-quadrado

Bullets:
- Divide dados em classes (bins)
- Compara frequências observadas vs esperadas
- Calcula estatística Qui-quadrado
- Obtém p-valor com graus de liberdade

Cuidados:
- contagem mínima por classe
- sensível aos intervalos escolhidos

Notas:
> “É um teste intuitivo quando pensamos em contagens em faixas de tempo.”

---

## Slide 11 – Escolha da Distribuição

**Título:** Escolha da Distribuição Final

Bullets:
- Combinar:
  - conhecimento do processo
  - ajuste de parâmetros
  - testes visuais
  - testes formais
- Se exponencial ‘passa’ razoavelmente, pode ser suficiente
- Se não, considerar lognormal ou empírica

Notas:
> “Nem sempre precisamos da distribuição ‘perfeita’; buscamos uma que seja adequada ao propósito.”

---

## Slide 12 – Integração com o Simulador

**Título:** Integração com o Simulador

Bullets:
- Atualizar funções do modelo:
  - `tempo_entre_chegadas()` com λ ajustado
  - `tempo_de_servico()` com distribuição ajustada
- Comparar resultados da simulação com:
  - estatísticas empíricas
  - versão anterior do modelo

Notas:
> “Isso melhora a aderência do simulador à realidade e fortalece a validação.”

---

## Slide 13 – Exercícios – Ajuste e Aderência

**Título:** Exercícios – Ajuste de Dados

Bullets:
- A partir de uma amostra de tempos de atendimento:
  - calcular estatísticas descritivas
  - ajustar pelo menos 2 distribuições (exponencial e lognormal)
  - aplicar um teste de aderência (KS ou Qui-quadrado)
- Escolher a distribuição ‘preferida’ e justificar
- Explicar como essa escolha impacta o simulador

Notas:
> “Aqui o aluno fecha o ciclo: dados → ajuste → teste → decisão de modelagem.”
