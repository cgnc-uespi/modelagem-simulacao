# Modelagem e Simulação de Eventos Discretos

## 1. O que é a disciplina?

Nesta disciplina você vai aprender a **representar sistemas reais** (como filas, serviços, redes) por meio de **modelos** e a usar **simulação de eventos discretos** para analisar o comportamento desses sistemas.

O foco é entender:
- como surgem filas e gargalos;
- como dimensionar recursos (atendentes, servidores, máquinas);
- como tomar decisões com base em dados e experimentos de simulação.

---

## 2. Estudo de caso: CadÚnico

Ao longo do curso, usaremos como exemplo principal **processos ligados ao Cadastro Único para Programas Sociais (CadÚnico)**, com base nos microdados amostrais oficiais.

Base de dados oficial:
- Microdados amostrais do CadÚnico – dados.gov.br
  <https://dados.gov.br/dados/conjuntos-dados/microdados-amostrais-do-cadastro-unico>
- Observatório do CadÚnico
  <https://paineis.mds.gov.br/public/extensions/observatorio-do-cadastro-unico/index.html>
- Data Explorer CadÚnico
  <https://aplicacoes.cidadania.gov.br/vis/data3/data-explorer.php>

Por quê?
- É um sistema real, central em políticas sociais brasileiras;
- Envolve filas, atendimento, recursos limitados e prazos de atualização;
- Decisões ali afetam diretamente a vida de milhões de famílias.

Vamos:
- modelar chegadas de famílias, filas e processos de atendimento/cadastro;
- simular o funcionamento de fluxos ligados ao CadÚnico em diferentes cenários;
- discutir como a simulação pode apoiar decisões de gestão e políticas públicas.

---

## 3. O que você vai aprender a fazer

Ao final da disciplina, você deve ser capaz de:

- Enxergar sistemas reais (como o CadÚnico) como **sistemas de filas** e eventos;
- Construir **modelos de simulação de eventos discretos** simples;
- Implementar simuladores básicos em código (ou usar ferramentas existentes);
- Coletar, tratar e ajustar **dados de tempos** (chegadas, atendimentos);
- Projetar **experimentos de simulação** (cenários, replicações, métricas);
- Analisar resultados para apoiar decisões (ex.: quantos guichês são suficientes?).

---

## 4. Como a disciplina está organizada

### Parte 1 – Fundamentos
- Conceitos de sistema, modelo e simulação;
- Simulação de eventos discretos (estado, eventos, relógio, lista de eventos);
- Filas: chegadas, atendimentos, disciplina de fila;
- Geração de números aleatórios e variáveis aleatórias.

### Parte 2 – Aplicando ao CadÚnico
- Modelo de fila para atendimento em CRAS/postos de cadastro;
- Simulação manual (no papel/planilha) e implementação computacional;
- Verificação e validação de modelos;
- Coleta e tratamento de microdados do CadÚnico;
- Ajuste de distribuições e testes de aderência.

### Parte 3 – Experimentos e Projetos
- Projeto de experimentos de simulação;
- Dimensionamento (atendentes, horários, capacidade);
- Análise de resultados e apresentação de recomendações;
- Projeto final aplicado ao CadÚnico.

---

## 5. Como você será avaliado

A forma exata de avaliação pode variar, mas em geral deve incluir:

- **Listas de exercícios**: reforçam o conteúdo de cada aula (modelagem, eventos, filas, etc.);
- **Trabalhos práticos**: simulação manual, implementação de modelos, análise de dados;
- **Projeto aplicado ao CadÚnico**: em grupo, modelando e simulando um problema realista (por exemplo, dimensionamento de atendentes em CRAS);
- **Provas ou avaliações escritas**: para consolidar os conceitos teóricos.

Detalhes (pesos, datas) serão apresentados pelo professor em sala/plataforma.

---

## 6. O que você precisa saber antes

É útil (mas não obrigatório) ter familiaridade básica com:
- programação (alguma linguagem de sua preferência);
- noções de probabilidade e estatística básica (média, variância, distribuição);
- estruturas de dados simples (filas, listas).

Se você não estiver confortável com algum desses tópicos, a disciplina também é uma boa oportunidade para reforçar essas bases, com apoio dos materiais e das atividades práticas.

---

## 7. Por que isso é importante?

Modelagem e simulação são ferramentas muito usadas em:
- engenharia de software (sistemas distribuídos, filas de requisições);
- pesquisa operacional (logística, produção, saúde);
- ciência de dados e analytics;
- planejamento de serviços públicos.

Ao aprender a simular um sistema como o CadÚnico, você desenvolve uma forma de pensar que se aplica a muitos outros contextos: enxergar o sistema, abstrair, modelar, experimentar e decidir.

---

## 8. Materiais de Referência

A pasta `ppt/` contém os slides das aulas em formato PowerPoint (`.pptx`). Use-os para:

- **Estudar** o conteúdo apresentado em sala de forma visual e resumida;
- **Revisar** antes de quizes e avaliações;
- **Acompanhar** as aulas com o material de referência em mãos.

Os arquivos cobrem todos os temas da disciplina: introdução, simulação manual, modelagem, tratamento de dados, ajuste de distribuições, verificação e validação, e dimensionamento de sistemas.

---

## 9. Como aproveitar melhor a disciplina

- Participe das discussões sobre o CadÚnico e outros exemplos reais;
- Faça os exercícios com seriedade: eles preparam você para o projeto;
- Use os slides em `ppt/` e as notas disponíveis como guia de estudo, não só na véspera de prova;
- Se interessar, pense na disciplina como ponto de partida para um **TCC** ou projeto de pesquisa em simulação aplicada a serviços públicos.

Se tiver dúvidas ou ideias de aplicação em outros sistemas (saúde, transporte, etc.), traga para a aula – a disciplina é um espaço ótimo para explorar esses temas.
