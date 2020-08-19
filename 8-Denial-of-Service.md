# Denial of Service

> ⚡︎ **This chapter has [practical labs](https://github.com/Samsar4/Ethical-Hacking-Labs/tree/master/9-Denial-of-Service)**

DoS attacks can cause the following problems:
- Ineffective services
- Inaccessible services
- Interruption of network traffic
- Connection interference

**Goal:**
- Seeks to take down a system or deny access to it by authorized users


### Botnet 
*Network of zombie computers a hacker uses to start a distributed attack.*
  - Botnets can be designed to do malicious tasks including sending **spam, stealing data, ransomware, fraudulently clicking on ads or distributed denial-of-service (DDoS) attacks.**
  - Can be controlled over HTTP, HTTPS, IRC, or ICQ
  
![botnet](https://www.f5.com/content/dam/f5-labs-v2/article/articles/edu/20190605_what_is_a_ddos/DDoS_attack.png)

---

## <u>Basic Categories</u>

### Volumetric attacks
- Also know as floods, most common type of DDoS.
- Send a massive amount of traffic to the target network with the goal of consuming **so much bandwidth** that users are denied access.

### IP Fragmentation attacks
- IP / ICMP fragmentation attack is a common form of volumetric DoS. In such an attack, datagram fragmentation mechanisms are used to overwhelm the network.

- Bombard the destination with fragmented packets, causing it to use memory to reassemble all those fragments and overwhelm a targeted network.

- **Can manifest in different ways:**
  - **UDP Flooding** - attacker sends large volumes of fragments from numerous sources.
  - **UDP and ICMP** fragmentation attack - only parts of the packets is sent to the target; Since the packets are fake and can't be reassembled, the server's resources are quickly consumed.
  - T**CP fragmentation attack** - also know as a Teardrop attack, targets TCP/IP reassembly mechanisms; Fragmented packets are prevented from being reassembled. The result is that data packets overlap and the targeted server becomes completely overwhelmed.

### Application layer attacks (layer 7 attacks)
- Consume the resources necessary for the application to run.
- Target web servers, web application and specific web-based apps.
- Abuse higher-layer (7) protocols like HTTP/HTTPS and SNMP.
- Can be measured in packets per second.
*Note - application level attacks are against weak code; application attacks are just the general term.*


### TCP state-exhaustion attacks 
- Attempt to consume connection state tables like: **Load balancers, firewalls and application servers.**

### SYN attack
- Sends thousands of SYN packets
- Uses a **false source address** / spoofed IP address.
- Eventually engages all resources and exhausts the machine

### SYN flood
- Sends thousands of SYN packets; 
- **Does not spoof IP**, but doesn't respond to the SYN/ACK packets
- Eventually bogs down the computer, runs out of resources.

### ICMP flood
- Sends ICMP Echo packets with a spoofed address; eventually reaches limit of packets per second sent

### Smurf
- Large number of pings to the broadcast address of the subnet with **source IP spoofed** as the target; entire subnet responds exhausting the target

### Fraggle
- Same as smurf but with UDP packets

### Ping of Death
- Fragments ICMP messages; after reassembled, the ICMP packet is larger than the maximum size and crashes the system

### Teardrop
- Overlaps a large number of garbled IP fragments with oversized payloads; causes older systems to crash due to fragment reassembly

### Peer to peer
- Clients of peer-to-peer file-sharing hub are disconnected and directed to connect to the target system

### Phlashing
- A DoS attack that causes permanent damage to a system.
- Modifies the firmware and can also cause a system to brick.

### LAND attack
- Sends a SYN packet to the target with a spoofed IP the same as the target; if vulnerable, target loops endlessly and crashes

---

### Tools:
- **Low Orbit Ion Cannon** (LOIC) - DDoS tool that floods a target with TCP, UDP or HTTP requests


- **High Orbit Ion Cannon** (HOIC) - More powerful version of LOIC;  The application can open up to 256 simultaneous attack sessions at once, bringing down a target system by sending a continuous stream of junk traffic until legitimate requests are no longer able to be processed.

![loic](https://i.ytimg.com/vi/HavEPVxUn-A/maxresdefault.jpg)

- **Other Tools**
  - Trinity - Linux based DDoS tool
  - Tribe Flood Network - uses voluntary botnet systems to launch massive flood attacks
  - R-U-Dead-Yet (RUDY) - DoS with HTTP POST via long-form field submissions
