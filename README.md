                                                                                                      
**<p style="text-align: center;">Configuration of TYT MD-750 Digital Radio</p>**
<p style="text-align: center;">Rev. 1.0, September 2023, Andrzej SP5GW</p>
<p align="center">
<img src="./img/md750.png" width="900" height="200"/>
</p>

**Software Installation on the PC**

Installation of Programming Application

Generally this part does not cause any problems. At the time of writting this manual download section of official Tytera page did not work (https://www.tyt888.com/download.html). Installer for the application has been downloaded from https://radiostrefa.eu/pl/p/Radiotelefon-TYT-MD-750-DMR-FM-VHFUHF/676 (pliki do pobrania). Downloaded repository titled *"TYT-Oprogramowanie-2"* includes zip repo called *"MD-750 Driver and Software"*, which included two subfolders: *C7000xxxx* and *xxxxv1.0.8*. First directory includes USB driver, which missed digital signature so it can be omitted. Second subfolder includes application installer, which shall be executed. At this stage it will be not possible to communicate with radio device until devices USB driver has been successfuly installed 
(see next step). 

Installation of C7000 device usb driver

It is not easy to find working usb driver for C7000 device. Package, which seems to work can be downloaded from: https://amaradio.cz/problem-s-driverem-k-tyt-md-750-vyresen/. Repository USB-driver shall be extrcted and then file "usblib_hrc7000"* from it shall be executed in Administrator mode (right click on the file and select option Run as Administrator). As a result  popup Save As ... is displayed. This shall be ignored. After a while Windows confirms that driver has been successfuly installed. In my case to get TYT Programming cable/radio properly configured in Windows, I had to go to device manager (right clik on Windows icon in Win 11 and select device manager). From there I had to locate C7000 walkie-takie and right click on it/select upgrade driver. This action creates device catalog lib-usbwin32 devices, which includes walkie-talkie-C7000 device in working state. As a results of above steps you shall be able to start MD-750 app and read configuration from MD-750 device (Program -> Read). If there is still a problem with usb driver then you read operation will fail. It is assumed that prior to read attempt MD-750 has been connected to PC using supplied usb programming cable. Radio must be also switched on.

It is critical when defining channels in programming application to add them to the Zone. If this step is skipped channels will not be visible in radio's menu...

**Basic MD-750 radio operation**

OK - access to menu  
P1 - toggle between VFOs  
P2 - toggle between channel and VFO mode. In VFO mode (no channel number displayed next to frequency) you can input frequency directly from the keyboard.

Device configuration for radio's menu

		- 	OK -> SET -> Radio Set - access radio settings menu (to go back press BACK, to move arround use up/down keys)    
		- 	OK -> SET -> Radio Set -> (2) Squelsh:0 - to hear noise and be sure radio is in operation  
		- 	OK -> SET -> Radio Set -> (3) TX Power:Low - to set output power to low (about 1W)  
		- 	OK -> SET -> Radio Set -> (5) Band:Narrow - to set narrodband FM (important for some repeaters)  
		- 	OK -> SET -> Radio Set -> (9) Double-Wait:Single Wait (change between VFOs is done using P1 button)  
		- 	OK -> SET -> Radio Set -> (11) Beep -> Call Permit:Analog  
		-   OK -> Zone -> Toggle between defined zones (zones group channels available from the radio's menu)
		
		- 	OK -> SET -> Channel CFG -> (6) Freq Step:12.5k (according IARU Region 1 2m band plan)

Channel Configuration in Analog Mode

		- 	OK -> SET -> Channel CFG -> (7) Channel Type:FM - to put radio into analog mode
	
		Now you can go back to top menu level from where you can directly set radio frequecny.   
		After pushing PTT button you will be able to transmit. When you are trasmitting LED on the top of the radio  
		changes from Green to Red.
		
		Configuring Analog Repeater from Radio Keypad    
			We will use SR5WP (FM-Link repeater), its parameters are:    
			TX Frequency: 438.6250MHz    
			RX Frequency: 431.0250MHz (offset: -7.1MHz)  
			CTCSS 127.3 Hz (transmitter and activation)

		Detailed information regarding repeater configuration can be found under the links below:
			przemienniki.net 
			fm-link.pl 
		Alternative method to define repeater from radio menu using offset (did not always worked for me due to  
		lack of offset availability in radio's menu)  
		Sierra Echo youtube video with step by step configuration (alternative configuration method using offset)  
		https://www.youtube.com/watch?v=RDXTbgtwDEY
		
		The easiest way to define radio channel is via programming Software

		- 	VFO -> Mode:Analog Set both VFOs to Analog mode
		- 	Channel -> Add (Right Click on Channel) 
		- 	Channel -> Add -> Mode:Analog
		- 	Channel -> Add -> Name:SR5WP
		- 	Channel -> Add -> RX Freq.:438.6250MHz
		- 	Channel -> Add -> TX Feq.:431.0250MHz
		- 	Channel -> Add -> Squelsh Level:0
		- 	Channel -> Add -> Bandwith:12.5kHz
		- 	Channel -> Add -> Tx Tone:127.3Hz
		- 	Channel -> Add -> Rx Tone: 127.3Hz

		- 	Zone -> Add (Right Click on Zone) -> Move new channel listed from Available to Member

		- 	File -> Save:save configuration locally on the computer
		- 	Program -> Write (write new configuration to the radio)

Channel Configuration in Digital Mode

        In order to be able to attach to DMR network you need to register on radioid.net portal. This is mandatory  
        step in order to obtain Radio ID (DMR ID) parameter, which needs to be used as part of your equipment  
        configuration. After your application has been approved you will receive two Radio ID numbers. Use the one  
        with remark: DMR in subsequent configuration steps of this manual.

    	Configuring Digital DMR Repeater
    	 
        We will use SR5WU (DMR repeater located in Warsaw-Ursynow), its parameters are:
            TX Frequency: 438.7750MHz
            RX Frequency: 431.1750MHz
            Offset: -7.6MHz 
            Color Code: 5

        More information regarding available DMR repeaters can be found at:
	        przemienniki.net
	        radioid.net
	        brandmiester.network
	        sp-dmr.pl

        Information regarding existing talking groups in Poland can be found at   
        https://wiki.brandmeister.networkindex.php/Poland

		The easiest way to define radio channel is via programming Software        

		-  General Setting -> RadioID: 2601994

        Define group calls you will be listening to/transmitting:
		-  Contact -> Digital Contact -> Add -> Group Call -> Name: TG260=SP (DMR Group for Poland)
		-  Contact -> Digital Contact -> Add -> Group Call -> Call Id: 260

        Assign groups you defined in previous step to Rx Group List
        (Idea here is that you can listen to multiple groups)
		-  Rx Group List -> Create Group called Groups and move Group Call Contacts there


		-  Channel -> Add (Right Click on Channel) 
		-  Channel -> Add -> Mode:Digital
		-  Channel -> Add -> Name:SR5WU
		-  Channel -> Add -> RX Freq.:438.77500MHz
		-  Channel -> Add -> TX Feq.:431.17500MHz
		-  Channel -> Add -> Squelsh Level:0
		-  Channel -> Add -> Rx Group List:Groups
		-  Channel -> Add -> Color Code: 5
		-  Channel -> Add -> Contact: TG260-SP (this is the group you will transmit to)
		-  Channel -> Add -> Slot: 1

		-  Zone -> Add -> Rename:Digi_SR5
		-  Add SR5_WU channel to Digi_SR5 using gui
            
		-  File -> Save:save configuration locally on the computer
		-  Program -> Write (write new configuration to the radio)

Example configuration files, wchich can be loaded to TYT programming software can be found in directory: ./RAdio Configuration Files