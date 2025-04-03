# SSH Switch Configuration

### Objective

Simulate a console connection to a switch using Packet Tracer and understand and configure basic switch settings

### Skills Learned

- Learn to configure hostname, IP addresses, and passwords and setting up SSH
- Practice using show commands to verify switch configurations

### Tools Used

- Cisco Packet Tracer

### Steps

*Ref 1: Simulating the console connection using packet tracer. Using the blue console cable to connect the switch (console) to the pc (RS 232)*

![image](https://github.com/user-attachments/assets/d9022095-f27e-4564-a242-853d3803004e)

*Ref 2: Access the PC terminal to begin entering the command prompts to configure the switch*

![image](https://github.com/user-attachments/assets/396c1fd2-f75e-4be8-8ac1-9c7dcec92a88)

*Ref 3: Switch>enable (to get to privilaged exec role) then enter Switch#sh running-config. Should notice there's nothting configured since its a new switch*

![image](https://github.com/user-attachments/assets/7033fb60-7d17-4a26-9235-7bc84f4be793)

*Ref 4: To find the version of our switch enter Switch#sh version; 15.0(2)* 

![image](https://github.com/user-attachments/assets/cfe28d88-4fdc-4c3c-ba3e-8956244c18a9)

*Ref 5: Assign the switch hostname, enter Switch#config t > Switch(config)#hostname Switch01. Configure password encryption, Switch01(config)#service password-encryption (use this command to use encrypted that is stored in our configuration file because by default the password that's set on CISCO switches are stored in plain txt and configuration. This adds to the layer of protection when we are setting up passwords so they are encrypted. And to prevent anyone from easily reading the passwords when viewing the configuration file. Assign a secret password for privileged exec mode access, Switch01(config)#enable secret homelab. This sets up an encrypted password for our homelab*

![image](https://github.com/user-attachments/assets/26f8bd49-7050-45cb-b266-bc007cf3cab8)

*Ref 6: Won't be able to get privileged exec mode access without entering the password we created*

![image](https://github.com/user-attachments/assets/310a2619-8e99-4879-861d-4789accdfa00)

*Ref 7: Preventing unwanted DNS lookups, Switch01(config)# no ip domain-lookup. Disable DNS lookup to prevent the switch from wasting time trying to resolve incorrect commands and domain names.*

![image](https://github.com/user-attachments/assets/2106688a-8964-4df1-b508-d3542e89d170)

*Ref 8: Configure a MOTD (Message of the Day) banner. This banner is useful because it's used to communicate important information such as legal disclaimer or security policies. Switch01#conf t > Switch01(config)#banner motd # "Unauthorized access is strictly prohibited. #"*

![image](https://github.com/user-attachments/assets/750904a8-8252-42fd-9d6d-8ed559fe5ade)

*Ref 9: Configuring an IP address on Bill. VLAN1 is a default VLAN on most switches and when we assign an IP address to VLAN 1, it allows us to remotely manage the switch so we don't have to connect to our console cable anymore. Once we have configured our remote connection to the switch and we have given it an IP address. Vlan1 shows up as being "administratively down" (Switch01#sh ip int brief)*

![image](https://github.com/user-attachments/assets/f3fc08d7-4323-4135-9f8f-0fc65bd5c9ab)

*Ref 10: Assigning VLAN1 IP address 192.168.1.5 255.255.255.0 . Switch01#conf t > Switch01(config)#int vlan 1 > Switch01(config-if)#ip address 192.168.1.5 255.255.255.0 > Switch01(config-if)#no shut*

![image](https://github.com/user-attachments/assets/6c3857a5-3397-4902-bc97-0b4bd6ce38e0)

*Ref 11: Assigning a IP address to our PC to test the connection between the PC and the switch*

![image](https://github.com/user-attachments/assets/c3e07ee8-902f-4352-beca-7c88770b21d0)

*Ref 12: Connecting our switch to the PC with a straight-through cable to test the connection and it works*

![image](https://github.com/user-attachments/assets/142708ed-c2ac-430a-ab62-2e45c7f20ae7)

*Ref 13: Going back to the desktop prompt to set up a default gateway allows the switch to communicate with devices outside of its local network enabling remote management from different subnets (Switch01(config)#ip default-gateway 192.168.1.1)*

![image](https://github.com/user-attachments/assets/f77d297a-4759-44c1-abc6-1899a81c7cd4)

*Ref 14: Enable remote management with SSH because you want a more secure connection. First we need to create a local user that we can use to login to SSH. Use command Switch01(config)#username admin privilege 15 secret cisco123, using admin as a username in this example and assigning privilage 15 gives it, admin rights, full access to all commands, such as the "Reload" command and the ability to make configuration changes. In Cisco, level 1 is read only, and access to limited commands, such as the "Ping" command. "Secret" sets the password for the admin user to be encrypted which is more secure than doing a password command.*

![image](https://github.com/user-attachments/assets/daaeec7e-febc-4459-8bfb-87a21b3970d9)

*Ref 15: Creating a domain, Switch01(config)#ip domain-name 0xshadowbyte.com as an example. It's required to create a domain name when setting up SSH because it is a secured protocol. Switchs needs to generate RSA encryption keys for secure communication when using SSH. Next we need to generate the keys on the switch by using the command "Switch01(config)#crypto key generate rsa"*

![image](https://github.com/user-attachments/assets/b0adc7d8-e4ed-4b3c-994c-370e214d4519)

*Ref 16: Now we can enable our SSH for remote access since we got the keys generated. Use command "Switch01(config)#ip ssh version 2 (SSH2 is more secure with enhanced encryption). Command "Switch01(config)#line vty 0 15" will access the virtual terminal lines 0 - 15 and these lines handle remote connection. We use this command so that the switch will access remote connection from these lines. Then enter command "Switch-1(config-line)#transport input ssh, allow connection on the vty lines. Last command is "Switch01(config-line)#login local, this is going to tell the switch to use the local authorization that we setup*

![image](https://github.com/user-attachments/assets/9f291883-854c-4d2f-a880-468f043906bb)

*Ref 17: Go to the command prompt from PC and enter "ssh -l admin 192.168.1.5 then enter the password "cisco123" and the command prompt to access the switch from the PC is available*

![image](https://github.com/user-attachments/assets/a5f0eb49-368d-4f7c-be2c-c0a398de4170)
