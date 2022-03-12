**Waves of Interference 5G lab**

This in an indepedent sub-project of IN-SIGHT.it in which Niels ten Oever, Maxigas, and Jeroen de Vos seek to construct critical interpretative frames by analysing governance processes and implementations that make sense of the 5G phenomena and its infrastructural ecology.

To provide this research project with a strong theoretical, technical, and social foundation, we have developed a [position paper](https://raw.githubusercontent.com/in-sight-it/in-sight-it.github.io/gh-pages/assets/Peoples5GLabPostitionPaper.pdf). Comments on this position paper are very welcome, and we seek to update the document when new insights arise. Previous versions will be stored here as well.  

The research currently has two going parts:

**1. Examinging social media platforms and website to identify interpetative frames of 5G**
  
  Initial work on this has been done during the [Digital Methods Initiative Winterschool](https://wiki.digitalmethods.net/Dmi/WinterSchool2021Infodemic5G)
    
**2. Constructing experimental 5G networks through a 5G lab**
  
  We aim to critically examine different network designs and affordances that become possible through the implementation 5G standards. 
  
  We aim to use our findings to make 5G technologies more insightful to a larger audience through visualizations and interactions that inform citizen engagement with standard setting, polticy making, and technology development.
  
## Current project:
  - [DONE] Get 4G LTE network working
  - [DONE] Get 5G network working
  - [DONE] Program SIM cards 
  - [DONE] Register software devices to network (UERANSIM)
    	- Short halt because of broken GPS DO - ordered new one from Ettus
  - [DONE] Install new GPS DO TCXO
  - [DONE] Get radio network working and register on the network  
	- Phones are not picking up radio network, might be cheap 4G antenna?  
	- Try with logarithmic antennae  
  	- Was not an issue with antennae but with a config in the dockers, was fixed with a git pull - always use updated software kids :)  
  	- Purchased new antennae from Ettus
  - [In Progress] Registration works until Osmohlr kicks us off the network, see: https://github.com/herlesupreeth/docker_open5gs/issues/74
  		- tried to make changes to oshmohlr.cfg
  			hlr
			 subscriber-create-on-demand 5 cs+ps
	          to no avail
  - [In Progress] Visualize 5G network traffic on laptop
  	- Weavescope & ctop & sysdig & sysdiginspect
  - [In Progress] Visualize 5G network traffic on LED cube
  	- New code (!) <https://github.com/agtoever/tcpdump2led/blob/master/tcpdump2led.py>
  - [Next] Run edge services in 5G network
  	- Ideally a service that uses precise geolocation and timing date from the network
  - [Next] Visualize edge services in 5G on laptop
  - [Next] Visualize edge services in 5G on laptop on LED cube
  - [Next] Use synth to add audio to visualization

## Equipment
    
### Hardware
  - USRP B210 SDR Kit 2x2 (70 MHz - 6GHz) - Ettus Research <https://www.ettus.com/all-products/ub210-kit/>
  - SIMs - sysmoISIM-SJA2-10p-adm sysmoISIM-SJA2 SIM + USIM + ISIM Card (10-pack)
  - ebay 100 MHz GPS Disciplined Oscillator // Failed after two months -> DON'T BE TEMPTED TO GET THIS ONE
  - Board Mounted GPSDO (TCXO) - Ettus Research <https://www.ettus.com/all-products/gpsdo-tcxo-module/>
  - Two  VERT2450 Antenna https://www.ettus.com/all-products/vert2450/
  - Several SMA Male to SMA Male RG58 50ohm Coaxial Cable SMA Plug WiFi Antenna Extension Cable Connector Adapter Pigtail
  - Geekcreit® 8x8x8 LED Cube 3D Light Square Blue LED Electronic DIY Kit

### Antennas
  - DELOCK 89614 - Antenna LTE, omnidirectioneel, outdoor
  - NAVILOCK 60554 - BeiDou & GPS-antenna / SMA / 3,0 m
  - 600M-16G Broadband Log Periodoc Antenna Directional Antenna UWB Wifi Antenna
  - UWB Log Periodic antenna 740-6000 MHz Ultra Wideband Logperiodic Antenna Board
  - 4G LTE antena outdoor SMA 12dBi Omni antenne 3G TS9 male 5m 2.4GHz CRC9 TS9 for Huawei B315 E8372 E3372 ZTE routers
  - 2 x VERT2450 Antenna https://www.ettus.com/all-products/vert2450/
  
### Tools
  - Soldering iron (Aoyue 3210)
  - Solder suction device
  - Soldering magnifying glass with LED
  - Multimeter
  - Laptop XPS13 w/ubuntu 20.04 LTS
  - Gaggia Classic Espresso Machine
 

### Software
  - Ubuntu 22.04 LTS (as development platform (Debian doesn't support new laptop hardware, newer Ubuntu versions are not supported by all drivers, leading to significant issues with software dependencies when building everything from source). 
  - UHD (to talk to the B210: <https://github.com/EttusResearch/uhd>)
  - GNURadio (to experiment with the B210 and understand its concepts: <https://github.com/gnuradio/gnuradio>)
  - Open5Gs (excellently dockerized here: <https://github.com/herlesupreeth/docker_open5gs>)
  - Portainer (vizualise, inspect, and monitor dockers)
  - Weavescope & ctop & sysdig & sysdiginspect (to visualize traffic between containers)
  - Ledcube firmware (<https://github.com/yarivkeinan/8x8x8-led-cube-firmware>)
  - Ledcube serial access JTAG (<https://github.com/tomazas/ledcube8x8x8>)
  - Ledcube Java program to control LEDS (and Hex data stream standard) <https://github.com/tomazas/DotMatrixJava>
  - PySim (to read+write SIMcards: <https://github.com/osmocom/pysim>)  
  	- for PySim to run on Ubuntu 22.04 one needs to install pcscd and pcsc-tools and start the daemon:  
  		- $ sudo apt install pcscd pcsc-tools  
		- $ sudo service pcscd start  
	- Follow PySim installation instructions and $ python3 ./pySim-read.py -p0 (or -p1) should work  
	
### Config
  - Change the environment file (.env) in docker_open5gs
	  - MCC 204 #which is the code for NL
	  - MNC 42 #which is an unused operator number
	  - Card 1
~~~

		$ python3 ./pySim-prog.py -p 0 -t sysmoISIM-SJA2 -n Peoples5GLab -a 43284945 -x 204 -y 42 -i 204420000000001 -s 8988211000000472202 -o C10CB11F8743F39B3E73A61A772794BF -k 1FE6F93E061AF90A57DC00631F324CCC
		Using PC/SC reader interface
		Ready for Programming: Insert card now (or CTRL-C to cancel)
		Generated card parameters :
			 > Name     : Peoples5GLab
			 > SMSP     : e1ffffffffffffffffffffffff0581005155f5ffffffffffff000000
			 > ICCID    : 8988211000000472202
			 > MCC/MNC  : 204/42
			 > IMSI     : 204420000000001
			 > Ki       : 1FE6F93E061AF90A57DC00631F324CCC
			 > OPC      : C10CB11F8743F39B3E73A61A772794BF
			 > ACC      : None
			 > ADM1(hex): 3433323834393435
			 > OPMODE   : None
~~~
 
	  - Card 2 
~~~

	  	$ python3 ./pySim-prog.py -p 0 -t sysmoISIM-SJA2 -n Peoples5GLab -a 94800032 -x 204 -y 42 -i 204420000000002 -s 8988211000000472293 -o A84E9EB56739F7F30735004E020D3D2B -k E31AA81800AA6CCD13E0DC6FA656363F  
		Using PC/SC reader interface
		Ready for Programming: Insert card now (or CTRL-C to cancel)
		Generated card parameters :
			 > Name     : Peoples5GLab
			 > SMSP     : e1ffffffffffffffffffffffff0581005155f5ffffffffffff000000
			 > ICCID    : 8988211000000472293
			 > MCC/MNC  : 204/42
			 > IMSI     : 204420000000002
			 > Ki       : E31AA81800AA6CCD13E0DC6FA656363F
			 > OPC      : A84E9EB56739F7F30735004E020D3D2B
			 > ACC      : None
			 > ADM1(hex): 3934383030303332
			 > OPMODE   : None

~~~

  
### Hardware failure
  - Cheap hardware failure. Lesson learned: do not buy cheap hardware.
  - The ebay OCXO GPSDO failed after two months with:
		  	$ ./sync_to_gps  

~~~

		Creating the USRP device with: ...
		[INFO] [UHD] linux; GNU C++ version 9.3.0; Boost_107100; UHD_3.15.0.0-release
		[INFO] [B200] Detected Device: B210
		[INFO] [B200] Operating over USB 3.
		[INFO] [B200] Detecting internal GPSDO.... 
		[INFO] [GPS] Found a generic NMEA GPS device
		[INFO] [B200] Initialize CODEC control...
		[INFO] [B200] Initialize Radio control...
		[INFO] [B200] Performing register loopback test... 
		[INFO] [B200] Register loopback test passed
		[INFO] [B200] Performing register loopback test... 
		[INFO] [B200] Register loopback test passed
		[INFO] [B200] Setting master clock rate selection to 'automatic'.
		[INFO] [B200] Asking for clock rate 16.000000 MHz... 
		[INFO] [B200] Actually got clock rate 16.000000 MHz.
		Using Device: Single USRP:
		  Device: B-Series Device
		  Mboard 0: B210
		  RX Channel: 0
		    RX DSP: 0
		    RX Dboard: A
		    RX Subdev: FE-RX2
		  RX Channel: 1
		    RX DSP: 1
		    RX Dboard: A
		    RX Subdev: FE-RX1
		  TX Channel: 0
		    TX DSP: 0
		    TX Dboard: A
		    TX Subdev: FE-TX2
		  TX Channel: 1
		    TX DSP: 1
		    TX Dboard: A
		    TX Subdev: FE-TX1

		Synchronizing mboard 0: B210

		**************************************Helpful Notes on Clock/PPS Selection**************************************
		As you can see, the default 10 MHz Reference and 1 PPS signals are now from the GPSDO.
		If you would like to use the internal reference(TCXO) in other applications, you must configure that explicitly.
		You can no longer select the external SMAs for 10 MHz or 1 PPS signaling.
		****************************************************************************************************************

		Waiting for reference lock....LOCKED
		[WARNING] [GPS] update_cache: Malformed GPSDO string: $GPGGA,002811.058,0000.0000,N,00000.0000,E,0,00,,,M,,,,0000*09
		[WARNING] [GPS] update_cache: Malformed GPSDO string: $GPGGA,002811.058,0000.0000,N,00000.0000,E,0,00,,,M,,,,0000*09
		[WARNING] [GPS] update_cache: Malformed GPSDO string: $GPGGA,002811.058,0000.0000,N,00000.0000,E,0,00,,,M,,,,0000*09
		[WARNING] [GPS] update_cache: Malformed GPSDO string: $GPGGA,002811.058,0000.0000,N,00000.0000,E,0,00,,,M,,,,0000*09

		Error: ValueError: locked(): unable to determine GPS lock statusThis could mean that you have not installed the GPSDO correctly.

		Visit one of these pages if the problem persists:
		 * N2X0/E1X0: http://files.ettus.com/manual/page_gpsdo.html * X3X0: http://files.ettus.com/manual/page_gpsdo_x3x0.html

		 * E3X0: http://files.ettus.com/manual/page_usrp_e3x0.html#e3x0_hw_gps
		 
  - The new Ettus TCXO arrived and it gives me an excellent lock:
  
		  	$ /usr/lib/uhd/examples/sync_to_gps  

		Creating the USRP device with: ...
		[INFO] [UHD] linux; GNU C++ version 9.3.0; Boost_107100; UHD_3.15.0.0-release
		[INFO] [B200] Detected Device: B210
		[INFO] [B200] Operating over USB 3.
		[INFO] [B200] Detecting internal GPSDO.... 
		[INFO] [GPS] Found an internal GPSDO: GPSTCXO, Firmware Rev 0.929b
		[INFO] [B200] Initialize CODEC control...
		[INFO] [B200] Initialize Radio control...
		[INFO] [B200] Performing register loopback test... 
		[INFO] [B200] Register loopback test passed
		[INFO] [B200] Performing register loopback test... 
		[INFO] [B200] Register loopback test passed
		[INFO] [B200] Setting master clock rate selection to 'automatic'.
		[INFO] [B200] Asking for clock rate 16.000000 MHz... 
		[INFO] [B200] Actually got clock rate 16.000000 MHz.
		Using Device: Single USRP:
		  Device: B-Series Device
		  Mboard 0: B210
		  RX Channel: 0
		    RX DSP: 0
		    RX Dboard: A
		    RX Subdev: FE-RX2
		  RX Channel: 1
		    RX DSP: 1
		    RX Dboard: A
		    RX Subdev: FE-RX1
		  TX Channel: 0
		    TX DSP: 0
		    TX Dboard: A
		    TX Subdev: FE-TX2
		  TX Channel: 1
		    TX DSP: 1
		    TX Dboard: A
		    TX Subdev: FE-TX1

		Synchronizing mboard 0: B210

		**************************************Helpful Notes on Clock/PPS Selection**************************************
		As you can see, the default 10 MHz Reference and 1 PPS signals are now from the GPSDO.
		If you would like to use the internal reference(TCXO) in other applications, you must configure that explicitly.
		You can no longer select the external SMAs for 10 MHz or 1 PPS signaling.
		****************************************************************************************************************

		Waiting for reference lock....LOCKED
		GPS Locked
		USRP time: 1623256927.000000000
		GPSDO time: 1623256927.000000000

		SUCCESS: USRP time synchronized to GPS time

~~~

   Funny detail: When I ran it the first time the malformed string from the previous GPS DO was apparently still in the cache, causing me to freak out for a moment!! 
   		[WARNING] [GPS] update_cache: Malformed GPSDO string: GPSTCXO, Firmware Rev 0.929b

   Some more detail:  

~~~
			$ /lib/uhd/utils/query_gpsdo_sensors   

		[Creating the USRP device with: ...
		INFO] [UHD] linux; GNU C++ version 9.3.0; Boost_107100; UHD_3.15.0.0-release
		[WARNING] [UHD] Unable to set the thread priority. Performance may be negatively affected.
		Please see the general application notes in the manual for instructions.
		EnvironmentError: OSError: error in pthread_setschedparam
		[INFO] [B200] Detected Device: B210
		[INFO] [B200] Operating over USB 3.
		[INFO] [B200] Detecting internal GPSDO.... 
		[INFO] [GPS] Found an internal GPSDO: GPSTCXO, Firmware Rev 0.929b
		[INFO] [B200] Initialize CODEC control...
		[INFO] [B200] Initialize Radio control...
		[INFO] [B200] Performing register loopback test... 
		[INFO] [B200] Register loopback test passed
		[INFO] [B200] Performing register loopback test... 
		[INFO] [B200] Register loopback test passed
		[INFO] [B200] Setting master clock rate selection to 'automatic'.
		[INFO] [B200] Asking for clock rate 16.000000 MHz... 
		[INFO] [B200] Actually got clock rate 16.000000 MHz.
		Using Device: Single USRP:
		  Device: B-Series Device
		  Mboard 0: B210
		  RX Channel: 0
		    RX DSP: 0
		    RX Dboard: A
		    RX Subdev: FE-RX2
		  RX Channel: 1
		    RX DSP: 1
		    RX Dboard: A
		    RX Subdev: FE-RX1
		  TX Channel: 0
		    TX DSP: 0
		    TX Dboard: A
		    TX Subdev: FE-TX2
		  TX Channel: 1
		    TX DSP: 1
		    TX Dboard: A
		    TX Subdev: FE-TX1

		Setting the reference clock source to "gpsdo"...
		Clock source is now gpsdo
		Setting the reference clock source to "gpsdo"...
		Time source is now gpsdo
		Waiting for ref_locked...USRP Locked to Reference.
		**************************************Helpful Notes on Clock/PPS Selection**************************************
		As you can see, the default 10 MHz Reference and 1 PPS signals are now from the GPSDO.
		If you would like to use the internal reference(TCXO) in other applications, you must configure that explicitly.
		****************************************************************************************************************
		Waiting for the GPSDO to warm up...
		The GPSDO is warmed up and talking.

		GPS does not have lock. Wait a few minutes and try again.
		NMEA strings and device time may not be accurate until lock is achieved.


		Trying to align the device time to GPS time...
		GPS and UHD Device time are aligned.
		last_pps: 1624027114 vs gps: 1624027114.
		Printing available NMEA strings:
		GPS_GPGGA: $GPGGA,143834.00,5221.2515,N,00451.2612,E,0,05,3.2,21.0,M,45.9,M,,*5B 
		GPS_GPRMC: $GPRMC,143834.00,V,5221.2515,N,00451.2612,E,0.2,0.0,180621,,*23 
		GPS Epoch time at last PPS: 1624027115.00000 seconds
		UHD Device time last PPS:   1624027115.00000 seconds
		UHD Device time right now:  1624027115.01646 seconds
		PC Clock time:              1624027112 seconds

		Done!
~~~
  
## Videos
  - [Installing the GPS-DO](https://www.youtube.com/watch?v=HrnWpnW-Gfg)
  - [Casemodding to fit GPS-DO](https://www.youtube.com/watch?v=V1i42qqgNYY)

### Workshop outline
  - Ask people to communicate a complex standards over a distance without using their voice
  - Let people communicate using the semaphore flags standard
  - Introduce morse and show that was used in telegraph communications
  - Show by using led cube how a network transmits more signal
  - Show with led cube evolution of complexity from telegraph, to PSTN (circuit switching), GSM (mobility), 3G (data), 4G (everything over IP), 5G (more microservices and edge computing).

## Acknowledgents
  - Albert ten Oever, LAG Hackerspace, Arnd 'Justa' TechInc

  
