# NetProtectionLab_TP2
Simple Network Sniffing using Wireshark, TCPdump and more about DHCPv4 IP Leasing

## DHCP Protocol & DHCPv4 Leasing
Dynamic Host Configuration Protocol (DHCP) is a network management protocol used to automate the process of configuring devices on IP networks, thus allowing them to use network services such as DNS, NTP, and any communication protocol based on UDP or TCP. A DHCP server dynamically assigns an IP address and other network configuration parameters to each device on a network so they can communicate with other IP networks. 

![image](https://user-images.githubusercontent.com/91763346/234403456-4d66c745-2171-4651-b6d6-bd8a74d04925.png)

The typical dynamic DHCP lease cycle is as follows:

1. A client acquires an IP address lease through the allocation process of requesting one from the DHCP server.
2. If a client already has an IP address from an existing lease, it needs to refresh its IP address when it reboots after being shut down and contact the DHCP server to have an IP address reallocated.
3. Once a lease is active, the client is bound to the lease and to the address.
4. Once the lease has expired, a client contacts the server that initially granted the lease to renew it so it can keep using its IP address.
5. If a client is moving to a different network, its dynamic IP address is terminated, and it requests a new IP address from the DHCP server of the new network.

## Testing out DHCP Lease and configuration commands on Windows.

We can start by executing the following command to get our current network config

```
ipconfig /all
```
![image](https://user-images.githubusercontent.com/91763346/234405191-787e7831-1b79-4013-8759-d801eb01885c.png)

We can execute the following commands while having Wireshark capture our network traffic

```
ipconfig /release  -- that command will release and end the lease of our current IP from the DHCP server
ipconfig /renew    -- the /renew will proceed to start the handshake all over again to get a brand new ip (sometimes you'll still get the same ip)
```
![image](https://user-images.githubusercontent.com/91763346/234410367-71b844aa-35ca-4f1f-878b-0c5ee21b7e35.png)

TCPdump - Network logging

tcpdump is a packet analyzer that is launched from the command line. It can be used to analyze network traffic by intercepting and displaying packets that are being created or received by the computer it's running on.

![image](https://user-images.githubusercontent.com/91763346/234410962-fe6a34aa-fb55-4db6-8aa9-32ff7b257730.png)

Using tcpdump to capture global host traffic

![image](https://user-images.githubusercontent.com/91763346/234412032-b2c8a7b7-133c-4396-9693-89f111b9ae91.png)

Using tcpdump to capture ICMP host traffic

![image](https://user-images.githubusercontent.com/91763346/234412411-e32fb124-6e4b-4a50-92bc-916d41e71af6.png)

we are also running a ping to **google.com**

![image](https://user-images.githubusercontent.com/91763346/234412889-b55e2100-be1d-4b0f-8488-130ac8e6d716.png)

Using tcpdump to dump traffic in a file

![image](https://user-images.githubusercontent.com/91763346/234412991-032409ee-06a6-4897-9508-83a30771b757.png)

Using tcpdump to read pcap traffic from a file
```
sudo tcpdump -r OUTPUT
```

![image](https://user-images.githubusercontent.com/91763346/234413371-a640bb51-ba09-477d-8831-69eee75a5fdc.png)





