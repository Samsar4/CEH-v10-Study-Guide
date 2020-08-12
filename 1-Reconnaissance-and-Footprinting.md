# <u> Reconnaissance and Footprinting</u>

> ⚡︎ **This chapter have [practical labs](https://github.com/Samsar4/Ethical-Hacking-Labs/tree/master/1-Footprinting-and-Reconnaissance)**

## <u>Footprinting</u>
Footprinting is a part of reconnaissance process which is used for gathering possible information about a target computer system or network. 

**Footprinting could be both passive and active**. Reviewing a company’s website is an example of passive footprinting, whereas attempting to gain access to sensitive information through social engineering is an example of active information gathering.

During this phase, a hacker can collect the following information (only high-level information):

- **Domain name**
- **IP Addresses**
- **Namespaces**
- **Employee information**
- **Phone numbers**
- **E-mails**
- **Job Information**

Can be:
  - **Anonymous** - information gathering without revealing anything about yourself
  - **Pseudonymous** - making someone else take the blame for your actions

### <u>Types of Footprinting</u>

- **Active** - requires attacker to touch the device or network
  - Social engineering and other communication that requires interaction with target
- **Passive** - measures to collect information from publicly available sources
  - Websites, DNS records, business information databases

**Competitive Intelligence** - information gathered by businesses about competitors

**Alexa.com** - resource for statistics about websites

## <u>Methods and Tools</u>

### Search Engines

- **[NetCraft](https://www.netcraft.com/)** - Blueprint a comprehensive list of information about the technologies and information about target website.
- **Job Search Sites** - Information about technologies can be gleaned from job postings.
- **Google search** 
  - `filetype:`  - looks for file types
  - `index of` - directory listings
  - `info:` - contains Google's information about the page
  - `intitle:` - string in title
  - `inurl:` - string in url
  - `link:` - finds linked pages
  - `related:` - finds similar pages
  - `site:` - finds pages specific to that site
- **Metagoofil** - Command line interface that uses **Google hacks** to find information in meta tags (domain, filetype, etc; Is a google dorks for terminal).

### Website Footprinting

- **Web mirroring** - allows for discrete testing offline
  - HTTrack
  - Black Widow
  - Wget
  - WebRipper
  - Teleport Pro
  - Backstreet Browser
- **Archive.org / [Wayback machine](https://archive.org/web/)** 
- Provides cached websites from various dates which possibly have sensitive information that has been now removed.
  - **Wayback Machine -> Google.com**: ![wayback](https://searchengineland.com/figz/wp-content/seloads/2011/01/archive41-500x256.png)

### Email Footprinting

- **Email  header** - may show servers and where the location of those servers are
  - Email headers can provide: **Names, Addresses (IP, email), Mail servers, Time stamps, Authentication and so on.**
  -![emailheader](https://www.wikihow.com/images/thumb/7/72/Read-Email-Headers-Step-7.jpg/v4-460px-Read-Email-Headers-Step-7.jpg.webp)
  - **EmailTrackerPro** is a Windows software that trace an email back to its true point of origin: ![emailtrackerpro](http://www.emailtrackerpro.com/support/v9/tutorials/images/traceheader/3.png)
- **Email tracking** - services can track various bits of information including the IP address of where it was opened, where it went, etc.

### DNS Footprinting

- Ports

  - Name lookup - UDP 53
  - Zone transfer - TCP 53

- Zone transfer replicates all records

- **Name resolvers** answer requests

- **Authoritative Servers** hold all records for a namespace

- **DNS Record Types**

  

  - | Name  | Description        | Purpose                                        |
    | ----- | ------------------ | ---------------------------------------------- |
    | SRV   | Service            | Points to a specific service                   |
    | SOA   | Start of Authority | Indicates the authoritative NS for a namespace |
    | PTR   | Pointer            | Maps an IP to a hostname                       |
    | NS    | Nameserver         | Lists the nameservers for a namespace          |
    | MX    | Mail Exchange      | Lists email servers                            |
    | CNAME | Canonical Name     | Maps a name to an A reccord                    |
    | A     | Address            | Maps an hostname to an IP address              |

- **DNS Poisoning** - changes cache on a machine to redirect requests to a malicious server

- **DNSSEC** - helps prevent DNS poisoning by encrypting records

- **SOA Record Fields**

  - **Source Host** - hostname of the primary DNS
  - **Contact Email** - email for the person responsible for the zone file
  - **Serial Number** - revision number that increments with each change
  - **Refresh Time** - time in which an update should occur
  - **Retry Time** - time that a NS should wait on a failure
  - **Expire Time** - time in which a zone transfer is allowed to complete
  - **TTL** - minimum TTL for records within the zone

- **IP Address Management**

  - **ARIN** - North America
  - **APNIC** - Asia Pacific
  - **RIPE** - Europe, Middle East
  - **LACNIC** - Latin America
  - **AfriNIC** - Africa

- **Whois** - obtains registration information for the domain from command line or web interface.
  - on Kali, whois is pre-installed on CLI; e.g: `whois google.com`)
  - on Windows, you can use **SmartWhois** GUI software to perform a whois, or any website like domaintools.com
- **Nslookup** - Performs DNS queries; (nslookup is pre-installed on Kali Linux)

  - `nslookup www.hackthissite.org`
  - ```
    Server:         192.168.63.2
    Address:        192.168.63.2#53

    Non-authoritative answer:
    Name:   www.hackthissite.org
    Address: 137.74.187.103
    Name:   www.hackthissite.org
    Address: 137.74.187.102
    Name:   www.hackthissite.org
    Address: 137.74.187.100
    Name:   www.hackthissite.org
    Address: 137.74.187.101
    Name:   www.hackthissite.org
    Address: 137.74.187.104
    ```
    - First two lines shows my current DNS server; The IP addresses returned are '**A record**', meaning is the IPvA address of the domain; Bottom line NsLookup queries the specified DNS server and retrieves the requested records that are associated with the domain. 

    - **The following types of DNS records are especially useful to use on Nslookup:**


    - | Type  | Description        |
      | ----- | ------------------ |
      | A     |  the IPv4 address of the domain          |
      | AAAA  |  the domain’s IPv6 address          |
      | CNAME |  the canonical name — allowing one domain name to map on to another. This allows more than one website to refer to a single web server.          | 
      | MX    |  the server that handles email for the domain.        |
      | NS    |  one or more authoritative name server records for the domain.          | 
      | TXT   |  a record containing information for use outside the DNS server. The content takes the form name=value. This information is used for many things including authentication schemes such as SPF and DKIM.          |

  - **Nslookup - Interactive mode zone transfer** (Interactive mode allows the user to query name servers for information about various hosts and domains or to print a list of hosts in a domain).
    - `nslookup`
    - `server <IP Address>`
    - `set type = <DNS type>`
    - `<target domain>`
  - ```
    nslookup 
    > set type=AAAA                                                                                                                                            
    > www.hackthissite.org
    Server:         192.168.63.2                                                                                                                               
    Address:        192.168.63.2#53                                                                                                                            
                                                                                                                                                              
    Non-authoritative answer:                                                                                                                                  
    Name:   www.hackthissite.org                                                                                                                               
    Address: 2001:41d0:8:ccd8:137:74:187:103                                                                                                                   
    Name:   www.hackthissite.org                                                                                                                               
    Address: 2001:41d0:8:ccd8:137:74:187:102                                                                                                                   
    Name:   www.hackthissite.org                                                                                                                               
    Address: 2001:41d0:8:ccd8:137:74:187:101                                                                                                                   
    Name:   www.hackthissite.org                                                                                                                               
    Address: 2001:41d0:8:ccd8:137:74:187:100
    Name:   www.hackthissite.org
    Address: 2001:41d0:8:ccd8:137:74:187:104
    ```
- **Dig** - unix-based command like nslookup

  - `dig <target>`
  - ```
    dig www.hackthissite.org

    ; <<>> DiG 9.16.2-Debian <<>> www.hackthissite.org
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51391
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 1

    ;; OPT PSEUDOSECTION:
    ; EDNS: version: 0, flags:; MBZ: 0x0005, udp: 4096
    ;; QUESTION SECTION:
    ;www.hackthissite.org.          IN      A

    ;; ANSWER SECTION:
    www.hackthissite.org.   5       IN      A       137.74.187.104
    www.hackthissite.org.   5       IN      A       137.74.187.101
    www.hackthissite.org.   5       IN      A       137.74.187.100
    www.hackthissite.org.   5       IN      A       137.74.187.102
    www.hackthissite.org.   5       IN      A       137.74.187.103

    ;; Query time: 11 msec
    ;; SERVER: 192.168.63.2#53(192.168.63.2)
    ;; WHEN: Tue Aug 11 15:05:01 EDT 2020
    ;; MSG SIZE  rcvd: 129

    ```
### Network Footprinting

- IP address range can be obtained from regional registrar (ARIN here)
- Use traceroute to find intermediary servers
  - traceroute uses ICMP echo in Windows
- Windows command - tracert
- Linux Command - traceroute

### Other Relevant Tools

- **OSRFramework** - uses open source intelligence to get information about target. *(Username checking, DNS lookups, information leaks research, deep web search, regular expressions extraction, and many others)*.
- **Web Spiders** - obtain information from the website such as pages, etc.
- **[Recon-ng](https://github.com/lanmaster53/recon-ng)** - Recon-ng is a web-based open-source reconnaissance tool used to extract information from a target organization and its personnel.
- **[Metasploit Framework](https://github.com/rapid7/metasploit-framework)** - The Metasploit Framework is a tool that provides information about security vulnerabilities and aids in penetration testing and IDS signature development; This is a huge framework that provide Recon tools as well.
- **[theHarvester](https://github.com/laramies/theHarvester)** - theHarvester is a OSINT tool; Can gathers emails, subdomains, hosts, employee names, open ports and banners from different public sources like search engines, PGP key servers and SHODAN computer database.
- **Social Engineering Tools**
  - Maltego
  - Social Engineering Framework (SEF)
- **[Shodan](https://www.shodan.io/)** - Shodan is a search engine that lets the user find specific types of computers (webcams, routers, servers, etc.) ... connected to the internet using a variety of filters. Some have also described it as a search engine of service banners, which are metadata that the server sends back to the client.

> ⚡︎ **The [practical labs](https://github.com/Samsar4/Ethical-Hacking-Labs/tree/master/1-Footprinting-and-Reconnaissance) have all mentioned tools above; Is recommended to try these tools in your virtual environment.**
