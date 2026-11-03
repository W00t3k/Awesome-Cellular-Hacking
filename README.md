# Awesome Cellular Hacking

> A comprehensive curated list of resources for 2G/3G/4G/5G cellular security research and analysis

This repository consolidates community knowledge in the cellular security space, including exploits, research papers, tools, and educational resources. The goal is to preserve and organize important security research that might otherwise become difficult to find.

**Disclaimer:** This information is intended for educational and defensive security research purposes only. Use responsibly and in compliance with applicable laws and regulations.

## Table of Contents

- [Getting Started](#getting-started)
- [Rogue Base Stations](#rogue-base-stations)
- [Recent Updates (2024-2026)](#recent-updates-2024-2026)
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
- Software: 5GBaseChecker, LTEFuzz, BaseBridge, SigPloit, FirmWire, 5GHOUL
- Focus areas: Baseband fuzzing, RAN-Core interface testing, SS7/Diameter signaling

### Lab Setup Checklist

- [ ] Linux host (Ubuntu 22.04 or 24.04 recommended)
- [ ] UHD drivers installed and device recognized (`uhd_find_devices`)
- [ ] Faraday cage or RF shielding for active transmissions
- [ ] Programmable SIM cards (sysmoUSIM-SJA2 or similar)
- [ ] Dedicated test devices (not your daily driver)
- [ ] Isolated network environment (no production network access)

### Key Concepts to Understand First

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

## Recent Updates (2024-2026)

### New Research (2025-2026)

- **[SNI5GECT: Sniffing and Injecting 5G Traffic Without Rogue Base Stations](https://thehackernews.com/2025/08/new-sni5gect-attack-crashes-phones-and.html)** — Singapore University of Technology and Design, USENIX Security 2025

  Framework that enables sniffing unencrypted 5G messages and injecting attack payloads over-the-air without jamming or rogue base stations. An attacker within 20 meters can force devices to reboot and downgrade to 4G. [GitHub](https://github.com/asset-group/5ghoul-5g-nr-attacks)

- **[5Gone: Uplink Overshadowing Attacks in 5G-SA](https://arxiv.org/abs/2602.10272)** — ETH Zurich, Feb 2026

  SDR-based uplink overshadowing attack against 5G-SA networks exploiting 3GPP standard deficiencies. Enables surgical DoS, privacy, and downgrade attacks with E2E latency under 500μs. Runs on standard x86 hardware without dedicated acceleration.

- **[Kairos: Timing-Induced Interaction Failures in LTE and 5G Core Networks](https://arxiv.org/abs/2605.30985)** — 2026

  Lightweight testing framework exposing timing-induced interaction failures. Discovered 20 new vulnerabilities and reproduced 34 existing issues across Open5GS, srsRAN, Amarisoft, and commercial implementations.

- **[RANsacked: 100+ Flaws in LTE and 5G Implementations](https://thehackernews.com/2025/01/ransacked-over-100-security-flaws-found.html)** — University of Florida / NC State, Jan 2025

  Researchers disclosed 119 vulnerabilities (97 CVEs) across seven LTE and three 5G implementations including Open5GS, Magma, OpenAirInterface, Athonet, SD-Core, srsRAN. Every flaw can be used to persistently disrupt city-wide cellular communications. Some require no SIM card — a single unauthenticated packet can crash an MME or AMF.

- **[CITesting: Context Integrity Violations in LTE Core Networks](https://dl.acm.org/doi/10.1145/3719027.3765230)** — KAIST, ACM CCS 2025 (Distinguished Paper)

  KAIST researchers identified a new class of uplink attacks against LTE core networks. Unlike traditional downlink attacks, these work through legitimate base stations and can affect anyone in the same MME coverage area. All four tested implementations (Open5GS, srsRAN, Amarisoft, Nokia) were vulnerable.

- **[LLFuzz: LLM-Guided Baseband Firmware Fuzzing](https://arxiv.org/abs/2507.09660)** — KAIST, July 2025

  LLM-guided fuzzing framework for cellular baseband firmware targeting MediaTek and Samsung Shannon. Discovered 11 memory corruption vulnerabilities including buffer overflows in NAS and RRC message handlers. Leverages LLM to generate semantically valid protocol messages.

- **[Uncovering Hidden Paths in 5G: Protocol Tunneling and Network Boundary Bridging](https://dl.acm.org/doi/10.1145/3719027.3765206)** — ACM CCS 2025

  New research on exploiting protocol tunneling in 5G networks to cross network boundaries and reach components that should be isolated.

- **[BaseBridge: Over-the-Air and Emulation Testing for Cellular Baseband Firmware](https://github.com/FirmWire/BaseBridge)** — IEEE S&P 2025

  Bridges the gap between over-the-air and emulation-based testing for cellular baseband firmware analysis. Extends the FirmWire emulator.

- **[From Control to Chaos: Formal Analysis of 5G Access Control](https://sp2025.ieee-security.org/accepted-papers.html)** — Penn State, IEEE S&P 2025

  Comprehensive formal analysis of 5G's access control mechanisms, uncovering critical vulnerabilities.

- **[Devilray: Adversarial Model Revealing Blind Spots in Fake Base Station Detection](https://arxiv.org/abs/2605.19232)** — May 2026

  Systematic adversarial baseline exploring realistic FBS evasion strategies. Evaluates 7 detectors and identifies gaps in coverage across 2,592 feasible FBS configurations.

- **[GLaDoS: Location-aware Denial-of-Service of Cellular Networks](https://dl.acm.org/doi/10.5555/3766078.3766351)** — USENIX Security 2025

  Location-aware DoS attacks targeting specific geographical areas in cellular networks.

- **[Breaking 5G on The Lower Layer](https://arxiv.org/abs/2602.10250)** — 2026

  Lower-layer exploitation research presenting SIB1 spoofing and Timing Advance manipulation attacks during random access procedures.

- **[5G Network Slicing: Security Challenges, Attack Vectors, and Mitigation](https://pmc.ncbi.nlm.nih.gov/articles/PMC12251764/)** — PMC, July 2025

  Comprehensive classification of attacks across orchestration, virtualization, and inter-slice communication layers in 5G.

- **[Survey on 5G Physical Layer Security Threats and Countermeasures](https://www.mdpi.com/1424-8220/24/17/5523)** — MDPI Sensors, 2024

  In-depth review of PHY layer attack surface in 4G/5G: jamming, spoofing, eavesdropping, pilot contamination, and current SDR-based research tooling.

### New Research (2024)

- **[Hermes: Unlocking Security Analysis of Cellular Network Protocols](https://www.usenix.org/conference/usenixsecurity24/presentation/al-ishtiaq)** — USENIX Security 2024

  End-to-end framework to automatically generate formal FSM representations from natural language cellular specifications. Achieves 81-87% accuracy and uncovers 3 new vulnerabilities plus 19 previous attacks in 4G/5G specifications. [GitHub](https://github.com/SyNSec-den/hermes-spec-to-fsm)

- **[CellularLint: Identifying Inconsistent Behavior in Cellular Network Specifications](https://www.usenix.org/conference/usenixsecurity24/presentation/rahman)** — USENIX Security 2024

  Semi-automatic framework for inconsistency detection in 4G/5G standards using few-shot learning on domain-adapted LLMs. [GitHub](https://github.com/CellularLint/cellularlint-codes)

- **[Logic Gone Astray: Security Analysis of 5G Basebands](https://www.usenix.org/conference/usenixsecurity24/)** — USENIX Security 2024

  Control plane protocol security analysis framework for 5G baseband implementations.

- **[ASTRA-5G: Automated Over-the-Air Security Testing](https://dl.acm.org/doi/abs/10.1145/3643833.3656141)** — WiSec 2024

  Open-source framework automating security testing for 5G SA devices by leveraging enhanced core and RAN software. [Research Paper](https://research.google/pubs/astra-5g-automated-over-the-air-security-testing-and-research-architecture-for-5g-sa-devices/)

- **[5GBaseChecker Tool Release](https://github.com/SyNSec-den/5GBaseChecker)** — Penn State University, Black Hat 2024

  Open-source tool for detecting vulnerabilities in 5G baseband implementations. Used to find 12 critical bugs in Samsung, MediaTek, and Qualcomm chipsets affecting Google, OPPO, OnePlus, Motorola, and Samsung devices.

### Base Station Software and Tools (Updated)

- **[OpenBTS 2024 Reloaded](https://github.com/PentHertz/OpenBTS)** — Updated for modern UHD drivers and Ubuntu 22.04/24.04
- **[OpenAirInterface (OAI)](https://openairinterface.org/)** — Complete 3GPP Release-15+ implementation with active 5G development
- **[LimeNET CrowdCell](https://limemicro.com/)** — Network-in-a-box with integrated LimeSDR for small cell deployments
- **[Amarisoft LTEENB/gNB](https://www.amarisoft.com/)** — Professional-grade LTE/5G NR base station software
- **[DragonOS](https://sourceforge.net/projects/dragonos-focal/)** — Debian/Lubuntu-based SDR distro with cellular tools pre-installed; supports RTL-SDR, HackRF, LimeSDR, BladeRF; latest release is DragonOS Noble (24.04). [Website](https://cemaxecuter.com/)
- **[WarDragon](https://cemaxecuter.com/)** — Passive RF sensor platform with AI-enhanced cellular survey capabilities; integrates with TAK; includes Ransack for multi-RAT survey
- **[Magma Core Network](https://magmacore.org/)** — Meta's distributed packet core, now under the Linux Foundation
- **[5GBaseChecker](https://github.com/SyNSec-den/5GBaseChecker)** — Automated 5G baseband vulnerability detection tool
- **[Ransack](https://github.com/alphafox02/ransack)** — Multi-RAT cellular survey/recon platform; unifies LTE/5G NR/GSM/NB-IoT observations from SDRs, Qualcomm phones, and Rayhunter into SQLite with REST API
- **[5GHOUL](https://github.com/asset-group/5ghoul-5g-nr-attacks)** — 5G NR fuzzing and attack framework targeting Qualcomm/MediaTek

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
| **Open5GS** | Open-source 5G core and EPC implementation | [GitHub](https://github.com/open5gs/open5gs) |
| **Kamailio** | Open-source SIP server used in IMS/VoLTE labs | [Website](https://www.kamailio.org/) |

### Configuration Guides

- **[BladeRF and YateBTS Configuration](https://github.com/Nuand/bladeRF/wiki/Setting-up-Yate-and-YateBTS-with-the-bladeRF)**
- **[srsRAN Project Documentation](https://docs.srsran.com/projects/project)**
- **[srsRAN 4G Documentation](https://docs.srsran.com/projects/4g)**

### Analysis Tools

| Tool | Description | Link |
|------|-------------|------|
| **Ransack** | Multi-RAT cellular survey platform for DragonOS; merges LTE/5G NR/GSM/NB-IoT into unified DB; orchestrates srsRAN, LTESniffer, FALCON, Rayhunter | [GitHub](https://github.com/alphafox02/ransack) |
| **Rayhunter** | EFF's IMSI catcher detector for Orbic hotspots; detects 2G downgrades and suspicious requests | [GitHub](https://github.com/EFForg/rayhunter) |
| **5GBaseChecker** | Automated 5G baseband vulnerability detection (Penn State) | [GitHub](https://github.com/SyNSec-den/5GBaseChecker) |
| **5GHOUL** | 5G NR attacks against Qualcomm/MediaTek with stateful fuzzer | [GitHub](https://github.com/asset-group/5ghoul-5g-nr-attacks) |
| **FirmWire** | Full-system baseband firmware emulation for fuzzing/debugging | [GitHub](https://github.com/FirmWire/FirmWire) |
| **BaseBridge** | Bridges OTA and emulation testing for baseband firmware | [GitHub](https://github.com/FirmWire/BaseBridge) |
| **LTE-Cell-Scanner** | LTE cell detection and analysis | [GitHub](https://github.com/Evrytania/LTE-Cell-Scanner) |
| **gr-gsm** | GSM analysis with GNU Radio | [GitHub](https://github.com/ptrkrysik/gr-gsm/wiki/Passive-IMSI-Catcher) |
| **IMSI-Catcher Detector** | Android app for detecting IMSI catchers | [GitHub](https://github.com/CellularPrivacy/Android-IMSI-Catcher-Detector) |
| **CellGuard** | iOS app detecting rogue base stations via baseband analysis | [GitHub](https://github.com/seemoo-lab/CellGuard) |
| **QCSuper** | Capture 2G-4G traffic using Qualcomm phones | [P1 Security](https://labs.p1sec.com/2019/07/09/presenting-qcsuper-a-tool-for-capturing-your-2g-3g-4g-air-traffic-on-qualcomm-based-phones/) |
| **FALCON LTE** | Fast analysis of LTE control channels in real-time | [GitHub](https://github.com/falkenber9/falcon) |
| **Kalibrate** | GSM base station scanner and frequency calibration | [GitHub](https://github.com/scateu/kalibrate-hackrf) |
| **LTE Sniffer** | Open-source LTE downlink/uplink eavesdropper | [GitHub](https://github.com/SysSec-KAIST/LTESniffer) |
| **OsmocomBB** | Free firmware for mobile phone baseband processors | [Osmocom](https://osmocom.org/projects/osmocombb) |
| **Modmobmap** | Mobile network mapping | [GitHub](https://github.com/Synacktiv-contrib/Modmobmap) |
| **Modmobjam** | Mobile jamming research tool | [GitHub](https://github.com/Synacktiv-contrib/Modmobjam) |
| **CITesting** | Context integrity violation testing for LTE core networks | [ACM DL](https://dl.acm.org/doi/10.1145/3719027.3765230) |
| **SigPloit** | SS7/Diameter/GTP/SIP signaling security testing framework | [GitHub](https://github.com/SigPloiter/SigPloit) |
| **LTEFuzz** | LTE protocol fuzzer (KAIST) | [GitHub](https://github.com/koo7/LTEFuzz) |
| **LLFuzz** | LLM-guided baseband firmware fuzzing for MediaTek/Samsung Shannon | [Paper](https://arxiv.org/abs/2507.09660) |
| **Crocodile Hunter** | EFF tool for detecting rogue cell towers by wardriving | [GitHub](https://github.com/EFForg/crocodile-hunter) |
| **SCAT** | Signaling Collection and Analysis Tool for Qualcomm/Samsung | [GitHub](https://github.com/fgsect/scat) |
| **Hermes** | FSM synthesis from natural language specifications | [GitHub](https://github.com/SyNSec-den/hermes-spec-to-fsm) |
| **CellularLint** | Inconsistency detection in 4G/5G standards | [GitHub](https://github.com/CellularLint/cellularlint-codes) |
| **5GReasoner** | Property-directed formal verification of 5G control-plane protocols | [Paper](https://dl.acm.org/doi/10.1145/3319535.3354263) |
| **DoLTEst** | Downlink negative testing framework for LTE devices; 1,848 test cases | [Paper](https://www.usenix.org/conference/usenixsecurity22/presentation/park-cheoljun) |
| **ProChecker** | FSM extraction + model checking for 4G LTE implementations | [Paper](https://www.researchgate.net/publication/353412860) |
| **LTEInspector** | Property-driven adversarial model-based testing for 4G LTE | [Paper](https://syed-rafiul-hussain.github.io/index.php/teaching/cse543-f21/docs/lteinspector.pdf) |
| **BASECOMP** | Comparative analysis for baseband integrity protection | [GitHub](https://github.com/kaist-hacking/BaseComp) |
| **BaseTrace** | Framework for iPhone baseband interface research | [GitHub](https://github.com/seemoo-lab/BaseTrace) |
| **ss7map** | SS7 network exposure mapping | [P1 Security](https://ss7map.p1sec.com/) |
| **Osmocom Suite** | Complete open-source GSM/GPRS stack | [Osmocom](https://osmocom.org/projects) |

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

### Modern Baseband Fuzzing (2024-2026)

- **[SNI5GECT: Practical 5G Traffic Injection](https://thehackernews.com/2025/08/new-sni5gect-attack-crashes-phones-and.html)** — USENIX Security 2025

  Sniff and inject 5G messages without rogue base stations or jamming. Demonstrated 4G downgrade attacks within 20 meters of victim. [GitHub](https://github.com/asset-group/5ghoul-5g-nr-attacks)

- **["NASty" 5G Baseband Vulnerabilities through Dependency-Aware Fuzzing](https://www.youtube.com/watch?v=gXGIo5fy800)** — Black Hat USA 2025

  Targeting Non-Access Stratum (NAS) layer vulnerabilities using dependency-aware fuzzing. Discovered security bypass using "!!FAKE-TESTHARNESS!!" message. Symbolic execution challenges with Samsung Shannon basebands requiring TB-level memory.

- **[Budget-Friendly Baseband Fuzzing Setup](https://t2.fi/schedule/2024/)** — DefCon 32, Janne Taponen

  Covers building cost-effective baseband fuzzing rigs using SDRs, using LLMs to accelerate protocol parser development, and testing automotive ECUs, payment terminals, and mobile devices.

- **[RANsacked Fuzzing Framework](https://dl.acm.org/doi/10.1145/3658644.3670320)** — University of Florida / NC State, ACM CCS 2024

  Domain-informed fuzzing approach targeting RAN-Core interfaces. Discovered 119 vulnerabilities across ten network implementations.

- **[BaseBridge](https://github.com/FirmWire/BaseBridge)** — IEEE S&P 2025

  Framework that bridges over-the-air and emulation-based testing for cellular baseband firmware. Extends FirmWire.

- **[FirmWire](https://github.com/FirmWire/FirmWire)** — NDSS 2022

  Full-system baseband firmware emulation platform for Samsung and MediaTek. Discovered 8 remote memory corruptions including 3 pre-authentication RCE vulnerabilities.

### Vulnerability Research Tools

- **[5GBaseChecker](https://github.com/SyNSec-den/5GBaseChecker)** — Automated 5G baseband vulnerability detection
- **[5GHOUL](https://github.com/asset-group/5ghoul-5g-nr-attacks)** — Stateful 5G NR fuzzer with OTA attack capabilities
- **[LLFuzz](https://arxiv.org/abs/2507.09660)** — LLM-guided baseband fuzzing for MediaTek/Samsung Shannon (KAIST 2025)
- **[CITesting](https://dl.acm.org/doi/10.1145/3719027.3765230)** — Context integrity violation testing for LTE core networks
- **[Kairos](https://arxiv.org/abs/2605.30985)** — Timing-induced interaction failure testing
- **[ASTRA-5G](https://research.google/pubs/astra-5g-automated-over-the-air-security-testing-and-research-architecture-for-5g-sa-devices/)** — Automated OTA security testing for 5G SA devices
- **[certmitm](https://github.com/juurlink/certmitm)** — TLS implementation testing tool

---

## Attack Vectors

### Radio Jamming Attacks

From [NIST SP 800-187](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-187.pdf):

- **Smart Jamming** — Targeted channel interference timed to avoid detection
- **Dumb Jamming** — Broadband noise across frequency ranges
- **UE Interface Jamming** — Preventing UE signaling to eNodeB
- **eNodeB Interface Jamming** — Disrupting base station communications

### Overshadowing Attacks (2024-2026)

- **[5Gone: Uplink Overshadowing in 5G-SA](https://arxiv.org/abs/2602.10272)** — Feb 2026

  Uplink overshadowing attack transmitting at same time/frequency as victim with higher power. Enables surgical DoS, privacy leaks, and downgrade attacks. Runs on COTS x86 hardware.

- **[AdaptOver: Adaptive Overshadowing Attacks](https://arxiv.org/abs/2106.05039)** — 2022

  Adversary can decode, overshadow, and inject arbitrary messages OTA in either direction. Can cause persistent DoS (≥12h) or force IMSI transmission in plaintext. Demonstrated on live LTE/5G-NSA networks at 3.8km range.

### 5G Security Research

- **[SNI5GECT: Sniffing and Injecting 5G Traffic](https://arxiv.org/abs/2505.00000)** — USENIX Security 2025
- **[Breaking 5G on The Lower Layer](https://arxiv.org/abs/2602.10250)** — SIB1 spoofing and TA manipulation attacks
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
- **[Full Chain Baseband Exploits](https://labs.taszk.io/articles/post/full_chain_bb_part1/)** — taszk.io; zero-click RCE in baseband and Android runtime
- **[Unburdened By What Has Been: Exploiting L2 for Baseband RCE on Samsung Exynos](https://labs.taszk.io/articles/post/there_will_be_bugs/)** — taszk.io; CVE-2023-41111, CVE-2023-41112
- **[CITesting: Context Integrity Violations in LTE Core Networks](https://dl.acm.org/doi/10.1145/3719027.3765230)** — ACM CCS 2025 (Distinguished Paper)
- **[New Vulnerabilities in 4G and 5G Cellular Access Network Protocols](https://dl.acm.org/doi/10.1145/3317549.3319728)** — WiSec 2019

---

## Conference Talks

### Black Hat Asia 2026

- **[Qualcomm BootROM Vulnerability (CVE-2026-25262)](https://www.kaspersky.com/blog/qualcomm-cve-2026-25262/55811/)** — Kaspersky ICS CERT

  Hardware-level vulnerability in Qualcomm chipsets' Emergency Download Mode (EDL). Unpatchable BootROM flaw allows attackers with physical access to write arbitrary data to memory, potentially gaining full device control. Affects MDM9x07, MDM9x45, MDM9x65, MSM8909, MSM8916, MSM8952, SDX50 series.

### Black Hat USA 2025

- **[Uncovering 'NASty' 5G Baseband Vulnerabilities through Dependency-Aware Fuzzing](https://www.youtube.com/watch?v=gXGIo5fy800)**

  Non-Access Stratum (NAS) layer vulnerability research using dependency-aware fuzzing. Revealed security bypass via "!!FAKE-TESTHARNESS!!" message and challenges with Samsung Shannon baseband symbolic execution. [Slides](https://github.com/sixteen250/BlackHat_USA2025_Sessions)

- **[Uncovering Threats and Exposing Vulnerabilities in Next-Gen Cellular RAN](https://www.youtube.com/watch?v=rqzK1xd3wng)**

  Research on 5G Radio Access Networks transitioning to disaggregated, software-driven O-RAN architectures.

### DEF CON 33 (August 2025)

- **[Gateways to Chaos: How We Proved Modems Are a Ticking Time Bomb](https://www.youtube.com/watch?v=kItqWJHN_dI)** — Chiao-Lin "Steven Meow" Yu, Trend Micro

  Over 35 severe flaws in ISP-supplied modems (ADSL, fiber, cable, 4G/5G) rooted in outdated IoT SDKs. Affects power grids, water systems, ATMs globally.

- **[Hacking Hotspots: Pre-Auth RCE and Arbitrary SMS on 4G/5G Routers](https://infocondb.org/con/def-con/def-con-33/hacking-hotspots-pre-auth-remote-code-execution-arbitrary-sms-adjacent-attacks-on-5g-and-4glte-routers)**

  Reverse-engineering firmware of Tuoshi and KuWFi 4G/5G routers revealing pre-auth RCE and arbitrary SMS injection.

### Black Hat USA 2024

- **[5G Baseband Vulnerabilities — Penn State University](https://techcrunch.com/2024/08/07/hackers-could-spy-on-cellphone-users-by-abusing-5g-baseband-flaws-researchers-say/)**

  Researchers disclosed 12 vulnerabilities in 5G basebands from Samsung, MediaTek, and Qualcomm, affecting devices from Google, OPPO, OnePlus, Motorola, and Samsung. Released 5GBaseChecker tool.

### DEF CON 32 (August 2024)

- **[Economizing Mobile Network Warfare: Budget-Friendly Baseband Fuzzing](https://t2.fi/schedule/2024/)** — Janne Taponen

  Making baseband fuzzing accessible with affordable SDR hardware. Covers LLM-assisted protocol parser development and vulnerability discovery across automotive ECUs, payment terminals, and cellular modems.

- **[RF Attacks on Aviation's Defense Against Mid-Air Collisions](https://www.rtl-sdr.com/sdr-and-rf-videos-from-defcon-32/)**
- **[Breaking the Beam: Exploiting VSAT Modems from Earth](https://www.rtl-sdr.com/sdr-and-rf-videos-from-defcon-32/)**
- **[GPS Spoofing: It's About Time, Not Just Position](https://www.rtl-sdr.com/sdr-and-rf-videos-from-defcon-32/)**

### OffensiveCon 2025

- **[No Signal, No Security: Dynamic Baseband Vulnerability Research](https://securityboulevard.com/2025/06/offensivecon25-no-signal-no-security-dynamic-baseband-vulnerability-research/)** — Daniel Klischies, David Hirsch

  Dynamic approaches to baseband vulnerability research.

- **[Mobile Network Attacks: Exploiting Smartphones Through Baseband](https://www.offensivecon.org/trainings/2025/exploiting-smartphones-through-baseband.html)** — Training

  Hands-on training covering cellular network fundamentals (2G-5G), baseband OS internals, and vulnerability exploitation techniques.

### ACM CCS 2025

- **[CITesting: Systematic Testing of Context Integrity Violations in LTE Core Networks](https://dl.acm.org/doi/10.1145/3719027.3765230)** — KAIST (Distinguished Paper)

  New class of uplink attacks against LTE core networks that work through legitimate base stations — no rogue BTS required. All four tested implementations were vulnerable, including commercial systems from Nokia and Amarisoft.

- **[Uncovering Hidden Paths in 5G: Exploiting Protocol Tunneling and Network Boundary Bridging](https://dl.acm.org/doi/10.1145/3719027.3765206)**

  Demonstrates how attackers can use protocol tunneling to traverse network boundaries and reach isolated 5G components.

### IEEE S&P 2025

- **[BaseBridge: Bridging Over-the-Air and Emulation Testing for Cellular Baseband Firmware](https://github.com/FirmWire/BaseBridge)**

  Framework for cellular baseband firmware security testing combining emulation and OTA approaches.

- **[From Control to Chaos: A Comprehensive Formal Analysis of 5G's Access Control](https://sp2025.ieee-security.org/accepted-papers.html)** — Penn State

### USENIX Security 2025

- **[SNI5GECT: A Practical Approach to Inject aNRchy into 5G NR](https://thehackernews.com/2025/08/new-sni5gect-attack-crashes-phones-and.html)** — Singapore University of Technology and Design

- **[GLaDoS: Location-aware Denial-of-Service of Cellular Networks](https://dl.acm.org/doi/10.5555/3766078.3766351)**

### USENIX Security 2024

- **[Hermes: Unlocking Security Analysis of Cellular Network Protocols](https://www.usenix.org/conference/usenixsecurity24/presentation/al-ishtiaq)**

  Automatic FSM generation from natural language specifications. Uncovered 3 new vulnerabilities and identified 19 previous attacks.

- **[CellularLint: Identifying Inconsistent Behavior in Cellular Network Specifications](https://www.usenix.org/conference/usenixsecurity24/presentation/rahman)**

  LLM-based inconsistency detection in 4G/5G standards.

- **[Logic Gone Astray: Security Analysis of 5G Basebands](https://www.usenix.org/conference/usenixsecurity24/)**

  Control plane protocol analysis framework.

### USENIX Security 2023

- **[BASECOMP: A Comparative Analysis for Integrity Protection in Cellular Baseband Software](https://www.usenix.org/conference/usenixsecurity23/presentation/kim-eunsoo)**

  Semi-automated integrity protection analysis using probabilistic inference. Discovered 29 bugs including critical NAS AKA bypass in Samsung. [GitHub](https://github.com/kaist-hacking/BaseComp)

### Previous Years

- **[Black Hat USA 2022: Attacks from a New Front Door in 4G and 5G Networks](https://i.blackhat.com/USA-22/Wednesday/US-22-Shaik-Attacks-From-a-New-Front-Door-in-4G-5G-Mobile-Networks.pdf)**
- **[Black Hat USA 2021: Over The Air Baseband Exploit — 5G RCE](https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Over-The-Air-Baseband-Exploit-Gaining-Remote-Code-Execution-On-5G-Smartphones.pdf)** — [White Paper](https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Over-The-Air-Baseband-Exploit-Gaining-Remote-Code-Execution-On-5G-Smartphones-wp.pdf)
- **[Black Hat USA 2020: Detecting Fake 4G Base Stations in Real Time](https://i.blackhat.com/USA-20/Wednesday/us-20-Quintin-Detecting-Fake-4G-Base-Stations-In-Real-Time.pdf)**
- **[NSA PLAYSET GSM](https://www.defcon.org/images/defcon-22/dc-22-presentations/Pierce-Loki/DEFCON-22-Pierce-Loki-NSA-PLAYSET-GSM.pdf)** — DEF CON 22
- **[VoLTE Phreaking](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/papers/talks/HAXPO-VoLTE-Phreaking-Ralph-Moonen.pdf)** — Ralph Moonen
- **[RF Exploitation: IoT/OT Hacking with SDR](https://conference.hitb.org/hitbsecconf2019ams/materials/HAXPO%20D2%20-%20Demystifying%20IoT:OT%20Hacks%20With%20SDR%20-%20Himanshu%20Mehta%20&%20Harshit%20Agrawal.pdf)** — HITB 2019
- **[Bye-Bye IMSI Catchers: Security Enhancements in 5G](https://conference.hitb.org/hitbsecconf2018pek/materials/D2T2%20-%20Bye%20Bye%20IMSI%20Catchers%20-%20Security%20Enhancements%20in%205g%20-%20Lin%20Huang.pdf)** — HITB 2018
- **[Side Channel Attacks in 4G and 5G](https://i.blackhat.com/eu-19/Thursday/eu-19-Hussain-Side-Channel-Attacks-In-4G-And-5G-Cellular-Networks.pdf)** — Black Hat Europe 2019
- **[Dirty Use of USSD Codes in Cellular Networks](https://troopers.de/wp-content/uploads/2012/12/TROOPERS13-Dirty_use_of_USSD_codes_in_cellular-Ravi_Borgaonkor.pdf)** — TROOPERS 2013, Ravi Borgaonkar
- **[Hacking LTE Public Warning Systems](https://conference.hitb.org/hitbsecconf2019ams/materials/HAXPO%20D1%20-%20Hacking%20LTE%20Public%20Warning%20Systems%20-%20Weiguang%20Li.pdf)** — HITB 2019

---

## Research Papers

### 2026

- **[5Gone: Uplink Overshadowing Attacks in 5G-SA](https://arxiv.org/abs/2602.10272)** — ETH Zurich, Feb 2026

  SDR-based uplink overshadowing exploiting 3GPP standard deficiencies. E2E latency under 500μs on COTS hardware.

- **[Breaking 5G on The Lower Layer](https://arxiv.org/abs/2602.10250)** — 2026

  SIB1 spoofing and Timing Advance manipulation attacks during random access.

- **[Kairos: Timing-Induced Interaction Failures in LTE and 5G Core Networks](https://arxiv.org/abs/2605.30985)** — 2026

  Discovered 20 new vulnerabilities and reproduced 34 issues across open-source and commercial cores.

- **[Devilray: Adversarial Model Revealing Blind Spots in Fake Base Station Detection](https://arxiv.org/abs/2605.19232)** — May 2026

  Systematic adversarial baseline evaluating 7 FBS detectors across 2,592 configurations.

- **[Security Overview and Analysis of 3GPP 5G MAC CE](https://arxiv.org/abs/2506.09502)** — June 2026

  Analysis of 5G NR Medium Access Control protocol specification (3GPP V18.5.0).

- **[Semantics Over Syntax: Uncovering Pre-Authentication 5G Baseband Vulnerabilities](https://arxiv.org/abs/2604.04283)** — April 2026

  Automated approach to finding pre-auth vulnerabilities in 5G basebands using semantic analysis.

### 2025

- **[CITesting: Systematic Testing of Context Integrity Violations in LTE Core Networks](https://dl.acm.org/doi/10.1145/3719027.3765230)** — ACM CCS 2025 (Distinguished Paper Award)

  KAIST's CITesting tool runs thousands of test cases against LTE core implementations, dwarfing the 31-case coverage of prior tooling (LTEFuzz). All four tested implementations contained CIV vulnerabilities.

- **[Uncovering Hidden Paths in 5G: Protocol Tunneling and Network Boundary Bridging](https://dl.acm.org/doi/10.1145/3719027.3765206)** — ACM CCS 2025

- **[5G Network Slicing: Security Challenges, Attack Vectors, and Mitigation Approaches](https://pmc.ncbi.nlm.nih.gov/articles/PMC12251764/)** — MDPI, July 2025

- **[Starshields for iOS: Navigating the Security Cosmos in Satellite Communication](https://www.ndss-symposium.org/wp-content/uploads/2025-124-paper.pdf)** — NDSS 2025

  First comprehensive security analysis of Apple's satellite communication features. Researchers reverse-engineered the proprietary protocol, demonstrated restriction bypasses, and built a simulation testbed covering Emergency SOS, Find My, roadside assistance, and iMessage over satellite.

- **[RANsacked: A Domain-Informed Approach for Fuzzing LTE and 5G RAN-Core Interfaces](https://thehackernews.com/2025/01/ransacked-over-100-security-flaws-found.html)** — University of Florida / NC State, Jan 2025

  119 vulnerabilities, 97 CVEs, across ten implementations. Any one enables city-wide disruption.

- **[SNI5GECT: A Practical Approach to Inject aNRchy into 5G NR](https://www.kaspersky.com/blog/5g-attack-downgrade-sni5gect/54258/)** — USENIX Security 2025

- **[GLaDoS: Location-aware Denial-of-Service of Cellular Networks](https://dl.acm.org/doi/10.5555/3766078.3766351)** — USENIX Security 2025

- **[LLFuzz: LLM-Guided Baseband Firmware Fuzzing](https://arxiv.org/abs/2507.09660)** — KAIST, July 2025

  LLM-guided fuzzing framework targeting MediaTek and Samsung Shannon basebands. Discovered 11 memory corruption vulnerabilities in NAS/RRC message handlers. Uses LLM to generate semantically valid protocol messages for improved coverage.

- **[BaseBridge: Bridging Over-the-Air and Emulation Testing for Cellular Baseband Firmware](https://github.com/FirmWire/BaseBridge)** — IEEE S&P 2025

- **[From Control to Chaos: Formal Analysis of 5G Access Control](https://sp2025.ieee-security.org/accepted-papers.html)** — IEEE S&P 2025

### 2024

- **[Hermes: Unlocking Security Analysis of Cellular Network Protocols](https://www.usenix.org/conference/usenixsecurity24/presentation/al-ishtiaq)** — USENIX Security 2024

  Automatic FSM synthesis from natural language. 81-87% accuracy, 3 new vulnerabilities, 19 previous attacks identified.

- **[CellularLint: Identifying Inconsistent Behavior in Cellular Specifications](https://www.usenix.org/conference/usenixsecurity24/presentation/rahman)** — USENIX Security 2024

- **[Logic Gone Astray: Security Analysis of 5G Basebands](https://www.usenix.org/conference/usenixsecurity24/)** — USENIX Security 2024

- **[ASTRA-5G: Automated Over-the-Air Security Testing for 5G SA Devices](https://dl.acm.org/doi/abs/10.1145/3643833.3656141)** — WiSec 2024

- **[Catch You Cause I Can: Busting Rogue Base Stations using CellGuard](https://dl.acm.org/doi/10.1145/3678890.3678898)** — RAID 2024

- **[Survey on 5G Physical Layer Security Threats and Countermeasures](https://www.mdpi.com/1424-8220/24/17/5523)** — MDPI Sensors 2024

  Comprehensive review of PHY-layer attack surface covering eavesdropping, jamming, spoofing, pilot contamination, and SDR-based research frameworks.

- **[The Impact of IMSI Catcher Deployments on Cellular Network Security](https://arxiv.org/abs/2405.00793)** — 2024

### 2023

- **[BASECOMP: A Comparative Analysis for Integrity Protection in Cellular Baseband Software](https://www.usenix.org/conference/usenixsecurity23/presentation/kim-eunsoo)** — USENIX Security 2023

  Semi-automated integrity protection analysis. Discovered 29 bugs including critical NAS AKA bypass in Samsung.

- **[European 5G Security in the Wild](https://arxiv.org/pdf/2305.08635.pdf)** — 2023

### 2019-2022

- **[FirmWire: Transparent Dynamic Analysis for Cellular Baseband Firmware](https://cise.ufl.edu/~butler/pubs/ndss22-firmwire.pdf)** — NDSS 2022
- **[Privacy Attacks on 4G/5G Paging Protocols](https://assets.documentcloud.org/documents/5749002/4G-5G-paper-at-NDSS-2019.pdf)** — NDSS 2019
- **[New Vulnerabilities in 4G and 5G Cellular Access Network Protocols](https://dl.acm.org/doi/10.1145/3317549.3319728)** — WiSec 2019

  Three new attack classes exploiting unprotected device capability information: identification, bidding-down, and battery drain.

- **[New Privacy Threat on 3G, 4G, and Upcoming 5G AKA Protocols](https://arxiv.org/pdf/1905.07617.pdf)**
- **[BaseSAFE: Baseband SAnitized Fuzzing through Emulation](https://arxiv.org/pdf/2005.07797.pdf)**
- **[AdaptOver: Adaptive Overshadowing Attacks in Cellular Networks](https://arxiv.org/abs/2106.05039)** — 2022

  OTA message injection at 3.8km range. Demonstrated on live LTE/5G-NSA networks.

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

- **[Rayhunter](https://github.com/EFForg/rayhunter)** — EFF, 2025

  Open-source IMSI catcher detector that runs on affordable Orbic mobile hotspots (~$20-30). Analyzes control traffic in real-time looking for 2G downgrade attempts and unusual IMSI requests. Thousands deployed worldwide with community-contributed packet captures. [Documentation](https://efforg.github.io/rayhunter/) — [Blog Post](https://www.eff.org/deeplinks/2025/03/meet-rayhunter-new-open-source-tool-eff-detect-cellular-spying)

- **[CellGuard](https://github.com/seemoo-lab/CellGuard)** — SEEMOO Lab, 2024

  iOS app that detects rogue base stations by analyzing baseband packets in real-time. Integrates with the Apple Cell Location Database for anomaly detection. [Website](https://cellguard.seemoo.tu-darmstadt.de/) — [Research Paper](https://dl.acm.org/doi/10.1145/3678890.3678898)

- **[BaseTrace](https://github.com/seemoo-lab/BaseTrace)** — SEEMOO Lab

  Framework for researching the interface between iPhone's application processor and baseband.

### IMSI Catcher Detection and Research

- **[SeaGlass: City-Wide IMSI-Catcher Detection](https://seaglass.cs.washington.edu/)** — UW
- **[SeaGlass Research Paper](https://seaglass-web.s3.amazonaws.com/SeaGlass___PETS_2017.pdf)** — PETS 2017
- **[Evaluating IMSI Catcher Detectors](http://www.cs.ox.ac.uk/files/9192/paper-final-woot-imsi.pdf)** — Oxford
- **[IMSI-Catcher Detector (Android)](https://github.com/CellularPrivacy/Android-IMSI-Catcher-Detector)**
- **[Devilray: Adversarial FBS Detection Analysis](https://arxiv.org/abs/2605.19232)** — May 2026

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

- **[O-RAN Alliance Security Update 2025](https://www.o-ran.org/blog/o-ran-alliance-security-update-2025)** — WG11 security assurance program and AI/ML threat analysis
- **[O-RAN Security Risks and Vulnerabilities](https://www.sciencedirect.com/science/article/pii/S1389128626004925)** — 60% of risks are DoS/performance degradation; xApp compromise threats
- **[Open RAN: Attack of the xApps](https://www.trendmicro.com/vinfo/us/security/news/vulnerabilities-and-exploits/open-ran-attack-of-the-xapps)** — Trend Micro analysis of Near-RT RIC vulnerabilities
- **[End-to-End O-RAN Security Architecture](https://arxiv.org/abs/2304.05513)** — Threat surface analysis including Open Fronthaul
- **[Private 5G Penetration Testing Guide](https://www.nist.gov/cybersecurity)** — Enterprise private network testing
- **[Campus 5G Security Assessment](https://csrc.nist.gov/)** — NIST private 5G security guidance
- **[Security Implications of 5G Communication in Industrial Systems](https://arxiv.org/abs/2604.11509)** — 2024

---

## Network Slicing and Edge Security

- **[5G Network Slicing Attack Research](https://pmc.ncbi.nlm.nih.gov/articles/PMC12251764/)** — MDPI, July 2025
- **[Multi-Access Edge Computing (MEC) Vulnerabilities](https://www.etsi.org/technologies/multi-access-edge-computing)** — ETSI MEC security specs
- **[Network Function Virtualization (NFV) Attacks](https://www.etsi.org/technologies/nfv)** — Virtual network function security

---

## Automotive and Industrial Cellular

- **[Security Analysis of LTE Connectivity in Connected Cars: Tesla Case Study](https://arxiv.org/abs/2510.22024)** — 2025
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
- **[Samsung Semiconductor Security Updates](https://semiconductor.samsung.com/support/quality-support/product-security-updates/)** — Shannon baseband CVEs
- **[Apple Security Research](https://security.apple.com/)** — iOS/baseband security program

---

## SIM Security

### SIM Swap Attack Prevention and Detection

- **[iVerify SIM Swap Detection](https://www.iverify.io/)** — Mobile security platform with SIM swap attack detection capabilities
- **[ML-Based SIM Swap Detection Research](https://arxiv.org/search/?query=SIM+swap+detection)** — Machine learning approaches to detecting SIM swap fraud patterns
- **[T-Mobile SIM Protection](https://www.t-mobile.com/support/account/account-security)** — Carrier SIM protection features (Account Takeover Protection)
- **[CTIA SIM Swap Best Practices](https://www.ctia.org/)** — Industry guidelines for SIM swap fraud prevention

### SIM Vulnerability Research

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

### 2026 Notable CVEs

- **[CVE-2026-25262](https://www.kaspersky.com/blog/qualcomm-cve-2026-25262/55811/)** — Qualcomm BootROM (Sahara protocol) unpatchable vulnerability; affects MDM9x07, MDM9x45, MDM9x65, MSM8909, MSM8916, MSM8952, SDX50 series
- **[CVE-2026-21385](https://socprime.com/blog/cve-2026-21386-vulnerability/)** — Qualcomm Graphics memory corruption; exploited in targeted attacks on Android
- **[MediaTek March 2026 Bulletin](https://corp.mediatek.com/product-security-bulletin/March-2026)** — CVE-2026-20423 through CVE-2026-20445 affecting MT7902, MT7920, MT7921, MT7922, MT7925, MT7927

### 2024-2025 Notable CVEs

- **[CVE-2023-24033 (Google Project Zero)](https://googleprojectzero.blogspot.com/2023/03/multiple-internet-to-baseband-remote.html)** — Samsung Exynos baseband: internet-to-baseband RCE via malformed SDP in VoLTE/VoWiFi; no user interaction required. Part of 18 zero-day disclosure affecting Pixel 6/7, Galaxy S22, Vivo, and Samsung wearables
- **[CVE-2024-55568](https://nvd.nist.gov/vuln/detail/CVE-2024-55568)** — Samsung Exynos baseband heap buffer overflow in SDP parsing; remote code execution via crafted VoLTE packets
- **[CVE-2024-25073](https://semiconductor.samsung.com/support/quality-support/product-security-updates/cve-2024-25073/)** — Samsung Shannon baseband: pointer not properly checked in Call Control module, leads to DoS
- **[CVE-2025-58349](https://semiconductor.samsung.com/support/quality-support/product-security-updates/cve-2025-58349/)** — Samsung: incorrect handling of LTE MAC packets with many MAC Control Elements causes baseband crash
- **[Open5GS CVEs (2024-2025)](https://www.cvedetails.com/vulnerability-list/vendor_id-22759/year-2025/Open5gs.html)** — Multiple DoS vulnerabilities including NULL pointer dereferences and assertion failures
- **[RANsacked: 97 CVEs](https://thehackernews.com/2025/01/ransacked-over-100-security-flaws-found.html)** — Affecting Open5GS, Magma, OAI, Athonet, SD-Core, NextEPC, srsRAN

### CVE Resources

- **[NVD CVE Search](https://nvd.nist.gov/vuln/search)** — Search for cellular-related CVEs
- **[Google Project Zero](https://googleprojectzero.blogspot.com/)** — Ongoing mobile security research
- **[Samsung Security Bulletins](https://security.samsungmobile.com/securityUpdate.smc)** — Regular baseband updates
- **[SIMjacker Research](https://simjacker.com/)** — SIM-based attack evolution
- **[Free5GC CVEs](https://app.opencve.io/cve/?vendor=free5gc)** — OpenCVE tracking

---

## International Research

- **[ENISA 5G Reports](https://www.enisa.europa.eu/)** — EU 5G security assessments
- **[KAIST SysSec Lab](https://syssec.kaist.ac.kr/)** — Leading cellular security research group (CITesting, LTEFuzz, LTESniffer, BASECOMP)
- **[Penn State SyNSec Lab](https://syed-rafiul-hussain.github.io/)** — Syed Rafiul Hussain's group (5GBaseChecker, Hermes, CellularLint)
- **[Japanese 5G Security Guidelines](https://www.nisc.go.jp/eng/)** — Japan national cybersecurity strategy
- **[ASSET Research Group (Singapore)](https://asset-group.github.io/)** — 5GHOUL, SNI5GECT research

---

## Training and Education

### Professional Training

- **[OffensiveCon: Mobile Network Attacks Training](https://www.offensivecon.org/trainings/2025/exploiting-smartphones-through-baseband.html)** — Hands-on baseband exploitation (2G-5G)
- **[SANS Mobile Security](https://www.sans.org/)** — Professional mobile security courses
- **[Offensive Security Mobile Testing](https://www.offensive-security.com/)** — Advanced mobile penetration testing
- **[PentHertz Training](https://penthertz.com/)** — RF and wireless security training

### Lab Environments

- **[Open5GS + srsRAN Lab Setup](https://github.com/s5uishida/open5gs_5gc_srsran_sample_config)** — Complete 5G SA config with ZeroMQ UE/RAN
- **[End-to-End Open5GS-srsRAN Guide](https://github.com/ngkore/Open5GS-srsRAN)** — Deployment guide for Ubuntu 22.04
- **[5G SA Lab Setup Tutorial](https://himanshup.hashnode.dev/5g-sa-lab-setup-using-srsran-open5gs)** — Step-by-step srsRAN + Open5GS guide
- **[OpenAirInterface Lab Setup](https://github.com/OpenAirInterface/openairinterface5g)** — Open-source 5G lab environment
- **[DragonOS](https://sourceforge.net/projects/dragonos-focal/)** — Pre-configured SDR Linux distribution; latest is Noble (24.04)
- **[5G Security Datasets](https://github.com/DLTeamTUC/5GDatasets)** — PCAP, CSV, and AMF logs for flooding/fuzzing/replay attacks on Open5GS, OAI, Amarisoft
- **[GNU Radio / SDR University Courses](https://www.gnuradio.org/)** — SDR educational materials
- **[VET5G: Virtual Testbed for 5G Security](https://arxiv.org/abs/2507.20873)** — OpenAirInterface + Android emulator testbed

---

## Vendor-Specific Research

- **[Ericsson Security Research](https://www.ericsson.com/en/security)**
- **[Nokia Bell Labs Security](https://www.bell-labs.com/)**
- **[Qualcomm Security Bulletins](https://www.qualcomm.com/company/product-security/bulletins)**
- **[MediaTek Product Security](https://www.mediatek.com/)**
- **[Samsung Shannon Baseband Research](https://semiconductor.samsung.com/support/quality-support/product-security-updates/)**
- **[Google Project Zero: 18 Exynos Zero-Days (2023)](https://googleprojectzero.blogspot.com/2023/03/multiple-internet-to-baseband-remote.html)** — CVE-2023-24033 and 17 others; 4 RCE without user interaction via VoLTE/VoWiFi
- **[Google Project Zero: Exynos Baseband CVE-2024-55568](https://googleprojectzero.blogspot.com/)** — Heap buffer overflow in Samsung Exynos baseband allowing remote code execution

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

### GitHub Collections

- **[Cellular-Security-Papers](https://github.com/onehouwong/Cellular-Security-Papers)** — Comprehensive collection of academic papers, tools, and talks
- **[Awesome-Cellular-Hacking](https://github.com/W00t3k/Awesome-Cellular-Hacking)** — This repository
- **[Firmware-Analysis-Papers](https://github.com/onehouwong/Firmware-Analysis-Papers)** — Baseband and firmware security papers
- **[5GSEC](https://github.com/5GSEC)** — 5G security research organization

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

### Video Tutorials

- **[DragonOS FocalX Cellular Security Research w/ LTESniffer (Part 1)](https://www.youtube.com/watch?v=5AVPC0KcbMY)** — srsRAN, LimeSDR, B205mini setup
- **[DragonOS FocalX Cellular Security Research + IMSI Capture w/ LTESniffer (Part 3)](https://www.youtube.com/watch?v=Lu4Vt_RE0MA)** — X310, srsRAN advanced config
- **[RTL-SDR SDR and RF Videos from DEF CON 32](https://www.rtl-sdr.com/sdr-and-rf-videos-from-defcon-32/)** — Collection of RF/cellular talks

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

### Notable Researchers and Organizations to Follow

| Name/Organization | Focus Area | Link |
|-------------------|------------|------|
| **Syed Rafiul Hussain** | 5G/LTE protocol security, baseband fuzzing | [Website](https://syed-rafiul-hussain.github.io/) |
| **Imtiaz Karim** | 5GReasoner, LTE noncompliance, cellular formal verification | [Website](https://www.imtiazkarim.net/) |
| **KAIST SysSec Lab** | LTE/5G core network security | [Website](https://syssec.kaist.ac.kr/) |
| **SEEMOO Lab (TU Darmstadt)** | iOS baseband, IMSI catcher detection | [GitHub](https://github.com/seemoo-lab) |
| **ASSET Research Group** | 5G NR fuzzing (5GHOUL, SNI5GECT) | [Website](https://asset-group.github.io/) |
| **cemaxecuter** | DragonOS, WarDragon, Ransack cellular survey tools | [Twitter](https://twitter.com/cemaxecuter) / [Website](https://cemaxecuter.com/) |
| **taszk.io** | Samsung/MediaTek baseband exploits, full-chain RCE | [Website](https://labs.taszk.io/articles/tags/baseband/) |
| **Google Project Zero** | Baseband vulnerability research, Exynos zero-days | [Blog](https://googleprojectzero.blogspot.com/) |
| **PentHertz** | RF/wireless security pentesting | [Twitter](https://twitter.com/PentHertz) |
| **P1 Security** | SS7/Diameter security | [Website](https://www.p1sec.com/) |
| **EFF** | Surveillance tech, Rayhunter, Crocodile Hunter | [Website](https://www.eff.org/) |

### Conferences and Competitions

- **[DEF CON](https://defcon.org/)** — RF Village, Wireless Village, and main track cellular talks
- **[Black Hat USA/Europe](https://www.blackhat.com/)** — Regular cellular/baseband research presentations
- **[OffensiveCon](https://www.offensivecon.org/)** — Baseband exploitation talks and training
- **[Pwn2Own Ireland](https://www.zerodayinitiative.com/Pwn2OwnIreland2025Rules.html)** — Mobile-focused; $100K for baseband RCE exploits
- **[CanSecWest](https://www.secwest.net/)** — Baseband and mobile security research presentations
- **[WiSec](https://wisec.acm.org/)** — ACM Conference on Security and Privacy in Wireless and Mobile Networks
- **[IEEE S&P / CCS / USENIX Security](https://www.ieee-security.org/TC/SP/)** — Top-tier academic venue for cellular security papers
- **[HITB](https://conference.hitb.org/)** — Regular telecom security talks
- **[NDSS](https://www.ndss-symposium.org/)** — Network security including FutureG workshop on 5G/6G

---

## Contributing

Fork the repo, add resources with descriptions, verify links are active, and submit a pull request with context on what was added.

## Legal Notice

This repository is for educational and research purposes only. Users are responsible for complying with all applicable laws and regulations. The maintainers do not endorse or encourage illegal activities.

---

**Last Updated:** August 2026
**Maintainer:** [@W00t3k](https://github.com/W00t3k)

*Broken links or new resources? Open an issue or submit a PR.*


---

## Verified Cellular Security Research Additions (September-November 2026)

> Append-only research update, November 3, 2026. The original resources above have been retained without modification. Entries below link to original research, published papers, vendor bulletins, or registered vulnerability disclosures. A published CVE or laboratory proof of concept does not by itself establish exploitation in the wild.

### SMS, Messaging, and Mobile Network Availability

- **[SMS of Death: Zero-Click Android Telephony DoS (CVE-2026-58882)](https://smsofdeath.com/)** — Mark B, Oct 29, 2026

  Malformed WAP Push SMS messages trigger an exception in Android's telephony framework, crashing `com.android.phone` without user interaction and disrupting active calls, including emergency calls. Repeated processing can cause persistent service disruption or reboot loops on affected devices. [Google Security Bulletin](https://source.android.com/docs/security/bulletin/2026/2026-11-01) — Critical DoS; security patch level 2026-11-01.

- **[Android November 2026 Security Bulletin: Telephony and Modem Fixes](https://source.android.com/docs/security/bulletin/2026/2026-11-01)** — Google, Nov 2, 2026

  Official Android bulletin listing CVE-2026-58882 as a Critical System denial-of-service issue. Also includes critical MediaTek modem fixes and other platform vulnerabilities. Android and chipset patches may arrive on different schedules depending on device manufacturer and carrier.

- **[Securing Cellular Network Availability Against Wireless Blackhole Attack](https://www.sciencedirect.com/science/article/pii/S0140366426001994)** — Computers Communications, 2026

  Research on fake base stations manipulating broadcast control signaling to draw multiple subscribers away from legitimate 4G/5G service. Discusses the Wireless Blackhole threat and availability-focused countermeasures.

### LTE/5G Core Networks, PFCP, GTP-C, and Service-Based Interfaces

- **[iFinder: Understanding Implicit Trust Errors in Core Carrier Networks](https://linziyuu.github.io/iFinder-Website/)** — Nanyang Technological University, USENIX Security 2026

  Multi-agent framework that identified 84 previously unknown vulnerabilities across seven LTE/5G core implementations, including Open5GS, free5GC, OpenAirInterface, SD-Core, and eUPF. Researchers report 83 confirmed findings and 81 assigned CVEs, with denial-of-service and subscriber session-hijacking impacts. [Research Paper](https://arxiv.org/abs/2607.10315)

- **[CVE-2026-106805: free5GC PFCP Session Establishment Resource Exhaustion](https://github.com/free5gc/free5gc/issues/1162)** — Nov 2, 2026

  Free5GC v4.2.3 can fail to release allocated UE IP addresses when PFCP Session Establishment responses do not arrive. Repeated failures can exhaust the address pool and block new PDU sessions. [CVE Record](https://nvd.nist.gov/vuln/detail/CVE-2026-106805)

- **[CVE-2026-106806: Open5GS HTTP/2 SBI Memory Exhaustion](https://github.com/open5gs/open5gs/issues/4788)** — Nov 2, 2026

  Duplicate HTTP/2 header processing can leak allocated strings in Open5GS v2.8.0. Repeated malformed requests to a reachable Service-Based Interface (SBI) can exhaust network-function memory and cause denial of service. [CVE Record](https://nvd.nist.gov/vuln/detail/CVE-2026-106806)

- **[CVE-2026-106807: Open5GS PFCP Transaction Exhaustion](https://github.com/open5gs/open5gs/issues/4791)** — Nov 2, 2026

  Resource exhaustion in Open5GS v2.8.0 PFCP transaction handling can trigger an unhandled assertion and terminate an SMF/UPF process. Exploitation requires the ability to send traffic to the affected PFCP interface. [CVE Record](https://nvd.nist.gov/vuln/detail/CVE-2026-106807)

- **[CVE-2026-106808: OpenAirInterface UDM Authentication Endpoint Stack Overflow](https://github.com/openairinterface/oai-cn5g-udm/issues/4)** — Nov 2, 2026

  OpenAirInterface CN5G v2.2.1 UDM does not adequately bound resynchronization data converted into fixed-size buffers. Crafted input from a party able to reach the SBI endpoint and supply a valid SUPI can crash the UDM. [CVE Record](https://nvd.nist.gov/vuln/detail/CVE-2026-106808)

- **[CVE-2026-117068: OpenAirInterface AMF NAS Registration Crash](https://github.com/openairinterface/oai-cn5g-amf/pull/26)** — Nov 2, 2026

  A truncated SUCI in a NAS Registration Request can trigger integer underflow and an out-of-bounds read in the CN5G AMF v2.2.1 decoder, terminating the AMF process. [CVE Record](https://nvd.nist.gov/vuln/detail/CVE-2026-117068)

- **[CVE-2026-25501: free5GC SMF PFCP Session Report Crash](https://github.com/free5gc/free5gc/security/advisories/GHSA-vq85-8f6p-g9q5)** — Feb 2026

  A malformed PFCP SessionReportRequest with a Downlink Data Report flag but no corresponding information element triggers a nil-pointer dereference in free5GC SMF versions through 1.4.1. Restrict PFCP (UDP/8805) access to trusted network functions.

- **[CVE-2026-26024: free5GC PFCP Usage Report Handling Crash](https://nvd.nist.gov/vuln/detail/CVE-2026-26024)** — Feb 2026

  A malformed PFCP SessionReportRequest containing a Usage Report with a missing required URRID element can terminate the free5GC SMF in versions through 1.4.1. This is an interface-reachability-dependent denial-of-service issue.

- **[CVE-2026-26025: free5GC PFCP Session Report Parsing DoS](https://nvd.nist.gov/vuln/detail/CVE-2026-26025)** — Feb 2026

  Additional malformed PFCP SessionReportRequest handling issue affecting free5GC SMF versions through 1.4.1. A network actor able to send packets to the SMF's PFCP interface can cause process termination.

- **[Integrity Under Siege: A Rogue gNodeB's Manipulation of 5G Network Slice Allocation](https://www.sciencedirect.com/science/article/pii/S1389128626004974)** — Computer Networks, Sep 2026

  Experimental analysis of compromised network-slice allocation integrity using a rogue gNodeB. The paper reports quality-of-service degradation, fallback effects, resource contamination, and user-plane resource pressure.

### SIM Security and Cellular Baseband Research

- **[CATana: On the Dangers of SIM-Originating AT Commands](https://www.usenix.org/conference/woot26/presentation/lisowski)** — University of Birmingham / Fuzzware, USENIX WOOT 2026

  Analyzes the SIM Toolkit RUN AT interface using the CATana toolkit. Nine of 26 tested smartphones and IoT devices exposed SIM-originating AT commands; researchers identified four vulnerabilities with impacts including command execution, file reading, 2G downgrade, and device denial of service.

- **[SoK: Insecurity of Cellular Basebands](https://www.usenix.org/conference/woot26/presentation/carnot)** — EURECOM / Avantix, USENIX WOOT 2026

  Systematization of cellular baseband attack surfaces and weaknesses, comparing static analysis, over-the-air testing, emulation, and fuzzing. Highlights current gaps in vulnerability discovery and baseband hardening.

- **[CONSET: Confirmed 5G Pre-Authentication Baseband CVEs](https://cse.buffalo.edu/~hongxinh/news.html)** — University at Buffalo / Texas A&M, 2026

  Follow-up disclosure details for the CONSET work already listed above: MediaTek CVE-2025-20666, CVE-2025-20644, and CVE-2025-20703 were assigned after researchers found semantic RRC parsing vulnerabilities. The USENIX Security 2026 paper reports seven previously unknown vulnerabilities affecting 64 chipset models and more than 542 phone models. [Conference Paper](https://www.usenix.org/conference/usenixsecurity26/presentation/huang-qiqing)

### 2026 Chipset and Modem Security Advisories

- **[MediaTek November 2026 Security Bulletin](https://www.mediatek.com/product-security-bulletin/November-2026)** — MediaTek, Nov 2, 2026

  Vendor-confirmed Critical modem out-of-bounds-write vulnerabilities CVE-2026-20499 and CVE-2026-20545 through CVE-2026-20549, plus additional High and Medium modem findings. Affected chipsets span multiple smartphone and cellular-IoT product families; consult the bulletin for precise models and OEM patch delivery.

- **[MediaTek October 2026 Security Bulletin](https://www.mediatek.com/product-security-bulletin/October-2026)** — MediaTek, Oct 2026

  Includes Critical modem memory-corruption vulnerabilities CVE-2026-20519 and CVE-2026-20520, and additional modem issues involving memory safety and input validation. The vendor bulletin was updated on October 30, 2026.

- **[CVE-2026-20540: MediaTek Modem DoS via Rogue Base Station](https://nvd.nist.gov/vuln/detail/CVE-2026-20540)** — MediaTek, Oct 2026

  A modem out-of-bounds read that can cause remote denial of service after a user device connects to an attacker-controlled rogue base station. Exploitation requires that radio-access condition and does not require additional user interaction.

- **[MediaTek July 2026 Security Bulletin](https://www.mediatek.com/product-security-bulletin/July-2026)** — MediaTek, July 2026

  Discloses High-severity modem vulnerabilities CVE-2026-20457 through CVE-2026-20461, including improper input validation and potential modem crashes across a range of mobile chipsets.

- **[MediaTek May 2026 Security Bulletin](https://www.mediatek.com/product-security-bulletin/May-2026)** — MediaTek, May 2026

  Includes modem vulnerabilities CVE-2026-20449 (heap buffer overflow) and CVE-2026-20450 (reachable assertion), both rated High severity and capable of crashing affected modem implementations.

### Detection, Defense, and Standards-Based Validation

- **[NIST CSWP 36G: False Base Station — Applying 5G Cybersecurity and Privacy Capabilities](https://csrc.nist.gov/pubs/cswp/36/g/false-base-station-applying-5g-cybersecurity-and-p/ipd)** — NIST NCCoE, Sep 30, 2026 (Initial Public Draft)

  Evaluates 5G device behavior across six simulated fake-base-station scenarios in NIST's 5G security testbed. Covers availability, privacy, and remaining denial-of-service risks despite stronger 5G protections.

- **[NIST CSWP 36F: Initial NAS Message Security](https://csrc.nist.gov/pubs/cswp/36/f/initial-nas-message-security-applying-5g-cybersecu/ipd)** — NIST NCCoE, Aug 6, 2026 (Initial Public Draft)

  Explains how standards-defined 5G protections can encrypt and integrity-protect sensitive content in initial Non-Access Stratum messages, and describes how operators can test whether those protections are enabled in their deployments.

- **[GSMA Mobile Telecommunications Security Landscape 2026](https://www.gsma.com/solutions-and-impact/technologies/security/gsma-mobile-telecommunications-security-landscape-2026/)** — GSMA, 2026

  Industry threat-landscape report documenting attack trends across networks, devices, and subscribers. Covers weaknesses in software implementations, barriers to launching attacks, supply chain exposure, and operational mitigation priorities.

- **[ADAD: AI-Driven Detector for Fake Base Station and Signal Overshadowing Attacks](https://www.sciencedirect.com/science/article/pii/S138912862600678X)** — Computer Networks, Oct 2026

  Detection research focused on fake-base-station and signal-overshadowing threats in radio access networks, including the LTE control-plane procedures retained by 5G NSA and some satellite direct-to-cell deployments.


---

### iOS Exploitation and Persistent Jailbreak Research (2026)

- **[Coruna: The Mysterious Journey of a Powerful iOS Exploit Kit](https://cloud.google.com/blog/en/topics/threat-intelligence/coruna-powerful-ios-exploit-kit)** — Google Threat Intelligence Group, March 2026

  Advanced iOS exploit kit containing 23 exploits across five complete chains targeting iOS 13.0–17.2.1. Combines WebKit RCE, sandbox escapes, and kernel exploitation. Associated with surveillance and financially motivated attacks.

- **[Calif: Persistent iPhone Jailbreak at Hexacon 2026](https://blog.calif.io/p/iphone)** — Calif, October 2026

  Researchers demonstrated an untethered jailbreak on an iPhone 18 Pro running iOS 27.0.1, retaining root access following reboot. Also presented Signal and iMessage exploitation demonstrations. Technical details and public exploit code have not been released.

- **[ARIstoteles: Dissecting Apple's Baseband Interface](https://arxiv.org/abs/2604.23457)** — April 2026

  Reverse engineering and fuzzing research targeting Apple's undocumented ARI interface between the application processor, CommCenter, and cellular baseband. Introduces automated Wireshark dissector generation and a framework for identifying baseband-facing attack surfaces.
