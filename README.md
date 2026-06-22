# Ciclo de Krebs_PCD

Meu projeto consiste na construção de um grafo de fluxo metabólico do Ciclo de Krebs, permitindo identificar se um organismo é capaz de realizar essa via metabólica a partir dos genes e enzimas presentes em seu genoma. Para isso, foram utilizadas informações obtidas nas bases de dados KEGG (Kyoto Encyclopedia of Genes and Genomes) e NCBI (National Center for Biotechnology Information), que serviram como referência para a associação entre reações metabólicas e enzimas.

Este projeto faz parte da disciplina de Prática em Ciência de Dados ministrada pelos professores Drs. Leandro Nascimento Lemos, Daniel Roberto Cassar e James Moraes de Almeida, na ILUM – Escola de Ciência.

## Objetivo

O objetivo deste trabalho é representar o fluxo metabólico que realiza o Ciclo de Krebs por meio de um grafo direcional ponderado, permitindo representar visualmente as transformações bioquímicas entre metabólitos e analisar a capacidade de diferentes organismos de realizar essa importante rota metabólica de produção de energia.

Além da visualização da rede, o projeto implementa uma ferramenta capaz de verificar automaticamente se um organismo possui todas as enzimas necessárias para completar as etapas essenciais do ciclo.

## Estrutura da Rede Metabólica

A rede foi construída utilizando uma estrutura de dados em Python baseada em dicionários. Nessa representação:

- Cada nó representa um metabólito.
- Cada aresta representa uma reação metabólica.
- Cada reação possui uma ou mais enzimas associadas.
- O sentido das arestas indica a direção da conversão metabólica.

Entre os principais metabólitos representados estão:

- Glycolysis
- Phosphoenol-pyruvate
- Pyruvate
- Oxaloacetate
- Acetyl-CoA
- Citrate
- Isocitrate
- 2-Oxo-glutarate
- Succinyl-CoA
- Succinate
- Fumarate
- (S)-Malate

Além dos metabólitos do ciclo, também foram incluídas conexões com etapas da glicólise e da formação do acetil-CoA, permitindo contextualizar a entrada de carbono no Ciclo de Krebs.

## Visualização da Rede

Para a construção e visualização do grafo foram utilizadas as bibliotecas:

- NetworkX
- Matplotlib

caso voce não tenha essas duas bibliotecas, basta abrir o terminal e digitar os seguintes códigos separadamente

```
pip.instal Matplotlib
```

```
pip.instal NetworkX
```

O grafo é modelado como uma rede direcionada (`DiGraph`), na qual:

- Os nós representam metabólitos.
- As arestas representam reações bioquímicas.
- Os rótulos das arestas correspondem às enzimas responsáveis por cada transformação.

O algoritmo `spring_layout` foi utilizado para organizar automaticamente os nós no espaço, produzindo uma representação visual clara das relações metabólicas existentes.

A visualização permite identificar:

- O fluxo das moléculas ao longo do ciclo.
- Os intermediários metabólicos.
- Os pontos de entrada e saída do ciclo.
- As enzimas envolvidas em cada etapa.

## Identificação das Enzimas Essenciais

A partir da estrutura do grafo, foi criado um conjunto contendo as enzimas associadas a cada etapa essencial do Ciclo de Krebs.

As etapas analisadas são:

1. Oxaloacetate → Citrate
2. Citrate → Isocitrate
3. Isocitrate → 2-Oxo-glutarate
4. 2-Oxo-glutarate → Succinyl-CoA
5. Succinyl-CoA → Succinate
6. Succinate → Fumarate
7. Fumarate → (S)-Malate
8. (S)-Malate → Oxaloacetate

Cada etapa pode possuir uma ou mais enzimas capazes de catalisar a reação correspondente.

## Verificação da Presença do Ciclo de Krebs

Além da construção da rede metabólica, foi implementado um algoritmo capaz de determinar se um organismo possui as enzimas necessárias para realizar o Ciclo de Krebs.

Para isso, as enzimas associadas a cada etapa essencial do ciclo foram extraídas diretamente da estrutura do grafo metabólico. Cada etapa é representada por um conjunto de enzimas que podem catalisar a reação correspondente.

Foi implementada a função:

verifica_ciclo_krebs(enzimas_organismo)

Essa função recebe como entrada uma lista contendo os genes ou enzimas identificados em um organismo e compara esse conjunto de informações com as enzimas necessárias para cada etapa do ciclo.
O algoritmo segue os seguintes passos:

Recebe a lista de enzimas do organismo.
Converte a lista em um conjunto (set) para facilitar as buscas.
Percorre todas as etapas essenciais do Ciclo de Krebs.
Verifica se existe pelo menos uma enzima capaz de catalisar cada reação.
Registra as etapas para as quais nenhuma enzima foi encontrada.
Determina se o ciclo está completo ou incompleto.

Quando todas as etapas essenciais possuem pelo menos uma enzima correspondente, o organismo é considerado capaz de realizar o Ciclo de Krebs.
Caso alguma etapa esteja ausente, o programa informa exatamente quais transformações metabólicas não podem ser realizadas.

## como utilizar

Para usar o projeto em seu computador, localmente, você precisará baixar este repositório. Para isso, você pode clonar o repositório ou baixar o arquivo zip.

## Referências

1- Informação verbal fornecida pelos Prof. Dr. Leandro Nascimento Lemos, Prof. Dr. Daniel Roberto Cassar e Prof. Dr. James Moraes de Almeida na disciplina de Prática em Ciência de dados, em Campinas, ILUM – Escola de Ciência

2- 