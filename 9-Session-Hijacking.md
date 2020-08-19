# <u>Session Hijacking</u>

> ⚡︎ **This chapter has [practical labs](https://github.com/Samsar4/Ethical-Hacking-Labs/tree/master/10-Session-Hijacking)**

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
