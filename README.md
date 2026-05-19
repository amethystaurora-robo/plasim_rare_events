# Applying Rare Event Sampling to the Planet Simulator (PlaSim) 
## Introduction
## Methods
## Results
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/AMOC_k100.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/energy_budget_surf.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/energy_budget_toa.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/energy_budget_surf_off.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/energy_budget_surf_on.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/energy_budget_toa_off.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/energy_budget_toa_on.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/lats_hfls.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/lats_hfls_off.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/lats_hfss.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/lats_hfss_off.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/lats_rls.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/lats_rls_off.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/lats_rlut.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/lats_rlut_off.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/Lats_rss.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/lats_rss_off.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/lats_rst.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/lats_rst_off.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_hfls.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_hfss.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_rls.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_rlut.png" width="500" >
</p><p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_rss.png" width="500" >
</p>
<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_rst.png" width="500" >
</p>

This repo applies a rare event algorithm to the coupled atmospheric-oceanic model of intermediate complexity PlaSim. The goals of this research are 
\enumerate
a. determining the edge state in PlaSim between on and off states of the AMOC
b. determining optimal locations and state variables to position optimal observations for an early warning system of AMOC collapse
c. refining the methodology used in Cini et al. to produce noise-induced transitions in PlaSim

A control simulation with a spin-up of 1000 years is initialized with a total of 2000 years, and one random point from the run is chosen to continue a simulation of an ensemble of 100 trajectories. Running this ensemble with an initial kick at the first timepoint results in stochastic forcing of the system, allowing the trajectories to spread. The standard deviation of the AMOC index of the trajectories is taken, and when the system has lost memory over time, this may be taken as the resampling time. Alternatively, determining the integral auto-correlation time gives nearly the same value, with a resulting resampling time of ~20 days. 

Although this is the most scientific way to calculate the resampling time, a resampling time of 20 days resulted in no transitions within 100 years. Based on previous research, we have already found transitions with a resampling time of 1 year, so we can continue with that value. In the future, I may try with different resampling times, and ks.

An ensemble of trajectories is initiated taking 100 stationary states of PlaSim from the control run after its spin-up has completed. At resampling intervals, the rare event algorithm is applied. 

Plasim sits at the middle of Dijkstra's hierarchy of models \cite{dijkstra2024role}. an Earth System Model of Intermediate Complexity. This model consists of a dynamical core based on the moist primitive equations representing conservation of momentum, mass and energy, which has been adapted from a simplified general circulation model, the Portable University Model of the Atmosphere (PUMA) \cite{fraedrich2005planet}. This has been coupled with systems of lower complexity including land-surface processes, vegetation, ocean and sea ice \cite{fraedrich2005planet}. Our version of PLASIM has included an additional functionality of the large-scale geostrophic ocean, which has been implemented by J Hardenberg.

The justification for selecting PLASIM as the specific EMIC is its proven ability to exhibit noise-induced tipping. Noise-induced transitions in PLASIM occur by beginning an ensemble of trajectories from different initial conditions, and adding a small random perturbation at each resampling step \cite{

This work builds on research conducted by Matteo Cini, by exploring more of the theoretical aspects of climate dynamics in PlaSim as opposed to physical causes of collapse.


- Next two steps is checking on radiation flux as a result of the transition (a marker of the edge state), and checking locations which are important for monitoring transitions (and seeing if they match up with the locations of R-tipping, which is the salinity in the southern Atlantic.
- Not sure how to do the second one, as we need to have an early warning indicator of noise-induced transitions first, unless the idea is to confirm with Plasim, not noise-induced.


