# UPF

The primary role of UPF in 5G system is to provide interconnetion towards the external data network. Data network can be Internet, IMS, enterprise system etc. On any cases, we need UPF to provide connectivity between 5G network and data network. 5G technology is itself a mobile technology which means that the mobile device will keep moving around. In such cases, we need one anchor point to provide a fixed connectivity towards the data network. This is called mobility anchor and UPF provides the functionality as the mobility anchor. For example if a device moves, it will connect to many gNB's, the data network was not able to see that mobile is moving. It will always route the IP traffic to the UPS and then the 5G system takes care of routing the data from the particular UPF to wherever the devices. The functionality of UPF as a mobility anchor toward the external network is fulfilled. Since all the data from the particular data network comes to UPF, it also an ideal spot for measuring the traffic usage and providing charging related information to the charging system. So it can measure exactly the MB and GB of a data that is consumed by a certain device. Suppose, if a device is in idle mode and the the downlink data is scheduled for the device, then in order to make sure the data is not lost the UPF also have a buffering for functionality. It will buffered the downlink information until the device is ready to receive the information after waking up from the idle mode. In addition, the UPF is also responsible for quality of service marking. In external data network we don't know is there any particular quality of service differentiation, but once the data enters in 5G system then we have a different mechanism to provide different quality of service. In the flow, the first step is with the UPF. So the UPF looks at the different data and assign them a different quality of service identifier so that the different application with different quality of service identifiers can be treated differently going forward in the network.

![](/upf1.drawio.png)

Here we can see there are two serial UPF. So UPF have a mechanism to forward certain kind of packet to more central UPF or in other words it might, re-route the traffic already in the earlier part of a core network. This can be used for treating different type of traffic through the different UPF's. 

First half of a diagram indicates the different mechanism that we have for packet detection rule. Whenever there is incoming packet to UPF, the first thing it has to detect what kind of category does this packet fall into Hollister.

For this purpose there is a packet forwarding control protocol (PFCP) which will provide the packet detection rule. And then we have actual packet detection rule (PDRs), to identify what category the incoming packets fall into. If multiple criteria have made, we also have priority mechanism due to which packet are treated accordingly. 

When the actual PDR are passed and criteria is met, then we actually have the instruction set about how to deal with particular packet before it forwarded out of the upf. So there we have forwarding action rule (FARs), should incoming packet be forwarded in a different route or not?. This is done by FAR. 

Next we have buffer action rule (BARs), for example in the case of application like streaming audio or streaming video so there is no need to buffer so that the buffer rule might be dropped the packet if it has to wait for a while. On the other hand, if it is a file transfer, then the buffering rule might say that buffer as much as possible don't drop the packets. 

Next we have quality of service enforcement rule (QERs), there are different application in 5G system so this rule indicates how to assign quality of service identifier for a given kind of IP packet. Then we have uses reporting Rome, maybe we have to report the time for which a PDU session his held or maybe to provide a reporting on the amount of data consumed. There is also an advanced data reporting on what is the average time spent in a buffer by a packet etc, so all this kind of functionality together constitute the UPF and after the packet is detected and handled by FAR, BAR, QER, then the reporting measures are also taken into account and then the packet is forwarded out of the UPF.
