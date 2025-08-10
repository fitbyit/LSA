## ✅ What is a DHCP Server?
### A DHCP (Dynamic Host Configuration Protocol) server is a network service that automatically assigns IP addresses and other network configuration parameters to devices (clients) on a network.
---

## 🔁 How It Works – DHCP Process (DORA):
1. Discover – Client broadcasts to find a DHCP server.
2. Offer – DHCP server offers an IP configuration
3. Request – Client requests the offered IP.
4. Acknowledge – Server confirms and leases the IP.
---

## To set up a DHCP (Dynamic Host Configuration Protocol) server on RHEL 
---

## Step 1: Install the DHCP Server Package
```
yum install dhcp-server -y
```

## Step 2: Configure the DHCP Server

### 1. Edit the DHCP configuration file
```
gedit /etc/dhcp/dhcpd.conf
```

### 2. Add or modify the following lines in the file:
```
default-lease-time 600;
max-lease-time 7200;
subnet 192.168.16.0 netmask 255.255.255.0 {
  range 192.168.16.100 192.168.16.200;  # IP range to be assigned to clients
  option routers 192.168.16.1;        # Default gateway IP
  option subnet-mask 255.255.255.0;  # Subnet mask
}
```


## Step 3: Restart the DHCP Service
```
systemctl restart dhcpd
```

### Check the status of the DHCP service to ensure it’s running:
```
systemctl status dhcpd
```

# Step 4: Test the DHCP Server
- Start you Client Machine and check ip address
- You can see that ip address will within the range define in DHCP Server

