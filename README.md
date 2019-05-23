
# Awesome-Cellular-Hacking 
Please note multiple researchers published and compiled this work. This is a list of their research in the 3G/4G/5G Cellular security space. This information is intended to consolidate the community's knowledge. Thank you, I plan on frequently updating this "Awesome Cellular Hacking" curated list with the most up to date exploits, blogs, research, and papers.

The idea is to collect information like the BMW article below, that slowly gets cleared and wiped up from the Internet - making it less accessible, and harder to find. Feel free to email me any document or link to add.

## Contents

# Research Papers

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


# Talks and Conferences

- [LTE security and protocol exploits](https://github.com/W00t3k/Awesome CellularHacking/blob/master/ShmooCon_talk_final_01162016.pdf)
- [LTE Recon - (Defcon 23)](https://www.rtl-sdr.com/one-more-rtl-sdr-talk-from-defcon-23/)
- [LTE Pwnage: Hacking	HLR/HSS	and	MME CoreNetwork	Elements	](https://conference.hitb.org/hitbsecconf2013ams/materials/D1T2%20-%20Philippe%20Langlois%20-%20Hacking%20HLR%20HSS%20and%20MME%20Core%20Network%20Elements.pdf)
- [Jam tomorrow, jam yesterday, but also jam today ]()
- [Synacktiv (https://www.synacktiv.com/ressources/sstic_rump_2018_modmobjam.pdf)
- [Touching the Untouchables: Dynamic Security](https://syssec.kaist.ac.kr/pub/2019/kim_sp_2019.pdf)
- [WiFi IMSI Catcher ](https://www.blackhat.com/docs/eu-16/materials/eu-16-OHanlon-WiFi-IMSI-Catcher.pdf)
- [Analysis of the LTE Control Plane](https://syssec.kaist.ac.kr/pub/2019/kim_sp_2019.pdf)
- [WiFi IMSI Catcher ](https://www.blackhat.com/docs/eu-16/materials/eu-16-OHanlon-WiFi-IMSI-Catcher.pdf)
- [Demystifying the Mobile Network by Chuck McAuley](http://2014.video.sector.ca/video/110383258)
- [GSM - have we overslept the last-wake-up call?]()
- (https://www.defcon.org/images/defcon-22/dc-22-presentations/Pierce-Loki/DEFCON-22-Pierce-Loki-NSA-PLAYSET-GSM.pdf)
- [D1T2 - Bypassing GSMA Recommendations on SS7 Networks - Kirill Puzankov](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/D1T2%20-%20Bypassing%20GSMA%20Recommendations%20on%20SS7%20Networks%20-%20Kirill%20Puzankov.pdf)
- [VoLTE Phreaking - Ralph Moonen](https://github.com/W00t3k/Awesome-Cellular-Hacking/blob/master/HAXPO%20D1%20-%20VoLTE%20Phreaking%20-%20Ralph%20Moonen.pdf)

# [↑](#contents)Evil BTS
[OpenBTS software](http://openbts.org/) is a Linux application that uses a software-defined radio to present a standard 3GPP air interface to user devices, while simultaneously presenting those devices as SIP endpoints to the Internet

[YateBTS](https://yatebts.com/) is a software implementation of a GSM/GPRS radio access network based on Yate and is compatible with both 2.5G and 4G core networks comprised in our YateUCN unified core network server. Resiliency, customization and technology independence are the main attributes of YateBTS

- [bladRF and YateBTS Configuration](https://github.com/Nuand/bladeRF/wiki/Setting-up-Yate-and-YateBTS-with-the-bladeRF)

[srsLTE](https://github.com/srsLTE/srsLTE) is a free and open-source LTE software suite developed by SRS (www.softwareradiosystems.com)

# GSM Traffic Impersonation and Interception Related Blogs

- [Practical attacks against GSM networks: Impersonation](https://blog.blazeinfosec.com/practical-attacks-against-gsm-networks-part-1/)
- https://blog.strcpy.info/2016/04/21/building-a-portable-gsm-bts-using-bladerf-raspberry-and-yatebts-the-definitive-guide/
- https://www.rtl-sdr.com/rtl-sdr-tutorial-analyzing-gsm-with-airprobe-and-wireshark/
- http://leetupload.com/blagosphere/2014/03/28/analyze-and-crack-gsm-downlink-with-a-usrp/
- [How To Build Your Own Rogue GSM BTS For Fun and Profit](https://www.evilsocket.net/2016/03/31/how-to-build-your-own-rogue-gsm-bts-for-fun-and-profit/)
- https://www.nccgroup.trust/uk/about-us/newsroom-and-events/blogs/2016/may/gsmgprs-traffic-interception-for-penetration-testing-engagements/

Common issues:
- Imprioper FW
- Lack of proper antennas
- Wrong cellular phone type 
- Wrong SIM
- Not configured correctly - Mobile Country Codes (MCC) and Mobile Network Codes (MNC)
- incorrect APN

## Stingray's

- https://www.wired.com/story/dcs-stingray-dhs-surveillance/
- https://www.vice.com/en_us/article/gv5k3x/heres-how-much-a-stingray-cell-phone-surveillance-tool-costs
- https://www.nyclu.org/en/stingrays

## SS7/Telecom Specific

- http://www.hackitoergosum.org/2010/HES2010-planglois-Attacking-SS7.pdf
- [Getting in the SS7  kingdom: hard technology and disturbingly easy hacks= to get entry points in the walled garden](http://www.hackitoergosum.org/2010/HES2010-planglois-Attacking-SS7.pdf)

## Jamming and Mapping
* https://github.com/Synacktiv-contrib/Modmobjam
* https://github.com/Synacktiv-contrib/Modmobmap


## Scanning
* https://github.com/Evrytania/LTE-Cell-Scanner
* https://harrisonsand.com/imsi-catcher/
* https://github.com/Oros42/IMSI-catcher
* https://github.com/CellularPrivacy/Android-IMSI-Catcher-Detector
* https://github.com/ptrkrysik/gr-gsm/wiki/Passive-IMSI-Catcher

 
## CERT/Media Alerts

- [Voice over LTE implementations contain multiple vulnerabilities - CERT ALERT](https://www.kb.cert.org/vuls/id/943167/)


## [↑](#contents)Resources
* [RTL-SDR](https://www.rtl-sdr.com/) 
* [MCC-MNC Codes for Base Stations](http://www.mcc-mnc.com/)
* [RFSec-ToolKit](https://github.com/cn0xroot/RFSec-ToolKit)
* [FakeBTS](http://fakebts.com/category/attacks/)
* https://rmusser.net/docs/Wireless.html#cn

## Misc

- https://www.eff.org/pages/cell-site-simulatorsimsi-catchers
- [AT&T Microcell FAIL - fail0verflow (Older blog article, but still a good read)](https://fail0verflow.com/blog/2012/microcell-fail/)
