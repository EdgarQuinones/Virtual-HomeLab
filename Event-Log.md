# Event Log  
This document contains my current journey of having a Virtual Homelab. I try to keep track of everything I have learned, machine configurations, and events that occur.
## Services Learned 
### nmcli: Command-line tool for controlling NetworkManager
  - sudo con mod/up 'network' ipv4.addresses <IP> ipv4.method auto/manual 
    - Can manually configure your IP, or have your DHCP server auto setup. 
### Fail2Ban: Set of server and client programs to limit brute force authentication attempts
- I added this as for another layer of security for my CentOS machine
### Yum: Updator, similar to apt to update, upgrade, and install programs
### DHCP Server
I managed to get the DHCP Server working!! Now my 2 other machines had their IPs configured automatically.
  - I had 2 Network Intefaces, but I wanted to only to listen on 1, so I used this command.
    - First had to make a cp of the dhcpd file and edit the ExecStart line to add the interface I wanted to be listed on. 
      - sudo cp /usr/lib/systemd/system/dhcpd.service /etc/systemd/system/dhcpd.service
      - ExecStart=/usr/sbin/dhcpd -f -cf /etc/dhcp/dhcpd.conf -user dhcpd -group dhcpd --no-pid <Interface>

## Event Log
I am recording any problems I face for future reference, and for saving memories.
| Time  | Events                                         | Response Action                                           | Status      | Notes                                                                                     |
|-------|--------------------------------------------------|-----------------------------------------------------------|-------------|-------------------------------------------------------------------------------------------| 
| 3/21, 00:15 | Problem: Restarted the CentOS Machine, and all ips were gone. | Re-entered all commands needed to setup both external and internal IP.  | Resolved | I need to make sure to enable services, and have auto-connect turned on so they automacticlly configure.  |
| 0:30  | Problem: Debian IP was not configuring to the DHCP's specified IP. | Changed the network adaptor from NAT to internal network | Resolved | I need to remember when I first create VMs they start connected to the internet with NAT. |
| 0:37  | Complete: All 3 machines have their networks configured from the custom DHCP server, and they can communicate with each other. | Will start looking into more services to add to the machines | Update | Today was day 1 of setting up my own Virtual Homelab, it has been very exciting and I am looking forward to the many more things I will try out.
