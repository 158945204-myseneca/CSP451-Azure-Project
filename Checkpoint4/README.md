# CSP451-Azure-Project

### Checkpoint4 Submission

- **COURSE INFORMATION: CSP451NIA**
- **STUDENT’S NAME: Kenneth Chu**
- **STUDENT'S NUMBER: 158945204**
- **GITHUB USER_ID: 158945204-myseneca**
- **TEACHER’S NAME: Atoosa Nasiri**

---

### Table of Contents
1. [Part A - Creating Network Resources using Azure CLI](#Part A - Creating Network Resources using Azure CLI)
2. [Part B - Working with Azure CLI Bash](#Part B - Working with Azure CLI Bash)
3. [Part C - Network Review Questions](#Part C - Network Review Questions)
4. [Part D - Creating Virtual Machines](#Part D - Creating Virtual Machines)

## Part A - Creating Network Resources using Azure CLI

**In network_config_test.sh what does if [[ ! $(az group list -o tsv --query "[?name=='$RG_NAME']") ]] do? Explain your answer.**

>This line basically checks whether an Azure Resource group with the specified named ‘$RG_NAME’ exists. If the result of the command indicates that there is no match, the condition becomes true. This ensures that the resource group is not created again if it already exists, preventing errors. If the condition is met, the subsequent code within the block will then be executed.

**Why is it crucial to check if a resource exist before creating it? What bash syntax do you use to test this? How do you check if a vnet exists in vnet_create.sh?**

>Checking if a resource exists before creating it is crucial to avoiding changes to existing resources. In Bash, we use a syntax that involves the az <resource-type> show command to query information about the resource. For instance, in vnet_create.sh, we check if a Virtual Network (VNET) exists by using if [[ ! $(az network vnet show -g $RESOURCE_GROUP -n $VNET_NAME) ]]; then. This line ensures that the VNET specified by the name $VNET_NAME in the given resource group $RESOURCE_GROUP does not already exist.

**What is the Azure CLI command to create vnet? Give the specific command as per your environment and unique ID configuration. What are the required and what are the optional parameters that you need to pass to it?**

>To create a vnet using the Azure CLI, we would have to use the command

```
az network vnet create --resource-group <resource-group-name> --name <vnet-name> --address-prefixes <address-prefix> --subnet-name <subnet-name> --subnet-prefix <subnet-prefix>
```

>In this command, we would replace placeholders like <resource-group-name> and <vnet-name> with our specific details. The required parameters include specifying the resource group, VNET name, address prefixes for the VNET, subnet name, and subnet prefix. We may also include optional parameters like --location for choosing the Azure region or --dns-servers for custom DNS configuration. These optional parameters can be tailored to your specific needs, and you can find more details in the Azure CLI documentation for az network vnet create.

**What is the Azure CLI command to create subnet? Give the specific command as per your environment and unique ID configuration. What are the required and what are the optional parameters that you need to pass to it?**

>To create a subnet using the Azure CLI, we would use the command
```
az network vnet subnet create --resource-group <resource-group-name> --vnet-name <vnet-name> --name <subnet-name> --address-prefix <subnet-prefix>. Replace placeholders like <resource-group-name> and <vnet-name>
```

>As per our own environments and unique ID configurations, the optional parameters that are required to be passed to it are:
- the name of the resource group, (Student-RG-1088917)
- the VNET names, (Student-1088917-vnet), (Server-22-Subnet) and (Router-22-Subnet)

>For our assignment, I was assigned the number 22 that will replace ‘XX’ in the code.

## Part B - Working with Azure CLI Bash

The [Router-22-SN1-Details.json](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/e6e4c2e328aff6f6cec8c8b4be268f1df8c9431f/Checkpoint4/json/Router-22-SN1-Details.json) file can be found here.

The [peerings.tbl](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/e6e4c2e328aff6f6cec8c8b4be268f1df8c9431f/Checkpoint4/json/peerings.tbl) file can be found here.

The [route_details.json](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/e6e4c2e328aff6f6cec8c8b4be268f1df8c9431f/Checkpoint4/json/route_details.json) file can be found here.

The [route_list.tblfile](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/e6e4c2e328aff6f6cec8c8b4be268f1df8c9431f/Checkpoint4/json/route_list.tblfile) file can be found here.

The [student_vnet.json](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/e6e4c2e328aff6f6cec8c8b4be268f1df8c9431f/Checkpoint4/json/student_vnet.json) file can be found here.

The [vnet_list.json](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/e6e4c2e328aff6f6cec8c8b4be268f1df8c9431f/Checkpoint4/json/vnet_list.json) file can be found here.

## Part C - Manage Conflicts - Merge Editor

**What is Azure Virtual Network (VNET)? Elaborate in your own words, you may use diagrams if drawn by yourself.**

>Azure Virtual Network (VNET) in Microsoft Azure is a private network in the cloud where we can set up our digital homes (VMs and Applications) We can assign it it’s own IP addresses, and subnets for different purposes. We can imagine it as though we’re designing our own infrastructure, or house where each VNet has its own purpose. Just like we would in a house, where we have a kitchen and washroom.

**In the context of Hybrid Cloud architecture. How on-prem computers can access resources inside Azure virtual network?**

>In a Hybrid Cloud setup where computers are both on-prem and in the cloud, we can access resources inside virtual networks by logging into the Azure account using the command ‘az login.’ It provides the on-prem resources to have access to our cloud environment.

**What are the most important benefits of Azure Virtual Networks? Elaborate in your own words. Do not copy/paste from Azure Documentation. Itemized list of just benefit without proper elaboration will not receive any marks.**

>Azure Virtual Networks (VNETs) are like personal secure neighborhood in the digital world, where we can decide the rules. Going back to my previous example, we can imagine setting up our space with custom addresses and different rooms for different tasks, much like organizing our home. These digital spaces easily connect to your home network or other places securely, creating safe pathways like building online roads. Just like managing your home, these digital spaces can grow and change with your needs, making it all work smoothly together.

**What is the difference between Network Security Group (NSG) and Route-Tables?**

>Network Security Groups (NSG) and Route Tables in Azure act as one of our first lines of defense for our digital environment. NSGs decide who we allow into our digital space, based on the rules that were set up. On the other hand, Route Tables act as guides that allow traffic to flow within our digital space. It redirects the traffic to different areas. All in all, NSGs decide who is allowed in and Route Tables decide where traffic goes to.

**What is the difference between NSG and Firewalls?**

>NSGs and Firewalls act as guards for our digital environment. NSGs again are like the guards that decide who is allowed in and out of our digital environment. It verifies the IDs of the users, as though they are checking ID. They focus on specific areas within your digital space, ensuring only the right people can access certain spots. Firewalls are like the outer walls of our environment, where it blocks anything suspicious from getting in. So, NSGs are the rule enforcers for specific areas, while Firewalls are the big guards protecting the whole fortress from potential threats.

**What is a hub-and-spoke network topology and how be deployed in Azure Cloud?**

>When we think of a hub-and-spoke network in Azure, we can think of it as though it is a wheel. The hub is considered the center of the wheel that acts as our main office. The spokes are what connect the main office to other places, such as other departments. This helps keep Azure organized and allows us to manage our infrastructure better.

**In working with Azure VNETs, do you need to define gateways for Azure to route traffic between subnets?**

>We can consider Azure VNETs as neighborhoods in a big city. If we want the neighborhoods (subnets) to communicate with one another, we set up paths or roadways that allow smooth traffic with the appropriate security measures to ensure that everyone can get to where they need to go.

**When do you need to configure and use Virtual Network Gateways?**

>We would use Virtual Network Gateways when we want to connect different parts of our virtual network together. We can imagine it as though we are sharing resources, files and data using a special connection, in this case the Virtual Network Gateway. It serves as a dedicated hotline ensuring that different resources can communicate with one another.

## Part D - Creating Virtual Machines

**List all VMs and send the output in table format to vm_list.tbl file. What command did you use?**

```
az vm list --output table > vm_list.tbl
```

**Get the details of your WC-99 using az show command and send the output in json format to WC-99-details.json file. What command did you use?**

```
az vm show --name WC-22 --resource-group student-rg-1088 917 --output json > WC-22-details.json
```

**List all NSG using az list command and send the output in table format to nsg_list.tblfile. What command did you use?**

```
az network nsg list --output table > nsg_list.tbl
```

**After deleting list all your VMs using az  vm list ... with the output in table format. What command did you use? How can you ensure all your VMs are deleted?**
```
az vm list --output table
```
The [vm_list.tbl](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/e6e4c2e328aff6f6cec8c8b4be268f1df8c9431f/Checkpoint4/json/vm_list.tbl) file can be found here

The [WC-22-details.json](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/e6e4c2e328aff6f6cec8c8b4be268f1df8c9431f/Checkpoint4/json/WC-22-details.json) file can be found here.

The [nsg_list.tbl](https://github.com/158945204-myseneca/CSP451-Azure-Project/blob/e6e4c2e328aff6f6cec8c8b4be268f1df8c9431f/Checkpoint4/json/nsg_list.tbl) file can be found here.