# Aula 4 – Números Pseudoaleatórios e Variáveis Aleatórias em Simulação

_Disciplina: Modelagem e Simulação de Eventos Discretos_

_Estudo de caso central: **Cadastro Único para Programas Sociais (CadÚnico)**._

## 1. Por que precisamos de números aleatórios?

Nos modelos **estocásticos** do CadÚnico, tempos entre chegadas de famílias, tempos de atendimento em guichês, tempos até abandono da fila, entre outros, são variáveis aleatórias.

Para simular esses modelos no computador, precisamos **gerar valores aleatórios** que obedeçam a certas distribuições (exponencial, normal, uniforme, empírica, etc.).

O computador, porém, é uma máquina determinística. Como então geramos "aleatoriedade"?

---

## 2. Números pseudoaleatórios

Os computadores usam **geradores pseudoaleatórios**:

- Na prática, são **algoritmos determinísticos** que produzem sequências que "parecem" aleatórias;
- Dado um valor inicial chamado **seed** (semente), o gerador produz sempre a mesma sequência (o que é bom para **reprodutibilidade**).

### Propriedades desejáveis

Um bom gerador deve apresentar:

- **Período longo:** a sequência demora muito para se repetir;
- **Uniformidade:** para geradores de `U ~ Uniforme(0,1)`, os valores devem se distribuir aproximadamente de forma uniforme no intervalo;
- **Independência aparente:** valores consecutivos não devem apresentar padrões óbvios.

### Importância da seed

- Escolher uma seed explícita permite **repetir** experimentos (útil para depuração e comparação de cenários);
- Mudando a seed, criamos **replicações independentes** do experimento de simulação.

No CadÚnico, isso é útil para:

- comparar cenários diferentes (número de guichês, organização das filas) sob diferentes "sorteios" de chegadas e atendimentos;
- garantir que, ao mudar apenas um parâmetro, as diferenças de resultado sejam devidas a esse parâmetro, e não à sequência aleatória.

---

## 3. Variáveis Uniformes (0,1)

A maioria das bibliotecas gera, inicialmente, números com distribuição **Uniforme(0,1)**.

- Isso significa que o valor gerado está entre 0 e 1 e qualquer subintervalo tem probabilidade proporcional ao seu tamanho.
- Exemplo: a probabilidade de cair entre 0,2 e 0,3 é aproximadamente 0,1 (10%).

A partir desses números uniformes, podemos gerar **variáveis com outras distribuições**, como as usadas em modelos de chegada e serviço do CadÚnico.

---

## 4. Transformando Uniformes em outras distribuições

### 4.1. Método da inversa (conceito)

Se conhecemos a função de distribuição acumulada (CDF) `F(x)` de uma variável aleatória X, e `U ~ Uniforme(0,1)`, então:

> X = F⁻¹(U)

segue a distribuição desejada.

Na prática:

- Geramos `U` uniforme entre 0 e 1;
- Calculamos `X = F⁻¹(U)`;
- O valor `X` terá a distribuição desejada.

Exemplo (exponencial com taxa λ):

- Se `U ~ U(0,1)`, então um valor exponencial pode ser gerado por:  
  `X = - (1/λ) * ln(1 - U)`  
  (ou simplesmente `- (1/λ) * ln(U)`, já que `1 - U` também é uniforme).

### 4.2. Outras técnicas

Para distribuições mais complexas (por exemplo, distribuições empíricas ajustadas a dados de tempo de atendimento no CadÚnico):

- Métodos de aceitação-rejeição;
- Métodos específicos (Box-Muller para normal, etc.);
- Uso de bibliotecas prontas que já encapsulam esses métodos.

Nesta disciplina, o foco principal é **entender o conceito**, não implementar todos os métodos na mão.

---

## 5. Uso prático em simulação (CadÚnico)

Na implementação de um modelo do CadÚnico, normalmente teremos funções do tipo:

- `tempo_entre_chegadas_cadunico(hora_do_dia)`: retorna um valor aleatório que representa o intervalo até a próxima chegada, possivelmente com taxa dependente do horário;
- `tempo_de_servico_cadunico(tipo_servico)`: retorna um valor aleatório para a duração do atendimento de uma família de determinado tipo;
- `tempo_ate_desistencia()`: se modelarmos abandono, retorna um tempo aleatório até a família desistir.

Internamente, essas funções:

1. Chamam um gerador `U ~ Uniforme(0,1)`;
2. Transformam esse `U` para a distribuição desejada (exponencial, empírica, etc.).

Exemplo em pseudocódigo, para tempos entre chegadas exponenciais em um certo intervalo de tempo do CadÚnico:

```pseudo
funcao tempo_entre_chegadas_cadunico(taxa_lambda):
    U <- uniforme_0_1()
    X <- - (1 / taxa_lambda) * ln(U)
    retornar X
```

---

## 6. Cuidados práticos

### 6.1. Reprodutibilidade

- Sempre que possível, fixe a seed quando estiver **depurando** o modelo do CadÚnico;
- Para rodar diferentes **replicações** de um mesmo experimento (mesmo cenário de guichês, mesma política), use seeds diferentes e registre-as.

### 6.2. Dependência entre sequências

- Evite usar o mesmo gerador/semente de forma ingênua em cenários distintos onde independência é importante;
- Em casos mais avançados, usar streams/substreams de geradores é uma prática comum (além do escopo básico).

### 6.3. Validação empírica

- É possível (e desejável) testar se os valores gerados parecem seguir a distribuição que se pretende usar para o CadÚnico:
  - histogramas de tempos entre chegadas;
  - histogramas de tempos de atendimento;
  - comparação de médias/variâncias aproximadas com dados coletados no CadÚnico.

---

## 7. Atividade proposta (Aula 4)

1. Usando uma linguagem à sua escolha (ou planilha), gere uma sequência de, por exemplo, 1000 valores Uniforme(0,1) e:
   - calcule média e variância aproximadas;
   - observe a distribuição (por histograma ou contagem por faixas).
2. Implemente (ou descreva em pseudocódigo) uma função `tempo_entre_chegadas_cadunico(lambda)` que:
   - gere `U ~ U(0,1)`;
   - retorne `X = - (1/λ) * ln(U)`.
3. Discuta como você usaria essa função no contexto do CadÚnico (por exemplo, para simular chegadas em um período de uma hora), e por que é importante poder **repetir** a sequência (mesma seed) ao comparar cenários.
