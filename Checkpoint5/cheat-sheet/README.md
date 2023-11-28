# Configuring & Troubleshooting Basic Connectivity

## Configuring VMs for Basic Connectivity

### Windows Client Installation (WC-xx)

Install the following applications using a web browser:

- Mozilla Firefox browser
- MySQL Client Shell
- Wireshark
- FileZilla FTP Client

Check the IP configuration:

```
ipconfig /all
```

### Windows Server Installation (WS-xx)

Install the following applications using a web browser:

- Mozilla Firefox browser
- Wireshark

Check the IP configuration:

```
ipconfig /all
```

### Linux Router Installation (LR-xx)

Perform the following configuration tasks:

- Install SSH keys to access the machine for administration
- Remove the firewalld service
- Install iptables-services (remember to enable and restart the service)
- Change the hostname to LR-XX.CSP4512234.com
- Enable IPv4 Forwarding
- Install tcpdump
- Run a Yum Update

```bash
# Remove the firewalld service
sudo firewall-cmd --state
sudo systemctl stop firewalld
sudo systemctl disable firewalld
sudo systemctl mask --now firewalld
sudo systemctl status firewalld

# Install iptables services
sudo yum install iptables-services
sudo systemctl enable iptables
sudo systemctl start iptables
sudo systemctl status iptables

# Work with hostname
sudo hostnamectl status
sudo hostnamectl set-hostname LR-xx.CSP451xxxx.com #static

# set prompt to show your configured hostname
export PS1='\u@LR-xx.CSP451xxxx.com:\w\$ '

# Install tcpdump
sudo yum install tcpdump

# Run yum update
sudo yum update
```

### Enable IP-Forwarding

Check if IP Forwarding is enabled using `sysctl`. You can query the `sysctl` kernel value `net.ipv4.ip_forward` to see if forwarding is enabled or not.

Check if IP Forwarding is enabled using `sysctl`

```bash
sudo sysctl net.ipv4.ip_forward
# if not enabled
net.ipv4.ip_forward = 0
# if enabled
net.ipv4.ip_forward = 1
```

Or check if IP Forwarding is enabled by checking the value in the `/proc` system

```bash
sudo cat /proc/sys/net/ipv4/ip_forward
# 0 if not enabled
# 1 if enabled
```

Enable IP Forwarding on the fly

```bash
sudo sysctl -w net.ipv4.ip_forward=1
# Or
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
# Or if you get permission denied
sudo echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
```

To **permanently** Enable IP Forwarding, the best way is using file `/etc/sysctl.conf`

```bash
sudo nano /etc/sysctl.conf
```

Add `net.ipv4.ip_forward = 1` line and save it.

```bash
net.ipv4.ip_forward = 1
```

Enable the changes made in `sysctl.conf`

```bash
sudo systemctl restart NetworkManager
```

### Linux Server Installation (LS-xx)

Perform the following configuration tasks:

- Install SSH keys to access the machine for administration
- Remove the firewalld service
- Install iptables-services (remember to enable and restart the service)
- Change the hostname to LS-XX.CSP4512234.com
- Install tcpdump
- Run a Yum Update

```bash
# Remove the firewalld service
sudo systemctl stop firewalld
sudo systemctl disable firewalld
sudo yum remove firewalld

# Install iptables services
sudo yum install iptables-services
sudo systemctl enable iptables
sudo systemctl start iptables
sudo systemctl status iptables

# Work with hostname
sudo hostnamectl status
sudo hostnamectl set-hostname LS-xx.CSP451xxxx.com ##static

# Install tcpdump
sudo yum install tcpdump

# Run yum update
sudo yum update
```

## Connect to Linux VMs - ssh & scp

Connect to your VM using command line

```bash
ssh -i <key-name> username@xxx.xxx.xxx.xxx
```

[How to use SSH keys with Windows on Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/ssh-from-windows)

## Working with Linux Firewalls

Check Firewall Settings

```bash
sudo iptables -nvL --line-numbers
```

Syntax to Insert rule, which would be above the existing

```bash
sudo iptables -I <CHAIN> <rule-number> firewall-rule
```

View all `iptables` rules

```bash
sudo iptables -t filter -L <CHAIN> --line-numbers -n -v
```

Insert a rule at a specific rule with line number

```bash
suo iptables -I <CHAIN> <rule-number> -p <protocol> -m <state> --dport <port no> -j <ACTION>
```

Drop chain FORWARD with line number

```bash
sudo iptables -D FORWARD <rule-number>
```

Capture traffic to log file

```bash
sudo iptables -I FORWARD -p all -m limit --limit 10/s -j LOG  --log-prefix "DROPPING..."

# Where to find the logs from `LOG` chain
cat /var/log/messages
```

Add watch and `alias` to allow continuous monitoring of firewalls

```bash
alias ip="watch -n 1 'sudo iptables -nvL --line-number'" 
```
