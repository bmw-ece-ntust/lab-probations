---
title: O-RAN overview.
tags: [ORAN]

---

![](https://i.imgur.com/JORnn3y.png =150x)@NTUST
# O-RAN overview.
>[name=Ravi][color=#38c16a]

:::success
**Purpose-** To develop a basic understing of O-RAN.
:::

## **Basic concept of O-RAN**

---

:::info
#### :memo: **Outline:**
[TOC]
:::

### O-RAN verticles

* 1 - O-RAN architecture and specifications.
* 2- Open software for the O-RAN.
* 3- Testing and integration of O-RAN implementations.

![image](https://hackmd.io/_uploads/HyTv5lsK1x.png)

### Working groups in O-RAN

1️⃣ WG1: Use Cases and Overall Architecture.
* Defines the overall Open RAN architecture and use cases.
* Specifies key interfaces and functional splits.
* Ensures interoperability among different vendors.

2️⃣ WG2: The Non-Real-Time RAN Intelligent Controller (Non-RT RIC) and A1 Interface
* Develops the Non-RT RIC for AI/ML-driven automation.
* Standardizes the A1 Interface for rApps to communicate with the Non-RT RIC.
* Focuses on policy management, network analytics, and AI model training.

3️⃣ WG3: The Near-Real-Time RAN Intelligent Controller (Near-RT RIC) and E2 Interface
* Defines the Near-RT RIC for real-time optimizations (xApps).
* Standardizes the E2 Interface for RIC to communicate with O-CU, O-DU, and gNB.
* Develops APIs for xApps to optimize network performance.

4️⃣ WG4: Open Fronthaul Interfaces
* Develops the Split 7.2x fronthaul interface for O-DU ↔ O-RU communication.
* Focuses on eCPRI-based fronthaul standardization.
* Enables interoperability between different RU and DU vendors.

5️⃣ WG5: Open Transport Interfaces
* Specifies interfaces for transport networks connecting Open RAN components.
* Focuses on xHaul solutions (Fronthaul, Midhaul, Backhaul).
* Ensures end-to-end latency and QoS guarantees.

6️⃣ WG6: Cloudification and Orchestration
* Defines cloud-native Open RAN architectures.
* Works on virtualization of O-CU, O-DU, and RIC functions.
* Develops Kubernetes-based orchestration models for Open RAN.

7️⃣ WG7: White-box Hardware
* Develops white-box RU, DU, and CU hardware for Open RAN.
* Ensures compatibility with COTS (Commercial Off-The-Shelf) hardware.
* Focuses on FPGA, x86, and ARM-based platforms.

8️⃣ WG8: Stack Reference Design
* Provides reference software stack architectures for O-CU and O-DU.
* Ensures alignment with 3GPP and O-RAN standards.
* Works with open-source projects like O-RAN SC (Software Community).

9️⃣ WG9: Open RAN Security
* Defines security frameworks for Open RAN components.
* Focuses on Zero Trust security models.
* Addresses data encryption, authentication, and network protection.

🔟 WG10: Testing and Integration
* Develops testing methodologies for O-RAN interoperability.
* Defines test suites, CI/CD pipelines, and compliance frameworks.
* Works on integration with open-source testbeds (e.g., O-RAN SC, TIP).

1️⃣1️⃣ WG11: RAN Slicing
* Defines mechanisms for RAN slicing in Open RAN.\n- Ensures multi-tenancy and network slicing capabilities.
* multi-tenancy - Software multitenancy is a software architecture in which a single instance of software runs on a serv

1️⃣2️⃣ WG12: AI/ML Framework
* Focuses on AI/ML models for Open RAN optimization.
* Develops AI training pipelines for rApps and xApps.
* Works on AI-driven traffic prediction, anomaly detection, and interference management.

🔹 3. Focus Groups
Apart from WGs, the O-RAN Alliance also has focus groups addressing specific aspects:

* Open Source Focus Group (OSFG) – Works on open-source RIC, O-CU, and O-DU implementations.\n- Plugfest Focus Group – Conducts interoperability testing across vendors.


### O-RAN Evolution

![image](https://hackmd.io/_uploads/ryh15biFkl.png)


### Seperation of layers

![image](https://hackmd.io/_uploads/rkzrq-otJe.png)

### O-RAN Architecture(Layered View)


![image](https://hackmd.io/_uploads/B1e4hbst1g.png)

### O-RAN Architecture (Interface View)

![image](https://hackmd.io/_uploads/S1u8SMsYJx.png)


### O-RAN Interfaces

1. A1 Interface

    Connects: Non-Real-Time RIC (RAN Intelligent Controller) ↔ Near-Real-Time RIC
    Function: Supports policy-based guidance and AI/ML model updates for network optimization.

2. E2 Interface

    Connects: Near-Real-Time RIC ↔ O-CU (Central Unit) / O-DU (Distributed Unit)
    Function: Enables near-real-time optimization and control of RAN elements.

3. O1 Interface

    Connects: Service Management and Orchestration (SMO) ↔ O-RAN Network Functions (O-CU, O-DU, O-RU)
    Function: Provides FCAPS (Fault, Configuration, Accounting, Performance, Security) management for O-RAN components.

4. O2 Interface

    Connects: SMO ↔ Cloud Infrastructure
    Function: Facilitates orchestration and management of cloud resources supporting O-RAN functions.

5. Open Fronthaul (F1, W1, E1, Xn, NG, and A interfaces)

    * Lower Layer Split (LLS) - Open Fronthaul (between O-DU and O-RU):
        * M-Plane (Management Plane): Manages O-RU via O1 interface.
        * C/U-Plane (Control/User Plane): Handles real-time data and control signaling.
        * S-Plane (Synchronization Plane): Ensures time synchronization between O-RU and O-DU.
    * Higher Layer Split (HLS) - F1 Interface (between O-CU and O-DU):
        Separates CU and DU to enable vendor interoperability.
    Other Interfaces (W1, E1, Xn, NG, A):
       * W1: Connects CU-UP and CU-CP.
       * E1: Connects CU-CP and CU-UP.
        * Xn: Connects gNB nodes.
        * NG: Connects CU to the 5GC (5G Core).
        * A: Connects CU to the 4G EPC (Evolved Packet Core) for NSA (Non-Standalone) operation.

### O-RAN components:

1. Service Management and Orchestration (SMO)

    Role: Manages the entire O-RAN system, handling FCAPS (Fault, Configuration, Accounting, Performance, and Security).
    Interfaces: O1 (to O-RAN network functions), O2 (to cloud infrastructure), A1 (to Non-RT RIC).
    Functionality: AI/ML-driven automation, lifecycle management, and policy enforcement.

2. RAN Intelligent Controller (RIC)

O-RAN introduces two types of RICs for intelligent RAN optimization:
a. Non-Real-Time RIC (Non-RT RIC)

    Role: Provides long-term policy optimization and AI/ML model training.
    Time Scale: >1 second (non-real-time).
    Interfaces: A1 (to Near-RT RIC), O1 (to SMO).
    Functionality: Uses AI/ML to optimize the RAN via policies and control loops.

b. Near-Real-Time RIC (Near-RT RIC)

    Role: Optimizes RAN performance in near-real-time by executing xApps.
    Time Scale: 10ms - 1 second.
    Interfaces: E2 (to O-CU/O-DU), A1 (to Non-RT RIC).
    Functionality: Executes xApps to control and optimize RAN functions dynamically.

3. Open RAN Nodes (O-CU, O-DU, O-RU)

The RAN hardware is disaggregated into three functional units:
a. O-CU (O-RAN Central Unit)

    Role: Handles higher-layer processing (RRC, PDCP).
    Interfaces:
        F1 (to O-DU)
        E1 (between CU-CP and CU-UP)
        Xn (to other O-CUs)
        NG (to 5G Core).
    Functionality: Manages control and user-plane functions, with CU-CP and CU-UP separation.

b. O-DU (O-RAN Distributed Unit)

    Role: Performs lower-layer processing (RLC, MAC, part of PHY).
    Interfaces:
        F1 (to O-CU)
        Open Fronthaul (to O-RU).
    Functionality: Optimizes latency-sensitive tasks and interacts with Near-RT RIC.

c. O-RU (O-RAN Radio Unit)

    Role: Handles RF processing and lower PHY functions.
    Interfaces: Open Fronthaul (to O-DU).
    Functionality: Sends/receives radio signals, supporting MIMO and beamforming.

4. Cloud Infrastructure

    Role: Provides cloud-based execution for O-RAN components.
    Interfaces: O2 (to SMO).
    Functionality: Runs virtualized/containerized network functions (VNFs/CNFs) for O-CU, O-DU, RICs.
    
 ### 🔹 rApps and xApps

1. rApps (Non-Real-Time RIC Applications)

    Run on: Non-Real-Time RIC (Non-RT RIC)
    Time Scale: >1 second (long-term RAN optimization)
    Interfaces: A1 (to Near-RT RIC), O1 (to SMO)
    Functionality: Uses AI/ML to analyze network data, generate policies, and provide long-term optimizations for the RAN.

Examples of rApps

    Traffic Steering rApp: Analyzes long-term traffic patterns and suggests policy-based routing changes.
    Energy Savings rApp: Monitors power consumption and enables energy-efficient RAN configurations.
    Anomaly Detection rApp: Uses AI/ML to detect abnormal behavior in the network.
    Subscriber QoE rApp: Optimizes user experience by analyzing QoE (Quality of Experience) data.
    RAN Slice Management rApp: Allocates network slices based on demand and policies.

2. xApps (Near-Real-Time RIC Applications)

    Run on: Near-Real-Time RIC (Near-RT RIC)
    Time Scale: 10ms - 1 second (near-real-time RAN control)
    Interfaces: E2 (to O-CU/O-DU), A1 (to Non-RT RIC)
    Functionality: Controls RAN functions dynamically to optimize performance in real-time.

Examples of xApps

    Interference Management xApp: Reduces interference between neighboring cells by adjusting power levels.
    Load Balancing xApp: Adjusts user connections across different cells to prevent congestion.
    Mobility Optimization xApp: Improves handovers and reduces dropped calls.
    Beamforming Optimization xApp: Dynamically adjusts beam patterns to enhance coverage and capacity.
    QoS Control xApp: Ensures priority traffic (e.g., emergency calls, video streaming) gets higher bandwidth.

Key Differences: rApps vs xApps



| Feature | rApps | xApps |
| -------- | -------- | -------- |
| Runs on    | Non-RT RIC     | Near-RT RIC     |
| Time Scale | >1 second (long-term)     |10ms - 1 second (real-time)    |
| Function     | Policy-based optimization     | Real-time controlText     |
| Interfaces     | A1, O1     | E2, A1     |
| Example Apps     | Energy savings, anomaly detection, RA    | Load balancing, handover optimization, interference management    |

