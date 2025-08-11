# pvl-stats

This repo contains code for analyzing the SIV Studies database. pvl-stats.Rmd has functions for computing various SIV pVL outcomes and produces a df, as well as this figureset:

<img width="5400" height="4800" alt="27537" src="https://github.com/user-attachments/assets/1fa74b9d-13b5-46eb-b0b1-b1d5f83ed4f3" />

The computed stats are:

**Chronic Phase Setpoint**
Computes the geometric mean of PVLs from 8-16 weeks post-infection, and also tries to do the same within the ART window if there is one. Currently there isn't any extra filtering to take into account the derivative within the ranges for computing setpoint, but we could consider adding one per GW's feedback in the spec document.

**Acute Phase Peak**
Flags the maximum pVL value within the first X days of the data.

**On ART Blip Frequency**
Flags values above LOD within the ART window.

**Time to Rebound**
Computes several columns for how many days after ART release it took to detect pVL > 0, 100, or 1000.

**Post Rebound Setpoint**
Does the geometric mean calculation for ChronicPhaseSetpoint, but in the post-ART window, with a configurable # of days buffer before running the calculation.

**Acute Phase Burden**
Computes the area under the curve of pVL within the first X days of the data.
