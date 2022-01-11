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

A figura abaixo (figura 1), extraída do artigo "High density polyethylene (HDPE): Experiments and modeling", apresenta a relação entre tensão e deformação para o PEAD. É dada a relação experimental e predita pelo modelo VBS para três taxas de deformação diferentes.

<center><img src="https://github.com/amandalemette/EQM2109/blob/22103b301f68ed48c5c7993a57ce58de59231bee/Turma_2021.2/Henrique_Abreu/Imagens/figura3.png"
 
A figura 1 pode ser dividida em três regiões, região elástica (região I), região plástica (região II), e região de descarregamento (região III). A soma das regiões I e II constituem a região de carregamento, ou seja, onde um único eixo do corpo de prova estava submetido a uma carga. Já a região de descarregamento demonstra o comportamento mecânico do corpo de prova ao deixar de ser submetido a mesma carga que ocorria durante o carregamento. Na região elástica (região I) a relação entre tensão e deformação deve ser linear, pois o corpo de prova deve ser capaz de recuperar a sua forma original ao cessar o carregamento. Já na região plástica (região II) percebe-se que não existe mais relação linear entre a tensão e a deformação e portanto o corpo de prova está sofrendo uma deformação permanente. Na região de descarregamento, pode-se perceber que o material recupera ligeiramente a sua forma com a diminuição da tensão, demonstrando que existe elasticidade ainda na região plástica.
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/eb592a0370b82cb17191247a6ecffbb4b30d0f3d/Turma_2021.2/Henrique_Abreu/Imagens/figura3_elast_plast_unload.png"

Por meio do software GetData Graph Digitizer, foram extraídos os dados experimentais da curva com taxa de deformação igual a 0,001 [1/s]. Os dados que representam a região de carregamento (região I e II) foram salvos no arquivo serie1_load.txt e posteriormente armazenados em um dataframe (df0) no Python. Já os dados que representam a região de carregamento (região I e II) e descarregamento (região I, II e III) foram salvos no arquivo serie1_load-unload.txt e posteriormente armazenados em um dataframe (df1) no Python.

A definição do modelo VBO é dado abaixo (equação 1):
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/9d1f5f867d07ddcb0fd70a78941064ab9f67063f/Turma_2021.2/Henrique_Abreu/Imagens/flow_law.png?raw=true"

A função de escoamento é dada por (equação 2):
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/81b3e0e7eebebd0bee5dd641d494538227d855dd/Turma_2021.2/Henrique_Abreu/Imagens/flow_function.png"
             
O parâmetro C utilizado para modelar o comportamento não-linear do descarregamento (equação 3):
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/017a03d2cd677afe384555feb72785ba5f40e8eb/Turma_2021.2/Henrique_Abreu/Imagens/unloading_behavior.png"
             
O invariante de sobretensão é dado por (equação 4):
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/overstress_invariant.png"

A tensão de equilíbrio é dada por (equação 5):

<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/equilibrium_stress-rate.png"

A função de forma é dada por (equação 6):
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/shape_function.png"
             
A tensão cinemática é dada por (equação 7):
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/kinematic_stress.png"

E o módulo da tangente é dado por (equação 8):
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/tangent_modulus.png"
             
As condições de contorno foram dadas pelo artigo na tabela 1:

<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/chart.png"

Estas equações constitutivas (equações 2-8) permitem que o modelo VBS (equação 1) forneça a  deformação para diferentes tensões. Deste modo, as equações constitutivas foram escritas em Python à fim de replicar o modelo VBS. Por fim, utilizou-se as tensões experimentais, armazenadas no dataframe df0, para se obter as deformações a partir da réplica do modelo VBS criada no Python.
             
# Resultados e Discussões
             
Pela função de escoamento do modelo VBS replicado em Python, pôde-se obter uma curva próxima à experimental na região elástica, região a qual a curva de escoamento é linear. Porém o modelo obtido não apresentou a linearidade característica desta região do gráfico.

<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/modelo_escoamento.png"
             
O gráfico abaixo considera também a região de descarregamento do material, ou seja, . Como visto no gráfico, a função de escoamento somente se aproxima da região elástica, o artigo aponta que para modelar a região de descarregamento é preciso considerar o parâmetro C.
             
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
