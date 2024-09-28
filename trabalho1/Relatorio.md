# **Relatório do Trabalho 1**

## Índice

1. [Introdução](#introducao)
2. [Modelagem](#modelagem)
    1. [Modelagem de Calorias](#calorias)
3. [Implementação](#implementacao)
4. [Resultados Numéricos](#resultados)
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


Os nutrientes desejados, em ordem respectiva às letras do nome, são: <span style="color: cyan;">Caloria</span>, <span style="color: blue;">Cálcio</span>, <span style="color: yellow;">Vitamina A</span>, <span style="color: red;">Riboflavina</span> e <span style="color: green;">Ácido Ascórbico</span>.

O *Produto X* é uma das Mercadorias que pode ser comprada para suprir a dieta, e cujas informações nutricionais e custo estão explicitados na tabela acima, também dependendo das 5 primeiras letras do nome.

As outras Mercadorias que podem ser utilizadas para compor a dieta e alcançar os objetivos nutricionais desejados estão disponibilizados na tabela abaixo, dando-se ênfase para alguns produtos, que são os únicos disponíveis na loja em que serão comprados, estes sendo: *Farinha de Trigo (Enriquecida)*, *Leite Evaporado*, *Queijo Cheddar*, *Fígado Bovino*, *Repolho*, *Espinafre*, *Batata Doce* e *Feijão Verde (Seco)*.

| Numero | Mercadoria                  | <span style="color: cyan;">Caloria</span> | Proteina | <span style="color: blue;">Cálcio</span> | Ferro | <span style="color: yellow;">Vitamina A</span> | Tiamina | <span style="color: red;">Riboflavina</span> | Niacina | <span style="color: green;">Ácido Ascórbico</span> |
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

| Numero | Mercadoria                  | <span style="color: cyan;">Caloria</span> | <span style="color: blue;">Cálcio</span> | <span style="color: yellow;">Vitamina A</span> | <span style="color: red;">Riboflavina</span> | <span style="color: green;">Ácido Ascórbico</span> |
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

> Os nutrientes necessários na Dieta serão referenciados como sendo N<sub>nutriente</sub>

### <div id='calorias'/> Modelagem da Quantidade de <span style="color: cyan;">Calorias</span> Necessárias:

44.7 * M<sub>1</sub> + 8.4 * M<sub>2</sub> + 7.4 * M<sub>3</sub> + 2.2 * M<sub>4</sub> + 2.6 * M<sub>5</sub> + 1.1 * M<sub>6</sub> + 9.6 * M<sub>7</sub> + 17.4 * M<sub>8</sub> + X<sub><span style="color: cyan;">Calorias</span></sub> * M<sub>X</sub> 

## <div id='implementacao'/> **Implementação**

## <div id='resultados'/> **Resultados Numéricos**

## <div id='conclusao'/> **Conclusões**

## <div id='bibliografia'/> **Bibliografia**

<style>
.markdown-body strong{
    color: orange;
}

.markdown-body em{
    color: rgb(111,255,0);
}
</style>
