# Network Security Threats Report

## Introduction

As time passes, humanity's reliance on the internet is increasing day by day — and honestly, that’s not a bad thing. The internet helps make our work faster, more efficient, and more connected. But with the rapid growth in users, there’s also a growing need to keep everyone safe and secure while maintaining their individual privacy and identity.

Modern networking might be one of the greatest inventions of our time, but like everything, it has its own weaknesses. And unfortunately, those weaknesses lead to threats — threats that can make systems vulnerable to breaches and compromise a user's integrity, confidentiality, or accountability.

The  report focuses on some of the major network threats like **Denial-of-Service (DoS)**, **Man-in-the-Middle (MITM)** attacks, and **Spoofing**. These are discussed in detail, along with how they work, their impact, real-world examples, and the measures that can be taken to defend against them.


##  Denial-of-Service (DoS) Attacks

One of the most common and widely known types of network threats is the Denial-of-Service (DoS) attack. Interestingly, it doesn't exploit a vulnerability in the usual sense, but instead takes advantage of a normal function of networks — the ability to let users access services from anywhere, at any time. Attackers misuse this feature by generating a massive amount of traffic toward a specific website, application, or online service. While traffic itself isn’t harmful, too much of it — especially when it’s fake — becomes a serious issue.

Most of this traffic comes from compromised devices like **botnets**, which are remotely controlled by the attacker. As the service becomes overwhelmed by fake requests, real and authorized users are no longer able to access it. This can lead to **severe slowdowns**, **website crashes**, and even **financial losses due to service downtime**.

> *"A denial-of-service (DoS) attack attempts to prevent legitimate users from accessing information or services by flooding the system with traffic or exploiting system vulnerabilities to crash the service."* — *William Stallings* [1]

This definition by world-renowned author **William Stallings** explains DoS attacks as overloading services with an unhealthy amount of traffic and exploiting design limitations to deny access to legitimate users.

> *"Denial of Service is an attack that prevents or impairs the authorized use of networks, systems, or applications by exhausting resources such as bandwidth, memory, or processing power."*  
> — *NIST SP 800-61 Rev. 2* [2]

The **NIST** definition highlights how DoS attacks waste system resources — like memory, bandwidth, and CPU — before real users get a chance to use them. It’s like throwing away the service's capacity on fake users so there's nothing left for real ones.

To easily expalin DoS attack to anyone let consider a scenario of your favourite bakery;
Imagine you're in line at your favorite bakery, excited to buy their famous banana bread. But the queue isn't moving. The staff tells you they’re helping other customers — except those "customers" aren’t buying anything. They’re just asking useless questions and wasting time. Meanwhile, the fresh bread is sitting on the shelf getting cold. You’re still waiting, your friend has been waiting even longer, and no actual sales are being made.

> The bread isn't sold.
>Real customers don’t get what they came for.
> The store is busy, but nothing meaningful happens.

That’s what a **DoS attack** looks like in the digital world; fake traffic clogs the service, preventing real users from getting through.


###  DoS working

A Denial-of-Service (DoS) attack works by overwhelming a targeted system, server, or network with excessive traffic or resource requests, rendering it unable to respond to legitimate user requests.

The attacker sends a flood of fake or malformed requests using a single machine or IP address, consuming critical system resources such as CPU, memory, or bandwidth. As a result, the system becomes slow, unresponsive, or crashes entirely.

DoS attacks may exploit specific protocol weaknesses (e.g., TCP handshake in SYN flood) or application-level flaws (e.g., HTTP GET/POST floods). The goal is not to breach data, but to disrupt service availability.

A Denial-of-Service (DoS) attack works by bombarding a website, server, or online service with so many fake or unnecessary requests that it can’t keep up. Since every system has limited resources like bandwidth, memory, or processing power, this overload forces it to slow down, crash, or stop responding altogether.

The attacker usually sends all this traffic from one system, not a whole network like in DDoS attacks. The goal isn’t to steal data or get inside — it’s just to make the service unusable for real people who are trying to access it.

Sometimes they use tricks like sending incomplete connection requests (like in a SYN flood) or flooding a server with repeated messages so it’s stuck dealing with junk while ignoring actual users.

DoS attacks break things not by hacking into them, but by overloading them until they stop working.


## Types of Denial-of-Service (DoS) Attacks

DoS attacks come in different forms based on what part of the system they try to break. Below are the most common types:

---

### 1. Volume-Based Attacks
These attacks try to overwhelm the target by flooding it with a huge amount of traffic. The idea is to clog the internet connection or network pipeline.

**Examples:**
- **UDP Flood:** Sends a large number of UDP packets to random ports.
- **ICMP Flood (Ping Flood):** Bombards the target with ICMP echo (ping) requests.

**Goal:** Exhaust the network bandwidth  
**Measurement:** Bits per second (bps)

---

### 2. Protocol Attacks
These target system resources by abusing weaknesses in network protocols like TCP, ICMP, or ARP. They overload networking equipment like firewalls and routers.

**Examples:**
- **SYN Flood:** Sends incomplete TCP handshakes to tie up connection slots.
- **Ping of Death:** Sends oversized or malformed ping packets to crash the system.
- **Smurf Attack:** Uses spoofed IP and ICMP to flood a system with ping replies.

**Goal:** Crash or exhaust resources in protocol handling  
**Measurement:** Packets per second (pps)

---

### 3. Application Layer Attacks
These target specific applications or websites and try to exhaust their processing power or memory by mimicking normal user behavior — but at scale.

**Examples:**
- **HTTP GET/POST Flood:** Sends tons of fake HTTP requests to a web server.
- **Slowloris:** Opens many connections and keeps them alive by sending partial requests very slowly.

**Goal:** Overload the app or backend server  
**Measurement:** Requests per second (rps)
### Real-World Example: GitHub DDoS Attack (2018)

On February 28, 2018, GitHub — the world’s largest code hosting platform, 
was hit by one of the **biggest Distributed Denial-of-Service (DDoS) attacks ever recorded** at the time.

This attack peaked at a massive **1.35 terabits per second (Tbps)**, overwhelming GitHub’s servers with fake traffic and making the site temporarily inaccessible for millions of users around the world.

####  How the Attack Worked:
- The attackers used a technique called a **"memcached amplification attack."**
- Memcached servers are meant to improve web performance by storing data in memory.
- But many of these servers were exposed to the internet **without authentication**.
- Attackers sent small requests to these servers while **spoofing GitHub’s IP address**.
- These servers responded with much **larger replies (amplified by up to 50,000x)** — all directed toward GitHub.

####  Impact:
- GitHub’s services became **temporarily unavailable**.
- It caused **serious traffic congestion**, affecting developers and businesses relying on GitHub.
- GitHub had to quickly route traffic through **a DDoS mitigation service** (Akamai/Prolexic) to absorb and block the attack.

#### Outcome:
- GitHub recovered within minutes thanks to rapid detection and automatic rerouting.
- The incident highlighted the growing threat of **amplification-based DDoS attacks**.
- It pushed companies to **secure open servers** and improve **response infrastructure**.

>  At the time, it was considered the **largest DDoS attack in history**, later surpassed by other high-volume attacks in 2020+.[3]

##  Impact of DoS Attacks

DoS attacks may seem simple, but their consequences can be severe — especially when services are highly time-sensitive or business-critical.

### 1. Service Unavailability
Flooding the server makes websites and applications slow or completely inaccessible, frustrating users and interrupting business operations.

### 2. Financial and Reputational Loss
Downtime can lead to loss of revenue, emergency recovery costs, and damage to brand trust — especially if customers rely on 24/7 access.

### 3. Security Distraction
While the system is overloaded, attackers may use the chaos to hide other threats or breaches, making DoS attacks a diversion tactic in some cases.

##  Mitigation and Countermeasures for DoS Attacks

Stopping a DoS attack completely isn’t always easy. Sometimes, finding a full solution isn’t even possible — especially when the problem lies in the very service you're designed to provide. But there are smart ways to detect the attack early and reduce the damage it causes.


### 1. Rate Limiting

Rate limiting helps restrict how many requests a single user or IP can make in a short time. It’s one of the simplest ways to stop basic floods.

It’s like saying — you can ring my doorbell, but only five times. After that, the button disappears for a while, and you’ll have to wait before ringing again.

### 2. Firewalls and Intrusion Detection Systems (IDS)

Modern firewalls and IDS tools are like digital security guards. They can detect suspicious patterns, block known bad IPs, and filter out junk traffic before it even hits your app.

Think of it like a security guard who watches the door. If someone rings the bell too many times for no good reason, the guard stops them from ever ringing it again.


### 3. Use a DDoS Protection Service

Cloud-based services like **Cloudflare**, **AWS Shield**, or **Akamai** are built to handle huge traffic loads. They recognize fake requests and help absorb or block them, keeping your site running smoothly even during an attack.

I spent some of my resources to hire professionals to redesign the doorbell. Now it filters visitors — letting friends in, while trolls keep pressing a fake button that rings but doesn’t disturb me anymore.


### 4. Keep Systems Patched and Optimized

Outdated systems are easier to crash or overwhelm. Regular updates, optimization, and server hardening make sure attackers have fewer loopholes to exploit.

It’s like upgrading your door’s lock so it doesn’t jam easily or break when someone keeps shaking it.


>  The key is to stay prepared — DoS attacks are about overwhelming systems, so your best defense is making sure your system is strong, efficient, and alert enough to push back.

## 2. Man-in-the-Middle (MITM)

MITM is where the attacker secretly intercepts and alters communications.

## 3. Spoofing

Spoofing involves pretending to be a trusted source...

## Conclusion

Understanding these attacks is critical to maintaining secure networks.
