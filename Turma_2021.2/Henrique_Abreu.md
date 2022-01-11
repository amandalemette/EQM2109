## Trabalho final da disciplina EQM2109
# Modelagem da relação tensão-deformação do Polietileno de Alta Densidade
Professora Amanda Lemette

Aluno: Henrique Abreu

# Resumo
O artigo "High density polyethylene (HDPE): Experiments and modeling" compara resultados de ensaios mecânicos realizados em corpos de prova de polietileno de alta densidade (PEAD) a resultados da simulação utilizando a teoria da viscoplasticidade baseada em sobrecarga (VBS). O artigo também compara os resultados experimentais ao modelo de elasto-viscoplasticidade de Boyce. Porém o foco deste trabalho está na comparação dos resultados experimentais aos resultados utilizando a VBS.

# Introdução
Os materiais poliméricos não apresentam um comportamento mecânico linearmente dependente do tempo e da temperatura ao serem submetidos à ensaios mecânicos. Foram portanto desenvolvidas equações, chamadas equações constitutivas, à fim de descrever isoladamente alguns dos comportamentos mecânicos dos materiais poliméricos. A partir das equações constitutivas foram desenvolvidos os modelos constitutivos, que buscam explicar a complexidade do comportamento mecânico dos polímeros ao serem submetidos a diferentes condições de carregamento e descarregamento.

Os modelos constitutivos podem ser divididos entre as duas principais abordagens para descrever o comportamento mecânico dos materiais poliméricos; as abordagens micro e macro-mecânicas. A abordagem micro-mecânica é baseada na física da deformação, ou seja, são considerados os vetores de tensão normal e cisalhante para a modelagem do comportamento mecânico, o que permite explicar mais facilmente os constituintes microestruturais e os mecânismos de deformação influenciados pela temperatura. Já na abordagem macro-mecânica, as teorias da viscoelasticidade e viscoplasticidade lineares foram modificadas para abranger o comportamento mecânico não-linear. Esta modificação do modelo linear se dá pela introdução da tensão ou deformação baseada em escala de tempo, isto ocorre por meio do uso dos invariantes de tensão ou deformação, que por suas vezes são constituídos pelas tensões principais e seus vetores direção constituídos pelas direções principais. Nos últimos anos, pesquisadores desenvolveram modelos híbridos, que utilizam a abordagem macro e micro-mecânicas, um destes modelos é o modelo de elasto-viscoplasticidade de Boyce et al. (2000). Apesar de ser um modelo híbrido, este modelo oferece uma abordagem majoritariamente macro-mecânica.

Outro modelo constitutivo utilizado é uma modificação da teoria da viscoplasticidade baseada em sobrecarga (VBS), realizada por Colak (2005). A VBS foi inicialmente desenvolvida para explicar o comportamento mecânico de metais, suas modificações permitem a sua utilização para explicar o comportamento de polímeros, e mais recentemente, de nanocompósitos. O modelo VBS proposto por Colak (2005) utiliza o valor de dois tensores, uma propriedade escalar, e uma lei de crescimento para explicar o comportamento mecânico do polietileno de alta densidade (PEAD) em ensaios de carregamento e descarregamento uniaxial.

No artigo "High density polyethylene (HDPE): Experiments and modeling" foi analisado o comportamento mecânico do PEAD submetido ao carregamento e descarregamento a diferentes taxas de deformação. Foram realizados também ensaios de fluência e relaxação a diferentes tensões e níveis de deformação. Os resultados experimentais foram então simulados utilizando o modelo VBS proposto por Colak (2005) e o modelo de Boyce et al. (2000) à fim de comparar as duas metodologias para a modelagem do comportamento do PEAD. Porém, devido a ausência dos valores dos tensores utilizados no artigo no modelo de Boyce et al. (2000), neste trabalho foi utilizado somente o modelo VBS para replicar a modelagem do ensaio de tração uniaxial (carregamento e descarregamento).

# Metodologia

A figura abaixo, extraída do artigo "High density polyethylene (HDPE): Experiments and modeling", apresenta a relação entre tensão e deformação para o PEAD. É dada a relação experimental e predita pelo modelo VBS para três taxas de deformação diferentes.

<center><img src="https://github.com/amandalemette/EQM2109/blob/22103b301f68ed48c5c7993a57ce58de59231bee/Turma_2021.2/Henrique_Abreu/Imagens/figura3.png"
             
Por meio do software GetData Graph Digitizer, foram extraídos os dados experimentais da curva com taxa de deformação igual a 0,001 [1/s]. Os dados foram salvos no arquivo serie1.txt e posteriormente armazenados em um dataframe (df0) no Python.

A definição do modelo VBO é dado na equação 1 abaixo:

<center><img src="https://github.com/amandalemette/EQM2109/blob/9d1f5f867d07ddcb0fd70a78941064ab9f67063f/Turma_2021.2/Henrique_Abreu/Imagens/flow_law.png?raw=true"

O parâmetro C utilizado para modelar o comportamento não-linear do descarregamento:
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/017a03d2cd677afe384555feb72785ba5f40e8eb/Turma_2021.2/Henrique_Abreu/Imagens/unloading_behavior.png"
             
O invariante de sobretensão é dado por:
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/overstress_invariant.png"

A tensão de equilíbrio é dada por:

<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/equilibrium_stress-rate.png"

A função de forma é dada por:
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/shape_function.png"
             
A tensão cinemática é dada por:
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/kinematic_stress.png"

E o módulo da tangente é dado por:
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/tangent_modulus.png"
             
As condições de contorno foram dadas pelo artigo na tabela 1:

<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/chart.png"

Estas equações constitutivas permitem que o modelo VBS (equação 1) forneça a taxa de deformação para diferentes tensões. Deste modo, as equações constitutivas foram escritas em Python à fim de replicar o modelo VBS. Por fim, utilizou-se as tensões experimentais, armazenadas no dataframe df0, para se obter as deformações a partir da réplica do modelo VBS criada no Python.
             
# Resultados e Discussões

Pela função de escoamento do modelo VBS pôde-se obter uma curva próxima à experimental para a região elástica. Porém o modelo obtido não tem a linearidade esperada nesta região
do gráfico.

<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/modelo_escoamento.png"
             
O gráfico abaixo considera também a região de descarregamento do material. Como visto no gráfico, a função de escoamento somente se aproxima da região elástica, o artigo aponta que para modelar a região de descarregamento é preciso considerar o parâmetro C.
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/modelo_escoamento_load.png"
             
Por fim, não houve sucesso na tentativa de utilizar o modelo VBO para obter uma curva próxima à todas as regiões dadas pela curva experimental.
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/017a03d2cd677afe384555feb72785ba5f40e8eb/Turma_2021.2/Henrique_Abreu/Imagens/modelo_load-unload.png"
             
A tensão desviadora de equilíbrio (g) tem bastante influência no modelo, a curva do gráfico acima foi obtida para g = 6.  
             
Para g = 14, obtém-se o seguinte gráfico:
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/cb2ef9a6ade1cec390bb8c618fa0de24a7ae4643/Turma_2021.2/Henrique_Abreu/Imagens/g_14.png"             
             
Foram realizadas outras tentativas para diferentes valores de g sem que houve uma melhor aproximação do modelo, portanto é necessário um estudo mais aprofundado deste e de outros parâmetros apontados no artigo, tais como:
             
- A taxa de tensão desviadora objetiva;
- A tensão cinemática;
- A tensão de equilíbrio (G).

# Conclusões

Pôde-se obter um modelo aproximado para a deformação na região elástica da curva tensão-deformação. Porém não foi possível utilizar o modelo VBS corretamente para chegar a uma
aproximação para as regiões inelástica e de descarregamento dos resultados experimentais.
             
# Referências
             
- DUSUNCELI, Necmi; COLAK, Ozgen U.. High density polyethylene (HDPE): Experiments and modeling;
- COLAK, Ozgen U.. Modeling deformation behavior of polymers with viscoplasticity theory based on overstress;
- COLAK, Ozgen U.; CAKIR, Y.. Material model parameter estimation with genetic algorithm optimization method and modeling of strain and temperature dependent behavior of epoxy resin with cooperative-VBO model.
