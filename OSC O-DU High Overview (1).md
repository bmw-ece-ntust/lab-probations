---
title: OSC O-DU High Overview
tags: [O-DU, OSC]

---

![](https://i.imgur.com/JORnn3y.png =150x)@NTUST

# OSC O-DU High Overview
>[name=Ravi][color=#38c16a]

:::success
Goal: 
* Understand the functionality, Architecture and purpose of OSC DU.
* Integartion of DU-high.
* Performance measurement.

:::

:::warning
Refrences:
* [O-DU High Overview — o-du-l2 master documentation](https://docs.o-ran-sc.org/projects/o-ran-sc-o-du-l2/en/latest/overview.html)
* [EVERYTHING YOU NEED TO KNOW ABOUT OPEN RAN](https://www.parallelwireless.com/wp-content/uploads/Parallel-Wireless-e-Book-Everything-You-Need-to-Know-about-Open-RAN.pdf)

:::

:::info
The O-DU (Open Distributed Unit) High is a critical component in the 5G NR (New Radio) protocol stack, specifically designed to implement the functional blocks of the L2 layer in Standalone (SA) mode. This includes essential layers such as the NR MAC (Medium Access Control), NR Scheduler, and NR RLC (Radio Link Control) layers
:::

:::info
#### :memo: **Outline:**
[TOC]
:::

## Architecture:
![image](https://hackmd.io/_uploads/HyQxtSCIyl.png)

In 5G NR (New Radio) StandAlone (SA) mode, the O-DU (O-RAN Distributed Unit) plays a crucial role in managing the lower layers of the protocol stack, specifically the Layer 2 (L2) functionalities. These layers include the NR MAC (Medium Access Control), NR Scheduler, and NR RLC (Radio Link Control) layers.


 Modules sharing a given color belong to one thread. O-DU architecture can be defined at a thread level as follows:

* **Thread 1: O-DU thread :** The O-DU thread typically refers to a processing thread within the O-DU (Open Distributed Unit) in a 5G network. The O-DU is responsible for handling mid-layer protocol functions and plays a crucial role in processing and coordinating radio signals between the Radio Unit (O-RU) and the Central Unit (O-CU). 
* **Thread 2:** DU APP inclusive of Config Handler, DU Manager, UE Manager, and ASN.1 Codecs.
* **Thread 3:** 5G NR RLC DL and MAC (inclusive of 5G NR SCH and Lower MAC)
* **Thread 4:** 5G NR RLC UL

* **Thread 5: SCTP Handler:** The SCTP (Stream Control Transmission Protocol) Handler plays a crucial role in managing the communication between different components in a 5G network, especially over the NG interface (e.g., between the gNB and the AMF). SCTP is used in 5G for reliable message-oriented transport of signaling messages, such as NGAP (Next Generation Application Protocol) or XnAP in the RAN.
* **Thread 6:** Lower MAC Handler
* **Thread 7: EGTP Handler:** Managing user plane and control plane traffic. It is primarily used in the S1-U, S5/S8, N3, and N9 interfaces, ensuring efficient encapsulation and tunneling of data between network nodes.
* **Thread 8: O1 :** O1 refers to the Operations, Administration, and Maintenance (OAM) interface, The O1 interface is used for managing the lifecycle of O-RAN components and ensuring efficient operation, administration, and maintenance of the network.

## O-DU High Modules
 
 * **1- DU-APP :** This module configures and manages all the operations of O-DU. It interfaces with external entities.
 
 * ** 2- 5G NR RLC :**This module provides services for transferring the control and data messages between MAC layer and O-CU (via DU App).

    * 5G NR RLC UL and 5G NR RLC DL are the sub modules of this module that implement uplink and downlink functionality respectively.
 * **3- 5G NR MAC :** This module uses the services of the NR physical layer to send and receive data on the various logical channels.
 * **4- 5G NR SCH :** This module is completely encapuslated withing 5G NR MAC i.e. all interactions of the 5G NR SCH is via the 5G NR MAC.Schedules resources in UL and DL for cell and UE based procedures.
 * **5- O-DU Utility and Common Functions** : These modules contain platform specific files and support O-DU High functionality and message exchanges.
 * **6- O1 Module :** O1 module runs as a thread in O-DU High.
   
   ![image](https://hackmd.io/_uploads/rkiJxEZwkx.png)
   
## O-DU High Interfaces.

![image](https://hackmd.io/_uploads/rkDAeEZvJx.png)

* **O1** : O-DU High to connected with OAM to manage Operations, Administration, and Maintenance (OAM). OAM in O-RAN is focusing on open and interoperable interfaces, particularly the O1 interface.
* **E2AP :** E2AP supports interaction between the RIC and the RAN components through the E2 interface.The interface allows for programmable control of RAN elements, ensuring more flexible network operations (such as optimizing performance, dynamic resource allocation, and network slicing).
    * **Use case-** E2AP can be used to manage the configuration of network slices by adjusting parameters in real-time based on the demand.

* **F1AP :** O-DU High communicates with O-CU on the F1AP interface. The control message exchanges are on F1-C while data message exchanges are on F1-U interfaces.

* **FAPI :**  FAPI (Functional Application Platform Interface) is a standardized interface that enables communication between the PHY (physical layer) and MAC (medium access control) layers in a base station, such as a Distributed Unit (DU).
* O-DU High to O-DU Low

## Message Flow as per interface
 ### F1AP
 The control message exchanges are on F1-C while data message exchanges are on F1-U interfaces.The below F1AP messages on F1-C are implemented. `Ref- 3GPP 38.473-f60 v15.3`
 
    :small_blue_diamond:**Interface Management**

        * F1 Setup
        * gNB-DU Configuration Update
        * F1 Reset
        * PAGING
        
    :small_blue_diamond:**UE Context Management**

        * UE Context Setup
        * UE Context Modification
        * UE Context Release

    :small_blue_diamond:**RRC Message Transfer**
        
        * Initial UL RRC Message Transfer
        * DL RRC Message Transfer
        * UL RRC Message Transfer
        * RRC Delivery Report

 ### E2AP
 O-DU High communicates with Near RT RIC on the E2 interface. The below E2AP messages are implemented. `Ref- O-RAN.WG3.E2GAP-R003-v03.00 and O-RAN.WG3.E2AP-R003-v03.00`
 
:small_blue_diamond:**Global Procedures**
        
        * E2 Setup
        * E2 Node Configuration Update
        * RIC Service Update
        * E2 Connection Update
        * E2 Removal
        * E2 Reset
        * Error Indication
        
:small_blue_diamond:**Near RT RIC Functional Procedures**
        
        * RIC Subscription
        * RIC Subscription Modification
        * RIC Subscription Modification Required
        * RIC Subscription Delete
        * RIC Subscription Delete Required
        * RIC Indication
        
 ### FAPI
  O-DU High communicates with O-DU Low on the FAPI interface. The below FAPI messages are supported.
  
  :small_blue_diamond:**P5 messages - PHY mode control interface**
        
        * PARAM.request/PARAM.response        
        * CONFIG.request/CONFIG.response
        * START.request
        * STOP.request
        * STOP.indication
:small_blue_diamond:**P7 messages - Main data path interface**
        
        * DL_TTI.request 
        * UL_TTI.request
        * SLOT.indication
        * UL_DCI.request
        * TX_Data.request
        * RX_Data.indication
        * CRC.indication
        * UCI.indication
        * RACH.indication
        
## O-DU High functionality
* [Cell Up and Broadcast Procedure.](https://hackmd.io/ikGQEBScRV2MEiGOu6QU8Q#Cell-Up-and-Broadcast-Procedure)
* [UE Attach](https://docs.o-ran-sc.org/projects/o-ran-sc-o-du-l2/en/latest/overview.html#ue-related-procedure)
* [Closed Loop Automation Procedure](https://docs.o-ran-sc.org/projects/o-ran-sc-o-du-l2/en/latest/overview.html#closed-loop-automation-procedure)
* [O1 Netconf get-alarm list procedure](https://docs.o-ran-sc.org/projects/o-ran-sc-o-du-l2/en/latest/overview.html#o1-netconf-get-alarm-list-procedure)
* [Network Slicing procedure](https://docs.o-ran-sc.org/projects/o-ran-sc-o-du-l2/en/latest/overview.html#network-slicing-procedure)
* [Idle Mode Paging procedure](https://docs.o-ran-sc.org/projects/o-ran-sc-o-du-l2/en/latest/overview.html#idle-mode-paging-procedure)
* [Inter-DU Handover within O-CU](https://docs.o-ran-sc.org/projects/o-ran-sc-o-du-l2/en/latest/overview.html#inter-du-handover-within-o-cu)
* [Inter-CU Handover (Xn-Based)](https://docs.o-ran-sc.org/projects/o-ran-sc-o-du-l2/en/latest/overview.html#inter-cu-handover-xn-based)
* [Discontinuous reception (DRX)](https://docs.o-ran-sc.org/projects/o-ran-sc-o-du-l2/en/latest/overview.html#discontinuous-reception-drx)

### Cell Up and Broadcast Procedure



![image](https://hackmd.io/_uploads/rJMtYmfvJl.png)

1- If O1 enable- SMO sends cell configuration to DU APP. DU APP stores the configurations in its local database.
Else -  DU APP module uses static configuration.

2- The DU APP module of O-DU High sends F1 Setup Request to O-CU. This message contains a list of cells that the O-DU High has been configured with.

3- The O-CU responds with F1 Setup Response. This message contains a list of cells which must be activated.

4- The O-DU High scans the list of cells received and sends corresponding cell configurations to 5G NR MAC.

5- 5G NR MAC, in-turn configures the 5G NR SCH. It also configures the O-DU Low via the Lower MAC module.

6- On receiving the cell config response, DU APP sends a gNB DU Config Update towards the O-CU. The O-CU responds with gNB DU Config Update ACK towards the O-DU High.

7- The DU APP now exchanges F1 Reset message with the O-CU to initialize the UE contexts.
Q.? From where is getting UE context?

8- DU APP sends Cell Start Req towards 5G NR MAC. This message is translated by the Lower MAC into the FAPI message START.request towards the O-DU Low.

9- On receiving START.request, O-DU Low begins to send slot indications towards 5G NR MAC via the lower MAC. The frequency of these slot indications is determined by the numerology(Mu) supported. 5G NR MAC forwards these slot indications to the 5G NR SCH and DU APP modules.

10- When the first slot indication reaches the DU APP, cell is marked as up. If O1 is enabled, DU APP triggers an alarm to SMO to indicate the CELL is UP.

11- The 5G NR SCH, keeps tracking the SSB and SIB1 ocassions on receiving regular slot indications. On detecting the relevant ocassion, 5G NR SCH schedules SSB/SIB1 and forwards the DL Scheduling Information to 5G NR MAC.

12- The 5G NR MAC mutiplexes the PDU and sends SSB/SIB1 packets towards the O-DU Low through the Lower MAC.

TTI- Transmission Time Interval

DL TTI req(SSB)
DL TTI Req(PDCCH)
TX TTI Req(PDSCH)

**F1 Setup Request:**

## UE Pocedures

### Closed Loop Automation Procedure :

Refers to a self-regulating system that automatically optimizes network performance, resolves issues, and manages resources based on real-time data. This is a cornerstone of modern network management, enabling efficient and dynamic operations.

![image](https://hackmd.io/_uploads/rkjv7T7Pye.png)

1- SMO commands ODU-High to bring the cell down via O1 interface.

2- DU-APP module of ODU-High sends GNB-DU configuration update message to O-CU. It contains the details of cell to be deleted. O-CU acknowledges this message by sending GNB-DU configuration update acknowledgment.

3- For each UE, DU APP sends UE Context Release Request to O-CU with information about the to be released. O-CU responds with UE Context Release request. It contains the RRC release message. O-DU high sends this RRC Release message to UE.

4- DU APP then sends UE delete request to MAC and RLC. Once a confirmation is received from both MAC and RLC, DU APP deletes UE from its own database as well.

5- Once all UEs are released, O-DU High sends STOP.Request to L1. L1 responds with stop indication.

6- Once cell has stopped, DU APP sends cell delete request to MAC. On receiving confimation from MAC, DU APP deletes cell information from its own database as well and sends UE Context Release Complete.

7- On receiving cell bring up command from SMO, the complete Cell bring up and UE attach procedure will be repeated (as explained in above sections in Cell Up and Broadcast Procedure).

### O1 Netconf get-alarm list procedure

:::success
Health Status Retrieval scenario of O-DU High health-check. It enables a northbound client(SMO) to retrieve the health of the O-DU High based on the last self-check performed. The alarm-list is provided as the response to the request via O1 Netconf interface.

:::

![image](https://hackmd.io/_uploads/B1ilSTQwyg.png)

1- On the cell state change from de-active to activate, DU APP module raises a cell up alarm message and sends it over the Unix socket using the Alarm Interface API.

2- On other side a Unix socket server, running as a thread, in O1 module receives the cell up alarm message and it passes on the alarm information to the Alarm Manager.

3-Alarm Manager stores the alarm data in a list.

4- Whenever SMO/OAM requires the current alarm list, it sends a Netconf get request. The request is received by the Netopeer Server and a callback method, registered with the Session Handler, is invoked.

5- The callback function fetches the alarm list from Alarm Manager and sends it back to the client (SMO/OAM) via Netconf interface.

### Network Slicing procedure


![image](https://hackmd.io/_uploads/SJHXOTmv1g.png)


1- Once the Cell is UP, Slice Configuration received from O1 to O-DU is processed. DU APP forwards the Slice Configuration Request towards MAC which is further forwarded to Scheduler.

2- Scheduler stores the Slice Configuration in DB and sends the Slice Configuration Response for each Slice to MAC and further towards DU APP. Slice Configuration Procedure completes.

3- Once a UE attaches and PDU session is established then RLC will periodically calculate the Slice Performance Metrics(UL and DL Throughput) for slices configured during UE Context Setup/Modification procedure.

5- RLC sends the Consolidated Slice Metrics to DU APP at every 60 sec duration. This is further forwarded towards SMO/Non-RT RIC.

3- SMO/Non-RT RIC analyses these metrics and may optimize the slice configuration(RRM Policies) for dedicated slice. This is received at MAC and Scheduler as Slice Reconfiguration Request from DU APP.

7- Scheduler updates the received Slice Configuration in its DB and sends back the Slice Reconfiguration Response to MAC and further MAC forwards it to DU APP. Scheduler applies the optimized RRM policies for the dedicated slice.

### Idle Mode Paging procedure

![image](https://hackmd.io/_uploads/BJwesiDPyl.png)


1- When a Paging is received from O-CU and the Cell to be Paged is UP then DU APP will calculate Paging Frame(PF) and i_s(Index of Paging Ocassion/Slot) and groups the Paging of UEs falling on same PF/SFN together and stores in its Cell’s Databse.

2- When a Slot Indication for SFN is received then DU APP extracts the Paging of all UEs whose PF is ahead by PAGING_DELTA and builds Paging RRC PDU. DU APP sends the same via DL PCCH Indication to MAC.

3- MAC forwards to SCH as PAGING INDICATION.

4- SCH stores the Page Message in its DB and when the SLOT_INDICATION for that SFN arrives, SCH performs scheduling and resource allocation for PDCCH (alongwith DCI 1_0 format) and PDSCH channels and sends to MAC through DL PAGING ALLOCATION message.

5- MAC forwards the PAGE to PHY in TX_Data.Request.


### Inter-DU Handover within O-CU

![image](https://hackmd.io/_uploads/BJ37JnwvJg.png)


1- The UE sends Measurement Report message to the source O-DU. This message is sent from O-DU to O-CU in the UL RRC MESSAGE TRANSFER message over F1AP interface.

2- Based on UE Measurement Report, O-CU makes a handover decision to another cell belonging to the target O-DU.

3- The O-CU sends a UE CONTEXT MODIFICATION REQUEST message to source O-DU to query the latest configuration.

4- The DU APP in source O-DU responds with a UE CONTEXT MODIFICATION RESPONSE message that includes latest full configuration information.

5- The O-CU sends a UE CONTEXT SETUP REQUEST message to the target O-DU to create an UE context and setup one or more data bearers. The UE CONTEXT SETUP REQUEST message includes Hand-overPreparationInformation. At target O-DU, DU APP sends UE Create Request to MAC and RLC layers to create the UE context with radio resources and receives UE Create Response from the respective protocol layers.

6- The target O-DU responds with a UE CONTEXT SETUP RESPONSE message if the target O-DU can admit resources for the handover.

7- The O-CU sends a UE CONTEXT MODIFICATION REQUEST message to the source O-DU, which includes RRCReconfiguration message towards the UE. The O-CU also indicates the source O-DU to stop the data transmission for the UE.

8- The source O-DU forwards the received RRCReconfiguration message to the UE and then sends the UE Reconfiguration Request to MAC/Scheduler and RLC layer and get the UE Reconfiguration Response from the respective protocol layers.

9- The source O-DU responds to the O-CU with UE CONTEXT MODIFICATION RESPONSE message.




