To configure an Allstar node, you first need to create an AllstarLink account and register a server.
Then, you will install the AllstarLink software (often using a pre-built image like hamvoipe.org) onto a suitable computer, such as a Raspberry Pi. The initial setup is completed by running an interactive configuration script or menu that guides you through entering your server and node information, and then you can make further adjustments by manually editing configuration files like rpt.conf. [1, 2, 3, 4, 5, 6]  

1. Create an AllstarLink account and register a server 
• Go to the AllstarLink website and sign up for an account, following the on-screen instructions. 
• Once your account is active, register a server from the portal and request a node number. You will need to provide information like the server name and location. [1, 2, 4, 7]  
• Extend the node number. This is done in the event that you want additional nodes in the future.
	• This will result in your node number (example 65922) to be "extended" to 659220 and you can add 659221 and so forth later.
• Take note of your 6 digit node number and password. We will need it later...

2. Install the AllstarLink software 
• Download to computer [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
• Download to computer [allstar3-arm64-X.Y.Z.img.xz](https://repo.allstarlink.org/images/pi/)
• Install Raspberry Pi Imager on your computer
• Follow Steps 4 through 17 -> [Step-by-Step Pi Appliance Setup](https://allstarlink.github.io/install/pi-appliance/pi-detailed/#step-by-step-pi-appliance-setup)
	• Take note of the node name. This is the name of your raspberrypi, not your allstarnode. We will get to that later.
	• Take note of the password. This is your raspberrypi user/admin password, not your allmon3 password. We will get to that later as well.
• Insert the SD card into your Raspberry Pi, connect it to your network via Ethernet, (Wifi is fine if configured) and power it on. 

3. Run the initial configuration script
• In a web browser on your computer; click the address bar and type: https://nodename.local # replacing "nodename" with the noted node name from Section 2.
• If/when prompted by a big scary "Your connection isn't private" message. Click Advanced and then click Continue to ... (unsafe). It's lying to you.
• Essentially follow Steps 21 through 24 -> [Step-by-Step Pi Appliance Setup](https://allstarlink.github.io/install/pi-appliance/pi-detailed/#step-by-step-pi-appliance-setup)
	• Hopefully you're either at a command prompt or the asl-menu prompt. If the screen is all black, type `sudo asl-menu` and press enter.
	• Alternatively, you can run the asl-menu utility manually to access the setup menu at any time. [3, 5, 6]
• Select "Node Settings" with [Enter]. Change your selection with [Tab] which is just above the [Caps Lock] button.
• Select "Allstar Node Setup Menu"
• Select "Add Node" and enter your allstar nodenumber from Section 1.
• Select "Default/manual configuration (show all settings)
• Enter Node number, password, callsign, Radio Interface (probably SimpleUSB), Duplex type (probably 1), leave everything else the same.
• Use [Tab] to navigate to <Back> and hit [Enter]
• Restart Asterisk then go <Back> again
• Go to Expert Configuration menu
• Select "Edit rpt.conf file" to open the settings file
• Edit these settings
	• hangtime = 100
	• althangtime = 200
	• remote_inact_timeout = 0
	• remote_timeout = 0
	• holdofftelem = 1
	• telemdefault = 0
• Save file and exit editor
• Restart Asterisk then <Back to Main> then <Exit Main Menu>
• Confirm exit of asl-menu

4. Create allmon3 username and password
• `sudo allmon3-passwd new_username` # replace new_username with your name or whatever
• Type `exit` to close the session.

5. Enjoy Allstar
• Go back to your computer or cell phone on the same wifi network
• Open web browser and go to: https://nodename.local/allmon3 # replacing "nodename" with the noted node name from Section 2.
• Log in with your allmon3 username and password from Section 4.
• Connect to another node and start transmitting
• Test with "Parrot Mode"
	• `rpt cmd node_num cop 21` # replace node_num with your node_num # ENABLE
	• `rpt cmd node_num cop 22` # replace node_num with your node_num # DISABLE
• Do not test with parrot while connected to another node.


[1] https://rvradionetwork.com/documents/SHARI%20Allstar%20Node%20Setup%20Procedure-Version%201.4.pdf
[2] https://wiki.allstarlink.org/wiki/Beginners_Guide
[3] https://hamprojects.info/wp-content/uploads/HamVOIP-Allstar-Node-Setup-and-Configuration-Guide-by-KG8MM.pdf
[4] https://www.youtube.com/watch?v=iCZsMFrVJlM
[5] https://wiki.allstarlink.org/wiki/ASL_FAQ
[6] https://allscan.info/docs/diy-node.php
[7] https://kits4hams.com/wp-content/uploads/2024/04/SHARI-PiHat-Allstar-Node-Setup-Procedure-Version-2.00.pdf
[8] https://www.youtube.com/watch?v=7LB6D2FLGZk
[9] https://www.youtube.com/watch?v=QkO6dk8cdEs
[10] https://www.youtube.com/watch?v=tpLL0hGAqPM
[11] https://www.youtube.com/watch?v=k0iP4dECx6A
[12] https://community.allstarlink.org/t/first-time-node-setup/17861

