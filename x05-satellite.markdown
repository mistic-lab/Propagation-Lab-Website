---
layout: page
title: Satellite
permalink: /satellite/
---

## Overview

The Propagation Laboratory is actively involved in Amateur satellite development, especially student training and open access software and harware work related to this area. Combining Amateur radio with satellite development is an excellent learning opportunity for engineering students at the University of Victoria. This page captures the information which is required for any Amateur to interact with orbiting satellites which the Propagation Laboratory contributed to. Should there by any missing information, Amateurs are encouraged to [contact us](https://www.propagationlab.ca/contact/) so we can properly amend this page. 

## Satellite Specific Information

<!-- ### Skya’anaSat

Skya’anatSat is currently under development. It is slated to launch in 2026 Q2 to SSO, carrying a VHF digipeater, a CW telemetry beacon, a DVB-S2 video beacon on 10 m, and an ionospheric sounding experiment with a citizen science aspect. It will also use UHF Amateur spectrum for TT&C. Amateurs are encouraged to be involved in this mission via participation in the above mentioned experiments. Information on these will be added to this page as it becomes available. 

#### Amateur Payload

The Amateur payload is available to be used by all interested and propely licensed parties, gobally. The schedule of experiments will be posted here at a later time. The Amateur payload is the debut of the [Modular CubeSat Radio](https://www.propagationlab.ca/opensource/), featuring the components necessary to faciliate the Amateur radio and ionoshperic science experiments. These are the core consisting of the SDR, computer and camera, as wel as HF and VHF RF front ends.

- HF antenna: Base loaded 1/4 wave whip for 10m
- VHF antenna: In house, half wave dipole
- Radio: In house low power HF SDR based on the [Hermes Lite 2](http://www.hermeslite.com/)
- HF RF front end: In house HF amplifier
- VHF RF front end" In house VHF transverter
- Emission: Designators TBD, LFM radar sweep, 15 WPM CW, Greencube style packet, DVB-S2 (QPSK, 0.35 roll off, 66kBaud, 1/2 rate FEC with normal block length and pilot symbols)
- Service Area: Global

#### TT&C

Please note that the spacecraft only transmits TT&C when prompted by its control station in Victoria, BC, Canada. All uplink commands are encrypted, and Amateur radio operators do not have the ability to upload commands to the spacecraft, or prompt it to transmit UHF telemetry on demand. Using the information on this page, however, it is possible to observe, record and decode the downlink traffic between this satellite and the UVic control station.

- Control station: VE7UVG
- Phisically separate RF chain from Amateur payload, based on hertiage from ORCASat
- Antenna: Half-wave in-house dipole
- Radio: In-house half duplex UHF transceiver based on Planet's [Open LST](https://github.com/OpenLST/openlst)
- Emission: Designator 25K0F1DBN, uncoded 2-FSK with PN9 whitening, 10.17 kbps rate, 6.18 kHz deviation
- Service Area: When above 15 degrees elevation, as observed Victoria , BC
 -->

### ORCASat

ORCASat was a 2U CubeSat, with a mission of HQP traning. This section is maintained for legacy purposes. ORCASat has deorbited in July 2023. Please note that the spacecraft only transmits when prompted by its control station in Victoria, BC, Canada. All uplink commands are encrypted, and Amateur radio operators do not have the ability to upload commands to the spacecraft, or prompt it to transmit telemetry on demand. Using the information on this page, however, it is possible to observe, record and decode the downlink traffic between this satellite and the UVic control station.


- Control station: VE7UVG
- Antenna: Half-wave in-house dipole, port/starboard side
- Radio: In-house half duplex UHF transceiver based on Planet's [Open LST](https://github.com/OpenLST/openlst)
- Emission: Designator 25K0F1DBN, uncoded 2-FSK with PN9 whitening, 10.17 kbps rate, 6.18 kHz deviation
- Service Area: When above 15 degrees elevation, as observed Victoria , BC

## Detailed TT&C Information

All the satellites on this page use the same telemetry format, based on the [Open LST](https://github.com/OpenLST/openlst) project. Protocol information which is required for decoding  can be found below.

## Telemetry Format

A packet radio scheme is used, with transmission format derived from what is used by the Open LST project, with variable payload length and structure based on the packet format natively supported by the Texas Instruments (TI) CC1110 transceiver. The default TI structure shown in Figure 51 on page 194 of the CC1110 [datasheet](https://www.ti.com/lit/gpn/cc1110-cc1111). Below is an explanation of what features of the default TI structure used, and what are omitted.

- The optional Address byte is not used.
- Variable packet length mode is employed where the Length field gives the length of the Data field (payload) in bytes. When operating with variable length packets, the radio will use the first byte in the packet to determine how many additional bytes it should expect to receive. The length of the variable packet is determined by the first byte in the Payload Message field, which happens to be the Length field of our packet above.
- The PKTLEN register is used to set the maximum packet length allowed in RX.
- The hardware CRC is also not used, instead it is implemented in software in the payload.

When a packet is received, the hardware packet handler will strip the packet down to the Payload Data only. This payload data is the packet with Length, flag and footer fields. This packet is again operated on and made into the original \| Hardware ID \| Seq_Num \| System \| Command \| Payload Message \| packet, that the radio command handler will recognize and so will the CDH team.

The resulting RF messaging communication protocol is shown below. Fields marked with "*" are sent LSB first.

| Length | Flag | Seq_Num | System | Command | Payload Message | Hardware ID | Software CRC |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 byte | 1 byte | 2 bytes* | 1 byte | 1 byte | N bytes | 2 bytes* | 2 bytes |