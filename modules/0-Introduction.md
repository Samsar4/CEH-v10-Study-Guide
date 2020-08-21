# <u>Introduction</u>

## <u> Fundamental Security Concepts </u>
The whole principle is to avoid **Theft, Tampering and Disruption** of the systems through **CIA Triad** (Confidentiality, Integrity and Availability).

<p align="center">
<img width="50%" src="https://i.ytimg.com/vi/AJTJN4wDBM8/hqdefault.jpg">
</p>

- **Confidentiality**
Keeping systems and data from being accessed, seen, read to anyone who is not authorized to do so.

- **Integrity**
Protect the data from modification or deletion by unauthorized parties, and ensuring that when authorized people make changes that shouldn't have been made the damage can be undone.

- **Availability**
Systems, access channels, and authentication mechanisms must all be working properly for the information they provide and protect to be available when needed.

**Note:** *In addition, other properties, such as authenticity, accountability, non-repudiation and reliability can also be involved. (ISO/IEC 27000:2009)*

- **Auditing & Accountability**
Basically keep tracking of everthing, like, who's been logging in when are they loggin in whose access this data.

- **Non-Repudiation**
Non-repudiation is the assurance that someone cannot deny the validity of something. Non-repudiation is a legal concept that is widely used in information security and refers to a service, which provides proof of the origin of data and the integrity of the data.

### **Security, Functionality and Usability balance**

There is an inter dependency between these three attributes. When **security goes up, usability and functionality come down**. Any organization should balance between these three qualities to arrive at a balanced information system.

<p align="center">
<img width="50%" src="https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/f14455ed4def635e1bc93b85657f43dbbf4a3127/triad2.png">
</p>

## <u>Types of Hackers</u>

<p align="center">
<img width="50%" src="https://www.simplilearn.com/ice9/free_resources_article_thumb/types-hacker.JPG">
</p>


- **White Hat** - Ethical hackers.
- **Black Hat** - Hackers that seek to perform malicious activities.
- **Gray Hat** - Hackers that perform good or bad activities but do not have the permission of the organization they are hacking against.

**Hacktivist** - Someone who hacks for a cause; political agenda.

**Suicide Hackers** - Are hackers that are not afraid of going jail or facing any sort of punishment; hack to get the job done.

**Cyberterrorist** - Motivated by religious or political beliefs to create fear or disruption.

**State-Sponsored Hacker** - Hacker that is hired by a government or entity related.

## <u>Hacking Vocabulary</u>

- **Hack value** - Perceived value or worth of a target as seen by the attacker.
- **Vulnerability** - A system flaw, weakness on the system (on design, implementation etc).
- **Exploit** - Exploits are a way of gaining access to a system through a security flaw and taking advantage of the flaw for their benefit.
- **Payload** - Component of an attack; is the part of the private user text which could also contain malware such as worms or viruses which performs the malicious action; deleting data, sending spam or encrypting data.
- **Zero-day attack** - Attack that occurs before a vendor knows or is able to patch a flaw.
- **Daisy Chaining / Pivotting** - It involves gaining access to a network and /or computer and then using the same information to gain access to multiple networks and computers that contains desirable information. 
- **Doxxing** - Publishing PII about an individual usually with a malicious intent.
- **Enterprise Information Security Architecture** (EISA) - process that determines how systems work within an organization.
- **Incident management** - Deals with specific incidents to mitigate the attack.



## <u> Attack Types and Vectors </u>

### Attack Vectors
- **APT - Advanced Persistent Threats**
    - An advanced persistent threat is a stealthy threat actor, typically a nation state or state-sponsored group, which gains unauthorized access to a computer network and remains undetected for an extended period.
- **Botnets**
    - Huge network of compromised hosts. (used for DDoS).
- **Cloud computing**
- **Insider attacks**
    - Disgruntled employee can damage assets from inside.
- **Mobile threats**
- **Viruses, worms, and malware**

### Attack Types
- **Operating System** (OS) - Attacks targeting OS flaws or security issues inside such as guest accounts or default passwords
- **Application Level** - Attacks on programming code and software logic
- **Shrink-Wrap Code** - Act of exploiting holes in unpatched or poorly-configured software.
- **Misconfiguration** - Attack takes advantage of systems that are misconfigured due to improper configuration or default configuration

## <u>Vulnerabilities</u>

- **CVSS - Common Vulnerability Scoring System** 
  - Places numerical score based on severity
- **CVE – Common Vulnerabilities and Exposures** 
  - Is a list of publicly disclosed vulnerabilities and exposures that is maintained by MITRE.
- **NVD - National Vulnerability Database** 
  -  is a database, maintained by NIST, that is fully synchronized with the MITRE CVE list; US Gov. vulnerabilities repository.

### Vulnerability Categories

- **Misconfiguration** - improperly configuring a service or application
- **Default installation** - failure to change settings in an application that come by default
- **Buffer overflow** - code execution flaw
- **Missing patches** -  systems that have not been patched
- **Design flaws** - flaws inherent to system design such as encryption and data validation
- **Operating System Flaws** - flaws specific to each OS
- **Default passwords** - leaving default passwords that come with system/application


## <u>Five Phases of Hacking</u>

1. **Reconnaissance**  - Gathering evidence about targets; 
There are two types of Recon:
    - **Passive Reconnaissance**: Gain information about targeted computers and networks without actively engaging with the systems
        - e.g: Google Search, Public records, New releases, Social Media, Wardrive scanning networks around.
    - **Active Reconnaissance**: Envolves direct interaction with the target.
        - e.g: Make a phone call to the target, Job interview; tools like Nmap, Nessus, OpenVAS, Nikto and Metasploit can be considered as Active Recon.

2. **Scanning & Enumeration** - Obtaining more in-depth information about targets.
    - e.g: Network Scanning, Port Scanning, Which versions of services are running.
3. **Gaining Access** - Attacks are leveled in order to gain access to a system.
4. **Maintaining Access** - Items put in place to ensure future access.
    - e.g: Rookit, Trojan, Backdoor can be used.
5. **Covering Tracks** - Steps taken to conceal success and intrusion; Not be noticed; Clear the logs;

## <u>Penetration Test - Basics</u>

> **This subject will be covered with details in [Chapter 14 - Pentesting](https://github.com/Samsar4/CEH-v10-Study-Guide/blob/master/modules/14-Pentesting.md).**

- Clearly defined, full scale test of security controls
- Phases
  - **Preparation** - Contracts and team determined
  - **Assessment** - All hacking phases (reconnaissance, scanning, attacks, etc.)
  - **Post-Assessment** - Reports & conclusions
- Types
  - **Black Box** - Done without any knowledge of the system or network.
  - **White Box** - When the attacker have complete knowledge of the system provided by the owner/target.
  - **Gray Box** - When the attacker has some knowledge of the system and/or network

## <u>Security Controls</u>

- **Directive** - Also known as **procedural controls** because they deal with company procedures such as security policies, operations plans, and guidelines. 

- **Deterrent control**: Deters the actor from attempting the threat.
    - e.g: Warning Sign, SSH Login Banner.

- **Preventive control**: Deters the actor from performing the threat.
    - e.g: Fence, Server Locks, Password Complexity, Firewall.

- **Detective control**: Recognizes an actor's threat.   
    - e.g: Background check, CCTV, IDS/IPS.

- **Compensating control**: Provides alternative fixes to any of the above functions

- **Corrective control**: Mitigates the impact of a manifested threat. (Backups can mitigate a ransomware; IPS can block an attacker)

*Most of security controls are preventive phase controls*.

### Types of  Security Controls

| Description    | Examples                                      |
| -------------- | --------------------------------------------- |
| Physical       | Guards, lights, cameras                       |
| Technical      | Encryption, smart cards, access control lists |
| Administrative | Training awareness, policies                  |

| Description  | Examples                    |
| ------------ | --------------------------- |
| Preventative | authentication, alarm bells |
| Detective    | audits, backups             |
| Corrective   | restore operations          |

## <u>Law Categories</u>

- **Criminal** - Laws that protect public safety and usually have jail time attached.
- **Civil** - Private rights and remedies.
- **Common** - Laws that are based on societal customs.


## <u>Laws and Standards</u>

- **OSSTM Compliance** - "Open Source Security Testing Methodology Manual" maintained by ISECOM , defines three types of compliance
  - **Legislative** - Deals with government regulations (Such as SOX and HIPAA)
  - **Contractual** - Deals with industry / group requirement (Such as PCI DSS)
  - **Standards based** - Deals with practices that must be followed by members of a given group/organization (Such as ITIL ,ISO and OSSTMM itself)
  
- **OSSTM Controls**
  - **OSSTM Class A - Interactive Controls**
    - *Authentication* -  Provides for identification and authorization based on credentials 
    - *Indemnification* - Provided contractual protection against loss or damages
    - *Subjugation* - Ensures that interactions occur according to processes defined by the asset owner
    - *Continuity* -  Maintains interactivity with assets if corruption of failure occurs
    - *Resilience* - Protects assets from corruption and failure
   
  
  
  - **OSSTM Class B  - Process Controls**
      - *Non-repudiation* - Prevents participants from denying its actions
      - *Confidentiality* - Ensures that only participants know of an asset
      - *Privacy* - Ensures that only participants have access to the asset
      - *Integrity* - Ensures that only participants know when assets and processes change
      - *Alarm*  - Notifies participants when interactions occur
      
- **ISO 27001** - Security standard based on the British BS7799 standard, focuses on security governance

- **NIST-800-53** -  Catalogs security and privacy controls for federal information systems, created to help implementation of FISMA

- **ISO 27002 AND 17799** - Based on BS799 but focuses on security objectives and provides security controls based on industry best practice

- **FISMA** - "Federal Information Security Modernization Ac Of 2002" A law updated in 2004 to codify the authority of the Department of Homeland Security with regard to implementation of information security policies 
  
- **FITARA** - "Federal Information Technology Acquisition Reform Act" A 2013 bill that was intended to change the framework that determines how the US GOV purchases technology 

- **HIPAA** - "Health Insurance Portability and Accountability Act" a law that set's privacy standards to protect patient medical records and health information shared between doctors, hospitals and insurance providers

- **PCI-DSS**  - "Payment Card Industry Data Security Standard" Standard for organizations handling Credit Cards, ATM cards and other POS cards

- **COBIT** - "Control Object for Information and Related Technology" IT Governance framework and toolset, created by ISACA and ITGI

- **SOX** - "Sarbanes-Oxley Act" Law that requires publicly traded companies to submit to independent audits and to properly disclose financial information

- **GLBA** - "U.S Gramm-Leach-Bliley Act" Law that protects the confidentiality and integrity of personal information that is collected by financial institutions.

- **CSIRT** - "Computer Security Incident Response Team" CSIRT provided a single point of contact when reporting computer security incidents

- **ITIL** - "Information Technology Infrastructure Library" - An operational framework developed in the '80s that standardizes IT management procedures 

## <u>Essential Knowledge</u>

- **The OSI Model** we just looked at is just a reference/logical model. It was designed to describe the functions of the communication system by dividing the communication procedure into smaller and simpler components. 

- **The TCP/IP model** is a concise version of the OSI model. It contains four layers, unlike seven layers in the OSI model. 

| Layer | Device Type | OSI Layer | TCP/IP model | TCP/IP New (actual) | Protocols | PDU
--|--|--|--|--|--|--
7 | Gateway | **Application** | Application| Application | HTTP, FTP, POP, SMTP, DNS, RIP | Data
6 | -       | **Presentation**| Application| Application | HTTP, FTP, POP, SMTP, DNS, RIP, MIME | Data
5 | -       | **Session**     | Application| Application | HTTP, FTP, POP, SMTP, DNS, RIP, SCP | Data
4 | -       | **Transport**   | Transport  | Transport | TCP/UDP | Segments
3 | Router  | **Network**     | Internet   | Network | IP, ARP, ICMP, IGMP | Packets
2 | Switch/bridge | **Data Link** | Link   | Data Link | Ethernet, Token Ring | Frames
1 | Hubs/Repeater | **Physical**  | Link   | Physical | Ethernet, Token Ring | Bits

### <u>TCP Handshake</u>

<h4 align="center">The Three-way handshake</h4>
<p align="center">
<img width="77%" src="https://wiki.mikrotik.com/images/f/fc/Image2001.gif">
</p>

#### ✅ TCP Connection establishment process 
1. **Host A** sends out a **SYN** (synchronize) packet with proposed initial sequence number to Host B.
2. **Host B** receives **SYN** message, it returns a packet with both SYN and ACK flags (**SYN-ACK**) set in the [TCP header](https://www.gatevidyalay.com/transmission-control-protocol-tcp-header/).
3. **Host A** receives the **SYN-ACK**, it sends back **ACK** (Acknowledgment) packet.
4. **Host B** receives **ACK** and at this stage the connection is **ESTABLISHED.**

#### ❌ TCP Connection termination
1. **Host A** sends a **FIN** (finish) flag, indicating that is has finished sending the data.
2. **Host B** who receives the **FIN**, doest not terminate the connection but enters into a "passive close" (CLOSE_WAIT) state and sends the **ACK** for the **FIN** back to the Host A.
3. **Host A** enters into a (TIME_WAIT) state, and sends an **ACK** back to the Host B.
4. **Host B** gets the **ACK** from the Host A and **closes the connection.**

⚠️ *Sequence numbers increase on new communication.  Example is computers A and B.  A would increment B's sequence number.  A would never increment it's own sequence.*

### <u>TCP Flags</u>

| Flag | Name           | Function                                                     |
| ---- | -------------- | ------------------------------------------------------------ |
| SYN  | Synchronize    | Set during initial communication.  Negotiating of parameters and sequence numbers |
| ACK  | Acknowledgment | Set as an acknowledgement to the SYN flag.  Always set after initial SYN |
| RST  | Reset          | Forces the termination of a connection (in both directions)  |
| FIN  | Finish         | Ordered close to communications                              |
| PSH  | Push           | Forces the delivery of data without concern for buffering    |
| URG  | Urgent         | Data inside is being sent out of band.  Example is cancelling a message |

### <u>Port Numbers</u>

- **Internet Assigned Numbers Authority** (IANA) - maintains Service Name and Transport Protocol Port Number Registry which lists all port number reservations

- Ranges

  - **Well-known ports** - 0 - 1023

  - **Registered ports** - 1024 - 49,151

  - **Dynamic ports** - 49,152 - 65,535

    | Port Number | Protocol | Transport Protocol |
    | ----------- | -------- | ------------------ |
    | 20/21       | FTP      | TCP                |
    | 22          | SSH      | TCP                |
    | 23          | Telnet   | TCP                |
    | 25          | SMTP     | TCP                |
    | 53          | DNS      | TCP/UDP            |
    | 67          | DHCP     | UDP                |
    | 69          | TFTP     | UDP                |
    | 80          | HTTP     | TCP                |
    | 110         | POP3     | TCP                |
    | 135         | RPC      | TCP                |
    | 137-139     | NetBIOS  | TCP/UDP            |
    | 143         | IMAP     | TCP                |
    | 161/162     | SNMP     | UDP                |
    | 389         | LDAP     | TCP/UDP            |
    | 443         | HTTPS    | TCP                |
    | 445         | SMB      | TCP                |
    | 514         | SYSLOG   | UDP                |

  - A service is said to be **listening** for a port when it has that specific port open

  - Once a service has made a connection, the port is in an **established** state

  - **`Netstat`** command:

    - Shows open ports on computer
    - **netstat -an** displays connections in numerical form
    - **netstat -b** displays executables tied to the open port (admin only)

### <u>Subnetting</u>

- **IPv4 Main Address Types**
  - **Unicast** - acted on by a single recipient
  - **Multicast** - acted on by members of a specific group
  - **Broadcast** - acted on by everyone on the network
    - **Limited** - delivered to every system in the domain (255.255.255.255)
    - **Directed** - delivered to all devices on a subnet and use that broadcast address
- **Subnet mask** - determines how many address available on a specific subnet
  - Represented by three methods
    - **Decimal** - 255.240.0.0
    - **Binary** - 11111111.11110000.00000000.00000000
    - **CIDR** - x.x.x.x/12   (where x.x.x.x is an ip address on that range)
  - If all the bits in the host field are 1s, the address is the broadcast
  - If they are all 0s, it's the network address
  - Any other combination indicates an address in the range
  - ![img](https://s3.amazonaws.com/prealliance-thumbnails.oneclass.com/thumbnails/001/751/775/original/stringio.txt?1513221790)