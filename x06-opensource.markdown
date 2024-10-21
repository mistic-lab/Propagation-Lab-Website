---
layout: page
title: Open Source
permalink: /opensource/
---

## Overview

The Propagation Laboratory, along with its partners, is an active player in the open access community, with a heavy focus on Amateur radio projects. This page summarizes the key contributions in this area. Pretty much all of these are related to the Amateur-satellite service in one way or another, as one key area of activity by the Laboratory is the use of Amateur satellite work, and hardware and software development related to this as an vehicle to train students in STEM, and especially in areas realted to radio communcations. 

## Modular CubeSat Radio

The Modular CubeSat Radio is an open source SDR, based on the [Hermes Lite 2](http://www.hermeslite.com/), that is being developed for the Skya'anaSat project. It is a modular radio design which aims to provide access to all Amateur-satellite allocations while being accessible to the average hobbyist. There are Amateur-satellite frequency allocations up to 250 GHz but the highest frequency Amateur satellite only goes up to ~10 GHz with the transponder on QO-100. The Modular CubeSat Radio project hopes to provide a design that can be easily expanded on using modules that handle frequency conversion. It will be developed with HF and VHF RF modules with higher frequency bands being left for future projects or community designs.

The GitLab repo for the Modular CubeSat Radio is hosted by CFAR [here](https://gitlab.orcasat.ca/open-source-projects/mcr).

## Flight Tested CubeSat Antenna

The CubeSat Antenna is a half wavelength deplyable tape dipole that was originally designed to be the TT&C antenna on [ORCASat](https://orcasat.ca). The antenna is designed to interface with PC104 compliant boards using a reduced size header to simplify assembly. It was built and tuned in-house at the University of Victoria anechoic chamber, achieving a VSWR of 1.02:1 and an antenna efficiency of 95%. In-depth testing and characterization was conducted by the [Antenna Test Lab](https://antennatestlab.com/) and final verification was done at the Canadian Space Agency David Florida Laboratory [ATF2 facility](https://www.asc-csa.gc.ca/eng/laboratories-and-warehouse/david-florida/facilities/radio-frequency-qualification.asp).

Mechanical and electrical files for the CubeSat Antenna can be found on CFAR's [GitLab repo](https://gitlab.orcasat.ca/orcasat-group/orcasat-antenna).

## Satellite Station Cross Boom

The [CB-11 cross boom](https://www.m2inc.com/FGCB60), purchased from M2 Antenna Systems, was used as part of the our Amateur satellite  station to hold up both our circularly polarized Yagis. It is mounted on an antenna rotator at the top of an antenna tower. This commercial product was reinforced by producing a longer centre section, as well as Delrin inserts to help the fibreglass rods support out antennas. It is based on the work of AB1OC and W2SW found [here](https://stationproject.blog/2019/01/01/sat40-part-2-antennas/).

Mechanical drawings can be found on CFAR's [GitLab repo](https://gitlab.orcasat.ca/orcasat-group/ground-station-crossboom).

