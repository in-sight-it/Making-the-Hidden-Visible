This in an indepedent sub-project of IN-SIGHT.it in which Niels ten Oever, Maxigas, and Jeroen de Vos seek to construct critical interpretative frames by analysing governance processes and implementations that make sense of the 5G phenomena and its infrastructural ecology.

The research currently has two approaches:

**1. Examinging social media platforms and website to identify interpetative frames of 5G**
  
  Initial work on this has been done during the [Digital Methods Initiative Winterschool](https://wiki.digitalmethods.net/Dmi/WinterSchool2021Infodemic5G)
    
**2. Constructing experimental 5G networks through a 5G lab**
  
  We aim to critically examine different network designs and affordances that become possible through the implementation 5G standards. 
  
  We aim to use our findings to make 5G technologies more insightful to a larger audience through visualizations and interactions that inform citizen engagement with standard setting, polticy making, and technology development.
  
## Current project:
  - [DONE] Get 4G LTE network working
  - [DONE] Get 5G network working
  - [In Progress] Program SIM cards to get range of devices registered to network
  - [In Progress] Visualize 5G network traffic on laptop
  - [In Progress] Visualize 5G network traffic on LED cube
  - [Next] Run edge services in 5G network
  - [Next] Visualize edge services in 5G on laptop
  - [Next] Visualize edge services in 5G on laptop on LED cube
  - [Next] Use synth to add audio to visualization

## Equipment
    
### Hardware
  - USRP B210 SDR Kit 2x2 (70 MHz - 6GHz) - Ettus Research <https://www.ettus.com/all-products/ub210-kit/>
  - SIMs - sysmoISIM-SJA2-10p-adm sysmoISIM-SJA2 SIM + USIM + ISIM Card (10-pack)
  - 100 MHz GPS Disciplined Oscillator (I should have gotten the 10 MHz one)
  - Several SMA Male to SMA Male RG58 50ohm Coaxial Cable SMA Plug WiFi Antenna Extension Cable Connector Adapter Pigtail
  - Geekcreit® 8x8x8 LED Cube 3D Light Square Blue LED Electronic DIY Kit

### Antennas
  - DELOCK 89614 - Antenna LTE, omnidirectioneel, outdoor
  - NAVILOCK 60554 - BeiDou & GPS-antenna / SMA / 3,0 m
  - 600M-16G Broadband Log Periodoc Antenna Directional Antenna UWB Wifi Antenna
  - UWB Log Periodic antenna 740-6000 MHz Ultra Wideband Logperiodic Antenna Board
  - 4G LTE antena outdoor SMA 12dBi Omni antenne 3G TS9 male 5m 2.4GHz CRC9 TS9 for Huawei B315 E8372 E3372 ZTE routers

### Software
  - Ubuntu 20.04 LTS (as development platform (Debian doesn't support new laptop hardware, newer Ubuntu versions are not supported by all drivers, leading to significant issues with software dependencies when building everything from source). 
  - UHD (to talk to the B210: <https://github.com/EttusResearch/uhd>)
  - GNURadio (to experiment with the B210 and understand its concepts: <https://github.com/gnuradio/gnuradio>)
  - PyBOMBS (to deploy GNURadio packages: <https://github.com/gnuradio/pybombs>)
  - Open5Gs (excellently dockerized here: <https://github.com/herlesupreeth/docker_open5gs>)
  - Portainer (vizualise, inspect, and monitor dockers)
  - Weavescope & ctop & sysdig & sysdiginspect (to visualize traffic between containers)
  - Ledcube firmware (<https://github.com/yarivkeinan/8x8x8-led-cube-firmware>)
  - Ledcube serial access JTAG (<https://github.com/tomazas/ledcube8x8x8>)
  - Ledcube Java program to control LEDS (and Hex data stream standard) <https://github.com/tomazas/DotMatrixJava>
  - PySim (to read+write SIMcards: <https://github.com/osmocom/pysim>)

### Tools
  - Soldering iron (Aoyue 3210)
  - Solder suction device
  - Soldering magnifying glass with LED
  - Multimeter
  - Laptop XPS13 w/ubuntu 20.04 LTS
  - Gaggia Classic Espresso Machine
  
### Workshop outline
  - Ask people to communicate a complex standards over a distance without using their voice
  - Let people communicate using the semaphore flags standard
  - Introduce morse and show that was used in telegraph communications
  - Show by using led cube how a network transmits more signal
  - Show with led cube evolution of complexity from telegraph, to PSTN (circuit switching), GSM (mobility), 3G (data), 4G (everything over IP), 5G (more microservices and edge computing).
  
## Videos
  - [Installing the GPS-DO](https://www.youtube.com/watch?v=HrnWpnW-Gfg)
  - [Casemodding to fit GPS-DO](https://www.youtube.com/watch?v=V1i42qqgNYY)

## Acknowledgents
  - Albert ten Oever, LAG Hackerspace, Arnd 'Justa' TechInc

  
