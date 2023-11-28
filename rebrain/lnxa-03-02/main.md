# main

[Postfix and Dovecot SASL](https://doc.dovecot.org/configuration_manual/howto/postfix_and_dovecot_sasl/)

[Testing IMAP and SMTP Authentication with Telnet](http://www.opensquad.com/blog/testing-imap-and-smtp-authentication-with-telnet/)

## Example conf.d/10-master.conf excerpt

```
service auth {
...
  unix_listener /var/spool/postfix/private/auth {
    mode = 0660
    # Assuming the default Postfix user and group
    user = postfix
    group = postfix
  }
  ...
}

# Outlook and Windows Mail works only with LOGIN mechanism, not the standard PLAIN:
auth_mechanisms = plain login

```

## Example Postfix main.cf excerpt

```
smtpd_sasl_type = dovecot

# Can be an absolute path, or relative to $queue_directory
# Debian/Ubuntu users: Postfix is setup by default to run chrooted, so it is best to leave it as-is below
smtpd_sasl_path = private/auth

# On Debian Wheezy path must be relative and queue_directory defined
#queue_directory = /var/spool/postfix

# and the common settings to enable SASL:
smtpd_sasl_auth_enable = yes
# With Postfix version before 2.10, use smtpd_recipient_restrictions
smtpd_relay_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination

```

## testing

```
telnet localhost imap
Trying ::1...
Connected to localhost.
Escape character is '^]'.

A1 LOGIN <user> <password>

* OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE AUTH=PLAIN] Dovecot ready.A1 login <username> <password>
A1 OK [CAPABILITY IMAP4rev1 LITERAL+ SASL-IR LOGIN-REFERRALS ID ENABLE IDLE SORT SORT=DISPLAY THREAD=REFERENCES ...] Logged in

A2 LOGOUT

* BYE Logging out
A2 OK Logout completed.
Connection closed by foreign host.


```
echo -ne '\0rebrainme-mail\0rebrainme-mail' | base64
AHJlYnJhaW5tZS1tYWlsAHJlYnJhaW5tZS1tYWls
```

```
telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
220 mail.testserver.com ESMTP Postfix

EHLO toto

250-mail.adinfrance.com
250-PIPELINING
250-SIZE 40000000
250-ETRN
250-AUTH PLAIN
250-AUTH=PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

AUTH PLAIN ZWNobyAtbmUgXDBsb2dpblwwcGFzc3dvcmQK

235 2.7.0 Authentication successful

QUIT

221 2.0.0 Bye
```
