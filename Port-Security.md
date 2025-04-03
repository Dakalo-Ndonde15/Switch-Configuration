# Switch Port Security - CISCO

### Objective
  
Understand the importance of switch Port Security in safeguarding networks from unauthorized access.
Learn how to implement best practices for Port Security in a workplace environment.
Familiarize with Cisco commands for enabling and configuring Port Security.
Gain knowledge of different security modes and MAC address configuration methods.
Learn how to verify Port Security settings and monitor for violations.

### Skills Learned

- Ability to disable unused ports to enhance network security.
- Proficiency in configuring Port Security features such as MAC filtering and port lockdown.
- Understanding of the three security modes: shutdown, protect, and restrict.
- Capability to set MAC addresses statically, dynamically, or using the sticky method.
- Competence in using verification commands to check Port Security status and troubleshoot issues.

### Tools Used

- CISCO Packet Tracer

### Steps

*Ref 1: Setting up an example of switch port security with 3 PCs, 1 switch and 1 laptop in a workplace.*

It's important to implement network port security in the workplace to prevent unauthorized access and rogue devices forom compromising network security. A fundamental practice is to disable unused poorts, especially in vacant offices or during guest access point setups. There are three security modes: shutdown (default), protect and restrict. Each mode has different responses to unauthorized devices. The shutdown mode disables the port upon a violatioon, while protect and restrict modes allow known MAC addresses but differ in notification handling. MAC addresses can be configured statically, dynamically, or using MAC address sticky with sticky being preferred for ease of management. Static addresses require manual entry, while dynamic addresses are learned automatically but not retained after a reboot. 

![image](https://github.com/user-attachments/assets/45fea850-cda8-4504-ac69-d9ba64863f44)

*Ref 2: Using the CLI command to see if there are port security on any of the switch ports.*

We use the statement "en" - to enable privilage exact mode, and "sh port-security" to show if port security has been set up for the switch ports. Nothing showed up then we use "sh port-security interface fa0/1" to give us more information on the port security provided. As we look closely port security is disabled and violation mode is set to shutdown, which is the default violation mode.

![image](https://github.com/user-attachments/assets/d7416e7c-4744-46d9-8a38-a0049d752da3)

### 1st Scenario - MAC address: Static, violation mode: Protect 

For the first scenario we are going to set up the device MAC addresses as static and then the violation mode to oprotect. Take note before we start configuring the switch with port security that it is disabled by default so you have to manually enable it by using commands and also you can only configure port security on access ports you can't do this on trunk ports or eitehr channel ports.

*Ref 3: Finding the MAC address for PC3 which is "0002.1769.5791" (click on PC3 > Config > FastEthernet0)*

![image](https://github.com/user-attachments/assets/ccd658aa-87de-49ef-9ffc-5629ddcbe652)

*Ref 4: Using the CLI command on the switch to configure port security*

Go to the switch and type in command "en > conf t > int-fa0/1" (enable privilage mode, configure terminal and interface number which is fa0/1). From there type in command "switchport mode access > switchport port-security > switchport port-security maximum 2 > switchport port-security violation protect > switchport port-security mac-address 0002.1769.5791" (type in switch port port security and press enter, there we have enabled port security. Next parameter that we are going to doo is to specifiy how many maximum machines we're going to allow on the switch port; which is 2 from the example. Next parameter we can specify what kind of violation mode we want, in our case we want to set our violation mode as protect. So to do so we type in switch port port security and violation and type in protect because we wanted to specify that we want to protect. Next we're going to do a static method for the MAC address, let's type in the command switchport port-security mac-address 0002.1769.5791. And to verify if our command works we have to type in command sh port-security interface fa0/1.

![image](https://github.com/user-attachments/assets/2465956d-1810-4719-98d9-6b84b57260cc)

*Ref 5: Using two more verification commands to see if port security is enabled*

Type in sh port-security or sh port-security address. 

![image](https://github.com/user-attachments/assets/19c218d3-4d31-4d7a-ac98-8883631da6ab)

### Scenario 2 - Using MAC address sticky and having our violation as shutdown

*Ref 6: Using the same switch we're gonna set up the MAC address stick and violation as shutdown for the second PC, PC4*

First step is to enable port security then type in int fa0/2, for interface number fa0/2. Then we need to make sure tha tan access port is enable so we type in switchport mode accesss and then type in switchpoort port-security then switchport port-security mac-address sticky. We type in sticky instead of a mac addresss oof the machine. We don't need to set up violation mode to shutdown since it's set up by default. 

![image](https://github.com/user-attachments/assets/d889f156-de77-440f-a180-8dfeeab34eea)

And to verify if its configured properly we type in sh port-security int fa0/2, sh port-security, or port-security address. Now this shows that two MAC address has port security set up. One is set up with protect as a security action and the other as shutdown. They're configured properly. *Ref 7*

![image](https://github.com/user-attachments/assets/780d993f-1da6-4871-a055-38262d01d2b8)

If you want to set up port security for a range of ports, for example fa0/03-10, violation as protect and mac address as sticky. Type in command interface range fa0/03-10, switch port-security violation protect and switch port-security mac-address sticky. *Ref 8*

![image](https://github.com/user-attachments/assets/7640a1e2-7a37-452e-bdb2-1e3f3dcca00b)




