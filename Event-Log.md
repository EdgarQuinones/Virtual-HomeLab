Services Learned:
  This is more of a personal document for noting important services and commands I have learned when working on my home lab.

March 21: 

- nmcli: Command-line tool for controlling NetworkManager
  - sudo con mod/up 'network' ipv4.addresses <IP> ipv4.method auto/manual 
    - Can manually configure your IP, or have your DHCP server auto setup. 

- Fail2Ban: Set of server and client programs to limit brute force authentication attempts

- Yum: Updator, similar to apt to update, upgrade, and install programs

- DHCP Server
  - I managed to get the DHCP Server working!! Now my 2 other machines had their IPs configured automatically.
  - I had 2 Network Intefaces, but I wanted to only to listen on 1, so I used this command.
    - First had to make a cp of the dhcpd file and edit the ExecStart line to add the interface I wanted to be listed on. 
      - sudo cp /usr/lib/systemd/system/dhcpd.service /etc/systemd/system/dhcpd.service
      - ExecStart=/usr/sbin/dhcpd -f -cf /etc/dhcp/dhcpd.conf -user dhcpd -group dhcpd --no-pid <Interface>

Make sure you auto-connect and enable and save everything... For somereason I thought I saved and had everything working but after restarting, both of my IPs were changed. 

### Event Log
I am recording any problems I face for future reference, and for saving memories.
| Time  | Incident                                         | Response Action                                           | Status      | Notes                                                                                     |
|-------|--------------------------------------------------|-----------------------------------------------------------|-------------|-------------------------------------------------------------------------------------------|
| 00:32 | Restarted the CentOS Machine, and all ips were gone. | Re-entered all commands needed to setup both external and internal IP.  | Resolved | I need to make sure to enable services, and have auto connect on things so they automacticlly configure.  |
| 1:30  | Network file for Kali machine #2 is missing.     | Edgar looked for it, but could not find it. Looking into backing it up. | In Progress | Might have been the red team who deleted it, could be in the system.                      |
| 4:00  | Red team is sending system-wide messages         | Alex looked for any backdoors or users they are logged in as | No Solution | Certainly a red team attack. Was never able to find where they were coming from, continued for the next hour until the competition ended. |
