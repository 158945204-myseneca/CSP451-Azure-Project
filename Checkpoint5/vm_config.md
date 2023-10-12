# VM Configurations

_Remember to replace ‘XX’ with your Unique ID_

## Configuring VMs - Basic Connectivity

### Windows 10 Client: WC-XX

Install the following applications:

- Notepad++, Filezilla FTP client, MySQL shell (MySQL client)

### Linux Router: LR-XX

Perform the following configuration tasks:

- Install SSH keys to access the machine for administration
- Remove the firewalld service
- Install iptables-services (remember to enable and restart the service)
- Change the hostname to LR-XX.CSP4512234.com
- Enable IPv4 Forwarding
- Install tcpdump
- Run a Yum Update

**Ensure that all configurations are persistent (they don’t go away after you restart the VM.)**

### Windows Server: WS-XX

Optional - Install the following applications:

- Install Wireshark, Firefox

### Linux Server: LS-XX

Perform the following configuration tasks:

- Install SSH keys to access the machine for administration
- Remove the firewalld service
- Install iptables-services (remember to enable and restart the service)
- Change the hostname to LS-XX.CSP4512234.com
- Install tcpdump
- Run a Yum Update

**Ensure that all configurations are persistent (they don’t go away after you restart the VM.)**
