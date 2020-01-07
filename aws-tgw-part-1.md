# AWS Transit Gateway - Part-1

## Understanding IP ranges

| Class | Bits/Mask (n) | Host bits (32-n) | Total Networks    |
| :---: | :-----------: | :--------------: | :-------------:   |
| A     | 8             | 24               | (2<sup>8-1</sup>) |
| B     | 16            | 16               | (2<sup>16-2</sup>)|
| C     | 24            | 8                | (2<sup>24-3</sup>)|  

* **CIDR block format** - **a.b.c.d/n** *Examples*: 10.192.0.0/16, 10.192.10.0/24
* **Number of hosts formula** : **[2<sup>(32-n)</sup> - 2]**

## Basics for creating a TGW in CFN

- **Border Gateway Protocol (BGP)** is responsible for deciding which route to take for sending a packet from the source to destination on the internet
- Internet is a network of networks and each network is an autonomous system. Each autonomous system has a autonomous system number (ASN) which **identifies** the network and the routes are published
- Subnetwork (subnet) is a logical subdivision of a IP network. *Example:* a VPC of 10.192.0.0/16 can have 10.192.10.0/24 as a subnet
- **A route table contains a set of rules, called routes**, that are used to determine where network traffic is directed. Each subnet of a VPC is associated with a route table which controls the routing in the subnet. If you don't explicitly associate a subnet with a particular route table, the subnet is implicitly associated with the main route table. *You cannot delete the main route table, but you can replace the main route table with a custom table that you've created*
- Route table association is the association between the subnet and the route table. Each route specifies a destination CIDR

**Examples:**

- Traffic destined for the external corporate network 172.16.0.0/12 is targeted for the virtual private gateway. So the customer gateway will be having the address of the corporate network. If you are having the private subnet, any traffic outside the VPC should be going to the corporate network

    | Destination | Target |
    | :---------: | :----: |
    | 10.0.0.0/16 | local  |
    | 0.0.0.0/0   | vgw-id |  
             
- Traffic destined for the internet is targeted for the internet gateway. If you are having the public subnet, any traffic outside the VPC should be going to the internet gateway

    | Destination | Target |
    | :---------: | :----: |
    | 10.0.0.0/16 | local  |
    | 0.0.0.0/0   | igw-id |
    
- **To enable instances in a private subnet to connect to the Internet, you can create a NAT gateway or launch a NAT instance in a public subnet**, and then add a route for the private subnet that routes IPv4 Internet traffic (0.0.0.0/0) to the NAT device
- **You can create an egress-only Internet gateway for your VPC to enable instances in a private subnet to initiate outbound communication to the Internet**, but prevent the Internet from initiating connections with the instances
- **Route Propagation:** Each attachment comes with routes that can be installed to one or more transit gateway route tables. For a VPC attachment, these are the CIDR blocks of the VPC. For a VPN connection attachment, these are the prefixes that are advertised over the BGP session established with the VPN connection. When an attachment is propagated to a transit gateway route table, these routes are installed in the route table
- **Equal-cost multi-path (ECMP)** is a strategy used in routing to forward traffic to a destination over multiple best paths
