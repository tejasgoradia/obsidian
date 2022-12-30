[Azure PowerShell CheatSheet](https://github.com/andreipintica/Azure-PowerShell-CheatSheethttps://github.com/andreipintica/Azure-PowerShell-CheatSheet)



# [AZ-104: Deploy and manage Azure compute resources](https://learn.microsoft.com/en-us/training/paths/az-104-manage-compute-resources/)

## [Configure virtual machines](https://learn.microsoft.com/en-us/training/modules/configure-virtual-machines/)

https://learn.microsoft.com/en-us/training/modules/create-linux-virtual-machine-in-azure/

https://learn.microsoft.com/en-us/training/modules/create-windows-virtual-machine-in-azure/

https://learn.microsoft.com/en-us/training/modules/connect-vm-with-azure-bastion/


## [Configure virtual machine availability](https://learn.microsoft.com/en-us/training/modules/configure-virtual-machine-availability/)

[# Azure Scale Set vs Availability Set](https://tutorialsdojo.com/azure-scale-set-vs-availability-set/)

[# Azure — Difference between Scale Sets and Availability Sets](https://medium.com/awesome-azure/difference-between-scale-set-and-availability-set-in-azure-9b2da03b891c)

[Understanding Availability Sets and Availability Zones](https://techcommunity.microsoft.com/t5/itops-talk-blog/understanding-availability-sets-and-availability-zones/ba-p/1992518)

## [Configure virtual machine extensions](https://learn.microsoft.com/en-us/training/modules/configure-virtual-machine-extensions/)

- what is the difference between virutal machine extensions and custom script extensions
- how is azure app service plan any different to creating vm scale sets
- what is sql injection and CORS
- what is stored access policy for storage account
- what is the difference between the two settings for enabling public access at a container level
	- a) Public read access for blobs
	- b) Public read access for a container and its blobs
- Confirm that budget is not a hardlimit which prohibits resource creation or results into resource termination
- what is a network virtual appliance (NVA)?
- what is a virtual network service endpoint? How is service endpoint different to private links?
- What is a gateway?
- What is the difference between load balancer, application gateway, traffic manager, front door, proxy vs reverse proxy?
	https://www.youtube.com/watch?v=bGPEiQhyC-s
- what is the difference between VPN gateway and Application gateway?



**Azure reserves the first four and last IP address for a total of 5 IP addresses within each subnet.**
For example, the IP address range of 192.168.1.0/24 has the following reserved addresses:
- 192.168.1.0: Network address
- 192.168.1.1: Reserved by Azure for the default gateway
- 192.168.1.2, 192.168.1.3: Reserved by Azure to map the Azure DNS IPs to the VNet space
- 192.168.1.255: Network broadcast address.


