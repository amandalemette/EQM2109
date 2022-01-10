## Trabalho final da disciplina EQM2109
# Modelagem da relação tensão-deformação do Polietileno de Alta Densidade
Professora Amanda Lemette

Aluno: Henrique Abreu

# Resumo
O artigo "High density polyethylene (HDPE): Experiments and modeling" compara resultados de ensaios mecânicos realizados em corpos de prova de polietileno de alta densidade (PEAD)
a resultados da simulação utilizando a teoria da viscoplasticidade baseada em sobretensão (VBS). O artigo também compara os resultados experimentais a modelos de 
elasto-viscoplasticidade de Boyce. Porém o foco deste trabalho está na comparação dos resultados experimentais aos resultados utilizando a VBS.


# Introdução
No artigo proposto foi analisado o comportamento do polietileno de alta densidade (PEAD) submetido ao carregamento e descarregamento a diferentes taxas de deformação. Foram realizados também ensaios de fluência e relaxação a diferentes tensões e níveis de deformação. Os resultados experimentais foram então simulados utilizando a teoria da viscoplasticidade baseada em sobretensão (VBS) e o modelo de Boyce à fim de comparar as duas metodologias para a modelagem do comportamento do PEAD. Porém, neste trabalho foi utilizada somente a VBS para a modelagem do ensaio de tração uniaxial (carregamento e descarregamento).

# Metodologia

A figura 3 do artigo apresenta a relação entre tensão e deformação para o PEAD. É dada a relação experimental e predita pelo modelo VBS para três taxas de deformação diferentes.
Por meio do software GetData Graph Digitizer, foram extraídos os dados experimentais para a curva da taxa de deformação igual a 0,001 [1/s]. Os dados foram salvos no arquivo
serie1.txt e posteriormente armazenados em um dataframe (df0) no Python.

A definição do modelo VBO foi dada na equação 14 do artigo.

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

Estas equações permitem que o modelo VBS (equação 14) forneça a taxa de deformação para diferentes tensões. Deste modo, utilizou-se as tensões experimentais para obter as deformações a partir do modelo VBS.
             
# Resultados e Discussões

Pela função de escoamento do modelo VBO pôde-se obter uma curva próxima à experimental para a região elástica. Porém o modelo obtido não tem a linearidade esperada nesta região
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
