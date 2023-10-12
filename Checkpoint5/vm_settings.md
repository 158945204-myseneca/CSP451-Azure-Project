# VM Settings

_Remember to replace ‘XX’ with your Unique ID_

## Creating VMs - Using Portal

### Windows 10 Client: WC-XX

| Property  | Setting |
| :------------ | :----------- |
|**Basics**||
|**Resource Group:**| Student-RG-xxxxxx |
|**VM name** | WC-XX |
|**Base Image** | Windows 10 Pro, version 22H2 - x64 Gen2 |
|**Security type:**| 🔥Standard (the basic level of security for your Virtual Machine) |
|**Authentication type** | password |
|**Virtual Machine Sizes**| B1s |
|**Licensing:**| [x] I confirm I have an eligible Windows 10/11 license with multi-tenant hosting rights. |
|**Disks**||
|**OS disk type:**| Standard HDD LDR (locally-redundant storage) |
|**Delete with VM:**| 🔥[x] yes |
|**Key management:**| (keep default) |
|**Networking**||
|**VNET:**| Student-?????? vnet |
|**Public IP:**| 🔥None |
|**NIC network security group:** | Basic |
|**Delete NIC when VM is deleted:** | 🔥[x] yes |
|**Management**||
|**Auto-shutdown:**| Enable auto-shutdown |
|**Notification before shutdown:**| [ ] _Only select if you want email notification_ |
|||

### Linux Router: LR-XX

| Property  | Setting |
| :------------ | :----------- |
|**Basics**||
|**Resource Group:**| Student-RG-xxxxxx |
|**VM name** | LR-XX |
|**Base Image** | Red Hat Enterprise Linux 8.7 (LVM) - x64 Gen2 |
|**Security type:**| 🔥Standard (the basic level of security for your Virtual Machine) |
|**SSH Public key source:**| Generate new key pair |
|**Authentication type:**| SSH public key |
|**Username:**| _your own username_ |
|**Key pair name:**| routerkey |
|**Virtual Machine Sizes**| B1s |
|**Disks**||
|**OS disk type:**| Standard HDD LDR (locally-redundant storage) |
|**Delete with VM:**| [x] yes |
|**Key management:**| (keep default) |
|**Networking**||
|**VNET:**| Router-XX |
|**Public IP:**| None |
|**NIC network security group:** | Basic |
|**Delete NIC when VM is deleted:** | [x] yes |
|**Management**||
|**Auto-shutdown:**| Enable auto-shutdown |
|**Notification before shutdown:**| [ ] _Only select if you want email notification_ |
|||

### Windows Server: WS-XX

| Property  | Setting |
| :------------ | :----------- |
|**Basics**||
|**Resource Group:**| Student-RG-xxxxxx |
|**VM name** | WS-XX |
|**Base Image** | Windows Server 2019 Datacenter - x64 Gen2 |
|**Security type:**| 🔥Standard (the basic level of security for your Virtual Machine) |
|**Authentication type** | password |
|**Virtual Machine Sizes**| B1s |
|**Disks**||
|**OS disk type:**| Standard HDD LDR (locally-redundant storage) |
|**Delete with VM:**| [x] yes |
|**Key management:**| (keep default) |
|**Networking**||
|**VNET:**| Server-XX |
|**Public IP:**| None |
|**NIC network security group:** | Basic |
|**Delete NIC when VM is deleted:** | [x] yes |
|**Management**||
|**Auto-shutdown:**| Enable auto-shutdown |
|**Notification before shutdown:**| [ ] _Only select if you want email notification_ |
|||

### Linux Server: LS-XX

| Property  | Setting |
| :------------ | :----------- |
|**Basics**||
|**Resource Group:**| Student-RG-xxxxxx |
|**VM name** | LS-XX |
|**Base Image** | Red Hat Enterprise Linux 8.7 (LVM) - x64 Gen2 |
|**Security type:**| 🔥Standard (the basic level of security for your Virtual Machine) |
|**SSH Public key source:**| Generate new key pair |
|**Authentication type:**| SSH public key |
|**Username:**| _your own username_ |
|**Key pair name:**| serverkey |
|**Virtual Machine Sizes**| B1s |
|**Disks**||
|**OS disk type:**| Standard HDD LDR (locally-redundant storage) |
|**Delete with VM:**| [x] yes |
|**Key management:**| (keep default) |
|**Networking**||
|**VNET:**| Server-XX |
|**Public IP:**| None |
|**NIC network security group:** | Basic |
|**Delete NIC when VM is deleted:** | [x] yes |
|**Management**||
|**Auto-shutdown:**| Enable auto-shutdown |
|**Notification before shutdown:**| [ ] _Only select if you want email notification_ |
|||
