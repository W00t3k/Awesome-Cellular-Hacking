# Awesome Cellular Hacking - Complete Collection 2025

> A comprehensive curated list of resources for 2G/3G/4G/5G cellular security research and analysis

This repository consolidates community knowledge in the cellular security space, including exploits, research papers, tools, and educational resources. The goal is to preserve and organize important security research that might otherwise become difficult to find.

**⚠️ Disclaimer:** This information is intended for educational and defensive security research purposes only. Use responsibly and in compliance with applicable laws and regulations.

## 📋 Table of Contents

- [Rogue Base Stations](#️-rogue-base-stations)
- [Recent Updates (2024-2025)](#-recent-updates-2024-2025)
- [Software & Tools](#️-software--tools)
- [Hardware Setup](#-hardware-setup)
- [Testing & Research Methodologies](#-testing--research-methodologies)
- [Attack Vectors](#️-attack-vectors)
- [Conference Talks](#-conference-talks)
- [Research Papers](#-research-papers)
- [Equipment & Hardware](#-equipment--hardware)
- [Detection & Defense](#️-detection--defense)
- [Cellular IoT & NB-IoT Security](#-cellular-iot--nb-iot-security)
- [Satellite-Cellular Integration](#️-satellite-cellular-integration)
- [Private 5G Network Security](#-private-5g-network-security)
- [Network Slicing & Edge Security](#-network-slicing--edge-security)
- [Automotive & Industrial Cellular](#-automotive--industrial-cellular)
- [Forensics & Investigation](#-forensics--investigation)
- [Vulnerability Disclosure](#-vulnerability-disclosure)
- [SIM Security](#-sim-security)
- [SS7 & Telecom Infrastructure](#-ss7--telecom-infrastructure)
- [Surveillance Technology](#-surveillance-technology)
- [Recent CVEs & Updates](#-recent-cves--updates)
- [International Research](#-international-research)
- [Training & Education](#-training--education)
- [Vendor-Specific Research](#-vendor-specific-research)
- [Roaming & Interconnect Security](#-roaming--interconnect-security)
- [Resources](#-resources)

## 🏗️ Rogue Base Stations

### GSM/CDMA Traffic Impersonation and Interception

- **[How To Build Your Own Rogue GSM BTS For Fun and Profit](https://www.evilsocket.net/2016/03/31/How-To-Build-Your-Own-Rogue-GSM-BTS-For-Fun-And-Profit/)**
  
  Guide to creating a portable GSM BTS for private networks or security testing. Covers the technical setup using relatively inexpensive equipment.

- **[How to create an Evil LTE Twin/LTE Rogue BTS](https://adam-toscher.medium.com/how-to-create-an-evil-lte-twin-34b0a9ce193b)**
  
  Tutorial for setting up a 4G/LTE Evil Twin Base Station using srsRAN and USRP SDR devices.

- **[Practical attacks against GSM networks: Impersonation](https://blog.blazeinfosec.com/practical-attacks-against-gsm-networks-part-1/)**
  
  Detailed analysis of GSM Base Station impersonation using Software Defined Radio (SDR) and open source tools.

- **[Tutorial: Analyzing GSM with Airprobe and Wireshark](https://www.rtl-sdr.com/rtl-sdr-tutorial-analyzing-gsm-with-airprobe-and-wireshark/)**
  
  Step-by-step guide for using RTL-SDR to analyze GSM signals with GR-GSM/Airprobe and Wireshark.

- **[GSM/GPRS Traffic Interception for Penetration Testing](https://research.nccgroup.com/2016/05/19/gsm-gprs-traffic-interception-for-penetration-testing-engagements/)**
  
  NCC Group's research on GSM/GPRS interception capabilities for penetration testing engagements.

## 🆕 Recent Updates (2024-2025)

### Latest Base Station Software & Tools
- **[OpenBTS 2024 Reloaded](https://github.com/PentHertz/OpenBTS)**: Updated for modern UHD drivers and Ubuntu 22.04/24.04 support
- **[OpenAirInterface (OAI)](https://openairinterface.org/)**: Major 5G platform with complete 3GPP Release-15+ implementation
- **[LimeNET CrowdCell](https://limemicro.com/)**: Network-in-a-box solution with integrated LimeSDR for small cell deployments
- **[Amarisoft LTEENB/gNB](https://www.amarisoft.com/)**: Professional-grade LTE/5G NR base station software
- **[DragonOS](https://github.com/cemaxecuter/DragonOS)**: Ubuntu-based SDR distribution with preinstalled cellular tools
- **[Magma Core Network](https://magmacore.org/)**: Meta's distributed packet core now under Linux Foundation
- **[5GBaseChecker](https://github.com/SyNSec-den/5GBaseChecker)**: New tool for automated 5G baseband vulnerability detection

## 🛠️ Software & Tools

### Base Station Software

| Software | Description | Link |
|----------|-------------|------|
| **OpenBTS (2024 Reloaded)** | Linux application using SDR to present 3GPP air interface (Updated for modern systems) | [GitHub](https://github.com/PentHertz/OpenBTS) |
| **OpenBTS (Original)** | Original Range Networks implementation | [SourceForge](https://sourceforge.net/projects/openbts/) |
| **YateBTS** | GSM/GPRS radio access network implementation | [Website](https://yatebts.com/) |
| **srsRAN Project** | Open-source 5G O-RAN CU/DU software suite | [GitHub](https://github.com/srsran/srsRAN_Project) |
| **srsRAN 4G** | Open-source 4G software radio suite | [GitHub](https://github.com/srsran/srsRAN_4G) |
| **OpenAirInterface** | Complete 4G/5G protocol stack implementation | [Website](https://openairinterface.org/) |

### Configuration Guides

- **[BladeRF and YateBTS Configuration](https://github.com/Nuand/bladeRF/wiki/Setting-up-Yate-and-YateBTS-with-the-bladeRF)**
- **[srsRAN Project Documentation](https://docs.srsran.com/projects/project)**
- **[srsRAN 4G Documentation](https://docs.srsran.com/projects/4g)**

### Analysis Tools

- **[LTE-Cell-Scanner](https://github.com/Evrytania/LTE-Cell-Scanner)** - LTE cell detection and analysis
- **[gr-gsm](https://github.com/ptrkrysik/gr-gsm/wiki/Passive-IMSI-Catcher)** - GSM analysis with GNU Radio
- **[IMSI-Catcher Detector](https://github.com/CellularPrivacy/Android-IMSI-Catcher-Detector)** - Android app for detecting IMSI catchers
- **[QCSuper](https://labs.p1sec.com/2019/07/09/presenting-qcsuper-a-tool-for-capturing-your-2g-3g-4g-air-traffic-on-qualcomm-based-phones/)** - Capture 2G-4G traffic using Qualcomm phones
- **[5GBaseChecker](https://github.com/SyNSec-den/5GBaseChecker)** - Tool for detecting vulnerabilities in 5G baseband implementations (2024)
- **[FALCON LTE](https://github.com/falkenber9/falcon)** - Fast Analysis of LTE Control Channels for real-time analysis
- **[Kalibrate](https://github.com/scateu/kalibrate-hackrf)** - GSM base station scanner and frequency calibration tool
- **[LTE Sniffer](https://github.com/SysSec-KAIST/LTESniffer)** - Open-source LTE downlink/uplink eavesdropper
- **[OsmocomBB](https://osmocom.org/projects/osmocombb)** - Free firmware for mobile phone baseband processors
- **[Modmobmap](https://github.com/Synacktiv-contrib/Modmobmap)** - Mobile network mapping
- **[Modmobjam](https://github.com/Synacktiv-contrib/Modmobjam)** - Mobile jamming research

## 🔧 Hardware Setup

### USRP Installation on Linux

```bash
# Add Ettus Research repository
sudo add-apt-repository ppa:ettusresearch/uhd
sudo apt-get update

# Install UHD drivers and tools
sudo apt-get install libuhd-dev libuhd003 uhd-host

# Find connected devices
uhd_find_devices

# Download firmware images
cd /usr/lib/uhd/utils/
./uhd_images_downloader.py

# Test device connection
sudo uhd_usrp_probe
```

### Expected Output

```
[INFO] [UHD] linux; GNU C++ version 7.4.0; Boost_106501; UHD_3.14.1.1-release
[INFO] [B200] Detected Device: B*****
[INFO] [B200] Operating over USB 3.
[INFO] [B200] Initialize CODEC control...
[INFO] [B200] Initialize Radio control...
[INFO] [B200] Performing register loopback test...
[INFO] [B200] Register loopback test passed
```

### SDR Hardware Options

| Hardware | Frequency Range | Bandwidth | Price Range | Use Case | Link |
|----------|----------------|-----------|-------------|----------|------|
| **Ettus Research (USRP)** | | | | | |
| **USRP B210** | 70 MHz - 6 GHz | 61.44 MHz | $2,100 | Professional development, 2x2 MIMO | [Ettus](https://www.ettus.com/all-products/ub210-kit/) |
| **USRP B200mini** | 70 MHz - 6 GHz | 61.44 MHz | $775 | Compact USRP B-series | [Ettus](https://www.ettus.com/) |
| **USRP N210** | DC - 6 GHz | 25 MHz | $1,700 | High-performance networked SDR | [Ettus](https://www.ettus.com/) |
| **USRP N320** | 1 MHz - 6 GHz | 200 MHz | $8,000 | High-end networked 2x2 MIMO | [Ettus](https://www.ettus.com/) |
| **USRP X310** | DC - 6 GHz | 160 MHz | $6,000 | High-performance desktop/rack | [Ettus](https://www.ettus.com/all-products/x310-kit/) |
| **USRP X410** | 1 MHz - 7.2 GHz | 400 MHz | $15,000 | Latest high-performance 4x4 MIMO | [Ettus](https://www.ettus.com/) |
| **USRP X440** | 30 MHz - 4 GHz | 1.6 GHz | $25,000+ | Latest 8x8 MIMO RFSoC platform | [Ettus](https://www.ettus.com/) |
| **USRP E320** | 70 MHz - 6 GHz | 56 MHz | $4,000 | Embedded 2x2 MIMO SDR | [Ettus](https://www.ettus.com/) |
| **Nuand (BladeRF)** | | | | | |
| **BladeRF 2.0 xA4** | 47 MHz - 6 GHz | 61.44 MHz | $420 | Budget 2x2 MIMO development | [Nuand](https://www.nuand.com/product/bladerf-xa4/) |
| **BladeRF 2.0 xA9** | 47 MHz - 6 GHz | 61.44 MHz | $720 | High FPGA resources, 2x2 MIMO | [Nuand](https://www.nuand.com/product/bladerf-xa9/) |
| **BladeRF x40 (Legacy)** | 300 MHz - 3.8 GHz | 40 MHz | $400 | Entry-level legacy model | [Nuand](https://www.nuand.com/product/bladerf-x40/) |
| **Great Scott Gadgets** | | | | | |
| **HackRF One** | 1 MHz - 6 GHz | 20 MHz | $350 | Budget TX/RX development | [GSG](https://greatscottgadgets.com/hackrf/) |
| **YARD Stick One** | 300-348, 391-464, 782-928 MHz | 2.5 MHz | $110 | Sub-GHz IoT frequencies | [GSG](https://greatscottgadgets.com/yardstickone/) |
| **Lime Microsystems** | | | | | |
| **LimeSDR USB** | 100 kHz - 3.8 GHz | 61.44 MHz | $289 | Open-source 2x2 MIMO | [Lime Micro](https://limemicro.com/sdr/limesdr-usb/) |
| **LimeSDR Mini** | 10 MHz - 3.5 GHz | 30.72 MHz | $139 | Compact LimeSDR variant | [Lime Micro](https://limemicro.com/boards/limesdr-mini/) |
| **LimeSDR Mini 2.0** | 10 MHz - 3.5 GHz | 30.72 MHz | $169 | Updated with ECP5 FPGA | [Lime Micro](https://limemicro.com/sdr/limesdr-mini-2-0/) |
| **LimeSDR X3** | Various bands | Up to 61.44 MHz | $3,000+ | Professional 3x transceiver PCIe | [Lime Micro](https://limemicro.com/sdr/limesdr-x3/) |
| **Analog Devices** | | | | | |
| **PlutoSDR** | 325 MHz - 3.8 GHz | 20 MHz | $150 | Education and learning platform | [Analog Devices](https://www.analog.com/en/design-center/evaluation-hardware-and-software/evaluation-boards-kits/adalm-pluto.html) |
| **RTL-SDR Blog** | | | | | |
| **RTL-SDR V3** | 500 kHz - 1.75 GHz | 3.2 MHz | $35 | Ultra-budget RX-only scanner | [RTL-SDR](https://www.rtl-sdr.com/buy-rtl-sdr-dvb-t-dongles/) |
| **RTL-SDR V4** | 500 kHz - 1.75 GHz | 3.2 MHz | $40 | Latest RTL-SDR with R828D | [RTL-SDR](https://www.rtl-sdr.com/rtl-sdr-blog-v4-dongle-initial-release/) |
| **Airspy** | | | | | |
| **Airspy R2** | 24 MHz - 1.8 GHz | 10 MHz | $200 | High-performance VHF/UHF scanner | [Airspy](https://airspy.com/) |
| **Airspy Mini** | 24 MHz - 1.8 GHz | 6 MHz | $99 | Compact Airspy in dongle format | [Airspy](https://airspy.com/) |
| **Airspy HF+ Discovery** | 9 kHz - 31 MHz, 60-260 MHz | 768 kHz | $169 | Dedicated HF reception | [Airspy](https://airspy.com/) |
| **SDRplay** | | | | | |
| **RSP1A** | 1 kHz - 2 GHz | 10 MHz | $119 | Wideband general purpose | [SDRplay](https://www.sdrplay.com/) |
| **RSPdx** | 1 kHz - 2 GHz | 10 MHz | $299 | Professional features, dual antenna | [SDRplay](https://www.sdrplay.com/) |
| **Red Pitaya** | | | | | |
| **STEMlab 125-14** | DC - 60 MHz | 50 MHz | $600 | HF transceiver, lab instrument | [Red Pitaya](https://redpitaya.com/) |
| **STEMlab 122-16** | DC - 50 MHz | Variable | $625 | High-resolution HF SDR/scope | [Red Pitaya](https://redpitaya.com/) |

### Common SDR Issues & Troubleshooting

| Issue | Possible Causes |
|-------|----------------|
| Device not detected | Improper firmware, USB connection issues |
| Poor signal quality | Incorrect antennas, wrong frequency configuration |
| Connection failures | Wrong SIM, incorrect MCC/MNC codes |
| Performance issues | Virtualized platform limitations, wrong SDR firmware |

## 🔬 Testing & Research Methodologies

### Modern Baseband Fuzzing (2024)
- **[Budget-Friendly Baseband Fuzzing Setup](https://t2.fi/schedule/2024/)** - DefCon 32 2024
  
  Guidelines for building cost-effective baseband fuzzing rigs using Software Defined Radios (SDRs). Includes methods for:
  - Firmware acquisition and reverse engineering
  - Using Large Language Models to accelerate protocol parser development  
  - Testing automotive ECUs, payment terminals, and mobile devices
  - Practical vulnerability assessment in ISP networks

### Vulnerability Research Tools
- **[5GBaseChecker](https://github.com/SyNSec-den/5GBaseChecker)** - Automated 5G baseband vulnerability detection
- **[certmitm](https://github.com/juurlink/certmitm)** - TLS hacking tool for finding insecure implementations

## ⚔️ Attack Vectors

### Radio Jamming Attacks

From [NIST SP 800-187](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-187.pdf):

- **Smart Jamming:** Targeted channel interference timed to avoid detection
- **Dumb Jamming:** Broadband noise transmission across frequency ranges
- **UE Interface Jamming:** Preventing UE signaling to eNodeB
- **eNodeB Interface Jamming:** Disrupting base station communications

### 5G Security Research

- **[Privacy Attacks on 4G/5G Paging Protocols](https://assets.documentcloud.org/documents/5749002/4G-5G-paper-at-NDSS-2019.pdf)**
- **[European 5G Security in the Wild](https://arxiv.org/pdf/2305.08635.pdf)**
- **[5G Threat Modeling Framework](https://arxiv.org/pdf/2005.05110v1.pdf)**
- **[ENISA 5G Threat Landscape](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/ENISA%20threat%20landscape%20for%205G%20Networks.pdf)**
- **[5GReasoner Analysis Framework](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/5GReasoner.pdf)**
- **[5G NR Jamming, Spoofing, and Sniffing](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/5gjam.pdf)**
- **[New Vulnerabilities in 5G Networks](https://threatpost.com/5g-security-flaw-mitm-targeted-attacks/147073/)**
- **[New Privacy Threat on 3G, 4G, and Upcoming 5G AKA Protocols](https://arxiv.org/pdf/1905.07617.pdf)**
- **[Insecure Connection Bootstrapping in Cellular Networks](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/wisec19-preprint.pdf)**
- **[Protecting 4G and 5G Cellular Paging Protocols](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/popets-2020-0008.pdf)**

### LTE/4G Security Research

- **[LTRACK: Stealthy Mobile Phone Tracking](https://www.usenix.org/system/files/sec22summer_kotuliak.pdf)**
- **[Detecting Fake 4G Base Stations](https://i.blackhat.com/USA-20/Wednesday/us-20-Quintin-Detecting-Fake-4G-Base-Stations-In-Real-Time.pdf)**
- **[BaseSAFE: Baseband Fuzzing](https://arxiv.org/pdf/2005.07797.pdf)**
- **[LTE Public Warning System Attacks](https://netstech.org/wp-content/uploads/2019/06/cmas-mobisys2019.pdf)**
- **[Signal Overshadowing Attacks](https://www.usenix.org/system/files/sec19-yang-hojoon.pdf)**
- **[Breaking LTE on Layer Two](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/breaking_lte_on_layer_two.pdf)**
- **[LTE/LTE-A Jamming, Spoofing, and Sniffing](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/LTE_Jamming_Magazine_Paper_final.pdf)**
- **[LTE Protocol Exploits](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/LTE_security_TakeDownCon.pdf)**
- **[Practical Attacks Against Privacy and Availability](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/Prac-4G-Attacks.pdf)**
- **[LTE Security Assessment](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/LTE_open_source_HackerHalted.pdf)**
- **[Hiding in Plain Signal: Physical Signal Overshadowing](https://www.usenix.org/system/files/sec19-yang-hojoon.pdf)**
- **[LTE Security Disabled—Misconfiguration in Commercial Network](https://www.infsec.ruhr-uni-bochum.de/media/infsec/veroeffentlichungen/2019/04/23/wisec19-final123.pdf)**
- **[All The 4G Modules Could Be Hacked](https://i.blackhat.com/USA-19/Wednesday/us-19-Shupeng-All-The-4G-Modules-Could-Be-Hacked.pdf)**
- **[Paging Storm Attacks against 4G/LTE Networks](https://www.cs.binghamton.edu/~ghyan/papers/wisec20.pdf)**
- **[Hacking Public Warning System in LTE](https://conference.hitb.org/hitbsecconf2019ams/materials/HAXPO%20D1%20-%20Hacking%20LTE%20Public%20Warning%20Systems%20-%20Weiguang%20Li.pdf)**
- **[Analysis of the LTE Control Plane](https://syssec.kaist.ac.kr/pub/2019/kim_sp_2019.pdf)**
- **[Baseband Attacks: Remote Exploitation](https://www.usenix.org/system/files/conference/woot12/woot12-final24.pdf)**
- **[LTE Security and Protocol Exploits - ShmooCon 2016](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/ShmooCon_talk_final_01162016.pdf)**
- **[Military Communications Conference 2018 - Slides](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/milcom2018_slides_final.pdf)**
- **[WiSec 2019 - Final Paper](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/wisec19.pdf)**

## 🎤 Conference Talks

### Black Hat 2024
- **[5G Baseband Vulnerability Research by Penn State](https://techcrunch.com/2024/08/07/hackers-could-spy-on-cellphone-users-by-abusing-5g-baseband-flaws-researchers-say/)**
  
  Researchers from Pennsylvania State University presented findings about 12 vulnerabilities in 5G basebands made by Samsung, MediaTek, and Qualcomm, affecting phones by Google, OPPO, OnePlus, Motorola, and Samsung. They released 5GBaseChecker tool on GitHub for vulnerability research.

### DefCon 32 (2024) 
- **[Economizing Mobile Network Warfare: Budget-Friendly Baseband Fuzzing](https://t2.fi/schedule/2024/)** by Janne Taponen
  
  Explores the role of Software Defined Radios (SDRs) in making baseband fuzzing accessible and affordable. Covers building cost-effective baseband fuzzing rigs, using Large Language Models to accelerate protocol parser development, and discovering vulnerabilities in device radio access network (RAN) interfaces across automotive ECUs, payment terminals, cellular modems, and mobile phones.

### Black Hat 2022
- **[Attacks from a New Front Door in 4G & 5G Networks](https://i.blackhat.com/USA-22/Wednesday/US-22-Shaik-Attacks-From-a-New-Front-Door-in-4G-5G-Mobile-Networks.pdf)**

### Black Hat 2021
- **[Over The Air Baseband Exploit: 5G RCE](https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Over-The-Air-Baseband-Exploit-Gaining-Remote-Code-Execution-On-5G-Smartphones.pdf)**
- **[Technical White Paper](https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Over-The-Air-Baseband-Exploit-Gaining-Remote-Code-Execution-On-5G-Smartphones-wp.pdf)**

### TROOPERS 2013
- **[Dirty Use of USSD Codes in Cellular Networks](https://troopers.de/wp-content/uploads/2012/12/TROOPERS13-Dirty_use_of_USSD_codes_in_cellular-Ravi_Borgaonkor.pdf)** by Ravi Borgaonkar
  
  Analysis of Unstructured Supplementary Service Data (USSD) vulnerabilities in cellular networks and how they can be exploited for malicious purposes.

### Additional Conference Resources
- **[NSA PLAYSET GSM](https://www.defcon.org/images/defcon-22/dc-22-presentations/Pierce-Loki/DEFCON-22-Pierce-Loki-NSA-PLAYSET-GSM.pdf)**
- **[VoLTE Phreaking - Ralph Moonen](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/HAXPO%20D1%20-%20VoLTE%20Phreaking%20-%20Ralph%20Moonen.pdf)**
- **[RF Exploitation: IoT/OT Hacking with SDR](https://conference.hitb.org/hitbsecconf2019ams/materials/HAXPO%20D2%20-%20Demystifying%20IoT:OT%20Hacks%20With%20SDR%20-%20Himanshu%20Mehta%20&%20Harshit%20Agrawal.pdf)**
- **[Bye-Bye-IMSI-Catchers](https://conference.hitb.org/hitbsecconf2018pek/materials/D2T2%20-%20Bye%20Bye%20IMSI%20Catchers%20-%20Security%20Enhancements%20in%205g%20-%20Lin%20Huang.pdf)**
- **[Side Channel Analysis in 4G and 5G](https://i.blackhat.com/eu-19/Thursday/eu-19-Hussain-Side-Channel-Attacks-In-4G-And-5G-Cellular-Networks.pdf)**

## 📚 Research Papers

### NDSS 2025
- **[Starshields for iOS: Navigating the Security Cosmos in Satellite Communication](https://www.ndss-symposium.org/wp-content/uploads/2025-124-paper.pdf)**
  
  First comprehensive security analysis of Apple's satellite communication features for iPhones. Researchers reverse-engineered Apple's proprietary satellite protocol, analyzed security/privacy properties, demonstrated restriction bypasses, and created a simulation testbed. Covers Emergency SOS, Find My, roadside assistance, and iMessage/SMS over satellite.

### 2024 Research
- **[5GBaseChecker Tool Release](https://github.com/SyNSec-den/5GBaseChecker)** - Penn State University
  
  Open-source tool for detecting vulnerabilities in 5G baseband implementations. Used to discover 12 critical vulnerabilities in Samsung, MediaTek, and Qualcomm basebands.

## 📊 Equipment & Hardware

### Research Equipment Used in "Over The Air Baseband Exploit"

| Component | Purpose | Link |
|-----------|---------|------|
| Ettus USRP B210 | Software Defined Radio | [Product Page](https://www.ettus.com/all-products/ub210-kit/) |
| srsENB | 4G/5G Base Station Software | [GitHub](https://github.com/srsran/srsRAN/tree/master/srsenb) |
| Open5GS | 5G Core Network | [GitHub](https://github.com/open5gs) |
| sysmo-usim-tool | SIM Programming | [Project Page](https://osmocom.org/projects/cellular-infrastructure/wiki/SysmoISIM-SJA2) |
| pysim | SIM Analysis Tool | [GitHub](https://github.com/osmocom/pysim) |
| CoIMS | VoLTE Testing | [Play Store](https://play.google.com/store/apps/details?id=com.sherle.coims) |
| Docker Open5GS | Containerized Core | [Tutorial](https://open5gs.org/open5gs/docs/tutorial/03-VoLTE-dockerized/) |

## 🛡️ Detection & Defense

### 🚨 Protection from Stingrays & IMSI Catchers

- **[CellGuard](https://github.com/seemoo-lab/CellGuard)** - **NEW 2024** 🔥
  
  Advanced iOS app that detects rogue base stations and cellular attacks targeting iPhones. Analyzes baseband packets in real-time to identify suspicious activities and IMSI catchers. Developed by SEEMOO lab with cutting-edge research into cellular surveillance detection.
  
  - Real-time baseband packet analysis
  - Suspicious activity detection algorithms  
  - Integration with Apple Cell Location Database
  - TestFlight beta available for testing
  - [Website & Documentation](https://cellguard.seemoo.tu-darmstadt.de/)
  - [TestFlight Beta](https://testflight.apple.com/join/HrsaoHM3)

### IMSI Catcher Detection & Research

- **[SeaGlass: City-Wide IMSI-Catcher Detection](https://seaglass.cs.washington.edu/)**
- **[SeaGlass Research Paper](https://seaglass-web.s3.amazonaws.com/SeaGlass___PETS_2017.pdf)**
- **[White-Stingray Detection App Evaluation](http://www.cs.ox.ac.uk/files/9192/paper-final-woot-imsi.pdf)**
- **[IMSI-Catcher Detector (Android)](https://github.com/CellularPrivacy/Android-IMSI-Catcher-Detector)** - Android app for detecting IMSI catchers

### Security Alerts & Advisories

- **[CERT Alert: VoLTE Implementation Vulnerabilities](https://www.kb.cert.org/vuls/id/943167/)**

## 📱 Cellular IoT & NB-IoT Security

- **[NB-IoT Security Analysis Framework](https://arxiv.org/search/?query=NB-IoT+security)** - Narrowband IoT security research
- **[Cat-M1/LTE-M Attack Vectors](https://www.gsma.com/iot/mobile-iot-security/)** - GSMA IoT security guidelines
- **[Cellular IoT Botnet Research](https://www.virusbulletin.com/virusbulletin/search/)** - IoT cellular malware analysis

## 🛰️ Satellite-Cellular Integration

- **[Starlink Security Research](https://conference.hitb.org/)** - Satellite cellular convergence attacks
- **[3GPP Non-Terrestrial Networks (NTN) Security](https://www.3gpp.org/specifications/specification-numbering)** - Official 5G satellite integration specs
- **[LEO Satellite Cellular Vulnerabilities](https://arxiv.org/search/?query=satellite+cellular+security)** - Low Earth Orbit security research

## 🏢 Private 5G Network Security

- **[O-RAN Security Research](https://www.o-ran.org/specifications)** - Open RAN security specifications
- **[Private 5G Penetration Testing Guide](https://www.nist.gov/cybersecurity)** - Enterprise private network testing
- **[Campus 5G Security Assessment](https://csrc.nist.gov/)** - NIST private 5G security guidance

## 🌐 Network Slicing & Edge Security

- **[5G Network Slicing Attack Research](https://ieeexplore.ieee.org/search/searchresult.jsp?queryText=5G+network+slicing+security)** - IEEE research papers
- **[Multi-Access Edge Computing (MEC) Vulnerabilities](https://www.etsi.org/technologies/multi-access-edge-computing)** - ETSI MEC security specs
- **[Network Function Virtualization (NFV) Attacks](https://www.etsi.org/technologies/nfv)** - Virtual network function security

## 🚗 Automotive & Industrial Cellular

- **[V2X Security Research](https://www.its.dot.gov/research_areas/emerging_tech/htm/EmerTech_V2X.htm)** - Vehicle-to-everything communications
- **[Cellular-V2X Attack Vectors](https://ieeexplore.ieee.org/search/searchresult.jsp?queryText=C-V2X+security)** - Automotive cellular security
- **[Industrial IoT Cellular Security](https://www.nist.gov/cybersecurity/iot)** - IIoT cellular threat landscape

## 🔍 Forensics & Investigation

- **[XRY Mobile Forensics](https://msab.com/products/xry/)** - Commercial cellular forensics platform
- **[Cellebrite UFED](https://cellebrite.com/)** - Mobile device extraction tools
- **[MSAB Cellular Evidence Analysis](https://msab.com/)** - Network evidence collection
- **[NIST Mobile Forensics Guidelines](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-101r1.pdf)** - Mobile device forensics standards

## 🚨 Vulnerability Disclosure

- **[Android Security Bulletins](https://source.android.com/docs/security/bulletin)** - Regular Android/baseband patches
- **[Qualcomm Security Bulletins](https://www.qualcomm.com/company/product-security/bulletins)** - Snapdragon security updates
- **[Samsung Mobile Security](https://security.samsungmobile.com/)** - Galaxy security research program
- **[Apple Security Research](https://security.apple.com/)** - iOS/baseband security program

## 💳 SIM Security

- **[Rooting SIM Cards](https://media.blackhat.com/us-13/us-13-Nohl-Rooting-SIM-cards-Slides.pdf)**
- **[SIM Port Hack Case Study](https://medium.com/coinmonks/the-most-expensive-lesson-of-my-life-details-of-sim-port-hack-35de11517124)**
- **[SIM Cloning with Oscilloscope](https://www.blackhat.com/docs/us-15/materials/us-15-Yu-Cloning-3G-4G-SIM-Cards-With-A-PC-And-An-Oscilloscope-Lessons-Learned-In-Physical-Security-wp.pdf)**
- **[Small Tweaks do Not Help: MILENAGE Analysis](https://www.blackhat.com/docs/us-15/materials/us-15-Yu-Cloning-3G-4G-SIM-Cards-With-A-PC-And-An-Oscilloscope-Lessons-Learned-In-Physical-Security-wp.pdf)**

## 🏢 SS7 & Telecom Infrastructure

- **[Bypassing GSMA SS7 Recommendations](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/D1T2%20-%20Bypassing%20GSMA%20Recommendations%20on%20SS7%20Networks%20-%20Kirill%20Puzankov.pdf)**
- **[Attacking SS7 Networks](http://www.hackitoergosum.org/2010/HES2010-planglois-Attacking-SS7.pdf)**
- **[Getting in the SS7 Kingdom](http://www.hackitoergosum.org/2010/HES2010-planglois-Attacking-SS7.pdf)**

## 📡 Surveillance Technology

### Stingray/IMSI Catchers

- **[DHS Stingray Surveillance](https://www.wired.com/story/dcs-stingray-dhs-surveillance/)**
- **[Stingray Cost Analysis](https://www.vice.com/en_us/article/gv5k3x/heres-how-much-a-stingray-cell-phone-surveillance-tool-costs)**
- **[NYCLU Stingray Information](https://www.nyclu.org/en/stingrays)**
- **[EFF Cell Site Simulators](https://www.eff.org/pages/cell-site-simulatorsimsi-catchers)**

## 🆕 Recent CVEs & Updates

- **[CVE Database Search](https://nvd.nist.gov/vuln/search)** - Search for cellular-related vulnerabilities
- **[Project Zero Cellular Security Research](https://googleprojectzero.blogspot.com/)** - Google's ongoing mobile security research
- **[Samsung Security Bulletins](https://security.samsungmobile.com/securityUpdate.smc)** - Regular baseband security updates
- **[SIMjacker and Simswap Updates](https://simjacker.com/)** - Evolution of SIM-based attacks

## 🌍 International Research

- **[China Mobile Security Research](https://ieeexplore.ieee.org/)** - Chinese cellular security papers
- **[European Cybersecurity Agency (ENISA) 5G Reports](https://www.enisa.europa.eu/)** - EU 5G security assessments
- **[Japanese 5G Security Guidelines](https://www.nisc.go.jp/eng/)** - Japan cybersecurity strategy
- **[Korean KISA Mobile Security](https://www.kisa.or.kr/eng/)** - Korean mobile security research

## 🎓 Training & Education

- **[SANS Mobile Security Training](https://www.sans.org/)** - Professional mobile security courses
- **[Offensive Security Mobile Testing](https://www.offensive-security.com/)** - Advanced mobile penetration testing
- **[Cellular Security Lab Environments](https://github.com/OpenAirInterface/openairinterface5g)** - Open-source 5G lab setup
- **[SDR University Courses](https://www.gnuradio.org/)** - GNU Radio educational materials

## 🏭 Vendor-Specific Research

- **[Ericsson Security Research](https://www.ericsson.com/en/security)** - Network equipment security
- **[Nokia Bell Labs Security](https://www.bell-labs.com/)** - Cellular infrastructure research
- **[Huawei Security Research](https://www.huawei.com/en/trust-center)** - Equipment security analysis
- **[ZTE Security Bulletins](https://www.zte.com.cn/)** - Network equipment vulnerabilities

## 🌐 Roaming & Interconnect Security

- **[GRX/IPX Security Research](https://www.gsma.com/newsroom/)** - GSMA roaming security
- **[International Roaming Attacks](https://arxiv.org/search/?query=mobile+roaming+security)** - Cross-border cellular security
- **[Diameter Protocol Security](https://tools.ietf.org/html/rfc6733)** - 4G/5G signaling security

## 🔗 Resources

### Development & Analysis Tools

- **[RTL-SDR Community](https://www.rtl-sdr.com/)** - Software Defined Radio resources
- **[MCC-MNC Database](http://www.mcc-mnc.com/)** - Mobile Country/Network Code reference
- **[RFSec-ToolKit](https://github.com/cn0xroot/RFSec-ToolKit)** - RF security testing tools
- **[FakeBTS](http://fakebts.com/category/attacks/)** - Base station attack resources

### Research Collections

- **[RF Security Documentation](https://rmusser.net/docs/Wireless.html#cn)**
- **[Conference Proceedings Collections](https://ieeexplore.ieee.org/)** - IEEE research database
- **[ACM Digital Library](https://dl.acm.org/)** - ACM research papers
- **[USENIX Security Papers](https://www.usenix.org/conferences)** - Security conference proceedings

### Legal & Regulatory

- **[FCC Equipment Authorization Rules](https://www.fcc.gov/general/equipment-authorization-procedures)** - US cellular equipment regulations
- **[CISA 5G Security Guidance](https://www.cisa.gov/)** - US critical infrastructure guidance
- **[European 5G Cybersecurity Certification](https://ec.europa.eu/digital-single-market/en/european-cybersecurity-certification-framework)** - EU certification requirements

## 📚 Additional Reading

- **[Analyzing GSM Downlink with USRP](http://leetupload.com/blagosphere/2014/03/28/analyze-and-crack-gsm-downlink-with-a-usrp/)**
- **[AT&T Microcell Analysis](https://fail0verflow.com/blog/2012/microcell-fail/)**
- **[Dynamic Security Analysis](https://syssec.kaist.ac.kr/pub/2019/kim_sp_2019.pdf)**
- **[Touching the Untouchables](https://syssec.kaist.ac.kr/pub/2019/kim_sp_2019.pdf)**
- **[LTE Recon - (DefCon 23)](https://www.rtl-sdr.com/one-more-rtl-sdr-talk-from-defcon-23/)**
- **[BMW Security Assessment using OpenBTS](https://keenlab.tencent.com/en/whitepapers/Experimental_Security_Assessment_of_BMW_Cars_by_KeenLab.pdf)**
- **[LTE Security Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-187.pdf)**
- **[4G Access Level Security Assessment](https://hackinparis.com/data/slides/2015/timur_yusinov_root_via_sms.pdf)**
- **[Demystifying Mobile Networks](http://2014.video.sector.ca/video/110383258)**
- **[LTE Pwnage: Core Network Elements](https://conference.hitb.org/hitbsecconf2013ams/materials/D1T2%20-%20Philippe%20Langlois%20-%20Hacking%20HLR%20HSS%20and%20MME%20Core%20Network%20Elements.pdf)**
- **[WiFi IMSI Catcher](https://www.blackhat.com/docs/eu-16/materials/eu-16-OHanlon-WiFi-IMSI-Catcher.pdf)**

## 🤝 Contributing

This is a community-driven project. To contribute:

1. Fork the repository
2. Add your resources with proper descriptions
3. Ensure links are working and content is relevant
4. Submit a pull request with a clear description

## ⚖️ Legal Notice

This repository is for educational and research purposes only. Users are responsible for complying with all applicable laws and regulations. The maintainers do not endorse or encourage any illegal activities.

---

**Last Updated:** June 2025  
**Maintainer:** [@W00t3k](https://github.com/W00t3k)

*If you find broken links or have resources to add, please open an issue or submit a pull request.*
