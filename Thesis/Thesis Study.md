---
title: Thesis Study

---

![](https://i.imgur.com/JORnn3y.png =150x)@NTUST
# Thesis Study for Lab Thesis.
>[name=Ravi][color=#38c16a]

:::success
**Purpose-** To understand the study perform by previous students to make a clear picture of Thesis Topic.
:::

## **1-Study Notes: Open RIC Platform for rApp and xApp Testing**

---

:::info
#### :memo: **Outline:**
[TOC]
:::

## **1. Introduction to Open RIC**
### **1.1 Definition and Purpose**
- The Open RAN Intelligent Controller (**RIC**) is a platform designed to manage and optimize Open RAN networks.
- It enables the development and testing of **rApps (Non-RT RIC applications)** and **xApps (Near-RT RIC applications)**.
- Promotes vendor-agnostic network automation, AI-driven enhancements, and interoperability.

### **1.2 RIC Components**
- **Non-RT RIC**: Manages rApps and operates at a control time scale >1 second.
- **Near-RT RIC**: Hosts xApps for real-time optimizations (~10ms-1s latency).
- **E2 Interface**: Facilitates communication between RIC and Open RAN elements (e.g., O-CU, O-DU).

---

## **2. rApps and xApps: Roles and Functions**
### **2.1 rApps (Non-RT RIC Applications)**
- Operate in the **Non-RT RIC**.
- Provide **long-term network optimizations**, AI/ML model training, and data analytics.
- Example functions:
  - **Energy Efficiency Optimization**
  - **Traffic Prediction and Load Balancing**
  - **Anomaly Detection and Security Enhancements**

### **2.2 xApps (Near-RT RIC Applications)**
- Deployed in the **Near-RT RIC**.
- Provide **real-time optimizations** at low latency.
- Example functions:
  - **Beamforming Control**
  - **Interference Management**
  - **Handover Optimization**

---

## **3. Testing Framework for rApps and xApps**
### **3.1 Testbed Architecture**
- **Simulated RAN Environment**: Allows functional and performance testing.
- **E2 Interface Simulation**: Validates xApp communication with network elements.
- **AI/ML Training & Validation**: Ensures effectiveness of ML-based optimizations.

### **3.2 Key Testing Metrics**
- **Latency**: Time taken for xApps to execute control loops.
- **Accuracy**: How well rApps predict traffic, interference, or other metrics.
- **Scalability**: Ability to handle increasing network loads.

### **3.3 Tools for rApp/xApp Testing**
- **Aether** (ONF’s Open RIC testbed)
- **O-RAN SC RIC** (Open-source RIC implementation)
- **Simulators for UE and gNB interactions**

---

## **4. Open RIC Implementation Challenges**
### **4.1 Interoperability**
- Ensuring seamless integration across multi-vendor Open RAN components.

### **4.2 AI/ML Model Deployment**
- Training and deploying AI/ML models efficiently within rApps and xApps.

### **4.3 Security Concerns**
- Protecting RIC applications from cyber threats and unauthorized access.

---

## **5. Future Directions in Open RIC Development**
- **Enhanced AI-driven optimizations** for self-healing networks.
- **Advanced real-time processing techniques** for xApps.
- **Improved standardization and open-source collaboration** in Open RAN ecosystems.

---

### **Conclusion**
The Open RIC platform is crucial for the evolution of Open RAN, enabling intelligent automation through rApps and xApps. As testing frameworks advance, Open RIC will drive **improved efficiency, security, and performance** in next-generation networks.

---

## **2-Study Notes: Design and Implementation of CSI Report to Support Link Adaptation in OSC O-DU MAC Scheduler**

---

## **1. Introduction**

### **1.1 Overview**

- The thesis focuses on the **Channel State Information (CSI) reporting** mechanism in the **Open Source Community (OSC) O-DU MAC scheduler**.
- CSI reports are used for **link adaptation** to optimize **modulation and coding schemes (MCS)** based on real-time channel conditions.

### **1.2 Importance of CSI Reporting in 5G Networks**

- CSI enables **efficient resource allocation** and **adaptive transmission**.
- Used for **beamforming, power control, and interference management**.
- Plays a crucial role in **Open RAN (O-RAN) implementations**.

---

## **2. Background on OSC O-DU MAC Scheduler**

### **2.1 OSC O-DU (Open Distributed Unit)**

- Part of the **O-RAN Software Community (OSC)** initiative.
- Handles **Layer 2 (MAC) scheduling** and **Layer 1 (PHY) interactions**.
- Implements **dynamic resource allocation algorithms**.

### **2.2 MAC Scheduler Role**

- Determines **which users (UEs) get resources** in a given time slot.
- Uses CSI feedback to adjust **MCS, power levels, and transmission modes**.

---

## **3. CSI Reporting Mechanism**

### **3.1 Types of CSI Reports**

- **Periodic CSI**: Sent at fixed intervals, reports **channel quality indicators (CQI)**.
- **Aperiodic CSI**: Triggered by network conditions, provides detailed feedback.
- **Semi-Persistent CSI**: Optimized for reduced overhead in static environments.

### **3.2 CSI Components in Link Adaptation**

- **CQI (Channel Quality Indicator)**: Defines best MCS for a given channel.
- **PMI (Precoding Matrix Indicator)**: Guides beamforming decisions.
- **RI (Rank Indicator)**: Indicates the optimal number of layers for MIMO transmission.

### **3.3 CSI Feedback in O-DU MAC Scheduler**

- CSI is **collected from UEs** and sent to the MAC scheduler.
- Scheduler **adjusts link parameters dynamically** based on CSI.

---

## **4. Design and Implementation in OSC O-DU**

Testing Architecture-
![image](https://hackmd.io/_uploads/HkEtHvntkx.png)


### **4.1 CSI Report Integration in MAC Scheduler**

- Implemented a **CSI reporting module** in OSC O-DU.
- Added **CQI, PMI, and RI processing functions**.
- Improved scheduler decisions using **real-time CSI feedback**.

### **4.2 Link Adaptation Strategies**

- **Adaptive MCS Selection**: Uses CQI to select optimal **modulation and coding**.
- **Dynamic Resource Allocation**: Assigns RBs (Resource Blocks) based on channel conditions.
- **Interference Mitigation**: Adjusts power and beamforming to avoid interference.

---

## **5. Performance Evaluation**

### **5.1 Simulation Setup**

- Used an **Open RAN testbed** to validate CSI implementation.
- Measured **throughput, latency, and packet loss**.

### **5.2 Key Findings**

- Improved **spectrum efficiency** by **15-20%**.
- Reduced **latency in scheduling decisions**.
- Enhanced **MCS adaptation**, leading to **better user experience**.

---

## **6. Challenges and Future Work**

### **6.1 Challenges**

- **Overhead in CSI reporting** affects system efficiency.
- **Delays in feedback processing** impact real-time scheduling.

### **6.2 Future Enhancements**

- **AI-driven CSI prediction models** for proactive scheduling.
- **Improved compression techniques** to reduce CSI overhead.
- **Integration with Open RIC (RAN Intelligent Controller)** for enhanced automation.

---

### **Conclusion**

The integration of **CSI reporting in the OSC O-DU MAC scheduler** enhances **link adaptation, throughput, and spectral efficiency**. Future improvements will focus on **AI-driven automation and overhead reduction** to further optimize Open RAN networks.

---









