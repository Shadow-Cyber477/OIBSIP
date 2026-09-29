# Task 4: Research Report — Common Network Security Threats

## Introduction
Networks today run across the cloud, offices, and remote workers' homes. That gives attackers many more places to strike. Knowing how the most common attacks work, what damage they cause, and how to stop them helps security teams protect systems from downtime, unauthorized access, and financial loss.

---

## Threat Analysis

### 1. Denial of Service (DoS) and Distributed Denial of Service (DDoS) Attacks

#### How the Attack Works
These attacks make a website or server unavailable by flooding it with fake traffic, like hundreds of people crowding a shop door so real customers can't get in. A **DoS** attack comes from one machine. A **DDoS** attack comes from a **botnet**: thousands of hacked devices (cameras, routers, PCs) controlled by the attacker from one central server. Common methods include SYN floods, UDP amplification, and HTTP floods.

#### Real-World Example
In September 2016, the **Mirai botnet** attacked the DNS provider **Dyn** using over 100,000 hacked devices like IP cameras and home routers. The traffic reached about 1.2 Tbps and knocked out Twitter, Netflix, Reddit, and Spotify across the US and Europe.

#### Impact
- Services go offline.
- Lost sales and broken service agreements.
- Firewalls, routers, and bandwidth get overloaded.

#### Mitigation Strategies
1. **Cloud scrubbing services:** Providers like Cloudflare or Akamai spread traffic across many locations and filter out the bad requests before they reach your server.
2. **Rate limiting:** Set firewalls and load balancers to cap how many connections one IP address can make.
3. **Upstream blocking (BGP blackholing):** Ask your ISP to drop attack traffic before it reaches your network.

---

### 2. Man-in-the-Middle (MITM) Attacks

#### How the Attack Works
The attacker secretly sits between two people who think they are talking directly, like a postman who opens and reads your letters before delivering them. This is done through **ARP spoofing** (tricking devices on a local network into sending traffic through the attacker) or **rogue Wi-Fi hotspots**. The attacker can then read or change the data.

#### Real-World Example
In 2015, **Superfish** software came pre-installed on Lenovo laptops. It installed its own trusted certificate so it could read encrypted HTTPS traffic and inject ads. This also left users open to attackers who abused the same weakness.

#### Impact
- Stolen passwords, session tokens, and personal or financial data.
- Attackers can hijack sessions and pretend to be real users.
- Data can be changed or infected with malware in transit.

#### Mitigation Strategies
1. **Encryption (HTTPS/TLS) with HSTS:** Force secure connections so attackers can't downgrade them.
2. **Dynamic ARP Inspection (DAI):** Set up network switches to check ARP messages and reject fake ones.
3. **VPNs:** Have remote staff use an encrypted VPN (IPsec or WireGuard) on public Wi-Fi.

---

### 3. IP Spoofing

#### How the Attack Works
The attacker sends data with a **fake sender address**, like writing a false return address on an envelope. The internet's basic design doesn't check whether the sender address is real. Spoofing is often used to hide who is attacking, get past filters that trust certain IPs, and aim amplified traffic at a victim in DDoS "reflection" attacks.

#### Real-World Example
In February 2018, **GitHub** was hit by a 1.35 Tbps attack. Attackers sent small requests to open Memcached servers using GitHub's address as the sender. The servers replied with much larger responses, all sent to GitHub.

#### Impact
- Gets around simple IP-based access rules.
- Hides the real source of DDoS attacks.
- Can exhaust server resources (e.g., SYN flooding).

#### Mitigation Strategies
1. **Source address validation (BCP 38):** Have edge routers drop packets with sender addresses that shouldn't be there.
2. **Cryptographic authentication:** Use IPsec or SSH instead of trusting IP addresses.
3. **Unicast Reverse Path Forwarding (uRPF):** Have routers check that a packet's sender address matches a valid route back to it.

---

### 4. DNS Poisoning / Spoofing

#### How the Attack Works
DNS works like a phone book that turns website names into IP addresses. In DNS poisoning, the attacker plants **fake entries** in a DNS server's memory (its cache). When you type a real site like `bank.com`, you're sent to the attacker's fake copy, even though you typed the correct address.

#### Real-World Example
In April 2018, attackers hijacked traffic to **MyEtherWallet** by interfering with BGP routes and Amazon Route 53 DNS responses. Users were sent to a fake site hosted in Russia, and over $150,000 in Ethereum was stolen within two hours.

#### Impact
- Users are silently redirected to phishing or malware sites.
- Credentials and personal data are stolen.
- Trust in internet infrastructure is damaged.

#### Mitigation Strategies
1. **DNSSEC:** Digitally sign DNS records so fake ones can be detected.
2. **Hardened DNS resolvers:** Use random source ports and query IDs, which makes forging replies much harder.
3. **Encrypted DNS (DoH/DoT):** Stop others from reading or tampering with DNS queries.

---

## Threat Comparison Matrix

| Threat | How It's Done | Who Is at Risk | Difficulty to Execute | Ease of Mitigation |
| :--- | :--- | :--- | :--- | :--- |
| **DoS / DDoS** | Traffic floods, botnets | Websites, online services, ISPs | **Low to Medium** (DDoS-for-hire is easy to buy) | **Medium** (needs cloud scrubbing) |
| **MITM** | ARP spoofing, rogue Wi-Fi, SSL stripping | Public Wi-Fi users, remote workers | **Medium** | **Easy to Medium** (TLS, HSTS, VPN) |
| **IP Spoofing** | Fake sender addresses, reflection | Edge routers, IP-filtered systems | **Low to Medium** | **Medium** (needs wide BCP 38 adoption) |
| **DNS Poisoning** | Cache corruption, BGP hijacking | DNS resolvers, web users | **High** | **Medium to High** (needs DNSSEC) |

---

## Conclusion & Administrator Takeaways

Administrators should use **defense-in-depth**: several layers of protection, so one failure doesn't break everything. Three key takeaways:

1. **Use encryption and strong authentication everywhere.** Never trust an IP address alone. Use TLS 1.3 with HSTS, VPNs for remote access, and cryptographic authentication for admin interfaces.
2. **Filter traffic at the network edge.** Use BCP 38, Dynamic ARP Inspection, and uRPF to stop spoofed traffic entering or leaving your network.
3. **Get outside help for big attacks.** Internal firewalls can't absorb large DDoS floods or DNS hijacks alone. Use upstream scrubbing services, DNSSEC, and encrypted DNS (DoT/DoH).

---

## References

1. **National Institute of Standards and Technology (NIST).** (2013). *Guide to Intrusion Detection and Prevention Systems (IDPS)* (NIST Special Publication 800-94 Rev. 1). U.S. Department of Commerce. 
2. **Cybersecurity and Infrastructure Security Agency (CISA).** (2022). *Understanding and Mitigating Layer 3 and Layer 4 DDoS Attacks*. U.S. Department of Homeland Security. 
3. **Internet Engineering Task Force (IETF).** (2000). *Network Ingress Filtering: Defeating Denial of Service Attacks which employ IP Source Address Spoofing* (Best Current Practice BCP 38 / RFC 2827). 
4. **OWASP Foundation.** (2021). *OWASP Top Ten Web Application Security Risks: A04:2021 – Insecure Design & SQLi/Injection Vectors*. Open Web Application Security Project. 
