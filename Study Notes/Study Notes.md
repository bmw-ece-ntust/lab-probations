---
title: Study Notes
tags: [January, Weekly, Sheryl, Summer, Templates, Meeting, 12-27-2024, Notes]

---

![](https://i.imgur.com/JORnn3y.png =150x)@NTUST

Meeting Minutes
===

## 2025

## February
:::info
###### tags: `February` `Sheryl` 
- **Location:** T-809
- **Date:** 02/11/25
- **Time:** 01:30 to 2:00.
- **Action item**
    1. Check the new PCAP files logs.
    2. Discussed about the configure Deniel suggested.
     
-- **Next Step**
    1. Ask Ashwin/Madhav to share their logs FlexRAN, xFAPI where they make succesful MIB decode.
    2. Verify if MIB send correctly?
    3. As suggested by Deniel, Check if there are setting to set DU power configurations?
:::
    
:::info

###### tags: `February` `Weekly`
- **Location:** T-301
- **Date:** 02/10/25
- **Time:** 09:00 to 10:30.
- **Agenda**
    1. Weekly Stand-up meet.
* Learning-
    * Explain your idea of resolving issue with the help pf diagram to understand better.
:::
    
## January
###### tags: `January` `Weekly`

:::info
###### tags: `Weekly`
- **Location:** T-301
- **Date:** 01/15/25
- **Time:** 09:00 to 10:30.
- **Agenda**
    1. Weekly Stand-up meet.
* Learning-
    * While performing test Write your all results and make a record of everything you faced.
    * Provide use case to difine and validate your idea.

:::info
###### tags: `Sheryl`
- **Location:** EE-809
- **Date:** 01/13/25
- **Time:** 16:00 to 17:00.
- **Agenda**
1. Learn how to run UESIM for Cell search  and collect logs. 

* **Outcomes:**
    * [Learn to get aceess to the server.](https://hackmd.io/YXJJsobaQkuoRJp-YHEiVA#Access-Method)
    * [Configuration Radio Context](https://hackmd.io/YXJJsobaQkuoRJp-YHEiVA#Cell-search-and-UE-configure-script-setting)
    * [How to Bring up FlexRAN + xFAPI + O-DU HIGH + OAI CU.](https://hackmd.io/YXJJsobaQkuoRJp-YHEiVA#Bring-up-FlexRAN--xFAPI--O-DU-HIGH--OAI-CU)
    * [collect UE logs](https://hackmd.io/YXJJsobaQkuoRJp-YHEiVA#Opt-collect-UE-logs)
:::

:::info
- **Location:** T301-2
- **Date:** 01/07/25
- **Agenda**
1. Weekly updates by students `1 hour`

* **Outcomes:**
    * When presenting be precise with Architecture, topology and Interfaces that you use.
    * Focus on your Goal and methods/solutions used.
    * The nomenclature you used should be explained properly.
    * The data used should be precise and make clear purpose to your Goal and solution.
:::

:::info
- **Location:** OAI Lab
- **Date:** 01/06/25
- **Agenda**
1. RUn other UE to check throughput issue. `45 minutes`

* **Result**
    * UE was not able to camp on the OAI network environment.
* **Potential cause**
    * UE has some configuration issue because other UE was able to camp on networrk.
:::
###### tags: `Summer`
## 2024
## December


###### tags: `Templates` `Meeting`


:::info
- **Location:** Room EE809
- **Date:** 31/12/24
- **Agenda**
1. Understand the architecture modules and Interfcaces. `20 minutes`
2. Check The issue of MIB and SIB `10 minutes`
3. General questions about configuration and approach. `10 minutes`

* Action Item

    1- Understand the topology used in [Integration of TM500 + FlexRAN + xFAPI + O-DU HIGH + OAI CU](https://hackmd.io/Azu-QO88S1mhvw7iSurajA#Integration-of-TM500--FlexRAN--xFAPI--O-DU-HIGH--OAI-CU)
    2- Understand the configuration and address assigned to each node.
    3- What is current status of nodes.
    4- What is problem with MIB and SIB.
    5- I asked questions about the setting configuration provided.

- **Participants:**
    - Ravi
    - Sheryl
    
:::

###### tags: `Templates` `Meeting`


:::info
- **Location:** EE809
- **Date:** 27/12/24
- **Agenda**
1. Introduction to his thesis work `20 minutes`
2. Discussed about his approach to thesis `10 minutes`

- **Participants:**
    - Ravi
    - Jojo
    
:::



### 2024/12/26
:::info
### Throughput 
Participant:
- Summer
- Ravi

Time : 
- 14:00-16:00
### Agenda
#### Summer share the E2E environment
- Introduce [Topology of OAI + JURA](https://hackmd.io/NWRWHPjuT4ikbQ3_tnRkTg#Topology).
- Introduce [UE and UE tool we use for integration](https://hackmd.io/NWRWHPjuT4ikbQ3_tnRkTg#5-Run-UE).
- Introduce [throughput testing way and the result.](https://hackmd.io/@Summer063/BJS22JX71l)

#### Ravi share the experience for measure UE signal
- Ravi thinks in OAI environment there is CA(carrier aggregation). To make throughput this high(700-800Mbps).
- Share the QXDM tool enable method.
	- The compony he stay has open account for him.
	- So we can install it in our LAB laptop.
	- But the RAN requirement is 16GB. Our labtop is only 8GB. Will try whether it can use in our labtop of 8GB RAM.
	- Every Qualcom chipset UE can use QXDM tool.
- Share ELT toll can use in every MTK shipsett UE.


#### Action item
- [ ] Check MCS in UE
- [ ] Check UE disconnect reason
- [ ] Get the UE log from live network SIM and compare
- [ ] Check CA(carrier aggregation) OAI gNB use, and UE get.
- [ ] Ravi check whether LAB labtop is able to install QXDM tool.
- [x] Summer provide UE disconnect log to Ravi.
:::




# Study Notes

:::info
#### :memo: **Outline:**
[TOC]
:::

## Task 1 
:::info
:bulb: Figure out the problem of the low throughput in Metanoia’s RU. [Study Notes-12/27](https://hackmd.io/@ravishankar/B1OyccoS1l)

:::

:calendar: Date
:::success
Date format: 12-27-2024
:::
###### tags: `12-27-2024` `Notes`




### :pencil2: Details
:::success
Describe the details what the update for this issue. 
:::

### Log Analysis and Findings. [Figure out the problem of the low throughput in Metanoia’s RU](https://hackmd.io/m3WEoEq7TxCz-hIm9ATnmA#Figure-out-the-problem-of-the-low-throughput-in-Metanoia%E2%80%99s-RU)

#### [Log Reference](https://hackmd.io/@Johnson-72/HJhVtK9rkl) `Provided by Johnson`
:::info


* 1- [Findings in pacp log F1 log for OAI CU +OAI DU](https://trello.com/c/gRTQgBWW#comment-6785cdaf79d6a1fd2acc5717)
* 2- [Finding in pcap log split e2e pcap.](https://hackmd.io/m3WEoEq7TxCz-hIm9ATnmA#2-Finding-in-pcap-log-split-e2e-pcap)
* 3- [Finding in Log file 0920_free](https://hackmd.io/m3WEoEq7TxCz-hIm9ATnmA#3-Finding-in-Log-file-0920_free)
:::



### Difference between [ACK], [FIN,ACK] and [PSH,ACK]
![image](https://hackmd.io/_uploads/S172t6yIyg.png)

**ACK(Acknowlegde):** Confirms that the receiver has received the data packets. The receiver sends an ACK flag back to the sender to acknowledge receipt.
**PSH(Push):** Tells the application to immediately transmit the data, without waiting to fill the entire TCP segment.
**FIN(Finished):** Ends the TCP connection. FIN is an acronym for a flag in the TCP header that indicates when and how a connection is terminated

[FIN, ACK] is a combination of two TCP (Transmission Control Protocol) flags: FIN (Finish) and ACK (Acknowledgment).

[PSH, ACK] indicating that the packet contains data to be pushed and acknowledges previous data from the receiver.


### *ETSI* 8.3.2 UE Context Release Request - eNB initiated
8.3.2.1 General
The purpose of the UE Context Release Request procedure is to enable the eNB to request the MME to release the UEassociated logical S1-connection due to EUTRAN generated reason (e.g. 'TX2RELOCOverall Expiry'). The procedure uses
UE-associated signalling.
8.3.2.2 Successful Operation 

![image](https://hackmd.io/_uploads/rywo-CkL1g.png)

The eNB controlling a UE-associated logical S1-connection initiates the procedure by generating an UE CONTEXT
RELEASE REQUEST message towards the affected MME node.
The UE CONTEXT RELEASE REQUEST message shall indicate the appropriate cause value for the requested UEassociated logical S1-connection release. 

###  HEARTBEAT
PCFregisters with NRF and sends a heartbeat message to the same NRF to infer its status as active or inactive. Complying with 3GPP TS 29.510, PCF performs the following tasks when sending a heartbeat:

 * Sends a heartbeat in the form of a PATCH request to, and processes responses with the NRF that it has registered with. 
 * Performs the failover operation when the registered NRF is unavailable due to connectivity issues or some unknown reasons. In such situations, PCF registers and uses the available secondary or tertiary NRFwhentheprimary NRFisunresponsive. Simultaneously, PCF attempts to register with the primary NRF. Whenregistration to the original (primary) NRF is successful, PCF stops sending heartbeats to the secondary or tertiary NRF. In the absence of the primary NRF, PCF performs the failover and failback in the following sequence: 
 * Failover: Primary > Secondary or Tertiary > Tertiary 
 *  Failback: Tertiary > Secondary or Primary > Primary 
 *  WhenPCFregisters with a nonprimary NRF, it attempts to register with the primary NRF in the interval that is configured in the interval-in-secs parameter. For more information, see the nfServices information in the Network Repository Function Subscription to Notifications chapter. 
 * Whensending two consecutive heartbeat messages, PCF honors the time interval that is available in the heartBeatTimer attribute in the registration response or the heartbeat response.



### Subcarrier spacing (SCS) and numerology.


#### 3GPP TS 38.211 defines the following SCS values:

15 kHz
30 kHz
60 kHz
120 kHz
240 kHz

- Relation to Numerology (μ):

SCS = 15 kHz * 2^μ
μ = [0-4]

 #### Symbol Duration:

Formula: Symbol Duration = 1 / Subcarrier Spacing.
Examples:
For 15 kHz SCS: Symbol duration = 1 / 15,000 = 66.67 μs.
For 30 kHz SCS: Symbol duration = 33.33 μs.

Higher SCS results in shorter symbol durations, facilitating low-latency communication.

#### Use Cases and Frequency Ranges

**Frequency Ranges:**
FR1 (Sub-6 GHz): SCS = 15 kHz, 30 kHz, 60 kHz.

FR2 (mmWave, 24 GHz and above): SCS = 60 kHz, 120 kHz, 240 kHz.

**Use Cases:**
- 15 kHz, 30 kHz:
Suitable for eMBB and mMTC in FR1.

- 60 kHz, 120 kHz, 240 kHz:
Ideal for URLLC and high-bandwidth applications in FR2.

**Numerology and Supported Channels :**

![image](https://hackmd.io/_uploads/SkA7KfHL1e.png)





## Task 2 - 
:::info
:bulb:Check the issue of Physical Layer in [Integration of TM500 + FlexRAN + xFAPI + O-DU HIGH + OAI CU.](https://hackmd.io/@ravishankar/SyBopgaLJx)
:::

:calendar: Date
:::success
Date format: 12-31-2024
:::

### SSB Block in SA [ref.](https://howltestuffworks.blogspot.com/2019/10/5g-nr-synchronization-signalpbch-block.html)


1- Frequency search nd tunning
2- PSS and SSS decode
3- PBCH Decode
4- RMSI and OSI decode.
5- Also use for RSSP, RSRQ and SINR measurment.

![image](https://hackmd.io/_uploads/BJ099kNLyx.png)


1 RB = 12 subcarriers
20RB = 240 subcarriers

**Resource Element** : This is same as LTE. It is the smallest unit of the resource grid made up of one subcarrier in frequency domain and one OFDM symbol in time domain.

So, 1 Rseource element can have 12 subcarriers in frequency domain.



* 
* 


Physical-layer Cell Identity (PCI)
-   There are 1008 unique PCIs defined in 5G NR, double of that in LTE (504).
-   1008 NR PCIs are divided into 336 unique PCI groups and each group consisting of three different identities.
-   PCI of a cell can be calculated using;
NIDCell = 3 * NID(1) + NID(2) where NID(1) ∈ {0,1, … ,335} and NID(2) ∈ {0,1,2}
-   The UE derives PCI group number NID(1) from SSS and physical-layer identity NID(2) from PSS.

PBCH:

- PBCH occupies 20 RBwithin 2nd and 4th Symbol.
- PBCH also occupy 8 RB within 3rd symbol.
- While SS/PBCH(SSB) block is transmitted using antenna port 4000.
- Resource block allocate to the PBCH(PBCH payload + PBCH DMRS).
- DMRS- Demodulation reference signal occupies 25% of the resource element allocated t the PBCH.
- PBCH payload has (20*2+8)*12*75% = 432 resource elemets.
- PBCH use QPSK modulation so resource element carry = 432*2=864 bits.


![image](https://hackmd.io/_uploads/B1MYfb4Uyg.png)

**Table for frequency resources occupied by SSB:**

![image](https://hackmd.io/_uploads/HywjmbV8Jx.png)



### 5.4.3.1	Synchronization raster and numbering

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

### Calculations:

:::info
Formula to calculate:
FREF = FREF-Offs + ΔFGlobal (NREF – NREF-Offs)
:::

* **absoluteFrequencyPointA:** It represents the common reference point A, this reference point is the 0th RB of 273 RBs, which is the center point of RB#0. From above logs absoluteFrequencyPointA= 642722 (NREF)
* **absoluteFrequencyPointA=** 3000 MHz + 15* (642722 -600000) KHz= 3,640.83 MHz

* **absoluteFrequencySSB:** It represent the center frequency of SSB Block. A SSB block is 20 RBs results 20 * 12 =240 Subcarriers and from above logs snippet absoluteFrequencySSB= 643008 (NREF)
* **absoluteFrequencySSB=** 3000 MHz + 15* (643008 -600000) KHz= 3,645.12 MHz
Carrier Center Frequency: The total number of RB’s=51 and Resource Block corresponding to center frequency is 51/2=26
Center Frequency= absoluteFrequencyPointA + 26 RBs * 12 * Subcarrier Spacing
Center Frequency= 3,640.83 + 26 * 12 *30 KHz = 3,650.19 MHz

:::success 

:dart: Observation : We need to define these values accurately in Radio context configuration so that UE able to search for SSB on these values.
:::

### Calculation GSCN, SSref, Nref, ARFCN, SSB locations(SA)

#### **Band n1**

* Table 5.4.3.1-1: GSCN parameters for the global frequency raster for above 3 MHz channel bandwidth
* Range of frequencies (0-3000 MHz)
 
> **SS block frequency position SSREF** = N * 1200 kHz + M * 50 kHz, N = 1:2499, M ϵ {1,3,5}

* **No of Scans** = Last scan - first scan = 5419-5279=140 Scans.
* DL Range - 2110MHz -2170MHz
* UL Range - 1920MHz -1980MHz
> GSCN= 3N+(M-3)/2
>     5279= 3N+(1-3)/2
>     5279= 3N
>     N = 1760 

**SSref.**
> SSref = N*1200+M*50KHz
> = 1760*1200+1*50KHz
> = 2112050KHz= 2112.05MHz(May also know as Fref)

Nref= Nref-offset+ (Fref - Fref-offset)/Fglobal.
Nref = 422000+ (2112.05-2110)/0.005
Nref = 422410

* **Frequency Calculator**

https://www.cellmapper.net/arfcn?net=NR&ARFCN=621056&MCC=0

SSB locations(SA) 
* DL= 2112.05MHz
* UL= 1922.05MHz


#### **Band n78**

* Table 5.4.3.1-1: GSCN parameters for the global frequency raster for above 3 MHz channel bandwidth
* Range of frequencies (3000-24250 MHz)
 
> **SS block frequency position SSREF** = 3000MHz + N* 1.44MHz
> N= 0 to 14756
* **No of Scans** = Last scan - first scan = 8051-7711=340 Scans.
* DL Range - 3300MHz -3800MHz
* UL Range - 3300MHz -3800MHz
> GSCN= 7499+N
>     7711= 7499 + N
>     N = 212 

**SSref.**
> SSref = 3000MHz+212*1.44MHz
> = 3305.28MHz
> = 3305.08MHz(May also know as Fref)

Nref= Nref-offset+ (Fref - Fref-offset)/Fglobal.
Nref = 620000+ (3305.28-3300)/0.015
Nref = 620352

* **Frequency Calculator**

https://www.cellmapper.net/arfcn?net=NR&ARFCN=621056&MCC=0

SSB locations(SA) 
* DL= 3305.28MHz
* UL= 3305.28MHz



**During SA and NSA.**

![image](https://hackmd.io/_uploads/Hy6rWOc8Jl.png)



### Tutorials on OFDM.

- OFDM Overview

OFDM stands for Orthogonal Frequency Divisition Multiplexing. OFDM is very good method of utilizing the given frequency wisely, but there is a drawback to this method. For this method to work efficiently the space between sub carriers should be maintained exactly at the specified position which satisfy the condition of orthogonality.

- Cyclic Prefix- Avoid Interference of signal.

![image](https://hackmd.io/_uploads/ByAQzErI1x.png)

### MIB

MasterInformationBlock
Followings are the overall characteristics of MIB (MasterInformationBlock). See 38.331-5.2.1 and 38.213-4.1 for further details of MIB scheduling.

Transmitted over BCH / PBCH (NOTE : PBCH is transmitted as a part of SSB. So it will be benificial to understand on SSB as much as possible. See here for SSB details)
Transmitted with the periodicity of 80 ms and within this 80 ms repeatative transmission happens
For initial cell selection, a UE may assume that half frames with SS/PBCH blocks occur with a periodicity of 2 frames
Includes the parameters that are required to decode SIB1 (SystemInformationType1)
 

MIB ::= SEQUENCE {

    systemFrameNumber                   BIT STRING (SIZE (6)),

    subCarrierSpacingCommon             ENUMERATED {scs15or60, scs30or120},
     ssb-SubcarrierOffset                INTEGER (0..15),

    dmrs-TypeA-Position                 ENUMERATED {pos2, pos3},

    pdcch-ConfigSIB1                   INTEGER (0..255),

    cellBarred                          ENUMERATED {barred, notBarred},

    intraFreqReselection                ENUMERATED {allowed, notAllowed},

    spare                               BIT STRING (SIZE (1))

}

**subCarrierSpacingCommon :** Indicates the Subcarrier spacing for SIB1, Msg.2/4 for initial access and SI-messages. Interpretation of this value varies with frequency range as summarized in the following table.

**ssb-subcarrierOffset :** This corresponds to k_ssb(38.213). Indicates the frequency domain offset between SSB and the overall resource block grid in number of subcarriers. If k_ssb requires the value higher than 15, it is represented by the combination of a PBCH data field and ssb-subcarrierOffset.

**dmrs-TypeA-Position :** Indicates Position of (first) DL DM-RS.

**pdcchConfigSIB1:** Determines a bandwidth for PDCCH/SIB, a common ControlResourceSet (CORESET), a common search space and necessary PDCCH parameters. This corresponds to RMSI-PDCCH-Config.

### SystemInformationBlockType1

- Transmitted over DL-SCH (NOTE : SIB1 is the first RRC message (except MIB). So UE need to be able to decode SIB1 without much information from OTA signaling message. Therefore, 3GPP defines very specific (often complicated) procedure to transmit/decode DCI and PDSCH for SIB1
- Transmitted with the periodicity of 160 ms and within this 160 ms repeatative transmission happens.
- Includes information regarding the availability and scheduling (e.g. periodcity, SI-window size) of other SIB
- Indicates whether they (i.e. other SIBs) are provided via periodic broadcast basis or only on-demand basis (If other SIBs are provided on-demand then SIB1) Includes information for the UE to perform SI request

**commonControlResourcesSets :** A list of common control resource sets. Only CORESETs with ControlResourceSetId = 0 or 1 are allowed. The CORESET#0 corresponds to the CORESET configured in MIB (see pdcch-ConfigSIB1) and is used to provide that information to the UE by dedicated signalling during handover and (P)SCell addition. The CORESET#1 may be configured an used for RAR

**commonSearchSpaces :**  A list of additional common search spaces

**searchSpaceSIB1 :** ID of the search space for SIB1 message. Corresponds to L1 parameter 'rmsi-SearchSpace'

**searchSpaceOtherSystemInformation :** ID of the Search space for other system information, i.e., SIB2 and beyond. Corresponds to L1 parameter 'osi-SearchSpace'. If the field is absent, the monitoring occasions are derived as described in PDCCH Type 0 Common Search Space page.

**pagingSearchSpace :** ID of the Search space for paging. Corresponds to L1 parameter 'paging-SearchSpace'. If the field is absent, the monitoring occasions are derived as described in PDCCH Type 0 Common Search Space page.

**ra-ControlResourceSet :** CORESET configured for random access. When the field is absent the UE uses the CORESET according to pdcch-ConfigSIB1 which is associated with ControlResourceSetId = 0. Corresponds to L1 parameter 'rach-coreset-configuration'

**ra-SearchSpace :** ID of the Search space for random access procedure. Corresponds to L1 parameter 'ra-SearchSpace'.  If the field is absent, the monitoring occasions are derived as described in PDCCH Type 0 Common Search Space page.

### **How to calculate SSB Overhead?**

Total number of resource element used by SSB in a frame, devided by total number of resource element available in that frame.



![image](https://hackmd.io/_uploads/H1rVapP8Jx.png)



### MIMO

* When we have massive MIMO or many transmit element we can do beam forming.
* Peak Throughput might not incease but cell capacity will increase massively.
* Mssive MIMO results better CQI.

**CSI feedback-**

CSI feedback has three parts:
1- RI- Rank Indicator
2- CQI(Chanel quality Indicator)
3- PMI(Precoding matrix Info)

* UE has sinr to CQI conversion table.


### Key performance indicators (KPI): throughput, BLER, SNR, RSRP, and RSRQ.

**BLER: (Block error rate)**

- IBLER(Initial BLER) < 10%
- RBLER(Remaining BLER) < 1%


**SINR :**

- RSRP(Reference Signal Power)
- RS_SINR - RSRP/RS_interference

For UE measures coverage based on SSS in SSB. SO SS_RSRP and SS_SINR are important values. Howerver on different cells, the location of SSS is same so all the SSS will interfere with each other and thus SS_SINR would be low.

SS_SINR = SS RSRP/SS_interference.

Note- SS_SINR is used for N310/N311 as well.

**CSI-RS SINR :**
CSI-RS(Channel state information-RS)

**PDSCH-SINR :**

* Many UE use a combination of both CSI resources along with PDSCH resources to estimate SINR and then convert it to CQI.
* Thus, PDSCH SINR is usually the best SINR as it doesn't have any interference other than load based interference.

## What is xFAPI

* xFAPI is the key to achieving true interoperability in O-RAN, removing vendor lock-in and unlocking the full potential of open interfaces. Acting as a bridge between any L1 layer vendor and L2 layer vendor of O-RAN, xFAPI bridges the gap enabling multi-vendor compatibility with ease.

* xFAPI acts as a translator, providing interoperability between different IPC mechanisms, including shared memory (xSM) and sockets (nFAPI). Additionally, xFAPI includes an integrated capability that can be activated at runtime based on compilation flag that will check if L1-L2 are interoperable and provide the option to use xFAPI if desired (for additional functionalities such as detailed PDU stat generation at both interfaces, debugging tools like memory logger, state manager, multi-level logging, and monitoring and analysis on the dashboard).

![image](https://hackmd.io/_uploads/BkQKRjuYJl.png)


#### 📌  Key FAPI Specifications
1. Standardized by Small Cell Forum (SCF)
SCF FAPI v1.0 – v3.1 (LTE versions)
SCF 5G FAPI v1.0 – v2.0 (5G NR versions)
SCF nFAPI (Network-based FAPI for virtualized implementations)
Ensures interoperability in open and disaggregated RAN architectures.
2. FAPI Message Categories
FAPI defines three main categories of messages exchanged between PHY and MAC:

    * (a) Configuration Messages:
PARAM.request / response – Provides PHY capabilities to MAC.
CONFIG.request / response – Configures PHY parameters (e.g., RF settings, frame structure).

    * (b) Control & Scheduling Messages:
START.request / STOP.request – Controls PHY operation.
DL_CONFIG.request – Configures downlink transmission, including:
PDSCH, PBCH (MIB transmission), PDCCH, SSB.
UL_CONFIG.request – Configures uplink reception, including:
PUSCH, PRACH, PUCCH.
    * (c) Data Messages:
TX.request – Carries DL data, including PBCH (for MIB).
RX.indication – PHY reports received uplink data to MAC.


### 📡 FAPI in 5G NR
5G FAPI introduces support for:

SS/PBCH (MIB transmission):
* Multiple numerologies (15, 30, 60, 120 kHz)
* Massive MIMO and beamforming
* Dynamic TDD switching
* 5G NR-Specific Messages:

DL_TTI.request – Includes PBCH (for MIB transmission).
UL_TTI.request – For uplink scheduling.
P7 Messages – Used in nFAPI for cloud-based PHY/MAC splits.


### Control Messages
These messages schedule downlink (DL) and uplink (UL) transmissions.

(a) DL_TTI.request (5G FAPI)

📌 Purpose: Schedules PBCH (MIB transmission), PDCCH, PDSCH, and SSB bursts.

DL_TTI.request Format


| Field Name | Description |
| -------- | -------- | 
| sfn  | System Frame Number  |
| slot  | lot number (0–159)  |
| num_dci  | Number of DCI (PDCCH) messages  |
| num_pdsch  | Number of PDSCH allocations  |
| num_ssb| Number of SS/PBCH (MIB) bursts  |


PBCH (MIB) Configuration Inside DL_TTI.request

| Field Name | Description |
| -------- | -------- |
| ssb_index     | SSB beam index    |
| ssb_frequency     | Frequency of SSB burst    |
| pbch_payload     | Encoded MIB payload    |


(b) UL_TTI.request
📌 Purpose: Schedules uplink transmissions (PUSCH, PUCCH, PRACH).

UL_TTI.request Format:

| Field Name | Description |
| -------- | -------- |
| num_pusch    | Number of scheduled PUSCH grants     |
| num_pucch    | Number of scheduled PUSCH grants    |
| num_prach    | Number of scheduled PRACH occasions     |

### Data Transfer Messages
These messages carry the actual transmission data.

(a) TX.request
📌 Purpose: Contains PBCH (MIB), PDCCH, PDSCH payloads for downlink.

TX.request Format:


| Field Name | Description |
| -------- | -------- | 
| sfn    | System Frame Number     |
| slot    |  Slot number   |
| num_pdsch     | Number of PDSCH transmissions    |
| num_pbch    | Number of PBCH (MIB) payloads     |
| payload    | Encoded transport block     |


(b) RX.indication
📌 Purpose: Reports received UL data from PHY to MAC.

RX.indication Format:

| Field Name | Description |
| -------- | -------- |
| num_pusch     | Number of PUSCH receptions     |
| num_pucch     | Number of PUCCH receptions     |
| rssi     | Received signal strength     |
| payload     | Decoded uplink data    |






### FlexRAN










