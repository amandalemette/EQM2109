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

No artigo "High density polyethylene (HDPE): Experiments and modeling" foi analisado o comportamento mecânico do PEAD submetido ao carregamento e descarregamento a diferentes taxas de deformação. Também são realizados ensaios de relaxamento de tensão e de fluência. Os resultados experimentais foram então simulados utilizando o modelo VBS proposto por Colak (2005) e o modelo de Boyce et al. (2000) à fim de comparar as duas metodologias para a modelagem do comportamento do PEAD. Porém, devido a ausência dos valores dos tensores utilizados no artigo no modelo de Boyce et al. (2000), neste trabalho foi utilizado somente o modelo VBS para replicar a modelagem do ensaio de tração uniaxial (carregamento e descarregamento).

# Metodologia

## Carregamento e Descarregamento

A figura abaixo (figura 1), extraída do artigo "High density polyethylene (HDPE): Experiments and modeling", apresenta a relação entre tensão e deformação para o PEAD após um ensaio de tração uniaxial. É dada a relação experimental e predita pelo modelo VBS para três taxas de deformação diferentes.

<center><img src="https://github.com/amandalemette/EQM2109/blob/22103b301f68ed48c5c7993a57ce58de59231bee/Turma_2021.2/Henrique_Abreu/Imagens/figura3.png"
 
Um ensaio de tração uniaxial é realizado por meio de uma máquina de tensão e um corpo de prova, que por sua vez é submetido à uma força variável perpendicular ao plano da seção transversal deste corpo de prova, promovendo uma taxa de deformação constante. A figura 1 abaixo exemplifica um ensaio de tração.
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/2473f4c8443cd335d3ce2ee4d41e7374db88d38a/Turma_2021.2/Henrique_Abreu/Imagens/tensile_machine.jpg"
             
A figura 2 pode ser dividida em três regiões, região elástica (região I), região plástica (região II), e região de descarregamento (região III). A soma das regiões I e II constituem a região de carregamento, ou seja, onde um único eixo do corpo de prova estava submetido a uma carga. Já a região de descarregamento demonstra o comportamento mecânico do corpo de prova ao deixar de ser submetido a mesma carga que ocorria durante o carregamento, para este experimento isto ocorre quando uma deformação de 14% é atingida. Na região elástica (região I) a relação entre tensão e deformação deve ser linear, pois o corpo de prova deve ser capaz de recuperar a sua forma original ao cessar o carregamento. Já na região plástica (região II) percebe-se que não existe mais relação linear entre a tensão e a deformação e portanto o corpo de prova está sofrendo uma deformação permanente. Na região de descarregamento, pode-se perceber que o material recupera ligeiramente a sua forma com a diminuição da tensão, demonstrando que existe elasticidade ainda na região plástica.
             
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

Estas equações constitutivas (equações 2-8) permitem que o modelo VBS (equação 1) forneça a  deformação para diferentes tensões. Deste modo, as equações constitutivas foram escritas em Python à fim de replicar o modelo VBS. Por fim, utilizou-se as tensões experimentais, armazenadas nos dataframes df0 e df1, para se obter as deformações a partir da réplica do modelo VBS criada no Python.
             
## Relaxamento de tensão e Fluência
             
O artigo proposto apresenta resultados experimentais para testes de relaxamento de tensão e de fluência. No relaxamento de tensão, a tensão que mantém o corpo de prova deformado a um determinado nível, tende a diminuir ao longo do tempo (figura 3). Na fluência, a deformação do corpo de prova submetido a uma determinada tensão tende a aumentar ao longo do tempo (figura 4). É possivel observar na figura 4 que o artigo simula os resultados para fluência do PEAD utilizando o modelo VBS, porém por não haver no artigo a indicação dos parâmetros utilizados para realizar esta simulação, não foi possível reproduzir a simulação da fluência para o PEAD neste trabalho.
      
Figura 3:             
<center><img src="https://github.com/amandalemette/EQM2109/blob/75545c26c37f3bb172231d69e4ab1047085ff5b7/Turma_2021.2/Henrique_Abreu/Imagens/relaxation.png"
             
Figura 4:
<center><img src="https://github.com/amandalemette/EQM2109/blob/75545c26c37f3bb172231d69e4ab1047085ff5b7/Turma_2021.2/Henrique_Abreu/Imagens/creep.png"             
             
# Resultados e Discussões
             
Pela função de escoamento (equação 2) do modelo VBS replicado em Python, pôde-se obter uma curva próxima à experimental na região elástica, região a qual a curva de escoamento é linear. Porém o modelo obtido não apresentou a linearidade característica desta região do gráfico. Era esperado que o resultado para um modelo utilizando somente uma equação constitutiva não representasse exatamente os resultados experimentais, uma vez que modelos constitutivos como o VBS são formados por uma série de euqações constitutivas.

<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/modelo_escoamento.png"
             
O gráfico abaixo considera também os dados experimentais da região de descarregamento do material. Comparando o gráfico abaixo ao anterior, a função de escoamento (equação 2) passa a ser ainda menos representativa do comportamento mecânico do PEAD.
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/51c2bd8f3b6e12fbd5651253b83a604168712587/Turma_2021.2/Henrique_Abreu/Imagens/modelo_escoamento_load.png"

O modelo VBS aponta que para modelar a região de descarregamento, é preciso considerar o parâmetro C (equação 3). As demais equações constitutivas (equações 4-8) estão intrinsicamente presentes na equação do parâmetro C.             
             
Ao adicionar o parâmetro C para compor o modelo VBS, não pôde-se obter um resultado razoável. E portanto, não houve sucesso na tentativa de replicar o modelo VBS para obter uma curva próxima à curva experimental nas regiões de carregamento e descarregamento.
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/017a03d2cd677afe384555feb72785ba5f40e8eb/Turma_2021.2/Henrique_Abreu/Imagens/modelo_load-unload.png"
             
No entanto, pôde-se observar que a tensão desviadora de equilíbrio (equação 5) tem bastante influência no modelo, a curva do gráfico acima foi obtida para g = 6.  
             
Para g = 14, obtém-se o seguinte gráfico:
             
<center><img src="https://github.com/amandalemette/EQM2109/blob/cb2ef9a6ade1cec390bb8c618fa0de24a7ae4643/Turma_2021.2/Henrique_Abreu/Imagens/g_14.png"             
             
Foram realizadas outras tentativas para diferentes valores da tensão desviadora de equilíbrio sem que houvesse uma melhor aproximação do modelo. Pôde-se obervar que tal qual ocorre para o modelo de Boyce et al. (2000), o artigo não apresenta todos os parâmetros necessários para o cálculo das equações constitutivas, tampouco pôde-se encontrar os valores para os parâmetros ausentes em outros artigos pesquisados. Os parâmetros com valores ausentes são os seguintes:
             - s -> tensão desviante de Cauchy;
             - g -> tensão desviante de equilíbrio;
             - k -> tensão desviante cinemática;
             - K -> tensão cinemática.

# Conclusões

Pôde-se obter um modelo que se aproxima do resultado experimental na região elástica da curva tensão-deformação resultante do ensaio de tração em um corpo de prova de PEAD, porém o modelo não foi capaz de replicar a linearidade característica da região elástica.
Não foi possível replicar o modelo VBS corretamente para obter uma aproximação para as regiões plástica e de descarregamento dos resultados experimentais.
             
# Referências
             
- DUSUNCELI, Necmi; COLAK, Ozgen U.. High density polyethylene (HDPE): Experiments and modeling;
- COLAK, Ozgen U.. Modeling deformation behavior of polymers with viscoplasticity theory based on overstress;
- COLAK, Ozgen U.; CAKIR, Y.. Material model parameter estimation with genetic algorithm optimization method and modeling of strain and temperature dependent behavior of epoxy resin with cooperative-VBO model.
