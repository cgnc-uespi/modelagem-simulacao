# Aula 8 – Aplicações e Projetos em Modelagem e Simulação de Eventos Discretos

_Disciplina: Modelagem e Simulação de Eventos Discretos_

_Foco principal de aplicação: **Cadastro Único para Programas Sociais (CadÚnico)**; outros domínios podem ser usados como complementares._

## 1. Objetivo da aula

Conectar os conceitos aprendidos ao longo da disciplina com **aplicações concretas**, em especial o CadÚnico, e orientar a construção de um **projeto de simulação**.

---

## 2. Exemplos de aplicações (com ênfase no CadÚnico)

### 2.1. Cadastro Único para Programas Sociais (CadÚnico)

- Famílias chegando para diversos tipos de serviços (cadastramento, atualização cadastral, consultas, informações gerais);
- Múltiplos guichês de atendimento;
- Possíveis filas distintas (senhas por tipo de serviço (cadastramento, atualização), preferenciais (gestantes, idosos, famílias com crianças));
- Horários de pico, dias mais carregados (campanhas de cadastramento, recadastramento obrigatório);
- Regras de prioridade (idosos, gestantes, preferencial).

Perguntas típicas:

- Qual o tempo médio de espera atual no CadÚnico?
- Quantos guichês são necessários para cumprir uma meta de tempo máximo de espera?
- Qual o impacto de reforçar o atendimento apenas em horários de pico?
- Como diferentes políticas de fila (fila única vs filas por serviço) afetam o desempenho?

### 2.2. Outros domínios (para comparação ou projetos alternativos)

- Manufatura e logística (linhas de produção, centros de distribuição);
- Saúde (pronto-socorros, UTIs);
- Redes de computadores e sistemas distribuídos (filas em microserviços);
- Sistemas de serviços em geral (call centers, bancos, supermercados).

---

## 3. Estrutura de um projeto de simulação (CadÚnico)

Um projeto típico focado no CadÚnico pode ser estruturado em etapas:

1. **Definição do problema e objetivos**
   - Que aspectos do CadÚnico serão estudados? (por exemplo, fila de atendimento geral, fila de cadastramento, fila de atualização cadastral)
   - Quais perguntas queremos responder? (tempo de espera, dimensionamento de guichês, impacto de mudanças de política)

2. **Coleta e análise de dados**
   - Medir ou estimar:
     - taxas de chegada de famílias por horário e tipo de serviço (microdados CadÚnico — dados.gov.br);
     - tempos de atendimento por tipo de serviço;
     - horários de pico;
     - distribuição de tipos de atendimento (cadastramento, atualização cadastral, outros).

3. **Modelo conceitual**
   - Diagrama do sistema do CadÚnico (entidades, filas, guichês, eventos);
   - Definição de:
     - variáveis de estado (número de famílias em cada fila, estado de guichês);
     - eventos (chegada, início de atendimento, fim de atendimento, desistência);
     - lógica de funcionamento (regras de fila, prioridades, horários de operação).

4. **Modelo computacional (implementação)**
   - Escolha de linguagem/ferramenta (SimPy, Arena, AnyLogic, linguagem própria, etc.);
   - Implementação do simulador do CadÚnico conforme o modelo conceitual.

5. **Verificação e validação**
   - Verificar se o modelo computacional está correto (Aula 6);
   - Validar se o modelo representa bem o CadÚnico real (dentro dos objetivos), comparando com dados e discutindo com especialistas.

6. **Projeto de experimentos**
   - Definir cenários de interesse (Aula 7):
     - diferentes números de guichês;
     - diferentes escalas de atendentes por horário;
     - diferentes políticas de fila/prioridade.
   - Definir número de replicações, tratamento de warm-up, métricas.

7. **Análise de resultados e conclusões**
   - Comparar cenários;
   - Apresentar recomendações quantitativas para a gestão do CadÚnico.

---

## 4. Sugestão de temas de projeto (CadÚnico)

Algumas variações de tema, todas centradas no CadÚnico:

1. **Dimensionamento de guichês em dias típicos**
   - Objetivo: determinar o número de guichês necessário para manter o tempo médio de espera abaixo de um alvo em um dia típico.

2. **Impacto de reforço em horários de pico**
   - Objetivo: avaliar como a adição de guichês em períodos de pico (por exemplo, início da manhã e após o almoço) afeta o tempo de espera médio e máximo.

3. **Filas por tipo de serviço vs fila única**
   - Objetivo: comparar desempenho entre um CRAS com fila única e outro com filas específicas por tipo de serviço (cadastramento, atualização cadastral, consultas etc.).

4. **Efeito de campanhas de cadastramento**
   - Objetivo: analisar o impacto de um aumento temporário no fluxo de famílias (campanhas de cadastramento, mutirões) sobre as filas e dimensionamento de recursos.

5. **Abandono de fila (desistência)**
   - Objetivo: estudar a taxa de abandono no CadÚnico e como mudanças no número de guichês ou na política de atendimento podem reduzi-la.

---

## 5. Orientações para o projeto final

Sugestão de estrutura de entrega (focada no CadÚnico):

1. **Relatório escrito (4–8 páginas)**
   - Introdução:
     - breve descrição do CadÚnico e do problema;
     - objetivos do estudo (o que se deseja responder/otimizar).
   - Modelo conceitual:
     - diagramas de filas e guichês;
     - hipóteses de chegadas e atendimentos;
     - política de atendimento e prioridades.
   - Modelo computacional:
     - ferramenta/linguagem utilizada;
     - principais componentes (eventos, estruturas de dados).
   - Verificação e validação:
     - como foram realizados;
     - comparação com dados reais (quando disponíveis).
   - Projeto de experimentos:
     - cenários, replicações, métricas, tratamento de warm-up.
   - Resultados:
     - tabelas, gráficos, intervalos de confiança (se possível);
     - discussão sobre custos vs benefícios para o CadÚnico.
   - Conclusões e recomendações:
     - síntese das melhores configurações;
     - limitações do modelo;
     - sugestões para trabalhos futuros.

2. **Apresentação oral (curta)**
   - Resumo do problema, abordagem, principais resultados e recomendações.

3. **Código do modelo**
   - Scripts, modelos de ferramenta, arquivos de configuração necessário para reproduzir os resultados.

---

## 6. Atividade proposta (Aula 8)

1. Em grupos ou individualmente, escolha um tema de projeto **dentro do CadÚnico** (ou proponha variação, a ser aprovada pelo professor).
2. Produza um esboço inicial com:
   - descrição do sistema (foco do CadÚnico que será modelado);
   - objetivos do estudo (que métricas e decisões a simulação deve apoiar);
   - ideias preliminares de modelo conceitual (entidades, filas, guichês, eventos);
   - dados que serão necessários (taxas de chegada, tempos de atendimento, etc. – reais ou estimados);
   - possíveis cenários a serem comparados.
3. Discuta com o professor/orientador para refinar o escopo, garantindo que o projeto seja **viável no tempo disponível** e útil como estudo de caso aplicável à realidade dos gestores do CadÚnico.
