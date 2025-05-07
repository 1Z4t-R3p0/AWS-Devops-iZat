
## **Application Load Balancer (ALB)** 

- Routes requests to `/foo` → sends them to **EC2 instance A**
    
- Routes requests to `/bar` → sends them to **EC2 instance B**

| URL                    | Response           |
| ---------------------- | ------------------ |
| `http://<ALB-DNS>/foo` | Comes from EC2-Foo |
| `http://<ALB-DNS>/bar` | Comes from EC2-Bar |

The **ALB listener rules** are doing the path-based routing. The EC2s are just serving basic HTML from Apache.

![[Pasted image 20250507111759.png]]

---
### Steps 

1. A **VPC** with **2 public subnets** in different availability zones
    
2. A **security group** that allows:
     
    - Inbound: **HTTP (port 80)** from `0.0.0.0/0`
        
    - Outbound: **All traffic (default)**

---

### **Launch 2 EC2 Instances**

##### Do this **twice** (once for `foo`, once for `bar`)

1. Name: `EC2-Foo` (first), then `EC2-Bar` (second)
    
2. AMI: Choose **Ubuntu 22.04 LTS**
    
3. Instance type: `t2.micro`
    
4. Network: Choose your **default VPC**
    
5. Subnet: Choose different subnets for each EC2 (for ALB to work in 2 AZs)
    
6. Auto-assign Public IP: **Enabled**
    
7. User data (paste this for `foo` instance):

```sh
#!/bin/bash
apt update -y 
apt install -y apache2
sudo mkdir -p /var/www/html/foo
echo "<h1>This is FOO server</h1>" | sudo tee /var/www/html/foo/index.html 
systemctl restart apache2
```

>For the **`bar` instance**,
```sh
#!/bin/bash
apt update -y 
apt install -y apache2
sudo mkdir -p /var/www/html/bar
echo "<h1>This is BAR server</h1>" | sudo tee /var/www/html/bar/index.html 
systemctl restart apache2
```

10. Security group: Use the group that allows **port 80**
    
11. Launch both instances

---

### **Create Two Target Groups**

1. Go to **EC2 → Target Groups → Create target group**
    
2. Target type: **Instance**
    
3. Protocol: **HTTP**, Port: `80`
    
4. VPC: Choose your default VPC
    
5. Name: `tg-foo`
    
6. Health check path: `/`
    
7. Register targets:
    
    - Choose the **EC2-Foo instance**
        
    - Click **Include as pending**

>  **Repeat the same to create `tg-bar` and register the EC2-Bar instance.**

---

### **Create an Application Load Balancer**

1. Go to **EC2 → Load Balancers → Create Load Balancer**
    
2. Choose **Application Load Balancer**
    
3. Name: `my-alb`
    
4. Scheme: **Internet-facing**
    
5. IP address type: `IPv4`
    
6. Listeners: **HTTP (port 80)**
    
7. Availability Zones: Choose **2 AZs** and the subnets where your EC2s are
    
8. Security group: Choose one that allows **port 80**
    
9. Click **Next**

---

### **Configure Listener Rules**

After creating the ALB, do this:

1. Go to **Load Balancers → your ALB → Listeners**
    
2. Click **View/edit rules**
    
3. You'll see a **default rule** —> keep it
    
4. Click  **Add Rule** 

#### Rule for `/foo`

- IF → **Path** is `/foo`
    
- THEN → **Forward to target group** → `tg-foo`

Set **priority = 1**

Click **Save rule**

#### Rule for `/bar`

- IF → **Path** is `/bar`
    
- THEN → **Forward to target group** → `tg-bar`

Set **priority = 2**

Click **Save rule**

---

### **Test It in Browser**

1. Go to your **ALB → Description**
    
2. Copy the **DNS name** (e.g., `my-alb-123456.ap-south-1.elb.amazonaws.com`)
    
3. Open browser:
    
    - `http://<ALB-DNS>/foo` → You should see: `This is FOO server`
        
    - `http://<ALB-DNS>/bar` → You should see: `This is BAR server`

---

## ✅Troubleshooting Tips

| Problem                 | Solution                                                                |
| ----------------------- | ----------------------------------------------------------------------- |
| **404 Not Found**       | Make sure `/foo` and `/bar` folders exist in Apache                     |
| **Target is unhealthy** | Check security group (port 80), Apache running, health check path = `/` |
| **ALB not routing**     | Make sure listener rules match exactly `/foo` and `/bar`                |
| **Public IP missing**   | Ensure EC2s launched with Auto-assign public IP = Enabled               |

---