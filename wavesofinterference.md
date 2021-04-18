# Waves of Interference 5G lab

This in an indepedent sub-project of IN-SIGHT.it in which Maxigas, Niels ten Oever, and Jeroen de Vos seek to construct critical interpretative frames by analysing governance processes and implementations that make sense of the 5G phenomena and its infrastructural ecology.

The research currently has two approaches:

**1. Examinging social media platforms and website to identify interpetative frames of 5G**
  
  Initial work on this has been done during the [Digital Methods Initiative Winterschool](https://wiki.digitalmethods.net/Dmi/WinterSchool2021Infodemic5G)
    
**2. Constructing experimental 5G networks through a 5G lab**
  
  We aim to critically examine different network designs and affordances that become possible through the implementation 5G standards. 
  
  Subsequently we aims to use our findings to make 5G more insightful to a larger audience.
  
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
  - USRP B210 SDR Kit 2x2 (70 MHz - 6GHz) - Ettus Research
  - SIMs - sysmoISIM-SJA2-10p-adm sysmoISIM-SJA2 SIM + USIM + ISIM Card (10-pack)
  - 100 MHz GPS Disciplined Oscillator
  - Several SMA Male to SMA Male RG58 50ohm Coaxial Cable SMA Plug WiFi Antenna Extension Cable Connector Adapter Pigtail
  - Geekcreit® 8x8x8 LED Cube 3D Light Square Blue LED Electronic DIY Kit

### Antennas
  - DELOCK 89614 - Antenna LTE, omnidirectioneel, outdoor
  - NAVILOCK 60554 - BeiDou & GPS-antenna / SMA / 3,0 m
  - 600M-16G Broadband Antenna Directional Antenna UWB Wifi Antenna
  - UWB Log Periodieke antenne 740-6000 MHz Ultra Wideband Logperiodic Antenna Board
  - 4G LTE antena outdoor SMA 12dBi Omni antenne 3G TS9 male 5m 2.4GHz CRC9 TS9 for Huawei B315 E8372 E3372 ZTE routers

### Software
  - Open5Gs (excellently dockerized here: https://github.com/herlesupreeth/docker_open5gs )
  - PySim (to write SIMcards: https://github.com/osmocom/pysim)
  - Weavescope (to visualize traffic between containers)
  - Ledcube firmware (https://github.com/yarivkeinan/8x8x8-led-cube-firmware)
  - Ledcube serial access JTAG (https://github.com/tomazas/ledcube8x8x8)
  - Ledcube Java program to control LEDS (and Hex data stream standard) https://github.com/tomazas/DotMatrixJava

### Tools
  - Soldering iron (Aoyue 3210)
  - Magnifying glass
  - Multimeter
  - Laptop XPS13 w/ubuntu 20.10

## Videos
  - [Installing the GPS-DO](https://www.youtube.com/watch?v=HrnWpnW-Gfg)
  - [Casemodding to fit GPS-DO](https://www.youtube.com/watch?v=V1i42qqgNYY)



  
