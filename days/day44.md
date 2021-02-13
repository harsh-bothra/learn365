# Pentesting BACNet
Index | Section
--- | ---
**1** | Introduction
**2** | Attack Vectors
**3** | Enumeration
**4** | References & Good Reads

___


#### Introduction
```
1. BACNet : Building Automation & Control Networks
2. BACNet is used in the communication system for building automation.
3. BACnet acts as a standard communication protocol enabling interoperability between building devices and systems — controls and automation systems.
4. BACnet presents standard methods for requesting, interpreting, transporting and presenting information between systems from various vendors such as lighting, HVAC, fire systems and security. 
5. In order to achieve interoperability across the wide range of equipment, BACnet specifies three major parts. They are as follows:

    a. The first part specifies different methods for representing building automation equipment in a standard way.
    b. The second part specifies messages which can be sent across to control and monitor different equipment in the network.
    c. The third part specifies a set of applicable LANs (Local Area Network) which can be used for conveying BACnet communications
```

#### How to Test
```
1. Lack of Encryption

- Traffic is not encrypted by default and due to this the data travels in plain text. 
- It can be stolen by the MiTM Attack attempts.

2. Denial of Service

- It is possible to flood the BACNet network in order to perform a denial of service attack.

3. Disable Network Connections 

- This attack is performed by corrupting the routing table in the compromised device. 
- This is done by sharing faulty routing information. 
- Also, a device can be denied network connection by sending false messages to it

4. Wirte Access on the Devices.

- This attack changes the current values of BACnet object property. 
- Thus, it is possible to change the values of the object, creating undesired changes in the network.

5. Lack of Authentication

- BACnet is susceptible to spoofing attacks due to a lack of authentication and authorization. 
- Due to this, devices can generate fake messages and can force other devices to send their messages


```

#### Enumeration 

```
1. Default Port
- 47808

2. Enumeration through NMAP
- nmap --script bacnet-info --script-args full=yes -sU -n -sV -p 47808 <IP>

3. Manual Enumeration 

    pip3 install BAC0
    import BAC0
    bbmdIP = '<IP>:47808'
    bbmdTTL = 900
    bacnet = BAC0.connect(bbmdAddress=bbmdIP, bbmdTTL=bbmdTTL) #Connect
    bacnet.vendorName.strValue

4. Shodan Dorks
- port:47808 instance
- "Instance ID" "Vendor Name"

```

#### References & Good Reads

```
a. https://resources.infosecinstitute.com/topic/bacnet/
b. https://sapsan.on.fleek.co/hacktricks/pentesting/47808-udp-bacnet/
c. https://hitcon.org/2015/ENT/PDF/Building%20Automation%20and%20Control_miaoski.pdf
d. https://www.blackhat.com/docs/us-17/wednesday/us-17-Brandstetter-insecurity-In-Building-Automation-How-To-Create-Dark-Buildings-With-Light-Speed.pdf

```