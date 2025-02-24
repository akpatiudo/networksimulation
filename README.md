## Full Internet Simulation IN Packet Tracer Part Two: (Add Server, Configure Smart Access Point, and Connect Smartphones)
-  ![](https://i.imgur.com/PMiGI3a.png)

### Step 1: Configure the Server (Medlabtech.srv)
The server will be connected to the same switch as the PCs and will act as a central resource.
-   Connect Medlabtech.srv to the Switch
-  Physically connect the server’s Ethernet port to the switch.
-  Assign it an IP address on the same subnet as the PCs. (click on the server > Desktop)
  - Server Network Configuration
  -  Set a static IP on the server:
-![](https://i.imgur.com/67viNa5.png)
-  IP Address: 192.168.1.100
-  Subnet Mask: 255.255.255.0
-  Default Gateway: 192.168.1.1
-  DNS Server:192.168.1.100

-  **Verify Server Connectivity by run the following ping tests:**
  -  ping 192.168.1.1    # Home Router
  -  ping 203.0.113.1    # ISP Router
  -  ping 192.168.1.100        
  -  ![](https://i.imgur.com/QCA4h4g.png)
 If all pings succeed, the server is properly connected to the network.
-  **let Brows the server from the pc:**
-  click any of the pc,
-  Web browser.
-  type the server IP address on the Url: 192.168.1.100
- ![](https://i.imgur.com/k2B1fAl.png)

-  **Setup Web Page and DNS:**
-  Click the Server
-  On the HTTP and HTTPS
-  Index.html > Edith
-  Increase font to 20 or more(your Choice)
-  type >Welcome to Medlab Technology<
-  Save after you done with edithing (hit enter when it prompt you)
-  ![](https://i.imgur.com/aFOZUyl.png)
   
-  Click the Server
-  Go to Service > DNS > Name
-  Type www.medlabtech.com
-  Address type server Ip eg :192.168.1.100
-  click add > save
-  ![](https://i.imgur.com/Q5Zsj3P.png)

-  **Setup DHCP:**
-  click the Server
-  Go to Service > DHCP > On
-  Start IP Address: 192.168.1.10
-  Subnet Mask: 255.255.255.0
-  Default Gateway: 192.168.1.1
-  DNS Server:192.168.1.100
-  Number of Users 45 (as needed)
-  add and save
-  ![](https://i.imgur.com/880NMEZ.png)

###  Step 2: Configure the Smart Access Point (AP)
-  The AP provides wireless access to the network.
  Connect the AP:
  -  Physical Connection:
  -  AP (port 1) → Switch (Gig6/1)

**2.1 Configure the AP**
-  Use a console cable or access the AP web GUI (default IP: 192.168.1.50).
-  Click the AP divice, go to config
-  under interface, port 1Configure the following 
-  Set up WiFi SSID and Security:
-  ssid:   Medlab_WiFi
-  wpa2-psk:  medlab123
-  ![](https://i.imgur.com/c02l6RF.png)

### Step 3: Configure the Switch Port (For AP Connection)
-  Since the AP is connected to Switch Gig6/1, we configure this port:
-  enable
-  configure terminal
-  interface GigabitEthernet6/1
-  switchport mode access
-  switchport access vlan 1
-  spanning-tree 2portfast
-  no shutdown
-  exit
-  exit
-  copy running-config startup-config
- This ensures AP connects properly to the network.

###  Step 4: Connect Smartphones to the Smart AP
1. Smartphone WiFi Configuration
-  Go to WiFi settings on each smartphone.
-  Select SSID: Medlab_WiFi
-  Enter password: medlab123
-  Set IP to DHCP (Automatic). if it has the function
-  ![](https://i.imgur.com/qUCK8Wh.png)

**Confirm WiFi is connected.**
2. Test Connectivity
From each smartphone, run the following tests:
-  ping 192.168.1.1    # Router
-  Brows ping 192.168.1.100
-  ping 192.168.1.100  # Server
- If successful, smartphones are correctly connected to the network.
- ![](https://i.imgur.com/YwGMexk.png)

- ![](https://i.imgur.com/bUZit0C.png)

### Step 5: Troubleshooting Scenarios
-  Issue and 	Solution:
-  PCs/Server can't reach the ISP
-  Run show ip interface brief on the router.
-  Check if Gig6/0 is up and no shutdown if needed.

No internet access on the server	
-  Ensure DNS is set to 192.168.1.100 Use tracert 192.168.1.100 to check the path.
-  Smartphones can’t connect to WiFi
  -  Ensure the AP is in Access Point mode, SSID/password is correct, and DHCP is enabled.
     
-  AP is unreachable
-  Run ping 192.168.1.50 from a PC. If no response, check switch configuration (show interfaces status).
- These steps help diagnose and fix common network problems.

### Conclusion: 
-  Key Takeaways for an IT Technician
    -  By completing this network setup, we’ve learned:
    -  How to connect and configure a server, router, switch, and AP.
    -  How to assign static and dynamic IP addresses for proper routing.
    -  How to configure a wireless network for mobile device connectivity.
    - Troubleshooting techniques to identify and resolve connectivity issues.
    -  Network security practices to protect infrastructure from threats. (captured in part three)

###  Importance for an IT Technician
-  This hands-on experience is essential for network administration and troubleshooting.
-  It teaches critical thinking when diagnosing real-world network problems.
-  Understanding wired and wireless integration prepares you for enterprise network management.
- This lab is an excellent foundation for advanced networking and security topics.
- # networksimulation
