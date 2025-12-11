# 🖥️ Server & Services Lead 

## ✅ 1. Full Server List + Purpose
- **DC1 – Primary Domain Controller**  
  Handles Active Directory Domain Services (AD DS) and DNS. Central authority for authentication and directory lookups.
- **DC2 – Secondary Domain Controller**  
  Provides redundancy for AD DS and DNS. Ensures high availability if DC1 fails.
- **DNS Server**  
  Resolves internal hostnames to IP addresses. Critical for domain operations and service discovery.
- **DHCP Server**  
  Assigns IP addresses dynamically to client devices. Simplifies network management.
- **File Server**  
  Stores departmental files and shared resources. Backbone for collaboration.
- **Web Server (IIS)**  
  Hosts TrendyThreads’ demo e‑commerce site. Used by Marketing & E‑commerce.
- **Mail Server (Exchange)**  
  Provides internal email services for testing and communication.
- **Backup Server**  
  Runs backup tools to snapshot and protect all major servers. Ensures disaster recovery.

---

## ✅ 2. Roles & Features Installed
- **DC1/DC2** → Active Directory Domain Services (AD DS), DNS role  
- **DHCP Server** → DHCP role  
- **File Server** → File Services role  
- **Web Server** → IIS role  
- **Mail Server** → Microsoft Exchange Server role  
- **Backup Server** → Backup software (e.g., Windows Server Backup, Veeam)

---

## ✅ 3. File Share Layout Planning

| Share Name          | Used By           | Purpose                          |
|---------------------|------------------|----------------------------------|
| HR_Confidential     | HR Department    | Store sensitive HR documents     |
| Sales_Data          | Sales Department | Store customer and sales records |
| Inventory_DB        | Inventory Team   | Store stock and warehouse data   |
| Production_Designs  | Production Team  | Store design files and blueprints|
| Marketing_Assets    | Marketing Team   | Store images, videos, and ads    |
| Shared              | All Departments  | General collaboration folder     |

---

## ✅ 4. Basic Service Dependency Map
- **DHCP → DNS** (DHCP leases must register with DNS for name resolution)  
- **File Server → AD Groups** (permissions tied to security groups defined by Identity Lead)  
- **Web Server → Domain + Network** (requires DNS resolution and AD authentication)  
- **Backup Server → All Servers** (backs up DCs, File Server, Web Server, Mail Server)

---

## ✅ 5. Department Service Requirements Overview

| Department             | Services Used                          |
|------------------------|----------------------------------------|
| Sales                  | Sales_Data share, Email                |
| HR                     | HR_Confidential share, Email           |
| Inventory & Warehouse  | Inventory_DB share                     |
| Production             | Production_Designs share               |
| Marketing & E‑commerce | Marketing_Assets share, Web Server     |
| IT                     | All services (admin, support, backups) |
| Management             | Shared folder, Email                   |

---

## ℹ️ Additional Details

### 1. Web Server Choice
We’re using **IIS (Internet Information Services)** on Windows Server.  
- Integrates seamlessly with Active Directory.  
- Supports ASP.NET and static content.  
- Easy to manage via GUI and PowerShell.

### 2. File Server Choice
We’re using **Windows Server with File Services role**.  
- Native NTFS + AD group integration.  
- Supports SMB protocol for secure file sharing.  
- Simple departmental share configuration.

### 3. Exchange Server Location
Installed on a **dedicated Windows Server**, separate from DC1/DC2.  
- Avoids resource competition with domain controllers.  
- Improves performance and troubleshooting.

### 4. DNS & DHCP Placement
- **DNS** → Installed on **both DC1 and DC2** for redundancy.  
- **DHCP** → Installed on **DC1 only**.  
- Ensures high availability for DNS, while DHCP remains simple to manage.

