# **Relatório do Trabalho 1**

## Índice

1. [Introdução](#introducao)
2. [Modelagem](#modelagem)
    1. [Modelagem de Calorias](#calorias)
    2. [Modelagem de Cálcio](#calcio)
    3. [Modelagem de Vitamina A](#vitaminaA)
    4. [Modelagem de Riboflavina](#riboflavina)
    5. [Modelagem de Ácido Ascórbico](#acido)
3. [Implementação](#implementacao)
    1. [1° Passo da Implementação](#1passo)
    2. [2° Passo da Implementação](#2passo)
    3. [3° Passo da Implementação](#3passo)
4. [Resultados Numéricos](#resultados)
    1. [Custo Total por Pessoa](#custo)
    2. [Custo por Nutrientes da Letra b](#custoB)
5. [Conclusões](#conclusao)
6. [Bibliografia](#bibliografia)



## <div id='introducao'/> **Introdução**

O Objetivo do Trabalho é encontrar os custos mínimos para o cumprimento da dieta especificada pelo médico, de forma com que a quantidade de nutrientes necessários seja indicado pelas primeiras 5 letras do nome de cada aluno seguindo a tabela abaixo:

| Letra | Dieta | ProdutoX |
|-------|-------|----------|
| A     | 7     | 63       |
| B     | 60    | 52       |
| C     | 83    | 59       |
| D     | 10    | 85       |
| E     | 39    | 82       |
| F     | 59    | 58       |
| G     | 38    | 50       |
| H     | 30    | 69       |
| I     | 65    | 44       |
| J     | 27    | 26       |
| K     | 91    | 30       |
| L     | 68    | 43       |
| M     | 49    | 90       |
| N     | 6     | 91       |
| O     | 10    | 45       |
| P     | 32    | 82       |
| Q     | 51    | 98       |
| R     | 47    | 67       |
| S     | 20    | 97       |
| T     | 66    | 28       |
| U     | 78    | 54       |
| V     | 81    | 33       |
| W     | 81    | 59       |
| X     | 61    | 61       |
| Y     | 0     | 39       |
| Z     | 86    | 83       |


Os nutrientes desejados, em ordem respectiva às letras do nome, são: <span style="color: cyan;">Caloria</span>, <span style="color: blue;">Cálcio</span>, <span style="color: rgb(204,204,0);">Vitamina A</span>, <span style="color: red;">Riboflavina</span> e <span style="color: green;">Ácido Ascórbico</span>.

O *Produto X* é uma das Mercadorias que pode ser comprada para suprir a dieta, e cujas informações nutricionais e custo estão explicitados na tabela acima, também dependendo das 5 primeiras letras do nome.

As outras Mercadorias que podem ser utilizadas para compor a dieta e alcançar os objetivos nutricionais desejados estão disponibilizados na tabela abaixo, dando-se ênfase para alguns produtos, que são os únicos disponíveis na loja em que serão comprados, estes sendo: *Farinha de Trigo (Enriquecida)*, *Leite Evaporado*, *Queijo Cheddar*, *Fígado Bovino*, *Repolho*, *Espinafre*, *Batata Doce* e *Feijão Verde (Seco)*.

| Numero | Mercadoria                  | <span style="color: cyan;">Caloria</span> | Proteina | <span style="color: blue;">Cálcio</span> | Ferro | <span style="color: rgb(204,204,0);">Vitamina A</span> | Tiamina | <span style="color: red;">Riboflavina</span> | Niacina | <span style="color: green;">Ácido Ascórbico</span> |
|:------ |:--------------------------- |:------- |:-------- |:------ |:--------- |:------- |:----------- |:------- |:-------------- |:---------------- |
| 1      | Farinha de trigo (enriquecida) | 44.7    | 1411     | 2      | 365       | 0       | 55.4        | 33.3    | 441            | 0                |
| 5      | Farinha de milho            | 36      | 897      | 1.7    | 99        | 30.9    | 17.4        | 7.9     | 106            | 0                |
| 15     | Leite evaporado (lata)      | 8.4     | 422      | 15.1   | 9         | 26      | 3           | 23.5    | 11             | 60               |
| 17     | Margarina                   | 20.6    | 17       | 0.6    | 6         | 55.8    | 0.2         | 0       | 0              | 0                |
| 19     | Queijo (cheddar)            | 7.4     | 448      | 16.4   | 19        | 28.1    | 0.8         | 10.3    | 4              | 0                |
| 21     | Pasta de amendoim           | 15.7    | 661      | 1      | 48        | 0       | 9.6         | 8.1     | 471            | 0                |
| 24     | Bacon                       | 41.7    | 0        | 0      | 0         | 0.2     | 0           | 5       | 5              | 0                |
| 30     | Fígado (boi)                | 2.2     | 333      | 0.2    | 139       | 169.2   | 6.4         | 50.8    | 316            | 525              |
| 34     | Lombo de porco assado       | 4.4     | 249      | 0.3    | 37        | 0       | 18.2        | 3.6     | 79             | 0                |
| 40     | Salmão. rosa (lata)         | 5.8     | 705      | 6.8    | 45        | 3.5     | 1           | 4.9     | 209            | 0                |
| 45     | Feijão verde                | 2.4     | 138      | 3.7    | 80        | 69      | 4.3         | 5.8     | 37             | 862              |
| 46     | Repolho                     | 2.6     | 125      | 4      | 36        | 7.2     | 9           | 4.5     | 26             | 5369             |
| 50     | Cebola                      | 5.8     | 166      | 3.8    | 59        | 16.6    | 4.7         | 5.9     | 21             | 1184             |
| 51     | Batatas                     | 14.3    | 336      | 1.8    | 118       | 6.7     | 29.4        | 7.1     | 198            | 2522             |
| 52     | Espinafre                   | 1.1     | 106      | 0      | 138       | 918.4   | 5.7         | 13.8    | 33             | 2755             |
| 53     | Batata-doce                 | 9.6     | 138      | 2.7    | 54        | 290.7   | 8.4         | 5.4     | 83             | 1912             |
| 64     | Pêssegos. secos             | 8.5     | 87       | 1.7    | 173       | 86.8    | 1.2         | 4.3     | 65             | 257              |
| 65     | Ameixas secas               | 12.8    | 99       | 2.5    | 154       | 85.7    | 3.9         | 4.3     | 65             | 257              |
| 68     | Feijão verde. seco          | 17.4    | 1055     | 3.7    | 459       | 5.1     | 26.9        | 38.2    | 93             | 0                |
| 69     | Feijão branco. seco         | 26.9    | 1691     | 11.4   | 792       | 0       | 38.4        | 24.6    | 217            | 0                |



## <div id='modelagem'/> **Modelagem**

> Encontrando a Dieta de Custo Mínimo: (Letra A)

Primeiramente, é importante realizar a organização dos dados sendo trabalhados. Portanto, é possível reduzir a segunda tabela para manter somente as informações consideradas relevantes (mantendo somente os nutrientes desejados e os alimentos disponíveis).

| Numero | Mercadoria                  | <span style="color: cyan;">Caloria</span> | <span style="color: blue;">Cálcio</span> | <span style="color: rgb(204,204,0);">Vitamina A</span> | <span style="color: red;">Riboflavina</span> | <span style="color: green;">Ácido Ascórbico</span> |
|:------ |:--------------------------- |:----------------------------------------- |:---------------------------------------- |:---------------------------------------------- |:-------------------------------------------- |:-------------------------------------------------- |
| 1      | Farinha de trigo (enriquecida) | 44.7                                      | 2                                        | 0                                              | 33.3                                         | 0                                                  |
| 2     | Leite evaporado (lata)      | 8.4                                       | 15.1                                     | 26                                             | 23.5                                         | 60                                                 |
| 3     | Queijo (cheddar)            | 7.4                                       | 16.4                                     | 28.1                                           | 10.3                                         | 0                                                  |
| 4     | Fígado (boi)                | 2.2                                       | 0.2                                      | 169.2                                          | 50.8                                         | 525                                                |
| 5     | Repolho                     | 2.6                                       | 4                                        | 7.2                                            | 4.5                                          | 5369                                               |
| 6     | Espinafre                   | 1.1                                       | 0                                        | 918.4                                          | 13.8                                         | 2755                                               |
| 7     | Batata-doce                 | 9.6                                       | 2.7                                      | 290.7                                          | 5.4                                          | 1912                                               |
| 8     | Feijão verde. seco          | 17.4                                      | 3.7                                      | 5.1                                            | 38.2                                         | 0                                                  |


> Para referenciar os Produtos durante a Modelagem, o modelo utilizado será M<sub>indice</sub>

> Os nutrientes do Produto X serão referenciados como sendo X<sub>nutriente</sub> e sua quantidade será de M<sub>X</sub>

> Os nutrientes necessários na Dieta serão referenciados como sendo D<sub>nutriente</sub>

As modelagens serão feitas de forma a encontrar as quantidades de alimentos (custos) necessários para se obter pelo menos o mínimo de nutrição indicado pela dieta.

### <div id='calorias'/> Modelagem da Quantidade de <span style="color: cyan;">Calorias</span> Necessárias:

44.7 * M<sub>1</sub> + 8.4 * M<sub>2</sub> + 7.4 * M<sub>3</sub> + 2.2 * M<sub>4</sub> + 2.6 * M<sub>5</sub> + 1.1 * M<sub>6</sub> + 9.6 * M<sub>7</sub> + 17.4 * M<sub>8</sub> + X<sub><span style="color: cyan;">Calorias</span></sub> * M<sub>X</sub> $\geqslant$ D<sub><span style="color: cyan;">Calorias</span></sub>

### <div id='calcio'/> Modelagem da Quantidade de <span style="color: blue;">Cálcio</span> Necessário:

2 * M<sub>1</sub> + 15.1 * M<sub>2</sub> + 16.4 * M<sub>3</sub> + 0.2 * M<sub>4</sub> + 4 * M<sub>5</sub> + 0 * M<sub>6</sub> + 2.7 * M<sub>7</sub> + 3.7 * M<sub>8</sub> + X<sub><span style="color: blue;">Cálcio</span></sub> * M<sub>X</sub> $\geqslant$ D<sub><span style="color: blue;">Cálcio</span></sub>

### <div id='vitaminaA'/> Modelagem da Quantidade de <span style="color: rgb(204,204,0);">Vitamina A</span> Necessária:

0 * M<sub>1</sub> + 26 * M<sub>2</sub> + 28.1 * M<sub>3</sub> + 169.2 * M<sub>4</sub> + 7.2 * M<sub>5</sub> + 918.4 * M<sub>6</sub> + 290.7 * M<sub>7</sub> + 5.1 * M<sub>8</sub> + X<sub><span style="color: rgb(204,204,0);">Vitamina A</span></sub> * M<sub>X</sub> $\geqslant$ D<sub><span style="color: rgb(204,204,0);">Vitamina A</span></sub>

### <div id='riboflavina'/> Modelagem da Quantidade de <span style="color: red;"> Riboflavina </span> Necessária:

33.3 * M<sub>1</sub> + 23.5 * M<sub>2</sub> + 10.3 * M<sub>3</sub> + 50.8 * M<sub>4</sub> + 4.5 * M<sub>5</sub> + 13.8 * M<sub>6</sub> + 5.4 * M<sub>7</sub> + 38.2 * M<sub>8</sub> + X<sub><span style="color: red;">Riboflavina</span></sub> * M<sub>X</sub> $\geqslant$ D<sub><span style="color: red;">Riboflavina</span></sub>

### <div id='acido'/> Modelagem da Quantidade de <span style="color: green;">Ácido Ascórbico</span> Necessário:

0 * M<sub>1</sub> + 60 * M<sub>2</sub> + 0 * M<sub>3</sub> + 525 * M<sub>4</sub> + 5369 * M<sub>5</sub> + 2755 * M<sub>6</sub> + 1912 * M<sub>7</sub> + 0 * M<sub>8</sub> + X<sub><span style="color: green;">Ácido Ascórbico</span></sub> * M<sub>X</sub> $\geqslant$ D<sub><span style="color: green;">Ácido Ascórbico</span></sub>

### Objetivo: Minimizar **Custo** = M<sub>1</sub> + M<sub>2</sub> + M<sub>3</sub> + M<sub>4</sub> + M<sub>5</sub> + M<sub>6</sub> + M<sub>7</sub> + M<sub>8</sub> + M<sub>X</sub>

> Para encontrar as informações da Letra b, basta executar somente as linhas dos nutrientes desejados

## <div id='implementacao'/> **Implementação**

### <div id='1passo'/> 1° Passo da Implementação:

- Henrique
    - H $\rarr$ D<sub><span style="color: cyan;">Calorias</span></sub> = 30 x 10<sup>2</sup> <span style="color: cyan;">Calorias</span> ; X<sub><span style="color: cyan;">Calorias</span></sub> = 690 x 10<sup>2</sup> <span style="color: cyan;">Calorias</span>
    - E $\rarr$ D<sub><span style="color: blue;">Cálcio</span></sub> = 39 x 10<sup>-2</sup> gramas de <span style="color: blue;">Cálcio</span> ; X<sub><span style="color: blue;">Cálcio</span></sub> = 820 x 10<sup>-2</sup> gramas de <span style="color: blue;">Cálcio</span>
    - N $\rarr$ D<sub><span style="color: rgb(204,204,0);">Vitamina A</span></sub> = 6 x 10<sup>2</sup> UI de <span style="color: rgb(204,204,0);">Vitamina A</span> ; X<sub><span style="color: rgb(204,204,0);">Vitamina A</span></sub> = 910 x 10<sup>2</sup> UI de <span style="color: rgb(204,204,0);">Vitamina A</span>
    - R $\rarr$ D<sub><span style="color: red;">Riboflavina</span></sub> = 47 x 10<sup>-1</sup> miligramas de <span style="color: red;">Riboflavina</span> ; X<sub><span style="color: red;">Riboflavina</span></sub> = 67 x 10<sup>-1</sup> miligramas de <span style="color: red;">Riboflavina</span>
    - I $\rarr$ D<sub><span style="color: green;">Ácido Ascórbico</span></sub> = 65 miligramas de <span style="color: green;">Ácido Ascórbico</span> ; X<sub><span style="color: green;">Ácido Ascórbico</span></sub> = 44 miligramas de <span style="color: green;">Ácido Ascórbico</span>
- Lucas
    - L $\rarr$ D<sub><span style="color: cyan;">Calorias</span></sub> = 68 x 10<sup>2</sup> <span style="color: cyan;">Calorias</span> ; X<sub><span style="color: cyan;">Calorias</span></sub> = 430 x 10<sup>2</sup> <span style="color: cyan;">Calorias</span>
    - U $\rarr$ D<sub><span style="color: blue;">Cálcio</span></sub> = 78 x 10<sup>-2</sup> gramas de <span style="color: blue;">Cálcio</span> ; X<sub><span style="color: blue;">Cálcio</span></sub> = 540 x 10<sup>-2</sup> gramas de <span style="color: blue;">Cálcio</span>
    - C $\rarr$ D<sub><span style="color: rgb(204,204,0);">Vitamina A</span></sub> = 83 x 10<sup>2</sup> UI de <span style="color: rgb(204,204,0);">Vitamina A</span> ; X<sub><span style="color: rgb(204,204,0);">Vitamina A</span></sub> = 590 x 10<sup>2</sup> UI de <span style="color: rgb(204,204,0);">Vitamina A</span>
    - A $\rarr$ D<sub><span style="color: red;">Riboflavina</span></sub> = 7 x 10<sup>-1</sup> miligramas de <span style="color: red;">Riboflavina</span> ; X<sub><span style="color: red;">Riboflavina</span></sub> = 63 x 10<sup>-1</sup> miligramas de <span style="color: red;">Riboflavina</span>
    - S $\rarr$ D<sub><span style="color: green;">Ácido Ascórbico</span></sub> = 20 miligramas de <span style="color: green;">Ácido Ascórbico</span> ; X<sub><span style="color: green;">Ácido Ascórbico</span></sub> = 97 miligramas de <span style="color: green;">Ácido Ascórbico</span>
- Rafael
    - R $\rarr$ D<sub><span style="color: cyan;">Calorias</span></sub> = 47 x 10<sup>2</sup> <span style="color: cyan;">Calorias</span> ; X<sub><span style="color: cyan;">Calorias</span></sub> = 670 x 10<sup>2</sup> <span style="color: cyan;">Calorias</span>
    - A $\rarr$ D<sub><span style="color: blue;">Cálcio</span></sub> = 7 x 10<sup>2</sup> gramas de <span style="color: blue;">Cálcio</span> ; X<sub><span style="color: blue;">Cálcio</span></sub> = 630 x 10<sup>2</sup> gramas de <span style="color: blue;">Cálcio</span>
    - F $\rarr$ D<sub><span style="color: rgb(204,204,0);">Vitamina A</span></sub> = 59 x 10<sup>2</sup> UI de <span style="color: rgb(204,204,0);">Vitamina A</span> ; X<sub><span style="color: rgb(204,204,0);">Vitamina A</span></sub> = 580 x 10<sup>2</sup> UI de <span style="color: rgb(204,204,0);">Vitamina A</span>
    - A $\rarr$ D<sub><span style="color: red;">Riboflavina</span></sub> = 7 x 10<sup>-1</sup> miligramas de <span style="color: red;">Riboflavina</span> ; X<sub><span style="color: red;">Riboflavina</span></sub> = 63 x 10<sup>-1</sup> miligramas de <span style="color: red;">Riboflavina</span>
    - E $\rarr$ D<sub><span style="color: green;">Ácido Ascórbico</span></sub> = 39 miligramas de <span style="color: green;">Ácido Ascórbico</span> ; X<sub><span style="color: green;">Ácido Ascórbico</span></sub> = 82 miligramas de <span style="color: green;">Ácido Ascórbico</span>

### <div id='2passo'/> 2° Passo da Implementação

> Transformar a Modelagem para a Forma Padrão ($\geqslant$ $\rarr$ $\leqslant$)

-44.7 * M<sub>1</sub> - 8.4 * M<sub>2</sub> - 7.4 * M<sub>3</sub> - 2.2 * M<sub>4</sub> - 2.6 * M<sub>5</sub> - 1.1 * M<sub>6</sub> - 9.6 * M<sub>7</sub> - 17.4 * M<sub>8</sub> - X<sub><span style="color: cyan;">Calorias</span></sub> * M<sub>X</sub> $\leqslant$ - D<sub><span style="color: cyan;">Calorias</span></sub>

-2 * M<sub>1</sub> - 15.1 * M<sub>2</sub> - 16.4 * M<sub>3</sub> - 0.2 * M<sub>4</sub> - 4 * M<sub>5</sub> - 0 * M<sub>6</sub> - 2.7 * M<sub>7</sub> - 3.7 * M<sub>8</sub> - X<sub><span style="color: blue;">Cálcio</span></sub> * M<sub>X</sub> $\leqslant$ D<sub><span style="color: blue;">Cálcio</span></sub>

-0 * M<sub>1</sub> - 26 * M<sub>2</sub> - 28.1 * M<sub>3</sub> - 169.2 * M<sub>4</sub> - 7.2 * M<sub>5</sub> - 918.4 * M<sub>6</sub> - 290.7 * M<sub>7</sub> - 5.1 * M<sub>8</sub> - X<sub><span style="color: rgb(204,204,0);">Vitamina A</span></sub> * M<sub>X</sub> $\leqslant$ D<sub><span style="color: rgb(204,204,0);">Vitamina A</span></sub>

-33.3 * M<sub>1</sub> - 23.5 * M<sub>2</sub> - 10.3 * M<sub>3</sub> - 50.8 * M<sub>4</sub> - 4.5 * M<sub>5</sub> - 13.8 * M<sub>6</sub> - 5.4 * M<sub>7</sub> - 38.2 * M<sub>8</sub> - X<sub><span style="color: red;">Riboflavina</span></sub> * M<sub>X</sub> $\leqslant$ D<sub><span style="color: red;">Riboflavina</span></sub>

-0 * M<sub>1</sub> - 60 * M<sub>2</sub> - 0 * M<sub>3</sub> - 525 * M<sub>4</sub> - 5369 * M<sub>5</sub> - 2755 * M<sub>6</sub> - 1912 * M<sub>7</sub> - 0 * M<sub>8</sub> - X<sub><span style="color: green;">Ácido Ascórbico</span></sub> * M<sub>X</sub> $\leqslant$ D<sub><span style="color: green;">Ácido Ascórbico</span></sub>

### <div id='3passo'/> 3° Passo da Implementação

> Aplicação do Método Simplex (em Python)

- Necessário transformar os dados para a forma Ax $\leqslant$ b, onde estamos trabalhando nas mesmas unidades.
- 
  - A é a Matriz dos Coeficientes
  - x é o Vetor com as Variáveis (Neste caso, M<sub>i</sub> )
  - b é o Vetor das Restrições

> Encontrando a Matriz dos Coeficientes

```Python
def matriz_loja(nome:str):
    nome = nome.upper()
    m = deepcopy(tabela_loja)
    for i in range(5): #são cinco nutrientes
        if i < len(nome) and nome[i] in dieta_prodx_por_letra:
            letra = nome[i]
            val = float(dieta_prodx_por_letra[letra][1]) * conversao_prod_x[i] #converte para undade correta
            m[i].append(val)
        else: 
            m[i].append(0.)
    return np.matrix(m)
```

> Encontrando o Vetor de Restrições

```Python
def restricoes(nome:str):
    nome = nome.upper()
    r = []
    for i in range(5):
        if i < len(nome) and nome[i] in dieta_prodx_por_letra:
            letra = nome[i]
            val = float(dieta_prodx_por_letra[letra][0]) * conversao_dieta[i] #converte para unidade correta
            r.append(val)
        else:
            r.append(0.)
    return np.array(r)
```

> Encontrando o Vetor de Variáveis (Objetivo)

```Python
def dieta(nome:str, method:str):
    # Invertendo os sinais para transformar para a forma padrão
    m = -matriz(nome)
    r = -restricoes(nome)
    c = np.ones(len(alimentos) + 1) # esse é o funcional linear que será minimizado
    return scipy.optimize.linprog(c=c, A_ub=m, b_ub=r, method=method)
```

## <div id='resultados'/> **Resultados Numéricos**

> Resultado da Matriz de Coeficientes

- Henrique

M = $\begin{bmatrix}
-44.7 & -8.4 & -7.4 & -2.2 & -2.6 & -1.1 & -9.6 & -17.4 & -69 \\
-2 & -15.1 & -16.4 & -0.2 & -4 & -0 & -2.7 & -3.7 & -8.2 \\
-0 & -26 & -28.1 & -169.2 & -7.2 & -918.4 & -290.7 & -5.1 & -91 \\
-33.3 & -23.5 & -10.3 & -50.8 & -4.5 & -13.8 & -5.4 & -38.2 & -6.7 \\
-0 & -60 & -0 & -525 & -5369 & -2755 & -1912 & -0 & -44
\end{bmatrix}$

- Lucas

M = $\begin{bmatrix}
-44.7 & -8.4 & -7.4 & -2.2 & -2.6 & -1.1 & -9.6 & -17.4 & -43 \\
-2 & -15.1 & -16.4 & -0.2 & -4 & -0 & -2.7 & -3.7 & -5.4 \\
-0 & -26 & -28.1 & -169.2 & -7.2 & -918.4 & -290.7 & -5.1 & -59 \\
-33.3 & -23.5 & -10.3 & -50.8 & -4.5 & -13.8 & -5.4 & -38.2 & -6.3 \\
-0 & -60 & -0 & -525 & -5369 & -2755 & -1912 & -0 & -97
\end{bmatrix}$

- Rafael

M = $\begin{bmatrix}
-44.7 & -8.4 & -7.4 & -2.2 & -2.6 & -1.1 & -9.6 & -17.4 & -67 \\
-2 & -15.1 & -16.4 & -0.2 & -4 & -0 & -2.7 & -3.7 & -6.3 \\
-0 & -26 & -28.1 & -169.2 & -7.2 & -918.4 & -290.7 & -5.1 & -58 \\
-33.3 & -23.5 & -10.3 & -50.8 & -4.5 & -13.8 & -5.4 & -38.2 & -6.3 \\
-0 & -60 & -0 & -525 & -5369 & -2755 & -1912 & -0 & -82
\end{bmatrix}$

> Resultado do Vetor de Restrições

Usamos (para testar) dois métodos diferentes do `scipy.optimize.lingprog`, o `simplex`e o `highs`. Ambos dão o mesmo resultado. Vi, posteriormente na implementação do código deles do simplex - https://github.com/scipy/scipy/blob/c0065b69a98be549b46e44573bbf3c13e98681da/scipy/optimize/_linprog_simplex.py - que eles usam o método de duas fases para determinar uma solução inicial.


- Henrique

b = $\begin{bmatrix}
-3 \\ -0.39 \\ -0.6 \\ -4.7 \\ -65
\end{bmatrix}$

- Lucas

b = $\begin{bmatrix}
-6.8 \\ -0.78 \\ -8.3 \\ -0.7 \\ -20
\end{bmatrix}$

- Rafael

b = $\begin{bmatrix}
-4.7 \\ -0.07 \\ -5.9 \\ -0.7 \\ -39
\end{bmatrix}$

> Resultado do Vetor de Variáveis (Objetivo)

- Henrique

x = $\begin{bmatrix}
0 \\ 0.00280396 \\ 0 \\ 0.08403366 \\ 0.00687433 \\ 0 \\ 0 \\ 0.04034798
\end{bmatrix}$

- Lucas

x = $\begin{bmatrix}
0.0203727 \\ 0 \\ 0 \\ 0 \\ 0.00243949 \\ 0 \\ 0 \\ 0.136899
\end{bmatrix}$

- Rafael

x = $\begin{bmatrix}
0.00315594 \\ 0 \\ 0 \\ 0 \\ 0.01213675 \\ 0 \\ 0 \\ 0.06784447
\end{bmatrix}$

> Quantidade de nutrientes por pessoa
- Henrique

-Mx = $\begin{bmatrix}
3 \\ 0.39 \\ 24.27644967 \\ 4.7 \\ 65
\end{bmatrix}$

- Lucas

-Mx = $\begin{bmatrix}
6.8 \\ 0.78 \\ 10.31746934 \\ 1.57453944 \\ 20
\end{bmatrix}$

- Rafael

-Mx = $\begin{bmatrix}
4.7 \\ 0.43373201 \\ 15.08137274 \\ 0.7 \\ 39.
\end{bmatrix}$

### <div id='custo'/> Custo total por pessoa

- Henrique = *U$ 0.1340599306242723*

- Lucas = *U$ 0.15971118784604565*

- Rafael = *U$ 0.08313715497274843*

### <div id='custoB'/> Custo considerando somente a Vitamina A e a Riboflavina (Letra b)

> Nós concordamos que o custo que estaríamos dispostos a pagar seria considerando todos os alimentos (e seus preços) - mesmo aqueles que não estão disponíveis na loja.


- Henrique
  - <span style="color: rgb(204,204,0);">Vitamina A</span> = *U$ 0.0006533101045296169*
  - <span style="color: red;">Riboflavina</span> = *U$ 0.09251968503937008*
- Lucas
  - <span style="color: rgb(204,204,0);">Vitamina A</span> = *U$ 0.009037456445993032*
  - <span style="color: red;">Riboflavina</span> = *U$ 0.01377952755905512*
- Rafael
  - <span style="color: rgb(204,204,0);">Vitamina A</span> = *U$ 0.006424216027874565*
  - <span style="color: red;">Riboflavina</span> = *U$ 0.01377952755905512*

## <div id='conclusao'/> **Conclusões**

> É possível concluir que os valores necessários para alcançar a nutrição da dieta são todos baixos, com o Rafael sendo a pessoa que requer menos dinheiro para alcançar o objetivo nutricional.

## <div id='bibliografia'/> **Bibliografia**

https://docs.scipy.org/doc/scipy/reference/optimize.linprog-simplex.html

https://github.com/scipy/scipy/blob/c0065b69a98be549b46e44573bbf3c13e98681da/scipy/optimize/_linprog_simplex.py

https://docs.python.org/3/library/csv.html



<style>
.markdown-body strong{
    color: orange;
}

.markdown-body em{
    color: rgb(111,255,0);
}
</style>
