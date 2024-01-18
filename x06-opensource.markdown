---
layout: page
title: Open Source
permalink: /opensource/
---

## CubeSat Antenna

The CubeSat Antenna is a half wavelength deplyable tape dipole that was originally designed to be the TT&C antenna on [ORCASat](https://orcasat.ca). The antenna is designed to interface with PC104 compliant baords using a reduced size header to simplify assembly. It was built and tuned in-house at the University of Victoria anechoic chamber, achieving a VSWR of 1.02:1 and an antenna efficiency of 95%. In-depth testing and characterization was conducted by the [Antenna Test Lab](https://antennatestlab.com/) and final verification was done at the Canadian Space Agency David Florida Laboratory [ATF2 facility](https://www.asc-csa.gc.ca/eng/laboratories-and-warehouse/david-florida/facilities/radio-frequency-qualification.asp).

![ORCASat Antenna Picutre](/assets/img/ORCASat-ant.jpg)

Mechanical and electrical files for the CubeSat Antenna can be found on our [GitLab repo](https://gitlab.orcasat.ca/orcasat-group/orcasat-antenna).

## Modular CubeSat Radio

The Modular CubeSat Radio is an open source SDR, based on the [Hermes Lite 2](http://www.hermeslite.com/), that is being developed for the Skya'anaSat project. It is a modular radio design which aims to provide access to all amateur-satellite allocations while being accessible to the average hobbyist. There are amateur-satellite frequency allocations up to 250 GHz but the highest frequency amateur satellite only goes up to ~10 GHz with the transponder on QO-100. The Modular CubeSat Radio project hopes to provide a design that can be easily expanded on using modules that handle frequency conversion. It will be developed with HF and VHF RF modules with higher frequency bands being left for future projects or community designs.

Note: The GitLab repo for the Modular CubeSat Radio will be added here once development is completed.