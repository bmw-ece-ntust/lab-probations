---
title: OSC O-DU High Overview

---

![](https://i.imgur.com/JORnn3y.png =150x)@NTUST

# O-DU Low Overview
>[name=Ravi][color=#38c16a]

:::success
Goal: 
* Understand the functionality, Architecture and purpose of OSC DU Low.
* Integartion of DU-low.
* Performance measurement.

:::

:::info
#### :memo: **Outline:**
[TOC]
:::

:::success
The O-DU Low (Open Distributed Unit - Low) is a key part of the O-RAN architecture, responsible for real-time PHY processing and interfacing with the O-RU (Open Radio Unit). It is designed to handle high-performance, low-latency processing at Layer 1 (L1) of the protocol stack.
:::

2. O-DU Low Responsibilities

* High-PHY (Layer 1) Processing
* Fast-Fourier Transform (FFT) / Inverse FFT (IFFT)
* Channel estimation & equalization
* Beamforming (Massive MIMO)
* Forward Error Correction (FEC)
* Fronthaul Interface Handling
* Uses Split 7.2 Open Fronthaul to connect to O-RU.
* Supports eCPRI (Ethernet-based fronthaul).
* Synchronization & Timing
* GPS/PTP-based timing for 5G synchronization.
* FAPI/N-FAPI (MAC-PHY Interface)
* Communicates with O-DU High via FAPI/nFAPI.
* MIB & SIB Transmission
* Ensures proper MIB (Master Information Block) scheduling in DL_TTI.request.

#### The L1 has three interfaces to communicate with other network functions as described below:

* Interface between L1 and Front Haul, it adopts the WG4 specification for the CUS plane communication.

* Interface between O-DU Low and O-DU High, it adopts the FAPI interface according to the WG8 AAL specification.

* Interface between O-DU Low and accelerator, DPDK BBDev was adopted as original contribution, it will follow the WG6 definition after the WG6 specification is finalized.


The following figure shows the ORAN O-CU, O-DU and O-RU blocks for a gNB implemetation. 

![image](https://hackmd.io/_uploads/HJKDC0FF1e.png)

 * The O-DU Low projects implements the FAPI interface by a 5G FAPI TM module.
 * 
