 Trabalho Final - EQM2108
# Modelagem e simulação do estireno considerando o efeito gel
### Aluno: Francisco Strunck
### Professora: Amanda Lemette


# Introdução

Os polímeros têm um lugar de destaque em várias áreas, tais como: farmacêutica, química coloidal, tecnológica, dentre outras. Essa grande predominância exige constante investimento em novas tecnologias para a síntese desses materiais. Um polímero, de maneira geral, pode ser caracterizado com propriedades especificas variando a resistência mecânica, flexibilidade e resistência. Podem ser lineares, ramificados ou assumir uma estrutura em rede tridimensional [1].

Os polímeros podem ser inorgânicos ou orgânicos, naturais ou sintéticos. Os polímeros sintéticos orgânicos são, basicamente, formados por hidrocarbonetos insaturados, derivados do petróleo. A reação de polimerização que dá origem a esses materiais, em geral, é classificada em dois tipos: condensação e adição. Na reação por condensação, cada etapa do processo é acompanhada pela formação da molécula de uma substância simples, geralmente a água. Na polimerização por adição, os monômeros reagem para produzir um polímero, sem formar subprodutos [1].

O estireno é um monômero líquido, incolor e oleoso. Matéria-prima para diversos processos da indústria química tendo a principal aplicação na formação do poliestireno, uma resina do grupo dos termoplásticos, cuja característica reside na flexibilidade sob ação do calor e resistência quando resfriado. As aplicações deste polímero são diversas: eletrodomésticos, construção civil, embalagens, emulsões, borrachas, dentre outras. 

Particularmente, o poliestireno é formado por reação adição dos monômeros do estireno (Figura 1). O polímero tem destinação principalmente para elastômeros, resinas e poliestireno expandido. O estireno é majoritariamente obtido a partir do etilbenzeno extraído do petróleo. Durante o ano de 2020, o mercado de poliestireno sofreu uma queda de 7 % em função da pandemia. Neste ano o mercado movimentava mais de 30 bilhões de dólares e com projeção de crescimento de 4% ao ano até 2026, uma vez que países asiáticos continuam a construir novas plantas de produção. [8].

<center><img src="https://github.com/amandalemette/EQM2109/blob/cf5536e05e532ad7b46bd3fce0c2b97325fc0d36/Turma_2021.2/Francisco/Figura%201.png?raw=true"  width=600 height=250 /><center>
 
 
 
O poliestireno é um plástico amplamente utilizado, bem estabelecido e está cada vez mais presente no dia a dia. Espera-se que a demanda global aumente e por tanto é necessário que sua produção seja cada vez mais eficiente para atender a alta de seu consumo.
 
Para isso, a utilização cada vez mais intensiva de modelagem e simulação no processo de produção do poliestireno deve ser utilizada a fim de minimizar incertezas de produção (baixa qualidade, baixa produtividade, descartes e acidentes) maximizando os lucros.
 
Portanto, o objetivo deste trabalho é modelar e simular a polimerização do estireno em solução considerando o balanço de energia usando o método dos momentos. Inicialmente, utilizar o artigo de Alvarez e Odloak (2011) para aplicar a modelagem e o balanço de energia em um reator de tanque agitado contínuo (CSTR). Posteriormente, testar o uso da equação empírica para a considerar o efeito gel no mesmo sistema. Por fim, prever em função do tempo a massa molar média numérica (Mn), massa molar média ponderal (Mw), dispersividade (D), conversão, temperatura, viscosidade e produtividade.

  
# Metodologia

Foi realizada a simulação da polimerização do estireno em um reator CSTR no Python pelo método dos momentos utilizando os parâmetros e dados termodinâmicos do Alvarez e Odloak (2011) e, posteriormente, adicionado e efeito gel utilizando os dados fornecidos por Hui et al. (1972), de modo que seja possível comparar os dados dos artigos com os dados obtidos por esse trabalho.
 
A modelagem matemática é a parte principal deste trabalho. O método dos momentos é uma abordagem determinística onde são contabilizadas as propriedades médias do sistema por meio de um cálculo estatístico da população de polímeros vivos e polímeros mortos. Ao invés de realizar a reação molécula por molécula e ir armazenado essa informação de progressão da reação, como outros métodos realizam, o método dos momentos reduz de forma bastante elevada o processamento computacional por meio de um cálculo estatístico.

 De modo objetivo, este método pode ser descrito pelas Equações 2.1 e 2.2. A variável i é o comprimento de uma cadeia de polímero (número de unidades monoméricas), P é a concentração molar de cadeia viva e L é a concentração molar de cadeia morta. 

<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/eq2_1.png?raw=true" /><center> 

<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/eq2_2.png?raw=true" /><center> 
 
O momento zero, representado quando k = 0, é a soma dos indivíduos daquele sistema. O primeiro momento (k = 1) é a soma dos indivíduos do sistema multiplicado pelo número de unidades monomérica do polímero correspondente, já o segundo momento é a soma dos indivíduos do sistema multiplicado pelo número de unidades monomérica do polímero correspondente elevado ao quadrado e assim por diante.

<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/eq2_345.png?raw=true" /><center> 
 
O momento zero da distribuição do comprimento de cadeia representa a concentração de cadeias poliméricas no sistema, ou seja, o número total de moléculas de polímero. O primeiro momento representa a concentração de unidade monoméricas que foram incorporadas às cadeias poliméricas, ou seja, número total de unidades monoméricas presentes em todas as moléculas de polímero. Os demais momentos não representam conceitos físicos que possam ser objetivamente explicados.
 
Com base nos momentos é possível predizer dados das propriedades físico-químicas do polímero que são de grande interesse. Neste trabalho, será calculado a massa molar média numérica (𝑀𝑛), massa molar média ponderal (𝑀w), dispersividade (D) e a viscosidade (Eta).
 
<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/eq2_6789.png?raw=true" /><center> 
 
A modelagem da polimerização do estireno foi realizada em Python 3. Para a criação e manipulação de vetores, construção dos gráficos e integração e resolução das equações diferenciais ordinárias foi usado, respectivamente, as bibliotecas numpy, pyplot e odeint.

## Descrição do reator

Neste trabalho é realizado a polimerização do estireno por meio da operação contínua em um reator CSTR. Por ser uma reação exotérmica, o reator aumenta de temperatura em relação a temperatura inicial de entrada e, em razão do aumento da massa molar média das moléculas, um aumento da viscosidade. Esses parâmetros serão analisados uma vez que influem de modo substancial nas características finais do produto.
Como se pode observar, na Figura 3 ao lado, o reator recebe 3 fluxos de alimentação: monômero de estireno, iniciador azobisisobutironitrila (AIBN) e o solvente benzeno. A saída do reator consiste na mistura final com a produção do poliestireno e dos monômeros não reagidos, iniciador e solvente. 
Para o controle de temperatura, é utilizado uma camisa de fluido frio que também tem o fluxo de entrada e temperatura controlados. 

<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/figura2.png?raw=true" align="center" width=400 height=400 /><center>
 
Foi realizada a polimerização do estireno por meio da operação contínua em um reator de tanque agitado contínuo (CSTR). Por ser uma reação exotérmica, a temperatura do meio aumenta relação a temperatura inicial de entrada e, em razão do aumento da massa molar média das moléculas, há um aumento da viscosidade. Esses parâmetros serão analisados, uma vez que, influem de modo substancial nas características finais do produto.
 
Como se pode observar, na Figura 2 ao lado, o reator recebe 3 fluxos de alimentação: monômero de estireno, iniciador azobisisobutironitrila (AIBN) e o solvente benzeno. A saída do reator consiste na mistura final com a produção do poliestireno e dos monômeros não reagidos, iniciador e solvente. 

Para o controle de temperatura, é utilizado uma camisa de fluido frio que também tem o fluxo de entrada e temperatura monitorados.
  
## Descrição das reações

A cinética e o mecanismo de reações de polimerização podem ser escritos pelas seguintes etapas:

<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/reacoes.png?raw=true"  /><center>
    
## Modelo cinético

Para o modelo cinético é necessário levar em conta as seguintes considerações:

•	Considerando que os radicais são altamente reativos e, consequentemente, o tempo de vida é extremamente curto. Então, é possível considerar que a concentração dessas substâncias não varia com o tempo e, portanto, aplica-se a aproximação de quase estado (QSSA) para R e Pn;
 
<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/eq2_1011.png?raw=true" /><center>

•	O consumo de monômero é feito majoritariamente pela propagação;

•	Reações de transferência de cadeia para monômero, solvente e impurezas não são considerados;

•	A iniciação térmica do monômero não ocorre;

•	A taxa de reação por terminação global kt é composta pela soma da taxa de reação de combinação ktc e desproporcionamento ktd;

•	A taxa de propagação ser muito maior que a taxa de terminação;

•	O calor liberado na iniciação e terminação são insignificantes em comparação ao calor liberado na propagação.

<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/eq2_12131415.png?raw=true"  /><center>

onde,
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/eq2_161718.png?raw=true"  /><center>

finalmente,
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/eq2_192021.png?raw=true" /><center>
  
## Efeito Gel

O efeito gel é um fenômeno cinético que ocorre durante a realização da polimerização e está relacionada com o aumento de viscosidade do meio reacional decorrente do aumento do aumento da massa molar média das moléculas presentes no meio.
 
Essencialmente, ocorre a diminuição da mobilidade das cadeias vivas, diminuindo a velocidade de terminação de cadeia. Este fenômeno afeta fortemente as propriedades finais do polímero aumentando a massa molar média numérica (Mn), massa molar média ponderal (Mw), dispersividade (D) e temperatura do reator.
 
O efeito gel é qualificado matematicamente a diminuição da constante cinética de terminação em razão pela diminuição da mobilidade das moléculas de polímero vivo e, portanto, favorecendo a reação de propagação. Para o poliestireno, as fórmulas abaixo representam esse efeito, considerando a conversão (X). Demais constantes estão presentes em anexo.

<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/eq2_2223242526.png?raw=true" /><center>
  
# Resultados
 
Nesta seção são apresentados os resultados da modelagem do poliestireno. No primeiro caso é replicada a simulação do artigo de Alvarez e Odloak (2011) com a temperatura do reator constante. No segundo caso, é acrescentado dados termodinâmicos do artigo Hui et al. (1972) para a aplicação do efeito gel.  
 
## Situação 1: Replicação dos resultados do artigo em Python com temperatura do reator constante
 
Como o artigo de Alvarez e Odloak (2011) realiza o controle por um sistema de otimização em tempo real não é possível ter imagens idênticas aos do artigo. Entretanto, é possível analisar se os valores se equivalem em ordem de grandeza.
 
No primeiro caso, apresentado na figura abaixo, está a viscosidade do meio. A direita está o gráfico produzido pelo artigo e a esquerda o gráfico produzido nesta tarefa.

<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/figura3.png?raw=true" /><center> 
 
Pode-se observar que os valores iniciais perto de 3,9 Pa/(cdot s) em ambos os casos seguido do decrescimento dos valores. Após um período não é possível comparar os gráficos pois o controlador atua no sistema o meio evitando que a viscosidade passe de 3,5 Pa/(cdot s), o que ocorreria sem controle. O aumento de viscosidade é um sinal de que está ocorrendo um aumento da massa molar média das cadeias poliméricas do meio, sendo uma maneira indireta de medi-la. 
 
Para a temperatura do reator, assim como para a viscosidade, ocorre um comportamento semelhante no começo da simulação com um aumento gradual da temperatura que no caso deste trabalho continua sem a interferência do controlador e passa levemente de 330 K.

<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/figura4.png?raw=true" /><center> 
 
No caso da produtividade, a discrepância foi um pouco maior apesar de reproduzir o mesmo comportamento no intervalo inicial. Pode-se observar que a produtividade está diretamente relacionada com a temperatura do reator, uma vez que quanto maior a taxa de propagação do polímero maior quantidade de energia é liberada dado que a reação é exotermica.
 
<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/figura5.png?raw=true" /><center> 
 
## Situação 2: Comparação dos resultados acrescentando o efeito gel
 
Alvarez e Odloak (2011) relatam que o efeito gel é minimizado pelo modo em que o controle foi configurado. Entretanto, como não aplicamos o controle do processo é possível realizar a comparação entre a simulação sem e com o efeito gel.
 
No primeiro caso, está a viscosidade do meio. A esquerda o gráfico anteriormente produzido e a direita o gráfico aplicando o efeito gel.

<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/figura6.png?raw=true" /><center>
 
Pode-se observar que para a modelagem considerando o efeito gel a viscosidade do meio é muito mais alta. Isso ocorre em razão do aumento da taxa de polimerização (aumento da massa molar média numérica) e, consequentemente, da desaceleração da reação de terminação uma vez que a mobilidade dos polímeros diminui.
 
Como a reação de propagação é favorecida, a temperatura do reator tente a aumentar mais, e isso pode ser observado nas imagens abaixo. A esquerda o gráfico anteriormente produzido e a direita o gráfico aplicando o efeito gel. 
 
<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/figura7.png?raw=true" /><center>
 
A produtividade está diretamente relacionada com a temperatura do reator, uma vez que quanto maior a taxa de propagação do polímero maior quantidade de energia é liberada dado que a reação é exotermica. No segundo caso, a produtividade quando alcança o regime transiente é aproximadamente 12x maior que no primeiro caso.

<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/figura8.png?raw=true" /><center>
 
Para entender melhor a produtividade do reator, podemos observar a conversão de todo monômero que entra no reator. O valor em regime transiente no primeiro modelo é de 62,81% e no modelo considerando o efeito gel 71,56%. Essa diferença de aproximadamente 9,75% justifica, em parte, a maior produtividade.
 

<center><img src="https://github.com/amandalemette/EQM2109/blob/2ceb3310446b09e8e0a8d406bb4224d998c2a416/Turma_2021.2/Francisco/figura9.png?raw=true" /><center>
 
# Conclusões 

No primeiro caso de replicação dos resultados do artigo em Python é possível concluir que a polimerização se comporta da forma semelhante. Como os resultados do artigo se somam ao controle do processo, não é possível comparar de forma integral.
 
Adicionando as mudanças na simulação para aplicar o efeito gel na polimerização do estireno, é possível observar o que a literatura reporta: aumento viscosidade, maior dispersividade (D) e aumento da temperatura do reator. 


# Referências
  
[1] Paul C. Hiemenz, Timothy R Lodge, Polymer Chemistry, Second Edition, Taylor & Francis Group, 2007.
 
[2] Vinay Prasada, Matthias Schleyb, Louis P. Russoc, B. Wayne Bequettea. Product property and production rate control of styrene polymerization, Journal of Process Control, vol. 12, 353 – 372, 2002.
 
[3] Mariano Asteasuain, Alberto Bandoni, Claudia Sarmoria, Adriana Brandolin, Simultaneous process and control system design for grade transition in styrene polymerization, Chemical Engineering Science, vol. 61, 3362 – 3378, 2006.
 
[4] H. Bouhenchir, M. Cabassud, M.V. Le Lann, Predictive functional control for the temperature control of a chemical batch reactor, Computers and Chemical Engineering, vol. 30, 1141 – 1154, 2006.
 
[5] Nayef Mohamed Ghasem, Suhairi Abdul Sata, Mohamed Azlan Hussain, Temperature Control of a Bench-Scale Batch Polymerization Reactor for Polystyrene Production, Chemical Engineering Technology, vol. 30, 1193 – 1202, 2007.
 
[6] L. A. Alvarez* and D. Od, Optimization and Control of a Continuous Polymerization Reactor, Brazilian Journal of Chemical Engineering, vol. 29, no. 04,807 - 820, 2012.
 
[7] Abdelkarim M. Ertiame, Dingli Yu, Feng Yu & J.B. Gomm, Robust fault diagnosis for an exothermic semibatch polymerization reactor under open-loop, vol. 3, 14 – 23, 2015.
 
[8] Mordon Intelligence, POLYSTYRENE MARKET - GROWTH, TRENDS, COVID-19 IMPACT, AND FORECASTS (2021 - 2026), https://www.mordorintelligence.com/industry-reports/polystyrene-market. Acessado em: 27/12/2021.
 
[9] Yuyun Zeng, Jingquan Liu, Kaichao Sun, Lin-wen Hu. Machine learning based system performance prediction model for reactor control, Annals of Nuclear Energy, vol. 113, 270-278, 2018.
 
[10] - Expert Market Research, Reports. Disponível em: https://www.expertmarketresearch.com/reports /polystyrene-market. Acesso em: 09/12/2021

[11] - Ceresana, Polystyrene Market Report. Disponível em: https://www.ceresana.com/en/market-studies/plastics/polystyrene/. Acesso em: 09/12/2021

[12] - Hui,A.W.; Hamielec, A.E. Thermal polymerization of styrene at high conversions and temperatures. An experimental study. J.Applied Poly. Science 16, 749, 1972.

[13] – Alvarez L. A.; Odloak D., OPTIMIZATION AND CONTROL OF A CONTINUOUS POLYMERIZATION REACTOR. Brazilian Journal of Chemical Engineering, Vol. 29, No. 04, pp. 807 - 820, October - December, 2012

# Anexo
  
Tabela 1: Parâmetros do processo para o reator de polimerização
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/anexo1.png?raw=true" width=800 height=300 /><center>

Tabela 2: Condição operacional de estado estacionário para o reator de polimerização

<center><img src="https://github.com/amandalemette/EQM2109/blob/d4bac670a6ce3b9506f0b2bcda6cb5782a65aaa6/Turma_2021.2/Francisco/anexo2.png?raw=true"  width=800 height=300 /><center>
