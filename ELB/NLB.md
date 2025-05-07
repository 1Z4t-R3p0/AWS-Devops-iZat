
# ELB - Network Load Balancer

#### Architecture Overview:

```cs
User → ALB (HTTP) → EC2 Instances in 2 AZs
```

![[Pasted image 20250506194645.png]]

---

#### **Launch Two EC2 Instances**

- **AMI**: Ubuntu 
	
- Name : **EC2-A** 
    
- **Instance Type**: t2.micro (free tier)
	
- In different public subnets (different AZs)
	
- **Security Group**:
    - Inbound rule: Allow HTTP (port 80) from anywhere (0.0.0.0/0)

```bash
#!/bin/bash

sudo apt update -y   

# Install Apache2 web server

sudo apt install -y apache2

# Create the HTML file with server details

echo "<h1>This is  EC2-A </h1>" | sudo tee /var/www/html/index.html

# Restart Apache2 to apply changes

sudo systemctl restart apache2
```
>In Additional Details ---> data - optional ---> paste the below script.

Repeat for `EC2-B` with slightly different message.

---

#### **Create Target Group**

- Go to **EC2 → Target Groups → Create target group**
    
- **Type**: Instances
    
- **Protocol**: TCP
    
- **Port**: 80
    
- **Target type**: Instance
    
- **VPC**: Same as EC2s
    
- Name: `nlb-tg`
    
- Health check protocol: TCP and `/`
    
- Register both EC2 instances

---

#### **Create Application Load Balancer**

- Go to **EC2 → Load Balancers → Create Load Balancer**
    
- Choose **Network Load Balancer**
    
- Name: `my-nlb`
    
- Scheme: Internet-facing
    
- IP address type: IPv4
    
- Listener:
    
    - Protocol: **TCP**
        
    - Port: **80**
        
    - Forward to: `nlb-tg`
    
- Subnets: Choose 2 public subnets
    
- Click **Create**

---

#### Test the ALB

- Get the **DNS name** of the ALB from the console
    
- Open in a browser

```css
http://<NLB-DNS>
```

- You should see responses from either EC2 instance — refresh a few times to verify load balancing