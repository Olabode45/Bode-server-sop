# Bode-server-sop
sop for setting up a virtual server for mitt

### Step 3: Configure Networking

#### 3.1: Select Network Mode
Choose **Bridged Adapter** if the VM should behave like a physical device on the network, or **NAT** if you want basic internet access without exposing the VM directly.

#### 3.2: Assign Static IP 
To ensure consistent access during testing, assign a static IP address:
```bash
sudo nano /etc/netplan/01-netcfg.yaml

network:
  version: 2
  ethernets:
    ens18:
      dhcp4: no
      addresses: [192.168.1.50/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8, 1.1.1.1]

