---
layout: post
title: "Introducing Monte Carlo from Metropolis"  
author: Jefy Jeffy 
--- 

Today's lecture was titled Monte Carlo for a Lennard Jones Fluid - Part 2. The lecture reintroduced Monte Carlo for Molecular systems and the general idea behind how the calculations are conducted. Next, we discussed the importance of sampling and how the Metropolis algorithm is utilized in Monte Carlo calculations to include meaningful configurations. The group discussion revolved around the topic of utilizing smart algorithm choices, and the importance of radial distribution function. 

The Monte Carlo simulation is typically conducted in molecular systems to gain better information about the structure and the energy profile of the sytem, in the simplest of terms. It is also often very useful in predicting possible outcomes of a sytem under certain thermodynamic factors, such temperature, pressure, volume and so on. In statistical mechanics, Monte Carlo simulation is conducted by solving an integral which is hard (read: impossible) to evaluate analytically. Monte Carlo solves this integral by sampling a subset of configuration and comparing the energy of the sample subset to the average of all the subsets. 

Although theoretically, Monte Carlo simulation can be evaluated as mentioned above; however, it is crucial to generate contributions that are probable that contribute to the energy of the system or else, the algroithm ineffecient evaluating contributions that are unlikely. Thus, Metropolis algorithm is utilized to solve this problem and identify configurations that will be accepted. 

The Metropolis algorithm works in the following steps: 
1. Create an initial state which has the enrgy m. 
2. Move one random particle within the system. The particle must be something that has a uniform probability of being chosen. 
3. Calculate the energy of the new system and calculate the difference between the old energy and the new energ. 
4. Based on the delta_energy, the Metropolis criterion will determine if the new configuration is an "accepted" configuration. 

The criteria in this case is as follows: If the difference in energy is negative then the configuration is accepted; however, if it is positive, then the probability of the configuration being accepted: (e^(-delta_energy/T)) must be greater than a random probability for it to be accepted. Through the assignment portion, I noted that as the temperature increases, the probability of the positive delta_energy to be accepted as move increases. This was surprising to me as themodynamically, as the temperature increases, the potentially energy of the particle also increases. This leads me to believe that although Metropolis Monte Carlo is an efficient, it does not entirely take into account high energy scenarios. 

The group discussion was emphasized on the radial distribution function (RDF) which shows the distribution of the number of particles from a particle of interest as a function of distance. It was noted that solid has a more consstent RDF plot as the particles are more consistently packed, meanwhile the graphs for liquid and gases are fluctuate much less and eventually converge to 1 due to diffusion as the particle gets further away from each other. 

All in all, this has been a really interesting lecture and I have really enjoyed learning about the different methods that are used to enhance the algorithm for Monte Carlo. It really just makes me wonder how did people in like 1900s did this?! 