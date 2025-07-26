# Network Security Threats Report

## Introduction

As time passes, humanity's reliance on the internet is increasing day by day — and honestly, that’s not a bad thing. The internet helps make our work faster, more efficient, and more connected. But with the rapid growth in users, there’s also a growing need to keep everyone safe and secure while maintaining their individual privacy and identity.

Modern networking might be one of the greatest inventions of our time, but like everything, it has its own weaknesses. And unfortunately, those weaknesses lead to threats — threats that can make systems vulnerable to breaches and compromise a user's integrity, confidentiality, or accountability.

The  report focuses on some of the major network threats like **Denial-of-Service (DoS)**, **Man-in-the-Middle (MITM)** attacks, and **Spoofing**. These are discussed in detail, along with how they work, their impact, real-world examples, and the measures that can be taken to defend against them.

---

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

---

###  DoS working

A Denial-of-Service (DoS) attack works by overwhelming a targeted system, server, or network with excessive traffic or resource requests, rendering it unable to respond to legitimate user requests.

The attacker sends a flood of fake or malformed requests using a single machine or IP address, consuming critical system resources such as CPU, memory, or bandwidth. As a result, the system becomes slow, unresponsive, or crashes entirely.

DoS attacks may exploit specific protocol weaknesses (e.g., TCP handshake in SYN flood) or application-level flaws (e.g., HTTP GET/POST floods). The goal is not to breach data, but to disrupt service availability.

A Denial-of-Service (DoS) attack works by bombarding a website, server, or online service with so many fake or unnecessary requests that it can’t keep up. Since every system has limited resources like bandwidth, memory, or processing power, this overload forces it to slow down, crash, or stop responding altogether.

The attacker usually sends all this traffic from one system, not a whole network like in DDoS attacks. The goal isn’t to steal data or get inside — it’s just to make the service unusable for real people who are trying to access it.

Sometimes they use tricks like sending incomplete connection requests (like in a SYN flood) or flooding a server with repeated messages so it’s stuck dealing with junk while ignoring actual users.

DoS attacks break things not by hacking into them, but by overloading them until they stop working.

---

## Types of Denial-of-Service (DoS) Attacks

DoS attacks come in different forms based on what part of the system they try to break. Below are the most common types:



### 1. Volume-Based Attacks
These attacks try to overwhelm the target by flooding it with a huge amount of traffic. The idea is to clog the internet connection or network pipeline.

**Examples:**
- **UDP Flood:** Sends a large number of UDP packets to random ports.
- **ICMP Flood (Ping Flood):** Bombards the target with ICMP echo (ping) requests.

**Goal:** Exhaust the network bandwidth  
**Measurement:** Bits per second (bps)



### 2. Protocol Attacks
These target system resources by abusing weaknesses in network protocols like TCP, ICMP, or ARP. They overload networking equipment like firewalls and routers.

**Examples:**
- **SYN Flood:** Sends incomplete TCP handshakes to tie up connection slots.
- **Ping of Death:** Sends oversized or malformed ping packets to crash the system.
- **Smurf Attack:** Uses spoofed IP and ICMP to flood a system with ping replies.

**Goal:** Crash or exhaust resources in protocol handling  
**Measurement:** Packets per second (pps)



### 3. Application Layer Attacks
These target specific applications or websites and try to exhaust their processing power or memory by mimicking normal user behavior — but at scale.

**Examples:**
- **HTTP GET/POST Flood:** Sends tons of fake HTTP requests to a web server.
- **Slowloris:** Opens many connections and keeps them alive by sending partial requests very slowly.

**Goal:** Overload the app or backend server  
**Measurement:** Requests per second (rps)

---

### Real-World Example: GitHub DDoS Attack (2018)

On February 28, 2018, GitHub — the world’s largest code hosting platform, 
was hit by one of the **biggest Distributed Denial-of-Service (DDoS) attacks ever recorded** at the time.

This attack peaked at a massive **1.35 terabits per second (Tbps)**, overwhelming GitHub’s servers with fake traffic and making the site temporarily inaccessible for millions of users around the world.

#### -> How the Attack Worked:
- The attackers used a technique called a **"memcached amplification attack."**
- Memcached servers are meant to improve web performance by storing data in memory.
- But many of these servers were exposed to the internet **without authentication**.
- Attackers sent small requests to these servers while **spoofing GitHub’s IP address**.
- These servers responded with much **larger replies (amplified by up to 50,000x)** — all directed toward GitHub.

#### -> Impact:
- GitHub’s services became **temporarily unavailable**.
- It caused **serious traffic congestion**, affecting developers and businesses relying on GitHub.
- GitHub had to quickly route traffic through **a DDoS mitigation service** (Akamai/Prolexic) to absorb and block the attack.

#### -> Outcome:
- GitHub recovered within minutes thanks to rapid detection and automatic rerouting.
- The incident highlighted the growing threat of **amplification-based DDoS attacks**.
- It pushed companies to **secure open servers** and improve **response infrastructure**.

>  At the time, it was considered the **largest DDoS attack in history**, later surpassed by other high-volume attacks in 2020+.[3]

---

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

##  Introduction to Man-in-the-Middle (MITM) Attacks

Communication and data sharing are one of the main — if not the sole — purposes of digital networks. But the truth is, there’s **no guaranteed way to prove that your connection is 100% secure**. 
One of the biggest threats to network communication is the **compromise of privacy and secrecy** — where unauthorized users get access to what was meant to be a private exchange.

**Man-in-the-Middle (MITM)** attacks are a clear violation of that privacy. They don’t just compromise **confidentiality**, but also attack the **integrity and accountability** of your communication. In simple terms, MITM attacks allow an outsider to secretly intercept, read, and even **modify your data**, without you or the other person ever knowing.

Think of it like the old days when telephone operators manually connected your calls. Now imagine if the operator decided to secretly listen in, take notes, and maybe even repeat your secrets to someone else. But at least back then, you *knew* there might be someone in the middle, so you’d probably avoid saying anything too private or sensitive.

Now fast forward to today — and that’s what makes MITM attacks worse. In modern digital attacks, **you don’t even know the middleman exists**. The attacker quietly listens, records your messages, and can even **send fake messages pretending to be you** — and no one would notice.

In MITM attacks, you still think you’re connected directly to your friend, your bank, or your server — but there’s an invisible person in the middle, silently hijacking the conversation.



> *"A man-in-the-middle attack is a form of active eavesdropping in which the attacker makes independent connections with the victims and relays messages between them, making them believe they are talking directly to each other over a private connection, when in fact the entire conversation is being controlled by the attacker."[1]* 
Willaim Stallings one of the reputed author of cryptography and network security basically means the attacker **creates two separate connections** and stands between the victim and the real server — kind of like using two phones to pretend you're both people in a conversation. Neither side knows someone is controlling the entire exchange from the middle.

---

> *"In a man-in-the-middle attack, the attacker intercepts the communication between two parties and can monitor or alter the information exchanged, often without either party knowing that the link is compromised."[4]*  

Forouzan emphasizes that the attacker is **silently sitting in the middle**, reading or even changing messages, without anyone noticing. It’s like someone opening your sealed letter, editing it, and then resealing it before it reaches the other person.

---

These definitions make it clear that MITM attacks are dangerous not just because of what attackers **can see**, but because of what they can **change** — and the worst part is, you probably won’t even realize it’s happening.

## 🔍 How Does a Man-in-the-Middle (MITM) Attack Work?

At its core, a Man-in-the-Middle (MITM) attack is all about **intercepting communication between two parties** — usually a user and a server — without either party knowing that someone else is watching or interfering.

The attacker **positions themselves between you and the destination** (like a bank, email service, or website), and quietly listens, captures, or alters the data being exchanged. It’s like passing notes to a friend in class, but someone secretly reads the note in the middle, changes it, and then passes it along — and neither of you realizes what just happened.


###  Here’s how it typically happens:

1. **The Setup (Interception)**
   - The attacker tricks one or both parties into connecting to a **fake or compromised network** (like public Wi-Fi).
   - They may also use techniques like **ARP spoofing**, **DNS spoofing**, or **Wi-Fi eavesdropping** to hijack the data flow.

2. **The Relay (Sniffing or Manipulation)**
   - Once in the middle, the attacker can:
     - Just **monitor the traffic** (called passive MITM), or
     - **Alter messages**, **inject malicious code**, or **redirect users** (active MITM).
   - And the scary part? The user and server both still think they’re talking directly to each other.

3. **The Result (Data Theft or Control)**
   - Sensitive information like **login credentials**, **bank details**, **session cookies**, or **messages** can be stolen.
   - The attacker can also **impersonate** either party and perform actions on their behalf.

---

### A Common Scenario:
You're at a café using free public Wi-Fi. You connect to what looks like “Café_WiFi” — but it’s actually a fake hotspot set up by an attacker. As you log into your email or bank, everything you type is being **monitored or even modified** before it reaches its real destination.


MITM attacks are especially dangerous because:
- They’re **invisible** to users.
- They work best on **insecure or careless connections**.
- And they can affect even encrypted websites if the attacker tricks the system with fake certificates.



>  MITM attacks silently insert an attacker between you and who you're trying to talk to, without anyone realizing there's an extra person in the conversation.

---

##  Common Types of Man-in-the-Middle (MITM) Attacks

MITM attacks come in different forms, but all aim to silently intercept, monitor, or manipulate communication. Here are three major types that show up frequently in real-world scenarios:


### 1. Packet Sniffing

In this type, the attacker uses tools to **capture and inspect unencrypted data packets** that are traveling across a network — especially on open or public Wi-Fi. If the communication isn’t secured (like not using HTTPS), everything from messages to passwords can be read.

It’s like someone quietly listening to your entire conversation by tapping into the wires — without you even noticing.


### 2. Session Hijacking

Once you log into a website, your browser stores session cookies to keep you logged in. In session hijacking, the attacker **steals those cookies**  and with them, they can pretend to be you and access your accounts **without needing your password**.

 Imagine leaving your ID card on a bench. Someone picks it up and uses it to walk into your office, and no one questions it  that’s session hijacking.
 You did nothing but you will be blamed in case anything happens which was not supposed to happen, and you cannot proove it because it was your id card which was used.


### 3. Evil Twin Attack (Fake Wi-Fi Hotspot)

This one’s sneaky and surprisingly common. The attacker creates a fake Wi-Fi hotspot with a familiar name like “Café_WiFi” or “FreeAirportWiFi.” Once you connect, they can **monitor everything you do online** and even redirect you to fake websites.

It’s like sitting at a café, connecting to what looks like free internet, but it’s actually a trap and someone’s reading everything you send or receive.
Free things are not necesarilly good all time, this time it costed you your privacy whichis more important in this era where you are being monitored constanly.


These methods may differ in technique, but the core idea is the same: **the attacker silently inserts themselves into your communication and takes advantage of weak or unprotected networks.**

---

## Real-World Examples of MITM Attacks

While MITM attacks may sound like something out of a spy movie, they've happened in real life — and some caused serious damage. Here are a few well-known examples that show how dangerous and sneaky these attacks can be:



### 1. Superfish Scandal – Lenovo (2015)

Lenovo shipped laptops with a program called **Superfish Adware**, which installed a **self-signed root certificate** that allowed it to intercept HTTPS traffic. This basically **broke secure web connections** and made it possible for attackers to perform MITM attacks without the user realizing.

Attack Type: HTTPS spoofing / SSL interception  
Why it matters: Even **secure HTTPS connections were exposed**, and users were vulnerable to fake certificates that looked legitimate.



###  2. Firesheep Browser Extension (2010)

Firesheep was a Firefox plugin that let people **easily hijack sessions** over unsecured Wi-Fi. All someone had to do was sit in a coffee shop and open Firesheep — and boom, they could log in as you on sites like Facebook or Twitter.

 Attack Type: Session hijacking on public Wi-Fi  
 Why it matters: It showed how **easy it was to steal someone’s session** if the website didn’t use full HTTPS encryption.

---

##  Impact of MITM Attacks

MITM attacks are dangerous because they’re usually invisible — and by the time someone realizes what’s happened, it’s often too late. Here’s what they can lead to:



###  1. Loss of Confidential Information [6][7]
Attackers can steal **usernames, passwords, bank details**, or personal messages. This can lead to identity theft, financial fraud, and data leaks.



###  2. Identity Impersonation  
By hijacking sessions or altering communication, attackers can **pretend to be you**, sending messages or requests that you never made.



###  3. Damage to Trust and Reputation  [5][6][7]
If a company’s communication is compromised, it loses customer trust. Imagine users finding out their info was leaked — the brand may lose credibility overnight.

---

##  Mitigation and Countermeasures

While MITM attacks can’t always be prevented 100%, there are **multiple ways to make them harder to pull off** — both for users and organizations.



### 1. Use End-to-End Encryption  [7]
Always use HTTPS-secured websites and apps that support strong encryption (like TLS). This ensures even if data is intercepted, it **can’t be read**.


### 2.  Avoid Public Wi-Fi (or Use a VPN)  [5][6][7]
Public Wi-Fi is a playground for MITM attackers. If you have to use it, **use a VPN** to encrypt your traffic and keep your data safe.


### 3.  Validate Digital Certificates  
Websites use certificates to prove they are legit. If your browser warns you about a **suspicious or expired certificate**, don’t ignore it — it could be a fake site set up for a MITM attack.


### 4.  Enable HSTS (for Developers)  [6]
**HTTP Strict Transport Security (HSTS)** forces browsers to always connect using HTTPS. This prevents attackers from downgrading the connection to HTTP (SSL stripping).



### 5.  Use Intrusion Detection Systems (IDS)  [6][7]
In corporate environments, IDS tools can monitor network traffic patterns and **flag unusual behavior** that could indicate a MITM attempt.

---




## 3. Spoofing

Spoofing involves pretending to be a trusted source...

## Conclusion

Understanding these attacks is critical to maintaining secure networks.
