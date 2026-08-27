# Awesome Cellular Hacking

> A comprehensive curated list of resources for 2G/3G/4G/5G cellular security research and analysis

This repository consolidates community knowledge in the cellular security space, including exploits, research papers, tools, and educational resources. The goal is to preserve and organize important security research that might otherwise become difficult to find.

**Disclaimer:** This information is intended for educational and defensive security research purposes only. Use responsibly and in compliance with applicable laws and regulations.

## Table of Contents

- [Getting Started](#getting-started)
- [Rogue Base Stations](#rogue-base-stations)
- [Recent Updates (2024-2025)](#recent-updates-2024-2025)
- [Software and Tools](#software-and-tools)
- [Hardware Setup](#hardware-setup)
- [Testing and Research Methodologies](#testing-and-research-methodologies)
- [Attack Vectors](#attack-vectors)
- [Conference Talks](#conference-talks)
- [Research Papers](#research-papers)
- [Equipment and Hardware](#equipment-and-hardware)
- [Detection and Defense](#detection-and-defense)
- [Cellular IoT and NB-IoT Security](#cellular-iot-and-nb-iot-security)
- [Satellite-Cellular Integration](#satellite-cellular-integration)
- [Private 5G Network Security](#private-5g-network-security)
- [Network Slicing and Edge Security](#network-slicing-and-edge-security)
- [Automotive and Industrial Cellular](#automotive-and-industrial-cellular)
- [Forensics and Investigation](#forensics-and-investigation)
- [Vulnerability Disclosure](#vulnerability-disclosure)
- [SIM Security](#sim-security)
- [SS7 and Telecom Infrastructure](#ss7-and-telecom-infrastructure)
- [Surveillance Technology](#surveillance-technology)
- [Recent CVEs and Updates](#recent-cves-and-updates)
- [International Research](#international-research)
- [Training and Education](#training-and-education)
- [Vendor-Specific Research](#vendor-specific-research)
- [Roaming and Interconnect Security](#roaming-and-interconnect-security)
- [Community](#community)
- [Resources](#resources)

---

## Getting Started

New to cellular security research? This section outlines the recommended path for building foundational skills.

### Skill Levels

**Beginner (passive listening only)**
- Hardware: RTL-SDR V3 or V4 ($35-$40), a laptop running Linux
- Software: GNU Radio, GQRX, gr-gsm
- First project: Scan and decode GSM frames passively using gr-gsm and Wireshark
- Reading: [NIST SP 800-187 LTE Security Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-187.pdf)

**Intermediate (active research lab)**
- Hardware: HackRF One or LimeSDR Mini ($139-$350), programmable SIM cards (sysmoUSIM), a spare Android device
- Software: srsRAN 4G, Open5GS or Free5GC, OsmocomBB
- First project: Build a private LTE network in a Faraday cage and connect a test device
- Reading: srsRAN documentation, Open5GS tutorials

**Advanced (protocol fuzzing and baseband research)**
- Hardware: USRP B210 or BladeRF 2.0, multiple test devices
- Software: 5GBaseChecker, LTEFuzz, BaseBridge, SigPloit
- Focus areas: Baseband fuzzing, RAN-Core interface testing, SS7/Diameter signaling

### Lab Setup Checklist

- [ ] Linux host (Ubuntu 22.04 or 24.04 recommended)
- [ ] UHD drivers installed and device recognized (`uhd_find_devices`)
- [ ] Faraday cage or RF shielding for active transmissions
- [ ] Programmable SIM cards (sysmoUSIM-SJA2 or similar)
- [ ] Dedicated test devices (not your daily driver)
- [ ] Isolated network environment (no production network access)

### Key Concepts to Understand First

- [Darkmoon](https://github.com/ASCIT31/Dark-Moon) - Open source autonomous penetration testing platform (GPLv3). 50 specialist agents over MCP with proof of exploitation on every finding, runs locally.
- [3GPP Architecture Overview](https://www.3gpp.org/technologies/keywords-acronyms/98-lte): how UE, eNodeB, MME, SGW, PGW fit together
- [IMSI, IMEI, TMSI](https://en.wikipedia.org/wiki/International_mobile_subscriber_identity): subscriber identity fundamentals
- [AKA Protocol](https://www.3gpp.org/ftp/specs/archive/33_series/33.401/): how authentication works in LTE

---

## Rogue Base Stations

### GSM/CDMA Traffic Impersonation and Interception

- **[How To Build Your Own Rogue GSM BTS For Fun and Profit](https://www.evilsocket.net/2016/03/31/How-To-Build-Your-Own-Rogue-GSM-BTS-For-Fun-And-Profit/)**

  Guide to creating a portable GSM BTS for private networks or security testing. Covers technical setup using relatively inexpensive hardware.

- **[How to Create an Evil LTE Twin / LTE Rogue BTS](https://adam-toscher.medium.com/how-to-create-an-evil-lte-twin-34b0a9ce193b)**

  Tutorial for setting up a 4G/LTE Evil Twin base station using srsRAN and USRP SDR devices.

- **[Practical Attacks Against GSM Networks: Impersonation](https://blog.blazeinfosec.com/practical-attacks-against-gsm-networks-part-1/)**

  Detailed analysis of GSM base station impersonation using SDR and open source tools.

- **[Tutorial: Analyzing GSM with Airprobe and Wireshark](https://www.rtl-sdr.com/rtl-sdr-tutorial-analyzing-gsm-with-airprobe-and-wireshark/)**

  Step-by-step guide for using RTL-SDR to analyze GSM signals with GR-GSM/Airprobe and Wireshark.

- **[GSM/GPRS Traffic Interception for Penetration Testing](https://research.nccgroup.com/2016/05/19/gsm-gprs-traffic-interception-for-penetration-testing-engagements/)**

  NCC Group research on GSM/GPRS interception capabilities for penetration testing engagements.

---

## Recent Updates (2024-2025)

### New Research (2025)

- **[RANsacked: 100+ Flaws in LTE and 5G Implementations](https://thehackernews.com/2025/01/ransacked-over-100-security-flaws-found.html)** — University of Florida / NC State, Jan 2025

  Researchers disclosed 119 vulnerabilities (97 CVEs) across seven LTE and three 5G implementations including Open5GS, Magma, OpenAirInterface, Athonet, SD-Core, srsRAN. Every flaw can be used to persistently disrupt city-wide cellular communications. Some require no SIM card — a single unauthenticated packet can crash an MME or AMF.

- **[CITesting: Context Integrity Violations in LTE Core Networks](https://techxplore.com/news/2025-11-uncover-critical-flaws-global-mobile.html)** — KAIST, ACM CCS 2025 (Distinguished Paper)

  KAIST researchers identified a new class of uplink attacks against LTE core networks. Unlike traditional downlink attacks, these work through legitimate base stations and can affect anyone in the same MME coverage area. All four tested implementations (Open5GS, srsRAN, Amarisoft, Nokia) were vulnerable.

- **[Uncovering Hidden Paths in 5G: Protocol Tunneling and Network Boundary Bridging](https://dl.acm.org/doi/10.1145/3719027.3765206)** — ACM CCS 2025

  New research on exploiting protocol tunneling in 5G networks to cross network boundaries and reach components that should be isolated.

- **[BaseBridge: Over-the-Air and Emulation Testing for Cellular Baseband Firmware](https://dl.acm.org/doi/10.1145/3658644.3670320)** — IEEE S&P 2025

  Bridges the gap between over-the-air and emulation-based testing for cellular baseband firmware analysis.

- **[5G Network Slicing: Security Challenges, Attack Vectors, and Mitigation](https://pmc.ncbi.nlm.nih.gov/articles/PMC12251764/)** — PMC, July 2025

  Comprehensive classification of attacks across orchestration, virtualization, and inter-slice communication layers in 5G.

- **[Survey on 5G Physical Layer Security Threats and Countermeasures](https://www.mdpi.com/1424-8220/24/17/5523)** — MDPI Sensors, 2024

  In-depth review of PHY layer attack surface in 4G/5G: jamming, spoofing, eavesdropping, pilot contamination, and current SDR-based research tooling.

### Base Station Software and Tools (Updated)

- **[OpenBTS 2024 Reloaded](https://github.com/PentHertz/OpenBTS)** — Updated for modern UHD drivers and Ubuntu 22.04/24.04
- **[OpenAirInterface (OAI)](https://openairinterface.org/)** — Complete 3GPP Release-15+ implementation with active 5G development
- **[LimeNET CrowdCell](https://limemicro.com/)** — Network-in-a-box with integrated LimeSDR for small cell deployments
- **[Amarisoft LTEENB/gNB](https://www.amarisoft.com/)** — Professional-grade LTE/5G NR base station software
- **[DragonOS](https://github.com/cemaxecuter/DragonOS)** — Ubuntu-based SDR distro with cellular tools pre-installed
- **[Magma Core Network](https://magmacore.org/)** — Meta's distributed packet core, now under the Linux Foundation
- **[5GBaseChecker](https://github.com/SyNSec-den/5GBaseChecker)** — Automated 5G baseband vulnerability detection tool

---

## Software and Tools

### Base Station Software

| Software | Description | Link |
|----------|-------------|------|
| **OpenBTS (2024 Reloaded)** | Updated Linux SDR-based GSM air interface for modern systems | [GitHub](https://github.com/PentHertz/OpenBTS) |
| **OpenBTS (Original)** | Range Networks implementation | [SourceForge](https://sourceforge.net/projects/openbts/) |
| **YateBTS** | GSM/GPRS radio access network implementation | [Website](https://yatebts.com/) |
| **srsRAN Project** | Open-source 5G O-RAN CU/DU software suite | [GitHub](https://github.com/srsran/srsRAN_Project) |
| **srsRAN 4G** | Open-source 4G software radio suite | [GitHub](https://github.com/srsran/srsRAN_4G) |
| **OpenAirInterface** | Complete 4G/5G protocol stack | [Website](https://openairinterface.org/) |
| **Free5GC** | Open-source 5G core network implementation | [GitHub](https://github.com/free5gc/free5gc) |
| **Kamailio** | Open-source SIP server used in IMS/VoLTE labs | [Website](https://www.kamailio.org/) |

### Configuration Guides

- **[BladeRF and YateBTS Configuration](https://github.com/Nuand/bladeRF/wiki/Setting-up-Yate-and-YateBTS-with-the-bladeRF)**
- **[srsRAN Project Documentation](https://docs.srsran.com/projects/project)**
- **[srsRAN 4G Documentation](https://docs.srsran.com/projects/4g)**

### Analysis Tools

- **[LTE-Cell-Scanner](https://github.com/Evrytania/LTE-Cell-Scanner)** — LTE cell detection and analysis
- **[gr-gsm](https://github.com/ptrkrysik/gr-gsm/wiki/Passive-IMSI-Catcher)** — GSM analysis with GNU Radio
- **[IMSI-Catcher Detector](https://github.com/CellularPrivacy/Android-IMSI-Catcher-Detector)** — Android app for detecting IMSI catchers
- **[QCSuper](https://labs.p1sec.com/2019/07/09/presenting-qcsuper-a-tool-for-capturing-your-2g-3g-4g-air-traffic-on-qualcomm-based-phones/)** — Capture 2G-4G traffic using Qualcomm phones
- **[5GBaseChecker](https://github.com/SyNSec-den/5GBaseChecker)** — Automated 5G baseband vulnerability detection (Penn State, 2024)
- **[FALCON LTE](https://github.com/falkenber9/falcon)** — Fast analysis of LTE control channels in real-time
- **[Kalibrate](https://github.com/scateu/kalibrate-hackrf)** — GSM base station scanner and frequency calibration
- **[LTE Sniffer](https://github.com/SysSec-KAIST/LTESniffer)** — Open-source LTE downlink/uplink eavesdropper
- **[OsmocomBB](https://osmocom.org/projects/osmocombb)** — Free firmware for mobile phone baseband processors
- **[Modmobmap](https://github.com/Synacktiv-contrib/Modmobmap)** — Mobile network mapping
- **[Modmobjam](https://github.com/Synacktiv-contrib/Modmobjam)** — Mobile jamming research tool
- **[CITesting](https://dl.acm.org/doi/10.1145/3719027.3765230)** — Systematic testing of context integrity violations in LTE core networks (KAIST, 2025)
- **[SigPloit](https://github.com/SigPloiter/SigPloit)** — SS7/Diameter/GTP/SIP signaling security testing framework
- **[LTEFuzz](https://github.com/koo7/LTEFuzz)** — LTE protocol fuzzer from KAIST, predecessor to CITesting; generates malformed NAS/RRC messages
- **[Crocodile Hunter](https://github.com/EFForg/crocodile-hunter)** — EFF open-source tool for detecting rogue cell towers by wardriving
- **[SCAT](https://github.com/fgsect/scat)** — Signaling Collection and Analysis Tool; captures diagnostic logs from Qualcomm and Samsung basebands
- **[ss7map](https://ss7map.p1sec.com/)** — SS7 network exposure mapping by P1 Security
- **[Diameter EAP Tool (DET)](https://github.com/intelmq/intelmq)** — Diameter protocol fuzzing and testing
- **[Osmocom Suite](https://osmocom.org/projects)** — Complete open-source GSM/GPRS stack: osmo-nitb, osmo-bts, osmo-sgsn, osmo-msc and more

---

## Hardware Setup

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

### SDR Hardware Options

| Hardware | Frequency Range | Bandwidth | Price Range | Use Case | Link |
|----------|----------------|-----------|-------------|----------|------|
| **Ettus Research (USRP)** | | | | | |
| **USRP B210** | 70 MHz - 6 GHz | 61.44 MHz | $2,100 | Professional development, 2x2 MIMO | [Ettus](https://www.ettus.com/all-products/ub210-kit/) |
| **USRP B200mini** | 70 MHz - 6 GHz | 61.44 MHz | $775 | Compact USRP B-series | [Ettus](https://www.ettus.com/) |
| **USRP N210** | DC - 6 GHz | 25 MHz | $1,700 | High-performance networked SDR | [Ettus](https://www.ettus.com/) |
| **USRP N320** | 1 MHz - 6 GHz | 200 MHz | $8,000 | Networked 2x2 MIMO | [Ettus](https://www.ettus.com/) |
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
| **RTL-SDR V4** | 500 kHz - 1.75 GHz | 3.2 MHz | $40 | Latest with R828D tuner | [RTL-SDR](https://www.rtl-sdr.com/rtl-sdr-blog-v4-dongle-initial-release/) |
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

### Common SDR Issues and Troubleshooting

| Issue | Possible Causes |
|-------|----------------|
| Device not detected | Improper firmware, USB connection issues |
| Poor signal quality | Incorrect antennas, wrong frequency configuration |
| Connection failures | Wrong SIM, incorrect MCC/MNC codes |
| Performance issues | Virtualized platform limitations, wrong SDR firmware |

---

## Testing and Research Methodologies

### Modern Baseband Fuzzing (2024-2025)

- **[Budget-Friendly Baseband Fuzzing Setup](https://t2.fi/schedule/2024/)** — DefCon 32, Janne Taponen

  Covers building cost-effective baseband fuzzing rigs using SDRs, using LLMs to accelerate protocol parser development, and testing automotive ECUs, payment terminals, and mobile devices.

- **[RANsacked Fuzzing Framework](https://dl.acm.org/doi/10.1145/3658644.3670320)** — University of Florida / NC State, ACM CCS 2024

  Domain-informed fuzzing approach targeting RAN-Core interfaces. Discovered 119 vulnerabilities across ten network implementations.

- **[BaseBridge](https://dl.acm.org/doi/10.1145/3658644.3670320)** — IEEE S&P 2025

  Framework that bridges over-the-air and emulation-based testing for cellular baseband firmware.

### Vulnerability Research Tools

- **[5GBaseChecker](https://github.com/SyNSec-den/5GBaseChecker)** — Automated 5G baseband vulnerability detection
- **[CITesting](https://dl.acm.org/doi/10.1145/3719027.3765230)** — Context integrity violation testing for LTE core networks
- **[certmitm](https://github.com/juurlink/certmitm)** — TLS implementation testing tool

---

## Attack Vectors

### Radio Jamming Attacks

From [NIST SP 800-187](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-187.pdf):

- **Smart Jamming** — Targeted channel interference timed to avoid detection
- **Dumb Jamming** — Broadband noise across frequency ranges
- **UE Interface Jamming** — Preventing UE signaling to eNodeB
- **eNodeB Interface Jamming** — Disrupting base station communications

### 5G Security Research

- **[Privacy Attacks on 4G/5G Paging Protocols](https://assets.documentcloud.org/documents/5749002/4G-5G-paper-at-NDSS-2019.pdf)** — NDSS 2019
- **[European 5G Security in the Wild](https://arxiv.org/pdf/2305.08635.pdf)** — 2023
- **[5G Threat Modeling Framework](https://arxiv.org/pdf/2005.05110v1.pdf)**
- **[ENISA 5G Threat Landscape](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/5g/ENISA-5G-threat-landscape.pdf)**
- **[5GReasoner Analysis Framework](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/5g/5GReasoner.pdf)**
- **[5G NR Jamming, Spoofing, and Sniffing](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/5g/5gjam.pdf)**
- **[New Privacy Threat on 3G, 4G, and 5G AKA Protocols](https://arxiv.org/pdf/1905.07617.pdf)**
- **[Insecure Connection Bootstrapping in Cellular Networks](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/lte/wisec19-preprint.pdf)**
- **[Protecting 4G and 5G Cellular Paging Protocols](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/5g/popets-2020-0008.pdf)**
- **[Uncovering Hidden Paths in 5G: Protocol Tunneling](https://dl.acm.org/doi/10.1145/3719027.3765206)** — ACM CCS 2025
- **[5G Network Slicing Attack Classification](https://pmc.ncbi.nlm.nih.gov/articles/PMC12251764/)** — MDPI, July 2025

### LTE/4G Security Research

- **[LTRACK: Stealthy Mobile Phone Tracking](https://www.usenix.org/system/files/sec22summer_kotuliak.pdf)** — USENIX Security 2022
- **[Detecting Fake 4G Base Stations in Real Time](https://i.blackhat.com/USA-20/Wednesday/us-20-Quintin-Detecting-Fake-4G-Base-Stations-In-Real-Time.pdf)** — Black Hat 2020
- **[BaseSAFE: Baseband Fuzzing](https://arxiv.org/pdf/2005.07797.pdf)**
- **[LTE Public Warning System Attacks](https://netstech.org/wp-content/uploads/2019/06/cmas-mobisys2019.pdf)**
- **[Signal Overshadowing Attacks](https://www.usenix.org/system/files/sec19-yang-hojoon.pdf)** — USENIX Security 2019
- **[Breaking LTE on Layer Two](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/lte/breaking-lte-layer-two.pdf)**
- **[LTE/LTE-A Jamming, Spoofing, and Sniffing](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/lte/LTE-jamming-magazine.pdf)**
- **[LTE Protocol Exploits](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/lte/LTE-security-TakeDownCon.pdf)**
- **[Practical Attacks Against Privacy and Availability](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/lte/Prac-4G-Attacks.pdf)**
- **[LTE Security Assessment](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/lte/LTE-open-source-HackerHalted.pdf)**
- **[LTE Security Disabled: Misconfiguration in Commercial Networks](https://www.infsec.ruhr-uni-bochum.de/media/infsec/veroeffentlichungen/2019/04/23/wisec19-final123.pdf)**
- **[All The 4G Modules Could Be Hacked](https://i.blackhat.com/USA-19/Wednesday/us-19-Shupeng-All-The-4G-Modules-Could-Be-Hacked.pdf)** — Black Hat 2019
- **[Paging Storm Attacks Against 4G/LTE Networks](https://www.cs.binghamton.edu/~ghyan/papers/wisec20.pdf)**
- **[Analysis of the LTE Control Plane](https://syssec.kaist.ac.kr/pub/2019/kim_sp_2019.pdf)** — IEEE S&P 2019
- **[Baseband Attacks: Remote Exploitation of Memory Corruptions](https://www.usenix.org/system/files/conference/woot12/woot12-final24.pdf)** — WOOT 2012
- **[CITesting: Context Integrity Violations in LTE Core Networks](https://dl.acm.org/doi/10.1145/3719027.3765230)** — ACM CCS 2025 (Distinguished Paper)
- **[New Vulnerabilities in 4G and 5G Cellular Access Network Protocols](https://dl.acm.org/doi/10.1145/3317549.3319728)** — WiSec 2019

---

## Conference Talks

### ACM CCS 2025

- **[CITesting: Systematic Testing of Context Integrity Violations in LTE Core Networks](https://dl.acm.org/doi/10.1145/3719027.3765230)** — KAIST (Distinguished Paper)

  New class of uplink attacks against LTE core networks that work through legitimate base stations — no rogue BTS required. All four tested implementations were vulnerable, including commercial systems from Nokia and Amarisoft.

- **[Uncovering Hidden Paths in 5G: Exploiting Protocol Tunneling and Network Boundary Bridging](https://dl.acm.org/doi/10.1145/3719027.3765206)**

  Demonstrates how attackers can use protocol tunneling to traverse network boundaries and reach isolated 5G components.

### IEEE S&P 2025

- **[BaseBridge: Bridging Over-the-Air and Emulation Testing for Cellular Baseband Firmware](https://dl.acm.org/doi/10.1145/3658644.3670320)**

  New framework for cellular baseband firmware security testing that combines emulation and OTA testing approaches.

### Black Hat USA 2024

- **[5G Baseband Vulnerabilities — Penn State University](https://techcrunch.com/2024/08/07/hackers-could-spy-on-cellphone-users-by-abusing-5g-baseband-flaws-researchers-say/)**

  Researchers disclosed 12 vulnerabilities in 5G basebands from Samsung, MediaTek, and Qualcomm, affecting devices from Google, OPPO, OnePlus, Motorola, and Samsung. Accompanied by the release of the 5GBaseChecker tool.

### DefCon 32 (2024)

- **[Economizing Mobile Network Warfare: Budget-Friendly Baseband Fuzzing](https://t2.fi/schedule/2024/)** — Janne Taponen

  Making baseband fuzzing accessible with affordable SDR hardware. Covers LLM-assisted protocol parser development and vulnerability discovery across automotive ECUs, payment terminals, and cellular modems.

### Black Hat USA 2022

- **[Attacks from a New Front Door in 4G and 5G Networks](https://i.blackhat.com/USA-22/Wednesday/US-22-Shaik-Attacks-From-a-New-Front-Door-in-4G-5G-Mobile-Networks.pdf)**

### Black Hat USA 2021

- **[Over The Air Baseband Exploit: 5G RCE](https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Over-The-Air-Baseband-Exploit-Gaining-Remote-Code-Execution-On-5G-Smartphones.pdf)** — [White Paper](https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Over-The-Air-Baseband-Exploit-Gaining-Remote-Code-Execution-On-5G-Smartphones-wp.pdf)

### Black Hat USA 2020

- **[Detecting Fake 4G Base Stations in Real Time](https://i.blackhat.com/USA-20/Wednesday/us-20-Quintin-Detecting-Fake-4G-Base-Stations-In-Real-Time.pdf)**

### Additional Conference Resources

- **[NSA PLAYSET GSM](https://www.defcon.org/images/defcon-22/dc-22-presentations/Pierce-Loki/DEFCON-22-Pierce-Loki-NSA-PLAYSET-GSM.pdf)** — DEF CON 22
- **[VoLTE Phreaking](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/talks/HAXPO-VoLTE-Phreaking-Ralph-Moonen.pdf)** — Ralph Moonen
- **[RF Exploitation: IoT/OT Hacking with SDR](https://conference.hitb.org/hitbsecconf2019ams/materials/HAXPO%20D2%20-%20Demystifying%20IoT:OT%20Hacks%20With%20SDR%20-%20Himanshu%20Mehta%20&%20Harshit%20Agrawal.pdf)** — HITB 2019
- **[Bye-Bye IMSI Catchers: Security Enhancements in 5G](https://conference.hitb.org/hitbsecconf2018pek/materials/D2T2%20-%20Bye%20Bye%20IMSI%20Catchers%20-%20Security%20Enhancements%20in%205g%20-%20Lin%20Huang.pdf)** — HITB 2018
- **[Side Channel Attacks in 4G and 5G](https://i.blackhat.com/eu-19/Thursday/eu-19-Hussain-Side-Channel-Attacks-In-4G-And-5G-Cellular-Networks.pdf)** — Black Hat Europe 2019
- **[Dirty Use of USSD Codes in Cellular Networks](https://troopers.de/wp-content/uploads/2012/12/TROOPERS13-Dirty_use_of_USSD_codes_in_cellular-Ravi_Borgaonkor.pdf)** — TROOPERS 2013, Ravi Borgaonkar
- **[Hacking LTE Public Warning Systems](https://conference.hitb.org/hitbsecconf2019ams/materials/HAXPO%20D1%20-%20Hacking%20LTE%20Public%20Warning%20Systems%20-%20Weiguang%20Li.pdf)** — HITB 2019

---

## Research Papers

### 2025

- **[CITesting: Systematic Testing of Context Integrity Violations in LTE Core Networks](https://dl.acm.org/doi/10.1145/3719027.3765230)** — ACM CCS 2025 (Distinguished Paper Award)

  KAIST's CITesting tool runs thousands of test cases against LTE core implementations, dwarfing the 31-case coverage of prior tooling (LTEFuzz). All four tested implementations contained CIV vulnerabilities.

- **[Uncovering Hidden Paths in 5G: Protocol Tunneling and Network Boundary Bridging](https://dl.acm.org/doi/10.1145/3719027.3765206)** — ACM CCS 2025

- **[5G Network Slicing: Security Challenges, Attack Vectors, and Mitigation Approaches](https://pmc.ncbi.nlm.nih.gov/articles/PMC12251764/)** — MDPI, July 2025

- **[Starshields for iOS: Navigating the Security Cosmos in Satellite Communication](https://www.ndss-symposium.org/wp-content/uploads/2025-124-paper.pdf)** — NDSS 2025

  First comprehensive security analysis of Apple's satellite communication features. Researchers reverse-engineered the proprietary protocol, demonstrated restriction bypasses, and built a simulation testbed covering Emergency SOS, Find My, roadside assistance, and iMessage over satellite.

### 2024

- **[RANsacked: A Domain-Informed Approach for Fuzzing LTE and 5G RAN-Core Interfaces](https://dl.acm.org/doi/10.1145/3658644.3670320)** — ACM CCS 2024

  119 vulnerabilities, 97 CVEs, across ten implementations. Any one of them enables city-wide disruption of cellular communications.

- **[Survey on 5G Physical Layer Security Threats and Countermeasures](https://www.mdpi.com/1424-8220/24/17/5523)** — MDPI Sensors 2024

  Comprehensive review of PHY-layer attack surface covering eavesdropping, jamming, spoofing, pilot contamination, and SDR-based research frameworks.

- **[5GBaseChecker Tool Release](https://github.com/SyNSec-den/5GBaseChecker)** — Penn State University

  Open-source tool for detecting vulnerabilities in 5G baseband implementations. Used to find 12 critical bugs in Samsung, MediaTek, and Qualcomm chipsets.

### 2019-2023

- **[Privacy Attacks on 4G/5G Paging Protocols](https://assets.documentcloud.org/documents/5749002/4G-5G-paper-at-NDSS-2019.pdf)** — NDSS 2019
- **[New Vulnerabilities in 4G and 5G Cellular Access Network Protocols](https://dl.acm.org/doi/10.1145/3317549.3319728)** — WiSec 2019

  Three new attack classes exploiting unprotected device capability information: identification, bidding-down, and battery drain.

- **[New Privacy Threat on 3G, 4G, and Upcoming 5G AKA Protocols](https://arxiv.org/pdf/1905.07617.pdf)**
- **[BaseSAFE: Baseband SAnitized Fuzzing through Emulation](https://arxiv.org/pdf/2005.07797.pdf)**
- **[European 5G Security in the Wild](https://arxiv.org/pdf/2305.08635.pdf)** — 2023

---

## Equipment and Hardware

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

---

## Detection and Defense

### Protection from Stingrays and IMSI Catchers

- **[CellGuard](https://github.com/seemoo-lab/CellGuard)** — SEEMOO Lab, 2024

  iOS app that detects rogue base stations by analyzing baseband packets in real-time. Integrates with the Apple Cell Location Database for anomaly detection. [Website](https://cellguard.seemoo.tu-darmstadt.de/) — [TestFlight Beta](https://testflight.apple.com/join/HrsaoHM3)

### IMSI Catcher Detection and Research

- **[SeaGlass: City-Wide IMSI-Catcher Detection](https://seaglass.cs.washington.edu/)** — UW
- **[SeaGlass Research Paper](https://seaglass-web.s3.amazonaws.com/SeaGlass___PETS_2017.pdf)** — PETS 2017
- **[Evaluating IMSI Catcher Detectors](http://www.cs.ox.ac.uk/files/9192/paper-final-woot-imsi.pdf)** — Oxford
- **[IMSI-Catcher Detector (Android)](https://github.com/CellularPrivacy/Android-IMSI-Catcher-Detector)**

### Security Advisories

- **[CERT Alert: VoLTE Implementation Vulnerabilities](https://www.kb.cert.org/vuls/id/943167/)**

---

## Cellular IoT and NB-IoT Security

- **[NB-IoT Security Analysis Framework](https://arxiv.org/search/?query=NB-IoT+security)** — Narrowband IoT security research
- **[Cat-M1/LTE-M Attack Vectors](https://www.gsma.com/iot/mobile-iot-security/)** — GSMA IoT security guidelines
- **[Monitoring 5G Core Networks Vulnerabilities With eBPF](https://ieeexplore.ieee.org/document/10870553)** — IEEE Networking Letters 2025

---

## Satellite-Cellular Integration

- **[Starshields for iOS: Satellite Communication Security](https://www.ndss-symposium.org/wp-content/uploads/2025-124-paper.pdf)** — NDSS 2025
- **[3GPP Non-Terrestrial Networks (NTN) Security](https://www.3gpp.org/specifications/specification-numbering)** — Official 5G satellite integration specs
- **[LEO Satellite Cellular Vulnerabilities](https://arxiv.org/search/?query=satellite+cellular+security)** — Low Earth Orbit security research

---

## Private 5G Network Security

- **[O-RAN Security Research](https://www.o-ran.org/specifications)** — Open RAN security specifications
- **[Private 5G Penetration Testing Guide](https://www.nist.gov/cybersecurity)** — Enterprise private network testing
- **[Campus 5G Security Assessment](https://csrc.nist.gov/)** — NIST private 5G security guidance

---

## Network Slicing and Edge Security

- **[5G Network Slicing Attack Research](https://pmc.ncbi.nlm.nih.gov/articles/PMC12251764/)** — MDPI, July 2025
- **[Multi-Access Edge Computing (MEC) Vulnerabilities](https://www.etsi.org/technologies/multi-access-edge-computing)** — ETSI MEC security specs
- **[Network Function Virtualization (NFV) Attacks](https://www.etsi.org/technologies/nfv)** — Virtual network function security

---

## Automotive and Industrial Cellular

- **[V2X Security Research](https://www.its.dot.gov/research_areas/emerging_tech/htm/EmerTech_V2X.htm)** — Vehicle-to-everything communications
- **[Cellular-V2X Attack Vectors](https://ieeexplore.ieee.org/search/searchresult.jsp?queryText=C-V2X+security)** — Automotive cellular security
- **[BMW Security Assessment using OpenBTS](https://keenlab.tencent.com/en/whitepapers/Experimental_Security_Assessment_of_BMW_Cars_by_KeenLab.pdf)** — Keen Lab / Tencent

---

## Forensics and Investigation

- **[XRY Mobile Forensics](https://msab.com/products/xry/)** — Commercial cellular forensics platform
- **[Cellebrite UFED](https://cellebrite.com/)** — Mobile device extraction tools
- **[NIST Mobile Forensics Guidelines](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-101r1.pdf)** — NIST SP 800-101r1

---

## Vulnerability Disclosure

- **[Android Security Bulletins](https://source.android.com/docs/security/bulletin)** — Regular Android/baseband patches
- **[Qualcomm Security Bulletins](https://www.qualcomm.com/company/product-security/bulletins)** — Snapdragon security updates
- **[Samsung Mobile Security](https://security.samsungmobile.com/)** — Galaxy security research program
- **[Apple Security Research](https://security.apple.com/)** — iOS/baseband security program

---

## SIM Security

- **[Rooting SIM Cards](https://media.blackhat.com/us-13/us-13-Nohl-Rooting-SIM-cards-Slides.pdf)** — Black Hat 2013, Karsten Nohl
- **[SIM Port Hack Case Study](https://medium.com/coinmonks/the-most-expensive-lesson-of-my-life-details-of-sim-port-hack-35de11517124)**
- **[Cloning 3G/4G SIM Cards With a PC and an Oscilloscope](https://www.blackhat.com/docs/us-15/materials/us-15-Yu-Cloning-3G-4G-SIM-Cards-With-A-PC-And-An-Oscilloscope-Lessons-Learned-In-Physical-Security-wp.pdf)** — Black Hat 2015

---

## SS7 and Telecom Infrastructure

### SS7 Attack Research

- **[Bypassing GSMA SS7 Recommendations](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/ss7/Bypassing-GSMA-SS7-Kirill-Puzankov.pdf)** — Kirill Puzankov
- **[Attacking SS7 Networks](http://www.hackitoergosum.org/2010/HES2010-planglois-Attacking-SS7.pdf)** — HES 2010
- **[SS7: Locate. Track. Manipulate.](https://media.ccc.de/v/31c3_-_6249_-_en_-_saal_1_-_201412271715_-_ss7_locate_track_manipulate_-_tobias_engel)** — 31C3 2014, Tobias Engel; live demonstration of cross-network subscriber tracking
- **[SS7 Map](https://ss7map.p1sec.com/)** — P1 Security; map of SS7 exposure across global carriers
- **[Diameter Vulnerabilities Exposure](https://www.gsma.com/security/resources/fs-07-diameter-security/)** — GSMA FS.07; official Diameter security guidance for 4G roaming
- **[GSMA FS.11 SS7 Security](https://www.gsma.com/security/resources/fs-11-ss7-security/)** — GSMA baseline SS7 network security requirements

### SS7/Diameter Testing Tools

- **[SigPloit](https://github.com/SigPloiter/SigPloit)** — Modular testing framework for SS7, Diameter, GTP, and SIP; covers location tracking, call/SMS interception, and DoS scenarios
- **[ss7map](https://ss7map.p1sec.com/)** — Automated SS7 network topology and exposure mapper
- **[SCTP scanner](https://github.com/adagilabs/sctp_scanner)** — Discovers SCTP-based SS7 endpoints on IP networks

---

## Surveillance Technology

### Stingray / IMSI Catchers

- **[DHS Stingray Surveillance](https://www.wired.com/story/dcs-stingray-dhs-surveillance/)** — Wired
- **[Stingray Cost Analysis](https://www.vice.com/en_us/article/gv5k3x/heres-how-much-a-stingray-cell-phone-surveillance-tool-costs)** — Vice
- **[NYCLU Stingray Information](https://www.nyclu.org/en/stingrays)**
- **[EFF: Cell Site Simulators / IMSI Catchers](https://www.eff.org/pages/cell-site-simulatorsimsi-catchers)**
- **[WiFi IMSI Catcher](https://www.blackhat.com/docs/eu-16/materials/eu-16-OHanlon-WiFi-IMSI-Catcher.pdf)** — Black Hat Europe 2016

---

## Recent CVEs and Updates

- **[NVD CVE Search](https://nvd.nist.gov/vuln/search)** — Search for cellular-related CVEs
- **[Google Project Zero](https://googleprojectzero.blogspot.com/)** — Ongoing mobile security research
- **[Samsung Security Bulletins](https://security.samsungmobile.com/securityUpdate.smc)** — Regular baseband updates
- **[SIMjacker Research](https://simjacker.com/)** — SIM-based attack evolution

---

## International Research

- **[ENISA 5G Reports](https://www.enisa.europa.eu/)** — EU 5G security assessments
- **[KAIST SysSec Lab](https://syssec.kaist.ac.kr/)** — Leading cellular security research group (CITesting, LTEFuzz, LTESniffer)
- **[Japanese 5G Security Guidelines](https://www.nisc.go.jp/eng/)** — Japan national cybersecurity strategy

---

## Training and Education

- **[SANS Mobile Security](https://www.sans.org/)** — Professional mobile security courses
- **[Offensive Security Mobile Testing](https://www.offensive-security.com/)** — Advanced mobile penetration testing
- **[OpenAirInterface Lab Setup](https://github.com/OpenAirInterface/openairinterface5g)** — Open-source 5G lab environment
- **[GNU Radio / SDR University Courses](https://www.gnuradio.org/)** — SDR educational materials

---

## Vendor-Specific Research

- **[Ericsson Security Research](https://www.ericsson.com/en/security)**
- **[Nokia Bell Labs Security](https://www.bell-labs.com/)**
- **[Qualcomm Security Bulletins](https://www.qualcomm.com/company/product-security/bulletins)**
- **[MediaTek Product Security](https://www.mediatek.com/)**

---

## Roaming and Interconnect Security

- **[GRX/IPX Security Research](https://www.gsma.com/newsroom/)** — GSMA roaming security
- **[Diameter Protocol Security](https://tools.ietf.org/html/rfc6733)** — 4G/5G signaling security
- **[GSMA FS.19 IPX Security](https://www.gsma.com/security/resources/fs-19-ipe-security/)** — Security requirements for IPX providers handling roaming traffic
- **[Roaming Attacks via Diameter](https://www.p1sec.com/blog/diameter-roaming-attacks/)** — P1 Security analysis of Diameter-based roaming attack surface
- **[GTP Vulnerabilities in 4G/5G Roaming](https://www.a1qa.com/blog/gtp-vulnerabilities-mobile-network-security/)** — GTP-C and GTP-U attack surface at the roaming interface
- **[AdaptiveMobile SS7 Firewall Research](https://www.adaptivemobile.com/resources)** — Carrier-grade SS7/Diameter firewall bypass techniques

---

## Resources

### Development and Analysis Tools

- **[RTL-SDR Community](https://www.rtl-sdr.com/)** — SDR resources and tutorials
- **[MCC-MNC Database](http://www.mcc-mnc.com/)** — Mobile Country/Network Code reference
- **[RFSec-ToolKit](https://github.com/cn0xroot/RFSec-ToolKit)** — RF security testing tools
- **[cellularsecurity.org](https://cellularsecurity.org/)** — Community resource for cellular security research

### Research Collections

- **[RF Security Documentation](https://rmusser.net/docs/Wireless.html#cn)**
- **[USENIX Security Papers](https://www.usenix.org/conferences)** — Security conference proceedings
- **[ACM Digital Library](https://dl.acm.org/)** — ACM research papers
- **[IEEE Xplore](https://ieeexplore.ieee.org/)** — IEEE research database

### Legal and Regulatory

- **[FCC Equipment Authorization Rules](https://www.fcc.gov/general/equipment-authorization-procedures)** — US cellular equipment regulations
- **[CISA 5G Security Guidance](https://www.cisa.gov/)** — US critical infrastructure guidance
- **[NIST 5G Cybersecurity](https://www.nist.gov/cybersecurity)** — NIST cellular security frameworks

### Additional Reading

- **[Analyzing GSM Downlink with USRP](http://leetupload.com/blagosphere/2014/03/28/analyze-and-crack-gsm-downlink-with-a-usrp/)**
- **[AT&T Microcell Analysis](https://fail0verflow.com/blog/2012/microcell-fail/)**
- **[LTE Recon — DefCon 23](https://www.rtl-sdr.com/one-more-rtl-sdr-talk-from-defcon-23/)**
- **[LTE Security Guide — NIST SP 800-187](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-187.pdf)**
- **[LTE Pwnage: Core Network Elements](https://conference.hitb.org/hitbsecconf2013ams/materials/D1T2%20-%20Philippe%20Langlois%20-%20Hacking%20HLR%20HSS%20and%20MME%20Core%20Network%20Elements.pdf)** — HITB 2013

---

## Community

### Mailing Lists and Forums

- **[Osmocom Mailing Lists](https://lists.osmocom.org/mailman/listinfo)** — Active developer and user lists for OpenBTS, OsmocomBB, srsRAN topics
- **[srsRAN Discussions](https://github.com/srsran/srsRAN_Project/discussions)** — GitHub Discussions for the srsRAN Project
- **[OpenAirInterface Forum](https://gitlab.eurecom.fr/oai/openairinterface5g/-/issues)** — OAI issue tracker and community support
- **[Reddit r/RTLSDR](https://www.reddit.com/r/RTLSDR/)** — Active SDR community covering cellular scanning and analysis
- **[Reddit r/cellmapper](https://www.reddit.com/r/cellmapper/)** — Cell tower mapping and analysis community

### IRC and Chat

- **[Osmocom IRC](https://osmocom.org/projects/cellular-infrastructure/wiki/IRC)** — #osmocom on libera.chat; real-time support for Osmocom tools
- **[DEF CON RF Village](https://rfvillage.org/)** — Annual RF hacking community track at DEF CON

### Conferences to Follow

- **[DEF CON](https://defcon.org/)** — RF Village, Wireless Village, and main track cellular talks
- **[Black Hat USA/Europe](https://www.blackhat.com/)** — Regular cellular/baseband research presentations
- **[WiSec](https://wisec.acm.org/)** — ACM Conference on Security and Privacy in Wireless and Mobile Networks
- **[IEEE S&P / CCS / USENIX Security](https://www.ieee-security.org/TC/SP/)** — Top-tier academic venue for cellular security papers
- **[HITB](https://conference.hitb.org/)** — Regular telecom security talks

---

## Contributing

Fork the repo, add resources with descriptions, verify links are active, and submit a pull request with context on what was added.

## Legal Notice

This repository is for educational and research purposes only. Users are responsible for complying with all applicable laws and regulations. The maintainers do not endorse or encourage illegal activities.

---

**Last Updated:** March 2026
**Maintainer:** [@W00t3k](https://github.com/W00t3k)

*Broken links or new resources? Open an issue or submit a PR.*
