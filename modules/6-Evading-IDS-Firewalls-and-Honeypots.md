# Evading IDS, Firewalls and Honeypots

## <u>Devices To Evade</u>

- **Intrusion Detection System** (IDS) - hardware or software devices that examine streams of packets for malicious behavior
  - **Signature based** - compares packets against a list of known traffic patterns
  - **Anomaly based** - makes decisions on alerts based on learned behavior and "normal" patterns
  - **False negative** - case where traffic was malicious, but the IDS did not pick it up
  - **HIDS** (Host-based intrusion detection system) - IDS that is host-based
  - **NIDS** (Network-based intrusion detection system) - IDS that scans network traffic
- **Snort** - a widely deployed IDS that is open source
  - Includes a sniffer, traffic logger and a protocol analyzer
  - Runs in three different modes
    - **Sniffer** - watches packets in real time
    - **Packet logger** - saves packets to disk for review at a later time
    - **NIDS** - analyzes network traffic against various rule sets
  - Configuration is in /etc/snort on Linux and c:\snort\etc in Windows
  - **Rule syntax**
    - alert tcp !HOME_NET any -> $HOME_NET 31337 (msg : "BACKDOOR ATTEMPT-Backorifice")
      - This alerts about traffic coming not from an external network to the internal one on port 31337
  - **Example output**
    - 10/19-14:48:38.543734 0:48:542:2A:67 -> 0:10:B5:3C:34:C4 type:0x800 len:0x5EA
      **xxx -> xxx TCP TTL:64 TOS:0x0 ID:18112 IpLen:20 DgmLen:1500 DF**
    - Important info is bolded
- **Firewall**
  - An appliance within a network that protects internal resources from unauthorized access
  - Only uses rules that **implicitly denies** traffic unless it is allowed
  - Oftentimes uses **network address translation** (NAT) which can apply a one-to-one or one-to-many relationship between external and internal IP addresses
  - **Screened subnet** - hosts all public-facing servers and services
  - **Bastion hosts** - hosts on the screened subnet designed to protect internal resources
  - **Private zone** - hosts internal hosts that only respond to requests from within that zone
  - **Multi-homed** - firewall that has two or more interfaces
  - **Packet-filtering** - firewalls that only looked at headers
  - **Stateful inspection** - firewalls that track the entire status of a connection
  - **Circuit-level gateway** - firewall that works on Layer 5 (Session layer)
  - **Application-level gateway** - firewall that works like a proxy, allowing specific services in and out

## <u>Evasion Techniques</u>

- **Slow down** - faster scanning such as using nmap's -T5 switch will get you caught.  Pros use -T1 switch to get better results
- **Flood the network** - trigger alerts that aren't your intended attack so that you confuse firewalls/IDS and network admins
- **Fragmentation** -  splits up packets so that the IDS can't detect the real intent
- **Unicode encoding** - works with web requests - using Unicode characters instead of ascii can sometimes get past
- **Tools**
  - **Nessus** - also a vulnerability scanner
  - **ADMmutate** - creates scripts not recognizable by signature files
  - **NIDSbench** - older tool for fragmenting bits
  - **Inundator** - flooding tool

## <u>Firewall Evasion</u>

- ICMP Type 3 Code 13 will show that traffic is being blocked by firewall
- ICMP Type 3 Code 3 tells you the client itself has the port closed
- Firewall type can be discerned by banner grabbing
- **Firewalking** - going through every port on a firewall to determine what is open
- **Tools**
  - CovertTCP
  - ICMP Shell
  - 007 Shell
- The best way around a firewall will always be a compromised internal machine

### <u>Honeypots</u>

- A system setup as a decoy to entice attackers
- Should not include too many open services or look too easy to attack
- **High interaction** - simulates all services and applications and is designed to be completely compromised
- **Low interaction** - simulates a number of services and cannot be completely compromised
- **Examples**
  - Specter
  - Honeyd
  - KFSensor