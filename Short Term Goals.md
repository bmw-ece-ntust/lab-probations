---
title: Short Term Goals
tags: [January, ShortTermGoal, 30 Dec 2024]

---

![](https://i.imgur.com/JORnn3y.png =150x)@NTUST

>[name=Ravi][color=#38c16a]
## :book: January
###### tags: `January` `ShortTermGoal` 

### :dart: Short Term Goal


## Figure out the problem of the low throughput in Metanoia’s RU.

:::info
* ### Understand the [Integration of OAI gNB(BBU version/branch: develop/commit 68191088a) + JURA RU(SDK v2.2.2) on R750](https://hackmd.io/m3WEoEq7TxCz-hIm9ATnmA?both#2-Finding-in-pcap-log-split-e2e-pcap)




## Steps followed

> 1- Go through [Integration of OAI gNB(BBU version/branch: develop/commit 68191088a) + JURA RU(SDK v2.2.2) on R750](https://hackmd.io/@Summer063/ryDBN4Qpn/https%3A%2F%2Fhackmd.io%2F%40Summer063%2FHka6IP-Q1e#Internet-access) and [Integration of OAI gNB(BBU version/branch: develop/commit 168b172f9) + JURA RU(SDK v2.2.2) on R740](https://hackmd.io/@Summer063/ryDBN4Qpn/%2F%40Summer063%2FHyjno5GhA%3Fstext%3D77%253A98%253A0%253A1735283541%253AAE3s11)


> 2- Check the [Integration of OAI gNB(branch: develop) + TM500](https://hackmd.io/@Summer063/ryDBN4Qpn/%2F%40Summer063%2FrJ8oAM-Ap%3Fstext%3D179%253A47%253A0%253A1735291193%253AjucGqm)

> 3- Went through the pcap logs of [F1 log for OAI CU +OAI DU](https://hackmd.io/@Johnson-72/HJhVtK9rkl?stext=432%3A25%3A0%3A1735288545%3AaMDArl) and  [FH log for OAI CU/DU + TM500(optional)](https://hackmd.io/@Johnson-72/HJhVtK9rkl?stext=633%3A38%3A0%3A1735288908%3A9frViq).

### Finding in Pcap logs

## 1. Findings in pacp log [F1 log for OAI CU +OAI DU](https://hackmd.io/@Johnson-72/HJhVtK9rkl?stext=432%3A25%3A0%3A1735298927%3AMxSB5l)

1- UE(192.168.8.29) registration is succesful.
![image](https://hackmd.io/_uploads/BJ3TNWnBJe.png)

2- Control Plane NAS layer established.
![image](https://hackmd.io/_uploads/SyKjtZhryl.png)

3- After Initial context setup UE send UE Capability information to AMF. 
![image](https://hackmd.io/_uploads/S1Tr9bnH1g.png)

4- PDU session established.
![image](https://hackmd.io/_uploads/Hyg7n-3S1e.png)

5- Verify UE has internet cnnection
![image](https://hackmd.io/_uploads/r1kfpbhr1g.png)

6- UE can estbalish HTTP connection
![image](https://hackmd.io/_uploads/Bk7VkMnH1l.png)

7- There are issue

* The log indicates that the packet arrived out of order, which can be a symptom of network issues.
* There was a problem reassembling the TCP segments, with a possible retransmission that caused overlap.
* The errors, including out-of-order packets and reassembly problems, suggest that there might be network issues such as congestion, packet loss, or jitter affecting the connection between the two IPs.
![image](https://hackmd.io/_uploads/HJwIzG3rkx.png)


8- (RST) flag, which means the sender is requesting that the connection be immediately reset.

* The connection being no longer valid.
* An error detected on the connection.
* The server or client deliberately closing the connection.
* A timeout or unexpected condition on the server or client.

![image](https://hackmd.io/_uploads/SJKzrM3HJe.png)




## Next Steps

1- Try checking the servers.
2- I want to perform test again.


## 2. Finding in pcap log split e2e pcap. 

###### tags: `30 Dec 2024`
1- UE context is relesed in the middle to the test.

`14035	222.285885	192.168.8.43	192.168.8.21	NGAP	98	UEContextReleaseRequest`

This request is initiated by server 192.168.8.43.
So need to explore more here and compare IEs with following code.

```
UEContextReleaseRequest ::= SEQUENCE {
 protocolIEs ProtocolIE-Container {{UEContextReleaseRequest-IEs}},
 ...
}
UEContextReleaseRequest-IEs S1AP-PROTOCOL-IES ::= {
 { ID id-MME-UE-S1AP-ID CRITICALITY reject TYPE MME-UE-S1AP-ID PRESENCE mandatory }|
 { ID id-eNB-UE-S1AP-ID CRITICALITY reject TYPE ENB-UE-S1AP-ID PRESENCE mandatory }|
 { ID id-Cause CRITICALITY ignore TYPE Cause PRESENCE mandatory }|
 { ID id-GWContextReleaseIndication CRITICALITY reject TYPE GWContextReleaseIndication PRESENCE optional },
 ...
} 
```




![image](https://hackmd.io/_uploads/Sk-duG2ryg.png)


## 3. Finding in Log file 0920_free

```
dlsch_rounds 663/22/3/1, dlsch_errors 1, pucch0_DTX 24, BLER 0.14472 MCS (1) 6
```
At dlsch, Shows high BLER and modulation(table 1)with Qm  = 6.

![image](https://hackmd.io/_uploads/H1K7ZxlI1l.png)


The BLER is higher but not that much that (as it should be only BLER <= 10%) it should effect throughtput to cause 90Mbps throughput where expected 800 Mbps.

Steps can be followed to reduce the BLER are

* Noisy signal transmission by the network. `` Seems a case as check pcap log``
* Not maintained desired levels of RSRP power levels. ``*Not the case as per logs*``
* Mismatch of DL grants parameters. ``Not the case as per logs``
* And also may be possibility to check physical connections of NW side. ``Need to check``

>>Modulation techniques twicking can help us to check if we are able to achieve higher throughput.

:::


