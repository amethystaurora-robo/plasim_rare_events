# Applying Rare Event Sampling to the Planet Simulator (PlaSim) 
## Introduction

PlaSim-LSG is an Earth System Model of Intermediate Complexity (EMIC). It
has been based on a simplified general circulation model, the Portable University
Model of the Atmosphere (PUMA) [1,2] which contains a spectral dynamical
core based on the moist primitive equations. This has been coupled with systems
of lower complexity including land-surface processes, vegetation, and sea ice
[1]. PlaSim has then been coupled with the large-scale geostrophic (LSG)
ocean [3], following parameters selected in [4]. The added LSG component
better simulates centennial AMOC variability which is influenced by geostrophic
changes [2]. The selection of PlaSim-LSG for this project is based on its proven
ability to model noise-induced transitions in the AMOC, as concluded in [4].

## Methods
The PlaSim-LSG simulations continue the conclusions of [4], with the application of a rare event algorithm to induce N-tipping. As such, parameters selected
for PlaSim-LSG follow those described in [4], where the resampling time of the
rare event algorithm is $T_a = 1$ year and biasing parameter is $k=−3$, with
PlaSim-LSG been configured with a T21 resolution and with 10 vertical layers.
The strength of the overturning of the AMOC is measured in Sverdrups (Sv),
with 1 Sverdrup equalling 1 million cubic meters per second, where the average
flow in higher latitudes is about 17.0 Sv [2], and the threshold of collapse in
this study is 10.0 Sv. Simulations of PlaSim-LSG are conducted on the high-
performance computing service, running 10 trajectories in parallel to improve
the speed of the model. A control run of 2000 years was initiated, where the
first 1000 years were discarded as a transient period. Snapshots of the full system state were selected at evenly spaced intervals in the control run, and used
as initial conditions of the 100-member ensemble. The model was integrated
for 143 years, following the transitions observed in [4] from 50-100 years. The
weighting function of the rare event algorithm was applied to the AMOC index
at each resampling time, with the small random perturbation added to the sea
level pressure as described in [4].
To improve predictability of a transition, the edge state was investigated
following conclusions from [5], where the edge state is characterised by an
increase in gravitational potential energy. As an initial look into the edge state,
the global energy budget during the collapse of the AMOC was investigated, by
calculating radiative fluxes at the top of the atmosphere and at the surface, to
demonstrate redistribution of energy within the climate system as a result of
AMOC collapse.
The energy budget at the top of the atmosphere is calculated as follows:
```math
toa= rst + rlut 
```
where $rst$ is the total solar radiation flux and $rlut$ is the thermal radiation
upward, a negative value by default in PlaSim-LSG.

The energy budget at the surface is calculated as:
```math
surf= rss + rls + hfls + hfss
```
where $rss$ is the total solar radiation flux, $rls$ is the total thermal radiation
flux, $hfls$ is the latent heat flux and $hfss$ is the sensible heat flux. Outward
radiation is negative by default in PlaSim-LSG.

## Results
The experiment of [4] was reproduced, resulting in a transition from the AMOC
on to the off state in a 100-member ensemble integrated for 143 years. The rare
event algorithm is applied at each resampling step of 1 year, with a small random
perturbation applied to sea level pressure, and a collapse found by Year 100,
with the timeseries shown in Figure 1.

<p>
  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/AMOC_k100.png" width="400" >
</p>
Figure 1: A 143-year time series of the AMOC index is shown, with a clear
transition around Year 100.

Radiative fluxes at the top of the atmosphere in PlaSim-LSG consist of solar
flux and upward thermal radiation. The solar flux shown in Figure 2a shows
a slight decrease in radiation around the transition period, meaning that the
average temperature of the Earth is decreasing at the top of the atmosphere
after the AMOC transition. This is in line with the literature, which predicts
a colder Northern Hemisphere on average after AMOC collapse. The upward
thermal radiation at the top of the atmosphere shown in Figure 2b decreases
slightly, which may point to a change in cloud and/or sea ice cover, a topic which
should be investigated in the next phase of this study. The combined energy
budget shown in Figure 2c does not show a noticeable change in the transition
period, meaning that radiative equilibrium is maintained. In the early portion
of the timeseries in Figures 2a and 2c, there are noticeable spikes in radiative flux, which can also be seen in the energy budget. These may also be worth
investigating in further studies.
<p>
 a) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_rss.png" width="400" >
 b)  <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_rst.png" width="400" >
</p><p>
 c)   <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/energy_budget_toa.png" width="400" >
</p>

Figure 2: A comparison of total solar radiation flux and thermal radiation
upward during the collapse simulation (a-b). The energy budget at the top of
the atmosphere shown over time (c).

The spatially distributed change in radiative fluxes at the top of the atmo-
sphere is shown in Figure 3, where the total change has been calculated as
the difference between variables before the transition in Year 2, and after the
transition in Year 100. Each plot shows significant radiative increases on the
west coast of Greenland, an area which will be a focal point in future analyses.
<p>
  a) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/difference_rss.png" width="400" >
  b) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/difference_rst.png" width="400" >
</p>
<p>
  c) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/difference_total_toa.png" width="400" >
</p>
Figure 3: The total change in global radiation fluxes at the top of the atmo-
sphere, including the incoming short-wave solar flux (a), the upward thermal
radiative change (b), and the change in energy budget (c), with warmer colors
representing radiative increases and cooler colors representing decreases.

Radiative fluxes at the surface consist of the total solar flux, total thermal
flux, and sensible and latent heat exchanges. Figure 4b represents a surprising
result of the transition, where upward thermal radiation increases after the
transition, meaning that either the emission of the ocean is increasing or the
emission of the atmosphere is decreasing. The latent heat flux in Figure 4c
shows a decrease in evaporation, whereas the sensible heat flux in Figure 4d
shows a slight increase in energy transfer due to temperature differences between
the atmosphere and the ocean.

<p>
  a) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_hfls.png" width="400" >
  b) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_hfss.png" width="400" >
</p>
<p>
 c) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_rls.png" width="400" >
 d) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/mean_rlut.png" width="400" >
</p>
<p>
  e) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/energy_budget_surf.png" width="400" >
</p>
Figure 4: A comparison of total solar radiation flux, thermal radiation flux,
latent heat flux, and sensible heat flux during the collapse simulation (a-d). The
energy budget at the surface shown over time (e).

The spatially distributed changes in radiative fluxes at the surface before
and after the transition from the AMOC on to the AMOC off state are shown
in Figure 5, where there is a noticeable increase in radiation off the west coast
of Greenland, and a slight increase in incoming solar radiation around the Gulf
of Mexico, shown in Figure 5a.
<p>
  a) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/difference_rlut.png" width="400" >
  b) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/difference_rls.png" width="400" >
</p>
<p>
  c) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/difference_hfss.png" width="400" >
  d) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/difference_hfls.png" width="400" >
</p>
<p>
  e) <img src="https://github.com/amethystaurora-robo/plasim_rare_events/blob/main/graphs/difference_total_surf.png" width="400" >
</p>
Figure 5: The total change in global radiation fluxes at the Earth’s surface,
including the incoming short-wave solar flux (a), the upward thermal radiative
change (b), the change in latent heat exchange (c), sensible heat exchange (d),
and the total change in the surface energy budget (d), with warmer colors
representing radiative increases and cooler colors representing decreases.

## References
1. Klaus F Fraedrich et al. “The Planet Simulator: Towards a user friendly model”. In: Meteorologische Zeitschrift 14.3 (2005), pp. 299–304.
2. Oliver Mehling et al. “High-latitude precipitation as a driver of multi-centennial variability of the AMOC in a climate model of intermediate complexity”. In: Climate Dynamics 61.3 (2023), pp. 1519–1534.
3. Bit Shifter, Jost Von Hardenberg, Hartmut Borth, et al. “jhardenberg/PLASIM:Plasim-LSG TNG”. In: Zenodo (2020).
4. Matteo Cini et al. “Simulating AMOC tipping driven by internal climate variability with a rare event algorithm”. In: npj Climate and Atmospheric Science 7.1 (2024), p. 31.
5. Johannes Lohmann and Valerio Lucarini. “Melancholia states of the Atlantic meridional overturning circulation”. In: arXiv preprint arXiv:2405.13988 (2024).


