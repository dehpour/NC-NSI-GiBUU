# NC-NSI-GiBUU

This repo was based on [GiBUU](https://gibuu.hepforge.org/), but we implied some modifications to take into account the Neutral Current (NC) Non-Standard Interaction (NSI) for now, only in the Quasi-Elastic (QE) and $\Delta$ resonance production regimes yet. For Deep Inelastic Scattering (DIS) regime one can look at [NC-NSI-DIS](https://github.com/dehpour/NC-NSI-DIS) ([arXiv:2312.12420](http://arxiv.org/abs/2312.12420)).

## Install

First, make sure you have all [prerequisites](https://gibuu.hepforge.org/trac/wiki/tools) (in addition to them we used `python3` with `numpy`, `scipy` and `matplotlib` libs), then [get main GiBUU](https://gibuu.hepforge.org/trac/wiki/download). Finaly, download and overwrite this repo in the same dir. Then, [compile](https://gibuu.hepforge.org/trac/wiki/compiling) and [use](https://gibuu.hepforge.org/trac/wiki/running).

## Changes

All additional parameters to namelists are listed in `GiBUU/release/namelist.pdf`.

### NC NSI in QE scattering

We implemented the possibility of investigation of NC NSI in QE scattering by modification of `GiBUU/release/code/init/lepton/formfactors_QE_nucleon/FF_QE_nucleonScattering.f90`.

Note that we don't take into account NSI in `axialMonopole` yet, so please don't turn it on when work within NSI.

### NC NSI in $\Delta$ Res. production

We implemented the possibility of investigation of NC NSI in QE scattering by modification of `GiBUU/release/code/init/lepton/formfactors_QE_nucleon/FF_Delta_production.f90`.

We have to switch to different realizations of the matrix elements to use only $\Delta$ Res.  production by adding `which_resonanceModel = 1` in the `neutrino_matrixelement` namelist. Also, we fixed interactions charges in `GiBUU/release/code/init/neutrino/NeutrinoMatrixElement.f90` for take into account antineutrinos too.

## Example

In the presence of NSI, as our detectors cannot distinguish the final flavor, for example by the assumption of the incoming muon neutrino, we should calculate

$$
\sigma_{\rm SM+NSI}^{\mu}=\sigma_{\rm NSI}^{\mu e}+\sigma_{\rm SM+NSI}^{\mu \mu}+\sigma_{\rm NSI}^{\mu \tau}.
$$

We have `005_Neutrino_NC_NSI.job` in `GiBUU/release/testRun/jobCards` to do it. By default after installing, it uses SM only however e.g. by turning on `justSMpNSImumu` in `ff_QE` for QE scattering and/or in `input_FF_Delta` for $\Delta$ Res. production (it depends what you want include) with specific NSI params. which can be define in the same file, you can calc $\sigma_{\rm SM+NSI}^{\mu \mu}$, etc.

## Cite

If you do use anything here please cite [arXiv:24xx.xxxxx](http://arxiv.org/abs/24xx.xxxxx) with the following BibTex info

```
@article{
}
```
