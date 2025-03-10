---
title: OSC DU integration

---

## OSC DU integration (Issue with UE not receiving MIB )

:::info
:bulb: 
:::

## :calendar: Date
:::success
Date format: 12-31-2024
:::

## :pencil2: Details
:::success
Goal:

* Understanding of the O-RAN SC's O-DU high.
* Understand the architecture modules and Interfcaces.
* Overview of O-DU High Test.
* Check The issue of MIB and SIB

Resources:
O-RAN SC's O-DU high deep dive
O-DU High instalation
O-DU High Test
O-RAN Software Community training course 
:::




### Check The issue of MIB and SIB


Cell Search Procedure-

Steps- 
* UE is off.
* UE Power ON.
* Scan For frequencies
    * SLS(Stored list Search)
    * DBS(Derived band search), Full band Search `UE search DBS if it doesn't find anything on SLS`

:::info
As SSB Postions is defined By 3GPP 5.4.3 Synchronization raster
:::
ref- 

5.4.3.1	Synchronization raster and numbering

* The synchronization raster indicates the frequency positions of the synchronization block that can be used by the UE for system acquisition when explicit signalling of the synchronization block position is not present.
* A global synchronization raster is defined for all frequencies. The frequency position of the SS block is defined as SSREF with corresponding number GSCN. The parameters defining the SSREF and GSCN for all the frequency ranges are in table 5.4.3.1-1.
* The resource element corresponding to the SS block reference frequency SSREF is given in clause 5.4.3.2. The synchronization raster and the subcarrier spacing of the synchronization block is defined separately for each band.
* For NR V2X, the synchronization raster is not defined.
Table 5.4.3.1-1: GSCN parameters for the global frequency raster
Range of frequencies (MHz)	SS block frequency position SSREF	GSCN	Range of GSCN

| **Frequency Range (MHz)** | **SS Block Frequency Position (SSREF)**                                   | **GSCN Formula**                             | **Range of GSCN**    |
|---------------------------|---------------------------------------------------------------------------|----------------------------------------------|----------------------|
| **0 – 3000 MHz**           | `N * 1200 kHz + M * 50 kHz,` where `N = 1:2499`, `M ∈ {1, 3, 5}`         | `3N + (M - 3) / 2`                          | **2 – 7498**         |
| **3000 – 24250 MHz**       | `3000 MHz + N * 1.44 MHz,` where `N = 0:14756`                           | `7499 + N`                                   | **7499 – 22255**     |
| **24250 – 100000 MHz**     | `24250.08 MHz + N * 17.28 MHz,` where `N = 0:4383`                       | `22256 + N`                                  | **22256 – 26639**    |



To understand and Calculate SSB positions

 (SSREF) is given by:
:::success

1- For the range 0 – 3000 MHz, the SS block frequency position

![image](https://hackmd.io/_uploads/B1oT3BZIJe.png)

:::
2- For the range 3000 MHz – 24250 MHz, the SS block frequency position (SSREF) is:
:::success
![image](https://hackmd.io/_uploads/SkmW6rZUyx.png)
:::
3-For the range 24250 MHz – 100000 MHz, the SS block frequency position (SSREF) is:
:::success

![image](https://hackmd.io/_uploads/ryqBprWLkx.png)

:::





As I check Logs from

![image](https://hackmd.io/_uploads/Hkpgtrb8kx.png)
 
 And 
 
 ![image](https://hackmd.io/_uploads/H1VQFHWIJe.png)


```
FrequencyInfoDL ::=                 SEQUENCE {

    absoluteFrequencySSB               ARFCN-ValueNR,

    ssb-SubcarrierOffset               INTEGER (1..23)  OPTIONAL,   -- Need S

    frequencyBandList                  MultiFrequencyBandListNR,

    absoluteFrequencyPointA            ARFCN-ValueNR,

    scs-SpecificCarrierList            SEQUENCE (SIZE (1..maxSCSs)) OF SCS-SpecificCarrier,

    ...

}

 

SCS-SpecificCarrier ::=         SEQUENCE {

    offsetToCarrier             INTEGER (0..2199),

    subcarrierSpacing           SubcarrierSpacing,

    k0                          ENUMERATED {n-6, n0, n6},

    carrierBandwidth            NTEGER (1..maxNrofPhysicalResourceBlocks),

    ...

}
```

**absoluteFrequencySSB :** Frequency of the SSB to be used for this serving cell. The frequency provided in this field identifies the position of resource element RE=#0 (subcarrier #0) of resource block RB#10 of the SS block. The cell-defining SSB of an SpCell is always on the sync raster. Frequencies are considered to be on the sync raster if they are also identifiable with a GSCN value 

**absoluteFrequencyPointA** : Absolute frequency position of the reference resource block (Common RB 0). Its lowest subcarrier is also known as Point A. Note that the lower edge of the actual carrier is not defined by this field but rather in the scs-SpecificCarrierList. Corresponds to L1 parameter

:::success 

:dart: Observation : We need to define these values accurately in Radio context configuration so that UE able to search for SSB on these values.
:::

### Next Step

* I will check the values of Radio context configuration.