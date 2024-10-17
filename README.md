
---

### Acknowledgment and Licensing:
   This repository is based on content from [Karan Pratap Singh’s system-design repository](https://github.com/karanpratapsingh/system-design), which is licensed under the [MIT License](https://github.com/karanpratapsingh/system-design/blob/master/LICENSE).  
   
   Modifications have been made to better suit my personal learning objectives. This repository follows the same licensing terms.  


---

# System Design

# Table of contents

- **Getting Started**

  - [What is system design?](#what-is-system-design)

- **Chapter I**

  - [IP](#ip)
  - [OSI Model](#osi-model)
  - [TCP and UDP](#tcp-and-udp)
  - [Domain Name System (DNS)](#domain-name-system-dns)
  - [Load Balancing](#load-balancing)
  - [Clustering](#clustering)
  - [Caching](#caching)
  - [Content Delivery Network (CDN)](#content-delivery-network-cdn)
  - [Proxy](#proxy)
  - [Availability](#availability)
  - [Scalability](#scalability)
  - [Storage](#storage)

- **Chapter II**

  - [Databases and DBMS](#databases-and-dbms)
  - [SQL databases](#sql-databases)
  - [NoSQL databases](#nosql-databases)
  - [SQL vs NoSQL databases](#sql-vs-nosql-databases)
  - [Database Replication](#database-replication)
  - [Indexes](#indexes)
  - [Normalization and Denormalization](#normalization-and-denormalization)
  - [ACID and BASE consistency models](#acid-and-base-consistency-models)
  - [CAP theorem](#cap-theorem)
  - [PACELC Theorem](#pacelc-theorem)
  - [Transactions](#transactions)
  - [Distributed Transactions](#distributed-transactions)
  - [Sharding](#sharding)
  - [Consistent Hashing](#consistent-hashing)
  - [Database Federation](#database-federation)

- **Chapter III**

  - [N-tier architecture](#n-tier-architecture)
  - [Message Brokers](#message-brokers)
  - [Message Queues](#message-queues)
  - [Publish-Subscribe](#publish-subscribe)
  - [Enterprise Service Bus (ESB)](#enterprise-service-bus-esb)
  - [Monoliths and Microservices](#monoliths-and-microservices)
  - [Event-Driven Architecture (EDA)](#event-driven-architecture-eda)
  - [Event Sourcing](#event-sourcing)
  - [Command and Query Responsibility Segregation (CQRS)](#command-and-query-responsibility-segregation-cqrs)
  - [API Gateway](#api-gateway)
  - [REST, GraphQL, gRPC](#rest-graphql-grpc)
  - [Long polling, WebSockets, Server-Sent Events (SSE)](#long-polling-websockets-server-sent-events-sse)

- **Chapter IV**

  - [Geohashing and Quadtrees](#geohashing-and-quadtrees)
  - [Circuit breaker](#circuit-breaker)
  - [Rate Limiting](#rate-limiting)
  - [Service Discovery](#service-discovery)
  - [SLA, SLO, SLI](#sla-slo-sli)
  - [Disaster recovery](#disaster-recovery)
  - [Virtual Machines (VMs) and Containers](#virtual-machines-vms-and-containers)
  - [OAuth 2.0 and OpenID Connect (OIDC)](#oauth-20-and-openid-connect-oidc)
  - [Single Sign-On (SSO)](#single-sign-on-sso)
  - [SSL, TLS, mTLS](#ssl-tls-mtls)

- **Chapter V**

  - [System Design Interviews](#system-design-interviews)
  - [URL Shortener](#url-shortener)
  - [WhatsApp](#whatsapp)
  - [Twitter](#twitter)
  - [Netflix](#netflix)
  - [Uber](#uber)

- **Appendix**

  - [Next Steps](#next-steps)
  - [References](#references)

# What is system design?

System design is the process of defining the architecture, components, and interfaces of a system to satisfy specified requirements.

In simple words, it involves planning how to build a system that works well and meets the needs of users. This includes deciding how different parts of the system will interact, what technologies will be used, and how data will flow through the system.

## Why is System Design so important?

 **F**or **R**eliable **A**nd **M**aintainable **E**fficient **S**ystems

- **F**unctionality
- **R**esource Management & Reliability
- **A**ccessibility
- **M**aintainability
- **E**fficiency
- **S**calability

1. **Functionality:** It helps in creating a system that meets the specific requirements and functions as intended.
2. **Resource Management:** Efficient design makes better use of resources like time, money, and technology, avoiding waste and maximizing value.
3. **Maintainability:** It makes the system easier to maintain, update, and troubleshoot, reducing long-term costs and effort.
4. **Enhances Performance:** Proper design optimizes the system for better performance, making it faster and more efficient.
5. **Scalability:** A well-designed system can handle growth and increased demand without significant rework.
6. **User Satisfaction:** It results in a system that is user-friendly and meets the needs of its users, leading to higher satisfaction and usability.


# IP [Internet Protocol]
An IP address is a unique address that identifies a device on the internet or a local network

IP addresses enable devices to locate and communicate with each other, ensuring data is sent to the correct destination, which is essential for internet functionality.

## Versions

Let's learn about the different versions of IP Addresses:


### IPv4

IPv4 is the original Internet Protocol, using a 32-bit numeric dot-decimal notation that allows for around 4 billion IP addresses. It was enough at first, but as internet use grew, a new solution was needed.

_Example: `102.22.192.181`_


### IPv6

IPv6 is the new protocol introduced in 1998 and deployed from the mid-2000s. It uses a 128-bit alphanumeric hexadecimal notation, providing about 340 undecillion(340 trillion trillion trillion) IP addresses, which will meet the demand for a long time.

_Example: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`_

## Types

Let's discuss types of IP addresses:

### Public

A public IP address is assigned to your entire network by your ISP. All connected devices on your network share the same  IP address.

_Example: IP address provided to your router by the ISP._

### Private

A private IP address is assigned to each device on your network, like computers, tablets, and smartphones, by your router.

_Example: IP addresses generated by your home router for your devices._

Here’s the corrected and properly formatted text:

### Static

A static IP address does not change and is manually assigned. These are more reliable and often used for important services like hosting websites or remote access.

**Example Use Case:**
- **Server:** `192.168.1.10` (A server in a company network that needs a fixed address for remote access)

### Dynamic

A dynamic IP address changes periodically and is assigned by a [DHCP](https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol) server. These are more common, cheaper, and allow us to reuse IP addresses for most consumer devices.

**Example Use Case:**
- **Home Computer:** `192.168.1.15` (A computer connected to a home Wi-Fi network where the IP address may change periodically)


# OSI Model

The OSI Model is a framework for understanding network communication, divided into seven layers. Each layer builds on the previous one to standardize and simplify networking. It acts as a universal language for network communication, ensuring different systems can work together effectively.

**Interoperability** is the ability of different systems or software to communicate and work together, regardless of their origin or technology.
 
## Why Does the OSI Model Matter?

The OSI Model standardizes terminology for networking discussions and documentation, allowing us to break down and evaluate complex communication processes. Although TCP/IP networks are more commonly implemented today, the OSI Model still offers several benefits:

**P**lease **E**veryone **E**njoy **S**imple **S**olutions

- **Promotes Compatibility**: Encourages interoperable networking products.
- **Eases Troubleshooting**: Identifies and resolves issues across the network stack.
- **Enhances Security**: Supports a security-first approach.
- **Simplifies Complexity**: Breaks down complex functions into  manageable components.
- **Standardizes Terminology**: Provides a common language for networking discussions.


## Layers

The seven abstraction layers of the OSI model can be defined as follows, from top to bottom:

**Mnemonic**: **A**ll **P**eople **S**eek **T**o **N**avigate **D**igital **P**aths

- **A**pplication
- **P**resentation
- **S**ession
- **T**ransport
- **N**etwork
- **D**ata Link
- **P**hysical

Here's a concise overview of each OSI layer:

1. **Application**: Interfaces directly with user data; handles protocols like HTTP and SMTP.
2. **Presentation**: Translates, encrypts, decrypts, and compresses data for network transmission.
3. **Session**: Manages and maintains communication sessions; ensures data is properly synchronized and sessions are closed properly.
4. **Transport**: Ensures end-to-end communication; segments data for the Network layer and reassembles it on the receiving end.
5. **Network**: Handles data transfer between different networks; breaks data into packets and determines the best route (routing).
6. **Data Link**: Manages data transfer between devices on the same network; breaks packets into frames.
7. **Physical**: Involves the physical equipment for data transfer; converts data into bit streams (1s and 0s).


Here's a Detailed overview of each OSI layer:

1. **Application**:This layer interacts directly with user data and manages protocols such as HTTP and SMTP. Software applications like web browsers and email clients rely on the application layer to initiate communication.
   
   **Note**: The application layer is responsible for protocols and data manipulation, not the client software itself.

2. **Presentation**: Also known as Translation layer. It formats data from the application layer and it Translates, encrypts, decrypts, and compresses data for network transmission.

3. **Session**: Responsible for opening and closing communication sessions between two devices. It maintains sessions long enough to transfer all data and closes them to conserve(preventing waste usage of) resources.Ensures data is properly synchronized(using checkpoints) and sessions are closed.

   **session**: The time between when the communication is opened and closed is known as the session.

4. **Transport**:Takes data from the `Session layer`. Breaks data into segments for the `Network layer` and reassembles them on the receiving device.Ensures  reliable end-to-end communication

5. **Network**: Handles data transfer between different networks; breaks data into packets, finds the best route (routing), and reassembles packets at the destination.

   **Briefly**: Managing data transfer between networks by breaking up segments into packets, routing them to their destination, and reassembling them at the receiving device. The Network layer determines the best path (routing) for data.

   **Note**: The Network layer is not needed if the devices are on the same network.
   **Routing**: The process of finding the optimal path for data to reach its destination.
   **Segment**: Typically used to refer to a piece of data at the Transport layer (e.g., TCP segments). It’s a specific term for data that has been divided from a larger body for transmission purposes.
   
   **Packets**: Packets are units of data that are transmitted over a computer network.
 
6. **Data Link**: `Manages data transfer between devices on the same network`.This Data link layer takes packets from the network layer, breaks them into smaller frames, and ensures reliable transfer of these frames within the same network.

7. **Physical**: Manages the physical equipment(cables, switches) for data transfer; converts data into bit streams (strings of 1s and 0s) and ensures both devices agree on signal conventions.


# TCP and UDP

## TCP

TCP (Transmission Control Protocol) is a connection-oriented protocol that establishes a connection before transmitting data, ensuring that information is sent and received in the correct order. It includes error-checking mechanisms to guarantee reliable delivery of data. However, this reliability comes with higher overhead, which results in greater bandwidth usage. TCP is well-suited for applications like file transfers and web page loading where accuracy and order are crucial.

![tcp](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/tcp-and-udp/tcp.png)



## UDP

UDP (User Datagram Protocol) is a connectionless and simpler protocol that doesn't require establishing or   a connection. It lacks error-checking and recovery services, sending data continuously without ensuring its receipt. This makes UDP ideal for real-time communications such as broadcasting or multicast transmissions. It's preferred over TCP when minimal latency is critical, and occasional data loss is acceptable.

![udp](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/tcp-and-udp/udp.png)

## TCP vs UDP

**"**C**ool **D**ogs **R**un **S**uper **B**rightly **C**omfortably"

- **C**onnection
- **D**elivery
- **R**e-transmission
- **S**peed
- **B**roadcasting
- **C**ommon Uses
### **TCP vs UDP**

#### **TCP (Transmission Control Protocol)**
- **Connection-oriented:** Establishes a connection before data transfer.
- **Reliability:** Guarantees delivery, error recovery, and order of data.
- **Overhead:** Higher due to connection management and error checking.
- **Use Cases:** Web pages (HTTP), emails (SMTP, POP), file transfers (FTP).

#### **UDP (User Datagram Protocol)**
- **Connectionless:** No need to establish a connection.
- **Speed:** Faster due to lower overhead and no connection management.
- **Reliability:** No guarantee of delivery, order, or error recovery.
- **Use Cases:** Streaming video, online gaming, DNS queries.

| **Feature**        | **TCP**                                   | **UDP**                               |
|--------------------|-------------------------------------------|---------------------------------------|
| **Connection**     | Requires connection                       | No connection required                |
| **Delivery**       | Guaranteed                                | No guarantee                           |
| **Re-transmission**| Yes                                       | No                                    |
| **Speed**          | Slower                                    | Faster                                |
| **Broadcasting**   | No                                        | Yes                                    |
| **Common Uses**    | HTTPS, HTTP, FTP                          | Video streaming, DNS, VoIP            |

- **TCP** is suitable for applications where reliability and order are crucial, while **UDP** is preferred for applications where speed is more critical than reliability.

# Domain Name System (DNS)

The Domain Name System (DNS) is a hierarchical and decentralized naming system that translates human-readable domain names, like `google.com`, into IP addresses, such as `122.250.192.232`. This system allows us to use easily memorable names instead of numeric IP addresses to connect with websites and services.

## How DNS works

![how-dns-works](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/domain-name-system/how-dns-works.png)

DNS lookup involves the following steps:
Your description of the DNS lookup process is comprehensive and detailed.
---

### DNS Lookup Process

1. **User’s Browser: Initiating the Request**  
   You enter a URL (e.g., `www.example.com`) into your browser’s address bar.

2. **Local Cache Check (Browser)**  
   The browser checks its local cache for the IP address of the domain. If found, it skips the rest of the process.

3. **OS Cache Check**  
   If the IP isn’t cached in the browser, it checks the operating system’s DNS cache.

4. **Proxy Server (if used)**  
   If a proxy server is configured, the DNS request is sent to it.

5. **Router or Local DNS Resolver**  
   If no proxy is involved, the request goes to your router or local DNS resolver, often provided by your ISP. It checks its cache for the IP address.

6. **Private DNS Server (if configured)**  
   If the router’s cache doesn’t have the record, it queries any local private DNS servers.

7. **ISP’s Recursive DNS Resolver**  
   If needed, the request is forwarded to your ISP’s recursive DNS resolver, which has a larger cache.

8. **Root Name Server**  
   If the ISP’s resolver doesn’t have the information, it queries a root name server, which directs it to the appropriate TLD server.

9. **Top-Level Domain (TLD) Server**  
   The TLD server (e.g., `.com`) provides the IP address of the domain's authoritative name server.

10. **Authoritative Name Server**  
    The authoritative name server for `example.com` provides the IP address. It may have multiple IPs for redundancy and load balancing.

11. **GeoDNS (if used)**  
    Some authoritative servers use GeoDNS to provide IP addresses based on the user’s geographic location.

12. **ISP’s Recursive DNS Resolver (Again)**  
    The resolver caches the IP address and returns it to the private DNS server.

13. **Private DNS Server (Again)**  
    The private DNS server caches the IP address and sends it to the router.

14. **Router or Local DNS Resolver (Again)**  
    The router caches the IP address and provides it to the browser.

15. **User’s Browser (Finally)**  
    The browser receives the IP address and connects to the web server to load the requested webpage.

## Server types

Now, let's look at the four key groups of servers that make up the DNS infrastructure.

### DNS Resolver

A DNS resolver, also known as a DNS recursive resolver, is the first point of contact in a DNS query. It acts as an intermediary between a client and various DNS servers. Upon receiving a DNS query, the resolver either returns a cached response or performs a series of queries:

1. Queries a root nameserver.
2. Queries a TLD nameserver.
3. Queries an authoritative nameserver.

Once it receives the IP address from the authoritative nameserver, it sends the response back to the client.

### DNS Root Server

A root server handles queries from DNS resolvers by directing them to a TLD nameserver based on the domain extension (e.g., `.com`, `.net`). Managed by the Internet Corporation for Assigned Names and Numbers (ICANN), there are 13 types of root servers, each with multiple instances globally using Anycast routing for efficiency.

**Anycast Routing**: A network addressing and routing method where multiple servers share the same IP address, and traffic is routed to the nearest or best-performing server.

**Example**: Cloudflare’s Anycast network routes requests to the nearest data center for faster content delivery.

**Use Case**: Improving the speed and reliability of global content delivery by routing users to the nearest server.



### TLD Nameserver

A TLD nameserver manages domain names under a specific top-level domain (TLD), such as `.com`, `.net`, or country-specific domains like `.uk` or `.us` or whatever comes after the last dot in a URL. The Internet Assigned Numbers Authority (IANA), part of ICANN, breaks  these servers, dividing them into 4 groups:

- **Generic TLDs:** `.com`, `.org`, `.net`, etc.
- **Country Code TLDs:** `.uk`, `.us`, `.ru`, etc.
- **Sponsored TLDs**: A few dozen, such as `.edu`, `.gov`.
- **Infrastructure TLDs**: Currently just one, `.arpa`.
(Address and Routing Parameter Area).
### Authoritative DNS Server

The authoritative nameserver holds DNS records for a domain (e.g., `google.com`). It provides the IP address for the domain or an alias (CNAME record). If the domain cannot be found, it returns an NXDOMAIN message. This is usually the final step in the DNS lookup process.

### Query Types

- **Recursive Query:** The DNS server must return either the requested resource record or an error message if it cannot find the record.
- **Iterative Query:** The DNS server returns the best answer it can or refers the DNS client to another DNS server (e.g., a root or authoritative server). The DNS client must then repeat the query as directed.
- **Non-recursive Query:** The DNS server either returns a cached record or queries an authoritative server for the record. There are no additional rounds of queries.


## Record Types

DNS records, 
  also known as zone files,
  these records are sets of instructions stored in authoritative DNS servers.
  these records provide details about a domain, such as the IP address associated with the domain and how to handle requests.
  These records are written in a format called DNS syntax, which consists of text commands for DNS servers. Additionally, 
  each DNS record has a "TTL" (time-to-live), which defines how frequently the record is refreshed.

Most commonly used records:

- **A (Address)**:  
  Maps a domain name to an **IPv4 address**. It is used to find the web server that hosts the domain.  
  **Example**: `example.com` → `192.0.2.1`

- **AAAA (IPv6 Address)**:  
  Maps a domain name to an **IPv6 address**. This is similar to an A record but for IPv6, which is the newer version of IP addresses.  
  **Example**: `example.com` → `2001:0db8::1`

- **CNAME (Canonical Name)**:  
  Forwards one domain or subdomain to another domain name. **Does not provide an IP address** directly. Often used to alias one domain to another, like redirecting `www.example.com` to `example.com`.  
  **Example**: `www.example.com` → `example.com`

- **MX (Mail Exchanger)**:  
  Directs emails to specific email servers for the domain. Without an MX record, email cannot be routed to the domain.  
  **Example**: `example.com` → `mail.example.com` (email server)

- **TXT (Text)**:  
  Allows domain administrators to store **text notes**. Often used for **email security** configurations like SPF, DKIM, or DMARC, which help prevent email spoofing.  
  **Example**: `example.com` → `"v=spf1 include:_spf.google.com ~all"` (SPF record)

- **NS (Name Server)**:  
  Specifies which **DNS servers** are authoritative for the domain, meaning these servers hold the correct DNS records for that domain.  
  **Example**: `example.com` → `ns1.nameserver.com`

- **SOA (Start of Authority)**:  
  Stores essential **administrative information** about a domain, including the primary name server, the email of the domain admin, and other control settings for the domain.  
  **Example**: Holds details like `ns1.nameserver.com` and `admin@example.com`.

- **SRV (Service Location)**:  
  Specifies the **location (port and hostname)** of specific services, like VoIP or instant messaging services, making it easier to connect to these services.  
  **Example**: `_sip._tcp.example.com` → `sipserver.example.com:5060`

- **PTR (Pointer)**:  
  Used for **reverse DNS lookups**, meaning it maps an **IP address** back to a **domain name**. It’s the reverse of an A or AAAA record.  
  **Example**: `192.0.2.1` → `example.com`

- **CERT (Certificate)**:  
  Stores **public key certificates** to associate a domain with a cryptographic key. It is used to improve security for services like email or websites.  
  **Example**: `example.com` → certificate details (for secure communication).


## Subdomains
It is a part of a main domain name used to organize different sections or services of a website.

### Example:
- **subdomain.example.com**

### Use:
- **blog.example.com**: Used for a blog section.
- **shop.example.com**: Used for an online store.

## DNS Zones

 A DNS zone is a portion of a domain's DNS settings that is managed separately by an entity(person, organization, or company).

**Use**: It allows control over `DNS records` for specific parts of a domain, like subdomains or name servers.

## DNS Caching

**one-word**: DNS cache is just a memory of recent DNS lookups

**Definition**: A **DNS cache** is a temporary storage on a computer that saves recent DNS lookups, helping to quickly load websites by avoiding repeated DNS queries.

**Use**: It speeds up website loading by reusing previously resolved domain names, and each record has a time-to-live (TTL) that defines how long it stays in the cache.

**works**
In the Domain Name System (DNS), each DNS record has a **time-to-live (TTL)**, which tells how long it can stay in a **cache** (temporary memory). The TTL is set in **seconds**.

When your computer gets a DNS record, it stores it in the cache with the TTL. As time passes . Once TTL reaches **zero**, the record is deleted from the cache. If your computer needs that record again, it has to go through the **DNS resolution process** 

## Reverse DNS

**Definition**: A **reverse DNS lookup** finds the **domain name** associated with a given **IP address** (the opposite of regular DNS, which finds an IP from a domain name).

**Use**: It is commonly used by **email servers** to verify if an email is coming from a legitimate(valid) server by checking if the IP has a valid **PTR record**. Servers without PTR records may have their emails rejected.

Many email servers will reject messages from any server that does not support reverse lookups

### PTR Records:

**Definition**: A **PTR (Pointer) record** is a type of DNS record used for **reverse DNS lookups**, which links an **IP address** to a **domain name**.

## Examples

### Widely Used Managed DNS Solutions Explained

1. **[Route53](https://aws.amazon.com/route53) (AWS)**:
   - A scalable **DNS service** by Amazon Web Services (AWS).
   - Used to route end-user requests to infrastructure like **Amazon EC2** or other services.
   - Offers features like **domain registration**, **DNS failover**, and **load balancing**.

2. **[Cloudflare DNS](https://www.cloudflare.com/dns)**:
   - A **fast** and **secure DNS service**.
   - Focuses on protecting websites from **DDoS attacks** and improving performance with **content delivery**.
   - Provides DNS services with free and paid options, including **advanced security features**.

3. **[Google Cloud DNS](https://cloud.google.com/dns)**:
   - A fully managed, high-performance DNS service by **Google Cloud**.
   - Provides **low-latency** and **global** DNS resolution.
   - Integrates with **Google’s cloud infrastructure**, ideal for scaling and reliable services.

4. **[Azure DNS](https://azure.microsoft.com/en-in/services/dns) (Microsoft)**:
   - A DNS hosting service provided by **Microsoft Azure**.
   - Enables you to host your **DNS zones** on **Azure's infrastructure**.
   - Seamless integration with other Azure services and **99.99% availability**.

5. **[NS1](https://ns1.com/products/managed-dns)**:
   - A managed DNS provider known for **intelligent traffic routing** and **high availability**.
   - Offers advanced features like **geo-routing**, **filtering** and **automated traffic management**.
   - Used by companies with **global traffic** and a need for **customized DNS configurations**.

### Purpose:
These managed DNS services help businesses efficiently control domain name systems (DNS), optimize performance, ensure `high availability`, and add `security` to their web traffic.

### Load Balancing

**Definition:**
Load balancing is the process of distributing incoming network traffic across multiple resources (servers) to ensure that no single resource is overwhelmed(**overloaded** or **burdened** beyond capacity). This improves **availability** and **reliability** of services.

**reliability**:a website or service stays available and works properly even when there is heavy traffic or when some servers fail.

**Benefits:**
- **High Availability**: Traffic is directed only to online resources, minimizing downtime.
- **Reliability**: If one server fails, others can handle the load, ensuring continuous service.
- **Scalability**: Easily add or remove servers based on demand.

**Illustrations:**

1. **Basic Load Balancing**:
   ![Load Balancing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/load-balancing/load-balancer.png)
   - Distributes traffic across multiple servers.

2. **Load Balancing Layers**:
   ![Load Balancing Layers](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/load-balancing/load-balancer-layers.png)
   - Load balancing can occur at different layers (e.g., application, network) for additional scalability and redundancy.

**Use Cases:**
- **Web Servers**: Spread incoming web requests to multiple servers.
- **Database Servers**: Spread database queries across multiple servers to prevent any one server from becoming too slow.
- **Application Servers**: Ensure applications remain responsive under varying loads.


### Why Use Load Balancers?

**High Traffic Needs:**
- Modern websites handle huge volumes of simultaneous requests. To manage this efficiently, adding more servers is essential.

**Role of a Load Balancer:**
- **Distributes Requests**: It routes incoming requests across all available servers to maximize performance and prevent any single server from becoming overloaded.
- **Maintains Performance**: Ensures that no server is overworked, which helps keep the website running smoothly.
- **Handles Failures**: If a server fails, the load balancer redirects traffic to the remaining servers.
- **Supports Scaling**: Automatically includes new servers into the rotation as they are added.

**Benefits:**
- **Improves Speed**: By balancing the load, the website responds faster.
- **Increases Reliability**: Keeps the site running smoothly even if some servers fail.
- **Enhances Scalability**: Makes it easier to add more servers as traffic grows.


### Workload Distribution by Load Balancers

**Core Functionality:**
Load balancers distribute incoming requests to multiple servers based on different criteria to optimize performance and resource usage.

**Common Variations:**

- **Host-based Distribution**:
  - Routes requests based on the **requested hostname** (e.g., `www.example.com` vs. `api.example.com`).
  - **Use**: Directs traffic to different servers based on domain names.

- **Path-based Distribution**:
  - Uses the **URL path** (e.g., `/images/` vs. `/api/`) to route requests.
  - **Use**: Directs traffic to servers based on specific paths within the website.

- **Content-based Distribution**:
  - Analyzes the **message content** (e.g., parameter values) of the request.
  - **Use**: Routes requests based on the content of the request, like different data values or request types.

## Layers
Load balancers operate at one of the two levels:

**1. Network Layer (Layer 4):**
- **Function**: Routes traffic based on **IP addresses** and **network ports**.
- **Capabilities**: Does not perform content-based routing.
- **Speed**: Often uses dedicated hardware for high-speed operation.

**2. Application Layer (Layer 7):**
- **Function**: Routes traffic based on **entire requests**, including **URL paths** and **content**.
- **Capabilities**: Supports content-based routing for more detailed management of traffic.
- **Understanding**: Can make decisions based on the full context of the request.


## Types

Let's look at different types of load balancers:

### Types of Load Balancers

**1. Software Load Balancers:**
- **Deployment**: Easier and more cost-effective to set up than hardware versions.
- **Flexibility**: Can be customized to fit specific needs of software environments.
- **Management**: Available as installable solutions or managed cloud services.
- **Pros**: Greater flexibility, easier upgrades, and cost-effective.
- **Cons**: May require more setup and ongoing management.

**2. Hardware Load Balancers:**
- **Deployment**: Physical devices used on-premises.
- **Capacity**: Can handle high volumes of traffic but are more expensive.
- **Maintenance**: Requires updates and maintenance of proprietary firmware.
- **Pros**: High performance and reliability for large-scale traffic.
- **Cons**: Less flexible and more costly.

**3. DNS Load Balancers:**
- **Function**: Distributes client requests across a group of servers using DNS.
- **Limitations**: DNS does not monitor server status or handle failures effectively.
- **Pros**: Simple to implement and manage.
- **Cons**: Less reliable due to lack of failure detection and recovery.


### Routing Algorithms

**1. Round-robin**: Distributes requests evenly(balanced distribution) to all servers in a circular order.

**2. Weighted Round-robin**: Extends Round-robin by assigning weights to servers based on their capacity, distributing more requests to servers with higher weights.

**3. Least Connections**: Sends requests to the server with the fewest active connections.

**4. Least Response Time**: Chooses the server with the fastest response time and fewest active connections.

**5. Least Bandwidth**: Directs requests to the server handling the least amount of traffic (measured in Mbps).

**6. Hashing**: Uses a defined key (e.g., client IP, request URL) to distribute requests, ensuring consistent routing based on the key.


### Advantages of Load Balancing
Load balancing also plays a key role in preventing downtime, other advantages are:

1. **Scalability**: Easily add or remove servers to handle varying amounts of traffic.
2. **Redundancy**: Ensures continuous operation even if some servers fail.
3. **Flexibility**: Adapts to different types of requests and traffic patterns.
4. **Efficiency**: Optimizes resource usage and improves response times.

### Redundant Load Balancers

![redundant-load-balancing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/load-balancing/redundant-load-balancer.png)

- **Purpose**: Prevents the load balancer from becoming a single point of failure.
- **Method**: Use multiple load balancers in a cluster, with an active and passive setup for fault tolerance.

### Features of Load Balancers

- **Autoscaling**: Starting up and shutting down resources in response to demand conditions.
- **Sticky sessions**: The ability to assign the same user or device to the same resource in order to maintain the session state on the resource.
- **Healthchecks**: The ability to determine if a resource is down or performing poorly in order to remove the resource from the load balancing pool.
- **Persistence connections**: Allowing a server to open a persistent connection with a client such as a WebSocket.
- **Encryption**: Handling encrypted connections such as TLS and SSL.
6. **Certificates**: Handles client and server certificates for authentication.
7. **Compression**: Reduces response size for faster delivery.
8. **Caching**:An application-layer load balancer Stores frequently accessed data to improve performance.
9. **Logging**: Records request and response details for auditing and analytics.
- **Request tracing**: Assigning each request a unique id for the purposes of logging, monitoring, and troubleshooting.
11. **Redirects**: Sends users to different URLs based on request factors.
12. **Fixed Response**: Provides static responses like error messages when needed.

### Examples of Load Balancing Solutions

1. **Amazon Elastic Load Balancing**: Provides scalable load balancing for applications on AWS.
   - [AWS Elastic Load Balancing](https://aws.amazon.com/elasticloadbalancing)

2. **Azure Load Balancing**: Offers high availability and network traffic distribution for Azure services.
   - [Azure Load Balancer](https://azure.microsoft.com/en-in/services/load-balancer)

3. **GCP Load Balancing**: Distributes traffic across Google Cloud resources with global scaling.
   - [Google Cloud Load Balancing](https://cloud.google.com/load-balancing)

4. **DigitalOcean Load Balancer**: Easy-to-use load balancing solution for DigitalOcean's cloud infrastructure.
   - [DigitalOcean Load Balancer](https://www.digitalocean.com/products/load-balancer)

5. **Nginx**: Popular web server and load balancer known for high performance and flexibility.
   - [Nginx](https://www.nginx.com)

6. **HAProxy**: Widely-used open-source load balancer and proxy server for high availability.
   - [HAProxy](http://www.haproxy.org)

# Clustering

**Clustering** involves connecting multiple computers (nodes) to work together as a single system to enhance performance and reliability. Here's a breakdown:

- **Purpose**: Distribute tasks and workloads across multiple nodes to combine their memory and processing power, improving overall performance.
- **Setup**: Nodes are networked together and managed by software to function as a cohesive unit(all the individual nodes function together). They may use shared or local storage.
- **Leader Node**: One node often acts as the leader, directing tasks to other nodes and handling responses.
- **User Experience**: The cluster should operate as a single system from the user's perspective, minimizing latency and avoiding bottlenecks in communication between nodes.

**Example**: A web service that handles a large volume of requests might use a cluster to ensure smooth performance and reliability.

![cluster](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/clustering/cluster.png)


## Types
# Types of Computer Clusters

## Highly Available (Failover)
Ensures systems remain online by switching to a backup node if a primary one fails.

## Load Balancing
Distributes tasks across multiple nodes to avoid overload on a single node.

## High-Performance Computing (HPC)
Combines the power of multiple nodes for complex computations and intensive tasks.

# Cluster Configurations
The two most commonly used high availability (HA) clustering configurations are active-active and active-passive.

## Active-Active

![active-active](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/clustering/active-active.png)

Multiple nodes are active and handle tasks simultaneously for load balancing and improved performance.

The main purpose of an `active-active cluster` is to `achieve load balancing`. 

An active-active cluster is made up of at least two nodes.
both actively running the same kind of service simultaneously.

`A load balancer distributes workloads across all nodes to prevent any single node from getting overloaded`.

## Active-Passive
![active-passive](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/clustering/active-passive.png)

Only One node is active, while the other(s) are on standby or passive, ready to take over if the active node fails.


# Load Balancing vs. Clustering

## Difference Between Load Balancing and Clustering

| Feature            | Load Balancing                                        | Clustering                                              |
|--------------------|-------------------------------------------------------|---------------------------------------------------------|
| **Purpose**         | Distributes incoming traffic across multiple servers. | Groups multiple servers to work together as one system. |
| **Independence**    | Servers are independent and unaware of each other.    | Nodes are aware of each other and share resources.       |
| **Failover**        | Redirects traffic if a server fails.                  | Automatic recovery from node failures.                  |
| **Setup**           | Simple to configure and scale.                        | More complex setup with node synchronization.           |
| **Usage**           | Ideal for web services, applications, and APIs.       | Ideal for high-performance computing and databases.      |

## Advantages and Disadvantages of Load Balancing

### Advantages

| Advantage           | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| **Scalability**      | Easily add or remove servers based on traffic demands.                      |
| **Simplicity**       | Easier to configure and deploy compared to clustering.                      |
| **Performance**      | Prevents any one server from becoming overloaded.                           |
| **Failover**         | Redirects traffic to available servers in case of failure.                  |
| **Cost-effective**   | Minimal hardware requirements, making it cost-effective.                    |

### Disadvantages

| Disadvantage         | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| **No State Sharing** | Servers operate independently without sharing state or session information. |
| **Limited Redundancy**| Traffic may not be handled properly without clustering.                    |
| **Failover Limitations**| Lacks deeper fault-tolerance mechanisms found in clustering.             |

## Advantages and Disadvantages of Clustering

### Advantages

| Advantage             | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **High Availability**  | Ensures uninterrupted service even if a node fails.                         |
| **Resource Sharing**   | Nodes can share resources for better efficiency.                            |
| **Fault Tolerance**    | Automatically recovers from node failures, ensuring minimal downtime.        |
| **Redundancy**         | Provides redundancy, making the system more resilient.                      |
| **Improved Performance**| Combines the power of multiple nodes for better throughput.                |

### Disadvantages

| Disadvantage          | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **Complex Setup**      | Requires more intricate configuration and management.                      |
| **Synchronization**    | Data and resources need to be synchronized, adding overhead.               |
| **Cost**               | Requires more hardware and infrastructure, leading to higher costs.        |
| **Scalability Limitations**| Not as easy to scale as load balancing setups.                          |


# Combined Use of Load Balancing and Clustering

| Feature              | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| **Traffic Distribution** | Load balancing distributes incoming traffic evenly across nodes or servers. |
| **State Synchronization** | Clustering ensures nodes work together and synchronize state, improving redundancy. |
| **Resilience**        | Combining load balancing and clustering offers a more resilient and fault-tolerant system. |
| **Failover Mechanism**| Load balancing ensures continuous traffic flow, while clustering provides seamless failover by keeping nodes aware of each other. |
| **Performance**       | The combined approach ensures higher throughput and better response times by balancing loads and sharing resources between servers. |

# Advantages and Disadvantages of Combined Use

### Advantages

| Advantage             | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **High Availability**  | Ensures that services remain operational even if a node fails, by redirecting traffic and synchronizing state. |
| **Fault Tolerance**    | Faults are automatically handled by rerouting tasks to operational nodes.    |
| **Improved Efficiency**| Combines load balancing and clustering to maximize resource utilization and distribute workloads efficiently. |
| **Better Coordination**| Load balancers distribute traffic, while clusters work in unison to manage workloads and maintain consistency. |
| **Scalable Architecture** | Both load balancing and clustering allow for easy scalability by adding more nodes or servers. |

### Disadvantages

| Disadvantage           | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **Complex Setup**      | Combining both adds complexity in terms of configuration, deployment, and management. |
| **Higher Costs**       | Requires more infrastructure, resources, and administrative effort.         |
| **Synchronization Overhead** | Clustering can introduce overhead in synchronizing states between nodes. |
| **Difficult Maintenance** | Maintaining both load balancers and clusters requires specialized skills and monitoring tools. |

# Examples of Load Balancing

| Example                 | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| **Amazon ELB**           | Elastic Load Balancing from AWS distributes traffic across multiple EC2 instances. |
| **Nginx**                | An open-source load balancer that distributes web traffic to various servers. |
| **HAProxy**              | A reliable, high-performance load balancer widely used for web services.     |
| **Azure Load Balancer**  | Microsoft's service for distributing traffic to virtual machines.            |

# Examples of Clustering

| Example                  | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| **Kubernetes**            | Clusters containerized applications for automatic scaling and orchestration. |
| **Cassandra**             | A NoSQL database that uses clustering to distribute data across multiple nodes. |
| **MongoDB**               | A document-oriented database that utilizes clustering for distributed storage. |
| **Redis**                 | An in-memory data structure store that supports clustering for horizontal scaling and fault tolerance. |


# Caching

![caching](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/caching.png)

Caching is a performance optimization technique used to store copies of data temporarily to serve(or) access requests faster.

Caches  principle _"recently requested data is likely to be requested again"._

### Why Use Cache as a Mediator?
Caches serve as an intermediary layer to optimize data access while preserving the integrity of the main data sources.

- **Performance Boost**: Reduces the load on databases and speeds up data retrieval.
- **Reduced Latency**: Cached data can be served faster than querying the primary source each time.
- **Cost-Efficiency**: Minimizes expensive queries to primary sources like remote databases or APIs.

### Caching and Memory

Caches function like a hierarchical memory system, storing data in levels to balance speed and size:

- **L1 (Level 1)** is the smallest and fastest cache closest to the CPU.
- **L2, L3, etc.** caches are progressively larger but slower.

When data is requested, the system searches through cache levels (starting from L1) to retrieve it. If the data is not found (a **cache miss**), it is retrieved from slower memory or disk, then written to the cache for future requests.

### Cache Hit vs. Cache Miss

#### Cache Hit
A **cache hit** occurs when requested data is found in the cache. The hierarchy of cache levels determines the speed of access:

- **Hot cache**: Data retrieved from L1, the fastest possible.
- **Warm cache**: Data found in L2 or L3, slower than a hot cache.
- **Cold cache**: Data retrieved from lower levels, like L3 or beyond, still faster than fetching from main memory.

#### Cache Miss

A **cache miss** happens when data is not found in the cache. The system retrieves the data from slower memory(DB's, API's, File System's), then stores it in the cache for future use.

### Cache Miss Workflow:
1. **Cache Miss**: The requested data isn't found in the cache.
2. **Fetch from Primary Source**: The system fetches the data from the primary data source (e.g., a database).
3. **Store in Cache**: The fetched data is stored in the cache for faster retrieval in future requests.
4. **Return Response**: The data is returned to the user or application.

# Cache Invalidation

Cache invalidation is the process of removing or updating cache entries when the underlying data changes. If data becomes stale and isn't invalidated, it can cause inconsistencies. There are different caching strategies, each with trade-offs.

## Write-through cache

![write-through-cache](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/write-through-cache.png)

In a **write-through cache**, data is written to both the cache and the database simultaneously.

- **Pro**: Ensures strong consistency since cache and database are always in sync.
- **Con**: Higher latency for write operations because data is written twice.

## Write-around cache

![write-around-cache](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/write-around-cache.png)

In a **write-around cache**, data is written directly to the database, bypassing the cache.

- **Pro**: Reduces cache write load, potentially lowering write latency.
- **Con**: Increases cache misses, leading to higher read latency for frequently written data, as it must be fetched from the slower database.

## Write-back cache

![write-back-cache](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/write-back-cache.png)

In a **write-back cache**, data is written to the cache first and asynchronously written to the database later.

- **Pro**: Lower write latency and higher throughput, ideal for write-heavy workloads.
- **Con**: Risk of data loss if the cache crashes before syncing to the database. This risk can be mitigated with replication in the cache.

Each strategy has trade-offs in terms of performance, latency, and data consistency, and the choice depends on the specific application needs.

## Eviction Policies

Eviction policies determine which cache entries are removed when the cache is full. Here are some common cache eviction strategies:

- **First In First Out (FIFO)**: The oldest entry in the cache (the first one added) is evicted first, regardless of access frequency.
- **Last In First Out (LIFO)**: The most recently added entry is evicted first, without considering access patterns.
- **Least Recently Used (LRU)**: Evicts the entry that has not been accessed for the longest time, assuming that older data is less likely to be reused.
- **Most Recently Used (MRU)**: In contrast to LRU, this policy evicts the most recently accessed entry.
- **Least Frequently Used (LFU)**: Tracks how often an entry is used, evicting the one used the least.
- **Random Replacement (RR)**: Selects a random cache entry for eviction, regardless of when it was added or how frequently it was accessed.

Each policy serves different use cases, balancing cache efficiency, and memory use based on the application’s data access patterns.

## Distributed Cache
 
![distributed-cache](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/distributed-cache.png)

A distributed cache pools memory (RAM) from multiple networked computers (often called nodes) into a single logical in-memory data store.

**Example**: Redis Cluster (where multiple Redis nodes form a single cluster), offers fast data access and scalability beyond the limits of a single machine.

 
## Global Cache

![global-cache](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/global-cache.png)


A global cache is a shared, centralized cache that all application nodes access. If data is missing from the global cache, the cache retrieves it from the underlying data source.


## Use Cases

- **Database Caching**
- **Content Delivery Network (CDN)**
- **Domain Name System (DNS) Caching**
- **API Caching**

### When Not to Use Caching:

- When cache access takes as long as accessing the primary data store.
- When requests have low repetition, as caching relies on repeated access.
- When data changes frequently, which can cause the cache to fall out of sync.

_It's important to note that a cache should not be used as permanent data storage. They are almost always implemented in volatile memory because it is faster, and thus should be considered transient._

## Advantages of Caching

- Improves performance
- Reduces latency
- Decreases load on the database
- Lowers network costs
- Increases read throughput

## Common Technologies

- [Redis](https://redis.io)
- [Memcached](https://memcached.org)
- [Amazon Elasticache](https://aws.amazon.com/elasticache)
- [Aerospike](https://aerospike.com)


# Content Delivery Network (CDN)

A content delivery network (CDN) is a geographically distributed group of servers that work together to provide fast delivery of internet content. Generally, static files such as HTML/CSS/JS, photos, and videos are served from CDN.



## Why use a CDN?

Content Delivery Network (CDN) increases content availability and redundancy while reducing bandwidth costs and improving security. Serving content from CDNs can significantly improve performance as users receive content from data centers close to them and our servers do not have to serve requests that the CDN fulfills.

## How does a CDN work?

![cdn](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/content-delivery-network/cdn.png)

In a CDN, the origin server contains the original versions of the content while the edge servers are numerous and distributed across various locations around the world.

To minimize the distance between the visitors and the website's server, a CDN stores a cached version of its content in multiple geographical locations known as edge locations. Each edge location contains several caching servers responsible for content delivery to visitors within its proximity.

Once the static assets are cached on all the CDN servers for a particular location, all subsequent website visitor requests for static assets will be delivered from these edge servers instead of the origin, thus reducing the origin load and improving scalability.

For example, when someone in the UK requests our website which might be hosted in the USA, they will be served from the closest edge location such as the London edge location. This is much quicker than having the visitor make a complete request to the origin server which will increase the latency.

## Types

CDNs are generally divided into two types:

### Push CDNs

Push CDNs receive new content whenever changes occur on the server. We take full responsibility for providing content, uploading directly to the CDN, and rewriting URLs to point to the CDN. We can configure when content expires and when it is updated. Content is uploaded only when it is new or changed, minimizing traffic, but maximizing storage.

Sites with a small amount of traffic or sites with content that isn't often updated work well with push CDNs. Content is placed on the CDNs once, instead of being re-pulled at regular intervals.

### Pull CDNs

In a Pull CDN situation, the cache is updated based on request. When the client sends a request that requires static assets to be fetched from the CDN if the CDN doesn't have it, then it will fetch the newly updated assets from the origin server and populate its cache with this new asset, and then send this new cached asset to the user.

Contrary to the Push CDN, this requires less maintenance because cache updates on CDN nodes are performed based on requests from the client to the origin server. Sites with heavy traffic work well with pull CDNs, as traffic is spread out more evenly with only recently-requested content remaining on the CDN.

## Disadvantages

As we all know good things come with extra costs, so let's discuss some disadvantages of CDNs:

- **Extra charges**: It can be expensive to use a CDN, especially for high-traffic services.
- **Restrictions**: Some organizations and countries have blocked the domains or IP addresses of popular CDNs.
- **Location**: If most of our audience is located in a country where the CDN has no servers, the data on our website may have to travel further than without using any CDN.

## Examples

Here are some widely used CDNs:

- [Amazon CloudFront](https://aws.amazon.com/cloudfront)
- [Google Cloud CDN](https://cloud.google.com/cdn)
- [Cloudflare CDN](https://www.cloudflare.com/cdn)
- [Fastly](https://www.fastly.com/products/cdn)

# Content Delivery Network (CDN)

![cdn-map](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/content-delivery-network/cdn-map.png)

A **CDN** is a globally distributed system of servers that delivers web content to users from locations closest to them. CDNs help reduce latency by caching static assets (HTML, CSS, JavaScript, images, videos) on edge servers near users, ensuring faster load times.

### **Why use a CDN?**
- **Performance**: Reduces latency by serving content from servers closer to users.
- **Scalability**: Offloads traffic from origin servers, enabling better handling of spikes in demand.
- **Availability**: Increases redundancy, so if one server fails, others can handle the load.
- **Security**: Protects the origin server from direct attacks, like DDoS, by acting as a buffer.

### **How does a CDN work?**
![cdn](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/content-delivery-network/cdn.png)


A CDN caches the content from the origin server at multiple **edge locations** globally. When a user requests content, the CDN delivers it from the nearest edge location, reducing the time it takes to retrieve the data and decreasing server load.

1. **Origin Server**: Stores the original version of the content.
2. **Edge Servers**: Cache copies of the content at different locations, reducing latency.

For example, a user in London requesting a website hosted in the USA will be served from an edge server in London instead of fetching it from the USA, speeding up content delivery.

## Types of CDN

### Push CDN

In a **Push CDN**, the website owner is responsible for uploading content to the CDN manually. Whenever changes are made to the server content, they are "pushed" to the CDN, and the URLs are rewritten to point to the CDN. Content stays on the CDN until it is updated or expires based on pre-configured rules.

- **Best for**: Websites with infrequent updates or low traffic.
- **Pros**:
  - Greater control over when and what content is cached.
  - Minimizes traffic between the origin server and CDN by only uploading new or changed content.
- **Cons**:
  - Requires manual uploads and configuration.
  - Maintenance overhead due to content management.

### Pull CDN

In a **Pull CDN**, content is fetched and cached by the CDN when requested by the client. When a request for static content is made, the CDN first checks if it already has the content. If not, it fetches the content from the origin server, caches it, and serves it to the client. Subsequent requests for the same content are served from the cache.

- **Best for**: Websites with frequent content updates or heavy traffic.
- **Pros**:
  - Requires less manual effort since content is cached based on demand.
  - CDN nodes are updated automatically as users request content, making it suitable for dynamic content.
- **Cons**:
  - Initial requests can result in higher latency as the content is pulled from the origin server before being cached.

### Disadvantages of CDNs

**"CRaSHeD"**

- **C**: **Cost** - Can be expensive, especially with high traffic.
- **R**: **Restrictions** - Some regions or organizations block CDN domains.
- **S**: **Security** - Potential for security issues if not properly managed.
- **H**: **Hidden** - Performance impact if CDN has no nearby servers.
- **D**: **Delay** - Uncached or stale content can increase latency.

1. **Cost**: CDNs can be expensive, especially for websites with high traffic or large amounts of data being delivered. Usage-based pricing may result in unpredictable costs.
  
2. **Latency for Uncached Content**: If the content isn't already cached in a nearby CDN edge server, the first request may experience slower loading times as it needs to be fetched from the origin server.

3. **Complex Configuration**: Managing and configuring a CDN, especially with push CDNs, can require extra setup and maintenance, such as manually uploading content and configuring expiration rules.

4. **Geo-Restrictions**: Some regions or countries may block specific CDN services, limiting the reach of the website's content to those areas.

5. **Location Dependent**: If the CDN doesn't have a server close to a user's location, it may not provide significant performance improvements compared to serving content directly from the origin.

6. **Security Risks**: Improperly configured CDNs can lead to data exposure or potential vulnerabilities. Additionally, relying on third-party CDN providers introduces a potential attack surface if those services are compromised.

### **Examples**:
- **Amazon CloudFront**
- **Google Cloud CDN**
- **Cloudflare**
- **Fastly**

## Proxy Server

A proxy server acts as an intermediary between clients and backend servers. It handles client requests, relays them to origin servers, and can perform tasks such as filtering, logging, and transforming requests(by adding/removing headers, encrypting/decrypting, or compression).

## Types
There are two types of proxies:
![FWD Rvrse Proxy](https://i.sstatic.net/0qpxZ.png)


### Forward Proxy

A forward proxy(proxy or proxy server or web proxy), sits between clients and the internet. It handles requests from clients, interacting with web servers on their behalf.

![forward-proxy](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/proxy/forward-proxy.png)

**Advantages:**

- **Block**: Restricts access to certain content.
- **Geo**: Accesses geo-restricted content.
- **Anonymity**: Hides user identity.
- **Bypass**: Overcomes other browsing restrictions.

*Note*: Proxies can still track personal information. Setup and maintenance of a proxy server can be costly and requires configurations

### Reverse Proxy

A reverse proxy sits in front of one or more web servers. It intercepts client requests before they reach the origin servers.

![reverse-proxy](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/proxy/reverse-proxy.png)

**Advantages:**

- **Security**: Protects backend servers from direct exposure.
- **Caching**: Improves performance by caching content.
- **SSL**: Manages SSL encryption.
- **Load Balancing**: Distributes client requests across multiple servers.
- **Scalability**: Enhances flexibility and scalability.

*Note*: Using a reverse proxy can introduce complexity and a single point of failure. Configuring multiple reverse proxies increases complexity further.

# FWD vs ReverseProxy
**Forward Proxy**: Sits between clients and the internet. It handles client requests, provides anonymity, and controls access to websites.

**Reverse Proxy**: Sits between the internet and one or more servers. It handles incoming requests from the internet, provides load balancing, caching, and security for the servers.

## Load balancer vs Reverse Proxy

**Load Balancer**: Distributes incoming network traffic across multiple servers to ensure no single server becomes overwhelmed. It's primarily used to manage traffic across servers that perform the same function, improving availability and reliability.

**Reverse Proxy**: Sits between Internet and servers to handle client requests. It can provide additional functionalities such as caching, SSL termination, and security. While a reverse proxy can also perform load balancing, its main role is broader and can be used even with a single server.

In essence, while a reverse proxy can include load balancing as one of its features, a load balancer is specifically designed to distribute traffic among multiple servers.

## Examples

Below are some commonly used proxy technologies:

- [Nginx](https://www.nginx.com)
- [HAProxy](http://www.haproxy.org)
- [Traefik](https://doc.traefik.io/traefik)
- [Envoy](https://www.envoyproxy.io)

# Availability

- Availability is the percentage of time a system or service is operational and accessible during a specific period. -**Use**: It helps measure how often users can rely on a system to be available.

**Example**:  
- If a server is available 99% of the time, it means the server is operational and accessible for 99% of a given time period (e.g., a year or a day). For 1% of the time, it may be down for maintenance or due to failure.
The basic formula to calculate availability is:

\[\text{Availability} = \frac{\text{Uptime}}{\text{Uptime} + \text{Downtime}}\]

This gives the percentage of time a system is available.


## The Nine's of availability

- Availability is often measured in "nines." The more "nines" you have, the higher the system's availability.

\[
\text{Availability} = \frac{\text{Uptime}}{\text{Uptime} + \text{Downtime}}
\]

**Use**:  
- It's used to define service guarantees in **Service Level Agreements (SLAs)**. Businesses often promise a certain number of "nines" to show how much uptime the service will have.


**Example**:  
- A company offering a cloud service with "5 nines" of availability (99.999%) promises **5.25 minutes of downtime per year**. This means the system is expected to be down for only 5 minutes in an entire year.

 
| Availability (Percent)   | Downtime (Year)    | Downtime (Month)  | Downtime (Week)    |
| ------------------------ | ------------------ | ----------------- | ------------------ |
| 90% (one nine)           | 36.53 days         | 72 hours          | 16.8 hours         |
| 99% (two nines)          | 3.65 days          | 7.20 hours        | 1.68 hours         |
| 99.9% (three nines)      | 8.77 hours         | 43.8 minutes      | 10.1 minutes       |
| 99.99% (four nines)      | 52.6 minutes       | 4.32 minutes      | 1.01 minutes       |
| 99.999% (five nines)     | 5.25 minutes       | 25.9 seconds      | 6.05 seconds       |
| 99.9999% (six nines)     | 31.56 seconds      | 2.59 seconds      | 604.8 milliseconds |
| 99.99999% (seven nines)  | 3.15 seconds       | 263 milliseconds  | 60.5 milliseconds  |
| 99.999999% (eight nines) | 315.6 milliseconds | 26.3 milliseconds | 6 milliseconds     |
| 99.9999999% (nine nines) | 31.6 milliseconds  | 2.6 milliseconds  | 0.6 milliseconds   |


## Availability in Sequence vs Parallel
### 1. **Sequence Availability Formula**

When components are in sequence (dependent), the overall system availability decreases. The total availability is the product of the individual availabilities.

#### **Formula**:
\[
\text{Total Availability (Sequential)} = \text{Availability of Component A} \times \text{Availability of Component B} \times \dots \times \text{Availability of Component N}
\]

#### **Example**:
- If **Component A** has 99.9% availability and **Component B** has 99.9% availability, the total availability of the system is:
  \[
  \text{Total Availability} = 99.9\% \times 99.9\% = 99.8\%
  \]
  This means the system will be operational 99.8% of the time.

---

### 2. **Parallel Availability Formula**

When components are in parallel (redundant), the total availability increases. Even if one component fails, the other can still work.

#### **Formula**:
\[
\text{Total Availability (Parallel)} = 1 - (1 - \text{Availability of Component A}) \times (1 - \text{Availability of Component B}) \times \dots \times (1 - \text{Availability of Component N})
\]

#### **Example**:
- If **Component A** and **Component B** each have 99.9% availability and are arranged in parallel, the total availability is:
  \[
  \text{Total Availability} = 1 - (1 - 0.999) \times (1 - 0.999) = 99.9999\%
  \]
  This means the system is almost always available due to redundancy.

---

These formulas help calculate how different system setups impact overall availability. Systems in sequence are prone to lower availability, while systems in parallel provide higher reliability through redundancy.
### 5. **Availability vs Reliability**
No formula but we can express  relationship as
\[
\text{Reliability} = \text{Mean Time Between Failures (MTBF)}
\]
\[
\text{Availability} = \frac{\text{MTBF}}{\text{MTBF} + \text{Mean Time To Repair (MTTR)}}
\]

In other words, availability depends on both how often a system fails (**MTBF**) and how quickly it can be repaired (**MTTR**).

**Definition**:  
- **Availability** is about how often the system is operational.
- **Reliability** is about how long the system can run without failure.

**Use**:  
- A system can be available (i.e., online) but still unreliable if it fails frequently and needs constant fixing.

**Example**:  
- A website might have **99.9% availability** (it's online most of the time), but it could **crash every day for a few minutes**, meaning it's unreliable.


### 6. **High Availability vs Fault Tolerance**

**Definition**:  
- **High Availability**: Achieves minimal downtime using redundancy and quick recovery but allows short interruptions.
  
  \[
  \text{Availability (HA)} = \frac{\text{Uptime}}{\text{Total Time}}
  \]


- **Fault Tolerance**: Avoids Zero downtime entirely by running redundant systems in parallel, ensuring **continuous operation** even when one fails.

**Use**:  
- **High availability** is used when **minimal interruptions** are acceptable.
- **Fault tolerance** is used when **no interruptions** are acceptable but at a higher cost.

**Example**:  
- A **highly available system** might have two servers—if one fails, the other takes over, but there might be a brief delay in switching.
- A **fault-tolerant system** has both servers running simultaneously, so if one fails, the other continues **without any delay**.


  Formula follows the **Parallel Availability** calculation:

  \[
  \text{Fault Tolerant Availability} = 1 - \left(1 - \text{Availability of System A}\right) \times \left(1 - \text{Availability of System B}\right)
  \]
 

# Scalability

Scalability refers to a system's ability to handle increasing or decreasing workloads by adding or removing resources to meet demands.

![scalability](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/scalability/scalability.png)

There are two main types of scaling:

## Vertical scaling

- **Definition**: Increasing the power of an existing machine (e.g., adding more CPU, memory, or storage).

In other words, vertical scaling refers to improving an application's capability via increasing hardware capacity.

- **Advantages**:
  - Simple to implement.
  - Easier to manage.
  - Ensures data consistency.
- **Disadvantages**:
  - Risk of high downtime during upgrades.
  - Can become a single point of failure.
  - Harder to scale beyond hardware limits.

#### **Example**: 
Upgrading a server from 8 GB RAM to 32 GB RAM.


## Horizontal scaling

- **Definition**: Adding more machines to distribute the load, improving performance by adding more instances.
- **Advantages**:
  - Better fault tolerance and redundancy.
  - Flexible and easier to upgrade.
  - No single point of failure.
- **Disadvantages**:
  - Increased complexity in managing multiple systems.
  - Potential data consistency issues.
  - Load balancing between instances can create additional complexity.

#### **Example**: 
Adding more servers to a web service cluster to handle higher traffic.

# Storage Systems

Storage is essential in system design for managing how data is stored and accessed. Here are the most common storage concepts:

### 1. **RAID (Redundant Array of Independent Disks)**

RAID is a method of storing the same data on multiple drives(HDD or SSD) for redundancy and performance improvements.

- **RAID 0 (Striping)**: Splits data across multiple disks for improved speed but no redundancy.
- **RAID 1 (Mirroring)**: Copies data across multiple disks for redundancy.
- **RAID 5 (Striping with Parity)**: Combines striping with parity data for fault tolerance.
- **RAID 6 (Double Parity)**: Like RAID 5 but with two parity blocks, can handle two drive failures.
- **RAID 10 (Striping + Mirroring)**: Combines RAID 0 and RAID 1 for speed and redundancy.


### Comparison

Let's compare all the features of different RAID levels:

| Features             | RAID 0   | RAID 1               | RAID 5               | RAID 6                      | RAID 10                                  |
| -------------------- | -------- | -------------------- | -------------------- | --------------------------- | ---------------------------------------- |
| Description          | Striping | Mirroring            | Striping with Parity | Striping with double parity | Striping and Mirroring                   |
| Minimum Disks        | 2        | 2                    | 3                    | 4                           | 4                                        |
| Read Performance     | High     | High                 | High                 | High                        | High                                     |
| Write Performance    | High     | Medium               | High                 | High                        | Medium                                   |
| Cost                 | Low      | High                 | Low                  | Low                         | High                                     |
| Fault Tolerance      | None     | Single-drive failure | Single-drive failure | Two-drive failure           | Up to one disk failure in each sub-array |
| Capacity Utilization | 100%     | 50%                  | 67%-94%              | 50%-80%                     | 50%                                      |

### **Volumes**

**Description**: 
A volume is a logical unit of storage that can span multiple physical disks or be contained within a single disk. Volumes help in managing disk space and organizing data in a more flexible manner. They can be used to allocate specific amounts of storage to different applications or users.

**Details**:
- **Single Disk Volume**: A volume can be a partition on a single disk, providing a section of the disk for a specific purpose.
- **Spanning Volumes**: A volume can span multiple disks, combining their storage capacity into one logical unit.
- **Management**: Volumes can be formatted with different file systems and managed separately from physical disks.

---

### **File Storage**

**Description**:
File storage organizes data in a hierarchical directory structure, similar to traditional file systems used in operating systems. It stores files with metadata and directories, allowing users to navigate through folders to find specific files.

**Details**:
- **Structure**: Files are stored in directories and subdirectories, making it easy to organize and access data.
- **Path Requirement**: To locate a file, the complete path from the root directory to the file must be specified.
- **Usage**: Commonly used in scenarios where file access and organization are critical, such as personal data storage and network file sharing.

**Examples**:
- [Amazon EFS](https://aws.amazon.com/efs): Provides scalable file storage for use with Amazon EC2 instances.
- [Azure Files](https://azure.microsoft.com/en-in/services/storage/files): Offers file shares in the cloud accessible via the SMB protocol.
- [Google Cloud Filestore](https://cloud.google.com/filestore): A managed file storage service for applications requiring a file system interface.

---

### **Block Storage**

**Description**:
Block storage splits data into fixed-size blocks and stores each block separately with a unique identifier. It provides low-level storage where data can be read or written in blocks, which can be efficiently managed and retrieved.

**Details**:
- **Performance**: Offers high performance with low latency, ideal for applications requiring fast read and write operations.
- **Flexibility**: Blocks can be distributed across multiple storage devices, allowing for better scalability and redundancy.
- **Usage**: Commonly used for databases and applications requiring direct, high-speed access to storage.

**Example**:
- [Amazon EBS](https://aws.amazon.com/ebs): Provides persistent block storage for Amazon EC2 instances, allowing you to attach volumes to instances and manage them independently.

---

### **Object Storage**

**Description**:
Object storage manages data as discrete objects within a flat namespace. Each object includes data, metadata, and a unique identifier, and objects are stored in a repository that can be spread across multiple networked systems.

**Details**:
- **Scalability**: Easily scalable to handle large amounts of unstructured data, such as multimedia files or backups.
- **Data Management**: Objects are stored with metadata, allowing for rich tagging and retrieval capabilities.
- **Durability**: Often includes built-in redundancy and replication across multiple locations.

**Examples**:
- [Amazon S3](https://aws.amazon.com/s3): Provides scalable object storage with a simple web services interface for storing and retrieving any amount of data.
- [Azure Blob Storage](https://azure.microsoft.com/en-in/services/storage/blobs): Offers object storage for unstructured data with access via HTTP/HTTPS.
- [Google Cloud Storage](https://cloud.google.com/storage): Provides secure and durable object storage with a variety of access options.

---

### **NAS (Network Attached Storage)**

**Description**:
NAS is a storage device connected to a network, providing centralized access to data for multiple users. It enables users to store and retrieve files from a central location over the network.

**Details**:
- **Scalability**: Can be expanded by adding more storage devices or increasing capacity.
- **Accessibility**: Accessible from various devices on the network, providing a shared storage solution.
- **Control**: Offers on-site storage with the flexibility and control similar to public cloud services but managed locally.

---

### **HDFS (Hadoop Distributed File System)**

**Description**:
HDFS is a distributed file system designed for storing and managing large datasets across clusters of commodity hardware. It is optimized for high throughput and fault tolerance.

**Details**:
- **Data Distribution**: Stores files in large blocks (typically 128 MB or 256 MB), which are replicated across multiple nodes for fault tolerance.
- **Fault Tolerance**: Provides high availability by replicating data blocks across different nodes, allowing recovery in case of node failures.
- **Scalability**: Designed to scale out by adding more nodes to the cluster, making it suitable for handling massive amounts of data.

---

# Databases and DBMS
### **What is a Database?**

**Description**: 
A database is a systematically organized collection of structured data or information stored electronically. It is managed by a Database Management System (DBMS), which allows for data storage, retrieval, and manipulation.

**Details**:
- **Organization**: Data is stored in a structured format, typically using tables, rows, and columns.
- **Database System**: Consists of the database, the DBMS, and any associated applications that interact with the data.

---

### **What is DBMS?**

**Description**: 
A Database Management System (DBMS) is software that provides an interface between the user and the database, facilitating data management, storage, and retrieval.

**Details**:
- **Functions**: Enables users to perform operations such as querying, updating, and managing the data.
- **Administrative Tasks**: Handles tasks like performance optimization, data security, backup, and recovery.

---

### **Components**

#### **Schema**

**Description**: 
A schema defines the structure and organization of data within a database, specifying how data is categorized and related.

**Details**:
- **Structure Definition**: Includes definitions of tables, columns, data types, and relationships between tables.
- **Enforcement**: Can be strictly or loosely enforced depending on the database system and design.

#### **Table**

**Description**: 
A table is a collection of related data entries organized in rows and columns, similar to a spreadsheet.

**Details**:
- **Structure**: Each table consists of multiple columns, with each column storing a specific type of data.
- **Purpose**: Organizes data into a manageable format, making it easy to query and manipulate.

#### **Column**

**Description**: 
A column represents a single field in a table, holding data of a specific type for each row.

**Details**:
- **Data Types**: Columns can store various types of data, such as text, numbers, dates, or enumerated values.
- **Function**: Defines the attributes of the data stored in the table.

#### **Row**

**Description**: 
A row represents a single record in a table, with each row containing data for all columns in that table.

**Details**:
- **Data Entry**: Each row is an individual entry or record, with fields populated according to the table's columns.
- **Quantity**: Tables can contain numerous rows, depending on the amount of data.

## Types
![database-types](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/databases-and-dbms/database-types.png)

Below are different types of databases:

  - SQL
  - NoSQL
  - Document
  - Key-value
  - Graph
  - Timeseries
  - Wide column
  - Multi-model
 

## Challenges

Some common challenges faced while running databases at scale:

- **Data Volume**: Managing vast amounts of data from various sources(connected machines) and other sources.
- **Ensuring data security**: Ensuring access and protection from breaches.
- **Real-Time Demand**: Companies need fast access to data for quick decision-making.
- **Management costs**: Complexity requires more talent and resources.
- **Scalability**:As company grows data management must grow along with it.
- **Data Residency & Latency**: Some Organisations use cases demand on-premise optimized database systems.

# SQL databases

SQL databases are structured collections of data organized into tables with predefined relationships, using rows and columns. Each row can have a primary key to uniquely identify it, and tables can relate using foreign keys. SQL databases follow the [ACID consistency model](https://karanpratapsingh.com/courses/system-design/acid-and-base-consistency-models#acid).

### Materialized views

A materialized view stores precomputed query results for faster access. It enhances query speed, especially for frequently used complex queries, and reduces network load.

### N+1 query problem

The **N+1 query problem** occurs when an application makes an additional SQL query for each individual record, even though the required data could have been fetched in a single, more optimized query. This results in **N additional queries** after the initial query, leading to performance issues, especially when N is large.

### Example:

- A primary query fetches a list of users.
- Then, for each user, a separate query is made to fetch associated details (e.g., profile data).

Instead of running **N+1 queries**, this problem can be solved by:
- **Optimizing queries**: Using joins or more efficient queries to fetch all related data at once.
- **Batch loaders**: Tools like **GraphQL dataloaders** batch similar requests, reducing query count to one.

It's a common issue in **GraphQL** and **ORM** frameworks.
## Advantages of Relational Databases

- **Simple and accurate**: Relational databases are straightforward and ensure data accuracy through well-defined schemas and relationships.
- **Accessibility**: SQL allows for easy querying and accessing data in a structured manner.
- **Data consistency**: They follow ACID properties, ensuring consistent and reliable transactions.
- **Flexibility**: Relationships between data entities can be easily maintained and queried.

## Disadvantages of Relational Databases

- **Expensive to maintain**: Relational databases often require significant resources and expertise to manage.
- **Difficult schema evolution**: Changing the schema can be complex, especially for large systems.
- **Performance hits**: Complex joins and denormalization can affect performance.
- **Scaling limitations**: Horizontal scalability can be challenging due to tight schema constraints.

## Examples of Relational Databases

- **[PostgreSQL](https://www.postgresql.org)**
- **[MySQL](https://www.mysql.com)**
- **[MariaDB](https://mariadb.org)**
- **[Amazon Aurora](https://aws.amazon.com/rds/aurora)**
## NoSQL Databases

NoSQL databases refer to a broad range of non-relational databases that don't use SQL as the primary query language. Unlike relational databases, NoSQL databases allow flexible schemas and are optimized for horizontal scalability. They follow the [BASE consistency model](https://karanpratapsingh.com/courses/system-design/acid-and-base-consistency-models#base), providing more availability and flexibility at the expense of strong consistency.

### Types of NoSQL Databases

#### Document Databases
Document databases store data in JSON-like documents, allowing for semi-structured or unstructured data. They are general-purpose databases used for various transactional and analytical applications.

**Advantages:**
- Intuitive(easily) and flexible for developers.
- Easily scalable horizontally.
- Schemaless, meaning no need for pre-defined schemas.

**Disadvantages:**
- Lack of strict schema may lead to data inconsistency.
- Non-relational, so complex relationships are harder to manage.

**Examples:**
- [MongoDB](https://www.mongodb.com)
- [Amazon DocumentDB](https://aws.amazon.com/documentdb)
- [CouchDB](https://couchdb.apache.org)
### Key-Value Databases

Key-value databases are one of the simplest forms of NoSQL databases, storing data as key-value pairs. These pairs consist of a unique key and its associated value, making them extremely efficient for fast lookups. Key-value databases are often used for caching and session management due to their simplicity and high performance.

**Advantages:**
- Simple and highly performant for fast lookups.
- Horizontally scalable, making them suitable for handling high traffic.
- Ideal for session management and caching.
- Optimized for rapid read and write operations.

**Disadvantages:**
- Limited to basic CRUD operations (Create, Read, Update, Delete).
- Values cannot be filtered or queried without knowing the key.
- Lacks advanced indexing and scanning capabilities.
- Not designed for complex queries or relational data.

**Examples:**
- [Redis](https://redis.io)
- [Memcached](https://memcached.org)
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb)
- [Aerospike](https://aerospike.com)

### Graph Databases

Graph databases are a type of NoSQL database that use graph structures with nodes, edges, and properties to represent and store data. Instead of relying on tables or documents, graph databases model relationships between data entities as edges, making them ideal for applications where connections between data points are crucial.

**Advantages:**
- High query speed for relationship-based queries.
- Agile and flexible, allowing for quick updates and changes.
- Provides explicit representation of data relationships, making it easier to model real-world networks.

**Disadvantages:**
- Can be complex to design and manage.
- Lacks a universally standardized query language, although **Cypher** is widely used in some graph databases like Neo4j.

**Use Cases:**
- Fraud detection (by analyzing relationships between entities).
- Recommendation engines (such as suggesting products or connections based on user behavior).
- Social networks (modeling user connections and interactions).
- Network mapping (for understanding and analyzing infrastructure or organizational networks).

**Examples:**
- [Neo4j](https://neo4j.com)
- [ArangoDB](https://www.arangodb.com)
- [Amazon Neptune](https://aws.amazon.com/neptune)
- [JanusGraph](https://janusgraph.org)
### Time Series Databases

A time-series database is designed and optimized specifically for storing and querying data that is timestamped or time-series in nature. These databases handle continuous flows of data, such as sensor readings or application performance metrics.

**Advantages:**
- Fast insertion and retrieval of time-series data.
- Efficient storage for handling large amounts of time-stamped data.

**Use Cases:**
- IoT data collection.
- Metrics analysis (e.g., performance monitoring).
- Application monitoring and alerting.
- Understanding financial market trends.

**Examples:**
- [InfluxDB](https://www.influxdata.com)
- [Apache Druid](https://druid.apache.org)

---

### Wide Column Databases

Wide column databases store data in column families rather than traditional rows and columns, offering high flexibility and scalability. They are schema-agnostic and well-suited for handling massive datasets.

**Advantages:**
- Highly scalable, capable of managing petabytes of data.
- Ideal for real-time big data applications.

**Disadvantages:**
- Expensive infrastructure and maintenance.
- Slower write operations due to complex indexing.

**Use Cases:**
- Business analytics with large datasets.
- Storing attribute-based data for rapid querying.

**Examples:**
- [BigTable](https://cloud.google.com/bigtable)
- [Apache Cassandra](https://cassandra.apache.org)
- [ScyllaDB](https://www.scylladb.com)

---

### Multi-Model Databases

Multi-model databases support various data models like relational, key-value, document, and graph in one unified system, allowing flexibility for different data types and queries within the same backend.

**Advantages:**
- Flexible and able to accommodate diverse data types.
- Suitable for complex projects requiring multiple models.
- Consistent data handling across models.

**Disadvantages:**
- Can be complex to manage and develop.
- Less mature compared to specialized databases.

**Examples:**
- [ArangoDB](https://www.arangodb.com)
- [Azure Cosmos DB](https://azure.microsoft.com/en-in/services/cosmos-db)
- [Couchbase](https://www.couchbase.com)


### SQL vs NoSQL Databases

**SQL (Relational) Databases** and **NoSQL (Non-Relational) Databases** serve to different needs based on their design and functionalities.

#### High-Level Differences

**1. Storage**
- **SQL:** Data is stored in structured tables with rows and columns. Each row represents a record, and each column represents an attribute of the record.
- **NoSQL:** Uses various models for storage including key-value pairs, documents, graphs, and wide columns.

**2. Schema**
- **SQL:** Requires a predefined schema. Each record must adhere to the schema, and any changes require migration scripts.
- **NoSQL:** Features dynamic schemas. Records can have varying fields, and schemas can evolve without major restructuring.

**3. Querying**
- **SQL:** Utilizes SQL for powerful querying and manipulation of data, providing complex joins and aggregations.
- **NoSQL:** Query syntax varies by database type (e.g., document-based, key-based), often focused on collections or graphs rather than complex queries.

**4. Scalability**
- **SQL:** Typically scales vertically, which can be costly and complex. Horizontal scaling is possible but challenging.
- **NoSQL:** Designed for horizontal scaling, making it easier to distribute data across multiple servers, which can be more cost-effective and efficient.

**5. Reliability**
- **SQL:** Generally ACID (Atomicity, Consistency, Isolation, Durability) compliant, ensuring strong consistency and reliable transactions.
- **NoSQL:** Often prioritizes performance and scalability over strict ACID compliance, using eventual consistency models.

#### Choosing Between SQL and NoSQL

**For SQL:**
- Structured data with fixed schema requirements.
- Relational data needing complex joins.
- Transactions requiring strong consistency.
- Fast indexed lookups.

**For NoSQL:**
- Flexible or dynamic schema needs.
- Non-relational or varied data types.
- Workloads that do not require complex joins.
- High throughput and data-intensive applications.
- Cost-effective, scalable solutions for large volumes of data.

### Database Replication

Replication is a process that duplicates data across multiple databases to enhance reliability, fault tolerance, and accessibility.

#### Master-Slave Replication

**Overview:** In master-slave replication, the master node handles both read and write operations, while slave nodes handle read operations only. Slaves can also replicate from other slaves in a hierarchical manner. If the master fails, the system can operate in read-only mode until a new master is promoted.

![Master-Slave Replication](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/database-replication/master-slave-replication.png)

**Advantages:**
- Backups can be taken from slaves with minimal impact on the master.
- Read operations can be offloaded to slaves, reducing the load on the master.
- Slaves can be taken offline for maintenance without affecting the master.

**Disadvantages:**
- Increases hardware requirements and complexity.
- Potential downtime and data loss if the master fails.
- All writes must go through the master, potentially creating a bottleneck.
- Increased replication lag with more slaves.

#### Master-Master Replication

**Overview:** In master-master replication, both nodes handle read and write operations. They synchronize with each other, allowing continued operation even if one master fails.

![Master-Master Replication](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/database-replication/master-master-replication.png)

**Advantages:**
- Both nodes can handle read and write operations, distributing the load.
- Failover is quick and automatic.
- Provides higher availability and redundancy.

**Disadvantages:**
- More complex to configure and manage.
- May have issues with consistency or increased write latency due to synchronization.
- Conflict resolution needed as more write nodes are added.

#### Synchronous vs Asynchronous Replication

**Synchronous Replication:**
- **Description:** Data is written to both the primary and replica simultaneously, ensuring that both copies are always synchronized.
- **Advantages:** Strong consistency and immediate replication.
- **Disadvantages:** Can introduce latency and may impact performance due to the need for synchronous writes.

**Asynchronous Replication:**
- **Description:** Data is first written to the primary storage and then replicated to the replica at a later time. This is typically done on a scheduled basis.
- **Advantages:** More cost-effective and can handle larger volumes of data with less immediate impact.
- **Disadvantages:** Potential for replication lag, leading to temporary inconsistencies between primary and replica.


# Indexes

Indexes are used in databases to speed up data retrieval operations. They work like a table of contents, allowing quick access to rows in a table based on the indexed columns. While they enhance read performance, they introduce overhead in terms of storage and slower write operations.

when we create an index on a column of a table, we store that column and a pointer to the whole row in the index.

![indexes](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/indexes/indexes.png)

 
1. **Dense Index:**
   - **Description:** An index record is created for every row in the table.
   - **Advantages:**
     - Quick data retrieval using binary search.
     - No ordering requirements.
   - **Disadvantages:**
     - Requires more storage and maintenance.
     - Slower write operations due to index updates.

   ![Dense Index](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/indexes/dense-index.png)


2. **Sparse Index:**
   - **Description:** Index records are created only for some rows in the table.
   - **Advantages:**
     - Less storage and maintenance.
     - Faster write operations.
   - **Disadvantages:**
     - Slower data retrieval due to potential need for additional scans.
     - Optional for ordered data.

   ![Sparse Index](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/indexes/sparse-index.png)

# Normalization and Denormalization
**Normalization:** The process of organizing data to reduce redundancy and improve data integrity. It involves dividing a database into two or more tables and defining relationships between them.

**Denormalization:** The process of combining tables to improve read performance by reducing the complexity of queries, often at the cost of increased redundancy and write overhead.

## Terms
Commonly used terms in normalization and denormalization.

**Key Terms:**

- **Primary Key:** Uniquely identifies each row in a table.
- **Composite Key:** Primary key made up of multiple columns.
- **Super Key:** Set of all keys that can uniquely identify rows.
- **Candidate Key:** Attributes that uniquely identify rows in a table.
- **Foreign Key:** References the primary key of another table.
- **Alternate Key:** Keys that are not primary keys.
- **Surrogate Key:** System-generated unique identifier.

**Dependencies:**

- **Partial Dependency:** Occurs when a primary key determines other attributes.
- **Functional Dependency:** Relationship between two attributes, often between a primary key and a non-key attribute.
- **Transitive Functional Dependency:** When a non-key attribute determines another attribute.


### Anomalies

Database anomalies are issues that arise due to flaws in the database design or incorrect planning. Normalization is typically used to address these anomalies by organizing data and reducing redundancy.

**Types of Database Anomalies:**

- **Insertion Anomaly:** Difficulty in inserting data without additional attributes. For example, if a new employee "John" is hired but not assigned a team, inserting their record might be problematic.

- **Update Anomaly:** Issues with maintaining data consistency when updating records. For instance, if an employee "Hailey" is promoted, you may need to update multiple rows to reflect this change.

- **Deletion Anomaly:** When removing data requires the deletion of other related information. For example, deleting "Team B" would necessitate removing associated employee records.


**Example Table (Unnormalized):**

| ID  | Name   | Role              | Team |
| --- | ------ | ----------------- | ---- |
| 1   | Peter  | Software Engineer | A    |
| 2   | Brian  | DevOps Engineer   | B    |
| 3   | Hailey | Product Manager   | C    |
| 4   | Hailey | Product Manager   | C    |
| 5   | Steve  | Frontend Engineer | D    |


## Normalization

Normalization organizes data to eliminate redundancy and ensure data consistency. It involves creating tables and defining relationships to minimize anomalies.

**Why Normalize?**

- **Eliminates Redundancy:** Reduces duplication of data.
- **Ensures Consistency:** Prevents inconsistent data entries.
- **Flexible Structure:** Allows easy extension of the database schema.

**Normal Forms:**

1. **1NF (First Normal Form):**
   - No repeating groups or arrays.
   - Each set of related data must be unique.
   - Each column must contain atomic values(Same Data type).
   - Set of related data should have a separate table.

2. **2NF (Second Normal Form):**
   - Satisfies 1NF.
   - No partial dependencies (all non-key attributes must depend on the whole primary key).

3. **3NF (Third Normal Form):**
   - Satisfies 2NF.
   - No transitive dependencies (non-key attributes must not depend on other non-key attributes).

4. **BCNF (Boyce-Codd Normal Form):**
   - Satisfies 3NF.
   - Every determinant must be a candidate key.
   - it is also known as the 3.5 normal form (3.5NF).


**Advantages of Normalization:**

- **Reduces Data Redundancy:** Minimizes duplication.
- **Increases Data Consistency:** Ensures accurate data.
- **Enforces Referential Integrity:** Maintains valid relationships.

**Disadvantages of Normalization:**

- **Complex Design:** Increases design complexity.
- **Slower Performance:** May require additional joins.
- **Maintenance Overhead:** Can be harder to maintain.
Your summary of denormalization looks great! Here’s a bit more detail on each aspect for clarity:

### Denormalization

Denormalization involves restructuring a database by adding redundant data or creating additional tables to improve read performance. This technique balances the complexity of the schema with the performance needs of the database.

#### 1. **Adding Redundant Data to Existing Tables:**
   - **Example:**
     - **Before Denormalization:**
       - **Orders Table:** Stores order details with a foreign key to the `CustomerID`.
       - **Customers Table:** Stores customer details.
     - **After Denormalization:**
       - **Orders Table:** Includes customer details like `CustomerName` and `Address` directly in the table. This eliminates the need to join the `Customers` table when retrieving order information.

#### 2. **Creating Additional Tables for Aggregated Data:**
   - **Example:**
     - **Before Denormalization:**
       - **Sales Table:** Contains individual sales records.
     - **After Denormalization:**
       - **MonthlySalesSummary Table:** Precomputes and stores total sales for each month, reducing the need to calculate totals on the fly for every report query.

#### 3. **Duplicating Data Across Tables:**
   - **Example:**
     - **Before Denormalization:**
       - **Employees Table:** Contains employee details with a foreign key to the `DepartmentID`.
       - **Departments Table:** Contains department details.
     - **After Denormalization:**
       - **Employees Table:** Includes department-related information (like `DepartmentName` and `ManagerID`) directly in the `Employees` table to avoid joins when querying employee information.

### Advantages of Denormalization:
- **Faster Data Retrieval:** Reduces the need for complex joins, speeding up queries.
- **Simpler Queries:** Easier to write and maintain, as the data is readily available in fewer tables.
- **Fewer Tables:** Simplifies the database schema by reducing the number of tables needed.

### Disadvantages of Denormalization:
- **Expensive Writes:** Inserting or updating data can be more costly due to the need to maintain redundant information.
- **Complex Design:** Managing a denormalized schema can be more complex due to the added redundancy.
- **Data Redundancy:** Requires additional storage space to maintain redundant data.
- **Consistency Issues:** Increases the risk of data inconsistency as redundant data may become outdated or mismatched.

Denormalization is a trade-off between performance and complexity. It aims to optimize read operations at the cost of potential write performance and complexity in managing redundant data.
Your summary of the ACID and BASE consistency models is well-organized and informative. Here’s a slightly expanded version with more detail on each concept:

### ACID Consistency Model

**ACID** stands for Atomicity, Consistency, Isolation, and Durability. These properties are fundamental to ensuring reliable and predictable transaction processing in relational databases.

- **Atomicity:** 
  - **Definition:** Ensures that all operations in a transaction are completed successfully. If any operation fails, the entire transaction is rolled back, leaving the database in its previous state.
  - **Example:** If a bank transfer involves debiting one account and crediting another, atomicity ensures that both operations are completed, or neither is. If one fails, the entire transfer is rolled back.

- **Consistency:**
  - **Definition:** Ensures that a transaction brings the database from one valid state to another, maintaining all predefined rules and constraints (e.g., foreign keys, unique constraints).
  - **Example:** A database with a constraint that all employees must belong to a valid department ensures that adding or updating employee records maintains this constraint.

- **Isolation:**
  - **Definition:** Ensures that transactions are executed independently of each other, meaning the operations of one transaction do not interfere with those of another. This is managed through various isolation levels (e.g., Read Committed, Serializable).
  - **Example:** Two users simultaneously updating the same bank account balance will not see intermediate states caused by each other's operations.

- **Durability:**
  - **Definition:** Once a transaction is committed, its changes are permanent, even in the event of a system crash or failure.
  - **Example:** After a successful payment transaction, the changes to account balances will be preserved and visible after a system restart.

### BASE Consistency Model

**BASE** stands for Basic Availability, Soft-state, and Eventual consistency. BASE is often used in NoSQL databases where high availability and scalability are prioritized over strict consistency.

- **Basic Availability:**
  - **Definition:** The system appears to be operational most of the time, meaning it can handle requests even if some parts of the system are not functioning properly.
  - **Example:** A distributed database system might still respond to queries even if some nodes are down.

- **Soft-state:**
  - **Definition:** The system's state does not have to be immediately consistent across all nodes. Data may be temporarily inconsistent as updates propagate through the system.
  - **Example:** In a replicated database, updates to one replica might not be instantly reflected in others.

- **Eventual Consistency:**
  - **Definition:** The system guarantees that, given enough time, all updates will propagate and all nodes will eventually reflect the same data. However, immediate consistency is not guaranteed.
  - **Example:** An online shopping site may show outdated stock levels temporarily but will eventually reflect the correct levels once all replicas are updated.

### ACID vs BASE Trade-offs

- **ACID:**
  - **Advantages:** Ensures high data integrity and reliability, suitable for applications where consistency and accuracy are crucial (e.g., financial transactions).
  - **Disadvantages:** Can be complex to scale and may introduce latency due to strict consistency requirements.

- **BASE:**
  - **Advantages:** Offers high availability and scalability, suitable for applications where some inconsistency can be tolerated for better performance and fault tolerance (e.g., social media platforms).
  - **Disadvantages:** Requires careful design to handle eventual consistency and potential data anomalies.
 
## CAP Theorem

The CAP theorem, formulated by Eric Brewer, states that a distributed system can satisfy only two out of the following three characteristics:

1. **Consistency (C)**
2. **Availability (A)**
3. **Partition Tolerance (P)**

### Characteristics

1. **Consistency**
   - **Definition:** Every read request receives the most recent write, ensuring all clients see the same data at the same time.
   - **Effects or Consequence:** Updates to the data are immediately reflected across all nodes in the system.

2. **Availability**
   - **Definition:** Every request receives a response, whether it’s the most recent data or not, even if some nodes are down.
   - **Effects or Consequence::** The system remains operational and responsive to requests, regardless of node failures.

3. **Partition Tolerance**
   - **Definition:** The system continues to operate despite network partitions or message loss.
   - **Effects or Consequence::** The system can handle and recover from network failures or splits without going offline.

### Trade-offs

Because it's impossible to achieve all three characteristics simultaneously, distributed systems must make trade-offs. Here’s how different systems balance these properties:

1. **CA Database (Consistency + Availability)**
   - **Characteristics:** Provides consistency and availability but fails to handle network partitions.
   - **Behavior:** In case of a network partition, the system might become unavailable.
   - **Examples:** PostgreSQL, MariaDB.
   - **Use Case:** Suitable for scenarios where network partitions are rare and consistency and availability are critical.

2. **CP Database (Consistency + Partition Tolerance)**
   - **Characteristics:** Provides consistency and partition tolerance but might sacrifice availability.
   - **Behavior:** During a network partition, the system may reject requests or become unavailable until the partition is resolved.
   - **Examples:** MongoDB, Apache HBase.
   - **Use Case:** Ideal for applications requiring strong consistency and fault tolerance but can tolerate reduced availability during network issues.

3. **AP Database (Availability + Partition Tolerance)**
   - **Characteristics:** Provides availability and partition tolerance but may sacrifice consistency.
   - **Behavior:** Nodes remain operational and respond to requests even if they might not reflect the most recent write during a partition. The system will eventually reconcile inconsistencies.
   - **Examples:** Apache Cassandra, CouchDB.
   - **Use Case:** Suitable for scenarios where the system must remain operational and accessible even during network partitions, with eventual consistency.

### Summary

- **CA Systems:** Ensure consistency and availability but not partition tolerance.
- **CP Systems:** Ensure consistency and partition tolerance but may sacrifice availability.
- **AP Systems:** Ensure availability and partition tolerance but may sacrifice consistency.




## PACELC Theorem

The **PACELC theorem** extends the **CAP theorem** by considering an additional factor: **Latency (L)**. Here’s a breakdown of what the PACELC theorem entails:

**PACELC** stands for **Partition Tolerance (P), Availability (A), Consistency (C), Else (E), Latency (L), Consistency (C)**. 

### Explanation

- **P (Partition Tolerance):** In the case of network partitions, a distributed system must choose between consistency and availability.
  - **Availability (A):** The system remains operational and responsive to requests even during partitions.
  - **Consistency (C):** All nodes reflect the same data and all clients see the most recent write.

- **Else (E):** When there are no network partitions (i.e., the system is operating normally), the system must choose between latency and consistency.
  - **Latency (L):** The time it takes for a request to be processed and a response to be received.
  - **Consistency (C):** Ensuring that all nodes reflect the most recent write.

### Implications

1. **When Partitioned (P):**
   - The system must decide between:
     - **Availability (A):** The system will respond to all requests even if some nodes might have outdated data.
     - **Consistency (C):** Ensuring that all nodes have the same data, but some requests might be delayed or not processed until consistency is achieved.

2. **When Not Partitioned (E):**
   - The system must decide between:
     - **Latency (L):** How quickly requests are processed, which might involve trade-offs in ensuring that all nodes have the latest data.
     - **Consistency (C):** Ensuring that data is consistent across all nodes might increase the time it takes to process requests.

### Summary

- **PACELC Theorem** adds a layer to the CAP theorem by addressing performance considerations beyond just dealing with network partitions.
- **When partitions occur:** Focus on the trade-off between consistency and availability.
- **When partitions do not occur:** Focus on the trade-off between consistency and latency.


# Transactions

A **transaction** is a sequence of database operations treated as a _"single unit of work"_. The key idea is that all operations within a transaction either complete successfully together or have no effect at all. This ensures data integrity and consistency, especially in cases of failure or errors.


_Usually, relational databases support ACID transactions, and non-relational databases don't (there are exceptions)._

### Key Properties of Transactions

- **Atomicity:** All operations in a transaction are treated as a single unit. If any operation fails, the entire transaction fails and the database is rolled back to its previous state.
- **Consistency:** Transactions bring the database from one valid state to another, maintaining database invariants.
- **Isolation:** Transactions operate independently of one another. Changes made by one transaction are not visible to others until the transaction is committed.
- **Durability:** Once a transaction is committed, its changes are permanent, even in the event of a system crash.

**Visual Representation:**

![Transaction States](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/transactions/transaction-states.png)


## Transaction States

A transaction can be in one of the following states:

### Active

- **Definition:** The transaction is currently being executed.
- **Characteristics:** It is in its initial state, and operations are being processed.

### Partially Committed

- **Definition:** The transaction has executed its final operation but has not yet been fully committed.
- **Characteristics:** The transaction is in the process of being committed, but not all operations have been finalized.

### Committed

- **Definition:** The transaction has successfully completed all operations.
- **Characteristics:** All changes made during the transaction are now permanently stored in the database.

### Failed

- **Definition:** The transaction has encountered an error or failure that prevents it from continuing.
- **Characteristics:** The transaction cannot proceed further, and recovery actions need to be taken.

### Aborted

- **Definition:** The transaction has failed and has been rolled back to its initial state.
- **Characteristics:** All changes made during the transaction are undone, and the database is restored to its state before the transaction began.
- **Recovery Options:** 
  - **Restart the Transaction:** Attempt to execute the transaction again from the beginning.
  - **Kill the Transaction:** Discard the transaction permanently without retrying.

### Terminated

- **Definition:** The transaction has completed successfully or has been aborted, and it is now considered finished.
- **Characteristics:** The system is ready for new transactions, and the current transaction is no longer active.


# Distributed Transactions

A **distributed transaction** involves multiple databases or nodes across a network. It ensures that operations spanning different databases are executed in a manner that maintains consistency and integrity, similar to single-database ACID transactions. All participating databases must either commit or roll back the changes as a unified operation to preserve data integrity.

## Why do we need distributed transactions?

Unlike an ACID transaction on a single database, a distributed transaction involves altering data on multiple databases

Distributed transactions are necessary because operations may affect data stored across multiple databases. Coordinating these operations to ensure all-or-nothing execution is complex, and failure to do so could lead to data inconsistency. Therefore, a distributed transaction ensures that all nodes either complete the transaction or none of them do, maintaining a consistent state.

### Popular Solutions for Distributed Transactions

#### Two-Phase Commit (2PC)

The **Two-Phase Commit (2PC)** protocol is a distributed algorithm designed to ensure that all participating nodes in a distributed transaction agree on whether to commit or abort the transaction. It involves two main phases:

![Two-Phase Commit](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/distributed-transactions/two-phase-commit.png)

**Phases:**

1. **Prepare Phase:**
   - The coordinator node requests each participant node to prepare for the commit.
   - Each participant node responds with its readiness to commit. If all participants respond positively, the transaction proceeds to the next phase.

2. **Commit Phase:**
   - The coordinator instructs all participant nodes to commit the transaction.
   - If any participant node fails or the coordinator fails, the transaction is rolled back.

**Problems with 2PC:**

- **Node Crashes:** If a participant node crashes during the prepare phase, it may lead to an indefinite wait.
- **Coordinator Crashes:** If the coordinator crashes, the transaction could be left in an uncertain state.
- **Blocking Issues:** The protocol can block if nodes fail or if there are communication issues.

#### Three-Phase Commit (3PC)

The **Three-Phase Commit (3PC)** protocol extends 2PC by adding an additional phase to reduce blocking issues and improve resilience. It introduces a pre-commit phase to address some of the shortcomings of 2PC.

![Three-Phase Commit](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/distributed-transactions/three-phase-commit.png)

**Phases:**

1. **Prepare Phase:**
   - Similar to 2PC, the coordinator asks each participant node to prepare for committing the transaction.

2. **Pre-Commit Phase:**
   - The coordinator sends a pre-commit message to all participants.
   - Participants acknowledge receipt of the pre-commit message. If any participant fails to receive or acknowledge the pre-commit message, the transaction is aborted.

3. **Commit Phase:**
   - If all participants have acknowledged the pre-commit message, the coordinator sends a commit message to finalize the transaction.

**Advantages of 3PC:**

- **Reduces Blocking:** The pre-commit phase helps ensure that all participants are in agreement before the final commit phase, reducing the likelihood of indefinite blocking.
- **Improved Fault Tolerance:** The protocol is more resilient to failures compared to 2PC.

**Considerations:**

- **Complexity:** 3PC is more complex to implement than 2PC.
- **Coordination Overhead:** The additional phase introduces extra coordination overhead.

In summary, distributed transactions are essential for maintaining consistency and integrity in systems with multiple databases. The Two-Phase Commit protocol is a foundational method for coordinating such transactions, while the Three-Phase Commit protocol builds upon it to address some of its limitations and improve fault tolerance.


Here's an overview of the **Saga** pattern for managing distributed transactions:

## Sagas

A **saga** is a design pattern for managing distributed transactions in a way that maintains consistency across multiple services or databases without requiring a traditional distributed transaction protocol like Two-Phase Commit (2PC).

In a saga, a long-running process is divided into a series of smaller, local transactions. Each local transaction performs a part of the overall process and then triggers the next transaction through messages or events. If a local transaction fails, a set of compensating transactions is executed to roll back the changes made by previous transactions, ensuring that the system reaches a consistent state.

![Sagas](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/distributed-transactions/sagas.png)

### Coordination Approaches

1. **Choreography:**
   - Each local transaction publishes events or messages that other services listen to and react upon. The sequence of transactions is driven by these events.
   - **Example:** Service A completes its transaction and publishes an event that triggers Service B to perform its transaction.

2. **Orchestration:**
   - A central orchestrator (or coordinator) directs the sequence of local transactions. The orchestrator tells each service what transaction to execute and in what order.
   - **Example:** The orchestrator sends commands to Service A, Service B, and Service C, directing each to perform its respective transactions in a specific order.

### Problems with Sagas

1. **Debugging Complexity:**
   - Debugging a saga can be challenging because of the multiple local transactions and potential compensating transactions involved. Tracking the flow and identifying failures requires comprehensive logging and monitoring.

2. **Cyclic Dependencies:**
   - There's a risk of cyclic dependencies between saga participants, where transactions in one saga might trigger transactions in another saga, leading to complex interdependencies.

3. **Durability Challenges:**
   - Ensuring data durability can be difficult, especially if participant services have to handle failures and compensating transactions. There's also a risk of partial failures where some transactions succeed while others fail.

4. **Testing Difficulties:**
   - Testing sagas can be challenging because it requires all participating services to be operational and able to simulate various scenarios. This often necessitates complex integration testing setups.

### Summary

Sagas provide an alternative to traditional distributed transactions by breaking down a long-running transaction into manageable, localized transactions. They offer flexibility in managing distributed systems but come with their own set of challenges, such as debugging complexity and potential cyclic dependencies. Choosing between choreography and orchestration depends on the specific requirements and design of the system.

# Sharding

Before we discuss sharding, let's talk about data partitioning:

## Data Partitioning

**Data partitioning** is the technique of breaking a database into smaller, more manageable parts. This is done to improve the manageability, performance, and availability of the database. Partitioning can be implemented in several ways:


### Methods

There are many different ways one could use to decide how to break up an application database into multiple smaller DBs. Below are two of the most popular methods

1. **Horizontal Partitioning (or Sharding):**
   - **Description:** Splits table data horizontally based on ranges defined by a _partition key_. This approach is also known as **database sharding**.
   - **Goal:** Distributes rows of a table across multiple tables or databases, each containing a subset of the data.

2. **Vertical Partitioning:**
   - **Description:** Splits a table vertically based on columns. Each partition contains a subset of columns.
   - **Goal:** Divides tables into smaller tables with fewer columns to optimize performance for specific queries
  
In this tutorial, we will focus on **Sharding**.


## What is sharding?

**Sharding** is a horizontal partitioning strategy used to manage large databases by splitting them into smaller, more manageable pieces called **shards**. Each shard contains a subset of the data and has the same schema, but holds different data. This technique allows databases to handle larger volumes of data and increased load by distributing data across multiple servers.

![Sharding](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/sharding/sharding.png)

## Partitioning Criteria

1. **Hash-Based:**
   - **Description:** Uses a hashing algorithm to distribute rows 
   into partitions.
   - **Algorithm:** Rows are distributed across partitions based on a hash function applied to the partition key
   - **Advantages:** Provides even distribution of data.
   - **Disadvantages:** Rebalancing shards can be costly when adding or removing servers.

2. **List-Based:**
   - **Description:** Data is distributed based on predefined lists of values. Each partition is responsible for a specific list of values.
   - **Advantages:** Simple to implement and understand.
   - **Disadvantages:** Can lead to unbalanced data distribution if lists are not well-defined.

3. **Range-Based:**
   - **Description:** Data is divided based on ranges of values in the partition key. Each partition contains data within a specific range.
   - **Advantages:** Useful for range queries and sorted data.
   - **Disadvantages:** Data skew can occur if certain ranges are accessed more frequently.

4. **Composite:**
   - **Description:** Combines multiple partitioning strategies. For example, using range-based partitioning followed by hash-based partitioning within each range.
   - **Advantages:** Offers flexibility and can handle complex partitioning needs.
   - **Disadvantages:** More complex to manage and implement.

### Advantages of Sharding

- **Availability:** Sharding improves availability by isolating partitions. If one shard fails, others can still operate independently.
- **Scalability:** Distributes data across multiple servers, allowing horizontal scaling to handle increased load.
- **Security:** Sensitive and non-sensitive data can be stored in different shards, enhancing security and manageability.
- **Query Performance:** Queries are executed against smaller partitions, which can improve performance compared to querying a single, large database.
- **Data Manageability:** Simplifies management by breaking large tables into smaller, more manageable units.

### Disadvantages of Sharding

- **Complexity:** Sharding adds complexity to the system, including management, configuration, and operations.
- **Joins Across Shards:** Performing joins that span multiple shards can be inefficient and complex, as it requires data from different servers.
- **Rebalancing:** Uneven data distribution or load can necessitate rebalancing of shards, which can be complex and disruptive.

### When to Use Sharding

Consider sharding when:

- You need to scale horizontally and leverage existing hardware.
- Data needs to be distributed across different geographic regions.
- High performance is required with reduced load on individual servers.
- A large number of concurrent connections or transactions are anticipated.

Sharding is a powerful technique for managing large datasets and high-traffic databases but requires careful planning and management to address its complexities and challenges.

### Consistent Hashing: Problem and Solution

**Problem**:
In traditional hashing, adding or removing a node forces a remapping of many keys, causing inefficiencies in distributed systems. When the number of nodes (`N`) changes, keys mapped by `hash(key) % N` will be redistributed, impacting performance.

**Solution: Consistent Hashing**:
Consistent hashing provides a scalable solution by mapping nodes and keys onto a circular hash space (a ring). When nodes are added or removed, only a small fraction of the keys are redistributed, minimizing disruption.

### How Consistent Hashing Works:

- **Hash Ring**: Both keys (requests) and nodes are assigned positions on the hash ring using a hash function.
- When a request arrives, it is routed to the nearest node in a clockwise direction on the ring.
- This ensures that when nodes are added or removed, only the keys close to those nodes need to be redistributed, minimizing the reallocation.

### Virtual Nodes (VNodes):

- To distribute the load evenly and avoid hotspots, each physical node is assigned multiple positions on the ring, known as **virtual nodes**.
- This ensures better load distribution across nodes and faster rebalancing when changes occur.

By using consistent hashing and virtual nodes, distributed systems can scale efficiently while maintaining balanced load distribution.

Let's illustrate **consistent hashing** with formulas and a concrete example to explain how it works.

### Step 1: Setting up the Hash Ring
Assume we have 3 nodes: `Node_0`, `Node_1`, and `Node_2`. In consistent hashing, we map both **keys** (requests) and **nodes** to a position on a hash ring. Let's assume the hash function gives us a range from `0` to `m-1`, where `m = 360`. For simplicity, think of the ring as a clock with 360 degrees.

### Step 2: Hashing Nodes
Let's hash our nodes to positions on the ring using a hash function `H`:
- `H(Node_0) = 100`
- `H(Node_1) = 200`
- `H(Node_2) = 300`

These values represent positions on the ring:

```
      0
       |
 300 --+-- 100
       |
     200
```

### Step 3: Hashing Keys (Requests)
We now hash requests (keys) to the ring. Assume we have three requests `key_1`, `key_2`, and `key_3`, which get hashed as follows:
- `H(key_1) = 150`
- `H(key_2) = 250`
- `H(key_3) = 50`

### Step 4: Assigning Requests to Nodes
The consistent hashing algorithm assigns a key to the next **clockwise** node on the ring.

- **key_1 (150)** will be assigned to `Node_1 (200)` because 150 is between 100 and 200.
- **key_2 (250)** will be assigned to `Node_2 (300)` because 250 is between 200 and 300.
- **key_3 (50)** will be assigned to `Node_0 (100)` because 50 is between 300 (wrap around) and 100.

### Step 5: Adding/Removing Nodes
#### Case 1: Adding `Node_3`
Let’s add `Node_3` and assume it hashes to `H(Node_3) = 50`. After adding, the ring looks like this:

```
      0
       |
 300 --+-- 100
       |
     200
```

Now, the re-routing:
- `key_1 (150)` is still assigned to `Node_1 (200)`.
- **key_2 (250)** is still assigned to `Node_2 (300)`.
- **key_3 (50)** is now assigned to **`Node_3 (50)`** instead of `Node_0 (100)`.

Only **key_3** is remapped, while the others remain with their original nodes. This shows the minimal redistribution property of consistent hashing.

#### Case 2: Removing `Node_2`
If we remove `Node_2 (300)`, the ring becomes:

```
      0
       |
     --+-- 100
       |
     200
```

Now, the re-routing:
- `key_1 (150)` is still with `Node_1 (200)`.
- **key_2 (250)** is reassigned to `Node_0 (100)` (next clockwise after 250).

### Step 6: Virtual Nodes (VNodes)
To balance the load more evenly, we create **virtual nodes**. Each physical node is hashed to multiple positions on the ring, ensuring better distribution.

- `Node_0` can be hashed to `100`, `120`, and `140` (virtual positions).
- `Node_1` can be hashed to `200`, `220`, and `240`.
- `Node_2` can be hashed to `300`, `320`, and `340`.

By adding virtual nodes, the ring will have more evenly spaced positions, minimizing hotspots and balancing load across all physical nodes.

---

### Formula Summary:

1. **Hash Function**:
   - Hash of a node: `H(Node) → Position on Ring (0, m-1)`
   - Hash of a key: `H(key) → Position on Ring (0, m-1)`
  
2. **Routing Rule**:
   - `key_i` is assigned to the next node in a **clockwise direction**.

3. **Rebalancing with N Nodes**:
   - After adding/removing a node, only about `K/N` keys are redistributed (`K` = total keys, `N` = total nodes).



## Why do we need this?

In traditional hashing-based distribution methods, we use a hash function to hash our partition keys (i.e. request ID or IP). Then if we use the modulo against the total number of nodes (server or databases). This will give us the node where we want to route our request.

![simple-hashing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/consistent-hashing/simple-hashing.png)

$$
\begin{align*}
& Hash(key_1) \to H_1 \bmod N = Node_0 \\
& Hash(key_2) \to H_2 \bmod N = Node_1 \\
& Hash(key_3) \to H_3 \bmod N = Node_2 \\
& ... \\
& Hash(key_n) \to H_n \bmod N = Node_{n-1}
\end{align*}
$$

Where,

`key`: Request ID or IP.

`H`: Hash function result.

`N`: Total number of nodes.

`Node`: The node where the request will be routed.

The problem with this is if we add or remove a node, it will cause `N` to change, meaning our mapping strategy will break as the same requests will now map to a different server. As a consequence, the majority of requests will need to be redistributed which is very inefficient.

We want to uniformly distribute requests among different nodes such that we should be able to add or remove nodes with minimal effort. Hence, we need a distribution scheme that does not depend directly on the number of nodes (or servers), so that, when adding or removing nodes, the number of keys that need to be relocated is minimized.

Consistent hashing solves this horizontal scalability problem by ensuring that every time we scale up or down, we do not have to re-arrange all the keys or touch all the servers.

Now that we understand the problem, let's discuss consistent hashing in detail.

## How does it work

Consistent Hashing is a distributed hashing scheme that operates independently of the number of nodes in a distributed hash table by assigning them a position on an abstract circle, or hash ring. This allows servers and objects to scale without affecting the overall system.

![consistent-hashing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/consistent-hashing/consistent-hashing.png)

Using consistent hashing, only `K/N` data would require re-distributing.

$$
R = K/N
$$

Where,

`R`: Data that would require re-distribution.

`K`: Number of partition keys.

`N`: Number of nodes.

The output of the hash function is a range let's say `0...m-1` which we can represent on our hash ring. We hash the requests and distribute them on the ring depending on what the output was. Similarly, we also hash the node and distribute them on the same ring as well.

$$
\begin{align*}
& Hash(key_1) = P_1 \\
& Hash(key_2) = P_2 \\
& Hash(key_3) = P_3 \\
& ... \\
& Hash(key_n) = P_{m-1}
\end{align*}
$$

Where,

`key`: Request/Node ID or IP.

`P`: Position on the hash ring.

`m`: Total range of the hash ring.

Now, when the request comes in we can simply route it to the closest node in a clockwise (can be counterclockwise as well) manner. This means that if a new node is added or removed, we can use the nearest node and only a _fraction_ of the requests need to be re-routed.

In theory, consistent hashing should distribute the load evenly however it doesn't happen in practice. Usually, the load distribution is uneven and one server may end up handling the majority of the request becoming a _hotspot_, essentially a bottleneck for the system. We can fix this by adding extra nodes but that can be expensive.

Let's see how we can address these issues.

## Virtual Nodes

In order to ensure a more evenly distributed load, we can introduce the idea of a virtual node, sometimes also referred to as a VNode.

Instead of assigning a single position to a node, the hash range is divided into multiple smaller ranges, and each physical node is assigned several of these smaller ranges. Each of these subranges is considered a VNode. Hence, virtual nodes are basically existing physical nodes mapped multiple times across the hash ring to minimize changes to a node's assigned range.

![virtual-nodes](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/consistent-hashing/virtual-nodes.png)

For this, we can use `k` number of hash functions.

$$
\begin{align*}
& Hash_1(key_1) = P_1 \\
& Hash_2(key_2) = P_2 \\
& Hash_3(key_3) = P_3 \\
& . . . \\
& Hash_k(key_n) = P_{m-1}
\end{align*}
$$

Where,

`key`: Request/Node ID or IP.

`k`: Number of hash functions.

`P`: Position on the hash ring.

`m`: Total range of the hash ring.

As VNodes help spread the load more evenly across the physical nodes on the cluster by diving the hash ranges into smaller subranges, this speeds up the re-balancing process after adding or removing nodes. This also helps us reduce the probability of hotspots.


### Data Replication in Consistent Hashing

In systems utilizing **consistent hashing**, replication ensures **high availability** and **durability** by storing each piece of data across multiple nodes. 

- **Replication Factor (N)**: This defines the number of nodes where copies of data are stored.
- In distributed systems, such as **eventually consistent** systems, replication is done **asynchronously**, meaning updates can take time to propagate to all replicas.

### Advantages of Consistent Hashing

- **Predictable Scaling**: Adding/removing nodes has minimal disruption.
- **Facilitates Partitioning and Replication**: Distributes data across nodes efficiently.
- **Scalability and Availability**: Supports horizontal scaling and improves fault tolerance.
- **Reduces Hotspots**: Minimizes overloading of specific nodes through balanced distribution.

### Disadvantages of Consistent Hashing

- **Increased Complexity**: Implementing consistent hashing and replication adds design complexity.
- **Cascading Failures**: A failure in one node can affect others.
- **Uneven Load Distribution**: Even with virtual nodes, perfect balance is not guaranteed.
- **Costly Key Management**: Transient node failures can make key management expensive.

### Use Cases of Consistent Hashing

## Examples

Let's look at some examples where consistent hashing is used:

- Data partitioning in [Apache Cassandra](https://cassandra.apache.org).
- Load distribution across multiple storage hosts in [Amazon DynamoDB](https://aws.amazon.com/dynamodb).


- **Apache Cassandra**: A distributed NoSQL database that uses consistent hashing for partitioning.
- **Amazon DynamoDB**: A key-value database that applies consistent hashing for load distribution across storage hosts.

---

### Database Federation

**Database Federation** refers to splitting databases by function, where multiple physical databases appear as a single **logical database** to users.

- **Federated Schema**: Ties the databases together, providing a common interface and data structure for communication.

#### Characteristics of a Federated Database:

- **Transparency**: Hides the differences between data sources from users.
- **Heterogeneity**: Supports diverse hardware, networks, and data models.
- **Extensibility**: Allows easy addition of new data sources.
- **Autonomy**: Maintains independence of existing data sources.
- **Data Integration**: Combines data from various systems seamlessly.

#### Advantages of Federated Databases:

- **Flexible Data Sharing**: Access data across databases without tight coupling.
- **Autonomy**: Independent management of each database component.
- **Unified Data Access**: Simplifies access to heterogeneous data sources.
- **Decoupling from Legacy Systems**: Modern applications don’t need to integrate deeply with older databases.

#### Disadvantages of Federated Databases:

- **Increased Complexity**: Managing multiple systems and integrating data adds complexity.
- **Joining Data**: Complex queries across databases can be difficult to execute.
- **Autonomy Issues**: Dependency on autonomous data sources can introduce delays.
- **Performance and Scalability**: Scaling federated databases can be challenging.

### N-Tier Architecture Overview

**N-Tier architecture** separates an application into multiple logical layers and physical tiers, where each layer has a distinct responsibility. This separation helps manage dependencies, improve scalability, and enhance maintainability. Each layer typically interacts with the one directly below it, though in some configurations, it can access any lower layer.

![n-tier-architecture](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/n-tier-architecture/n-tier-architecture.png)

**Layers vs. Tiers**:
- **Layers**: Logical separation of concerns.
- **Tiers**: Physical separation, where components are distributed across different machines.

### N-Tier Architecture Types

1. **3-Tier Architecture**:
   - **Presentation Layer**: Manages user interactions and UI.
   - **Business Logic Layer**: Processes data, applies business rules, and validates inputs.
   - **Data Access Layer**: Handles database operations and interacts with the data storage.

2. **2-Tier Architecture**:
   - Combines presentation and data access layers directly, with no intermediate business layer. The client communicates directly with the database.

3. **Single-Tier (1-Tier) Architecture**:
   - All components run on a single server or computer, often seen in desktop applications.

### Closed vs. Open Layer Architecture
- **Closed Layer**: A layer can only communicate with the one directly below it, ensuring controlled interactions and limiting dependencies.
- **Open Layer**: A layer can communicate with any lower layer, which increases flexibility but may introduce unnecessary complexity.

### Advantages of N-Tier Architecture
- **Availability**: Independent tiers can increase application availability.
- **Security**: Each layer can enforce security policies, reducing risk exposure.
- **Scalability**: Tiers can be scaled independently, improving performance under load.
- **Maintenance**: Each layer can be managed separately, allowing specialized teams to focus on specific concerns.

### Disadvantages of N-Tier Architecture
- **Complexity**: More tiers and layers make the system harder to design and manage.
- **Network Latency**: As communication between tiers typically happens over a network, latency can increase with more tiers.
- **Cost**: Physically separating tiers often requires more hardware and infrastructure.
- **Security Management**: Managing network security across multiple tiers and layers becomes complex, especially with increased intercommunication.


Certainly! Let's break down **Message Brokers** and **Message Queues** in greater detail, using real-world examples and links for reference.

---

## Message Brokers

A **message broker** is middleware that facilitates communication between various applications and systems by handling message translations, routing, and delivery. The main goal of a message broker is to enable systems to exchange data reliably, regardless of their underlying platform or programming language. This decouples applications, allowing them to communicate without needing to know about each other’s existence or state.

### How It Works

When a **producer** (the service sending the message) sends a message to a broker, the broker manages the message until it can be processed by the **consumer** (the service receiving the message). The broker can store, filter, and deliver messages in a reliable manner, ensuring that data is transferred securely, even in distributed systems.

The **message flow** works like this:
1. The producer sends a message to the broker.
2. The broker stores the message and checks if the consumer is available.
3. The broker delivers the message to the consumer.
4. The consumer processes the message and acknowledges receipt.

### Real-World Example

Consider an e-commerce system where users place orders. A **message broker** like [RabbitMQ](https://www.rabbitmq.com) can be used to:
- Accept order data from the website.
- Send that data to a **payment service**, **inventory service**, and **shipping service** asynchronously.
- Each service processes the message independently. If one of the services is down, the message broker will retry or store the message until the service is back online.

This decoupling ensures that even if some parts of the system fail, the messages are not lost, and the system can still function smoothly.

### Models of Message Brokers

Message brokers support two primary messaging models:
1. **[Point-to-Point Messaging](https://karanpratapsingh.com/courses/system-design/message-queues)**: In this model, a message is sent to a queue, and only one consumer can consume each message. It's a one-to-one messaging model. For example, if you're handling banking transactions, you would use point-to-point messaging to ensure that only one service handles each transaction to avoid duplicate processing.
   
2. **[Publish-Subscribe (Pub/Sub) Messaging](https://karanpratapsingh.com/courses/system-design/publish-subscribe)**: In this model, a message is sent to a **topic**, and all consumers who subscribe to that topic receive the message. This is a one-to-many messaging model. For example, in a stock trading system, updates to stock prices can be published to a topic, and all consumers (e.g., mobile apps, websites) subscribing to that topic can receive real-time price updates.

### Comparison to Event Streaming

While **message brokers** like [RabbitMQ](https://www.rabbitmq.com) and [ActiveMQ](https://activemq.apache.org) focus on routing and guaranteeing message delivery, **event streaming platforms** like [Apache Kafka](https://kafka.apache.org) are optimized for high-throughput, real-time processing. Event streaming allows for logs of records (events) to be continuously appended to categories (topics) and consumed at any point.

For instance, Kafka is widely used for real-time analytics in financial systems. It can ingest huge volumes of stock market events, process them in real-time, and distribute them to multiple services. However, Kafka's focus on **event ordering** and **scalability** means it offers fewer built-in guarantees like exactly-once message delivery, which a message broker can provide.

### Advantages of Message Brokers

- **Decoupling**: Services can operate independently and communicate asynchronously. If one service is down, the others don’t need to wait for it to come back up.
  
- **Scalability**: Brokers handle a large number of messages, allowing distributed systems to scale easily.

- **Guaranteed Delivery**: Brokers ensure that messages are delivered, even if the consumer is temporarily unavailable. Messages are stored until the consumer is ready.

### Disadvantages of Message Brokers

- **Increased Complexity**: Introducing a message broker adds a new component to the system architecture that needs to be maintained.

- **Message Overhead**: Adding multiple consumers or complex routing can result in network and processing overhead.

### Common Message Brokers

- [RabbitMQ](https://www.rabbitmq.com): Great for traditional message queuing systems. It supports both point-to-point and pub/sub models.
  
- [Apache Kafka](https://kafka.apache.org): Designed for high-throughput event streaming and log processing.

- [NATS](https://nats.io): Lightweight, fast, and scalable broker for real-time applications.

---

## Message Queues

A **message queue** is a form of communication between services where messages are stored until they are processed. It's a reliable way to ensure that no data is lost when scaling services across distributed systems. A queue ensures that each message is delivered to one consumer and processed only once.

### How It Works

The producer pushes messages to a queue. The messages sit in the queue until a consumer is available to pull and process them. The consumer can then notify the queue that the message has been successfully processed, after which the message is removed from the queue.

- **Producers** can add jobs to the queue without waiting for them to be processed.
- **Consumers** can process jobs from the queue at their own pace.

### Real-World Example

Let’s say you have an online video processing service like [YouTube](https://www.youtube.com). Users upload videos, which need to be processed (encoded into different formats) before they can be viewed.

- When a video is uploaded, a job (message) is added to the message queue.
- Different video processing services (consumers) will pull jobs from the queue and encode them.
- Once the encoding is complete, the consumer sends a notification back, and the queue marks the job as processed.

This system ensures that multiple video encoders can work independently without overloading the system. The queue acts as a buffer that holds unprocessed jobs.

### Features of Message Queues

- **Push or Pull Delivery**: Messages can be delivered either by polling the queue (pull) or being pushed to the consumer when available.

- **FIFO (First-In-First-Out)**: Ensures that messages are processed in the order they were sent. This is critical for tasks like financial transactions where the order matters.

- **Delayed Delivery**: Some queues support scheduling messages for future delivery or processing. For example, sending emails at a scheduled time.

- **Dead-Letter Queues**: If a message cannot be processed (due to system errors or corrupt data), it can be moved to a **dead-letter queue** for later inspection.

- **Backpressure**: When the queue starts to fill up faster than it can be processed, **backpressure** mechanisms can prevent system overload by limiting the number of incoming requests.

### Advantages of Message Queues

- **Scalability**: Queues help scale systems easily by allowing multiple consumers to process jobs in parallel. For example, during peak traffic times (e.g., Black Friday), multiple servers can pull tasks from the same queue to handle the load.

- **Decoupling**: Queues decouple producers and consumers. For example, in a web app where users upload files, the web server doesn’t need to process the files directly. It can add them to the queue and respond to the user immediately while the background workers process them.

- **Reliability**: Messages in a queue are persistent, meaning they are stored until processed, ensuring no data loss in case of service crashes.

### Disadvantages of Message Queues

- **Latency**: Depending on the load, messages might sit in the queue for some time before they are processed, introducing latency in the system.

- **Complexity**: Managing a message queue system, handling retries, and ensuring idempotency can add complexity to system design.

### Common Message Queues

- **[Amazon SQS](https://aws.amazon.com/sqs)**: A fully-managed message queuing service that scales automatically and handles millions of messages per second.
  
- **[RabbitMQ](https://www.rabbitmq.com)**: Popular for its flexibility in message routing and reliable message queuing.

- **[ActiveMQ](https://activemq.apache.org)**: Open-source message queue used in many enterprise systems.

---

By understanding the distinct roles of **message brokers** and **message queues**, you can design systems that are robust, scalable, and reliable, enabling asynchronous, decoupled communication across microservices and distributed systems.

The **Publish-Subscribe (Pub/Sub)** pattern is a messaging model where messages, also known as events, are sent (or "published") to a specific topic by a publisher. The key feature of this model is that multiple subscribers can receive messages from the same topic, and they don’t need to be aware of each other or the publisher. This ensures a highly decoupled communication system, making it a popular choice in event-driven architectures.

### Working of Publish-Subscribe

In a **Pub/Sub** system:
- **Publisher**: This is the component that sends messages to a **topic** without worrying about which subscribers will consume the messages. It just broadcasts information.
- **Subscriber**: These are the consumers who subscribe to a **topic** to receive updates whenever the publisher broadcasts a message. Each subscriber can process the message differently based on its specific use case.

Unlike **message queues**, where a message is consumed by one consumer, in a **pub/sub** model, the same message is sent to multiple consumers (all subscribers of a topic) at the same time.

**Example Workflow**:
1. **Topic Creation**: A topic is created, such as "Order Processing" or "System Alerts."
2. **Publisher Sends a Message**: A publisher, such as a **payment gateway** or **monitoring service**, sends a message about a new event to this topic.
3. **Subscribers Receive Message**: All components that are subscribed to this topic (e.g., **shipping system**, **inventory system**, or **email notification service**) receive this message simultaneously and handle it in their own way.

### Real-World Example

Imagine a news agency that wants to notify different systems whenever breaking news happens:
- The **news agency** acts as a publisher and sends the news to a "Breaking News" topic.
- **Subscribers** could include:
  - A **mobile app** that sends push notifications.
  - A **website** that updates the news section.
  - A **statistics system** that tracks the most-read articles.

Each of these subscribers will receive the same news message but will process it differently (push notification, website update, etc.).

### Key Features of Pub/Sub

1. **Push-Based Delivery**: As soon as a message is published, it is immediately pushed to all subscribers without the need for them to poll for new messages. This reduces latency, making it ideal for real-time systems like financial trading or live sports scores.

2. **Fanout**: The message is broadcast to all subscribers simultaneously. This means that multiple consumers can handle the same message in parallel, which can be useful in scenarios like logging, monitoring, or notifications.

3. **Decoupling**: Publishers and subscribers don’t need to know about each other. The publisher just pushes to a topic, and any number of subscribers can process the message independently. This allows the systems to scale independently. For example, more subscribers can be added without changing the publisher’s logic.

4. **Filtering**: Subscribers can apply filters so that they only receive messages that are relevant to them. For instance, in a weather notification system, a subscriber might filter for messages related to hurricanes and ignore others.

5. **Durability**: Many Pub/Sub systems ensure durability, meaning messages are stored until they are delivered to all subscribers. This ensures that no messages are lost if a subscriber is temporarily unavailable.

6. **Security**: Authentication mechanisms ensure that only authorized components can publish or subscribe to topics. Additionally, messages can be encrypted to ensure security during transmission.

### Pub/Sub vs Message Queues

- **Message Queues**: A single consumer typically processes each message. Once a message is consumed, it’s removed from the queue. This is ideal for **task-based** systems where each task should be processed once.
  
- **Publish-Subscribe**: Each message is sent to all subscribers. Multiple consumers can process the same message independently. This is ideal for **broadcasting** events to multiple systems at once.

For example:
- **Message Queue**: A task scheduling system where each task (message) should be handled by one worker.
- **Pub/Sub**: A stock price alert where multiple users (subscribers) should receive updates on stock price changes.

### Advantages of Pub/Sub

1. **Eliminates Polling**: Subscribers don’t need to continuously check if a new message is available. Instead, they get notified automatically when a new message is published. This reduces system load and improves real-time performance.
   
2. **Scalability**: Publishers and subscribers can be scaled independently. For instance, you could have many consumers processing messages in parallel without overloading the publisher.

3. **Dynamic Targeting**: Publishers don’t need to know the consumers; they just send messages to a topic. Any interested subscriber can subscribe to that topic dynamically, reducing system complexity.

4. **Loose Coupling**: Since the publisher and subscribers are decoupled, changes to one do not impact the other. This allows for easier maintenance and upgrades.

### Common Use Cases

- **Notifications and Alerts**: When something important happens, such as a system alert or a new user sign-up, pub/sub is used to notify various services (e.g., SMS service, email service, logging systems).
  
- **Event-Driven Systems**: In microservices architectures, pub/sub can be used to distribute events like order updates across services.
  
- **Real-Time Data Streaming**: Systems like financial applications or social media feeds use pub/sub to stream real-time data to multiple endpoints.

### Pub/Sub Technologies

- **[Amazon SNS (Simple Notification Service)](https://aws.amazon.com/sns/)**: A fully managed pub/sub messaging service used for notifications and alerts. SNS allows you to send messages to various endpoints like HTTP/S, email, SMS, and AWS Lambda.

- **[Google Pub/Sub](https://cloud.google.com/pubsub)**: A messaging service that allows developers to build event-driven applications. It is highly scalable and is used in scenarios like real-time data analytics and log processing.

- **[Apache Kafka](https://kafka.apache.org)**: Although primarily known as an event streaming platform, Kafka also supports pub/sub communication. Kafka is widely used for real-time data pipelines and streaming applications.

---

### Further Reading

To dive deeper into Pub/Sub, you can explore:
- [AWS SNS Documentation](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)
- [Google Pub/Sub Documentation](https://cloud.google.com/pubsub/docs/overview)
- [Pub/Sub System Design - System Design Primer](https://github.com/donnemartin/system-design-primer)

These resources will give you a more detailed understanding of how pub/sub works and how you can implement it in different cloud environments.


An **Enterprise Service Bus (ESB)** is a key architectural pattern used in complex systems to handle integrations between multiple services or applications. Its main purpose is to act as a communication hub, connecting various systems that might use different protocols, data formats, or communication methods. An ESB ensures seamless communication, message routing, data transformation, and more, making it critical for large-scale enterprises that have numerous, interconnected systems.

### How ESB Works

The **ESB** serves as a middleware layer that centrally manages and facilitates communication between various systems, enabling services to communicate with one another. The ESB can handle multiple tasks like:
1. **Message Routing**: Directs messages between services based on predefined rules.
2. **Protocol Conversion**: Converts one communication protocol (e.g., HTTP, JMS, SOAP) into another, allowing systems using different protocols to communicate.
3. **Data Transformation**: Changes the data structure or format between the sender and receiver to ensure compatibility.
4. **Orchestration**: Manages complex workflows by coordinating multiple service requests into a single business process.
5. **Security**: Provides centralized security controls such as authentication, authorization, and encryption.
6. **Error Handling**: Manages error handling and retries, ensuring that failed integrations don’t cause a system-wide crash.

**Example Workflow**:
- **Scenario**: An e-commerce system that integrates an inventory system, payment gateway, and customer notification service.
    - When a new order is placed, the **ESB** receives the order details.
    - It routes the order data to the **Inventory System** to update stock levels.
    - Then, it transforms the message to the format the **Payment Gateway** understands and sends the payment request.
    - After successful payment, it notifies the **Customer Notification System** to send confirmation emails.
    - All these services may use different protocols and formats, and the ESB ensures seamless communication between them.

### Advantages of an ESB

1. **Improved Developer Productivity**: The ESB allows developers to integrate new technologies or systems into an application without disrupting existing services. For instance, if a new CRM system is added, developers can integrate it via the ESB without modifying the entire architecture.
   
2. **Simplified Scaling**: Individual components connected to the ESB can scale independently. For example, if the load on the payment gateway increases, you can scale it without affecting the rest of the system.

3. **Increased Resilience**: An ESB isolates services from each other, ensuring that failure in one service does not affect others. For example, if the customer notification system fails, the payment and inventory systems continue to operate independently.

4. **Centralized Governance**: The ESB serves as a single point for managing communication policies, security, and compliance. This is particularly beneficial in organizations with strict regulations around data privacy and security.

5. **Service Reusability**: The ESB enables reusable services. If multiple systems need to access the inventory system, the ESB can provide a common interface, eliminating the need to create multiple point-to-point integrations.

### Disadvantages of an ESB

Despite its benefits, the ESB also has several downsides:

1. **Single Point of Failure**: If the ESB goes down, all communication between systems may fail. This can be mitigated with proper redundancy and failover strategies, but it’s still a risk.
   
2. **Complexity**: The centralized nature of an ESB adds complexity. The more services you integrate, the more configurations, rules, and data transformations the ESB must manage, which can become cumbersome over time.

3. **Change Management**: When a change is made to the ESB (such as updating message formats or routing rules), it can impact all integrated systems. This necessitates rigorous testing and risk mitigation before applying any updates.

4. **Performance Bottleneck**: In a highly integrated environment, all traffic must pass through the ESB, potentially creating a performance bottleneck. If not optimized, this can slow down the entire system.

5. **Cross-Team Collaboration Challenges**: Because the ESB is centrally managed, making changes or coordinating updates across multiple teams (e.g., developers, operations) can become difficult. Teams often need to go through the ESB management team for modifications, which can slow down development cycles.

### Use Cases for an ESB

- **Financial Systems**: Banks and financial institutions often use ESBs to connect their various systems (e.g., ATM networks, payment gateways, and customer relationship management systems) that use different protocols and data formats.
  
- **Retail and E-commerce**: E-commerce platforms need to integrate payment systems, inventory management, customer notifications, and shipping services. An ESB can handle these integrations, allowing for seamless coordination between the services.

- **Healthcare**: In healthcare, various systems (e.g., electronic health records, billing systems, lab systems) need to exchange data. An ESB can handle protocol conversions and ensure the secure transmission of sensitive health data.

### ESB vs Microservices

While **ESBs** were once considered the go-to integration solution, the rise of **microservices architectures** has introduced alternatives to the ESB. In microservices, services communicate directly using lightweight protocols like REST and messaging queues. However, the ESB is still a valid solution when centralized control and complex transformations are required. Here’s a comparison:

- **ESB**:
  - Best for large, centralized control of enterprise systems.
  - Handles complex workflows, transformations, and orchestration.
  - Can introduce bottlenecks due to its centralized nature.

- **Microservices with APIs**:
  - Best for decentralized, lightweight systems.
  - Services communicate directly via REST APIs or message queues like Kafka.
  - Offers better scalability and reduced risk of single points of failure.

### Examples of ESB Technologies

1. **[Azure Service Bus](https://azure.microsoft.com/en-in/services/service-bus)**: A fully managed enterprise integration messaging service by Microsoft that enables decoupled communication between services.
   
2. **[IBM App Connect](https://www.ibm.com/in-en/cloud/app-connect)**: A tool that simplifies integration flows by connecting applications and systems in an enterprise.

3. **[Apache Camel](https://camel.apache.org)**: An open-source integration framework that works with multiple data formats and communication protocols.

4. **[Fuse ESB](https://www.redhat.com/en/technologies/jboss-middleware/fuse)**: A Red Hat product that simplifies integration between services, apps, and data with a lightweight ESB.

### Further Reading

To learn more about ESB and explore practical use cases, you can refer to the following:
- [What is Azure Service Bus?](https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview)
- [IBM App Connect Documentation](https://www.ibm.com/docs/en/app-connect)
- [Apache Camel Documentation](https://camel.apache.org/manual/latest/index.html)

These resources will help you understand the different ESB solutions and how to implement them in your enterprise architecture.

# Monoliths and Microservices

### Monoliths

A **monolith** is a software architecture pattern where the entire application is built as a single, indivisible unit. This means all components and functionalities are bundled together into one cohesive unit, rather than being separated into different services or modules.

![monolith](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/monoliths-microservices/monolith.png)

#### Characteristics

- **Single Codebase**: All features, modules, and functionalities are integrated into one codebase.
- **Single Deployment**: The entire application is deployed together, as one unit.
- **Tightly Coupled**: Different parts of the application are tightly integrated and dependent on each other.

#### Advantages of Monoliths

1. **Simple Development and Debugging**: Since everything is contained within one codebase, developers can easily access and modify the code, making development and debugging more straightforward.
   
2. **Fast and Reliable Communication**: Components within a monolithic application communicate directly with each other through function calls, which is faster and more reliable compared to network calls.

3. **Easy Monitoring and Testing**: Monitoring and testing are simpler as the entire application is available in a single unit, making it easier to track performance and issues.

4. **Supports ACID Transactions**: Monolithic applications typically handle transactions using ACID (Atomicity, Consistency, Isolation, Durability) principles effectively since all operations occur within a single application.

#### Disadvantages of Monoliths

1. **Complex Maintenance**: As the codebase grows, managing and maintaining a monolithic application becomes more challenging. Even minor changes require understanding the entire codebase.

2. **Tightly Coupled Application**: Different components are tightly coupled, making it hard to modify one part of the application without affecting others. This can hinder agility and slow down development.

3. **Commitment to Technology Stack**: A monolithic application usually commits to a single technology stack, which can be restrictive and limit the ability to adopt new technologies or frameworks.

4. **Redeployment Challenges**: Any update to the application requires redeploying the entire system, which can be time-consuming and risky.

5. **Reduced Reliability**: A single bug or failure can potentially bring down the entire system, impacting the application's overall reliability.

6. **Scaling Difficulties**: Scaling a monolithic application can be challenging because scaling requires scaling the entire application rather than individual components.

### Modular Monoliths

A **Modular Monolith** is an approach where the application is still a monolith in terms of deployment, but it is structured into well-defined, independent modules. Each module represents a specific feature or component of the application, and they communicate with each other through defined interfaces.

#### Benefits of Modular Monoliths

1. **Improved Maintainability**: By dividing the application into modules, each with its own responsibility, the codebase becomes more manageable. Changes to one module are less likely to affect others, which simplifies maintenance.

2. **Encapsulation**: Modules encapsulate their functionality and expose only necessary interfaces. This reduces inter-module dependencies and allows for more focused development and testing.

3. **Incremental Updates**: Modular design allows for incremental updates, where changes can be made to individual modules without redeploying the entire application.

4. **Flexibility**: While still a monolith, a modular approach can offer some benefits of microservices, such as easier testing and better organization, while avoiding the complexity of managing multiple services.

5. **Enhanced Collaboration**: Teams can work on different modules independently, leading to better collaboration and division of work.

#### Challenges with Modular Monoliths

1. **Complexity in Design**: Designing a modular monolith requires careful planning to ensure that modules are well-defined and have clear boundaries. Poor design can lead to tightly coupled modules that negate the benefits of modularization.

2. **Performance Overhead**: While modular monoliths can improve organization, the internal communication between modules can introduce overhead compared to direct function calls within a traditional monolith.

3. **Limited Isolation**: Although modular, all modules still run in the same process and share the same resources, which limits isolation compared to a microservices architecture.

### Use Cases for Modular Monoliths

- **Legacy Systems**: Organizations with existing monolithic applications can adopt a modular approach to improve maintainability and flexibility without completely rewriting their systems.
- **Medium-Sized Applications**: Applications that do not yet require the complexity of a microservices architecture but still need improved organization and maintainability can benefit from a modular monolith.

### Comparison with Microservices

**Monoliths** and **Modular Monoliths** vs. **Microservices**:

- **Monoliths/Modular Monoliths**:
  - Single codebase and deployment.
  - Easier to develop and debug in a tightly integrated environment.
  - Difficult to scale and adapt to new technologies.

- **Microservices**:
  - Multiple services, each with its own codebase and deployment.
  - Decentralized development and scaling.
  - More complex inter-service communication and deployment.

**Monolithic Architecture** is best suited for smaller applications or teams that need simplicity and tight integration, whereas **Microservices** are better for complex, large-scale systems requiring flexibility and independent scaling.

### Further Reading

To explore more about monolithic and modular monolith architectures, you might find these resources helpful:
- [Modular Monoliths: The Best of Both Worlds](https://www.redhat.com/en/blog/modular-monoliths-best-both-worlds)
- [The Evolution of Monoliths to Microservices](https://microservices.io/patterns/monolithic-to-microservices.html)

### Microservices

A **microservices architecture** breaks down an application into a collection of small, autonomous services. Each service is self-contained and is designed to handle a specific business capability or domain, operating independently from other services.

![microservices](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/monoliths-microservices/microservices.png)

### Characteristics

1. **Loosely Coupled**: Services are independent and can be deployed, scaled, and managed separately. This allows for faster development cycles and reduced dependencies.

2. **Small and Focused**: Each service addresses a specific business function or capability. The focus is on doing one thing well, which simplifies development and maintenance.

3. **Business-Oriented**: Microservices are often organized around business capabilities rather than technical layers, aligning closely with business needs and priorities.

4. **Resilience and Fault Tolerance**: The architecture is designed to handle failures gracefully. Services can fail without causing a complete system outage.

5. **Highly Maintainable**: Services are easier to understand, test, and maintain due to their small size and focused functionality.

### Advantages of Microservices

1. **Independent Deployment**: Each service can be deployed independently, allowing for continuous integration and deployment without affecting the entire system.

2. **Scalability**: Individual services can be scaled independently based on their own resource needs. This is more efficient than scaling a monolithic application as a whole.

3. **Flexibility in Technology Stack**: Different services can use different technologies or frameworks, allowing teams to choose the best tools for each job.

4. **Fault Isolation**: If a service fails, it does not necessarily bring down the entire system. This improves the overall reliability of the application.

5. **Team Autonomy**: Smaller teams can work on different services simultaneously without interfering with each other's work, improving development speed and productivity.

6. **Business Alignment**: Services are often aligned with business domains, making it easier to understand and manage business processes.

### Disadvantages of Microservices

1. **Distributed System Complexity**: Managing a distributed system introduces complexity in terms of service discovery, inter-service communication, and data management.

2. **Testing Challenges**: Testing interactions between services can be more complex than testing a monolithic application, requiring comprehensive integration testing.

3. **Operational Overhead**: Each service requires its own infrastructure, including databases and servers, which can be expensive and require more operational management.

4. **Inter-Service Communication**: Communication between services often involves network calls, which can introduce latency and require careful handling to ensure reliability.

5. **Data Consistency**: Ensuring data consistency across services can be challenging, particularly in systems where transactions span multiple services.

### Best Practices

1. **Model Services Around Business Domains**: Design services to align with business capabilities, ensuring they have clear, well-defined boundaries.

2. **Loose Coupling and High Cohesion**: Maintain low coupling between services and high cohesion within services to ensure they function independently while being easy to manage.

3. **Resilience Strategies**: Implement patterns like circuit breakers to prevent failures from propagating across services and ensure fault tolerance.

4. **Well-Defined APIs**: Services should communicate through well-defined APIs, avoiding the exposure of internal implementation details.

5. **Private Data Storage**: Each service should manage its own data, avoiding shared databases to reduce dependencies and improve modularity.

6. **Decentralized Teams**: Allow teams to be responsible for their own services, promoting ownership and reducing cross-team dependencies.

7. **Backward Compatibility**: Ensure API changes are backward compatible to prevent disruptions for clients consuming the service.

### Pitfalls

1. **Inappropriate Service Boundaries**: Incorrectly defining service boundaries can lead to tight coupling and dependencies between services.

2. **Complexity of Distributed Systems**: Underestimating the complexity of managing distributed systems can lead to operational challenges and inefficiencies.

3. **Shared Resources**: Using shared databases or common dependencies can undermine the benefits of microservices by creating tight coupling.

4. **Lack of Business Alignment**: Services that are not aligned with business domains can become difficult to manage and integrate.

5. **Clear Ownership**: Lack of clear ownership for services can lead to ambiguities in responsibilities and operational issues.

6. **Idempotency Issues**: Ensuring operations are idempotent (i.e., repeatable without side effects) can be challenging but is crucial for reliability.

7. **ACID vs BASE**: Microservices often use BASE (Basically Available, Soft state, Eventually consistent) instead of ACID (Atomicity, Consistency, Isolation, Durability) for consistency. Understanding when to use each model is important for maintaining data integrity.

### Distributed Monolith

A **Distributed Monolith** refers to a system that appears to use microservices but remains tightly coupled in practice. Common signs include:

- **Low Latency Communication**: Services require high-speed communication, indicating tight coupling.
- **Scalability Issues**: Services don’t scale independently.
- **Dependency Between Services**: Strong inter-service dependencies.
- **Shared Resources**: Common databases or resources.

To avoid a distributed monolith, ensure services are truly independent and focus on designing them to maximize their autonomy and minimize dependencies.

### Microservices vs Service-Oriented Architecture (SOA)

**Microservices** and **SOA** both aim to decompose applications into services, but they differ in scope:

- **SOA**: Focuses on reusability and interoperability of services using common communication standards. Services are typically larger and more generalized.

- **Microservices**: Focuses on small, autonomous services that are highly specialized and self-contained. Emphasizes team autonomy and decentralized development.

### When to Use Microservices

Microservices are beneficial for complex, large-scale systems with high development and operational demands. Consider microservices if:

- Your team is too large to work effectively on a single codebase.
- Teams experience frequent blockers due to dependencies on other teams.
- Microservices offer clear business value or solve specific organizational problems.
- Your current architecture imposes significant communication overhead.

**Monolithic architectures** might be more appropriate for simpler or smaller applications, or for teams that are not yet ready to handle the complexities of microservices. Starting with a monolithic approach and transitioning to microservices as the application grows can be a pragmatic strategy.

### Further Reading

For more in-depth exploration of microservices architecture, consider these resources:
- [Microservices Patterns](https://microservices.io/patterns/) by Chris Richardson
- [The Twelve-Factor App](https://12factor.net/) principles, which are often applied in microservices
- [Building Microservices](https://martinfowler.com/books/microservices.html) by Sam Newman

These resources offer additional insights and practical guidance on implementing and managing microservices effectively.


---
### Event-Driven Architecture (EDA)

**Event-Driven Architecture (EDA)** is a system architecture where events are used to communicate between services. Events are produced, routed, and consumed asynchronously, typically through a **message broker**. This decoupling allows for more scalable and flexible systems.

---

### What is an Event?

An **event** is a signal that represents a change in state within a system. It does not specify how the system should respond, only that a change has occurred. Examples include a user submitting a form, a system update, or an API call.

---

### Components of EDA

1. **Event Producers**: These are the sources that generate and publish events. For example, a service that logs user actions.
2. **Event Routers**: These act as intermediaries (like message brokers), routing events from producers to appropriate consumers.
3. **Event Consumers**: These components receive and process the events, taking action based on the data received.

---

### EDA Patterns

Some common architectural patterns in EDA include:

- **Sagas**: For managing distributed transactions.
- **Publish-Subscribe**: Where events are broadcasted to multiple consumers.
- **Event Sourcing**: Where events represent the primary source of truth for state.
- **CQRS**: A separation of read and write operations that often relies on events.

---

### Advantages of EDA

1. **Decoupling**: Producers and consumers are independent, reducing direct dependencies.
2. **Scalability**: Each component can be scaled independently.
3. **Flexibility**: New consumers can be added without affecting existing services.
4. **Agility**: Faster iteration and easier changes as services evolve.

---

### Challenges of EDA

1. **Guaranteed Delivery**: Ensuring all events are delivered can be tricky.
2. **Error Handling**: Handling errors in a distributed system is complex.
3. **Complexity**: Event-driven systems require careful design and management.
4. **Exactly-Once Processing**: Ensuring that events are processed once and in the correct order can be challenging.

---

### Use Cases for EDA

EDA is ideal for:

- **Real-time metrics** collection.
- **Logging** systems.
- **Integrating disparate systems**.
- **Fan-out** scenarios where multiple consumers need to process the same event simultaneously.

---

### Technologies for Implementing EDA

Common technologies used for EDA include:

- **NATS**: A lightweight, high-performance messaging system.
- **Apache Kafka**: A distributed streaming platform for high-throughput data pipelines.
- **Amazon EventBridge**: A serverless event bus for event-driven applications on AWS.
- **Amazon SNS**: A messaging service for fan-out and distributed communication.
- **Google Pub/Sub**: A messaging service for real-time analytics and streaming.

- [NATS](https://nats.io)
- [Apache Kafka](https://kafka.apache.org)
- [Amazon EventBridge](https://aws.amazon.com/eventbridge)
- [Amazon SNS](https://aws.amazon.com/sns)
- [Google PubSub](https://cloud.google.com/pubsub)


EDA enables systems to respond to changes in real-time and evolve independently, but it requires careful design to manage its inherent complexity.
### Event Sourcing

**Event Sourcing** is an architectural pattern where the changes (events) to an application's state are stored in an append-only log. Instead of storing only the current state of the data, every change (event) is recorded, and the current state can be derived by replaying all events from the log. This approach creates a **system of record** that holds the complete history of all changes.

---

### Event Sourcing vs Event-Driven Architecture (EDA)

Event Sourcing and Event-Driven Architecture (EDA) are often confused, but they serve different purposes:

- **Event-Driven Architecture (EDA)**: Focuses on using events to enable communication between services in a decoupled, asynchronous manner. EDA uses a message broker to publish and consume events.
  
- **Event Sourcing**: Focuses on **storing events as the source of truth** instead of the current state. These events represent each change in the system's state.

Event Sourcing can be used as a pattern **within** an event-driven architecture but is not synonymous with EDA.

---

### Advantages of Event Sourcing

- **Real-time data reporting**: Since the entire history is available, systems can easily provide insights based on past events.
- **Fail-safety**: If the system crashes, state can be restored by replaying events.
- **Flexibility**: All types of events can be stored and replayed for different purposes.
- **Audit logs**: It naturally provides audit logs for compliance, as it records every state change.

---

### Disadvantages of Event Sourcing

- **Efficient network infrastructure**: The system needs a highly efficient network to handle continuous event generation and storage.
- **Message format management**: A schema registry or some method to handle varying event formats is required.
- **Different event payloads**: Events may carry different data payloads, making standardization a challenge.

---

### Command and Query Responsibility Segregation (CQRS)

**Command Query Responsibility Segregation (CQRS)** is an architectural pattern where **commands** and **queries** are separated. This improves the system by allowing **commands** (actions that modify data) and **queries** (data requests) to be optimized independently.

- **Command**: An action that changes state, returns only success/failure, and does not return data.
- **Query**: A request for data that does not alter system state.

---

### CQRS with Event Sourcing

CQRS is commonly paired with Event Sourcing. In this case, the **event log** serves as the **write model** (the source of truth), while the **read model** is created by **materializing views** of the event log data, often in a **denormalized** format optimized for querying.

---

### Advantages of CQRS

- **Independent scaling**: Read and write workloads can be scaled independently.
- **Easier optimizations**: Read and write operations can be optimized separately.
- **Closer to business logic**: Clear separation of responsibilities and behavior.
- **Simplified querying**: Avoids complex joins by using denormalized read models.
- **Clear boundaries**: Commands and queries have distinct boundaries within the system.

---

### Disadvantages of CQRS

- **Complex design**: The separation increases the system’s architectural complexity.
- **Message duplication**: Risk of message failures or duplicate messages.
- **Eventual consistency**: The system may experience eventual consistency between the write and read models.
- **Maintenance**: Requires more effort to maintain and update.

---

### Use Cases for CQRS

- **Fine-tuned performance** for read and write operations.
- **Evolving systems** where business rules and data models change regularly.
- **Integration** with other systems, especially when combined with event sourcing.
- **Enhanced security** by controlling which entities can write to the data.

CQRS and Event Sourcing are powerful patterns that address the scalability, complexity, and flexibility needs of modern distributed systems, though they introduce complexity that needs to be carefully managed.
### API Gateway

An **API Gateway** acts as a single entry point for all client interactions with backend services. It is responsible for managing client requests and handling tasks like **authentication, load balancing, caching, and logging**. By consolidating multiple microservice endpoints, the API Gateway simplifies the client-server interaction.

---

### Why Use an API Gateway?

Microservices typically offer **fine-grained APIs**. However, clients often need to interact with multiple services, leading to complex client-side logic. An API Gateway solves this by offering a **single point of entry**, simplifying the client’s communication and adding centralized management.

---

### Key Features

- **Authentication and Authorization**
- **Service Discovery**
- **Reverse Proxy**: Routes client requests to the appropriate backend services.
- **Caching**: Stores responses to improve performance.
- **Security**
- **Retry and Circuit Breaking**: Handles failures and retries failed requests.
- **Load Balancing**: Distributes client requests evenly across backend services.
- **Logging, Tracing**
- **API Composition**: Combines responses from multiple microservices.
- **Rate Limiting and Throttling**
- **Versioning**
- **Routing**
- **IP Whitelisting/Blacklisting**

---

### Advantages

- **Encapsulates internal APIs**: Hides internal microservice architecture.
- **Simplifies client-side logic**: Clients only interact with a single API.
- **Centralized monitoring and management**: Facilitates logging, tracing, and analytics.
- **Improved security and performance management**: Provides better control over API access and response times.

---

### Disadvantages

- **Single point of failure**: If not handled carefully, the API Gateway can become a bottleneck.
- **Performance overhead**: Adds latency if not properly optimized.
- **Scaling challenges**: Needs to be scaled appropriately to handle high traffic.
- **Complex configuration**: Can require careful tuning to match the needs of different services and clients.

---

### Backend for Frontend (BFF) Pattern

The **Backend For Frontend (BFF)** pattern involves creating dedicated backend services for specific front-end applications. This prevents the need to tailor a general backend for multiple clients. The BFF handles **data fetching and formatting** from microservices, ensuring that the front end receives data in the required format.

- **When to Use BFF?**
  - When maintaining a shared backend is cumbersome.
  - To optimize backend data for specific frontend requirements.
  - When multiple frontends have different data requirements.

---

### API Gateway Examples

- [Amazon API Gateway](https://aws.amazon.com/api-gateway)
- [Apigee API Gateway](https://cloud.google.com/apigee)
- [Azure API Gateway](https://azure.microsoft.com/en-in/services/api-management)
- [Kong API Gateway](https://konghq.com/kong)

API Gateways provide a powerful way to manage microservices by offering a unified entry point, improving both security and performance.

# REST, GraphQL, gRPC

A good API design is always a crucial part of any system. But it is also important to pick the right API technology. So, in this tutorial, we will briefly discuss different API technologies such as REST, GraphQL, and gRPC.
Got it! I'll make sure to keep the links intact while giving a detailed response.

---

## What's an API?

An **API** (Application Programming Interface) is a set of rules that allows one piece of software to interact with another. APIs define how requests and responses should be made between systems, acting as a bridge to exchange data or execute functions. It’s like a contract that specifies what information can be requested and how the response will be structured.

In essence, APIs allow communication between applications, enabling functionalities like retrieving data from a server or performing actions within an app. For example, when you log in using Google or Facebook on another site, an API is responsible for that communication.

---

## REST

A **[REST API](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)** (Representational State Transfer) is an architectural style that follows a set of constraints for designing networked applications. It was first introduced by [Roy Fielding](https://roy.gbiv.com) in 2000. In RESTful APIs, the main building block is a **resource**.

### Key Concepts

1. **Constraints**: A RESTful API must follow these constraints:
   - **Uniform Interface**: Resources are accessed and modified via standard methods (e.g., GET, POST).
   - **Client-Server**: The server provides data, and the client consumes it; both are independent.
   - **Stateless**: Each request contains all the information needed, without relying on previous requests.
   - **Cacheable**: Responses can be cached for better performance.
   - **Layered System**: Allows for multiple layers, such as intermediaries between client and server.
   - **Code on Demand** (optional): Servers can deliver executable code to enhance client functionality.

2. **HTTP Verbs**: Common methods for interacting with resources:
   - **GET**: Retrieves data (e.g., `/users` to get a list of users).
   - **POST**: Creates a new resource (e.g., adding a user).
   - **PUT**: Updates or replaces a resource (e.g., updating user details).
   - **DELETE**: Deletes a resource (e.g., removing a user).

3. **HTTP Response Codes**: Status indicators of the API response:
   - **1xx**: Informational.
   - **2xx**: Success (e.g., 200 OK).
   - **3xx**: Redirection.
   - **4xx**: Client error (e.g., 404 Not Found).
   - **5xx**: Server error (e.g., 500 Internal Server Error).

---

### Advantages of REST

- **Simple and Flexible**: Easy to understand and implement. It works over HTTP and can use various formats like JSON and XML.
- **Decoupled**: The separation of the client and server allows for independent development.
- **Cacheable**: Improves performance by caching responses.
  
### Disadvantages of REST

- **Over-fetching**: REST may return more data than necessary.
- **Multiple round trips**: You might need several requests to gather all the required data.

---

### Use Case Example

REST APIs are commonly used in most web applications due to their flexibility. Consider an API that manages a **user** resource:

| URI           | HTTP Verb | Action               |
| ------------- | ----------| ---------------------|
| `/users`      | GET       | Retrieve all users    |
| `/users/{id}` | GET       | Retrieve a user by ID |
| `/users`      | POST      | Create a new user     |
| `/users/{id}` | PATCH     | Update a user by ID   |
| `/users/{id}` | DELETE    | Delete a user by ID   |

---

For more details on REST, check out this [REST architectural style paper](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).

**Learn more** about how HTTP status codes work [here](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes). 

---

Sure, here’s a detailed response on GraphQL including the links you provided:

---

## GraphQL

[GraphQL](https://graphql.org) is a query language and runtime for APIs designed to give clients exactly the data they request and nothing more. Developed by [Facebook](https://engineering.fb.com) and open-sourced in 2015, GraphQL provides a more flexible and efficient alternative to REST APIs.

### Key Concepts

1. **Schema**: 
   - The schema defines the types and operations available to clients. It serves as a contract between the client and server, detailing what queries and mutations can be performed.
   - Example:
     ```graphql
     type Query {
       getUser: User
     }

     type User {
       id: ID
       name: String
       city: String
       state: String
     }
     ```

2. **Queries**:
   - A query is a request from the client to fetch specific data. Queries allow clients to specify precisely what data they need.
   - Example:
     ```graphql
     {
       getUser {
         id
         name
         city
       }
     }
     ```

3. **Resolvers**:
   - Resolvers are functions that handle the actual retrieval of data for a query. They map fields in the schema to functions that return data.
   - Example resolver function:
     ```javascript
     const resolvers = {
       Query: {
         getUser: () => {
           return {
             id: "123",
             name: "Karan",
             city: "San Francisco"
           };
         }
       }
     };
     ```

### Advantages

- **Eliminates Over-fetching**: Clients only receive the data they request, avoiding unnecessary data transfer.
- **Strongly Defined Schema**: Provides a clear contract for what queries and mutations are possible.
- **Code Generation Support**: Tools like Apollo can generate code based on your GraphQL schema.
- **Payload Optimization**: Reduces the amount of data transferred over the network.

### Disadvantages

- **Shifts Complexity to Server-side**: The server must handle complex query processing and optimization.
- **Caching Challenges**: Caching can be more complex compared to REST due to dynamic queries.
- **Versioning Ambiguity**: Unlike REST, versioning is less straightforward.
- **N+1 Problem**: Multiple queries might lead to inefficient database queries, though this can be mitigated with tools like DataLoader.

### Use Cases

- **Efficient Data Retrieval**: Ideal for scenarios where you need to fetch multiple related resources in a single request.
- **Complex Systems**: Useful for systems where the data relationships are complex and frequently changing.
- **Rapid Prototyping**: Allows for quick adjustments to the API without impacting existing queries.

### Example

With the following GraphQL schema:
```graphql
type Query {
  getUser: User
}

type User {
  id: ID
  name: String
  city: String
  state: String
}
```

A client can make the following query:
```graphql
{
  getUser {
    id
    name
    city
  }
}
```

And receive this response:
```json
{
  "getUser": {
    "id": "123",
    "name": "Karan",
    "city": "San Francisco"
  }
}
```

Learn more about GraphQL at [graphql.org](https://graphql.org).

---

If you need more information or have questions about other API technologies like gRPC, feel free to ask!
Certainly! Here’s an updated version of the gRPC section with a real-time use case included:

---

## gRPC

[gRPC](https://grpc.io) is a modern, open-source framework for Remote Procedure Calls (RPC) that enables efficient, scalable, and high-performance communication between services. It utilizes HTTP/2 for transport, Protocol Buffers (protobufs) for serialization, and offers robust features for inter-service communication.

### Key Concepts

1. **Protocol Buffers (Protobufs)**

   **Concept**: Protocol Buffers is a language-neutral, platform-neutral interface definition language for defining data structures and services. Protobufs serialize data in a compact binary format that is faster and smaller than JSON or XML.

   **Example**:
   ```protobuf
   // Define a message type for a request
   message HelloRequest {
     string name = 1;
   }

   // Define a message type for a response
   message HelloResponse {
     string message = 1;
   }
   ```

2. **Service Definition**

   **Concept**: Services in gRPC are defined using protocol buffers. You specify the service methods and their input and output message types. Each method is an RPC that can be called remotely.

   **Example**:
   ```protobuf
   // Define a service with an RPC method
   service HelloService {
     rpc SayHello (HelloRequest) returns (HelloResponse);
   }
   ```

   Here, `HelloService` has one RPC method `SayHello` that takes a `HelloRequest` message and returns a `HelloResponse` message.

3. **Resolvers**

   **Concept**: In gRPC, resolvers are not a native concept as in GraphQL, but server-side methods (handlers) implement the service methods defined in the `.proto` file. These methods handle incoming requests and return responses.

   **Example**: Implementing the `SayHello` method in a gRPC server:
   ```python
   import grpc
   from concurrent import futures
   import hello_pb2
   import hello_pb2_grpc

   class HelloServiceServicer(hello_pb2_grpc.HelloServiceServicer):
       def SayHello(self, request, context):
           return hello_pb2.HelloResponse(message=f"Hello, {request.name}!")

   def serve():
       server = grpc.server(futures.ThreadPoolExecutor(max_workers=10))
       hello_pb2_grpc.add_HelloServiceServicer_to_server(HelloServiceServicer(), server)
       server.add_insecure_port('[::]:50051')
       server.start()
       server.wait_for_termination()

   if __name__ == '__main__':
       serve()
   ```

### Advantages

- **Lightweight and Efficient**: gRPC uses a binary protocol (HTTP/2 and Protobufs) which is more compact and efficient than text-based formats like JSON.
- **High Performance**: HTTP/2 provides features like multiplexed streams and server push, which enhance performance.
- **Built-in Code Generation**: gRPC tools generate client and server code in multiple languages based on `.proto` definitions.
- **Bi-directional Streaming**: Supports streaming of requests and responses, which is useful for real-time applications.

### Disadvantages

- **Relatively New**: Compared to REST and GraphQL, gRPC is newer and may have less mature tooling.
- **Limited Browser Support**: Native gRPC is not supported in browsers, though [gRPC-Web](https://grpc.io/docs/platforms/web/) provides a solution for web clients.
- **Steeper Learning Curve**: Requires learning protocol buffers and understanding gRPC-specific concepts.
- **Not Human Readable**: Protobufs are binary, so the data is not as easily readable as JSON or XML.

### Use Cases

gRPC is particularly well-suited for scenarios that require high performance and efficient communication. Here are some practical use cases:

- **Real-Time Communication**: For applications needing low latency and real-time updates, such as chat applications or live video streaming platforms. gRPC’s support for bi-directional streaming enables real-time messaging and updates between clients and servers.

- **Microservices Communication**: In a microservices architecture, gRPC provides efficient and high-performance communication between services. It’s ideal for environments where multiple services need to communicate frequently and with minimal latency.

- **Low Latency and High Throughput**: Applications where performance is critical, such as gaming platforms or financial services, benefit from gRPC’s low-latency and high-throughput capabilities.

- **Polyglot Environments**: In a development environment where services are written in multiple programming languages, gRPC’s support for many languages and automatic code generation helps maintain consistency and interoperability.

### Real-Time Use Case Example

**Use Case**: **Real-Time Chat Application**

In a real-time chat application, users need instant updates when messages are sent or received. gRPC’s bi-directional streaming capability is well-suited for this scenario.

**Example**:

1. **Service Definition** (Proto File - `chat.proto`):
   ```protobuf
   syntax = "proto3";

   service ChatService {
     rpc SendMessage (stream ChatMessage) returns (stream ChatMessage);
   }

   message ChatMessage {
     string sender = 1;
     string content = 2;
   }
   ```

2. **Server Implementation** (Python Example):
   ```python
   import grpc
   from concurrent import futures
   import chat_pb2
   import chat_pb2_grpc

   class ChatServiceServicer(chat_pb2_grpc.ChatServiceServicer):
       def SendMessage(self, request_iterator, context):
           for message in request_iterator:
               # Broadcast the message to all connected clients
               yield chat_pb2.ChatMessage(sender=message.sender, content=message.content)

   def serve():
       server = grpc.server(futures.ThreadPoolExecutor(max_workers=10))
       chat_pb2_grpc.add_ChatServiceServicer_to_server(ChatServiceServicer(), server)
       server.add_insecure_port('[::]:50051')
       server.start()
       server.wait_for_termination()

   if __name__ == '__main__':
       serve()
   ```

3. **Client Implementation** (Python Example):
   ```python
   import grpc
   import chat_pb2
   import chat_pb2_grpc

   def send_messages(stub):
       def message_generator():
           yield chat_pb2.ChatMessage(sender='Alice', content='Hello!')
           yield chat_pb2.ChatMessage(sender='Bob', content='Hi Alice!')

       for response in stub.SendMessage(message_generator()):
           print(f"Received message from {response.sender}: {response.content}")

   def run():
       with grpc.insecure_channel('localhost:50051') as channel:
           stub = chat_pb2_grpc.ChatServiceStub(channel)
           send_messages(stub)

   if __name__ == '__main__':
       run()
   ```

In this chat application example, the `ChatService` has a `SendMessage` RPC that allows clients to send and receive messages in real-time using bi-directional streaming. The server broadcasts each message to all connected clients, and clients can send messages and receive responses simultaneously.

Learn more about gRPC at [gRPC.io](https://grpc.io) and explore its features for building efficient and scalable communication systems.

---
Here's a comparative analysis of REST, GraphQL, and gRPC based on the parameters you've outlined:

---

## REST vs GraphQL vs gRPC

### Comparison Table

| Type    | Coupling | Chattiness | Performance | Complexity | Caching | Codegen | Discoverability | Versioning |
| ------- | -------- | ---------- | ----------- | ---------- | ------- | ------- | --------------- | ---------- |
| **REST**    | Low      | High       | Good        | Medium     | Great   | Bad     | Good            | Easy       |
| **GraphQL** | Medium   | Low        | Good        | High       | Custom  | Good    | Good            | Custom     |
| **gRPC**    | High     | Medium     | Great       | Low        | Custom  | Great   | Bad             | Hard       |

### Detailed Comparison

1. **Coupling**
   - **REST**: Low coupling. REST APIs typically expose resources and endpoints that are loosely connected. Clients interact with a well-defined interface without knowing the internal workings of the server.
   - **GraphQL**: Medium coupling. GraphQL requires the server to expose a schema that clients use to query data, which can create a tighter coupling between client and server than REST.
   - **gRPC**: High coupling. gRPC uses strongly typed service definitions and requires both client and server to use the same `.proto` files, leading to tighter coupling.

2. **Chattiness**
   - **REST**: High chattiness. REST APIs often require multiple requests to different endpoints to gather related data, leading to multiple round trips.
   - **GraphQL**: Low chattiness. GraphQL allows clients to request exactly the data they need in a single query, reducing the number of API calls.
   - **gRPC**: Medium chattiness. gRPC supports efficient communication and streaming, but complex operations might still require multiple requests.

3. **Performance**
   - **REST**: Good performance. REST APIs perform well but might be less efficient due to larger payloads and multiple requests.
   - **GraphQL**: Good performance. GraphQL's flexibility in querying can lead to optimized data retrieval, though complex queries might affect performance.
   - **gRPC**: Great performance. gRPC uses HTTP/2 and Protocol Buffers, making it highly efficient with low latency and high throughput.

4. **Complexity**
   - **REST**: Medium complexity. REST is relatively simple to implement and understand but can become complex with evolving requirements.
   - **GraphQL**: High complexity. GraphQL requires a well-defined schema and query language, making it more complex to implement and manage.
   - **gRPC**: Low complexity. gRPC's use of Protocol Buffers and code generation simplifies implementation and maintenance.

5. **Caching**
   - **REST**: Great caching support. REST leverages HTTP caching mechanisms, allowing responses to be cached effectively.
   - **GraphQL**: Custom caching. Caching can be complex as GraphQL queries are more dynamic and may require custom solutions.
   - **gRPC**: Custom caching. Caching is less straightforward due to the binary format and streaming nature, often requiring custom caching strategies.

6. **Code Generation**
   - **REST**: Bad. REST lacks built-in code generation support, often requiring manual implementation.
   - **GraphQL**: Good. GraphQL has strong tooling and libraries for code generation in various languages.
   - **gRPC**: Great. gRPC provides robust code generation for client and server stubs across multiple languages using `.proto` files.

7. **Discoverability**
   - **REST**: Good. RESTful APIs are typically easy to discover through documentation and well-defined endpoints.
   - **GraphQL**: Good. GraphQL schemas provide self-documenting APIs, allowing clients to explore available queries and mutations.
   - **gRPC**: Bad. gRPC lacks built-in discoverability, often requiring external tools or manual documentation.

8. **Versioning**
   - **REST**: Easy. REST APIs can use versioning strategies like URL paths or headers to manage changes and new versions.
   - **GraphQL**: Custom. Versioning in GraphQL is handled through schema evolution and deprecation, which can be complex.
   - **gRPC**: Hard. Versioning in gRPC requires managing `.proto` files and maintaining backward compatibility, which can be challenging.

### Which API Technology is Better?

There isn't a one-size-fits-all answer; the choice depends on your specific needs and context. Each technology has its own strengths:

- **REST**: Best for simple, well-defined interfaces with good caching support and easy versioning.
- **GraphQL**: Ideal for complex queries where clients need to request specific data and where flexible querying and efficient data fetching are important.
- **gRPC**: Suitable for high-performance, low-latency applications, especially in microservices environments where efficient communication and strong typing are needed.

Consider your application's requirements, the complexity of the data interactions, and the development and maintenance overhead when choosing the right API technology.

---

# Long polling, WebSockets, Server-Sent Events (SSE)

Web applications were initially developed around a client-server model, where the web client is always the initiator of transactions like requesting data from the server. Thus, there was no mechanism for the server to independently send, or push, data to the client without the client first making a request. Let's discuss some approaches to overcome this problem.
Here's an overview of HTTP Long Polling, including its working, advantages, and disadvantages:

---

## Long Polling

**Long polling** is a technique designed to push information from the server to the client without requiring the client to continuously request data. It allows for a more real-time experience by keeping a connection open until there is new data to send or a timeout occurs.

![long-polling](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/long-polling-websockets-server-sent-events/long-polling.png)

### Working

Here's how long polling works:

1. **Initial Request**: The client initiates a request to the server and waits for a response.
2. **Server Processing**: The server receives the request and holds the connection open until new data is available or a timeout occurs.
3. **Response**: Once new data is available, the server responds to the client with the update.
4. **New Request**: After receiving the response, the client immediately sends a new request to the server, creating a new long-polling connection.

This cycle repeats, allowing the server to push updates to the client as soon as they are available.

### Advantages

- **Easy Implementation**: Long polling is straightforward to implement and is supported by most web servers and browsers.
- **Compatibility**: It works with standard HTTP and is compatible with many existing web technologies.
- **Real-Time Experience**: Provides a near-real-time user experience by pushing updates to the client as soon as they are available.

### Disadvantages

- **Scalability Issues**: Each new request creates a new connection, which can be resource-intensive and problematic for high-traffic applications.
- **Increased Latency**: The server must wait for a new request to send updates, which can introduce latency.
- **Connection Overhead**: Maintaining many open connections can lead to increased server load and resource usage.
- **Message Ordering**: Managing reliable message ordering can be challenging when dealing with multiple simultaneous long-polling requests.

### Use Cases

Long polling is suitable for scenarios where:

- You need to push updates to clients in near real-time, but real-time requirements are not extremely high.
- Implementing WebSockets or Server-Sent Events (SSE) is not feasible due to compatibility or complexity reasons.
- The application is relatively simple and does not require the high performance of more advanced techniques.

For more real-time and scalable solutions, you might consider technologies like WebSockets or Server-Sent Events (SSE), which address some of the limitations of long polling.

---
Here’s an overview of WebSockets, including how they work, their advantages, and disadvantages:

---

## WebSockets

**WebSocket** is a protocol that enables full-duplex communication channels over a single TCP connection. This allows for a persistent, bidirectional connection between a client and a server, facilitating real-time data exchange with minimal overhead.

![websockets](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/long-polling-websockets-server-sent-events/websockets.png)

### Working

Here’s how WebSockets operate:

1. **Initiation**: The client starts the process by sending an HTTP request to the server with an `Upgrade` header indicating the desire to establish a WebSocket connection.
2. **Handshake**: The server responds with a status code indicating that the connection should be upgraded to a WebSocket connection (`101 Switching Protocols`).
3. **Connection Established**: Once the handshake is successful, a WebSocket connection is established. Both the client and server can send and receive data at any time over this connection.
4. **Data Transfer**: Data can be transmitted in both directions with low latency. This bidirectional communication allows real-time updates.
5. **Closure**: The connection remains open until either the client or server decides to close it. The closure can be initiated by either party.

### Advantages

- **Full-Duplex Communication**: WebSockets support simultaneous two-way communication, allowing real-time data exchange with lower latency compared to other methods.
- **Low Overhead**: Once established, WebSocket connections have minimal protocol overhead, reducing the amount of data sent per message compared to HTTP polling techniques.
- **Real-Time Interaction**: Ideal for applications requiring real-time updates, such as live chat applications, online gaming, or financial trading platforms.
- **Better Security**: WebSockets use the same security models as HTTP, including origin-based security.

### Disadvantages

- **Connection Management**: WebSocket connections need to be explicitly managed. If a connection is lost, it must be reestablished manually, which might require additional handling in your application.
- **Browser Support**: While modern browsers generally support WebSockets, older versions may not, which can be a limitation for certain applications.
- **Complexity**: Implementing WebSocket connections and managing their lifecycle can add complexity to the application, especially compared to simpler methods like HTTP polling.

### Use Cases

WebSockets are well-suited for applications that require real-time, interactive communication. Examples include:

- **Live Chat Applications**: WebSockets allow for instant messaging between users.
- **Online Games**: WebSockets enable real-time updates and interactions between players.
- **Financial Trading Platforms**: WebSockets provide real-time data updates and notifications, crucial for trading applications.
- **Collaborative Tools**: Applications like collaborative editing tools benefit from real-time synchronization between users.

For more information on WebSockets, you can refer to the [official WebSocket documentation](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API) and [WebSocket protocol overview](https://tools.ietf.org/html/rfc6455).

---
Here’s an overview of Server-Sent Events (SSE), including how they work, their advantages, and disadvantages:

---

## Server-Sent Events (SSE)

**Server-Sent Events (SSE)** is a standard allowing servers to push updates to the client over a single, long-lived HTTP connection. This method is designed for scenarios where the server needs to send real-time updates to the client without the client having to request them.

![server-sent-events](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/long-polling-websockets-server-sent-events/server-sent-events.png)

### Working

Here’s how SSE operates:

1. **Request**: The client sends an HTTP request to the server with an `Accept: text/event-stream` header.
2. **Connection Establishment**: The server responds with the appropriate headers (`Content-Type: text/event-stream`) and keeps the connection open.
3. **Event Transmission**: The server pushes updates or events to the client over the open connection whenever new data is available.
4. **Client Handling**: The client receives the events and processes them as they arrive.

### Advantages

- **Simplicity**: SSE is straightforward to implement for real-time updates. It builds on existing HTTP infrastructure.
- **Browser Support**: Supported by most modern browsers, making it easy to use in a wide range of web applications.
- **Firewall Compatibility**: Since it uses HTTP/HTTPS, SSE is generally compatible with firewalls and proxies.

### Disadvantages

- **Unidirectional**: SSE is only capable of pushing data from the server to the client. Clients cannot send data back over the same connection, which limits its use cases.
- **Connection Limits**: Some servers and proxies impose limits on the number of open connections, which can affect scalability.
- **Binary Data Limitation**: SSE does not natively support binary data, which may limit its use for applications requiring binary payloads.

### Use Cases

SSE is suitable for applications where real-time updates are required, but bidirectional communication is not necessary. Examples include:

- **Live News Feeds**: Push breaking news updates to users in real-time.
- **Stock Price Updates**: Provide continuous updates on stock prices or financial data.
- **Social Media Notifications**: Send updates or notifications to users as new events happen on their social feeds.

For more detailed information on SSE, you can visit the [MDN Web Docs on Server-Sent Events](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events).

---

# Geohashing and Quadtrees
### Geohashing and Quadtrees: Understanding Spatial Indexing

#### Geohashing: Encoding Geographic Coordinates

**Definition:** Geohashing is a method for converting geographic coordinates (latitude and longitude) into short, alphanumeric strings called geohashes. This technique creates a compact, human-readable representation of a location.

**How it Works:** Geohashing uses a hierarchical grid to divide the world into progressively smaller cells. Each character in the geohash refines the location within the grid. The more characters in the geohash, the more precise the location.

**Benefits:**
- **Simple and Compact:** Easier to store and share than raw latitude and longitude coordinates.
- **Spatial Proximity:** Geohashes with longer shared prefixes indicate locations that are geographically closer, making proximity searches efficient.
- **Anonymity:** Shorter geohashes reveal general areas, providing some privacy.

**Example:** For San Francisco (37.7564, -122.4016), the geohash `9q8yy9mf` represents a precise location, while `9q8` covers a larger region around the city.

**Use Cases:**
- **Database Representation:** Efficiently store and query location data.
- **Social Media Sharing:** Easier to share locations compared to coordinates.
- **Proximity Search:** Quickly find nearby points by comparing geohashes.

**Examples of Geohash Support:**
- [MySQL](https://www.mysql.com)
- [Redis](http://redis.io)
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb)
- [Google Cloud Firestore](https://cloud.google.com/firestore)

---

#### Quadtrees: Efficient Spatial Partitioning

**Definition:** A quadtree is a data structure used to partition a two-dimensional space into quadrants by recursively dividing it into four smaller regions. Each node in the tree represents a quadrant or a set of quadrants.

**Types of Quadtrees:**
- **Point Quadtrees:** Store individual points.
- **Point-Region (PR) Quadtrees:** Associate points with specific regions.
- **Polygonal Map (PM) Quadtrees:** Store complex shapes such as polygons.
- **Compressed Quadtrees:** Optimize storage by only storing non-empty nodes.
- **Edge Quadtrees:** Represent edges (lines) in images.

**Why Use Quadtrees?**
- **Efficient Searches:** Perform range queries to find points within a specific area.
- **Reduced Computation:** Subdivide only necessary areas, avoiding extensive calculations.
- **Performance Optimization:** Techniques like the [Hilbert curve](https://en.wikipedia.org/wiki/Hilbert_curve) improve search efficiency.

**Use Cases:**
- **Image Processing:** Represent and compress images efficiently.
- **Spatial Indexing:** Quickly find points or objects within a geographic region.
- **Location-Based Services:** Power applications like [Google Maps](https://www.google.com/maps) and [Uber](https://www.uber.com).
- **Mesh Generation:** Used in computer graphics for creating detailed meshes.
- **Sparse Data Storage:** Efficiently handle data concentrated in specific regions.

---

**In Summary:**
- **Geohashing** provides a compact and human-friendly way to encode locations, ideal for database storage and proximity searches.
- **Quadtrees** offer efficient spatial indexing and querying, making them suitable for applications involving large datasets and complex spatial operations.
 
### Circuit Breaker and Rate Limiting: Key Concepts for Robust Systems

#### Circuit Breaker: Preventing System Failures

**Definition:** The Circuit Breaker pattern is a design pattern used to detect failures and prevent a failure from continually recurring during maintenance or system issues. It helps to maintain system stability by avoiding cascading failures.

**How it Works:**
1. **Closed State:** Normal operation; all requests pass through. If failures exceed a threshold, the circuit breaker trips to the Open state.
2. **Open State:** Returns errors immediately without invoking the service. After a timeout, it moves to the Half-open state.
3. **Half-open State:** Allows a limited number of requests to pass through. If successful, it returns to the Closed state. If failures continue, it returns to the Open state.

**Benefits:**
- **Prevents Cascading Failures:** Stops further calls to a failing service, preventing overload.
- **Allows Recovery:** Provides time for the service to recover before resuming normal operations.
- **Alerts and Monitoring:** Helps in monitoring the health of the service.

**Example:** If a payment gateway service becomes unresponsive, a circuit breaker can prevent your application from making more payment requests until the service is back online.

**Reference Links:**
- [Circuit Breaker Pattern](https://microservices.io/patterns/circuit-breaker.html)

---

#### Rate Limiting: Controlling Access and Protecting Resources

**Definition:** Rate limiting is a technique used to control the frequency of requests to a service, protecting against overload and abuse.

**Why Rate Limiting?**
- **Prevent Resource Starvation:** Avoid denial-of-service attacks by limiting request rates.
- **Control Costs:** Manage operational costs by controlling resource usage.
- **Mitigate Attacks:** Defend against misuse and overuse of APIs.
- **Regulate Data Flow:** Manage the flow of large amounts of data through APIs.

**Algorithms for Rate Limiting:**
1. **Leaky Bucket:** Requests are processed at a constant rate. Excess requests are discarded if the bucket is full.
   - **Use Case:** Simple rate limiting with predictable request processing.

2. **Token Bucket:** Requests require a token from the bucket. Tokens refill at a set rate.
   - **Use Case:** Allows bursts of traffic up to a limit while maintaining an average rate.

3. **Fixed Window:** Tracks requests within a fixed time window. Requests exceeding the limit are discarded.
   - **Use Case:** Simple to implement but may allow bursts at the boundary of the window.

4. **Sliding Log:** Records timestamps of requests. Calculates the rate based on the logs within a time window.
   - **Use Case:** Provides precise control but can be resource-intensive.

5. **Sliding Window:** Combines fixed window and sliding log approaches. Uses counters with smoothing to handle bursts.
   - **Use Case:** Balances precision and efficiency, handling traffic spikes better.

**Rate Limiting in Distributed Systems:**
- **Inconsistencies:** Global rate limits can be challenging with multiple nodes. Solutions include sticky sessions or centralized data stores like [Redis](https://redis.io).
- **Centralized Stores:** Using tools like Redis can help maintain consistent limits but may introduce latency and race conditions.

**Reference Links:**
- [Rate Limiting Algorithms](https://en.wikipedia.org/wiki/Rate_limiting)
- [Redis for Rate Limiting](https://redis.io/topics/ratelimiter)

---

**Summary:**
- **Circuit Breaker** helps manage system failures by stopping faulty service calls and allowing recovery time.
- **Rate Limiting** controls the frequency of requests to protect resources and ensure system stability.

Both techniques are crucial for designing robust and resilient systems, ensuring they handle failures gracefully and remain performant under load.
### Race Conditions and Service Discovery: Key Concepts

#### Race Conditions: Handling Concurrent Operations

**Definition:** A race condition occurs when multiple processes access and manipulate shared data concurrently, leading to unpredictable results. This is a common issue in systems with concurrent operations, such as rate limiting.

**Problem with "Get-Then-Set":**
- **Naive Approach:** Retrieving a counter value, incrementing it, and storing it back can result in multiple processes reading the same initial value before any process writes the incremented value.
- **Issue:** Additional requests can cause multiple processes to store the incremented value incorrectly, bypassing rate limits.

**Solutions:**
1. **Distributed Locking:** Use a locking mechanism to prevent concurrent access to the counter. This ensures only one process can update the counter at a time.
   - **Drawback:** Can become a bottleneck and may not scale well.

2. **Atomic Operations:** Use atomic operations that combine get and set operations into a single, indivisible action. For example, using an atomic increment operation in a distributed datastore can ensure that the counter is correctly updated.

**Example:** Instead of incrementing a rate limit counter using separate read and write operations, use atomic operations provided by databases or distributed stores like [Redis](https://redis.io) to prevent race conditions.

---

#### Service Discovery: Managing Dynamic Services

**Definition:** Service discovery is the process of detecting and managing services within a network, crucial for microservices architectures where service instances can change dynamically.

**Why Service Discovery is Needed:**
- **Dynamic Environments:** In microservices, services can scale up or down, and their locations can change frequently. Service discovery helps clients locate services without manual updates.

**Service Discovery Patterns:**

1. **Client-Side Discovery:**
   - **How it Works:** Clients query a service registry to obtain the network locations of service instances. The client then directly contacts the service instance.
   - **Diagram:**
     ![Client-Side Service Discovery](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/service-discovery/client-side-service-discovery.png)
   - **Example:** A client uses a registry like [Consul](https://www.consul.io) to find the address of a microservice and then makes a direct request.

2. **Server-Side Discovery:**
   - **How it Works:** Clients make requests to a load balancer or gateway, which queries the service registry and forwards requests to available service instances.
   - **Diagram:**
     ![Server-Side Service Discovery](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/service-discovery/server-side-service-discovery.png)
   - **Example:** A load balancer like [Nginx](https://www.nginx.com) or [HAProxy](http://www.haproxy.org) distributes requests to services based on their availability.

**Service Registry and Registration:**

1. **Service Registry:**
   - **Definition:** A database storing network locations of service instances.
   - **Requirements:** Highly available and frequently updated to reflect changes in service availability.
   - **Examples:** [etcd](https://etcd.io), [Consul](https://www.consul.io), [Apache Zookeeper](https://zookeeper.apache.org).

2. **Service Registration:**
   - **Self-Registration:** Services register and de-register themselves, often sending heartbeat signals to maintain their registration.
   - **Third-Party Registration:** The registry polls or subscribes to events from the deployment environment to track services.

**Service Mesh:**
- **Purpose:** Manages, observes, and secures service-to-service communication within and across clusters.
- **Technologies:** [Istio](https://istio.io/latest/about/service-mesh), [Envoy](https://www.envoyproxy.io).

**Examples of Service Discovery Tools:**
- [etcd](https://etcd.io)
- [Consul](https://www.consul.io)
- [Apache Thrift](https://thrift.apache.org)
- [Apache Zookeeper](https://zookeeper.apache.org)

---

**Summary:**
- **Race Conditions** can disrupt rate limiting and other concurrent processes; solutions include distributed locking and atomic operations.
- **Service Discovery** ensures dynamic service instances are correctly located and managed in microservices architectures, with patterns like client-side and server-side discovery and tools like service registries and service meshes.

### SLA, SLO, and SLI: Key Concepts

#### Why They Are Important

SLAs, SLOs, and SLIs help companies define, track, and manage the quality and reliability of their services. They provide a structured approach to ensuring that service promises are clear, measurable, and achievable, which fosters user trust and aids in continuous improvement.

#### SLA (Service Level Agreement)

**Definition:** 
- An SLA is a formal agreement between a company and its users that outlines the expected level of service. It specifies the commitments the company makes regarding various metrics, such as uptime, response times, and other service quality indicators.

**Purpose:**
- To define the service level expectations and commitments between the service provider and the user.
- To establish legal or business terms related to the service's performance and availability.

**Example:** 
- An SLA might promise 99.9% uptime for a cloud service, guaranteeing that the service will not be down for more than 8.76 hours per year.

---

#### SLO (Service Level Objective)

**Definition:** 
- An SLO is a specific, measurable target set within the framework of an SLA. It details the expected performance level for a particular metric. SLOs are individual promises within the broader SLA.

**Purpose:**
- To set clear, achievable goals for service performance that align with the broader SLA.
- To provide a benchmark for evaluating whether the service provider is meeting the agreed-upon levels.

**Example:** 
- An SLO might specify that a web service should have a response time of less than 200 milliseconds for 95% of user requests.

---

#### SLI (Service Level Indicator)

**Definition:** 
- An SLI is a quantifiable metric used to assess whether the SLOs are being met. It is the actual measurement of the performance characteristic described in the SLO.

**Purpose:**
- To provide a way to measure and track service performance against the defined SLOs.
- To ensure that the service provider meets or exceeds the performance targets set in the SLOs.

**Example:** 
- An SLI might measure the average response time of a web service and report it as 180 milliseconds, which can then be compared against the SLO target of 200 milliseconds.

---

**Summary:**
- **SLA:** A formal agreement detailing overall service promises.
- **SLO:** Specific, measurable targets within the SLA.
- **SLI:** Metrics used to measure if SLOs are being met.

Understanding these concepts helps in managing service quality, setting clear expectations, and maintaining trust with users.

### Disaster Recovery (DR)

**Definition:** Disaster recovery is a process to restore access and functionality of IT infrastructure after a disruptive event such as natural disasters, cyberattacks, or system failures. It involves replicating data and operations to a secondary location to minimize downtime and data loss.

**Importance:**
- **Minimizes Interruption and Downtime:** Ensures business continuity by quickly restoring operations.
- **Limits Damages:** Reduces the impact of disruptions on business operations.
- **Fast Restoration:** Helps in quickly resuming normal operations after a disaster.
- **Better Customer Retention:** Maintains customer trust by minimizing service interruptions.

**Learn More:** [AWS Well-Architected Framework on Disaster Recovery](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/plan-for-disaster-recovery-dr.html)

---

#### Key Terms

**RTO (Recovery Time Objective):**
- **Definition:** The maximum acceptable time that a service can be down before affecting business operations.
- **Purpose:** Sets a target for how quickly services should be restored after an interruption.
- **Example:** If the RTO is 4 hours, the business aims to restore service within 4 hours of disruption.

**RPO (Recovery Point Objective):**
- **Definition:** The maximum acceptable amount of data loss measured in time.
- **Purpose:** Determines the point in time to which data should be recovered.
- **Example:** If the RPO is 1 hour, data should be recoverable up to 1 hour before the disruption.

---

#### DR Strategies

**Backup:**
- **Definition:** Regularly saving copies of data to off-site or removable media.
- **Advantages:** Simple and cost-effective.
- **Disadvantages:** Can lead to data loss if backups are not frequent or if recovery takes time.

**Cold Site:**
- **Definition:** A secondary location with basic infrastructure but no active data or applications.
- **Advantages:** Lower cost and easy to set up.
- **Disadvantages:** Longer recovery time as data and applications need to be restored or set up from scratch.

**Hot Site:**
- **Definition:** A fully equipped secondary site with real-time data replication and ready-to-use infrastructure.
- **Advantages:** Minimal downtime and quick recovery.
- **Disadvantages:** Higher cost due to continuous data replication and maintenance.

---
### Virtual Machines (VMs) and Containers

#### Virtual Machines (VMs)

**Definition:** A Virtual Machine (VM) is a virtualized computer system created on a physical hardware system, with its own virtual CPU, memory, network interface, and storage. VMs are managed by a hypervisor which separates and allocates hardware resources to the VMs.

**Key Components:**
- **Hypervisor:** Software that creates and manages VMs by allocating physical resources (CPU, memory, storage) to them. It can be:
  - **Type 1 Hypervisor (Bare-Metal):** Runs directly on the physical hardware (e.g., VMware ESXi).
  - **Type 2 Hypervisor (Hosted):** Runs on top of a host operating system (e.g., VMware Workstation).
  
**Advantages:**
- **Isolation:** Each VM operates independently, which ensures that applications running inside a VM do not affect the host or other VMs.
- **Resource Utilization:** Allows for server consolidation by running multiple VMs on a single physical server, improving hardware usage.
- **Testing and Production:** Useful for testing new applications or creating isolated production environments.

#### Containers

**Definition:** A container is a lightweight, standalone, and executable package that includes everything needed to run a piece of software, including the code, runtime, system tools, libraries, and settings. Containers abstract applications from the underlying environment, making them portable and consistent.

**Advantages:**
- **Separation of Responsibility:** Developers focus on application logic and dependencies, while operations manage deployment and scaling.
- **Workload Portability:** Containers can run consistently across different environments, simplifying development and deployment.
- **Application Isolation:** Containers provide logical isolation at the OS level, ensuring that applications do not interfere with each other.
- **Agile Development:** Speeds up development by avoiding dependency and environment issues.
- **Efficient Operations:** Containers are resource-efficient and lightweight compared to VMs.

#### Virtualization vs Containerization

**Virtualization:**
- **Mechanism:** Uses a hypervisor to virtualize physical hardware.
- **Components:** Each VM includes a guest OS, virtual hardware, and application with dependencies.
- **Resource Usage:** Higher overhead due to the need for a full OS and virtualized hardware.

**Containerization:**
- **Mechanism:** Virtualizes the OS instead of the hardware.
- **Components:** Each container includes only the application and its dependencies, sharing the host OS kernel.
- **Resource Usage:** Lightweight, using fewer resources compared to VMs, as they do not need a full OS.

![Virtualization vs Containerization](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/virtual-machines-and-containers/virtualization-vs-containerization.png)
### OAuth 2.0 and OpenID Connect (OIDC)

#### OAuth 2.0

**Overview:** OAuth 2.0 is an authorization framework that allows applications to access resources on behalf of a user without needing the user’s credentials. It focuses on authorization rather than authentication.

**Key Concepts:**

- **Resource Owner:** The user or system that owns the data or resources.
- **Client:** The application requesting access to the resources.
- **Authorization Server:** Issues access tokens to the client after successful authentication and consent.
- **Resource Server:** Hosts the resources and validates access tokens.
- **Scopes:** Define the extent of access the client has to the resources.
- **Access Token:** A token representing the client's authorization to access resources.

**How It Works:**

1. The client requests authorization from the Authorization Server, providing client credentials, scopes, and a redirect URI.
2. The Authorization Server authenticates the client and validates the request.
3. The Resource Owner grants access.
4. The Authorization Server responds with an Authorization Code or Access Token.
5. The client uses the Access Token to access resources from the Resource Server.

**Disadvantages:**

- Lacks built-in security features.
- No standard implementation across different providers.
- Scopes can vary, leading to inconsistencies.

![OAuth 2.0 Flow](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/oauth2-and-openid-connect/oauth2.png)

#### OpenID Connect (OIDC)

**Overview:** OpenID Connect is an authentication layer built on top of OAuth 2.0. It provides identity information about the user, in addition to access to resources.

**Key Concepts:**

- **Relying Party:** The application requesting user information.
- **OpenID Provider (IdP):** Issues identity tokens and user information.
- **Token Endpoint:** Accepts the Authorization Code and returns an Access Token (often in JWT format).
- **UserInfo Endpoint:** Provides user profile information based on the Access Token.

**Differences from OAuth 2.0:**

- OIDC adds an identity layer for user authentication.
- Uses JSON Web Tokens (JWT) for tokens, enhancing security and interoperability.
- Provides additional endpoints like UserInfo for retrieving user data.

**Benefits:**

- Provides authentication (who is the user) in addition to authorization.
- Standardized user identity and profile information retrieval.
- Integrates seamlessly with OAuth 2.0 for comprehensive security solutions.

Both OAuth 2.0 and OIDC are widely used in modern applications for secure and flexible authorization and authentication.
### Single Sign-On (SSO)

**Overview:** Single Sign-On (SSO) is an authentication process that allows users to access multiple applications with a single set of credentials. This reduces the need for multiple logins and enhances user convenience.

**Key Components:**

- **Identity Provider (IdP):** Centralized system managing user identities and authentication. It authenticates users and provides access to service providers.
- **Service Provider:** Provides services to the user and relies on the IdP to authenticate and authorize users.
- **Identity Broker:** Acts as an intermediary connecting multiple IdPs and service providers, facilitating SSO across different systems.

**SAML:**

- **Security Assertion Markup Language (SAML)** is an XML-based standard for exchanging authentication and authorization data between parties, particularly between an IdP and a service provider.
- SAML enables identity federation, allowing IdPs to pass authenticated identities and attributes to service providers seamlessly.

**How SSO Works:**

1. User requests a resource from an application.
2. The application redirects the user to the IdP for authentication.
3. User signs in with credentials (username and password).
4. The IdP sends an SSO response to the application.
5. The application grants access based on the SSO response.

![SSO Flow](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/single-sign-on/sso.png)

**SAML vs OAuth 2.0 and OpenID Connect (OIDC):**

- **SAML** uses XML and is geared towards enterprise security. It is suited for web-based applications with complex authentication needs.
- **OAuth 2.0** is an authorization framework for granting access to resources. It does not handle authentication but allows third-party access to user resources.
- **OIDC** builds on OAuth 2.0 to add authentication, providing user identity and profile information. It uses JSON and is more suited for modern web and mobile applications.

**Advantages of SSO:**

- **User Convenience:** Single set of credentials simplifies login processes.
- **Access Efficiency:** Faster access to multiple applications without repeated logins.
- **Security:** Centralized management enhances security and compliance.
- **Reduced Admin Costs:** Decreases IT support and administration time.

**Disadvantages of SSO:**

- **Single Point of Failure:** Compromise of SSO credentials can lead to access issues across all linked applications.
- **Performance:** Authentication may be slower due to the need for SSO verification.

**Popular Identity Providers (IdP):**

- [Okta](https://www.okta.com)
- [Google](https://cloud.google.com/architecture/identity/single-sign-on)
- [Auth0](https://auth0.com)
- [OneLogin](https://www.onelogin.com)

### SSL, TLS, and mTLS

**SSL (Secure Sockets Layer)**

- **Definition:** SSL is an outdated protocol for encrypting internet communications, first developed in 1995. It has been deprecated in favor of TLS.
- **Purpose:** SSL was created to protect user privacy and data integrity by encrypting communications between a user and a web server.
- **Current Usage:** The term "SSL certificate" persists in common usage, though SSL itself is no longer used.

**TLS (Transport Layer Security)**

- **Definition:** TLS is the successor to SSL and provides secure communication over the internet. It evolved from SSL to offer improved security and performance.
- **Components:**
  - **Encryption:** Protects data from being read by unauthorized parties.
  - **Authentication:** Ensures the identities of the parties involved in the communication.
  - **Integrity:** Verifies that the data has not been altered in transit.
- **Versions:** TLS has several versions, with TLS 1.2 and TLS 1.3 being the most commonly used today.

**mTLS (Mutual TLS)**

- **Definition:** mTLS is an extension of TLS that adds mutual authentication, requiring both parties (client and server) to verify each other's identities using certificates.
- **Purpose:** Provides an additional layer of security by ensuring that both ends of the connection are authenticated, enhancing trust and security.
- **Usage:** Commonly used in environments requiring high security, such as microservices, distributed systems, and IoT devices. It's integral to zero trust security models.

### Key Differences

- **SSL vs. TLS:** TLS is a more secure and updated protocol compared to SSL. SSL is outdated and has been replaced by TLS, though the term "SSL certificate" is still used.
- **TLS vs. mTLS:** While TLS provides encryption, authentication, and data integrity for one-way communication (server to client), mTLS adds mutual authentication for both ends of the connection, offering higher security.

Understanding these protocols is beneficial for designing secure systems, even though they might not be central to every system design interview.


### Detailed Guide to System Design Interviews

System design interviews assess your ability to create scalable, efficient, and maintainable systems. Here’s a step-by-step guide to help you prepare and excel in these interviews:

#### 1. **Requirements Clarifications**

##### **Functional Requirements**
These are the core functionalities that your system must provide to meet user needs. They define what the system should do.

- **Examples:**
  - **User Management:** Sign up, login, profile management.
  - **Data Storage:** CRUD operations for data entities.
  - **Search Functionality:** Full-text search, filtering, sorting.

- **Questions to Ask:**
  - “What are the primary features of this system?”
  - “Are there any specific business rules or use cases we should consider?”
  - “What are the expected user interactions and workflows?”

##### **Non-Functional Requirements**
These define the quality attributes of the system, such as performance, scalability, and security. They are not directly related to specific features but to the overall user experience and system performance.

- **Examples:**
  - **Performance:** Latency should be less than 100ms for API responses.
  - **Scalability:** The system should handle up to 10,000 concurrent users.
  - **Availability:** The system should have 99.99% uptime.

- **Questions to Ask:**
  - “What are the performance requirements?”
  - “What are the uptime and availability expectations?”
  - “Are there specific security considerations we need to address?”

##### **Extended Requirements**
These are additional features or considerations that are desirable but not essential.

- **Examples:**
  - **Analytics:** Collecting and analyzing user behavior data.
  - **Monitoring:** Health checks and logging for system performance.
  - **Internationalization:** Support for multiple languages.

- **Questions to Ask:**
  - “Are there any analytics or monitoring requirements?”
  - “Do we need to support multiple languages or regions?”

#### 2. **Estimation and Constraints**

Estimate the scale of the system to guide design decisions. Understanding scale helps in making informed choices about architecture, database design, and performance optimizations.

- **Questions to Ask:**
  - “What is the estimated number of users or requests per second?”
  - “What is the expected data volume and growth rate?”
  - “What is the read/write ratio of the system?”
  - “Are there peak times or high traffic scenarios we need to plan for?”

#### 3. **Data Model Design**

Designing the database schema involves defining entities, their relationships, and how data is stored and accessed. This step is crucial for understanding data flow and ensuring efficient data operations.

- **Questions to Address:**
  - **Entities and Relationships:** Identify core entities (e.g., users, orders, products) and their relationships (e.g., one-to-many, many-to-many).
  - **Schema Design:** Define tables, fields, and indexes. Consider normalization and denormalization based on the use case.
  - **SQL vs. NoSQL:** Choose the database type based on requirements (e.g., relational databases for structured data, NoSQL for unstructured or semi-structured data).

- **Example Schema Design:**
  ```sql
  CREATE TABLE Users (
      user_id INT PRIMARY KEY,
      username VARCHAR(50),
      email VARCHAR(100),
      password_hash VARCHAR(255)
  );

  CREATE TABLE Orders (
      order_id INT PRIMARY KEY,
      user_id INT,
      order_date TIMESTAMP,
      FOREIGN KEY (user_id) REFERENCES Users(user_id)
  );
  ```

#### 4. **API Design**

Define the APIs that will interact with your system. This includes specifying endpoints, request/response formats, and error handling.

- **Example API Design:**
  ```typescript
  // API to create a new user
  POST /users
  Request Body: {
      username: string,
      email: string,
      password: string
  }
  Response: {
      user_id: number,
      username: string,
      email: string
  }
  ```

- **Questions to Consider:**
  - “What are the main API endpoints and their responsibilities?”
  - “What are the request and response formats?”
  - “How will we handle errors and edge cases?”

#### 5. **High-Level Component Design**

Identify and design the major components of your system, such as servers, load balancers, and databases. Create a high-level architecture diagram to visualize how these components interact.

- **Components to Consider:**
  - **Load Balancer:** Distributes incoming requests across multiple servers.
  - **API Gateway:** Manages API requests, provides routing, and handles authentication.
  - **Microservices:** Breaks down the system into smaller, independent services.

- **Questions to Explore:**
  - “Should we use a monolithic or microservices architecture?”
  - “What type of load balancing and caching strategies will be used?”
  - “How will data be partitioned and replicated?”

#### 6. **Detailed Design**

Dive into the specifics of major components, discussing how they will be implemented and integrated. This is where you demonstrate your technical expertise and understanding of best practices.

- **Questions to Address:**
  - “How will we implement data partitioning and replication?”
  - “What caching strategies will we use to improve performance?”
  - “How will we handle data consistency and availability?”

- **Example Caching Strategy:**
  - Use an in-memory cache (e.g., Redis) for frequently accessed data to reduce database load and improve response times.

#### 7. **Identify and Resolve Bottlenecks**

Discuss potential performance bottlenecks and how to address them. Consider scalability, reliability, and robustness of the system.

- **Questions to Address:**
  - “Are there any single points of failure in the system?”
  - “How can we scale the system to handle increased traffic?”
  - “What strategies will we use for load distribution and fault tolerance?”

- **Example Bottleneck Resolution:**
  - Implement database sharding to distribute data across multiple servers and reduce load on a single database.

### Additional Tips

- **Be Humble:** Acknowledge what you know and what you don’t. Use your knowledge and experience to navigate the discussion.
- **Company Research:** Understand the company’s technology stack and focus areas. Review their engineering blog or recent tech articles for insights.

This comprehensive approach will help you tackle system design interviews effectively, demonstrating your ability to design robust, scalable systems.
### Designing a URL Shortener

Designing a URL shortener involves creating a system that efficiently handles a large volume of short URL requests and redirections. Here’s a detailed approach to designing such a system.

---

### **Requirements**

#### **Functional Requirements**

1. **Short URL Generation:**
   - Generate a unique, short alias for a given long URL.
   
2. **Redirection:**
   - Redirect users from the short URL to the original long URL.
   
3. **Link Expiration:**
   - Allow URLs to expire after a configurable timespan.

#### **Non-Functional Requirements**

1. **High Availability:**
   - The system should be available 24/7 with minimal downtime.
   
2. **Scalability:**
   - The system should handle increased traffic efficiently, both in terms of read and write operations.

#### **Extended Requirements**

1. **Abuse Prevention:**
   - Implement mechanisms to detect and prevent misuse of the service (e.g., spam or malicious links).
   
2. **Analytics:**
   - Track and record metrics such as the number of times a short URL is accessed.

---

### **Estimation and Constraints**

#### **Traffic Estimation**

- **Reads/Writes per Month:**
  - **Reads:** 10 billion per month
  - **Writes:** 100 million per month

- **Requests Per Second (RPS):**
  - **Writes:** ~40 RPS (100 million requests per month)
  - **Reads (Redirections):** ~4000 RPS (4K URLs/second)

#### **Bandwidth**

- **Incoming Bandwidth:**
  - 20 KB/second for write requests

- **Outgoing Bandwidth:**
  - ~2 MB/second for read requests (assuming each redirection requires 500 bytes of data)

#### **Storage**

- **Total Storage:**
  - 6 TB (for storing 12 billion records over 10 years)

#### **Cache**

- **Daily Cache Needs:**
  - 35 GB/day (caching 20% of the 4K read requests per second)

---

### **System Design Approach**

#### **1. **High-Level Architecture**

1. **Client Requests:**
   - Users send requests to shorten URLs or access short URLs.

2. **API Gateway:**
   - Routes requests to the appropriate service (shortening or redirection).

3. **Shortening Service:**
   - Handles URL shortening logic.
   - Generates unique short codes and stores mappings in the database.

4. **Redirection Service:**
   - Handles redirection requests.
   - Retrieves the original URL from the database using the short code.

5. **Database:**
   - Stores URL mappings, metadata, and expiration information.

6. **Cache:**
   - Caches frequently accessed short URLs to reduce database load.

7. **Analytics Service:**
   - Collects and processes data on URL usage and performance metrics.

8. **Monitoring and Logging:**
   - Monitors system health, performance, and logs errors or anomalies.

#### **2. **Detailed Component Design**

1. **Shortening Algorithm:**
   - **Hashing:** Use hash functions or base62 encoding to generate unique short codes.
   - **Collision Handling:** Implement checks or use a collision-resistant algorithm to ensure uniqueness.

2. **Database Design:**
   - **Schema Example:**
     ```sql
     CREATE TABLE UrlMappings (
         short_url VARCHAR(10) PRIMARY KEY,
         original_url TEXT NOT NULL,
         creation_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
         expiration_date TIMESTAMP
     );
     ```

3. **Caching Strategy:**
   - Use an in-memory cache (e.g., Redis) to store frequently accessed short URL mappings.
   - Implement cache expiration policies to ensure freshness of data.

4. **Redirection Logic:**
   - Efficiently map short URLs to long URLs and handle redirections.
   - Ensure low latency in fetching and redirecting URLs.

5. **Analytics Collection:**
   - Track metrics like click counts, geographical location of users, and timestamp of access.
   - Store aggregated data for reporting and analysis.

6. **Abuse Prevention:**
   - Implement rate limiting, spam detection, and validation checks.
   - Monitor for suspicious activities and take corrective actions.

#### **3. **Scalability and High Availability**

1. **Load Balancing:**
   - Distribute incoming traffic across multiple instances of the shortener and redirection services.

2. **Database Sharding:**
   - Distribute the database across multiple servers to handle large volumes of data and requests.

3. **Replication:**
   - Use database replication to ensure data redundancy and high availability.

4. **Failover Mechanisms:**
   - Implement failover strategies to handle hardware or software failures and maintain service availability.

---

### **Example API Design**

1. **Shorten URL API:**
   ```http
   POST /shorten
   Request Body: {
       "long_url": "https://example.com/very-long-url"
   }
   Response: {
       "short_url": "https://short.ly/abcd1234"
   }
   ```

2. **Redirection API:**
   ```http
   GET /{short_url}
   Response: {
       "redirect_url": "https://example.com/very-long-url"
   }
   ```

---

### **Conclusion**

Designing a URL shortener requires a thoughtful approach to handling high traffic, ensuring scalability, and maintaining system performance. By focusing on key aspects such as URL shortening algorithms, database design, caching, and high availability, you can build a robust and efficient URL shortener service.

### Data Model Design for URL Shortener

#### **Database Schema**

The database schema for the URL shortener can be divided into two main tables:

1. **Users Table:**
   - **Purpose:** Store user details who are creating and managing short URLs.
   - **Columns:**
     - `userID`: Unique identifier for the user (Primary Key).
     - `name`: Name of the user.
     - `email`: Email of the user.
     - `createdAt`: Timestamp when the user was created.

2. **URLs Table:**
   - **Purpose:** Store the details of each short URL.
   - **Columns:**
     - `shortURLID`: Unique identifier for each short URL (Primary Key).
     - `hash`: Short URL identifier (unique, indexed for performance).
     - `originalURL`: The original long URL.
     - `expiration`: Expiration date of the short URL (optional).
     - `userID`: Foreign key linking to the `users` table to identify the creator.

**Schema Example:**

```sql
CREATE TABLE Users (
    userID INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE URLs (
    shortURLID INT AUTO_INCREMENT PRIMARY KEY,
    hash VARCHAR(8) UNIQUE NOT NULL,
    originalURL TEXT NOT NULL,
    expiration TIMESTAMP,
    userID INT,
    FOREIGN KEY (userID) REFERENCES Users(userID)
);
```

#### **Database Choice**

**NoSQL Databases:**

- **Amazon DynamoDB:**
  - **Advantages:** High performance, scalable, fully managed.
  - **Use Case:** Suitable for handling large amounts of data with fast read and write operations.

- **Apache Cassandra:**
  - **Advantages:** Scalable, high availability, distributed database.
  - **Use Case:** Good for applications requiring high write throughput and availability.

- **MongoDB:**
  - **Advantages:** Flexible schema design, high performance.
  - **Use Case:** Ideal for scenarios with evolving data models and high read/write operations.

**SQL Databases:**

- **Azure SQL Database:**
  - **Advantages:** Managed service, good integration with other Azure services.
  - **Use Case:** Suitable if strong relational data consistency is needed.

- **Amazon RDS:**
  - **Advantages:** Managed relational database service, supports multiple SQL database engines.
  - **Use Case:** Good for applications requiring structured data with complex queries.

### API Design for URL Shortener

#### **1. Create URL**

**Description:** Generates a new short URL for a given long URL.

**Endpoint:** `POST /createURL`

**Request Example:**

```json
{
  "apiKey": "your-api-key",
  "originalURL": "https://example.com/very-long-url",
  "expiration": "2024-12-31T23:59:59Z"
}
```

**Response Example:**

```json
{
  "shortURL": "https://short.ly/abcd1234"
}
```

**Parameters:**
- `apiKey` (string): API key for authentication.
- `originalURL` (string): The long URL to shorten.
- `expiration` (Date, optional): When the short URL should expire.

**Returns:**
- `shortURL` (string): The newly created short URL.

#### **2. Get URL**

**Description:** Retrieves the original long URL from a short URL.

**Endpoint:** `GET /getURL`

**Request Example:**

```json
{
  "apiKey": "your-api-key",
  "shortURL": "https://short.ly/abcd1234"
}
```

**Response Example:**

```json
{
  "originalURL": "https://example.com/very-long-url"
}
```

**Parameters:**
- `apiKey` (string): API key for authentication.
- `shortURL` (string): The short URL to look up.

**Returns:**
- `originalURL` (string): The original long URL.

#### **3. Delete URL**

**Description:** Deletes a short URL from the system.

**Endpoint:** `DELETE /deleteURL`

**Request Example:**

```json
{
  "apiKey": "your-api-key",
  "shortURL": "https://short.ly/abcd1234"
}
```

**Response Example:**

```json
{
  "result": true
}
```

**Parameters:**
- `apiKey` (string): API key for authentication.
- `shortURL` (string): The short URL to delete.

**Returns:**
- `result` (boolean): Indicates whether the deletion was successful.

#### **Why Use an API Key?**

An API key:
- **Prevents Abuse:** Limits the number of requests from each user to prevent overuse or misuse.
- **Controls Access:** Helps in identifying and managing users of the service.
- **Rate Limiting:** Allows setting limits on the number of requests per second or minute to protect the service from being overwhelmed.

### Summary

The URL shortener system involves creating and managing a scalable and efficient database to store user and URL data. The API design provides clear endpoints for creating, retrieving, and deleting short URLs while ensuring secure and controlled access through API keys. Choosing the right database (SQL vs NoSQL) depends on the specific requirements and expected data handling needs.
### URL Shortener: Detailed Overview

**Definition:**
A URL shortener is a service that transforms a long URL into a shorter, more manageable one. This short URL redirects users to the original long URL. The primary use cases include simplifying URLs for sharing and tracking link analytics.

### Key Components and Design

#### 1. **URL Encoding**

**Definition:**
URL encoding is the process of converting a long URL into a shorter, unique identifier using an encoding scheme. This helps to ensure that the shortened URL is compact and easy to share.

**Approaches:**

1. **Base62 Encoding:**
   - **Definition:** Base62 encoding uses 62 characters (A-Z, a-z, 0-9) to represent numbers. This allows for a large number of unique short URLs.
   - **Advantages:**
     - Simple and easy to implement.
     - Scales well with the number of characters used.
   - **Disadvantages:**
     - Doesn't guarantee uniqueness; collisions can occur.
     - Limited by the length of the generated key.

2. **MD5 Hashing:**
   - **Definition:** MD5 is a hash function that produces a 128-bit hash value, which can be converted to a shorter URL. MD5 is widely used for hashing data.
   - **Advantages:**
     - Produces a fixed-length output, regardless of input size.
   - **Disadvantages:**
     - Hash collisions can occur, leading to duplicate short URLs.
     - Computational overhead and potential security vulnerabilities (MD5 is not cryptographically secure).

3. **Counter-Based Approach:**
   - **Definition:** A counter-based approach uses an incrementing counter to generate unique IDs for URLs. These IDs are then encoded into a short URL.
   - **Advantages:**
     - Ensures uniqueness as long as the counter is properly managed.
   - **Disadvantages:**
     - Can become a single point of failure.
     - Requires a distributed counter to handle high traffic and avoid collisions.

#### 2. **Key Generation Service (KGS)**

**Definition:**
A Key Generation Service is responsible for creating unique keys used in short URLs. It ensures that each key is unique and manages key assignment.

**Advantages:**
- Centralizes key generation and management.
- Reduces the risk of key duplication.

**Disadvantages:**
- Can become a bottleneck if not properly scaled.
- Needs to handle high concurrency and prevent race conditions.

#### 3. **Caching**

**Definition:**
Caching involves storing frequently accessed data in memory to reduce latency and improve response times. In the context of URL shorteners, caching helps to quickly resolve short URLs to their original counterparts.

**Advantages:**
- Reduces database load and improves performance.
- Provides faster access to frequently requested data.

**Disadvantages:**
- Adds complexity to the system.
- Cache invalidation and consistency need to be managed carefully.

#### 4. **High-Level System Design**

**Components:**

1. **API Server:**
   - **Role:** Handles incoming requests for creating, retrieving, and deleting URLs.
   - **Advantages:** Centralized point for handling user interactions.
   - **Disadvantages:** Needs to be highly scalable to handle high traffic.

2. **Database:**
   - **Role:** Stores the mappings between short URLs and original URLs, as well as user data.
   - **Advantages:** Persistent storage for URLs and user information.
   - **Disadvantages:** Database performance and scalability can be challenging with high traffic.

3. **Key Generation Service (KGS):**
   - **Role:** Generates unique keys for short URLs.
   - **Advantages:** Ensures uniqueness and avoids collisions.
   - **Disadvantages:** Requires robust management to handle high demand.

4. **Cache:**
   - **Role:** Stores frequently accessed URL mappings to reduce latency.
   - **Advantages:** Improves performance by reducing database load.
   - **Disadvantages:** Needs to be managed to ensure data consistency.

**Workflow:**

1. **Creating a Short URL:**
   - User requests a short URL for a long URL.
   - API server requests a unique key from KGS.
   - KGS provides a key, which is used to create a short URL.
   - The short URL and its mapping are stored in the database and cache.

2. **Accessing a Short URL:**
   - User accesses a short URL.
   - API server checks the cache for the URL mapping.
   - If not found in the cache, the server retrieves it from the database.
   - The user is redirected to the original URL or receives a 404 error if the URL is not found.

**Advantages:**
- Simplifies long URLs for easier sharing and tracking.
- Provides analytics and metrics for URL usage.

**Disadvantages:**
- Potential for abuse and misuse (e.g., spamming).
- Requires ongoing maintenance and scaling to handle traffic and data growth.

This detailed breakdown covers the core concepts, advantages, and disadvantages of designing and implementing a URL shortener. If you need more specific details or have further questions, feel free to ask!

### Detailed Design of URL Shortener

In this detailed design overview, we’ll cover advanced aspects of the URL shortener system, including data partitioning, database cleanup strategies, caching mechanisms, metrics and analytics, and security considerations. We'll also discuss how to identify and resolve bottlenecks to ensure a robust and scalable system.

#### 1. **Data Partitioning**

**Definition:**
Data partitioning (or sharding) involves dividing a database into smaller, more manageable pieces. This helps in scaling out the system by distributing data across multiple servers or nodes.

**Partitioning Schemes:**

- **Hash-Based Partitioning:**
  - **Definition:** Data is distributed across partitions based on a hash function applied to a key (e.g., user ID).
  - **Advantages:** Even distribution of data; straightforward implementation.
  - **Disadvantages:** Rebalancing can be complex if partitions need to be added or removed.

- **List-Based Partitioning:**
  - **Definition:** Data is distributed based on predefined ranges or lists (e.g., user regions).
  - **Advantages:** Simple for cases with clear categorical distributions.
  - **Disadvantages:** May lead to uneven data distribution if the list items have skewed data sizes.

- **Range-Based Partitioning:**
  - **Definition:** Data is divided based on ranges of values (e.g., timestamp ranges).
  - **Advantages:** Useful for time-series data; efficient for range queries.
  - **Disadvantages:** May lead to uneven partitions if data distribution is not uniform.

- **Composite Partitioning:**
  - **Definition:** Combines multiple partitioning schemes, such as hash and range.
  - **Advantages:** More flexible and can address multiple use cases.
  - **Disadvantages:** More complex to implement and manage.

- **Consistent Hashing:**
  - **Definition:** A technique to distribute data across a cluster of nodes in a way that minimizes reorganization when nodes are added or removed.
  - **Advantages:** Reduces rebalancing overhead and improves load distribution.
  - **Disadvantages:** Complexity in implementation and management.

#### 2. **Database Cleanup**

**Definition:**
Database cleanup involves removing expired or outdated entries from the database to maintain performance and manage storage.

- **Active Cleanup:**
  - **Definition:** A separate cleanup service periodically removes expired entries.
  - **Advantages:** Ensures timely removal of obsolete data; predictable cleanup intervals.
  - **Disadvantages:** Additional processing overhead; requires scheduling and maintenance.

- **Passive Cleanup:**
  - **Definition:** Entries are removed upon access if they are found to be expired.
  - **Advantages:** Lazy approach that reduces processing overhead.
  - **Disadvantages:** Expired entries might remain in the database longer; less predictable.

#### 3. **Cache**

**Definition:**
Caching stores frequently accessed data in memory to speed up retrieval and reduce load on the database.

- **Cache Eviction Policy:**
  - **Least Recently Used (LRU):**
    - **Definition:** Removes the least recently accessed items first.
    - **Advantages:** Simple and effective for scenarios where recent items are likely to be accessed again.
    - **Disadvantages:** May not always reflect actual data usage patterns; can be complex to implement with large data sets.

- **Handling Cache Misses:**
  - **Definition:** When data is not found in the cache, it’s fetched from the database and then added to the cache.
  - **Advantages:** Ensures that cache remains updated with frequently accessed data.
  - **Disadvantages:** Increased load on the database; potential for cache staleness.

#### 4. **Metrics and Analytics**

**Definition:**
Metrics and analytics involve collecting and analyzing data related to URL usage, such as access counts, user demographics, and performance.

- **Advantages:**
  - Provides insights into user behavior and system performance.
  - Helps in optimizing the system and making data-driven decisions.

- **Disadvantages:**
  - Requires additional storage and processing.
  - Ensuring data privacy and security can be complex.

#### 5. **Security**

**Definition:**
Security measures protect the URL shortener service from unauthorized access and misuse.

- **Private URLs and Authorization:**
  - **Definition:** Restrict access to URLs based on user permissions.
  - **Advantages:** Enhances security and controls access.
  - **Disadvantages:** Adds complexity to the system; requires user authentication mechanisms.

- **API Gateway:**
  - **Definition:** A service that handles routing, authorization, and rate limiting for APIs.
  - **Advantages:** Simplifies API management; provides built-in security features.
  - **Disadvantages:** Can become a single point of failure; additional cost and complexity.

#### 6. **Identifying and Resolving Bottlenecks**

**Potential Bottlenecks:**

- **API Service or Key Generation Service Crashes:**
  - **Solution:** Deploy multiple instances of these services and use load balancers to distribute traffic.

- **Traffic Distribution:**
  - **Solution:** Implement load balancers to distribute requests evenly across servers and services.

- **Database Load:**
  - **Solution:** Use read replicas to handle read-heavy operations; optimize queries and indexing.

- **Key Database Failure:**
  - **Solution:** Implement a standby replica for failover and ensure high availability.

- **Cache Availability:**
  - **Solution:** Use multiple instances and replicas of the cache to ensure redundancy and high availability.

**Advanced Design Overview:**

1. **Multiple Instances and Load Balancers:**
   - **Definition:** Deploy multiple instances of servers and use load balancers to manage traffic.
   - **Advantages:** Enhances scalability and fault tolerance.
   - **Disadvantages:** Increased complexity in managing and configuring multiple instances.

2. **Read Replicas for Database:**
   - **Definition:** Use read replicas to handle read operations separately from write operations.
   - **Advantages:** Improves read performance and reduces load on the primary database.
   - **Disadvantages:** Requires synchronization between replicas and primary database.

3. **Distributed Cache Instances:**
   - **Definition:** Implement multiple instances and replicas of the cache to ensure availability and performance.
   - **Advantages:** Provides redundancy and improves cache performance.
   - **Disadvantages:** Adds complexity in managing cache consistency and replication.

This detailed design covers the critical aspects of building and maintaining a scalable and robust URL shortener system. Understanding and addressing these components will help in creating a system that is both efficient and resilient.

### WhatsApp System Design

Building a system like WhatsApp involves several core components and design principles to ensure it supports billions of users, with the scalability, availability, and efficiency required. Let's break it down:

## Functional Overview

1. **One-on-one chat**: Support for direct messaging between two users.
2. **Group chats**: Allow multiple users (up to 100) to participate in a conversation.
3. **File sharing**: Support for image, video, and other file sharing.

## Non-functional Overview

1. **High Availability**: The system must remain available at all times with minimal downtime.
2. **Scalability**: The system must scale to accommodate billions of users with a dynamic increase in traffic.
3. **Minimal Latency**: Deliver messages in real-time with low response times.
4. **Durability**: Ensures messages and media are persistently stored and not lost.

## Extended Features

- **Receipts**: Sent, delivered, and read indicators for messages.
- **Last Seen**: Display the last active time of users.
- **Push Notifications**: Inform users about new messages and other updates.

---

## Estimations and Constraints

### Traffic

- **50M Daily Active Users (DAU)**, sending **40 messages per day each**.
- **Total Messages**: 2 billion messages per day.
- **Media Files**: 5% of messages are media (100M media files per day).

### Requests Per Second (RPS)
- Approx. 24K messages per second: 
  \[
  \frac{2B \space messages}{24 \space hours \times 3600 \space seconds} \approx 24K/s
  \]

### Storage
- **Message Storage**: 200GB of message data per day (assuming each message is ~100 bytes).
- **Media Storage**: 10TB of media storage per day (assuming each media file is ~100KB).
- **10-Year Estimate**: Total storage of ~38 PB.
  
### Bandwidth
- **10.2TB of data per day** requires about 120MB/sec of bandwidth.

---

## Data Model Design

### Tables Overview

1. **Users**: Stores user information (`userID`, `phoneNumber`, etc.).
2. **Messages**: Stores messages (`messageID`, `type`, `content`, `timestamp`, etc.).
3. **Chats**: Represents private conversations between two users (`chatID`, `lastMessage`, etc.).
4. **Users_Chats**: Maps users to chats (many-to-many relationship).
5. **Groups**: Represents group conversations (`groupID`, `groupName`, etc.).
6. **Users_Groups**: Maps users to groups (many-to-many relationship).

---

### Database Choice

- **Relational Database (PostgreSQL)** for structured data (users, chats, groups).
- **NoSQL (Cassandra)** for handling massive scale and distributed nature (messages, media storage).
- **Media Storage**: A separate storage solution like **Amazon S3** or **Google Cloud Storage** for media files.

---

## API Design

1. **Get All Chats/Groups**: Retrieve all chat or group IDs for a user.
   ```tsx
   getAll(userID: UUID): Chat[] | Group[]
   ```

2. **Get Messages**: Retrieve all messages for a chat or group.
   ```tsx
   getMessages(userID: UUID, channelID: UUID): Message[]
   ```

3. **Send Message**: Send a message from a user to a chat or group.
   ```tsx
   sendMessage(userID: UUID, channelID: UUID, message: Message): boolean
   ```

4. **Join/Leave Group**: Add or remove a user from a group.
   ```tsx
   joinGroup(userID: UUID, groupID: UUID): boolean
   leaveGroup(userID: UUID, groupID: UUID): boolean
   ```

---

## Core Components

1. **Real-time Communication**: Leverage **WebSockets** for maintaining long-lived connections between clients and servers for real-time message delivery.
2. **Message Queue**: Use a distributed messaging system like **Apache Kafka** to handle messaging traffic and ensure durability.
3. **Caching Layer**: Use **Redis** or **Memcached** for quick lookups (e.g., user status, last seen).
4. **Load Balancing**: Distribute incoming traffic efficiently across multiple servers using **load balancers** (e.g., Nginx, HAProxy).
5. **File Storage**: Media files can be stored on a distributed storage solution like **Amazon S3** or **Google Cloud Storage**.

---

## Advanced Features

1. **Message Delivery Status**: 
   - Track message delivery with different statuses: Sent, Delivered, Read.
   - Can be stored as metadata in the **messages** table.

2. **Last Seen and Online Status**: 
   - Use a combination of database and **Redis** for storing and updating users' online presence.

3. **Push Notifications**:
   - Integrate with **Apple Push Notification Service (APNS)** and **Firebase Cloud Messaging (FCM)** for sending push notifications on mobile.

---

## Scaling and Bottlenecks

To handle scaling and avoid bottlenecks:

1. **Multiple Instances**: Run multiple instances of services (message servers, WebSocket servers).
2. **Load Balancers**: Use load balancers to distribute traffic evenly across servers.
3. **Sharding**: Partition users across different databases based on user ID (hash-based partitioning) to prevent any single database from becoming a bottleneck.
4. **Replication**: Use **read replicas** to distribute read traffic in the database and ensure high availability.
5. **Backup Solutions**: Implement automatic backup and recovery strategies for message data and media.

By addressing these key considerations, we can ensure WhatsApp-like systems scale effectively, perform well under heavy loads, and provide users with real-time messaging.
## High-level design

To design a scalable and efficient WhatsApp-like service, we'll break down the system into microservices, each with a clear responsibility. Here's an overview of our architecture and design choices for key features.

### Architecture

We will adopt a **microservices architecture**, which allows for independent scalability and efficient management of different functionalities. Each service will have its own data store and API. Here are the core services:

1. **User Service**: Handles user authentication, registration, and profile management.
2. **Chat Service**: Manages one-on-one and group chats, including real-time messaging using WebSockets.
3. **Notification Service**: Sends notifications when users receive messages or updates.
4. **Presence Service**: Tracks the online status and last seen time for users.
5. **Media Service**: Handles file uploads and media content, such as images and videos.
6. **Message Queue**: Ensures ordered delivery of messages and manages notifications.
7. **Cache**: Using Redis or Memcached for tracking online users and presence status.

Each of these services will communicate via **gRPC** or **HTTP** for efficient, lightweight inter-service communication.

### Real-time Messaging: WebSockets vs Long Polling

We will use **WebSockets** to handle real-time communication for chat messages. WebSockets provide full-duplex communication, making them ideal for real-time applications where low latency and bidirectional communication are essential. Clients will establish a persistent connection with the server, which allows immediate message delivery when a new message is available.

In contrast, long polling would create additional load and latency, as clients repeatedly request updates from the server even when there are no new messages.

### Presence Service and Last Seen

The **Presence Service** will track whether users are online, along with their last seen timestamp. We will implement two strategies:

1. **Heartbeat Mechanism**: The client will send a ping to the server every few seconds, confirming the user is still online. This is low-overhead and gives an accurate reflection of online status.
2. **Lazy Update**: We can track user activity (e.g., message sent, chat opened) and mark users as inactive if they haven’t performed any action within a defined window (e.g., 30 seconds).

We will store the online status and last seen data in a **Redis** or **Memcached** cache for fast access.

### Notifications

When a user receives a message and is not online, the **Notification Service** will send push notifications using a **Message Queue** (e.g., Amazon SQS, RabbitMQ). The queue allows us to decouple the notification process from the main chat service, reducing delays.

- **Message Queue**: Ensures that notifications are processed in the correct order and reliably delivered at least once.
- **Firebase Cloud Messaging (FCM)** or **Apple Push Notification Service (APNS)** will deliver the notifications depending on the user’s device.

The flow is as follows:
1. The **Chat Service** adds a notification event to the message queue when a message is sent.
2. The **Notification Service** consumes this event and sends the notification via FCM or APNS based on the device type.

### Read Receipts and Delivery Confirmation

- **Delivery Acknowledgment (ACK)**: When a message is delivered, the server will receive an ACK from the client, updating the `deliveredAt` field in the database.
- **Read Receipts**: When the user opens the message or chat, the client sends a signal to update the `seenAt` field. Both delivery and read receipts will be managed asynchronously to avoid blocking the user interface.

### Scalability and Performance

- **Horizontal Scalability**: Each service (e.g., chat, notification, media) can scale independently based on load.
- **Service Discovery**: Using a **service mesh** (e.g., Istio) for routing and service discovery ensures that services can efficiently communicate without hard-coded locations.
- **Caching**: Presence, last seen, and online status will be stored in a cache to reduce load on the database.
  
This design allows us to meet the core requirements, ensuring scalability, real-time communication, and efficient resource usage.
### System Design Breakdown

#### 1. **Data Partitioning**
   - **Why:** To scale out databases for performance and manageability.
   - **Approach:** Horizontal partitioning (Sharding).
     - **Options:**
       - Hash-Based
       - List-Based
       - Range-Based
       - Composite Partitioning
     - **Solution:** Consistent Hashing to ensure even load distribution across shards.

#### 2. **Caching**
   - **Why:** Reduce load on databases and improve response times.
   - **Key Points:**
     - Cache older, less frequently accessed messages to reduce spikes.
     - Implement pagination for fetching older messages in group chats.
     - Use **LRU (Least Recently Used)** as a cache eviction policy.
     - **Cache Miss Handling:** Query database and refresh cache.
     - **Tools:** Redis or Memcached.

#### 3. **Media Access & Storage**
   - **Why:** Large-scale media storage.
   - **Solution:** Use object storage for scalable media storage.
     - **Options:** Amazon S3, Azure Blob, or Google Cloud Storage.
     - **Fun Fact:** Media can be deleted from servers after it's downloaded.
     - **Optimization:** Introduce media compression to reduce storage costs.

#### 4. **Content Delivery Network (CDN)**
   - **Why:** Improve availability and reduce bandwidth costs.
   - **Tools:** Amazon CloudFront, Cloudflare CDN.

#### 5. **API Gateway**
   - **Why:** Handle multiple communication protocols and manage API requests.
   - **Features:**
     - Authentication, Authorization.
     - Rate Limiting, Throttling.
     - API versioning.
   - **Tools:** Amazon API Gateway, Azure API Gateway.

#### 6. **Bottlenecks & Solutions**
   - **Service Failures:**
     - Run multiple instances of each service.
     - Use load balancers between clients, services, databases, and caches.
   - **Database Load:**
     - Use multiple read replicas.
   - **Cache Availability:**
     - Implement multiple cache instances and replicas.
   - **API Gateway Redundancy:**
     - Introduce standby replicas.
   - **Notification Robustness:**
     - Use message brokers (e.g., Kafka, NATS) to ensure message delivery.
   - **Media Storage Cost:**
     - Compress media to save storage space.
   - **Chat Service Overload:**
     - Separate group chat functionality into its own service.

### Key Architecture Design:
- Decouple services for better manageability (User, Chat, Notification, Presence, Media).
- Use WebSockets for real-time messaging.
- Implement caching and media storage to optimize performance.

### System Design for Twitter-like Service

Designing a scalable and efficient Twitter-like system involves addressing both functional and non-functional requirements while ensuring high availability, low latency, and fault tolerance. Below is a step-by-step breakdown of how to achieve this design.

---

## **1. Functional Requirements**

### **Core Features:**
- **Post new tweets:** Users can post text (up to 280 characters) or media (images, videos).
- **Follow users:** Users can follow/unfollow other users, influencing their feed.
- **Newsfeed:** Users see tweets from those they follow in a chronological or ranked order.
- **Search tweets:** Users can search for tweets based on keywords or hashtags.
  
### **Extended Features:**
- **Retweet:** Users can reshare tweets from others.
- **Favorites:** Users can like/favorite tweets.
- **Metrics and analytics:** Collect engagement metrics for user interaction tracking.

---

## **2. Non-Functional Requirements**

### **Scalability:** 
- The system must scale horizontally to handle billions of users and high request throughput (12K RPS).
  
### **Availability:**
- The system must be highly available, with failover mechanisms and redundancy in place.
  
### **Efficiency:** 
- Minimize latency by deploying globally distributed services and using caches.
  
---

## **3. Storage and Traffic Estimations**

### **Daily Traffic:**
- **Total tweets/day:** 1 billion tweets (200M DAU, 5 tweets/user).
- **Media tweets/day:** 100M media files (10% of tweets).
- **RPS:** 12K requests/second.

### **Storage:**
- **Daily storage for tweets:** 100 GB/day for text tweets.
- **Daily storage for media:** 5 TB/day for media (images, videos).
- **10-year storage projection:** ~19 PB.

### **Bandwidth:**
- **Ingress bandwidth:** 60 MB/second for tweet data and media.

---

## **4. High-Level System Design**

### **Core Components:**

1. **User Service:**
   - Handles user registration, login, and profile management.
   - Stores user metadata (usernames, bios, follower/following lists).

2. **Tweet Service:**
   - Manages tweet creation, storage, and retrieval.
   - Supports text and media uploads.

3. **Timeline/Feed Service:**
   - Assembles the user's timeline from tweets posted by followed accounts.
   - This can be **pull-based** (user requests their feed) or **push-based** (real-time updates).

4. **Search Service:**
   - Enables searching for tweets, users, hashtags, etc.
   - Uses an index/search engine like **Elasticsearch** for efficient querying.

5. **Media Service:**
   - Manages the storage and retrieval of media files (images, videos).
   - Stores media in object storage like **Amazon S3** or a similar cloud storage solution.

6. **Notification Service:**
   - Sends real-time notifications for follows, retweets, likes, etc.
   - Integrates with WebSockets or push notifications for mobile users.

---

### **Database Design:**

1. **User Data:**
   - Use a **Relational Database** (e.g., MySQL, Postgres) or **NoSQL Database** (e.g., Cassandra) to store user profiles, follower/following relationships.

2. **Tweets:**
   - Use **NoSQL Databases** (e.g., Cassandra, DynamoDB) for tweet storage due to the high volume and simplicity of storing key-value pairs (tweet ID to tweet content).

3. **Media:**
   - Store media in **object storage** (e.g., S3) with references in the database to manage media associations with tweets.

4. **Search Index:**
   - Use **Elasticsearch** or **Solr** to index and search tweets efficiently.

---

### **Architecture Design:**

1. **API Gateway:**
   - Acts as the front layer for all client requests (tweet posting, feed retrieval, search).
   - Directs requests to appropriate backend services.

2. **Load Balancers:**
   - Distribute traffic evenly among service instances to ensure no single instance is overwhelmed.

3. **Caching Layer:**
   - Use **Redis** or **Memcached** to cache frequent data (e.g., timeline, popular tweets) for low-latency access.

4. **Queueing System:**
   - **Apache Kafka** or **RabbitMQ** for processing events like new tweet posts, retweets, and notifications asynchronously.

---

### **Handling Timelines:**

- **Fanout Write (Push Model):** Every time a user tweets, the system pushes the tweet to the timelines of all followers. This requires more write operations but makes reading timelines very fast.
  
- **Fanout Read (Pull Model):** Tweets are stored individually, and the timeline is assembled when requested. This is more efficient in terms of storage but adds complexity to read operations.

### **Caching Strategies:**

- **Write-through Cache:** Cache the timeline of users as soon as it is generated.
- **Eviction policies:** Use LRU (Least Recently Used) or TTL (Time to Live) to manage cache size.

---

### **Media Storage:**

1. **Media Uploads:**
   - Store media files separately from the main database in distributed object storage like **Amazon S3** or **Google Cloud Storage**.
   - Use a **CDN** (Content Delivery Network) to cache and distribute media files closer to users, reducing load times.

2. **Thumbnailing and Transcoding:**
   - Create thumbnails for images and compressed versions of videos to optimize bandwidth usage.

---

### **Analytics and Monitoring:**

- **Metrics Collection:** Use services like **Prometheus** or **Datadog** to monitor key metrics like tweet rates, RPS, error rates, etc.
  
- **Log Aggregation:** Use **ELK Stack (Elasticsearch, Logstash, Kibana)** for centralized logging and monitoring.

---

## **5. Optimizations**

- **Rate Limiting:** Prevent abuse by rate-limiting requests for users based on IP or account activity.
  
- **Sharding:** Partition large datasets (users, tweets) across multiple servers using sharding techniques (based on user ID or tweet ID).

- **Replication:** Use database replication to ensure high availability and redundancy in case of hardware failures.

---

## **6. Extended Features**

1. **Retweeting:**
   - Store retweets as references to the original tweet. This minimizes data duplication and reduces storage requirements.

2. **Favorites/Likes:**
   - Implement a simple counter system to increment the number of likes on a tweet.

---

## **Conclusion**

This design addresses the high-level requirements of a Twitter-like social media platform, providing a scalable and highly available architecture that can handle billions of users, millions of daily active users, and large-scale media content. By utilizing distributed storage, caching, and efficient database models, the system can meet the performance demands while keeping operational complexity in check.
### Data Model Design Breakdown

The proposed data model reflects the core entities of the Twitter-like application and their relationships. Below is a breakdown of the key tables and their purposes:

---

### **Users Table**

This table stores user information such as name, email, date of birth (DOB), and other user details. Each user is uniquely identified by `userID`.

| Column     | Data Type | Description                                |
|------------|-----------|--------------------------------------------|
| `userID`   | UUID      | Unique identifier for each user.           |
| `name`     | String    | User's display name.                       |
| `email`    | String    | User's email address.                      |
| `dob`      | Date      | User's date of birth.                      |
| `bio`      | String    | Optional bio information.                  |
| `profileImageURL` | String | URL of the user's profile image.          |

---

### **Tweets Table**

This table stores all the tweets posted by users, including the type of tweet (text, image, video) and content. Each tweet is associated with the `userID` of the person who posted it.

| Column     | Data Type | Description                                |
|------------|-----------|--------------------------------------------|
| `tweetID`  | UUID      | Unique identifier for each tweet.          |
| `userID`   | UUID      | Reference to the user who posted the tweet.|
| `content`  | Text      | The actual content of the tweet.           |
| `mediaURL` | String    | URL of the media file (if any).            |
| `type`     | String    | Type of tweet (text, image, video, etc.).  |
| `createdAt`| Timestamp | Timestamp of when the tweet was created.   |

---

### **Favorites Table**

This table represents the relationship between users and their favorite tweets. It stores references to both the `userID` and `tweetID`.

| Column     | Data Type | Description                                |
|------------|-----------|--------------------------------------------|
| `favoriteID` | UUID      | Unique identifier for each favorite entry.|
| `userID`   | UUID      | ID of the user who favorited the tweet.    |
| `tweetID`  | UUID      | ID of the tweet that was favorited.        |
| `favoritedAt`| Timestamp | Timestamp of when the tweet was favorited. |

---

### **Followers Table**

This table handles the many-to-many relationship between users who follow each other. It includes the `followerID` (the user doing the following) and `followeeID` (the user being followed).

| Column       | Data Type | Description                                |
|--------------|-----------|--------------------------------------------|
| `followerID` | UUID      | ID of the user who is following.           |
| `followeeID` | UUID      | ID of the user being followed.             |
| `followedAt` | Timestamp | Timestamp when the follow action occurred. |

---

### **Feeds Table**

This table stores the feed of each user. It includes references to the `userID` and metadata related to the feed, such as how it’s sorted (e.g., chronological or ranked).

| Column     | Data Type | Description                                |
|------------|-----------|--------------------------------------------|
| `feedID`   | UUID      | Unique identifier for each feed.           |
| `userID`   | UUID      | Reference to the user whose feed this is.  |
| `lastUpdatedAt`| Timestamp | Last time the feed was updated.          |

---

### **Feeds_Tweets Table**

This table maps tweets to specific feeds, representing the many-to-many relationship between users' feeds and the tweets that appear in them.

| Column     | Data Type | Description                                |
|------------|-----------|--------------------------------------------|
| `feedID`   | UUID      | Reference to the feed.                     |
| `tweetID`  | UUID      | Reference to the tweet shown in the feed.  |

---

## **Database Choice**

Given the scale and requirements of this system, we should use a combination of relational and distributed NoSQL databases:

### **Relational Database (PostgreSQL):**
- Suitable for storing structured data like users, followers, and favorites.
- Provides transactional support for operations like following/unfollowing users and adding/removing favorite tweets.

### **NoSQL Database (Cassandra):**
- Ideal for storing high-volume, unstructured data like tweets and feeds.
- Provides scalability, fast write operations, and the ability to handle large datasets distributed across multiple nodes.

**Rationale:**
- Tweets and feeds will require high throughput, low latency, and the ability to scale, making NoSQL (Cassandra) ideal.
- User information and relationships (followers, favorites) benefit from consistency and relational queries, making PostgreSQL a better fit.

---

## **API Design**

### **1. Post a Tweet**

This API allows a user to post a tweet, which could include text and optional media content.

```tsx
postTweet(userID: UUID, content: string, mediaURL?: string): boolean
```

- **Parameters:**
  - `userID` (UUID): Unique identifier of the user posting the tweet.
  - `content` (string): The content of the tweet (text).
  - `mediaURL` (string): Optional URL of the media attached to the tweet (if any).

- **Returns:**
  - `boolean`: True if the tweet is posted successfully, false otherwise.

- **Flow:**
  1. Validate the tweet (e.g., check character limits, sanitize content).
  2. Store the tweet in the `tweets` table (in Cassandra).
  3. If successful, return `true`.

---

### **2. Follow/Unfollow User**

This API allows a user to follow or unfollow another user.

```tsx
follow(followerID: UUID, followeeID: UUID): boolean
unfollow(followerID: UUID, followeeID: UUID): boolean
```

- **Parameters:**
  - `followerID` (UUID): ID of the user initiating the follow/unfollow.
  - `followeeID` (UUID): ID of the user to be followed/unfollowed.

- **Returns:**
  - `boolean`: True if the follow/unfollow action was successful, false otherwise.

- **Flow (Follow):**
  1. Validate that `followerID` and `followeeID` are valid users.
  2. Add an entry in the `followers` table to reflect the relationship.
  3. Update the newsfeed for the `followerID` (push the latest tweets of the followee).
  4. If successful, return `true`.

- **Flow (Unfollow):**
  1. Validate that `followerID` and `followeeID` are valid users.
  2. Remove the entry from the `followers` table.
  3. Update the newsfeed for the `followerID` to remove the followee's tweets.
  4. If successful, return `true`.

---

### **3. Get Newsfeed**

This API retrieves the tweets shown in the user's newsfeed.

```tsx
getNewsfeed(userID: UUID): Tweet[]
```

- **Parameters:**
  - `userID` (UUID): Unique identifier of the user whose newsfeed is requested.

- **Returns:**
  - `Tweet[]`: Array of tweets to be shown in the newsfeed.

- **Flow:**
  1. Fetch the user's feed from the `feeds` table (in Cassandra).
  2. Retrieve the associated tweets using the `feeds_tweets` table.
  3. Return the list of tweets in the desired order (chronological, ranked, etc.).

---

## **Conclusion**

This data model and API design approach offer a scalable solution for handling user tweets, followers, and newsfeeds in a Twitter-like social media application. By using a combination of relational (PostgreSQL) and NoSQL (Cassandra) databases, we ensure that both the structured and unstructured data are handled efficiently at scale.

In the high-level design for the Twitter-like system, you've outlined several critical services and components necessary to scale and optimize functionality. Here's a concise breakdown of the key concepts:

### 1. **Microservices Architecture**
   - Each service has ownership of its data model.
   - Core services include:
     - **User Service**: Handles user authentication and management.
     - **Newsfeed Service**: Responsible for generating and publishing user newsfeeds.
     - **Tweet Service**: Manages tweets and related operations.
     - **Search Service**: Handles search functionality.
     - **Media Service**: Uploads and manages media files.
     - **Notification Service**: Sends notifications.
     - **Analytics Service**: Collects metrics for analysis.
   - Inter-service communication is optimized with **gRPC** for efficiency, and **service discovery** ensures reliable communication across services.

### 2. **Newsfeed Generation**
   - Newsfeed is created by:
     1. Fetching users and entities followed.
     2. Retrieving relevant tweets.
     3. Applying a **ranking algorithm** for sorting (e.g., affinity, weight, decay).
   - To optimize performance:
     - **Pre-generated feeds** are cached, and updates happen periodically.

### 3. **Publishing Models for Newsfeed**
   - **Pull Model**: Tweets are fetched on-demand (reduced writes, increased reads).
   - **Push Model**: Tweets are pushed to followers' feeds immediately (more writes).
   - **Hybrid Model**: A combination of both—push for regular users, pull for users with large followings.

### 4. **Ranking Algorithm**
   - Inspired by Facebook's EdgeRank, the ranking formula can be defined as:
     $$ \text{Rank} = \text{Affinity} \times \text{Weight} \times \text{Decay} $$
   - Machine learning algorithms may be used for more complex ranking.

### 5. **Retweets**
   - Retweets are implemented as new tweets with modified `type` (e.g., "retweet") and `content` properties linking to the original tweet.

### 6. **Search and Trending**
   - **Elasticsearch** is used for storing, searching, and analyzing data in real-time.
   - Trending topics can be identified by caching frequently searched queries and applying ranking algorithms for personalization.

### 7. **Push Notifications**
   - Push notifications are handled through **message brokers** like **Apache Kafka**.
   - Delivery of notifications is managed via services like **Firebase Cloud Messaging (FCM)** or **Apple Push Notification Service (APNS)**.

This design emphasizes scalability, performance, and flexibility through the combination of microservices, caching, and specialized services like Elasticsearch for search and Kafka for notifications.
### Netflix High-Level Design Overview

In this design, we will be creating a high-level architecture of a video streaming service like Netflix. This will cover aspects such as media storage, streaming, content delivery, and more.

### Key Functional Requirements:
1. **User Authentication**: Users should be able to register, log in, and manage their profiles.
2. **Content Delivery**: The system must deliver video content to users in an efficient and scalable manner.
3. **Recommendation System**: Users should receive content suggestions based on their viewing history.
4. **Search Functionality**: Users should be able to search for content using keywords, genres, and titles.
5. **Video Quality Adaptation**: The system should adapt video quality based on the user's network speed (adaptive bitrate streaming).
6. **Billing & Subscription Management**: Users should be able to manage their subscription plans and payments.

### Non-functional Requirements:
1. **Scalability**: The system should handle millions of users.
2. **Low Latency**: Minimal buffering and delays during video playback.
3. **High Availability**: The service should be available 24/7, with minimal downtime.
4. **Security**: Protect user data, ensure secure payments, and prevent unauthorized access.

---

### Architecture Components

#### 1. **User Service**
- Handles user authentication and profile management. 
- Technologies: OAuth, JWT for session management, databases for user profile storage (SQL or NoSQL).

#### 2. **Content Management Service**
- Allows admins to upload, manage, and delete videos. Manages metadata (titles, genres, ratings, etc.).
- Technologies: Node.js with MongoDB for metadata, AWS S3 or Google Cloud Storage for media.

#### 3. **Streaming Service**
- Handles video content delivery.
- Technologies: **HLS (HTTP Live Streaming)** or **MPEG-DASH (Dynamic Adaptive Streaming over HTTP)** for adaptive bitrate streaming.

#### 4. **Content Delivery Network (CDN)**
- Distributes content geographically to reduce latency and enhance speed.
- Technologies: Use services like **Cloudflare CDN** or **AWS CloudFront** to cache videos globally and reduce the load on the core infrastructure.

#### 5. **Recommendation Service**
- Implements recommendation algorithms such as **collaborative filtering** and **content-based filtering**.
- Technologies: Machine learning models built on frameworks like **Apache Spark** or **TensorFlow**, with data stored in **NoSQL** databases for quick retrieval.

#### 6. **Search Service**
- Allows users to search for movies or shows.
- Technologies: **Elasticsearch** for full-text search and filtering by metadata such as genre, title, or year.

#### 7. **Billing and Subscription Service**
- Manages user subscriptions and payments.
- Technologies: **Stripe** or **PayPal** for payment gateways, with records stored in **SQL databases** for tracking subscription tiers.

---

### Workflow Example: Streaming a Video

1. **User Requests Video**: The user selects a video from their dashboard.
2. **Request Sent to Streaming Service**: The user's request is handled by the streaming service, which retrieves the video URL and metadata from the **Content Management Service**.
3. **Stream Initiation**: The streaming service requests the video from the **CDN**. If not cached, it pulls the content from cloud storage (e.g., AWS S3) and sends it to the CDN.
4. **Adaptive Streaming**: Based on the user's network speed, the streaming service delivers the appropriate video quality using **HLS** or **MPEG-DASH**.
5. **Playback on Client**: The video is streamed to the user's device.

---

### Key Design Details

#### 1. **Media Storage**
- **Object Storage** is typically used for media storage due to its scalability and cost-effectiveness.
  - Services like **AWS S3** or **Google Cloud Storage** allow the storage of large media files (videos, images, etc.).
  - Videos are stored in different qualities and resolutions (240p, 480p, 720p, 1080p, 4K) for adaptive streaming.

#### 2. **Content Delivery Network (CDN)**
- A CDN stores cached copies of the media files on geographically distributed servers. This reduces load on the origin server and delivers content faster to users around the world.
- **Cloudflare**, **AWS CloudFront**, and **Akamai** are common CDN providers.

#### 3. **Adaptive Bitrate Streaming**
- Adaptive bitrate streaming enables the system to adjust the video quality dynamically depending on the user’s network bandwidth.
  - **HLS**: Apple's protocol for live and on-demand streaming.
  - **MPEG-DASH**: An industry standard for dynamic video streaming.

#### 4. **Recommendation Engine**
- **Collaborative Filtering**: Recommends content based on the user's preferences and viewing history.
- **Content-Based Filtering**: Recommends content based on similarities to items the user has previously liked or watched.
- Machine learning models can be used to constantly improve recommendations based on user behavior.

#### 5. **Scalability and Fault Tolerance**
- Services should be deployed as microservices that can be scaled horizontally across multiple servers.
- **Auto-scaling** policies (in **AWS** or **GCP**) can ensure the system scales as per traffic load.
- Use load balancers to distribute incoming traffic across multiple servers, ensuring no single server is overwhelmed.
  
---

### Potential Bottlenecks and Resolutions

1. **High Traffic and Video Buffering**
   - **Solution**: Use CDNs to cache content closer to users to reduce latency and improve loading speeds.
   
2. **Database Load for Metadata**
   - **Solution**: Use a NoSQL database like **Cassandra** or **MongoDB** that scales horizontally for storing large amounts of metadata.

3. **Search Performance**
   - **Solution**: Implement **Elasticsearch** to handle the full-text search efficiently, with quick response times even under heavy load.

4. **System Downtime**
   - **Solution**: Use multiple replicas of services and load balancers to ensure fault tolerance and high availability.

5. **High Costs for Media Storage**
   - **Solution**: Compress media files and only store popular content in higher resolutions to save on storage costs.

### Conclusion

This high-level architecture for a Netflix-like service ensures scalability, efficiency, and performance. By utilizing microservices, CDN, adaptive streaming, and a recommendation engine, this design can handle millions of users with minimal downtime and optimized resource usage.


## What is Netflix?

Netflix is a subscription-based streaming service that allows its members to watch TV shows and movies on an internet-connected device. It is available on platforms such as the Web, iOS, Android, TV, etc.

## Requirements

Our system should meet the following requirements:

### Functional requirements

- Users should be able to stream and share videos.
- The content team (or users in YouTube's case) should be able to upload new videos (movies, tv shows episodes, and other content).
- Users should be able to search for videos using titles or tags.
- Users should be able to comment on a video similar to YouTube.

### Non-Functional requirements

- High availability with minimal latency.
- High reliability, no uploads should be lost.
- The system should be scalable and efficient.

### Extended requirements

- Certain content should be [geo-blocked](https://en.wikipedia.org/wiki/Geo-blocking).
- Resume video playback from the point user left off.
- Record metrics and analytics of videos.

## Estimation and Constraints

Let's start with the estimation and constraints.

_Note: Make sure to check any scale or traffic-related assumptions with your interviewer._

### Traffic

This will be a read-heavy system, let us assume we have 1 billion total users with 200 million daily active users (DAU), and on average each user watches 5 videos a day. This gives us 1 billion videos watched per day.

$$
200 \space million \times 5 \space videos = 1 \space billion/day
$$

Assuming a `200:1` read/write ratio, about 5 million videos will be uploaded every day.

$$
\frac{1}{200} \times 1 \space billion = 5 \space million/day
$$

**What would be Requests Per Second (RPS) for our system?**

1 billion requests per day translate into 12K requests per second.

$$
\frac{1 \space billion}{(24 \space hrs \times 3600 \space seconds)} = \sim 12K \space requests/second
$$

### Storage

If we assume each video is 100 MB on average, we will require about 500 TB of storage every day.

$$
5 \space million \times 100 \space MB = 500 \space TB/day
$$

And for 10 years, we will require an astounding 1,825 PB of storage.

$$
500 \space TB \times 365 \space days \times 10 \space years = \sim 1,825 \space PB
$$

### Bandwidth

As our system is handling 500 TB of ingress every day, we will require a minimum bandwidth of around 5.8 GB per second.

$$
\frac{500 \space TB}{(24 \space hrs \times 3600 \space seconds)} = \sim 5.8 \space GB/second
$$

### High-level estimate

Here is our high-level estimate:

| Type                      | Estimate    |
| ------------------------- | ----------- |
| Daily active users (DAU)  | 200 million |
| Requests per second (RPS) | 12K/s       |
| Storage (per day)         | ~500 TB     |
| Storage (10 years)        | ~1,825 PB   |
| Bandwidth                 | ~5.8 GB/s   |

## Data model design

This is the general data model which reflects our requirements.

![netflix-datamodel](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/netflix/netflix-datamodel.png)

We have the following tables:

**users**

This table will contain a user's information such as `name`, `email`, `dob`, and other details.

**videos**

As the name suggests, this table will store videos and their properties such as `title`, `streamURL`, `tags`, etc. We will also store the corresponding `userID`.

**tags**

This table will simply store tags associated with a video.

**views**

This table helps us to store all the views received on a video.

**comments**

This table stores all the comments received on a video (like YouTube).

### What kind of database should we use?

While our data model seems quite relational, we don't necessarily need to store everything in a single database, as this can limit our scalability and quickly become a bottleneck.

We will split the data between different services each having ownership over a particular table. Then we can use a relational database such as [PostgreSQL](https://www.postgresql.org) or a distributed NoSQL database such as [Apache Cassandra](https://cassandra.apache.org/_/index.html) for our use case.

## API design

Let us do a basic API design for our services:

### Upload a video

Given a byte stream, this API enables video to be uploaded to our service.

```tsx
uploadVideo(title: string, description: string, data: Stream<byte>, tags?: string[]): boolean
```

**Parameters**

Title (`string`): Title of the new video.

Description (`string`): Description of the new video.

Data (`byte[]`): Byte stream of the video data.

Tags (`string[]`): Tags for the video _(optional)_.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Streaming a video

This API allows our users to stream a video with the preferred codec and resolution.

```tsx
streamVideo(videoID: UUID, codec: Enum<string>, resolution: Tuple<int>, offset?: int): VideoStream
```

**Parameters**

Video ID (`UUID`): ID of the video that needs to be streamed.

Codec (`Enum<string>`): Required [codec](https://en.wikipedia.org/wiki/Video_codec) of the requested video, such as `h.265`, `h.264`, `VP9`, etc.

Resolution (`Tuple<int>`): [Resolution](https://en.wikipedia.org/wiki/Display_resolution) of the requested video.

Offset (`int`): Offset of the video stream in seconds to stream data from any point in the video _(optional)_.

**Returns**

Stream (`VideoStream`): Data stream of the requested video.

### Search for a video

This API will enable our users to search for a video based on its title or tags.

```tsx
searchVideo(query: string, nextPage?: string): Video[]
```

**Parameters**

Query (`string`): Search query from the user.

Next Page (`string`): Token for the next page, this can be used for pagination _(optional)_.

**Returns**

Videos (`Video[]`): All the videos available for a particular search query.

### Add a comment

This API will allow our users to post a comment on a video (like YouTube).

```tsx
comment(videoID: UUID, comment: string): boolean
```

**Parameters**

VideoID (`UUID`): ID of the video user wants to comment on.

Comment (`string`): The text content of the comment.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

## High-level design

Now let us do a high-level design of our system.

### Architecture

We will be using [microservices architecture](https://karanpratapsingh.com/courses/system-design/monoliths-microservices#microservices) since it will make it easier to horizontally scale and decouple our services. Each service will have ownership of its own data model. Let's try to divide our system into some core services.

**User Service**

This service handles user-related concerns such as authentication and user information.

**Stream Service**

The stream service will handle video streaming-related functionality.

**Search Service**

The service is responsible for handling search-related functionality. It will be discussed in detail separately.

**Media service**

This service will handle the video uploads and processing. It will be discussed in detail separately.

**Analytics Service**

This service will be used for metrics and analytics use cases.

**What about inter-service communication and service discovery?**

Since our architecture is microservices-based, services will be communicating with each other as well. Generally, REST or HTTP performs well but we can further improve the performance using [gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc#grpc) which is more lightweight and efficient.

[Service discovery](https://karanpratapsingh.com/courses/system-design/service-discovery) is another thing we will have to take into account. We can also use a service mesh that enables managed, observable, and secure communication between individual services.

_Note: Learn more about [REST, GraphQL, gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc) and how they compare with each other._

### Video processing

![video-processing-pipeline](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/netflix/video-processing-pipeline.png)

There are so many variables in play when it comes to processing a video. For example, an average data size of two-hour raw 8K footage from a high-end camera can easily be up to 4 TB, thus we need to have some kind of processing to reduce both storage and delivery costs.

Here's how we can process videos once they're uploaded by the content team (or users in YouTube's case) and are queued for processing in our [message queue](https://karanpratapsingh.com/courses/system-design/message-queues).

Let's discuss how this works:

- **File Chunker**

![file-chunking](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/netflix/file-chunking.png)

This is the first step of our processing pipeline. File chunking is the process of splitting a file into smaller pieces called chunks. It can help us eliminate duplicate copies of repeating data on storage, and reduces the amount of data sent over the network by only selecting changed chunks.

Usually, a video file can be split into equal size chunks based on timestamps but Netflix instead splits chunks based on scenes. This slight variation becomes a huge factor for a better user experience since whenever the client requests a chunk from the server, there is a lower chance of interruption as a complete scene will be retrieved.

- **Content Filter**

This step checks if the video adheres to the content policy of the platform. This can be pre-approved as in the case of Netflix according to [content rating](https://en.wikipedia.org/wiki/Motion_picture_content_rating_system) of the media or can be strictly enforced like by YouTube.

This entire process is done by a machine learning model which performs copyright, piracy, and NSFW checks. If issues are found, we can push the task to a [dead-letter queue (DLQ)](https://karanpratapsingh.com/courses/system-design/message-queues#dead-letter-queues) and someone from the moderation team can do further inspection.

- **Transcoder**

[Transcoding](https://en.wikipedia.org/wiki/Transcoding) is a process in which the original data is decoded to an intermediate uncompressed format, which is then encoded into the target format. This process uses different [codecs](https://en.wikipedia.org/wiki/Video_codec) to perform bitrate adjustment, image downsampling, or re-encoding the media.

This results in a smaller size file and a much more optimized format for the target devices. Standalone solutions such as [FFmpeg](https://ffmpeg.org) or cloud-based solutions like [AWS Elemental MediaConvert](https://aws.amazon.com/mediaconvert) can be used to implement this step of the pipeline.

- **Quality Conversion**

This is the last step of the processing pipeline and as the name suggests, this step handles the conversion of the transcoded media from the previous step into different resolutions such as 4K, 1440p, 1080p, 720p, etc.

It allows us to fetch the desired quality of the video as per the user's request, and once the media file finishes processing, it gets uploaded to a distributed file storage such as [HDFS](https://karanpratapsingh.com/courses/system-design/storage#hdfs), [GlusterFS](https://www.gluster.org), or an [object storage](https://karanpratapsingh.com/courses/system-design/storage#object-storage) such as [Amazon S3](https://aws.amazon.com/s3) for later retrieval during streaming.

_Note: We can add additional steps such as subtitles and thumbnails generation as part of our pipeline._

**Why are we using a message queue?**

Processing videos as a long-running task and using a [message queue](https://karanpratapsingh.com/courses/system-design/message-queues) makes much more sense. It also decouples our video processing pipeline from the upload functionality. We can use something like [Amazon SQS](https://aws.amazon.com/sqs) or [RabbitMQ](https://www.rabbitmq.com) to support this.

### Video streaming

Video streaming is a challenging task from both the client and server perspectives. Moreover, internet connection speeds vary quite a lot between different users. To make sure users don't re-fetch the same content, we can use a [Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network).

Netflix takes this a step further with its [Open Connect](https://openconnect.netflix.com) program. In this approach, they partner with thousands of Internet Service Providers (ISPs) to localize their traffic and deliver their content more efficiently.

**What is the difference between Netflix's Open Connect and a traditional Content Delivery Network (CDN)?**

Netflix Open Connect is a purpose-built [Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network) responsible for serving Netflix's video traffic. Around 95% of the traffic globally is delivered via direct connections between Open Connect and the ISPs their customers use to access the internet.

Currently, they have Open Connect Appliances (OCAs) in over 1000 separate locations around the world. In case of issues, Open Connect Appliances (OCAs) can failover, and the traffic can be re-routed to Netflix servers.

Additionally, we can use [Adaptive bitrate streaming](https://en.wikipedia.org/wiki/Adaptive_bitrate_streaming) protocols such as [HTTP Live Streaming (HLS)](https://en.wikipedia.org/wiki/HTTP_Live_Streaming) which is designed for reliability and it dynamically adapts to network conditions by optimizing playback for the available speed of the connections.

Lastly, for playing the video from where the user left off (part of our extended requirements), we can simply use the `offset` property we stored in the `views` table to retrieve the scene chunk at that particular timestamp and resume the playback for the user.

### Searching

Sometimes traditional DBMS are not performant enough, we need something which allows us to store, search, and analyze huge volumes of data quickly and in near real-time and give results within milliseconds. [Elasticsearch](https://www.elastic.co) can help us with this use case.

[Elasticsearch](https://www.elastic.co) is a distributed, free and open search and analytics engine for all types of data, including textual, numerical, geospatial, structured, and unstructured. It is built on top of [Apache Lucene](https://lucene.apache.org).

**How do we identify trending content?**

Trending functionality will be based on top of the search functionality. We can cache the most frequently searched queries in the last `N` seconds and update them every `M` seconds using some sort of batch job mechanism.

### Sharing

Sharing content is an important part of any platform, for this, we can have some sort of URL shortener service in place that can generate short URLs for the users to share.

_For more details, refer to the [URL Shortener](https://karanpratapsingh.com/courses/system-design/url-shortener) system design._

## Detailed design

It's time to discuss our design decisions in detail.

### Data Partitioning

To scale out our databases we will need to partition our data. Horizontal partitioning (aka [Sharding](https://karanpratapsingh.com/courses/system-design/sharding)) can be a good first step. We can use partitions schemes such as:

- Hash-Based Partitioning
- List-Based Partitioning
- Range Based Partitioning
- Composite Partitioning

The above approaches can still cause uneven data and load distribution, we can solve this using [Consistent hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing).

_For more details, refer to [Sharding](https://karanpratapsingh.com/courses/system-design/sharding) and [Consistent Hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing)._

### Geo-blocking

Platforms like Netflix and YouTube use [Geo-blocking](https://en.wikipedia.org/wiki/Geo-blocking) to restrict content in certain geographical areas or countries. This is primarily done due to legal distribution laws that Netflix has to adhere to when they make a deal with the production and distribution companies. In the case of YouTube, this will be controlled by the user during the publishing of the content.

We can determine the user's location either using their [IP](https://karanpratapsingh.com/courses/system-design/ip) or region settings in their profile then use services like [Amazon CloudFront](https://aws.amazon.com/cloudfront) which supports a geographic restrictions feature or a [geolocation routing policy](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-geo.html) with [Amazon Route53](https://aws.amazon.com/route53) to restrict the content and re-route the user to an error page if the content is not available in that particular region or country.

### Recommendations

Netflix uses a machine learning model which uses the user's viewing history to predict what the user might like to watch next, an algorithm like [Collaborative Filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) can be used.

However, Netflix (like YouTube) uses its own algorithm called Netflix Recommendation Engine which can track several data points such as:

- User profile information like age, gender, and location.
- Browsing and scrolling behavior of the user.
- Time and date a user watched a title.
- The device which was used to stream the content.
- The number of searches and what terms were searched.

_For more detail, refer to [Netflix recommendation research](https://research.netflix.com/research-area/recommendations)._

### Metrics and Analytics

Recording analytics and metrics is one of our extended requirements. We can capture the data from different services and run analytics on the data using [Apache Spark](https://spark.apache.org) which is an open-source unified analytics engine for large-scale data processing. Additionally, we can store critical metadata in the views table to increase data points within our data.

### Caching

In a streaming platform, caching is important. We have to be able to cache as much static media content as possible to improve user experience. We can use solutions like [Redis](https://redis.io) or [Memcached](https://memcached.org) but what kind of cache eviction policy would best fit our needs?

**Which cache eviction policy to use?**

[Least Recently Used (LRU)](<https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)>) can be a good policy for our system. In this policy, we discard the least recently used key first.

**How to handle cache miss?**

Whenever there is a cache miss, our servers can hit the database directly and update the cache with the new entries.

_For more details, refer to [Caching](https://karanpratapsingh.com/courses/system-design/caching)._

### Media streaming and storage

As most of our storage space will be used for storing media files such as thumbnails and videos. Per our discussion earlier, the media service will be handling both the upload and processing of media files.

We will use distributed file storage such as [HDFS](https://karanpratapsingh.com/courses/system-design/storage#hdfs), [GlusterFS](https://www.gluster.org), or an [object storage](https://karanpratapsingh.com/courses/system-design/storage#object-storage) such as [Amazon S3](https://aws.amazon.com/s3) for storage and streaming of the content.

### Content Delivery Network (CDN)

[Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network) increases content availability and redundancy while reducing bandwidth costs. Generally, static files such as images, and videos are served from CDN. We can use services like [Amazon CloudFront](https://aws.amazon.com/cloudfront) or [Cloudflare CDN](https://www.cloudflare.com/cdn) for this use case.

## Identify and resolve bottlenecks

![netflix-advanced-design](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/netflix/netflix-advanced-design.png)

Let us identify and resolve bottlenecks such as single points of failure in our design:

- "What if one of our services crashes?"
- "How will we distribute our traffic between our components?"
- "How can we reduce the load on our database?"
- "How to improve the availability of our cache?"

To make our system more resilient we can do the following:

- Running multiple instances of each of our services.
- Introducing [load balancers](https://karanpratapsingh.com/courses/system-design/load-balancing) between clients, servers, databases, and cache servers.
- Using multiple read replicas for our databases.
- Multiple instances and replicas for our distributed cache.

# Uber

Let's design an [Uber](https://uber.com) like ride-hailing service, similar to services like [Lyft](https://www.lyft.com), [OLA Cabs](https://www.olacabs.com), etc.

## What is Uber?

Uber is a mobility service provider, allowing users to book rides and a driver to transport them in a way similar to a taxi. It is available on the web and mobile platforms such as Android and iOS.

## Requirements

Our system should meet the following requirements:

### Functional requirements

We will design our system for two types of users: Customers and Drivers.

**Customers**

- Customers should be able to see all the cabs in the vicinity with an ETA and pricing information.
- Customers should be able to book a cab to a destination.
- Customers should be able to see the location of the driver.

**Drivers**

- Drivers should be able to accept or deny the customer-requested ride.
- Once a driver accepts the ride, they should see the pickup location of the customer.
- Drivers should be able to mark the trip as complete on reaching the destination.

### Non-Functional requirements

- High reliability.
- High availability with minimal latency.
- The system should be scalable and efficient.

### Extended requirements

- Customers can rate the trip after it's completed.
- Payment processing.
- Metrics and analytics.

## Estimation and Constraints

Let's start with the estimation and constraints.

_Note: Make sure to check any scale or traffic-related assumptions with your interviewer._

### Traffic

Let us assume we have 100 million daily active users (DAU) with 1 million drivers and on average our platform enables 10 million rides daily.

If on average each user performs 10 actions (such as request a check available rides, fares, book rides, etc.) we will have to handle 1 billion requests daily.

$$
100 \space million \times 10 \space actions = 1 \space billion/day
$$

**What would be Requests Per Second (RPS) for our system?**

1 billion requests per day translate into 12K requests per second.

$$
\frac{1 \space billion}{(24 \space hrs \times 3600 \space seconds)} = \sim 12K \space requests/second
$$

### Storage

If we assume each message on average is 400 bytes, we will require about 400 GB of database storage every day.

$$
1 \space billion \times 400 \space bytes = \sim 400 \space GB/day
$$

And for 10 years, we will require about 1.4 PB of storage.

$$
400 \space GB \times 10 \space years \times 365 \space days = \sim 1.4 \space PB
$$

### Bandwidth

As our system is handling 400 GB of ingress every day, we will require a minimum bandwidth of around 5 MB per second.

$$
\frac{400 \space GB}{(24 \space hrs \times 3600 \space seconds)} = \sim 5 \space MB/second
$$

### High-level estimate

Here is our high-level estimate:

| Type                      | Estimate    |
| ------------------------- | ----------- |
| Daily active users (DAU)  | 100 million |
| Requests per second (RPS) | 12K/s       |
| Storage (per day)         | ~400 GB     |
| Storage (10 years)        | ~1.4 PB     |
| Bandwidth                 | ~5 MB/s     |

## Data model design

This is the general data model which reflects our requirements.

![uber-datamodel](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/uber/uber-datamodel.png)

We have the following tables:

**customers**

This table will contain a customer's information such as `name`, `email`, and other details.

**drivers**

This table will contain a driver's information such as `name`, `email`, `dob` and other details.

**trips**

This table represents the trip taken by the customer and stores data such as `source`, `destination`, and `status` of the trip.

**cabs**

This table stores data such as the registration number, and type (like Uber Go, Uber XL, etc.) of the cab that the driver will be driving.

**ratings**

As the name suggests, this table stores the `rating` and `feedback` for the trip.

**payments**

The payments table contains the payment-related data with the corresponding `tripID`.

### What kind of database should we use?

While our data model seems quite relational, we don't necessarily need to store everything in a single database, as this can limit our scalability and quickly become a bottleneck.

We will split the data between different services each having ownership over a particular table. Then we can use a relational database such as [PostgreSQL](https://www.postgresql.org) or a distributed NoSQL database such as [Apache Cassandra](https://cassandra.apache.org/_/index.html) for our use case.

## API design

Let us do a basic API design for our services:

### Request a Ride

Through this API, customers will be able to request a ride.

```tsx
requestRide(customerID: UUID, source: Tuple<float>, destination: Tuple<float>, cabType: Enum<string>, paymentMethod: Enum<string>): Ride
```

**Parameters**

Customer ID (`UUID`): ID of the customer.

Source (`Tuple<float>`): Tuple containing the latitude and longitude of the trip's starting location.

Destination (`Tuple<float>`): Tuple containing the latitude and longitude of the trip's destination.

**Returns**

Result (`Ride`): Associated ride information of the trip.

### Cancel the Ride

This API will allow customers to cancel the ride.

```tsx
cancelRide(customerID: UUID, reason?: string): boolean
```

**Parameters**

Customer ID (`UUID`): ID of the customer.

Reason (`UUID`): Reason for canceling the ride _(optional)_.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Accept or Deny the Ride

This API will allow the driver to accept or deny the trip.

```tsx
acceptRide(driverID: UUID, rideID: UUID): boolean
denyRide(driverID: UUID, rideID: UUID): boolean
```

**Parameters**

Driver ID (`UUID`): ID of the driver.

Ride ID (`UUID`): ID of the customer requested ride.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Start or End the Trip

Using this API, a driver will be able to start and end the trip.

```tsx
startTrip(driverID: UUID, tripID: UUID): boolean
endTrip(driverID: UUID, tripID: UUID): boolean
```

**Parameters**

Driver ID (`UUID`): ID of the driver.

Trip ID (`UUID`): ID of the requested trip.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Rate the Trip

This API will enable customers to rate the trip.

```tsx
rateTrip(customerID: UUID, tripID: UUID, rating: int, feedback?: string): boolean
```

**Parameters**

Customer ID (`UUID`): ID of the customer.

Trip ID (`UUID`): ID of the completed trip.

Rating (`int`): Rating of the trip.

Feedback (`string`): Feedback about the trip by the customer _(optional)_.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

## High-level design

Now let us do a high-level design of our system.

### Architecture

We will be using [microservices architecture](https://karanpratapsingh.com/courses/system-design/monoliths-microservices#microservices) since it will make it easier to horizontally scale and decouple our services. Each service will have ownership of its own data model. Let's try to divide our system into some core services.

**Customer Service**

This service handles customer-related concerns such as authentication and customer information.

**Driver Service**

This service handles driver-related concerns such as authentication and driver information.

**Ride Service**

This service will be responsible for ride matching and quadtree aggregation. It will be discussed in detail separately.

**Trip Service**

This service handles trip-related functionality in our system.

**Payment Service**

This service will be responsible for handling payments in our system.

**Notification Service**

This service will simply send push notifications to the users. It will be discussed in detail separately.

**Analytics Service**

This service will be used for metrics and analytics use cases.

**What about inter-service communication and service discovery?**

Since our architecture is microservices-based, services will be communicating with each other as well. Generally, REST or HTTP performs well but we can further improve the performance using [gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc#grpc) which is more lightweight and efficient.

[Service discovery](https://karanpratapsingh.com/courses/system-design/service-discovery) is another thing we will have to take into account. We can also use a service mesh that enables managed, observable, and secure communication between individual services.

_Note: Learn more about [REST, GraphQL, gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc) and how they compare with each other._

### How is the service expected to work?

Here's how our service is expected to work:

![uber-working](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/uber/uber-working.png)

1. Customer requests a ride by specifying the source, destination, cab type, payment method, etc.
2. Ride service registers this request, finds nearby drivers, and calculates the estimated time of arrival (ETA).
3. The request is then broadcasted to the nearby drivers for them to accept or deny.
4. If the driver accepts, the customer is notified about the live location of the driver with the estimated time of arrival (ETA) while they wait for pickup.
5. The customer is picked up and the driver can start the trip.
6. Once the destination is reached, the driver will mark the ride as complete and collect payment.
7. After the payment is complete, the customer can leave a rating and feedback for the trip if they like.

### Location Tracking

How do we efficiently send and receive live location data from the client (customers and drivers) to our backend? We have two different options:

**Pull model**

The client can periodically send an HTTP request to servers to report its current location and receive ETA and pricing information. This can be achieved via something like [Long polling](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#long-polling).

**Push model**

The client opens a long-lived connection with the server and once new data is available it will be pushed to the client. We can use [WebSockets](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#websockets) or [Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#server-sent-events-sse) for this.

The pull model approach is not scalable as it will create unnecessary request overhead on our servers and most of the time the response will be empty, thus wasting our resources. To minimize latency, using the push model with [WebSockets](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#websockets) is a better choice because then we can push data to the client once it's available without any delay, given that the connection is open with the client. Also, WebSockets provide full-duplex communication, unlike [Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#server-sent-events-sse) which are only unidirectional.

Additionally, the client application should have some sort of background job mechanism to ping GPS location while the application is in the background.

_Note: Learn more about [Long polling, WebSockets, Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events)._

### Ride Matching

We need a way to efficiently store and query nearby drivers. Let's explore different solutions we can incorporate into our design.

**SQL**

We already have access to the latitude and longitude of our customers, and with databases like [PostgreSQL](https://www.postgresql.org) and [MySQL](https://www.mysql.com) we can perform a query to find nearby driver locations given a latitude and longitude (X, Y) within a radius (R).

```sql
SELECT * FROM locations WHERE lat BETWEEN X-R AND X+R AND long BETWEEN Y-R AND Y+R
```

However, this is not scalable, and performing this query on large datasets will be quite slow.

**Geohashing**

[Geohashing](https://karanpratapsingh.com/courses/system-design/geohashing-and-quadtrees#geohashing) is a [geocoding](https://en.wikipedia.org/wiki/Address_geocoding) method used to encode geographic coordinates such as latitude and longitude into short alphanumeric strings. It was created by [Gustavo Niemeyer](https://twitter.com/gniemeyer) in 2008.

Geohash is a hierarchical spatial index that uses Base-32 alphabet encoding, the first character in a geohash identifies the initial location as one of the 32 cells. This cell will also contain 32 cells. This means that to represent a point, the world is recursively divided into smaller and smaller cells with each additional bit until the desired precision is attained. The precision factor also determines the size of the cell.

![geohashing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/geohashing.png)

For example, San Francisco with coordinates `37.7564, -122.4016` can be represented in geohash as `9q8yy9mf`.

Now, using the customer's geohash we can determine the nearest available driver by simply comparing it with the driver's geohash. For better performance, we will index and store the geohash of the driver in memory for faster retrieval.

The cell sizes of the geohashes of different lengths are as follows:

| Geohash length | Cell width | Cell height |
| -------------- | ---------- | ----------- |
| 1              | 5000 km    | 5000 km     |
| 2              | 1250 km    | 1250 km     |
| 3              | 156 km     | 156 km      |
| 4              | 39.1 km    | 19.5 km     |
| 5              | 4.89 km    | 4.89 km     |
| 6              | 1.22 km    | 0.61 km     |
| 7              | 153 m      | 153 m       |
| 8              | 38.2 m     | 19.1 m      |
| 9              | 4.77 m     | 4.77 m      |
| 10             | 1.19 m     | 0.596 m     |
| 11             | 149 mm     | 149 mm      |
| 12             | 37.2 mm    | 18.6 mm     |

**Quadtrees**

A [Quadtree](https://karanpratapsingh.com/courses/system-design/geohashing-and-quadtrees#quadtrees) is a tree data structure in which each internal node has exactly four children. They are often used to partition a two-dimensional space by recursively subdividing it into four quadrants or regions. Each child or leaf node stores spatial information. Quadtrees are the two-dimensional analog of [Octrees](https://en.wikipedia.org/wiki/Octree) which are used to partition three-dimensional space.

![quadtree](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/quadtree.png)

Quadtrees enable us to search points within a two-dimensional range efficiently, where those points are defined as latitude/longitude coordinates or as cartesian (x, y) coordinates.

We can save further computation by only subdividing a node after a certain threshold.

![quadtree-subdivision](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/quadtree-subdivision.png)

[Quadtree](https://karanpratapsingh.com/courses/system-design/geohashing-and-quadtrees#quadtrees) seems perfect for our use case, we can update the Quadtree every time we receive a new location update from the driver. To reduce the load on the quadtree servers we can use an in-memory datastore such as [Redis](https://redis.io) to cache the latest updates. And with the application of mapping algorithms such as the [Hilbert curve](https://en.wikipedia.org/wiki/Hilbert_curve), we can perform efficient range queries to find nearby drivers for the customer.

**What about race conditions?**

Race conditions can easily occur when a large number of customers will be requesting rides simultaneously. To avoid this, we can wrap our ride matching logic in a [Mutex](<https://en.wikipedia.org/wiki/Lock_(computer_science)>) to avoid any race conditions. Furthermore, every action should be transactional in nature.

_For more details, refer to [Transactions](https://karanpratapsingh.com/courses/system-design/transactions) and [Distributed Transactions](https://karanpratapsingh.com/courses/system-design/distributed-transactions)._

**How to find the best drivers nearby?**

Once we have a list of nearby drivers from the Quadtree servers, we can perform some sort of ranking based on parameters like average ratings, relevance, past customer feedback, etc. This will allow us to broadcast notifications to the best available drivers first.

**Dealing with high demand**

In cases of high demand, we can use the concept of Surge Pricing. Surge pricing is a dynamic pricing method where prices are temporarily increased as a reaction to increased demand and mostly limited supply. This surge price can be added to the base price of the trip.

_For more details, learn how [surge pricing works](https://www.uber.com/us/en/drive/driver-app/how-surge-works) with Uber._

### Payments

Handling payments at scale is challenging, to simplify our system we can use a third-party payment processor like [Stripe](https://stripe.com) or [PayPal](https://www.paypal.com). Once the payment is complete, the payment processor will redirect the user back to our application and we can set up a [webhook](https://en.wikipedia.org/wiki/Webhook) to capture all the payment-related data.

### Notifications

Push notifications will be an integral part of our platform. We can use a message queue or a message broker such as [Apache Kafka](https://kafka.apache.org) with the notification service to dispatch requests to [Firebase Cloud Messaging (FCM)](https://firebase.google.com/docs/cloud-messaging) or [Apple Push Notification Service (APNS)](https://developer.apple.com/documentation/usernotifications) which will handle the delivery of the push notifications to user devices.

_For more details, refer to the [WhatsApp](https://karanpratapsingh.com/courses/system-design/whatsapp#notifications) system design where we discuss push notifications in detail._

## Detailed design

It's time to discuss our design decisions in detail.

### Data Partitioning

To scale out our databases we will need to partition our data. Horizontal partitioning (aka [Sharding](https://karanpratapsingh.com/courses/system-design/sharding)) can be a good first step. We can shard our database either based on existing [partition schemes](https://karanpratapsingh.com/courses/system-design/sharding#partitioning-criteria) or regions. If we divide the locations into regions using let's say zip codes, we can effectively store all the data in a given region on a fixed node. But this can still cause uneven data and load distribution, we can solve this using [Consistent hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing).

_For more details, refer to [Sharding](https://karanpratapsingh.com/courses/system-design/sharding) and [Consistent Hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing)._

### Metrics and Analytics

Recording analytics and metrics is one of our extended requirements. We can capture the data from different services and run analytics on the data using [Apache Spark](https://spark.apache.org) which is an open-source unified analytics engine for large-scale data processing. Additionally, we can store critical metadata in the views table to increase data points within our data.

### Caching

In a location services-based platform, caching is important. We have to be able to cache the recent locations of the customers and drivers for fast retrieval. We can use solutions like [Redis](https://redis.io) or [Memcached](https://memcached.org) but what kind of cache eviction policy would best fit our needs?

**Which cache eviction policy to use?**

[Least Recently Used (LRU)](<https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)>) can be a good policy for our system. In this policy, we discard the least recently used key first.

**How to handle cache miss?**

Whenever there is a cache miss, our servers can hit the database directly and update the cache with the new entries.

_For more details, refer to [Caching](https://karanpratapsingh.com/courses/system-design/caching)._

## Identify and resolve bottlenecks

![uber-advanced-design](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/uber/uber-advanced-design.png)

Let us identify and resolve bottlenecks such as single points of failure in our design:

- "What if one of our services crashes?"
- "How will we distribute our traffic between our components?"
- "How can we reduce the load on our database?"
- "How to improve the availability of our cache?"
- "How can we make our notification system more robust?"

To make our system more resilient we can do the following:

- Running multiple instances of each of our services.
- Introducing [load balancers](https://karanpratapsingh.com/courses/system-design/load-balancing) between clients, servers, databases, and cache servers.
- Using multiple read replicas for our databases.
- Multiple instances and replicas for our distributed cache.
- Exactly once delivery and message ordering is challenging in a distributed system, we can use a dedicated [message broker](https://karanpratapsingh.com/courses/system-design/message-brokers) such as [Apache Kafka](https://kafka.apache.org) or [NATS](https://nats.io) to make our notification system more robust.

# Next Steps

Congratulations, you've finished the course!

Now that you know the fundamentals of System Design, here are some additional resources:

- [Distributed Systems](https://www.youtube.com/watch?v=UEAMfLPZZhE&list=PLeKd45zvjcDFUEv_ohr_HdUFe97RItdiB) (by Dr. Martin Kleppmann)
- [System Design Interview: An Insider's Guide](https://www.amazon.in/System-Design-Interview-insiders-Second/dp/B08CMF2CQF)
- [Microservices](https://microservices.io) (by Chris Richardson)
- [Serverless computing](https://en.wikipedia.org/wiki/Serverless_computing)
- [Kubernetes](https://kubernetes.io)

It is also recommended to actively follow engineering blogs of companies putting what we learned in the course into practice at scale:

- [Microsoft Engineering](https://engineering.microsoft.com)
- [Google Research Blog](http://googleresearch.blogspot.com)
- [Netflix Tech Blog](http://techblog.netflix.com)
- [AWS Blog](https://aws.amazon.com/blogs/aws)
- [Facebook Engineering](https://www.facebook.com/Engineering)
- [Uber Engineering Blog](http://eng.uber.com)
- [Airbnb Engineering](http://nerds.airbnb.com)
- [GitHub Engineering Blog](https://github.blog/category/engineering)
- [Intel Software Blog](https://software.intel.com/en-us/blogs)
- [LinkedIn Engineering](http://engineering.linkedin.com/blog)
- [Paypal Developer Blog](https://medium.com/paypal-engineering)
- [Twitter Engineering](https://blog.twitter.com/engineering)


I hope this course was a great learning experience. I would love to hear feedback from you.

Wishing you all the best for further learning!

# References

Here are the resources that were referenced while creating this course.

- [Cloudflare learning center](https://www.cloudflare.com/learning)
- [IBM Blogs](https://www.ibm.com/blogs)
- [Fastly Blogs](https://www.fastly.com/blog)
- [NS1 Blogs](https://ns1.com/blog)
- [Grokking the System Design Interview](https://www.designgurus.io/course/grokking-the-system-design-interview)
- [Grokking Microservices Design Patterns](https://www.designgurus.io/course/grokking-microservices-design-patterns)
- [System Design Primer](https://github.com/donnemartin/system-design-primer)
- [AWS Blogs](https://aws.amazon.com/blogs)
- [Architecture Patterns by Microsoft](https://learn.microsoft.com/en-us/azure/architecture/patterns)
- [Martin Fowler](https://martinfowler.com)
- [PagerDuty resources](https://www.pagerduty.com/resources)
- [VMWare Blogs](https://blogs.vmware.com/learning)

_All the diagrams were made using [Excalidraw](https://excalidraw.com) and are available [here](https://github.com/karanpratapsingh/system-design/tree/main/diagrams)._
