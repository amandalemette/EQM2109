## Final Project. Course. EQM: 2109

## Title: Dynamic Monte Carlo Simulation of Atom-Transfer Radical Polymerization

## Student: Carlos Alberto Castro Hoyos

## Professor: Amanda Lemette

## Introduction:

Monte Carlo simulation uses random sampling and statistical modeling to estimate mathematical functions and mimic the operations of complex systems. (Harrison, Granja and Leroy, 2021). Mainly, this method inverts the usual problem of statistics: rather than estimating random quantities in a deterministic manner, random quantities are employed to provide estimates of deterministic quantities. On the other hand, ATRP is another kind of carrying ourt living polymerization. This method sets up an equilibrium between a dormant phase of polymer chains and a growing phase. In the dormant phase, radicals have been trapped and are protected from termination, but are also unable to participate in polymerization. In the growing phase, radical chains have been released and can continue to grow by adding monomers in a radical mechanism. The idea is to release just a few radical chains at a time, recapturing them before they have a chance to undergo chain termination events (Living Radical Polymerization- ATRP, 2021). The mechanism depicted is shown in the figure No. 1.

<center><img src="https://github.com/amandalemette/EQM2109/blob/c76c3bf3300c34d1091c8b4597a3e461e4bfb305/Imagens/1.1.jpg"  width=1800 height=450 /><center>
  
                                          Figure No. 1. (Purkait, Sinha, Mondal and Singh, 2021)

Knowing the theorical foot for these models, it is possible to develop a dynamic Monte Carlo model in order to simulate an atom-transfer radical polymerization (ATRP). This simulation includes the calculation of different stages ocurring during the polymerization: Activatiod, deactivation, propagation, termination by combination and transfer to monomer. Through the definition of every reaction rate, it is possible to estimate the monomer conversion, the polydispersity and the complete molecular weight distribution. Basically, these predicions may be represented by graphics showing the performance of the simuation (Monte Carlo) and polymerization (ARTP) applied. 

## Methodology: 

The methodology developed in order to realize the Monte Carlo simulation is divided into 3 steps:
  
First step: Define and set the operation conditions (temperature, the reaction volume, the reaction time, the gel effect constants, the experimental rate constants and the initial conditions for especies). This is shown in the figures No. 2 and 3.
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/73c92740ef10b72c45bb250203fa15c1115592db/Imagens/2.png"  width=1800 height=550 /><center>
  
Figure No. 2. Setting the operation conditions (temperature, the reaction volume, the reaction time, the gel effect constants and the experimental rate constants).
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/ebf5b2de418e2996d4965ba3925564fc5b08622e/Imagens/3.png"  width=1800 height=550 /><center>

                                          Figure No. 3. Setting the initial condition for the species. 
  
Second step: Define and set the Monte Carlo parameters and the Monte Carlo rates. 
  
Based on Gillespie, experimental rate constants are transformed into stochastic rate constants (Monte Carlo parameters) with the three equations:

1) First order reactions: kmc = kexp

2) Biomolecular reactions between different species: kmc = kexp/(V*Na)

3) Biomolecular reactions between similar species: kmc = 2kexp/(VNa)

This definition is shown in the figure No. 4. (As ktd0 = 0, ktdMC = 0)
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/0f27db19c4063878cb4b1af127675f43bc250475/Imagens/4.png"  width=1800 height=550 /><center>
  
                                          Figure No. 4. Setting the Monte Carlo parameters 
  
As the only reaction which involves similar species is termination by combination, it is needed to apply the equation No. 3. On the other reactions is inforced to apply the equation No. 2.
  
Being defined the Monte Carlo parameters, the Monte Carlo rates are set involving the species. This definition is shown in the figure No. 5. 
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/3451f49a3c88753e207d9581ef54953d97470038/Imagens/5.png"  width=1800 height=550 /><center>
          
                                          Figure No. 5. Setting the Monte Carlo rates
  
Third step: Define the simution model, which implicates: Reaction probabilities and random values (from 0 to 1) in order to activate the probability definition and the reaction rates. 
  
The probability of any reaction (Pv) taking place at a given time is calculated with the equation shown in the figure No. 6
  
This another relation is used in order to determine which reaction will occur, by the definition of a random number (r1), shown in the figure No. 6
  
Another random number (r2) is generated to determine the time interval (t) between two consecutive reactions. The time step is related to the inverse of the total stochastic rates and the natural logarithmic of r2 according to the equation, shown in the figure No 6.
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/1fa3a21f0ecbfd9843dadf0012c2385d17d65247/Imagens/6.png"  width=500 height=350 /><center>
  
                                          Figure No. 6 Probability definition

where: Rv is the reaction rate of vth reaction. Mu is the number of the selected reaction type and r1 is a random number distributed uniformly in the interval
[0, 1].

According to the definition and the aims for this paper, the upper and lower limits for v are 5 and 1.
  
This whole definition written on Python is shown in the figure No. 7.
  
<center><img src="https://github.com/amandalemette/EQM2109/blob/a58b83cdff9ab6fa0ffc2d724f25ee9c64bf15ee/Imagens/7.png"  width=1000 height=350 /><center>
  
                                          Figure No. 7 Setting the probability model on Python 
  
## Results:
  
No results for the aimed properties (the monomer conversion, the polydispersity and the complete molecular weight distribution) were obtained as the simulation based on Monte Carlo did not run properly. 

## Discussion:

## References: 

Chemistry LibreTexts. 2021. 2.11: Living Radical Polymerization- ATRP. [online] Available at: <https://chem.libretexts.org/Bookshelves/Organic_Chemistry/Book%3A_Polymer_Chemistry_(Schaller)/02%3A_Synthetic_Methods_in_Polymer_Chemistry/2.11%3A_Living_Radical_Polymerization-_ATRP> [Accessed 11 December 2021].

Harrison, R., Granja, C. and Leroy, C., 2021. Introduction to Monte Carlo Simulation. [online] NCBI Resources. Available at: <https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2924739/> [Accessed 11 December 2021].

Purkait, M., Sinha, M., Mondal, P. and Singh, R., 2021. Temperature-Responsive Membranes. [online] ScienceDirect. Available at: <https://www.sciencedirect.com/topics/chemistry/atom-transfer-radical-polymerization> [Accessed 11 December 2021].
