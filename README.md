# Awesome-Cellular-Hacking 
Please note multiple researchers published and compiled this work. This is a list of their research in the 3G/4G/5G Cellular security space. This information is intended to consolidate the community's knowledge. Thank you, I plan on frequently updating this "Awesome Cellular Hacking" curated list with the most up to date exploits, blogs, research, and papers.

The idea is to collect information like the BMW article below, that slowly gets cleared and wiped up from the Internet - making it less accessible, and harder to find. Feel free to email me any document or link to add.

## Rogue BTS & CDMA/GSM Traffic Impersonation and Interception 

- [How to create an Evil LTE Twin/LTE Rogue BTS](https://medium.com/@adam.toscher/how-to-create-an-evil-lte-twin-34b0a9ce193b)
How to setup a 4G/LTE EVil Twin Base Station. Similar to @Evilsocket's How To Build Your Own Rogue GSM BTS For Fun and Profit  but adapted for some LTE 4G Testing/Use Cases
- [How To Build Your Own Rogue GSM BTS For Fun and Profit](https://www.evilsocket.net/2016/03/31/how-to-build-your-own-rogue-gsm-bts-for-fun-and-profit/)
"In this blog post I’m going to explain how to create a portable GSM BTS which can be used either to create a private ( and vendor free! ) GSM network or for GSM active tapping/interception/hijacking … yes, with some (relatively) cheap electronic equipment you can basically build something very similar to what the governments are using from years to perform GSM interception."
- [Practical attacks against GSM networks: Impersonation](https://blog.blazeinfosec.com/practical-attacks-against-gsm-networks-part-1/)
"Impersonating a cellular base station with SDR: With the flexibility, relative low cost of Software Defined Radio (SDR) and abundance of open source projects that emulate a cell tower, successfully impersonating a GSM Base Station (BTS) is not a difficult task these days."
- https://blog.strcpy.info/2016/04/21/building-a-portable-gsm-bts-using-bladerf-raspberry-and-yatebts-the-definitive-guide/
"I was always amazed when I read articles published by some hackers related to GSM technology. However, playing with GSM technologies was not cheap until the arrival of Software Defined Radios (SDRs), besides not being something easy to be implemented.
- https://www.rtl-sdr.com/rtl-sdr-tutorial-analyzing-gsm-with-airprobe-and-wireshark/ "The RTL-SDR software defined radio can be used to analyze cellular phone GSM signals, using Linux based tools GR-GSM (or Airprobe) and Wireshark. This tutorial shows how to set up these tools for use with the RTL-SDR."

- https://www.nccgroup.trust/uk/about-us/newsroom-and-events/blogs/2016/may/gsmgprs-traffic-interception-for-penetration-testing-engagements/ "Within the penetration testing domain quite often we have to deal with different technologies and devices.  It’s important to cover all aspects of connectivity of a device being tested which is why we have built a GSM/GPRS interception capability. There are a number of different devices and systems that make use of GSM/GPRS, non-exhaustively we commonly see:"

# Rogue Base Stations (Evil BTS, Evil 3g/4G, Rogue BTS)
[OpenBTS software](http://openbts.org/) is a Linux application that uses a software-defined radio to present a standard 3GPP air interface to user devices, while simultaneously presenting those devices as SIP endpoints to the Internet

[YateBTS](https://yatebts.com/) is a software implementation of a GSM/GPRS radio access network based on Yate and is compatible with both 2.5G and 4G core networks comprised in our YateUCN unified core network server. Resiliency, customization and technology independence are the main attributes of YateBTS

- [bladRF and YateBTS Configuration](https://github.com/Nuand/bladeRF/wiki/Setting-up-Yate-and-YateBTS-with-the-bladeRF)

[srsLTE](https://github.com/srsLTE/srsLTE) is a free and open-source LTE software suite developed by SRS (www.softwareradiosystems.com)

Common issues:
- Improper FW
- Lack of proper antennas
- Wrong cellular phone type 
- Wrong SIM
- Not configured correctly - Mobile Country Codes (MCC) and Mobile Network Codes (MNC)
- Incorrect software BTS settings
- Virtualized platform is not fast enough
- Wrong SDR firmware

## CERT/Media Alerts

- [Voice over LTE implementations contain multiple vulnerabilities - CERT ALERT](https://www.kb.cert.org/vuls/id/943167/)

## Recent Conference Talks/Presentations 

# Usenix

- [Hiding in Plain Signal:Physical Signal Overshadowing Attack on LTE](https://www.usenix.org/system/files/sec19-yang-hojoon.pdf) - This attack, which is referred to as signal overshadowing (named SigOver) has several advantages and differences when compared with existing
attacks using a fake base station

# Defcon/BH 2019

- [Shupeng-All-The-4G-Modules-Could-Be-Hacked](https://i.blackhat.com/USA-19/Wednesday/us-19-Shupeng-All-The-4G-Modules-Could-Be-Hacked.pdf)
- [New Vulnerabilities in 5G Networks](https://threatpost.com/5g-security-flaw-mitm-targeted-attacks/147073/)

## Cellular Attacks

- [QCSniper - A tool For capture 2g-4g air traffic using qualcomm phones ](https://labs.p1sec.com/2019/07/09/presenting-qcsuper-a-tool-for-capturing-your-2g-3g-4g-air-traffic-on-qualcomm-based-phones/)
- [This is Your President Speaking:
Spoofing Alerts in 4G LTE Networks](Link removed, will upload pdf)
- [Hacking Public Warning System in LTE Mobile Networks](https://conference.hitb.org/hitbsecconf2019ams/materials/HAXPO%20D1%20-%20Hacking%20LTE%20Public%20Warning%20Systems%20-%20Weiguang%20Li.pdf)
- [RF Exploitation: IoT/OT Hacking with SDR](https://conference.hitb.org/hitbsecconf2019ams/materials/HAXPO%20D2%20-%20Demystifying%20IoT:OT%20Hacks%20With%20SDR%20-%20Himanshu%20Mehta%20&%20Harshit%20Agrawal.pdf)
- [Forcing a targeted LTE Cellphone Into an Eavesdropping Network](https://youtu.be/hNDChDM1hEE) 
- [Hacking Cellular Networks](https://www.openairinterface.org/docs/workshop/3_OAI_Workshop_20170427/Session2_UE/Lin_Huan_-_UE_Security.pdf)
- [Bye-Bye-IMSI-Catchers](https://conference.hitb.org/hitbsecconf2018pek/materials/D2T2%20-%20Bye%20Bye%20IMSI%20Catchers%20-%20Security%20Enhancements%20in%205g%20-%20Lin%20Huang.pdf)
- [New Privacy Threat on 3G, 4G, and Upcoming 5G AKA Protocols ](https://arxiv.org/pdf/1905.07617.pdf)
- [White-Stingray: Evaluating IMSI Catchers Detection Applications](http://www.cs.ox.ac.uk/files/9192/paper-final-woot-imsi.pdf)
- [Breaking_LTE_on_Layer_Two](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/breaking_lte_on_layer_two.pdf)
- [LTE/LTE-A Jamming, Spoofing, and Sniffing: Threat Assessment and Mitigation](https://github.com/W00t3k/Awesome-cellular-Hacking/blob/master/LTE_Jamming_Magazine_Paper_final.pdf)
- [Exploring LTE security and protocol exploits with open source software and low-cost software radio by Roger Jover](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/LTE_open_source_HackerHalted.pdf)
- [LTE PROTOCOL EXPLOITS: IMSI CATCHERS,BLOCKING DEVICES AND LOCATION LEAKS](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/LTE_security_TakeDownCon.pdf)
- [Practical Attacks Against Privacy and Availability in
4G/LTE Mobile Communication Systems](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/Prac-4G-Attacks.pdf)
- [Using OpenBTS - "Experimental_Security_Assessment_of_BMW_Cars by KeenLab"](https://keenlab.tencent.com/en/whitepapers/Experimental_Security_Assessment_of_BMW_Cars_by_KeenLab.pdf)
- [5G NR Jamming, Spoofing, and Sniffing](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/5gjam.pdf)
- [LTE Security – How Good Is It?](https://csrc.nist.gov/CSRC/media/Presentations/LTE-Security-How-Good-is-it/images-media/day2_research_200-250.pdf)
- https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-187.pdf
-[Small Tweaks do Not Help: Differential Power Analysis of MILENAGE Implementations in 3G/4G USIM Cards](https://www.blackhat.com/docs/us-15/materials/us-15-Yu-Cloning-3G-4G-SIM-Cards-With-A-PC-And-An-Oscilloscope-Lessons-Learned-In-Physical-Security-wp.pdf)
- [#root via SMS: 4G access level security assessment](https://hackinparis.com/data/slides/2015/timur_yusinov_root_via_sms.pdf)
- [Small Tweaks do Not Help: Differential Power Analysis of MILENAGE Implementations in 3G/4G USIM Cards](https://www.blackhat.com/docs/us-15/materials/us-15-Yu-Cloning-3G-4G-SIM-Cards-With-A-PC-And-An-Oscilloscope-Lessons-Learned-In-Physical-Security-wp.pdf)
- [LTE security and protocol exploits](https://github.com/W00t3k/Awesome-CellularHacking/blob/master/ShmooCon_talk_final_01162016.pdf)
- [LTE Recon - (Defcon 23)](https://www.rtl-sdr.com/one-more-rtl-sdr-talk-from-defcon-23/)
- [LTE Pwnage: Hacking	HLR/HSS	and	MME CoreNetwork	Elements](https://conference.hitb.org/hitbsecconf2013ams/materials/D1T2%20-%20Philippe%20Langlois%20-%20Hacking%20HLR%20HSS%20and%20MME%20Core%20Network%20Elements.pdf)
- [Synacktiv](https://www.synacktiv.com/ressources/sstic_rump_2018_modmobjam.pdf)
- [WiFi IMSI Catcher](https://www.blackhat.com/docs/eu-16/materials/eu-16-OHanlon-WiFi-IMSI-Catcher.pdf)
- [Analysis of the LTE Control Plane](https://syssec.kaist.ac.kr/pub/2019/kim_sp_2019.pdf)
- [WiFi IMSI Catcher](https://www.blackhat.com/docs/eu-16/materials/eu-16-OHanlon-WiFi-IMSI-Catcher.pdf)
- [Demystifying the Mobile Network by Chuck McAuley](http://2014.video.sector.ca/video/110383258)
- (https://www.defcon.org/images/defcon-22/dc-22-presentations/Pierce-Loki/DEFCON-22-Pierce-Loki-NSA-PLAYSET-GSM.pdf)
- [D1T2 - Bypassing GSMA Recommendations on SS7 Networks - Kirill Puzankov](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/D1T2%20-%20Bypassing%20GSMA%20Recommendations%20on%20SS7%20Networks%20-%20Kirill%20Puzankov.pdf)
- [VoLTE Phreaking - Ralph Moonen](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/HAXPO%20D1%20-%20VoLTE%20Phreaking%20-%20Ralph%20Moonen.pdf)
- [Baseband Attacks: Remote Exploitation of Memory Corruptions in Cellular Protocol Stack] (https://www.usenix.org/system/files/conference/woot12/woot12-final24.pdf)


## SIM Specific Attacks

- [Rooting SIM-cards](https://media.blackhat.com/us-13/us-13-Nohl-Rooting-SIM-cards-Slides.pdf)
- [The Most Expensive Lesson Of My Life: Details of SIM port hack](https://medium.com/coinmonks/the-most-expensive-lesson-of-my-life-details-of-sim-port-hack-35de11517124)


## Stingray's

- https://www.wired.com/story/dcs-stingray-dhs-surveillance/
- https://www.vice.com/en_us/article/gv5k3x/heres-how-much-a-stingray-cell-phone-surveillance-tool-costs
- https://www.nyclu.org/en/stingrays

## SS7/Telecom Specific

- http://www.hackitoergosum.org/2010/HES2010-planglois-Attacking-SS7.pdf
- [Getting in the SS7  kingdom: hard technology and disturbingly easy hacks= to get entry points in the walled garden](http://www.hackitoergosum.org/2010/HES2010-planglois-Attacking-SS7.pdf)

## Github/Code Repo's

* https://github.com/Synacktiv-contrib/Modmobjam
* https://github.com/Synacktiv-contrib/Modmobmap

# Misc IMSI/Cellular Tools 
* https://github.com/Evrytania/LTE-Cell-Scanner
* https://harrisonsand.com/imsi-catcher/
* https://github.com/Oros42/IMSI-catcher
* https://github.com/CellularPrivacy/Android-IMSI-Catcher-Detector
* https://github.com/ptrkrysik/gr-gsm/wiki/Passive-IMSI-Catcher


## Resources
* [RTL-SDR](https://www.rtl-sdr.com/) 
* [MCC-MNC Codes for Base Stations](http://www.mcc-mnc.com/)
* [RFSec-ToolKit](https://github.com/cn0xroot/RFSec-ToolKit)
* [FakeBTS](http://fakebts.com/category/attacks/)
* https://rmusser.net/docs/Wireless.html#cn

## Misc

- [Touching the Untouchables: Dynamic Security](https://syssec.kaist.ac.kr/pub/2019/kim_sp_2019.pdf)
- https://www.eff.org/pages/cell-site-simulatorsimsi-catchers
- http://leetupload.com/blagosphere/2014/03/28/analyze-and-crack-gsm-downlink-with-a-usrp/
- [AT&T Microcell FAIL - fail0verflow (Older blog article, but still a good read)](https://fail0verflow.com/blog/2012/microcell-fail/)
