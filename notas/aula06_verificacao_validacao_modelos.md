# Aula 6 – Verificação e Validação de Modelos de Simulação

_Disciplina: Modelagem e Simulação de Eventos Discretos_

_Estudo de caso central: **Cadastro Único para Programas Sociais (CadÚnico)**._

## 1. Por que verificação e validação são importantes?

Ao construir um modelo de simulação do CadÚnico, temos duas grandes perguntas:

1. **Verificação:** o modelo foi implementado corretamente?  
   ("O programa está certo?")

2. **Validação:** o modelo representa adequadamente o CadÚnico real para o objetivo de estudo?  
   ("Estamos modelando a coisa certa?")

Um modelo pode estar **perfeitamente implementado**, mas ainda assim ser **inadequado** para tomar decisões sobre o sistema real.

---

## 2. Verificação (Verification)

Verificação diz respeito a **conferir se o modelo computacional está correto** em relação à especificação do modelo conceitual.

### 2.1. Técnicas de verificação

Aplicadas ao CadÚnico:

- **Revisão de código e de lógica:**
  - ler o pseudocódigo e o código que implementa o modelo;
  - checar se, por exemplo, o tratamento de `CHEGADA_CIDADAO` e `FIM_ATENDIMENTO` está de acordo com a lógica planejada.

- **Testes unitários em componentes do modelo:**
  - testar funções de geração de tempos (por exemplo, se `tempo_entre_chegadas_cadunico()` produz valores razoáveis);
  - testar rotinas de tratamento de eventos em cenários controlados (por exemplo, cenário com uma única chegada e um único atendimento).

- **Testes de consistência e depuração:**
  - verificar se variáveis de estado assumem valores válidos (por exemplo, nunca ter número negativo de famílias no sistema);
  - usar saídas de depuração (logs) em pequenos experimentos para ver a evolução da fila e dos guichês.

- **Cenários simples de teste:**
  - rodar o modelo em condições "extremas" ou simplificadas, onde sabemos aproximadamente o resultado esperado; por exemplo:
    - chegadas muito raras e atendimento rápido → pouca fila, baixa utilização;
    - muitas chegadas e atendimento lento → fila longa, alta utilização.

---

## 3. Validação (Validation)

Validação trata de **comparar o modelo com o sistema real** e com o objetivo da análise.

### 3.1. O que é um modelo "válido"?

Um modelo do CadÚnico é considerado válido quando:

- reproduz, com precisão suficiente, o comportamento da central **para as perguntas que queremos responder** (por exemplo, dimensionar número de atendentes para manter tempo de espera abaixo de X minutos).

Isso não significa que o modelo seja perfeito em todos os detalhes, mas sim **adequado ao propósito**.

### 3.2. Técnicas de validação

- **Comparação com dados históricos:**
  - comparar métricas do modelo (por exemplo, tempo médio de espera, número de atendimentos por dia) com dados medidos no CadÚnico;
  - ajustar parâmetros do modelo (taxas de chegada, distribuições de atendimento) para aproximar os resultados.

- **Revisão por especialistas:**
  - apresentar o modelo conceitual (diagramas de filas, tipos de atendimento, prioridades) para gestores do CRAS e agentes sociais;
  - verificar se as hipóteses (por exemplo, sobre horários de pico, tempos de atendimento) são razoáveis.

- **Testes de plausibilidade:**
  - verificar se o modelo responde de forma "sensata" a mudanças de parâmetros;
  - por exemplo, no modelo do CadÚnico:
    - aumentar a taxa de chegada deve aumentar o tempo médio de espera;
    - adicionar guichês em horários de pico deve reduzir o tempo de espera.

- **Análise de sensibilidade:**
  - variar alguns parâmetros (por exemplo, tempos médios de atendimento, taxa de chegada em horários de pico) para ver quanto os resultados mudam;
  - ajuda a entender se pequenas incertezas nos dados vão comprometer as conclusões.

---

## 4. Erros comuns e armadilhas

- **Modelo complicado demais, sem dados suficientes:**
  - por exemplo, tentar modelar muitos tipos de serviço no CadÚnico com detalhes minuciosos, sem dados para calibrar/validar;
  - às vezes é melhor um modelo mais simples e bem calibrado.

- **Confiar cegamente em resultados de simulação:**
  - esquecer que resultados são **estimativas** com incerteza;
  - é importante sempre contextualizar: intervalos de confiança, número de replicações, hipóteses do modelo.

- **Ignorar o objetivo original:**
  - começar querendo só estimar tempo de espera no CadÚnico e acabar construindo um modelo enorme que foge da pergunta inicial.

---

## 5. Exemplo ilustrativo: modelo do CadÚnico

Suponha que o objetivo é avaliar o **tempo de espera médio** no CadÚnico para diferentes números de guichês.

### Verificação

- Conferir se:
  - a fila (ou filas) de famílias é atualizada corretamente;
  - eventos de chegada e término de atendimento estão sendo tratados conforme a lógica;
  - não há contagens negativas de famílias;
  - tempos de atendimento no CadÚnico são gerados conforme a distribuição especificada.

### Validação

- Comparar o tempo médio de espera obtido na simulação com dados medidos no CadÚnico (por exemplo, em alguns dias amostrados);
- Discutir com gestores e agentes sociais do CRAS se as hipóteses de chegada (picos, horários) e de atendimento (distribuições de tempo) fazem sentido;
- Verificar se o modelo reage razoavelmente a mudanças de carga (por exemplo, simulando aumento artificial na taxa de chegadas em campanhas de cadastramento ou em meses de recadastramento obrigatório).

---

## 6. Relação com o ciclo de modelagem

A construção de um modelo de simulação do CadÚnico não é linear; envolve **iterar** entre:

1. Entender o sistema e definir objetivos (por exemplo, reduzir tempo de espera);
2. Construir modelo conceitual (desenhar filas, eventos, recursos);
3. Implementar o modelo (codificação);
4. Verificar o modelo (verificar se o código implementa corretamente a lógica);
5. Validar o modelo com dados reais e especialistas do CadÚnico;
6. Ajustar o modelo conforme necessário.

Verificação e validação aparecem em várias etapas desse ciclo.

---

## 7. Atividade proposta (Aula 6)

1. Considere o modelo do CadÚnico que você vem desenvolvendo nas aulas anteriores.
2. Escreva, em 1–2 parágrafos, como você faria a **verificação** desse modelo:
   - que testes específicos faria para checar a implementação? (pense em invariantes, cenários simples, logs).
3. Escreva, em 1–2 parágrafos, como você faria a **validação**:
   - que dados reais do CadÚnico precisaria? (por exemplo, tempo médio de espera registrado, número de atendimentos por hora);
   - com quem conversaria (gestores, atendentes, setor de TI);
   - que comportamentos esperaria observar ao variar alguns parâmetros (por exemplo, taxa de chegada em dias de pico)?
4. Discuta como equilibrar **complexidade do modelo** e **disponibilidade de dados** no contexto do CadÚnico.
