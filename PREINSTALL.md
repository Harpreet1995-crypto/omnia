# Pre-Installation Preparation

## Assumptions
Omnia assumes that prior to installation:
* Systems have a base operating system (currently CentOS 7 or 8)
* Network(s) has been cabled and nodes can reach the internet
* SSH Keys for `root` have been installed on all nodes to allow for password-less SSH
* Ansible is installed on either the master node or a separate deployment node
```
yum install ansible
```

## Example system designs
Omnia can configure systems which use Ethernet- or Infiniband-based fabric to connect the compute servers.

![Example system configuration with Ethernet fabric](images/example-system-ethernet.png)

![Example system configuration with Infiniband fabric](images/example-system-infiniband.png)

## Network Setup
Omnia assumes that servers are already connected to the network and have access to the internet.
### Network Topology
Possible network configurations include:
* A flat topology where all nodes are connected to a switch which includes an uplink to the internet. This requires multiple externally-facing IP addresses
* A hierarchical topology where compute nodes are connected to a common switch, but the master node contains a second network connection which is connected to the internet. All outbound/inbound traffic would be routed through the master node. This requires setting up firewall rules for IP masquerade, see [here](https://www.server-world.info/en/note?os=CentOS_7&p=firewalld&f=2) for an example.
### IP and Hostname Assignment
The recommended setup is to assign IP addresses to individual servers. This can be done manually by logging onto each node, or via DHCP.
