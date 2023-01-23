IT infrastructure
=================

How to connect to the LAN from SWAN 
-----------------------------------

To connect a computer to the LAN connect it via ethernet to any outlet with the "Uni" label. (TODO: label the outlets!). The computer needs to be configured with a static IP, with the following settings:

| **IP:** 192.168.113.XXX (XXX can be any number between 1 and 255, please verify that the IP is not used in the list of computers below)
| **Subnet mask:** 255.255.255.0 (or 24 if the mask length is required)
| **Gateway:** 192.168.113.2
| **DNS:** 8.8.8.8



List of computers
-----------------

+-------------------------------+---------------------+----------------+-------------------------+
| Device                        | IP                  | User Name      | Location                |
+===============================+=====================+================+=========================+
| Server                        | 192.168.113.2       | lhep           | Server room             | 
+-------------------------------+---------------------+----------------+-------------------------+
| Remote desktop thin client    | 192.168.113.4       | -              | Control room            |
+-------------------------------+---------------------+----------------+-------------------------+
| Tower PC                      | 192.168.113.5       | lhep           | Physics Lab             |
+-------------------------------+---------------------+----------------+-------------------------+
| Gamma spectrometer PC         | 192.168.113.67      | SWAN-HPGe      | Physics lab             |
+-------------------------------+---------------------+----------------+-------------------------+
| UniBEaM DAQ                   | 192.168.113.175     | User           | Physics lab             |
+-------------------------------+---------------------+----------------+-------------------------+
| raspberry PI - PI2            | 192.168.113.176     | lhep           | BTL bunker              |
+-------------------------------+---------------------+----------------+-------------------------+
| Lynx (gamma spectrometer)     | 192.168.113.177     | -              | Physics lab             |
+-------------------------------+---------------------+----------------+-------------------------+
| Raspberry Pie for Bellow      | 192.168.113.222     | remote_user    | Power supply room       |
+-------------------------------+---------------------+----------------+-------------------------+
| MBL power supply - X Steering | 192.168.113.230     | -              | Power supply room       |
+-------------------------------+---------------------+----------------+-------------------------+
| MBL power supply - Y Steering | 192.168.113.231     | -              | Power supply room       |
+-------------------------------+---------------------+----------------+-------------------------+
| MBL power supply - X Focusing | 192.168.113.232     | -              | Power supply room       |
+-------------------------------+---------------------+----------------+-------------------------+
| MBL power supply - Y Focusing | 192.168.113.233     | -              | Power supply room       |
+-------------------------------+---------------------+----------------+-------------------------+
| Power distribution unit       | 192.168.113.240     | -              | BTL bunker              |
+-------------------------------+---------------------+----------------+-------------------------+
| CZT motor controller          | 192.168.113.241     | -              | BTL bunker              |
+-------------------------------+---------------------+----------------+-------------------------+
| Cyclotron bunker video server | 192.168.113.242     | root           | Airlock                 |
+-------------------------------+---------------------+----------------+-------------------------+
| BTL bunker video server       | 192.168.113.243     | root           | Airlock                 |
+-------------------------------+---------------------+----------------+-------------------------+

How to connect to the SWAN VPN
------------------------------


**Windows:**

What follows is a step-by-step guide for connecting to the VPN in the case of a Windows computer. If you are using another operating system you need to use a different client.
The procedure is the following:

#.	Install the OpenVPN client from ` here <https://openvpn.net/community-downloads/>`_
#.	Copy your certificate and configuration files in a folder of your choice in your computer. For (e.g.  C:\\Users\\<user_name>\\Documents\\openvpn\\)
#.	Edit lines 88, 89, 90 and 108 of the client_template.ovpn file (you can rename it if you want), and replace the following strings:

	*	<path to keys folder>: the folder path where you copied the files (e.g C:\\Users\\<user_name>\\Documents\\openvpn\\). Pay attention to use the double inverted slash \\\\ instead of the single \\ !!!
	*	<client_name>: the name of your certificate file.

#.	Locate the OpenVPN-GUI icon next to the windows clock. If it is not there, you have to execute the OpenVPN-GUI application (which you installed in point 1) and normally it should appear.
#.	Right click on the icon and click “Import file”, locate the configuration file that you edited in point 3 and import it.
#.	Right click again on the OpenVPN-Gui icon and click connect. If the connection is successful you should get a message telling you that you are connected to the VPN. Now you can access all the computers in the lab using remote desktop, as if you were at SWAN.

**Note**: by default, the OpenVPN client will try to establish a connection at the computer startup. If you want to change this behavior you can go to Settings and disable the option “Launch on Logon”.

**Mac:**

#. Install `Tunnelblick <https://tunnelblick.net/downloads.html>`_ open source VPN client
#. Files you need:
	*	<client name>.ovpn
	*	<client name>.key
	*   <client name>.crt
	*   ca.crt
	*   ta.key
	
#. Make sure that in the .ovpn file the lines 88 - 90 contain the following::

	88. cr “< copy path of your ca.crt file into here! >“
	89. cert “< copy path of your <client name>.crt file into here! >“
	90. key “< copy path of your <client name>.key file into here! >“
	
	(You need to replace the text above with your files' path)
	
#. Drag and Drop your .opvn file into Tunnelblick’s Configuration Window.


	.. figure:: images/IT/swanvpn_mac_image1.png
	
	   In case of error, make sure that your paths are edited correctly within your .opvn file.


#. Go to Tunnelblick’s *Dienstprogramme* submenu (Utilities) and click on the second button "Tunund Tap-Systemerweiterungen installieren…"

	.. figure:: images/IT/swanvpn_mac_image2.png

#. This won’t be possible at first, as under the new MacOS (Sierra (?) and newer) some security
setting have to be changed. This is done as follows:
	
	#. Go to your Mac’s "Security \& Privacy" settings in your System Preferences
	#. Under the "General" Tab click the "Details …" button:

		.. figure:: images/IT/swanvpn_mac_image3.png
	
	#. The System will ask you to change your Computer’s Security policy and allow also nonapple-controlled software to make changes in your system. This is needed for Tunnelblick to work.
	#. Turn off your computer and turn it on again with a long press on the power button. Keep the Power button pressed until you enter your Computer’s advanced settings menu.
	#. Choose "Options"
	#. On the bar on the top of your screen chose "Utility settings" (*Dienstprogramme*) > Startup Security Utility (*Startsicherheitsdienstprogramm*)
	#. Select your main volume
	#. In this window, select the reduced security option and make sure the first of the two checkboxes is checked:

		.. figure:: images/IT/swanvpn_mac_image4.png
		
	#. Click "Ok" and restart your Mac
	#. Go back to your "Security \& Privacy" Settings tab within your System Preferences.
	#. Click the "Details" button again and make sure that the checkbox for "Jonathan Bullard" is activated, such that the Tunnelblick add-ons can be installed.

		.. figure:: images/IT/swanvpn_mac_image5.png

#. Go back to Tunnelblick, deinstall the add-ons and reinstall them.
#. The VPN connection should now work as intended.
	
	
	
