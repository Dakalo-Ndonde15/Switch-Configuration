# Basic Data and Voice VLAN Setup

### Objective
  
To set up an office network with four VLANs: one for regular office staff, one for HR, one for IT and one for VoIP (Voice over IP) devices like IP phones. A core switch will connect two access switches, and you will test connectivity between them.

### Skills Learned

- Networking Fundamentals: VLANs, core vs. access switches, trunk and access ports.
- Configuration & Management: VLAN setup, static IP assignment, trunk port setup.
- Hands-On Skills: Using Cisco Packet Tracer, connecting devices, configuring IP phones.
- Troubleshooting & Testing: Verifying connectivity, debugging VLAN issues.
- Security & Design: Controlling VLAN access

### Tools Used

- CISCO Packet Tracer

### Steps

*Ref 1: Adding devices to homelab 5 PCs, 5 IP Phones and 3 Switches*

![image](https://github.com/user-attachments/assets/0843ac9d-425a-4394-8bb6-390be0d361b7)

*Ref 2: Connecting all devices together with copper straight-though connections. While connecting the switch to IP Phone and IP Phone to PC, connection could not be completed because it needs to be physically or manually turned on on packet tracer*

![image](https://github.com/user-attachments/assets/8b871e9e-4f13-4c30-95d7-275b603835cf)

*Ref 3: Open up IP Phone 0 on packet tracer so you'll see the physical phone. Click and drag the IP_PHONE_POWER_ADAPTER onto the power adapter port so the IP Phone can be turned on*

![image](https://github.com/user-attachments/assets/2e045fc6-f575-4a20-be31-9ee54163d0e3)

*Ref 4: Do the same to IP Phone 1 and the rest of the other devices*

![image](https://github.com/user-attachments/assets/fedaa707-0522-41cb-bf30-30f140ceaaaf)

*Ref 5: Use the same copper straight-through cable, gigabite ethernet0/1 and 0/2, to connect both access switches to the core switch trunk ports. Trunk ports are set up on access switches to allow multiple VLANs to pass through*

![image](https://github.com/user-attachments/assets/16347da6-df69-4e88-a194-ceadc791dc04)

*Ref 6: Labeling VLAN 10 (Office) - IP 192.168.10.0/24 , VLAN 20 (HR) - IP 192.168.20.0/24, VLAN 30 (IT)  - IP 192.168.30.0/24 and VLAN 40 (Voice) before hand ot make it easier to rememember*

![image](https://github.com/user-attachments/assets/fdb96caf-b269-4422-b755-b6c75f7eac8f)

*Ref 7: Assigning static IP addresses to each individual PC based on access switches IP addresses*

![image](https://github.com/user-attachments/assets/2bfee7bf-b57d-4a4a-94b3-cc38ff350a2a)

*Ref 8: Open up the core switch CLI command prompt to assign it a name. (Switch>enable > Switch#conf t > Switch(config)#hostname CoreSwitch). Which in this case we're labeling it CoreSwitch to make it simplier to understand and follow*

![image](https://github.com/user-attachments/assets/32f36b65-d7fc-4cb4-a508-17babfb90eb8)

*Ref 9: From the same CLI command prompt create VLANs for the 10 - Office, 20 - HR, 30 - IT, 40 - Voice. (CoreSwitch(config)#vlan 10 > CoreSwitch(config-vlan)#name Office > CoreSwitch(config-vlan)#vlan 20 > CoreSwitch(config-vlan)#name HR > CoreSwitch(config-vlan)#vlan 30 > CoreSwitch(config-vlan)#name IT > CoreSwitch(config-vlan)#vlan 40 > CoreSwitch(config-vlan)#name Voice)*

![image](https://github.com/user-attachments/assets/239567d5-0148-4faa-82c0-3767bc1ca093)

*Ref 10: Use CoreSwitch#sh vlan command to verify that the VLANs were configured properly*

![image](https://github.com/user-attachments/assets/d1a5e168-759c-4ec7-a327-b67b0a4fc368)

*Ref 11: Configure trunk ports on core switch. Trunk ports allow multiple VLANs to pass through a single link between switches. Pro tip, if you have more than 3 or 4 vlan ports use command #switchport trunk allowed vlan all, to allow all vlans instead of typing them out individually. *

![image](https://github.com/user-attachments/assets/34a66c42-56ce-4d2e-b350-2c1784499d0c)

*Ref 12: Configuring vlan on access switches. Same thing we did at the beginning while renaming the core switch we do the same to access switch, in this case we're naming this one AccessSwitch1*

![image](https://github.com/user-attachments/assets/4c69e645-80d2-4fa6-a779-43f617756c85)

*Ref 13: After naming the switch, we now need to configure the vlans on AccessSwitch1. Follow the same commands as we did before for the core switch to assign vlan 10 - Office, vlan 20 - HR, and vlan 40 Voice. Then run #do sh vlan br to verify that the vlans were configured correctly*

![image](https://github.com/user-attachments/assets/5480be53-1ff2-4ea5-a435-c7fdfd2216bb)

*Ref 14: Now we need to configure the trunk port on AccessSwitch1 as well. #int gi0/1 > #switchport mode trunk > #switchport trunk allowed vlan 10,20,40*

![image](https://github.com/user-attachments/assets/9c4781e9-5fa8-4061-b49c-3ed572fdd740)

*Pro Tip: Color code the PCs so its easier to tell them apart*

![image](https://github.com/user-attachments/assets/427e426b-f091-4794-b7a0-a52b64d98a23)

*Ref 15: We also need to assign access and voice ports to the vlan 10 - Office computers. Since the access switch has many ports and two vlans are connected to it, we need to assign ports to them. For our example we're gonna assign fa0/1-5 to vlan 10 office computers and fa0/6-10 to vlan 20 HR computers. (AccessSwitch1(config)#int range fa0/1-5 > #switchport mode access #switchport access vlan 10 > #switchport voice vlan 40). We set up a voice vlan 40 port here because we have a phone connected to the access switch*

![image](https://github.com/user-attachments/assets/19467d49-5795-4ee5-92c4-cd58754d5670)

*Ref 16: Since the HR computers are connected to the same switch we use the same command window. Assign ports fa0/6-10 and voice vlan 40 to HR on the switch. #int range fa0/6-10 > #switchport mode access > #switchport access vlan 20 > #switchport voice vlan 40*

![image](https://github.com/user-attachments/assets/07c36282-18fa-4f17-8735-b9770d3b0dfd)

*Ref 17: Now we move on to the last access switch which is used by the IT department. Name the access switch "AccessSwitch2", assign vlan 30 - IT to it, then allow vlan 30 on trunk port. (#vlan 30 > #name IT > #exit > #int gi0/1 > #switchport mode trunk > #switchport trunk allowed vlan 30*

![image](https://github.com/user-attachments/assets/f15b7d1a-41d7-48b2-81a3-71496eb8b07a)

*Ref 18: Set up static IP for all 5 PCs (PC0-PC4). Click on the PC > IP Config > input the static IP address.*

![image](https://github.com/user-attachments/assets/c85d1f59-1de1-4384-aa17-140f9a8a96d0)

*Ref 19: Using PCs to ping each other to see if there is a connection and that all the ports,switches, and vlans were assigned correctly*

![image](https://github.com/user-attachments/assets/1f15f157-afb2-42f9-93b0-a1138298dc6c)

