# DHCP-Server-Setup

### Objective

This setup will allow you to understand how devices in a network can automatically obtain IP addresses and other network configuration details from a DHCP server.

### Skills Learned

- VLAN Configuration: Named and assigned via switch CLI. Trunk port connects router to switch.
- Router Setup: Sub-interfaces for VLANs with IP gateways and encapsulation for inter-VLAN routing.
- DHCP Server: Static IP, three DHCP pools, and relay setup for VLAN communication.
- Testing & Troubleshooting: Verify DHCP assignments and encourage modifications for practice.

### Tools Used

- CISCO Packet Tracer

### Steps

*Ref 1: Setting up 3 PCs, 1 Server, 1 Switch and 1 Router for the lab*

![image](https://github.com/user-attachments/assets/e481b373-d429-4d45-b002-0891617b7ec9)

*Ref 2: Creating labels so its easier to read and not get lost as we progress though the lab. VLAN 10 - Sales, VLAN 20 - IT, VLAN 30 - HR for the switch. Each individual PC will get a separate VLAN and IP.*

![image](https://github.com/user-attachments/assets/55d37d92-6f01-402c-8dbe-26d3316e3866)

*Ref 3: Configuring the VLANS on the Switch. Go to the CLI terminal of the switch and assign VLANS 10, 20, 30 for Sales, IT and HR.*

![image](https://github.com/user-attachments/assets/921f7391-9c1b-497c-b549-0ad9abeee48c)

*Ref 4: Assign vlan 10 to ports fa0/1-5 on access switch. (#int range fa0/1-5 > #switch mode access > #switchport access vlan 10)* 

![image](https://github.com/user-attachments/assets/3687be05-f990-460b-86e6-e37af3398ed1)

*Ref 5: Do the same for ports fa0/6-10 - vlan 20 and fa0/11-15 - vlan 30 with the same commands. Then to confirm if its configured properly run #do sh vlan br*

![image](https://github.com/user-attachments/assets/51d1dad2-55b4-423e-a536-d21706c5dcd2)

*Ref 6: Configure the trunk port for the router. The encapsulation command tells the router which vlan it's handling on each sub interface, that's why we're telling that it's on vlan 10. This is important because the router needs to differential the traffic coming from each vlan since there's multiple vlans coming into this interface. Important to not forget this command when creating sub-interfaces. Next we assign an IP address for the gateway for each vlan.*

![image](https://github.com/user-attachments/assets/282da7e4-6618-42d1-9f6b-879dcbde4d35)

*Ref 7: Enable the connection between the router and the switch by using command #int gi0/0 > #no shut*

![image](https://github.com/user-attachments/assets/0b754e3f-930f-4351-98aa-ac468942e8f4)

*Ref 8: Configuring the DHCP server. Set up a static ip address by going to the config tab > FastEthernet0 > setup a static IP 192.168.10.0*

![image](https://github.com/user-attachments/assets/617f8930-3151-4b7d-815a-4c43a358935a)

*Ref 9: Don't forget to setup the default gateway. Go to Settings > Default Gateway 192.168.10.1*

![image](https://github.com/user-attachments/assets/f19032ca-63cc-452c-9397-0964a8ed7aaa)

*Ref 10: Setting up the DHCP pool. Services > DHCP > Service "ON" > Input "VLAN 10" for Pool name > Input Default Gateway 192.168.10.1 > Add. Then do the same for VLAN 20 and VLAN 30 then you'll see the list get populated.*

![image](https://github.com/user-attachments/assets/5f7f12da-8245-4500-9a68-2a1a0e39633b)

*Ref 11: Setting up the DHCP relay on the router. DCHP relay is used to forward request from the other vlans to the dhcp server that's in vlan 10. Setting up vlan 20 and vlan 30 sub-interface on the router. (#int gi0/0.20 > #ip helper-address 192.168.10.2 > #exit > #int gi0/0.30 > #ip helper-address 192.168.10.2 > #exit.)*

![image](https://github.com/user-attachments/assets/7370b715-7c22-4ddc-aff7-bee3877375f4)

