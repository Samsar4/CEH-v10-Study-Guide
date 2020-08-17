# Denial of Service

> ⚡︎ **This chapter has [practical labs](https://github.com/Samsar4/Ethical-Hacking-Labs/tree/master/9-Denial-of-Service)**

- Seeks to take down a system or deny access to it by authorized users
- **Botnet** - network of zombie computers a hacker uses to start a distributed attack
  - Can be controlled over HTTP, HTTPS, IRC, or ICQ
- **Basic Categories**
  - **Fragmentation attacks** - attacks take advantage of the system's ability to reconstruct fragmented packets
  - **Volumetric attacks** - bandwidth attacks; consume all bandwidth for the system or service
  - **Application attacks** - consume the resources necessary for the application to run
    - Note - application level attakcs are against weak code; application attacks are just the general term
  - **TCP state-exhaustion attacks** - go after load balancers, firewalls and application servers
  - **SYN attack** - sends thousands of SYN packets to the machine with a false source address; eventually engages all resources and exhausts the machine
  - **SYN flood** - sends thousands of SYN packets; does not spoof IP but doesn't respond to the SYN/ACK packets; eventually bogs down the computer, runs out of resources
  - **ICMP flood** - sends ICMP Echo packets with a spoofed address; eventually reaches limit of packets per second sent
  - **Smurf** - large number of pings to the broadcast address of the subnet with source IP spoofed as the target; entire subnet responds exhausting the target
  - **Fraggle** - same as smurf but with UDP packets
  - **Ping of Death** - fragments ICMP messages; after reassembled, the ICMP packet is larger than the maximum size and crashes the system
  - **Teardrop** - overlaps a large number of garbled IP fragments with oversized payloads; causes older systems to crash due to fragment reassembly
  - **Peer to peer** - clients of peer-to-peer file-sharing hub are disconnected and directed to connect to the target system
  - **Phlashing** - a DoS attack that causes permanent damage to a system; also called bricking a system
  - **LAND attack** - sends a SYN packet to the target with a spoofed IP the same as the target; if vulnerable, target loops endlessly and crashes
- **Low Orbit Ion Cannon** (LOIC) - DDoS tool that floods a target with TCP, UDP or HTTP requests
- **Other Tools**
  - Trinity - Linux based DDoS tool
  - Tribe Flood Network - uses voluntary botnet systems to launch massive flood attacks
  - R-U-Dead-Yet (RUDY) - DoS with HTTP POST via long-form field submissions

### <u>Session Hijacking</u>

- Attacker waits for a session to begin and after the victim authenticates, steals the session for himself
- **Steps**
  1. Sniff the traffic between the client and server
  2. Monitor the traffic and predict the sequence numbering
  3. Desynchronize the session with the client
  4. Predict the session token and take over the session
  5. Inject packets to the target server
- Can be done via brute force, calculation or stealing
- Predicting can be done by knowing the window size and the packet sequence number
- Sequence numbers increment on **acknowledgement**
  - For example, an acknowledgement of 105 with a window of 200 means you could expect sequence numbering from 105 to 305
- **Tools**
  - **Ettercap** - man-in-the-middel tool and packet sniffer on steroids
  - **Hunt** - sniff, hijack and reset connections
  - **T-Sight** - easily hijack sessions and monitor network connections
  - **Zaproxy**
  - **Paros**
  - **Burp Suite**
  - **Juggernaut**
  - **Hamster**
  - **Ferret**
- **Countermeasures**
  - Using unpredictable session IDs
  - Limiting incoming connections
  - Minimizing remote access
  - Regenerating the session key after authentication
  - Use IPSec to encrypt
- **IPSec**
  - **Transport Mode** - payload and ESP trailer are encrypted; IP header is not
  - **Tunnel mode** - everything is encrypted; cannot be used with NAT
  - **Architecture Protocols**
    - **Authentication Header** - guarantees the integrity and authentication of IP packet sender
    - **Encapsulating Security Payload** (ESP) - provides origin authenticity and integrity as well as confidentiality
    - **Internet Key Exchange** (IKE) - produces the keys for the encryption process
    - **Oakley** - uses Diffie-Hellman to create master and session keys
    - ** Internet Security Association Key Management Protocol** (ISAKMP) - software that facilitates encrypted communication between two endpoints
