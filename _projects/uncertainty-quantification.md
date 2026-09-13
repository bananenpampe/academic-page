---
layout: page
title: Uncertainty quantification
description: Fast, propagatable uncertainty estimates for machine learning interatomic potentials.
img: assets/img/PET_UAFD_thumb.png
importance: 1
github: https://github.com/bananenpampe/DPOSE
related_publications: true
giscus_comments: true
---

I work actively on uncertainty quantification (UQ) schemes for machine learning interatomic potentials (MLIPs).

I have developed the **shallow ensembles** scheme for neural networks: a fast, last-layer ensemble-based UQ scheme for neural-network MLIPs that yields fast yet high-quality uncertainty estimates. Because the ensemble lives only in the last layer, its uncertainties can easily be propagated through arbitrarily complex simulation workflows with very little computational overhead {% cite kellner2024uncertainty %}. A follow-up work discusses how to train such ensembles well {% cite schafer2026train %}.

More recently, we developed the **PET-UAFD / PET-EXP** scheme, the first universal machine learning potentials of their kind, whose predictions are calibrated against experiment and which yield uncertainty estimates not with respect to DFT but with respect to experiment {% cite kellner2026errors %}.

UQ schemes will make physical simulations with ML surrogate models more trustworthy. They also enable a better trade-off between more accurate and faster simulations, balancing the various error sources in atomistic simulations.

The supplementary code and data for the shallow ensemble paper are available on [GitHub](https://github.com/bananenpampe/DPOSE).
