# AWS DevOps Engineer Intern Assignment 

## Objective
Deploy a simple website on an AWS EC2 instance, document the process, and host it using Nginx.

---

## Task 1: Create an AWS EC2 Instance

**Steps performed:**

1. Logged into the AWS Management Console and navigated to **EC2 > Launch Instance**.
2. Configured the instance:
   - **Name:** `nginx-instance` 
   - **AMI:** Ubuntu Server 22.04 LTS (Free Tier eligible)
   - **Instance type:** t3.micro (Free Tier eligible)
   - **Key pair:** Created a new key pair named `Aliya-s-dummy-key.pem` and downloaded it for SSH access.
3. Configured the **Security Group** with the following inbound rules:
   | Type  | Protocol | Port | Source    |
   |-------|----------|------|-----------|
   | SSH   | TCP      | 22   | My IP / 0.0.0.0/0 |
   | HTTP  | TCP      | 80   | 0.0.0.0/0 |
4. Launched the instance and noted the **Public IPv4 address**: `13.60.53.58`
5. Connected to the instance via SSH from local terminal:

   ```bash
   chmod 400 Aliya-s-dummy-key.pem
   ssh -i "Aliya-s-dummy-key.pem" ubuntu@13.60.53.58
   ```

**Deliverables:**
- EC2 Public IP: `[13.60.53.58]`
- Screenshot: EC2 Dashboard showing running instance
- Screenshot: Successful SSH login to the instance

---

## Task 2: Linux Basics

**Commands used to update packages, install Nginx, and check system status:**

```bash
# Update package index
sudo apt update -y

# Upgrade installed packages
sudo apt upgrade -y

# Install Nginx
sudo apt install nginx -y

# Start and enable Nginx to run on boot
sudo systemctl start nginx
sudo systemctl enable nginx

# Check Nginx service status
sudo systemctl status nginx

# Check disk usage
df -h

# Check memory usage
free -h

# Check running processes
ps aux
# or
top
```

**Deliverables:**
- Screenshot: `sudo systemctl status nginx` showing Nginx active/running
- Screenshot: Website accessible in browser via EC2 Public IP (default Nginx page, before replacement)
- Screenshot: `df -h` and `free -h` output

---

## Task 3: Host a Simple Website

Created a basic HTML page containing Name, College, Branch, Email, and Current Date, styled with a custom color theme and Google Fonts (Playfair Display + Poppins).

**Steps performed:**

1. Created `index.html` locally with the required personal details.
2. Transferred the file to the EC2 instance using `scp`:

   ```bash
   scp -i "Aliya-s-dummy-key.pem" index.html ubuntu@[13.60.53.58]:~/
   ```

3. Replaced the default Nginx page with the custom page:

   ```bash
   sudo cp ~/index.html /var/www/html/index.html
   ```

4. Restarted Nginx to ensure changes were served correctly:

   ```bash
   sudo systemctl restart nginx
   ```

5. Verified the website by visiting `http://[13.60.53.58]` in a browser.

**Deliverables:**
- Website accessible via EC2 Public IP: `http://[13.60.53.58]`
- Screenshot: Browser showing the custom HTML page live

---

## Task 4: Git & GitHub

**Steps performed:**

1. Created a new GitHub repository: `AWS-DevOps-Intern-Assignment`
2. initialized it in the project folder):

   ```bash
   git init
   git remote add origin https://github.com/Aliyas-22/AWS-DevOps-Intern-Assignment.git
   ```

3. Added the `index.html` file and this `README.md`:

   ```bash
   git add index.html README.md
   git commit -m "Add DevOps intern assignment: EC2 + Nginx hosted website"
   git branch -M main
   git push -u origin main
   ```

**Deliverables:**
- GitHub repository link: `https://github.com/Aliyas-22/AWS-DevOps-Intern-Assignment`

---

## Task 5: Documentation

### AWS Services Used
- **Amazon EC2** – to launch and manage the Ubuntu virtual machine
- **EC2 Security Groups** – to control inbound traffic on ports 22 (SSH) and 80 (HTTP)
- **Key Pairs (IAM)** – for secure SSH authentication

### Linux Commands Used
```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx
sudo systemctl restart nginx
df -h
free -h
ps aux
scp -i key.pem index.html ubuntu@<public-ip>:~/
sudo cp ~/index.html /var/www/html/index.html
```

### Learnings
- Gained hands-on experience launching and configuring an EC2 instance from scratch.
- Learned how Security Groups control network access to a cloud instance.
- Understood how Nginx serves static web content and how to replace default configurations.
- Practiced using Git/GitHub to version and share project deliverables.

### Total Time Taken
`Approximately 2.5 hours`

---

## Bonus (+10 Marks)

**Completed:** `Docker hello-world `

Made executable and run with:
```bash
docker run hello-world 
```

---

## Submission Summary

| Item | Link / Value |
|------|---------------|
| GitHub Repository | `https://github.com/Aliya-22/AWS-DevOps-Intern-Assignment` |
| EC2 Public IP | `13.60.53.58` |

---

**Author:** Shaikh Aliya Firdous
**College:** Aditya College of Engineering
**Branch:** MCA master of computer application
**Email:** itz.aliya22@gmail.com
