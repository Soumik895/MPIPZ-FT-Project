# Stochastic Modelling of FT Gene Transcription Bursts

This repository contains Python scripts for the stochastic simulation of transcriptional bursting of the **FLOWERING LOCUS T (FT)** gene. This work is a computational approach to the project proposal from the **Max Planck Institute for Plant Breeding Research (MPIPZ)**.

The core hypothesis is that the deletion of two distal enhancers for the FT gene does not affect the duration of transcription bursts, but instead **lengthens the refractory (inactive) time** between bursts.

The models in this repository are built to test this hypothesis by comparing simulations of a **"wild-type" (4-state)** and **"mutant" (2-state)** system.

## 1. The Models

All simulations are implemented using the **Gillespie Stochastic Simulation Algorithm (SSA)**. This algorithm stochastically determines which reaction (e.g., "gene turns on," "mRNA is made") will occur next and the random time interval that passes before it happens.

**Model A**: `gillespie_4state.ipynb` **(Wild-Type Plant)**

This script models the FT promoter as a four-state system, representing a wild-type plant where both enhancers are active.

* **State 0: Refractory (OFF)**

Gene is silenced by repressive chromatin. Transcription rate is `0`.

* **State 1: Enhancer 1 Active (ON)**

Transcription occurs at rate $k_{enh1}$.

 * **State 2: Enhancer 2 Active (ON)**

Transcription occurs at rate $k_{enh2}$.

* **State 3: Both Enhancers Active (ON)**

Transcription occurs at a synergistic rate $k_{both}$.

**Model B**: `gillespie_2state.ipynb` **(Enhancer-Deletion Mutant)**

This script provides a simpler, foundational model representing the enhancer-deletion mutant.

* **State 0: Refractory (OFF)**

The long, inactive "refractory" period.

* **State 1: Active (ON)**

The bursting state.

By comparing the outputs of these two models (specifically the time spent in the 'Refractory' state), we can directly simulate the effect of the enhancer deletion.


## 2. Project Context

This code was developed as part of a Statement of Purpose for the MPIPZ - IISERs Master Internship Proposal titled "Stochastic modelling of the transcription bursts of FLOWERING LOCUS T in Arabidopsis thaliana." The goal is to use these models as a starting point to find parameters that can recapitulate the experimental snRNAseq data provided by the lab.
