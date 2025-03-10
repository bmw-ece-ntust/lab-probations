---
title: 'Integration of TM500 + FlexRAN + xFAPI + O-DU HIGH + OAI CU '
tags: [TM500, FlexRAN]

---

![](https://i.imgur.com/JORnn3y.png =150x)@NTUST
## :dart: Integration of TM500 + FlexRAN + xFAPI + O-DU HIGH + OAI CU
>[name=Ravi][color=#38c16a]

:::info
* **Goals**
    * Integrate TM500 with RAN (FlexRAN+ xFAPI + O-DU High + OAI CU) and Core network as free5GC.
    * Test TM500 on various aspects like Throughput and Latency.
:::

:::success
* **References.**
     - [**OSC gerit**](https://gerrit.o-ran-sc.org/r/admin/repos/o-du/l2,general)
    - [**xFAPI: Deployment Guideline**](https://lf-o-ran-sc.atlassian.net/wiki/spaces/IAT/pages/176226489/xFAPI+Deployment+Guideline)
    - Prerequisite
        * OSC DU install
        * You can refer to this [note](https://hackmd.io/@Summer063/rk055mIF6) to install OSC DU.

:::

:::info
#### :memo: **Outline:**
[TOC]
:::

## Topology
![image](https://hackmd.io/_uploads/SypBs8Fryg.png =70%x)



## Access Method
:::success
**TM500 Server (Supermicro) :**
- IP Address : 192.168.8.67
- Username : viavi
- Password : viavi

**TM500 Control PC :**
- IP Address : 192.168.8.68
	- User Password : bmwee809
- Anydesk ID : 1549083559
	- Anydesk Password : bmwbmwbmwee809

**FlexRAN+xFAPI+OSC O-DU HIGH+OAI CU(Supermicro) :**
- IP Address : 192.168.8.76
	- Username : ubuntu
	- Password : bmwlab
	- Root Password : bmwlab
- IDRAC IP : 192.168.10.87
	- IDRAC user name : ADMIN
	- IDRAC Password : WDLZISCGYS
:::

## Environment
### FlexRAN + xFAPI + O-DU
**Hardware:**
|     Item     | Info                                             |
|:------------:| ------------------------------------------------ |
|     CPU      | Intel® Xeon® Gold 6433N CPU @ 3.60GHz (64 cores) |
|    Memory    | 251 GB                                           |
|     Disk     | 879 GB                                           |
|     NIC      | Intel Ethernet Controller E810-XXV for SFP (x2)  |
| Server Model | Supermicro SYS-111E-WR                           | 

**Software:**
|   **Item**    | **Info**                           |
|:-------------:|:---------------------------------- |
|      OS       | Ubuntu 22.04.4 LTS                 |
|    Kernel     | Linux maxwell 5.15.0-1069-realtime |
|     DPDK      | 22.11.1                            |
|   LinuxPTP    | 3.1.1                              |
| OSC DU Branch | i-release/k-release                | 
| l1app Branch  | FlexRAN 23.07                      |

### TM500
**Hardware:**
|     Item     | Info                                                     |
|:------------:| -------------------------------------------------------- |
|     CPU      | Intel(R) Xeon(R) CPU E5-2695 v4 @ 2.10GHz (18 cores) x 2 |
|    Memory    | 132GB                                                    |
|     Disk     | 1T                                                       |
|     NIC      | MT27800                                                  |
| Server Model | Supermicro SSG-6028R-E1CR12L                             |

**Software:**
|  **Item**   | **Info**                            |
|:-----------:|:----------------------------------- |
|     OS      | Red Hat Enterprise Linux 9 (RHEL 9) |
|   Kernel    | Linux bell 5.14.0-412.el9.x86_64    |
|  Boot disk  | WDC WD10SPZX-00Z                    | 
| TMA version | NLC 1.4.0                           |

## Status
| Item                                                                                                                                        | Status             |
| ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------ |
| [Bring up TM500](#1-TM500-Status)                                                                                                           | :heavy_check_mark: |
| [Check TM500 PTP sync](#Step13-TM500-PTP-Synchronization)                                                                                   | :heavy_check_mark: |
| [Bring up CN](#2-Core-Network-and-gNB-Connection)                                                                                           | :heavy_check_mark: |
| [PTP sync of gNB](#Step-32-gNB-PTP-synchronization)                                                                                         | :heavy_check_mark: |
| [Bring up gNB](#Step-33-Run-gNB)                                                                                                            | :heavy_check_mark: |
| [NG Setup](#Step-35-Check-CN-connection-with-DU)                                                                                            | :heavy_check_mark: |
| [RU get on time packet from DU](#Step-41-Check-DU-connection-at-RU-side)                                                                    | :heavy_check_mark: |
| [DU get FH packet from RU](#Step-42-Check-RU-connection-at-DU-side)                                                                         | :heavy_check_mark: |
| [Run UE](#5-Run-UESIM)                                                                                                                      | :heavy_check_mark: |
| [UE get mib and sib1 for DL sync (cell search fail)](https://hackmd.io/aMMRsl3aSjq8zVFrnFqtDg?view#cell-search-fail74) | :hourglass:        |
| [UE send preamble]()                                                                                                                        | :x:                |
| [DU get preamble]()                                                                                                                         | :x:                |
| [DU send RACH response(msg2)]()                                                                                                             | :x:                |
| [UE get RACH response(msg2)]()                                                                                                              | :x:                |
| [UE send RRC setup request(msg3)]()                                                                                                         | :x:                |
| [DU get RRC setup request(msg3)]()                                                                                                          | :x:                |
| [DU send RRC Set up(msg4)]()                                                                                                                | :x:                |
| [UE get RRC Set up(msg4)]()                                                                                                                 | :x:                |
| [RRC setup complete]()                                                                                                                      | :x:                |
| [NAS registration]()                                                                                                                        | :x:                |
| [NAS identity request]()                                                                                                                    | :x:                |
| [NAS identity response]()                                                                                                                   | :x:                |
| [Authenication request]()                                                                                                                   | :x:                |
| [Authenication response]()                                                                                                                  | :x:                |
| [NAS Security mode command]()                                                                                                               | :x:                |
| [NAS Security mode complete]()                                                                                                              | :x:                |
| [UECapabilityEnquiry]()                                                                                                                     | :x:                |
| [UECapabilityInformation]()                                                                                                                 | :x:                |
| [AS SecurityModeCommand]()                                                                                                                  | :x:                |
| [AS SecurityModeComplete]()                                                                                                                 | :x:                |
| [RRCReconfiguration]()                                                                                                                      | :x:                |
| [Registration accept]()                                                                                                                     | :x:                |
| [RRCReconfigurationComplete]()                                                                                                              | :x:                |
| [Registration complete]()                                                                                                                   | :x:                |
| [PDU session establish request]()                                                                                                           | :x:                |
| [PDU session establish accept]()                                                                                                            | :x:                |
| [Internet access]()                                                                                                                         | :x:                |
| [Performance]()                                                                                                                             | :x:                |
:::info
### Current Status
- UE is not able to receive MIB and SIB.
  - Potential cause- 
    - 1- UE not able to decode SSB position
    - 2- RAN not able to transmit DL sync signals.
:::

## Configuration
### Configuration Files

|     | O-DU High     | O-DU Low         | RUSIM                           | UESIM                    |
| --- | ------------- | ---------------- | ------------------------------- | ------------------------ |
| L2  | du_cfg.h      | N/A              | N/A                             | Configure Radio Contexts |
| L1  | lwr_mac_fsm.c | xrancfg_sub6.xml | oran_2_0_default.csv, o-ran.cfg | N/A                      |
| FH  | N/A           | xrancfg_sub6.xml | oran_2_0_default.csv, o-ran.cfg | N/A                      |

### O-DU High
- File location : `l2/src/du_app/du_cfg.h`

| Parameters                  | value                | config parameter                                                                                                                           |
| --------------------------- | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| CC config                   | 2x2                  | `vendorMsg->config_req_vendor.nr_of_dl_ports =2`, `vendorMsg->config_req_vendor.nr_of_ul_ports =2` in `/o-du-l2/src/5gnrmac/lwr_mac_fsm.c` |
| DL Point A frequency(ARFCN) | 3401.58 MHz (626772) | `NR_DL_ARFCN 626772`                                                                                                                       |
| DL center frequency         | 3450.72 MHz (630048) | Check calculation [here](#DL-center-frequency-calculation) <br> `MEAS_TIMING_ARFCN`                                                                                  |
| SSB frequency               | 3450.72 MHz (630048) | Check calculation [here](#SSB-center-frequency-calculation)                                                                                |
| System Bandwidth            | 100 MHz              | `NR_BANDWIDTH BANDWIDTH_100MHZ` in `/o-du-l2/src/du_app/du_cfg.h`                                                                          |
| SCS                         | 30KHZ                | `NR_SCS SCS_30KHZ` in `/o-du-l2/src/du_app/du_cfg.h`                                                                                       |
| PCI(Physical Cell ID)       | 1                    | `NR_CELL_ID 1` in `/o-du-l2/src/du_app/du_cfg.h`                                                                                           |
| Duplex mode                 | TDD                  | `DUPLEX_MODE DUP_MODE_TDD` Need to set when you compile DU HIGH                                                                            |

### FlexRAN 
- File location : `/FlexRAN/l1/bin/nr5g/gnb/l1/xrancfg_sub6.xml`

| Parameters               | value             | config parameter                                                                                                                                                                                                                                                                                                                                       |
| ------------------------ | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| vlan id                  | 5                 | `<c_plane_vlan_tag>5</c_plane_vlan_tag>``<u_plane_vlan_tag>5</u_plane_vlan_tag>`                                                                                                                                                                                                                                                                       |
| pdsch/pusch eaxcid       | 0, 1              | `vendorMsg->config_req_vendor.nr_of_dl_ports =2`, `vendorMsg->config_req_vendor.nr_of_ul_ports =2`                                                                                                                                                                                                                                                     |
| prach eaxcid             | 2, 3              | `vendorMsg->config_req_vendor.nr_of_ul_ports =2`                                                                                                                                                                                                                                                                                                       |
| dl/ul compression method | 9bitBFP Static    | `<xranCompMethod>0</xranCompMethod>`</br>`<xranCompHdrType>1</xranCompHdrType>`</br>`<xraniqWidth>16</xraniqWidth>`</br>`<xranPrachCompMethod>0</xranPrachCompMethod>`</br>`<xranPrachiqWidth>16</xranPrachiqWidth>`</br>`<oRu0PrbElemDl0>0,273,0,14,0,0,0,16,0,0,0</oRu0PrbElemDl0>`</br>`<oRu0PrbElemUl0>0,273,0,14,0,0,0,16,0,0,0</oRu0PrbElemUl0>` |
| DU MAC address           | 00:11:22:33:44:66 | create in `/home/oran/G_O-DU/phy/setupvf.sh`                                                                                                                                                                                                                                                                                                           |
| RU MAC address           | 10:70:fd:14:1c:10 | `<oRuRem0Mac0>10:70:fd:14:1c:10</oRuRem0Mac0>`                                                                                                                                                                                                                                                                                                         |
| MTU size                 | 1500              | `<MTU>9000</MTU>`                                                                                                                                                                                                                                                                                                                                      |
| T1a_min_cp_dl            | 258 μs            | `<T1a_min_cp_dl>258</T1a_min_cp_dl>`                                                                                                                                                                                                                                                                                                                   |
| T1a_max_cp_dl            | 392 μs            | `<T1a_max_cp_dl>470</T1a_max_cp_dl>`                                                                                                                                                                                                                                                                                                                   |
| T1a_min_cp_ul            | 285 μs            | `<T1a_min_cp_ul>285</T1a_min_cp_ul>`                                                                                                                                                                                                                                                                                                                   |
| T1a_max_cp_ul            | 300 μs            | `<T1a_max_cp_ul>429</T1a_max_cp_ul>`                                                                                                                                                                                                                                                                                                                   |
| T1a_min_up               | 155 μs            | `<T1a_min_up>50</T1a_min_up>       `                                                                                                                                                                                                                                                                                                                   |
| T1a_max_up               | 300 μs            | `<T1a_max_up>196</T1a_max_up>      `                                                                                                                                                                                                                                                                                                                   |
| Ta4_min                  | 0 μs              | `<Ta4_min>0</Ta4_min>              `                                                                                                                                                                                                                                                                                                                   |
| Ta4_max                  | 200 μs            | `<Ta4_max>75</Ta4_max>             `                                                                                                                                                                                                                                                                                                                   |
| Tadv_cp_dl               | 125 μs            | `<Tadv_cp_dl>25</Tadv_cp_dl>       `                                                                                                                                                                                                                                                                                                                   |
| T2a_min_cp_dl            | 259 μs            | `<T2a_min_cp_dl>285</T2a_min_cp_dl>`                                                                                                                                                                                                                                                                                                                   |
| T2a_max_cp_dl            | 470 μs            | `<T2a_max_cp_dl>479</T2a_max_cp_dl>`                                                                                                                                                                                                                                                                                                                   |
| T2a_min_cp_ul            | 125 μs            | `<T2a_min_cp_ul>285</T2a_min_cp_ul>`                                                                                                                                                                                                                                                                                                                   |
| T2a_max_cp_ul            | 1200 μs           | `<T2a_max_cp_ul>429</T2a_max_cp_ul>`                                                                                                                                                                                                                                                                                                                   |
| T2a_min_up               | 70 μs             | `<T2a_min_up>71</T2a_min_up>       `                                                                                                                                                                                                                                                                                                                   |
| T2a_max_up               | 345 μs            | `<T2a_max_up>428</T2a_max_up>      `                                                                                                                                                                                                                                                                                                                   |
| Ta3_min                  | 50 μs             | `<Ta3_min>20</Ta3_min>             `                                                                                                                                                                                                                                                                                                                   |
| Ta3_max                  | 171 μs            | `<Ta3_max>32</Ta3_max>             `                                                                                                                                                                                                                                                                                                                   |

### RUSIM
- File location : `\VIAVI\TM500\5G NR - NLC 1.4.0\ppc_pq\public\ftp_root\oran_2_0_defaults.csv`

| Parameters    | RUSIM     | config parameter                                                                                                                                               |
| ------------- | --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Tadv_cp_dl    | 125000 ns | `o-ran-delay-management:delay-management/bandwidth-scs-delay-state[bandwidth='100000'][subcarrier-spacing='30000']/ru-delay-profile/tcp-adv-dl,SR_UINT32_T`    |
| T2a_min_cp_dl | 258000 ns | `o-ran-delay-management:delay-management/bandwidth-scs-delay-state[bandwidth='100000'][subcarrier-spacing='30000']/ru-delay-profile/t2a-min-cp-dl,SR_UINT32_T` |
| T2a_max_cp_dl | 470000 ns | `o-ran-delay-management:delay-management/bandwidth-scs-delay-state[bandwidth='100000'][subcarrier-spacing='30000']/ru-delay-profile/t2a-max-cp-dl,SR_UINT32_T` |
| T2a_min_cp_ul | 285000 ns | `o-ran-delay-management:delay-management/bandwidth-scs-delay-state[bandwidth='100000'][subcarrier-spacing='30000']/ru-delay-profile/t2a-min-cp-ul,SR_UINT32_T` |
| T2a_max_cp_ul | 859000 ns | `o-ran-delay-management:delay-management/bandwidth-scs-delay-state[bandwidth='100000'][subcarrier-spacing='30000']/ru-delay-profile/t2a-max-cp-ul,SR_UINT32_T` |
| T2a_min_up    | 50000 ns  | `o-ran-delay-management:delay-management/bandwidth-scs-delay-state[bandwidth='100000'][subcarrier-spacing='30000']/ru-delay-profile/t2a-min-up,SR_UINT32_T`    |
| T2a_max_up    | 196000 ns | `o-ran-delay-management:delay-management/bandwidth-scs-delay-state[bandwidth='100000'][subcarrier-spacing='30000']/ru-delay-profile/t2a-max-up,SR_UINT32_T`    |
| Ta3_min       | 0 ns      | `o-ran-delay-management:delay-management/bandwidth-scs-delay-state[bandwidth='100000'][subcarrier-spacing='30000']/ru-delay-profile/ta3-min,SR_UINT32_T`       |
| Ta3_max       | 75000 ns  | `o-ran-delay-management:delay-management/bandwidth-scs-delay-state[bandwidth='100000'][subcarrier-spacing='30000']/ru-delay-profile/ta3-max,SR_UINT32_T`       |

- File location : `\VIAVI\TM500\5G NR - NLC 1.4.0\ppc_pq\public\ftp_root\o-ran.cfg`

| Parameters     | RUSIM             | config parameter                        |
| -------------- | ----------------- |:--------------------------------------- |
| DU MAC address | 00:11:22:33:44:66 | `DefaultDuMacAddress=00:11:22:33:44:66` |

#### Timing window compare
| Parameters    | RUSIM  | O-DU LOW |
| ------------- | ------ | -------- |
| Tadv_cp_dl    | 25 μs  | 25 μs    |
| T2a_min_cp_dl | 258 μs | 285 μs   |
| T2a_max_cp_dl | 470 μs | 479 μs   |
| T2a_min_cp_ul | 285 μs | 285 μs   |
| T2a_max_cp_ul | 859 μs | 429 μs   |
| T2a_min_up    | 50 μs  | 71 μs    |
| T2a_max_up    | 196 μs | 428 μs   |
| Ta3_min       | 0 ns   | 20 μs    |
| Ta3_max       | 75 μs  | 32 μs    |

### UESIM
#### Configure Radio Contexts
| Parameters                           | value            |
| ------------------------------------ | ---------------- |
| Duplex                               | TDD              |
| Cell Id                              | 0                |
| Downlink carrier frequency (100 kHz) | 34507.2 (100kHz) | 
| System bandwidth (MHz)               | 100              |
| AbsoluteFrequencyPointA (100 kHz)    | 34015.8 (100kHz) |
| AbsoluteFrequencySSB (100 kHz)       | 34507.2 (100kHz) |

<!-- #### Define MTS Cells
| Parameters             | value |
| ---------------------- | ----- |
| Cell Id                | 0     |
| DL Frequency (100 kHz) | 34002 | -->

## Run Application
## 1. TM500 Status
### Step1.1 Configure TM500
### TM500 RUSIM csv file generate
- VIAVI have a tool to generate csv file. Only need to provide yaml file and fill in the parameters.
:::success
#### csv file generate guide
1. Download the csv file generate tool
	- [csv file generate tool download](https://drive.google.com/drive/folders/1kHT4-YUZXDo3Mnssf59fUXME64ry38yy)
2. Open cmd in your laptop.

![image](https://hackmd.io/_uploads/H1MkuiURp.png)

3. Go in the path you download csv generator tool folder(`__tool rusim csv generator`).
```bash=
cd C:\Users\user\Desktop\School\NTUST\BMW\TM500\virtualize TM500\__tool rusim csv generator
```
4. Create a folder and put the yaml file in.

![image](https://hackmd.io/_uploads/HkfewsURp.png)

5. Use `csvGen.exe` to generate csv.
	- Put yaml file path after `-f` parameter.
```bash=
# example : csvGen -f <path of yaml file>
C:\Users\user\Desktop\School\NTUST\BMW\TM500\virtualize TM500\__tool rusim csv generator>csvGen -f ntust_oai/ntust_oai_du.yaml
--------------------------------------------------------------------------------
Viavi ORAN .csv file generator version 0.4 - 31st July 23
--------------------------------------------------------------------------------
###############
input file name: C:\Users\user\Desktop\School\NTUST\BMW\TM500\virtualize TM500\__tool rusim csv generator\ntust_oai\ntust_oai_du.yaml
###############

Suggested MCI command set:


CONF TEMPLATE_ORU SysrepoInitFile ntust_oai_du.csv
CONF TEMPLATE_ORU MtuOverride 1500
CONF TEMPLATE_ORU DuMacAddress 00:11:22:33:44:66
CONF TEMPLATE_ORU AutoStart ON
SCXT 0 NR
SELR 0 1 ORU1-P1 0
ADDR 0 1 ORU1-P1
```
6. The generated `.csv` file and `_cmd.txt` file will create at the same path of yaml file.
	- A _cmd.txt file containing the suggested MCI command associated with the RU described by the .csv file.

![image](https://hackmd.io/_uploads/HJtwwsIC6.png)
7. Change csv file name to `oran_2_0_defaults.csv`.

![image](https://hackmd.io/_uploads/SkzvFo80a.png)
:::
:::spoiler `NR_1CC4x4_num1_Greigns.yaml`
```bash=
############### Common parameters #####
ORAN YANG model version: 2 #2,3,4,5,6,7 or 8  - optional: default is 2
MTU size: 9000                         #optional: default is 1500bytes
O-RU configuration mode: 0                  # 0: semi-static - 1: ODU configured - optional: default is 0
O-DU MAC address: 00:11:22:33:44:66           #only required in semi-static mode
M-plane VLAN ID: 20                         #only required in ODU configured mode
M-plane DHCP state: on                      #on/off only required in ODU configured mode
M-plane IP version: IPV4                   #IPV4/IPV6 - only required in ODU configured mode
M-plane IP address: 10.10.10.2/24        #only required in ODU configured mode and when DHCP is off
M-plane CallHome Ip address: 10.10.10.1   #only required in ODU configured mode and when DHCP is off
PTP domain number: 24                    #optional - default is 24
PTP- G_8275_1- multicast-mac-address:   #NONFORWARDABLE/FORWARDABLE - optional - default is NONFORWARDABLE

############### per CC config #####
perCC config:

- CCid: 1
  Ethernet O-RU port: ORU1-P1          #(2x2 or 4x4 or 4layerMUMIMO or 8layerMUMIMO or 16layerMUMIMO) - optional: default is 2x2
  VLAN ID: 5
  CC configuration: 2x2               #(2x2 or 4x4) - optional: default is 2x2
  Traffic type: NR                    #(LTE or NR )- optional: default is NR
  Numerology: 1                        #(0,1,3) - optional: default is 1
  Bandwidth: 100                       #(in MHz) - optional: default is 100MHz
  Alpha value: 0                       #optional: default is 0
  Beta value: 0                        #optional: default is 0
  DL Carrier Frequency: 0               #optional: default is 0
  UL Carrier Frequency: 0               #optional: default is 0
  DL compression: 9bitBFP          # (16BitUncompressed, 14bitBFP, 12bitBFP, 9bitBFP or 4bitModComp) assumes static compression controlled on a per direction basis
  DL (PDSCH) eaxcid list: 0,1        #order in list is used to control mapping on multiple BB cards
  DL mixed numerology?: no               #(yes/no) only set to yes for FR2 mixed numerology/numerology =3
  Additional SSB eaxcid list:             #only required for FR2 mixed numerology/numerology =3
  UL compression: 9bitBFP               #(16BitUncompressed, 14bitBFP, 12bitBFP or 9bitBFP) assumes static compression controlled on a per direction basis
  UL (PUSCH) eaxcid list: 0,1         #order in list could be used to control mapping on multiple BB cards
  Is PUSCH and RACH traffic on separate eaxcid?: yes #(yes/no)
  Additional RACH eaxcid list: 2,3    #only required if PUSCH and RACH are on different eaxcid
  Number of UL streams dedicated to SRS:  #only required for MU-MIMO scenarios
  Eaxcid of first SRS dedicated stream:   #subsequent eaxcid values are incremented from this initial value
```
:::

| Parameters                                    | value   |
| --------------------------------------------- | ------- |
| MTU                                           | 9000    |
| VLAN ID                                       | 5       |
| CC configuration                              | 2x2     |
| Numerology                                    | 1       |
| Bandwidth                                     | 100     |
| Alpha value                                   | 0       |
| Beta value                                    | 0       |
| DL Carrier Frequency                          | 0       |
| UL Carrier Frequency                          | 0       |
| DL compression                                | 9bitBFP |
| DL (PDSCH) eaxcid list                        | 0,1     |
| DL mixed numerology?                          | no      |
| UL compression                                | 9bitBFP |
| UL (PUSCH) eaxcid list                        | 0,1     |
| Is PUSCH and RACH traffic on separate eaxcid? | yes     |
| Additional RACH eaxcid list                   | 2,3     |

:::spoiler `oran.cfg`
```bash=
#
# o-ran.cfg
#
# File for manually overriding configuration options for the m-plane
#
# Authors: Nick Thorn, Wade Oram
#
# Notes:
#   For more info please refer to:
#   https://aeronet.aeroflex.corp/5Gwiki/index.php?title=OranSysRepoCallHomeConfig
#

# ##################################################################################
# Eventually come from radio selection - common to all RU's
# ##################################################################################

# Enable DHCP (default 0)
#UseDhcp=1

# Use ipv6 (default 0)
UseIPv6=0

# Set the vendor id, used in DHCP (default "o-ran-ru/viavi")
#VendorId=xran-ru/viavi

# Automatically start the cu-plane (1) or wait for the m-plane activation to start (0) (default 1)
bAutoStartCUPlane=1

# ##################################################################################
# Eventually come from radio selection - Set individually per RU
# ##################################################################################

# THe uncompressed bit width used by the DU.
# Must be in the range 1 to 255
# Defaults to 16 if no value is provided or the value is ooutside the allowed range
#UncompressedBitWidth=16

# Set the uplane's use of compression. If this entry is not present, the compression settings in this file will not be used
UseUplaneCompression=1

# Set the u-plane compressed bit width - legal values are 9 (default) or 14
# only has significance when UseUplaneCompression=1
UplaneCompressedBitWidth=9

# set the type of RU - single server, RU - over multple servers - split processing, RU over multiple servers symetrical processing
# Values are RuSingleServer, RuMultipleServerSplit and RuMultipleServerSymetrtical. The default value is RuSingleServer
#RUType=SingleServerRu

# Set callhome ip address (default "")
#CallhomeIpAddresses=

# Set m-plane interface ip address (default "", ignored if DHCP is active)
MplaneIpAddress=2001:db8:1:a::1000/64

# set the du mac address - only used if the the mplane data is not populated.
# see:
#   For O-RAN_2_0: /o-ran-processing-element:processing-elements/ru-elements[name='????']/transport-flow/eth-flow/o-du-mac-address
#   For X-RAN_2_0: /xran-processing-element:processing-elements/ru-elements[name='????']/transport-flow/eth-flow/llscu-mac-address
DefaultDuMacAddress=00:11:22:33:44:66

# Sets/overrides the default xml data to load - must match the MPlaneStandard if present
# If not present the file will default to
#    xran_1_1_defaults.csv if the MPlaneStandard is set to xran_1.1
#    oran_2_0_defaults.csv for oran_2.0
#    oran_4_0_FHM_defaults_v001.csv for oran_4.0
SysrepoInitFile=oran_2_0_defaults.csv

# ##################################################################################
#  Common RU configuration and items that can be modified by DU
# ##################################################################################

# Sets the yang models to use, currently xran_1.1 and oran_2.0
# If a CSV is explicitely selected, this value is used only if there is not a header containing the mplane standard in the csv file
# otherwise this is used to select the default csv file when none is specified
# Defaults to oran_2.0 if not present
# MPlaneStandard=oran_4.0

# Set the DHCP DUID enterprise number & string, used for DHCPv6 (default "0002000000ec53363135373430393839")
# Note this is ascii encoded hex string
DuidEn=0002000000ec53363135373430393834

# Set the u-plane vlan-id.
# Eventually this will be unneeded because it is obtained from the m-plane data store (sysrepo)
# which is initialised with the csv file and subsequently modified by the DU (if the DU is M-plane aware).
# Valid values are 1 to 4094. Values outside this range imply no vlan.
LegacyUplaneVlanId=5

# Set the M-plane vlan-id.
# Valid values are 1 to 4094. Values outside this range imply no vlan.
#MplaneVlanId=1

# Set the S-plane vlan-id.
# Valid values are 1 to 4094. Values outside this range imply no vlan.
#SplaneVlanId=3

# Set the console debug verbosity (0 = off, 1 = error, 2 = debug, 3 = info)
#MplaneDebugLevel=3

# Wait for PTP to sync before starting the CU plane. When set to 0, the CU plane will be started without
# waiting for PTP to Sync. This should only be use for M-PLANE tests.
# Note: only applies to standalone builds
#bWaitForPtpSync=1

# Emulate SyncE notifications - this will send a syncE notification along with the PTP notification for DUs that require it.
#bEmulateSyncE=1

# Force single numerology even if multiple numerologies have been configured.
#bSingleNumerology=1

# Schedule PRACH on PUSCH
bPrachOnPusch=0

# Add uniform noise to UL Data, if enabled the minimum bits need to be 4 with a max of 15
#NumNoiseBits=4

# Set CU plane to override Frequency offset value using CplaneType3FreqOffsetVal
#bCplaneType3FreqOffsetOverride=0

# The CplaneType3FreqOffsetVal use by RU.
# Cplane Type 3 freqOffset has a range of +/- BW/2 in units of half SC, so range = +/- (12 * NumRbsInBw / 2) * (ScsForNumerology/PrachScs) * 2.
# For 100Mhz bandwidth below are valid range of values for each numerology considering minimum PRACH SCS 1.25kHz for Mid-band.
# Numerology0:-39600 to 39600 Numerology1:-78624 to 78624 Numerology2:-77760 to 77760 Numerology3:-792 to 792 Numerology4:-408 to 408
#CplaneType3FreqOffsetVal=-3276
```
:::

| Parameters               | value                 |
| ------------------------ | --------------------- |
| bAutoStartCUPlane        | 1                     |
| UseUplaneCompression     | 1                     |
| UplaneCompressedBitWidth | 9                     |
| DefaultDuMacAddress      | 00:11:22:33:44:66     |
| SysrepoInitFile          | oran_2_0_defaults.csv |
| LegacyUplaneVlanId       | 5                     |

### Step1.2 Bring up TM500(cloudUE)
- In Control PC, use SSH to access TM500 server(192.168.8.67).

![image](https://hackmd.io/_uploads/B13RcGuaT.png)

- Fill in FTP_USER and ETH0_ADDR in `cuedock.yaml`.
```bash=
cd installcue/
vim cuedock.yaml
FTP_ADDR = 192.168.8.68 // control PC IP
ETH0_ADDR = 192.168.8.67 // cloudUE ETH0 IP
```
- start docker and run up cloudUE
```bash=
# start docker
sudo systemctl start docker

# Install cloudUE on docker:
cd installcue/
sudo docker compose -f cuedock.yaml up -d
```
![image](https://hackmd.io/_uploads/BkzASkg5T.png)
- check cloudUE container is running up properly
```bash=
sudo docker ps
```
![image](https://hackmd.io/_uploads/HkYqIPHC6.png)

- Then you can telnet to TM500(192.168.8.67) to see the log.

![image](https://hackmd.io/_uploads/BkNvkqMY6.png)

<!-- :::warning
- If you get crash dump you can try to restart docker.
```bash=
# Remove cloudUE from docker:
sudo docker compose -f cuedock.yaml down
```
- After remove you need to bring up cloudue again
```bash=
sudo docker compose -f cuedock.yaml up -d
```
- Make licience up
```bash=
sudo docker ps
sudo docker exec -it  <container id> /bin/bash
rm -rf sda1
exit
```
:::
 -->
 
### Step1.3 TM500 PTP Synchronization
>Check in control PC telnet window
- PTP in TM500 will sync automatically. If you see the log below it sync successfully.

![image](https://hackmd.io/_uploads/Hk9-uTgqT.png)

### Step1.4 Use TMA to control TM500
### Connection with TM500
![image](https://hackmd.io/_uploads/Byq1Lye9a.png)

#### Wait until you see this log stop in ==telnet== window, you can use TMA to connect TM500.
- Click TMA icon in control PC, it is in the path of `C:\Program Files (x86)\VIAVI\TM500\5G NR - NLC 1.4.0\Test Mobile Application/TMA`

![image](https://hackmd.io/_uploads/H1D5mq3o6.png)
- Chose EXT-MUE then click start TMA.

![image](https://hackmd.io/_uploads/S12zVc2sT.png =x300)
#### New Session


Wait offset < 100
![image](https://hackmd.io/_uploads/SJCjW6u8Jx.png)
▲ phc2sys logs

### Step 3.3 Run gNB
:::warning
- These command only need to do one time.
1. Link the ip for O-DU High
```bash=
sudo ifconfig em2:ODU 192.168.130.81
sudo ifconfig em2:CU_STUB 192.168.130.82
```
2. Set the virtual function to DPDK
3. 
```bash
# Create VF and bind VF with DPDK
cd ~/intel_sw/phy/cvl.sh
sudo su
./cvl.sh
exit
```
:::
:::spoiler cvl.sh
```
echo "0" > /sys/class/net/ens1f1/device/sriov_numvfs

echo "1" > /sys/class/net/ens1f1/device/sriov_numvfs

sleep 5

sudo ip link set ens1f1 vf 0 mac 00:11:22:33:44:66 vlan 5 qos 1 spoofchk on trust off
#sudo ip link set ens1f1 vf 1 mac 00:11:22:33:44:89 vlan 5 qos 1 spoofchk on trust off

modprobe vfio_pci

sudo /usr/local/bin/dpdk-devbind.py --bind vfio-pci 0000:70:11.0

sudo ifconfig ens1f1 mtu 1500 
sudo ethtool -G ens1f1 rx 4096 tx 4096
```

:::

3. Run Application
:::info
order of run up:
1. [FlexRAN](#1-FlexRAN)
2. [xFAPI](#2-xFAPI)
3. [OAI CU](#3-CU)
4. [OSC DU](#4-ODU-High)
:::

:::warning
#### Before running you need to check the bus info and RU mac address `PciBusAddoRu0Vf` and `oRuRem0Mac0`
> /FlexRAN/l1/bin/nr5g/gnb/l1/xrancfg_sub6.xml
```
    <!-- O-RU 0 -->
    <PciBusAddoRu0Vf0>0000:70:11.0</PciBusAddoRu0Vf0>
    <PciBusAddoRu0Vf1>0000:70:11.1</PciBusAddoRu0Vf1>
    <PciBusAddoRu0Vf2>0000:51:01.2</PciBusAddoRu0Vf2>
    <PciBusAddoRu0Vf3>0000:51:01.3</PciBusAddoRu0Vf3>
```
```
    <!-- remote O-RU 0 Eth Link 0 VF0, VF1-->
    <oRuRem0Mac0>10:70:fd:14:1c:10</oRuRem0Mac0>
```


:::

### Bring up FlexRAN + xFAPI + O-DU HIGH + OAI CU

#### 1. FlexRAN
```bash=
sudo su
cd /home/ubuntu/intel_sw/FlexRAN/l1/bin/nr5g/gnb/l1/
source ../../../../../../phy/setupenv.sh 
./l1.sh -xran
```
**Wait belows logs show:**
```
'''
L1 start tick is 1420814686800159
step  1 end tick[1420817993294819], used time[2363.470215(ms)]
step  2 end tick[1420822824888853], used time[3453.605225(ms)]
step  3 end tick[1420827714811245], used time[3495.298096(ms)]
total elapsed time [9312.373000(ms)]

PHY>welcome to application console
```

#### 2. xFAPI
```bash=
sudo su
cd /home/ubuntu/intel_sw/xFAPI/bin/
source ../loadenvvar.sh 
./run_xfapi.sh 
```

#### 3. CU
run OAI CU or CU Stub
##### OAI CU
```
cd ~/openairinterface5g/cmake_targets/ran_build/build
sudo RFSIMULATOR=server ./nr-softmodem --rfsim --sa -O ../../../targets/PROJECTS/GENERIC-NR-5GC/CONF/cu_gnb.conf
```
##### CU Stub
```bash=
sudo su
cd /home/ubuntu/intel_sw/upstream-l2/bin/cu_stub
./cu_stub
```

#### 4. ODU-High
```bash=
sudo su
cd /home/ubuntu/l2_ntust/o-du-l2/bin/odu/
./odu 
```

[Complie Steps](#Compile-OSC-DU)


### Step 3.5 Check CN connection with DU
![image](https://hackmd.io/_uploads/Sy_V9-_rkg.png)


## 4. Interoperability between DU and RU
### Step 4.1 Check DU connection at RU side
- Type `FORW MTE GETRUSTATS` in command line.
- Make sure there is no too much early and late packet.

![image](https://hackmd.io/_uploads/SkN7rBl3T.png)
```
FORW MTE GETRUSTATS
```
## Catch PCAP in TM500
### using dpdk_cap()
- Telnet to the FH Server port 23
- Format : dpdk_cap(`<index>`, `<cap_size_in_mb>`)
	- `<index>` is the eth port eth2=0, eth3=1
	- `<cap_size_in_mb>` is the total size to capture
	- example : dpdk_cap(0,1000), captures1000MB files from eth2
#### 1. CTRL + ENTER in telnet command line
![image](https://hackmd.io/_uploads/rkiRi5u9a.png)

#### 2. enter dpdk_cap(0,50) and use CTRL + ENTER to stop catching log
- dpdk_cap(0,50) will catch 50 mb.

![image](https://hackmd.io/_uploads/Byun3c_qT.png)

#### 3. Log will save in folder
- path : `\VIAVI\TM500\5G NR - NLC 1.4.0\ppc_pq\public\ftp_root\`

![image](https://hackmd.io/_uploads/S1f8Aqu5p.png)

### Step 4.2 Check RU connection at DU side
- The packet count in FlexRan log should increase.

## 5. Run UESIM

### Cell search and UE configure script setting
#### Edit properties
1. Press Edit properties our double click `Configuration Radio Context`

![image](https://hackmd.io/_uploads/B1MZTgI5a.png)

2. Validate the parameter you change then save it.

![image](https://hackmd.io/_uploads/BkxOhSJ3Lyx.png)

### [Opt] collect UE logs
:::info
reference: TM500 5G测试系统操作指导手册(基本操作篇) 
:::

1. Press `Session` > `New Session` to clear collect preriod
![image](https://hackmd.io/_uploads/SkrkIy3Syg.png =80%x)

2. Click `Current Session` and make sure time is refresh
![image](https://hackmd.io/_uploads/Syq3Ikhryg.png)

3. Click `Logging Controller` to choose what we will collect
![image](https://hackmd.io/_uploads/SyM_PynHkx.png =60%x)
 
 If we tick `log`, it will be saved in file. 
 If we tick `view`, it will be showed on UI.
 
For Basic, use `Protocol log`

4. Click Red Button to start recording logs
 ![image](https://hackmd.io/_uploads/rJ-9_JhrJl.png =60%x)

5. Click Red Button to stop recording logs after all testing case
![image](https://hackmd.io/_uploads/SJngKk2Skl.png =60%x)

6. Click this button to convert data
![image](https://hackmd.io/_uploads/SkS0Yynryl.png)

Wait the belows log show, which means process is done
![image](https://hackmd.io/_uploads/S1IzcJnBke.png)

7. Click `Currect Session` and click `Export` > `To Zip`
![image](https://hackmd.io/_uploads/ByO4s12rJg.png)
After this we can get a folder include all files

#### Sample Result
> 241227_012249_session\241227_012249_session_241226_172541\241227_012256\241227_012256_DESKTOP-LS2MKBL_PROT_LOG_NAS_RRC_ALL_UE00000.log
![image](https://hackmd.io/_uploads/SkQK3JnBye.png)


#### Init command
![image](https://hackmd.io/_uploads/BkXRHshe0.png =x500)

:::spoiler Init command detail
```bash=
SETP L0_UL_CTRL_NR_ENABLE_UL_POWER_STATS 1
SETP L0_UL_CTRL_NR_ENABLE_UL_POWER_CONTROL 0
SETP L0_UL_CTRL_NR_APPLY_SUCCESSIVE_TIMING_ADVANCE 2

SETP NR_L0_PDSCH_BRP_ENABLE_HARQ_COMBINING 1
#SETP NR_L0_DL_SRP_PDSCH_FREQ_CORRECTION 2

#####SETP L1_NR_ENABLE_CSI_CONFIG 1
SETP L1_NR_MAX_NUM_SIMULTANEOUS_BLIND_DETECTS 9999
SETP L1_NR_ENABLE_CSI_RESOURCE_UNIQUENESS_WARNINGS 0

SETP L2_MAC_NR_UL_DL_SLOT_OFFSET 2
SETP L2_MAC_NR_UL_DL_PUCCH_OFFSET 2
#SETP L2_MAC_NR_ENABLE_PUCCH_WITH_PUSCH 1
SETP L2_MAC_NR_ENABLE_HARQ_CONTENTION_CHECK 0
SETP L2_MAC_NR_NUM_UES_PUCCH 64
SETP L2_MAC_NR_NUM_UES_PUSCH 64
SETP L2_MAC_NR_NUM_UES_PREAMBLE 1

#SETP NAS_NR_ENABLE_R15_DEC_18 1
SETP NAS_NR_ENABLE_R15_JUNE_19 1
#SETP NAS_NR_ENABLE_R15_DEC_19 1

SETP NAS_NR_ENABLE_EN_NW_SLICING 0
SETP NAS_ENABLE_INDICATIONS_IN_MTS_MODE 1

# SETP NR_UL_RTT_VERBOSE_REPORT 1
# SETP MTE_NR_RAV_INTERNAL_BAND_79_WORKAROUND 1

SETP L0_DL_SRP_NR_SET_MAX_PDCCH_DMRS_QUALITY_IND 1
SETP L0_ORP_NR_DL_GAIN 30

#SETP L1_NR_SCS30KHZ_USE_CASE_B_FOR_CELL_SEARCH 1

SETP L1_NR5G_VECTOR_GENERATED_BCH_DATA 1
```
:::

#### Configure Radio Contexts

| Parameters                           | value            |
| ------------------------------------ | ---------------- |
| Duplex                               | TDD              |
| Cell Id                              | 1                |
| Downlink carrier frequency (100 kHz) | 34507.2 (100kHz) |
| System bandwidth (MHz)               | 100              |
| AbsoluteFrequencyPointA (100 kHz)    | 34015.8 (100kHz) |
| AbsoluteFrequencySSB (100 kHz)       | 34015.8 (100kHz) | 



<!-- ### Define MTS Cells for Attach UE test

![image](https://hackmd.io/_uploads/HJu_FfIqT.png =x600)

| Parameters             | value |
| ---------------------- | ----- |
| Cell Id                | 1     |
| DL Frequency (100 kHz) | 34002 | -->

### UESIM do cell search
#### 1. Run the init command
![image](https://hackmd.io/_uploads/HyHPIBgnp.png =x500)

#### 2. Run the cell ssearch test case
![image](https://hackmd.io/_uploads/BklX7989p.png)

#### Result
![image](https://hackmd.io/_uploads/S1NA8reha.png)