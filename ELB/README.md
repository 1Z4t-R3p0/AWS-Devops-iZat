

## What is a Load Balancer?

A **Load Balancer** is a networking solution that automatically distributes incoming application traffic across multiple targets (like EC2 instances) to ensure **high availability**, **fault tolerance**, and **scalability**.

![[Pasted image 20250507192658.png]]

It helps:

- Prevent overload on a single server
    
- Improve app responsiveness
    
- Provide seamless failover in case of instance failure

---

## ☁️ Load Balancing with AWS

Amazon Web Services (AWS) offers **Elastic Load Balancing (ELB)**, a fully managed load balancing service that includes:

- **Application Load Balancer (ALB)** — operates at Layer 7 (HTTP/HTTPS)
    
- **Network Load Balancer (NLB)** — operates at Layer 4 (TCP/UDP)
    
- **Gateway Load Balancer (GWLB)** — operates at Layer 3 for third-party virtual appliances


These services make it easy to distribute traffic automatically across multiple **Availability Zones**, improving application availability and fault tolerance.

---

## 🔀 What is an Application Load Balancer (ALB)?

An **ALB** is designed for web applications and works at the **application layer (HTTP/HTTPS)**. It allows:

- **Path-based routing** (e.g., `/foo` → Server A, `/bar` → Server B)
    
- **Host-based routing**
    
- SSL termination
    
- WebSocket support

### ✅ Example Setup:

- ALB listens on HTTP port 80
    
- Routes `/foo` to EC2-Foo and `/bar` to EC2-Bar
    
- EC2 instances serve different HTML pages using Apache
    

#### Architecture:

```cs
User → ALB (HTTP) → EC2-Foo (/foo)  → EC2-Bar (/bar)
```

---

## ⚡ What is a Network Load Balancer (NLB)?

A **NLB** works at the **transport layer (TCP/UDP)** and is designed for:

- Ultra-low latency
    
- High throughput
    
- Static IP support

NLB forwards TCP connections directly to EC2 instances, making it ideal for applications that need extreme performance or don't require HTTP-level features.

### ✅ Example Setup:

- NLB listens on TCP port 80
    
- Forwards traffic evenly across EC2-A and EC2-B (no path-based routing)
    
- Load balancing verified by refreshing and observing responses from different servers
    

#### Architecture:

css

CopyEdit

```cs
User → NLB (TCP) → EC2-A or EC2-B
```

---

## Testing & Validation

- ALB:
    
    - `http://<ALB-DNS>/foo` → Returns "This is FOO server"
        
    - `http://<ALB-DNS>/bar` → Returns "This is BAR server"
        
- NLB:
    
    - `http://<NLB-DNS>` → Refresh to see "This is EC2-A" or "This is EC2-B"