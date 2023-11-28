### 1. Command to create a self-signed certificate

```
openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout private.key -out certificate.crt -subj "/C=US/ST=Denial/L=Springfield/O=Dis/CN=test.linux.example.com"
```

### 2. Installing certbot

```
sudo apt-get install snapd -y
sudo snap install core; sudo snap refresh core
sudo apt-get remove certbot
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot

---OR-->

sudo apt install certbot
```

### 3. Install a nginx

```
sudo apt-get install nginx-full -y
```

> Create a new config file in the config.d directory

```
vim /etc/nginx/conf.d/rebrain.conf
```

### 4. Get a certificate with certbot

```
certbot certonly --webroot -w /var/www/html -d fhmja1gkr7u9k63eaife.51.250.90.211.nip.io
```

> Certificate content

```
root@fhmja1gkr7u9k63eaife:/etc/letsencrypt/archive/fhmja1gkr7u9k63eaife.51.250.90.211.nip.io# cat cert1.pem
-----BEGIN CERTIFICATE-----
MIIFWTCCBEGgAwIBAgISBCnpH3ksZ7lRI0Cy96SKHGtIMA0GCSqGSIb3DQEBCwUA
MDIxCzAJBgNVBAYTAlVTMRYwFAYDVQQKEw1MZXQncyBFbmNyeXB0MQswCQYDVQQD
EwJSMzAeFw0yMjA3MDMxMDA5NDZaFw0yMjEwMDExMDA5NDVaMDQxMjAwBgNVBAMT
KWZobWphMWdrcjd1OWs2M2VhaWZlLjUxLjI1MC45MC4yMTEubmlwLmlvMIIBIjAN
BgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA5LITNIIGAAtuxN3VHXcYB+z5W6DK
c4cI4gt1TKaDF89573KMW1pEI0bZzSGpAzmWadzSxETpNNvQ5AaQbizt+ZNmgOWv
QodakoUpNE6oGfIsV00cmZF2evMuGNkDjQEey1/hWiMWGzS8iYoJcQDMvV1vviYi
9TaL/E4f4DQUM+siEmjkNBkvtwyARiMNHKW3TdBkk/01Nst7w9TGUVgrfwJ9+6dX
ZhS7cIc3PpNAOkcKPgfEUmuLS+BEQr8RIGyO5IkR3XkT5jkHJlRzPXIWpzp8fmJE
L59GnmVcyCQNiSipIHPA8BUtE2EZmdb7QZs3TXH1FMjbDgWClaFuptJsswIDAQAB
o4ICZTCCAmEwDgYDVR0PAQH/BAQDAgWgMB0GA1UdJQQWMBQGCCsGAQUFBwMBBggr
BgEFBQcDAjAMBgNVHRMBAf8EAjAAMB0GA1UdDgQWBBTTAeGVyp2XY0IWefpmqan/
t6VV8jAfBgNVHSMEGDAWgBQULrMXt1hWy65QCUDmH6+dixTCxjBVBggrBgEFBQcB
AQRJMEcwIQYIKwYBBQUHMAGGFWh0dHA6Ly9yMy5vLmxlbmNyLm9yZzAiBggrBgEF
BQcwAoYWaHR0cDovL3IzLmkubGVuY3Iub3JnLzA0BgNVHREELTArgilmaG1qYTFn
a3I3dTlrNjNlYWlmZS41MS4yNTAuOTAuMjExLm5pcC5pbzBMBgNVHSAERTBDMAgG
BmeBDAECATA3BgsrBgEEAYLfEwEBATAoMCYGCCsGAQUFBwIBFhpodHRwOi8vY3Bz
LmxldHNlbmNyeXB0Lm9yZzCCAQUGCisGAQQB1nkCBAIEgfYEgfMA8QB3AEHIyrHf
IkZKEMahOglCh15OMYsbA+vrS8do8JBilgb2AAABgcPAkhoAAAQDAEgwRgIhALws
V04jKGxWCaSkfCfitE83/qcUu7K1LWEsrbFQleD9AiEA+kGXoGUaXIRzYl5wohXL
U1AsgRAToyZkDYJn/ZiFC1AAdgBGpVXrdfqRIDC1oolp9PN9ESxBdL79SbiFq/L8
cP5tRwAAAYHDwJI+AAAEAwBHMEUCIQClqKukMnYRPOQITy6VkB3ml2Lclb5w1O6/
aOwJh3iV5AIgKfF1xu+/DXjWvuwNXBTk0WGAMW38sDoVQ7V7waKYP6MwDQYJKoZI
hvcNAQELBQADggEBACghRxvFdNZEzqenfhu2e7nVPol5Y4BdCZ7l5IlR8pZdc4we
Enup7t/K8ajvt/omqmiyszhydwpChDoJIm2tmCayHNLoTnkb1mbABATb4SveVFG+
4mlG5UktfnaXYx0edHhdn+yu9l+LJWSuWxD1cyKvwYjlDwwDDDNbHpSu2t0pjjXs
iDq1iOdR1e6kkB9Kru3wdx9VBKjPOh91si/mfzg4WTV3iJkE3wqK8OfYNTjlGLnx
FvCsBw72vBB5ir9Aj6dFx+m58MgsfaHdIaK8cUFkK/CQnyw1nKPfrEc40VYw4d2e
kyuIAmCIJ5HeLvtjLcfhtKC1S3fp5pQ7Jjjr1bY=
-----END CERTIFICATE-----
```

### 5. Generate auto-renewal certificate with nginx reload

> Add below row in the `/etc/letsencrypt/cli.ini`

```
deploy-hook = systemctl reload nginx
```

> Verify my changes work correctly

```
root@fhmja1gkr7u9k63eaife:~# certbot renew --dry-run
Saving debug log to /var/log/letsencrypt/letsencrypt.log

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Processing
/etc/letsencrypt/renewal/fhmja1gkr7u9k63eaife.51.250.90.211.nip.io.conf
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Cert not due for renewal, but simulating renewal for dry run
Plugins selected: Authenticator webroot, Installer None
Renewing an existing certificate
Performing the following challenges:
http-01 challenge for fhmja1gkr7u9k63eaife.51.250.90.211.nip.io
Using the webroot path /var/www/html for all unmatched domains.
Waiting for verification...
Cleaning up challenges
Dry run: skipping deploy hook command: systemctl reload nginx

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
new certificate deployed without reload, fullchain is
/etc/letsencrypt/live/fhmja1gkr7u9k63eaife.51.250.90.211.nip.io/fullchain.pem
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
** DRY RUN: simulating 'certbot renew' close to cert expiry
**          (The test certificates below have not been saved.)

Congratulations, all renewals succeeded. The following certs have been renewed:
  /etc/letsencrypt/live/fhmja1gkr7u9k63eaife.51.250.90.211.nip.io/fullchain.pem (success)
** DRY RUN: simulating 'certbot renew' close to cert expiry
**          (The test certificates above have not been saved.)
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
```

### 6. Add SSL config to server config

```
server {
	listen 443 ssl;

	server_name fhmja1gkr7u9k63eaife.51.250.90.211.nip.io;

	root /var/www/html;

	ssl_certificate /etc/letsencrypt/archive/fhmja1gkr7u9k63eaife.51.250.90.211.nip.io/fullchain1.pem;
	ssl_certificate_key /etc/letsencrypt/archive/fhmja1gkr7u9k63eaife.51.250.90.211.nip.io/privkey1.pem;
	ssl_session_timeout 1d;
	ssl_session_tickets off;

	ssl_protocols TLSv1.2 TLSv1.3;
	ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384;
	ssl_prefer_server_ciphers off;

	add_header Strict-Transport-Security "max-age=63072000" always;

	ssl_stapling on;
    	ssl_stapling_verify on;

	resolver 1.1.1.1;

	location / {
		index index.nginx-debian.html;
		try_files $uri $uri/ =404;
	}
}
```

### 7. Add a permanent redirect from http to https in the default config

```
server {
	listen 80;

	server_name fhmja1gkr7u9k63eaife.51.250.90.211.nip.io;

	location / {
		return 301 https://$host$request_uri;
	}
}

server {
	listen 80 default_server;
	listen [::]:80 default_server;

	server_name "";
	return 444;
}
```

### 8. Link to the site

Push me -> [Link to my site](https:://fhmja1gkr7u9k63eaife.51.250.90.211.nip.io)

