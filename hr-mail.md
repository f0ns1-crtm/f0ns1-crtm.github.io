---
layout: default
---

## hr-mail 192.168.43.33

On the target lab, the main activity it's enumerate the network and reuse the vanessa finance user credentials.


### 1. Network enumeration

During the network range enumeration 192.168.0.1/24 with nmap the following host was detected:

```
PS C:\Users\itemployee15> nmap.exe -A -Pn 192.168.43.33
Starting Nmap 7.95 ( https://nmap.org ) at 2024-06-19 01:53 Pacific Daylight Time
Nmap scan report for 192.168.43.33
Host is up (0.0051s latency).
Not shown: 995 filtered tcp ports (no-response)
PORT    STATE  SERVICE VERSION
25/tcp  open   smtp    hMailServer smtpd
| smtp-commands: HR-MAIL, SIZE 20480000, AUTH LOGIN, HELP
|_ 211 DATA HELO EHLO MAIL NOOP QUIT RCPT RSET SAML TURN VRFY
110/tcp open   pop3    hMailServer pop3d
|_pop3-capabilities: UIDL TOP USER
465/tcp closed smtps
587/tcp open   smtp    hMailServer smtpd
| smtp-commands: HR-MAIL, SIZE 20480000, AUTH LOGIN, HELP
|_ 211 DATA HELO EHLO MAIL NOOP QUIT RCPT RSET SAML TURN VRFY
995/tcp closed pop3s
Device type: general purpose
Running (JUST GUESSING): Microsoft Windows 2019|10 (94%)
OS CPE: cpe:/o:microsoft:windows_server_2019 cpe:/o:microsoft:windows_10
Aggressive OS guesses: Windows Server 2019 (94%), Microsoft Windows 10 1903 - 21H1 (89%), Microsoft Windows 10 1607 (88%), Microsoft Windows 10 1809 (85%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 2 hops
Service Info: Host: HR-MAIL; OS: Windows; CPE: cpe:/o:microsoft:windows

TRACEROUTE (using port 995/tcp)
HOP RTT     ADDRESS
1   2.00 ms 192.168.100.254
2   3.00 ms 192.168.43.33

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 62.98 seconds
```

Related to the open ports detected, it's seems that there are a Windows machine with an SMTP installed.

### 2. POP3 service extranel connection with FINANCE\vannesa credentials

Using local instaled telnet feature from attacker machine connecte woth pop3 service of hr-mail.gcbhr.local

```
telnet 192.168.43.33 110
```
List messages for vanessa user:
```
+OK POP3
USER vanessa@gcbfinance.local
+OK Send your password
PASS 300YearsAndStillG0ing$trong
+OK Mailbox locked and ready
list
+OK 5 messages (5499 octets)
1 727
2 1247
3 906
4 1190
5 1429
.
```
Dump messages:

```
retr 1
+OK 727 octets
Return-Path: erika@gcbfinance.local
Received: from [192.168.43.24] (hr-erika [192.168.43.24])
        by HR-MAIL with ESMTPA
        ; Fri, 6 Sep 2019 00:12:43 -0700
To: vanessa@gcbfinance.local
From: erika <erika@gcbfinance.local>
Subject: Hello there ;)
Message-ID: <4e5945ef-2d41-fdfc-2e18-859040ef23d2@gcbfinance.local>
Date: Fri, 6 Sep 2019 00:12:33 -0700
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:60.0) Gecko/20100101
 Thunderbird/60.7.2
MIME-Version: 1.0
Content-Type: text/plain; charset=utf-8; format=flowed
Content-Transfer-Encoding: 7bit
Content-Language: en-US

Guess who has a gcbfinance email id? ;)

I got Romi from IT to run this private mail server for us and others in
the gang! Use this for casual stuff not the official one.

.
retr 2
+OK 1247 octets
Return-Path: erika@gcbfinance.local
Received: from [192.168.43.24] (hr-erika [192.168.43.24])
        by HR-MAIL with ESMTPA
        ; Fri, 6 Sep 2019 00:22:39 -0700
Subject: Re: Hello there ;)
To: vanessa <vanessa@gcbfinance.local>
References: <4e5945ef-2d41-fdfc-2e18-859040ef23d2@gcbfinance.local>
 <ebdb1c9f-3e7f-67d9-5d74-b2752bf93735@gcbfinance.local>
From: erika <erika@gcbfinance.local>
Message-ID: <57864775-96fa-67b4-1a1a-ba6244d0f0c4@gcbfinance.local>
Date: Fri, 6 Sep 2019 00:22:31 -0700
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:60.0) Gecko/20100101
 Thunderbird/60.7.2
MIME-Version: 1.0
In-Reply-To: <ebdb1c9f-3e7f-67d9-5d74-b2752bf93735@gcbfinance.local>
Content-Type: text/plain; charset=utf-8; format=flowed
Content-Transfer-Encoding: 7bit
Content-Language: en-US

Romi told me that he routes this from the official mail server (and some
additional technical stuff which I didn't listen to). But you can still
send me archives (zip files).

On 9/6/2019 12:20 AM, vanessa wrote:
> Awesome! What about the policy?
>
> On 9/6/2019 12:12 AM, erika wrote:
>> Guess who has a gcbfinance email id? ;)
>>
>> I got Romi from IT to run this private mail server for us and others
>> in the gang! Use this for casual stuff not the official one.
>>
.
retr 3
+OK 906 octets
Return-Path: erika@gcbfinance.local
Received: from [192.168.43.24] (hr-erika [192.168.43.24])
        by HR-MAIL with ESMTPA
        ; Fri, 6 Sep 2019 00:47:12 -0700
Subject: Re: List of new employees
To: vanessa <vanessa@gcbfinance.local>
References: <1f66491c-c90b-b3b1-1bb3-416251d64158@gcbfinance.local>
From: erika <erika@gcbfinance.local>
Message-ID: <e40ff7ec-0f79-60bb-811c-ed5909313e1e@gcbfinance.local>
Date: Fri, 6 Sep 2019 00:47:02 -0700
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:60.0) Gecko/20100101
 Thunderbird/60.7.2
MIME-Version: 1.0
In-Reply-To: <1f66491c-c90b-b3b1-1bb3-416251d64158@gcbfinance.local>
Content-Type: text/plain; charset=utf-8; format=flowed
Content-Transfer-Encoding: 7bit
Content-Language: en-US

Keep it to the official ID. Do you know why your email time is shown as
midnight?

On 9/6/2019 12:45 AM, vanessa wrote:
> Hey Erika,
>
> Did you get the list of the new employees in IT?
>
.
retr 4
+OK 1190 octets
Return-Path: erika@gcbfinance.local
Received: from [192.168.43.24] (hr-erika [192.168.43.24])
        by HR-MAIL with ESMTPA
        ; Fri, 6 Sep 2019 00:48:43 -0700
Subject: Re: List of new employees
To: vanessa <vanessa@gcbfinance.local>
References: <1f66491c-c90b-b3b1-1bb3-416251d64158@gcbfinance.local>
 <e40ff7ec-0f79-60bb-811c-ed5909313e1e@gcbfinance.local>
 <d6d3e7fe-0d17-5c51-512f-b55af813ac08@gcbfinance.local>
From: erika <erika@gcbfinance.local>
Message-ID: <102631cd-2a68-d5bc-b504-c3651f2f4062@gcbfinance.local>
Date: Fri, 6 Sep 2019 00:48:33 -0700
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:60.0) Gecko/20100101
 Thunderbird/60.7.2
MIME-Version: 1.0
In-Reply-To: <d6d3e7fe-0d17-5c51-512f-b55af813ac08@gcbfinance.local>
Content-Type: text/plain; charset=utf-8; format=flowed
Content-Transfer-Encoding: 7bit
Content-Language: en-US

Let me check with him!

On 9/6/2019 12:47 AM, vanessa wrote:
> Oh sure!
>
> No idea! I will ask Romi!
>
> On 9/6/2019 12:47 AM, erika wrote:
>> Keep it to the official ID. Do you know why your email time is shown
>> as midnight?
>>
>> On 9/6/2019 12:45 AM, vanessa wrote:
>>> Hey Erika,
>>>
>>> Did you get the list of the new employees in IT?
>>>
.
retr 5
+OK 1429 octets
Return-Path: erika@gcbfinance.local
Received: from [192.168.43.24] (hr-erika [192.168.43.24])
        by HR-MAIL with ESMTPA
        ; Fri, 6 Sep 2019 02:08:37 -0700
Subject: Re: List of new employees
From: erika <erika@gcbfinance.local>
To: vanessa <vanessa@gcbfinance.local>
References: <1f66491c-c90b-b3b1-1bb3-416251d64158@gcbfinance.local>
 <e40ff7ec-0f79-60bb-811c-ed5909313e1e@gcbfinance.local>
 <d6d3e7fe-0d17-5c51-512f-b55af813ac08@gcbfinance.local>
 <102631cd-2a68-d5bc-b504-c3651f2f4062@gcbfinance.local>
Message-ID: <d06dd027-69c9-9ed7-f138-5fa04a11714b@gcbfinance.local>
Date: Fri, 6 Sep 2019 02:08:28 -0700
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:60.0) Gecko/20100101
 Thunderbird/60.7.2
MIME-Version: 1.0
In-Reply-To: <102631cd-2a68-d5bc-b504-c3651f2f4062@gcbfinance.local>
Content-Type: text/plain; charset=utf-8; format=flowed
Content-Transfer-Encoding: 7bit
Content-Language: en-US

He told me some technical reason. Also warned me about not telling
anyone else about it. Guess its a secret between us :D

On 9/6/2019 12:48 AM, erika wrote:
> Let me check with him!
>
> On 9/6/2019 12:47 AM, vanessa wrote:
>> Oh sure!
>>
>> No idea! I will ask Romi!
>>
>> On 9/6/2019 12:47 AM, erika wrote:
>>> Keep it to the official ID. Do you know why your email time is shown
>>> as midnight?
>>>
>>> On 9/6/2019 12:45 AM, vanessa wrote:
>>>> Hey Erika,
>>>>
>>>> Did you get the list of the new employees in IT?
>>>>
.
```


[back](./section4.html)