# mail

## install

```
sudo apt install postfix -y
sudo apt install mailutils -y
###
After modifying main.cf, be sure to run ' '.
```

## send message

```
root@fhm1b26l6b00hp8qm7vo:~# mail -s "The test message" rebrainme-mail@rebrainme.local <<< "Hello, bro. How is it going?"
```

## 

```
yc-user@fhm1b26l6b00hp8qm7vo:~$ telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 rebrainme.local ESMTP Postfix (Ubuntu)
EHLO rebrainme.local
250-rebrainme.local
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250-DSN
250-SMTPUTF8
250 CHUNKING
MAIL FROM: root@rebrainme.local
250 2.1.0 Ok
RCPT TO: rebrainme-mail@rebrainme.local
250 2.1.5 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
SUBJECT: Hello, Bro!

Hello bro, How is it going?


.
250 2.0.0 Ok: queued as 8503F421B1
quit
221 2.0.0 Bye
Connection closed by foreign host.
```

```
yc-user@fhm1b26l6b00hp8qm7vo:~$ su - rebrainme-mail
Password:
rebrainme-mail@fhm1b26l6b00hp8qm7vo:~$ mail
"/var/mail/rebrainme-mail": 1 message 1 new
>N   1 root@rebrainme.loc Sun Jul 31 15:56  14/492   Hello, Bro!
?
Return-Path: <root@rebrainme.local>
X-Original-To: rebrainme-mail@rebrainme.local
Delivered-To: rebrainme-mail@rebrainme.local
Received: from rebrainme.local (localhost [IPv6:::1])
    by rebrainme.local (Postfix) with ESMTP id 8503F421B1
    for <rebrainme-mail@rebrainme.local>; Sun, 31 Jul 2022 15:55:40 +0000 (UTC)
SUBJECT: Hello, Bro!
Message-Id: <20220731155605.8503F421B1@rebrainme.local>
Date: Sun, 31 Jul 2022 15:55:40 +0000 (UTC)
From: root@rebrainme.local

Hello bro, How is it going?


? q
Saved 1 message in /home/rebrainme-mail/mbox
Held 0 messages in /var/mail/rebrainme-mail
```

