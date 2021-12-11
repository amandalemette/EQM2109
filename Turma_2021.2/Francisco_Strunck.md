 Trabalho Final - EQM2108
# Modelagem e simulação do estireno considerando o efeito gel
### Aluno: Francisco Strunck
### Professora: Amanda Lemette

# Objetivos

Modelar e simular a polimerização do estireno em solução considerando o balanço de energia usando o método dos momentos. Utilizar o artigo de Alvarez e Odloak (2011) para aplicar o balanço de energia e testar o uso da equação empírica para a consideração do efeito gel. Por fim, prever a concentração de estireno massa molar média numérica (Mn), massa molar média ponderal (Mw), dispersividade (D), conversão, temperatura em função do tempo, viscosidade e produtividade.

# Introdução

O estireno é um monômero líquido, incolor e oleoso. Matéria-prima para diversos processos da indústria química tendo a principal aplicação na formação do poliestireno, uma resina do grupo dos termoplásticos, cuja característica reside na flexibilidade sob ação do calor e resistência quando resfriado. As aplicações deste polímero são diversas: eletrodomésticos, construção civil, embalagens, emulsões, borrachas, dentre outras. 
Em 2019, a produção de poliestireno está na casa dos 15 milhões de toneladas por ano e com tendência de crescimento de 2% ao ano até 2026, uma vez que países asiáticos continuam a construir novas plantas de produção.
O poliestireno é um plástico amplamente utilizado e bem estabelecido e está cada vez mais presente no dia a dia. Espera-se que a demanda global aumente e por tanto é necessário que sua produção seja cada vez mais eficiente para atender a alta de seu consumo.
Para isso, a utilização cada vez mais intensiva de modelagem e simulação no processo de produção do poliestireno deve ser utilizada a fim de minimizar incertezas de produção (baixa qualidade, baixa produtividade, descartes e acidentes), maximizando os lucros.

<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/figura1.png?raw=true" width=250 height=180 /><center>
  
# Metodologia

Foi realizado a simulação da polimerização do poliestireno no Python pelo método dos mínimos quadrados utilizando os parâmetros e dados do Alvarez e Odloak (2011) e complementado por Hui et al. (1972).

## Descrição do reator

Neste trabalho é realizado a polimerização do estireno por meio da operação contínua em um reator CSTR. Por ser uma reação exotérmica, o reator aumenta de temperatura em relação a temperatura inicial de entrada e, em razão do aumento da massa molar média das moléculas, um aumento da viscosidade. Esses parâmetros serão analisados uma vez que influem de modo substancial nas características finais do produto.
Como se pode observar, na Figura 3 ao lado, o reator recebe 3 fluxos de alimentação: monômero de estireno, iniciador azobisisobutironitrila (AIBN) e o solvente benzeno. A saída do reator consiste na mistura final com a produção do poliestireno e dos monômeros não reagidos, iniciador e solvente. 
Para o controle de temperatura, é utilizado uma camisa de fluido frio que também tem o fluxo de entrada e temperatura controlados. 

<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/figura2.png?raw=true" width=330 height=380 /><center>
  
## Descrição das reações

A cinética e o mecanismo de reações de polimerização podem ser escritos pelas seguintes etapas:

<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/reacoes.png?raw=true" width=600 height=300 /><center>
    
## Modelo cinético

Para o modelo cinético é necessário levar em conta as seguintes considerações:

•	Tempo de vida dos radicais é extremamente curto. Então, é possível considerar estado estacionário para R e Pn;

•	O consumo de monômero é feito majoritariamente pela propagação;

•	Reações de transferência de cadeia para monômero, solvente e impurezas não são considerados;

•	A iniciação térmica do monômero não ocorre;

•	A taxa de reação por terminação global kt é composta pela soma da taxa de reação de combinação ktc e desproporcionamento ktd;

•	A taxa de propagação ser muito maior que a taxa de terminação;

•	O calor liberado na iniciação e terminação são insignificantes em comparação ao calor liberado na polimerização.

Levando em conta todas essas considerações o modelo cinético utilizado é definido por:

<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/modelocinetico1.png?raw=true" width=600 height=400 /><center>

onde,
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/modelocinetico2.png?raw=true" width=400 height=400 /><center>

finalmente,
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/modelocinetico3.png?raw=true" width=600 height=300 /><center>
  
## Efeito Gel

O efeito gel é um fenômeno cinético que ocorre durante a realização da polimerização e está relacionada com o aumento de viscosidade do meio reacional decorrente do aumento do aumento da massa molar média das moléculas presentes no meio. 
Essencialmente, ocorre a diminuição da mobilidade das cadeias de crescimento diminuindo a velocidade de terminação de cadeia, resultando na aceleração da polimerização. Este fenômeno afeta fortemente as propriedades finais do polímero aumentando a massa molar média numérica (Mn), massa molar média ponderal (Mw), dispersividade (D) e temperatura do reator.
O efeito vítreo é qualificado matematicamente a diminuição da constante cinética de terminação em razão pela diminuição da mobilidade das moléculas de polímero vivo e, portanto, favorecendo a reação de propagação. Para o poliestireno, as fórmulas abaixo representam esse efeito, considerando a conversão (X). Demais constantes estão presentes em anexo.

<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/efeitogel.png?raw=true" width=500 height=400 /><center>
  
# Resultados

## Replicação dos resultados do artigo em Python com temperatura do reator constante

<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/conversao1.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/I1.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/M1.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/Mn1.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/Mw1.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/D1.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/Eta1.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/Pr1.png?raw=true" width=250 height=180 /><center>

## Aplicação do efeito gel 
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/Conversao2.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/I2.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/M2.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/Mn2.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/Mw2.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/D2.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/Eta2.png?raw=true" width=250 height=180 /><center>
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/Pr2.png?raw=true" width=250 height=180 /><center>

# Conclusões 

No primeiro caso de replicação dos resultados do artigo em Python é possível concluir que a polimerização se comporta da forma semelhante. Como os resultados do artigo se somam ao controle do processo, não é possível comparar de forma integral.
Adicionando as mudanças na simulação para aplicar o efeito gel na polimerização do estireno, é possível observar o que a literatura reporta: aumento da Mn e Mw, maior dispersividade (D), aumento da temperatura do reator e viscosidade. 

# Referências
  
[1] - Expert Market Research, Reports. Disponível em: https://www.expertmarketresearch.com/reports /polystyrene-market. Acesso em: 09/12/2021

[2] - Ceresana, Polystyrene Market Report. Disponível em: https://www.ceresana.com/en/market-studies/plastics/polystyrene/. Acesso em: 09/12/2021

[3] - Hui,A.W.; Hamielec, A.E. Thermal polymerization of styrene at high conversions and temperatures. An experimental study. J.Applied Poly. Science 16, 749, 1972.

[4] – Alvarez L. A.; Odloak D.,Optimization and control of a continuous polymerization reactor. Brazilian Journal of Chemical Engineering, Vol. 29, No. 04, pp. 807 - 820, October - December, 2012

# Anexo
  
Tabela 1: Parâmetros do processo para o reator de polimerização
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/anexo1.png?raw=true" width=800 height=300 /><center>

Tabela 2: Condição operacional de estado estacionário para o reator de polimerização

<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/anexo2.png?raw=true"  width=800 height=300 /><center>
