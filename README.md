## Applying Rare Event Sampling to the Planet Simulator (PlaSim) 

This research applies a rare event algorithm which uses cloning and killing  algorithm(more below) to force the system towards a collapsed state. The algorithm is applied to the coupled Global Climate Model (GCM) of intermediate complexity, PlaSim, to allow for improved accuracy of results as compared to the Gottwald model, but to save on computational cost when compared with other models.

A control simulation with a spin-up of 1000 years is initialized with a total of 2000 years, and one random point from the run is chosen to continue a simulation of an ensemble of 100 trajectories. Running this ensemble with an initial kick at the first timepoint results in stochastic forcing of the system, allowing the trajectories to spread. The standard deviation of the AMOC index of the trajectories is taken, and when the system has lost memory over time, this may be taken as the resampling time.

An ensemble of trajectories is initiated taking 100 stationary states of PlaSim from the control run after its spin-up has completed. At resampling intervals, the rare event algorithm is applied. 

So far results are that seasonal cycle prevents importance sampling from working.

Plasim sits in the middle of Dijkstra's hierarchy of models \cite{dijkstra2024role}. an Earth System Model of Intermediate Complexity. This model consists of a dynamical core based on the moist primitive equations representing conservation of momentum, mass and energy, which has been adapted from a simplified general circulation model, the Portable University Model of the Atmosphere (PUMA) \cite{fraedrich2005planet}. This has been coupled with systems of lower complexity including land-surface processes, vegetation, ocean and sea ice \cite{fraedrich2005planet}. Our version of PLASIM has included an additional functionality of the large-scale geostrophic ocean, which has been implemented by J Hardenberg (need to find a paper for this) (Can also add the parameters chosen). How much resolution? how many dimensions? How much scale?

Plasim sits in the middle of Dijkstra's hierarchy of models \cite{dijkstra2024role}. an Earth System Model of Intermediate Complexity. This model consists of a dynamical core based on the moist primitive equations representing conservation of momentum, mass and energy, which has been adapted from a simplified general circulation model, the Portable University Model of the Atmosphere (PUMA) \cite{fraedrich2005planet}. This has been coupled with systems of lower complexity including land-surface processes, vegetation, ocean and sea ice \cite{fraedrich2005planet}. Our version of PLASIM has included an additional functionality of the large-scale geostrophic ocean, which has been implemented by J Hardenberg

TODO: Read up on PLASIM
- quantify general description
- specifications of my run (10 atmospheric layers, etc.)
- inputs and outputs, parameterized inputs, etc etc
- AMOC overturning, how it's calculated - looking at one specific region - SPG
- Describe RE algorithm again, put graphs of AMOC spread and calculations of resampling time, AC time

- Have transition already with Matteo's k value, add mine

- Next two steps (if transitions are found) is checking on mass balance flux as a result of the transition (a marker of the edge state), and checking locations which are important for monitoring transitions (and seeing if they match up with the locations of R-tipping) read paper of Emma

- May need to integrate 200 years to get transition

