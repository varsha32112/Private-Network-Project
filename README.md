# Private-Network-Project

This project demonstrates the setup of a private two-tier architecture using CentOS VMs in VirtualBox. It includes a web server and a database server connected over a host-only network, simulating real-world application deployment with internal communication.

---

# 🖥️ Private Network Project

> A two-tier architecture using **VirtualBox** with **CentOS** VMs: one as a **Web Server** and the other as a **Database Server**, connected via a private/internal network. The web server hosts a PHP application that connects to a MySQL/MariaDB database running on the second VM.

---

## 🔧 Project Setup Steps

### 1. Download and Install VirtualBox
- Get the latest version from: [https://www.virtualbox.org](https://www.virtualbox.org)
- Install it on your system.

### 2. Download CentOS ISO
- Visit: [https://www.centos.org](https://www.centos.org)
- Prefer **CentOS 7 Minimal ISO** for performance and simplicity.

---

## 💡 Create Virtual Machines

### 3. Create VM 1: Web Server
- Name: `WebServer`
- Type: Linux → Red Hat (64-bit)
- RAM: 2GB  
- HDD: 20GB (dynamically allocated)

### 4. Create VM 2: Database Server
- Name: `DBServer`
- Type: Linux → Red Hat (64-bit)
- RAM: 2GB  
- HDD: 20GB

---

## 📀 Install CentOS on Both VMs

### 5. Attach CentOS ISO
- Go to **Settings > Storage** on both VMs
- Attach the CentOS ISO as boot disk

### 6. Install CentOS
- Boot into ISO and install CentOS on both machines
- Set hostname:
  - WebServer → `webserver.local`
  - DBServer → `dbserver.local`

---

## 🌐 Configure Network

### 7. Set Network Type (Internal or Host-Only)
- In VirtualBox → Settings → Network for both VMs:
  - **Adapter 1**: Enable → Attached to: **Internal Network**
  - Name: `intnet` (same for both)

### Install Apache (Both VMs)
- sudo yum install httpd -y
- sudo systemctl enable httpd
- sudo systemctl start httpd
### Install PHP (Only on WebServer)
- sudo yum install php php-mysql -y

### Install sql (Only on DBServer)
  - Install MySQL Server in DB Server
  - Command : dnf -y install mysql-server 

### Database Setup
- mysql -u root -p
- CREATE DATABASE webapp;
- CREATE USER 'udc123'@'%' IDENTIFIED BY 'root@123';
- GRANT ALL PRIVILEGES ON udc.* TO 'udc123'@'%';

  





