# Basic LAN Setup Homelab

### Objective
  
To simulate a small office network with three wired computers, one printer, and a wireless laptop, all connected to the same LAN. The router will provide DHCP to all devices, and you will test connectivity between them.

### Skills Learned

- Learned about wired and wireless connection
- Learned how to configure wired and wireless routers with DCHP
- Learned how to configure endpoint devices (wired and wireless)
- Learned how to connect printer to the router

### Tools Used

- CISCO Packet Tracer

### Steps

*Ref 1: Adding all end point devices (3 PCs, 1 Printer and 1 Laptop)*

![image](https://github.com/user-attachments/assets/5d0ccaa9-cc30-45bb-8fff-831e8cec1d7a)

*Ref 2: Adding all networking devices (1 Switch, 1 Router, 1 Wireless Router)*

![image](https://github.com/user-attachments/assets/37b61043-6dbc-4f10-925f-fb2320a7c689)

*Ref 3: Physically connect the devices. Start w/ connecting the PCs to the switch with a straight through cable, connecting unlike devices. Connect the printer to the switch with a straight through cable as well. Connect router to switch with a straight through cable. However, unlike switches the connection is shutdown by default. Connect the wireless router to the router with a cross-over cable, and the connection is shutdown which is normal until we configure the router.*

![image](https://github.com/user-attachments/assets/8fbe81ee-1f4c-4b43-8260-e054e2071c06)

*Ref 4: Setting up two separate IP addresses for wired and wireless router. Best practice to have separate IP so incease a security breach happens caused by a hacker, they won't have a direct connection to both wired and wireless network. In this example we set up the wired IP address as 192.168.1.0/24 and wireless as 192.168.2.0/24.*

![image](https://github.com/user-attachments/assets/5921eba6-2e46-41cc-a3a2-391597190f11)

*Ref 5: Configuring the router via its CLI command. Router>en > Router#conf t > Router(config)#.*

![image](https://github.com/user-attachments/assets/44660250-91e1-4e69-9ac0-0d135a6c85fc)

*Ref: 6: Creating a default gateway for our wired network, gi0/0*

![image](https://github.com/user-attachments/assets/82e58a02-ecad-4fe3-8bf6-bd9fe8f08b79)

*Ref 7: Creating a seperate default gateway for our wireless network, gi0/1*

![image](https://github.com/user-attachments/assets/a8f0db7b-6e0d-4ef4-962c-649990519ab5)

*Ref 8: Enabling the connection between the router and switch with command Router(config)#int gi0/0 > Router(config-if)#no-shut for wired network and Router(config)#int gi0/1 > Router (config-if)#no-shut for wireless network*

![image](https://github.com/user-attachments/assets/b3ebb7f3-1ee8-489e-a461-fb554a696d01)

*Ref 9: Setting up a DHCP Pool for wired devices on the 192.168.1.0/24 network. Router(config)#ip dhcp pool WiredLAN > Router(dhcp-config)#network 192.168.1.0 255.255.255.0 > Router(dhcp-config)#default-router 192.168.1.1.*

![image](https://github.com/user-attachments/assets/ff3ee64d-c3a0-49a1-a682-0abca99c2bd7)

*Ref 10: Setting up a DHCP Pool for wireless devices on the 192.168.2.0/24 network. Router(config)#ip dhcp pool WirelessLAN > Router(dhcp-config)#network 192.168.2.0 255.255.255.0 > Router(dhcp-config)#default-router 192.168.2.1* 

![image](https://github.com/user-attachments/assets/d5fc4058-5381-423a-87a8-4b35ce453e26)

*Ref 11: Go to one of the PCs from the wired devices and click on its IP configuration option. From there go to the "desktop" tap and under IP configuration, click DHCP to see if the request was successful*

![image](https://github.com/user-attachments/assets/02340f67-1e9f-4a70-9944-5299e1f87ece)

*Ref 12: Setting up the wireless router via GUI prompt. This is also where you edit the SSID so pay close attention to this. In this case we called it OfficeWiFi and make sure to save the changes before you go to the next page.*

![image](https://github.com/user-attachments/assets/2b7af2ea-4534-4758-8d83-7003d67d48b9)

*Ref 13: For wireless security we're going with WPA2 Personal for this excerise but for real world environment go with WPA2 Enterprise for passphase. Once you setup the passphase, don't forget to save the settings*

![image](https://github.com/user-attachments/assets/9abaebe0-2391-404b-ad48-bdc057513120)

*Ref 14: Connecting the laptop to the wireless router. Before connecting it, make sure it has wifi module hardware installed. If it doesn't, make sure the laptop is turned off before you install the hardware*

![image](https://github.com/user-attachments/assets/eeab0973-13ef-41fd-9af9-c8d4936da66c)

*Ref 15: Once it's set up and powered on, go to the desktop tap > pc Wireless to connect our laptop to the wireless router*

![image](https://github.com/user-attachments/assets/e773aa37-bffb-43cb-b319-1f7620e008bf)

*Ref 16: Connect your laptop to the wireless router by inputing the WPA2 Personal passphase that was created earlier*

![image](https://github.com/user-attachments/assets/41429cc4-a6e6-418a-82a9-7883f4c7a83c)

*Ref 17: Laptop has been successfully setup and connected to the wireless router*

![image](https://github.com/user-attachments/assets/4bf6b166-8c78-4aab-a571-c025f1271d6d)

*Ref 18: Setting up the printer with a static IP so it doesn't change whenever it restarts. The printer should have an IP in the same network as the other wired devices but outside the DHCP pool to avoid conflicts. For the example, we're giving the printer a static IP address of 192.168.1.101. Then click on the printer > config > interface > FastEthernet0*

![image](https://github.com/user-attachments/assets/0da659e9-018c-4fce-a1bc-a97e7648980b)




