---
layout: page
title: Satellite
permalink: /satellite/
---
## TT&C Information

Small satellites built and operated by partnership comprised of the UVic Propagation Laboratory, the UVic Centre for Aerospace Research, and UVic Satellite Design all use the same telemetry format, based on the [Open LST](https://github.com/OpenLST/openlst) project . Information which is required for reception can be found below.

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

## Satellite Specific Information

### Skya’anaSat

Skya’anatSat is currently under development. It is slated to launch in 2025 to SSO, carrying a Mode A transponder, a CW telemetry beacon, a DVB-S2 video beacon on 10 m, and an ionospheric sounding experiment. It will use UHF amateur spectrum for TT&C.

#### TT&C

- Antenna: Half-wave in-house dipole
- Radio: In-house half duplex UHF transceiver based on Open LST
- Service area: When above 15 degrees elevation, as observed Victoria , BC

#### Amateur Payload

- Antennas: In house, configuration TBD
- Radio: In house SDR based on the [Hermes Lite 2](http://www.hermeslite.com/)
- Service area: Global

### ORCASat

This section is maintained for legacy purposes.
- Antenna: Half-wave in-house dipole
- Radio: In-house half duplex UHF transceiver based on Open LST
- Service area: When above 15 degrees elevation, as observed Victoria , BC

Please note that the spacecraft only transmits when prompted by its control station in Victoria, BC, Canada. All uplink commands are encrypted, and amateur radio operators do not have the ability to upload commands to the spacecraft, or prompt it to transmit telemetry on demand.