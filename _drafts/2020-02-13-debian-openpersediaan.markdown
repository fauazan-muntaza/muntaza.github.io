---
layout: post
title:  "Deploy OpenPersediaan pada Linux Debian 10"
date:   2020-02-13 12:26:56 +0800
categories: debian
---

# Bismillah,

Catatan

```text
$ sudo apt-get update
```

$ sudo apt-get dist-upgrade
$ sudo reboot

muntaza@kalsel:~$ uname -rms
Linux 4.19.0-8-amd64 x86_64
$ apt list --installed | less
$ sudo apt install rsync
$ sudo apt install vim-python-jedi
sudo apt install python3-pip


sudo pip3 install Django==2.2.10

$ django-admin --version
2.2.10


$ apt list --installed | grep apache2

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

apache2-bin/stable,stable,now 2.4.38-3+deb10u3 amd64 [installed,automatic]
apache2-data/stable,stable,now 2.4.38-3+deb10u3 all [installed,automatic]
apache2-utils/stable,stable,now 2.4.38-3+deb10u3 amd64 [installed,automatic]
apache2/stable,stable,now 2.4.38-3+deb10u3 amd64 [installed]

$ sudo apt install libapache2-mod-php php-pgsql php-gd
$ sudo apt install postgresql-11 postgresql-contrib postgresql-client

$ sudo apt install postgresql-server-dev-11
$ sudo pip3 install psycopg2
$ sudo apt install wget

sudo apt install python3-acme python3-certbot python3-mock python3-openssl python3-pkg-resources python3-pyparsing python3-zope.interface

$ sudo systemctl stop  apache2
$ sudo apt install python3-certbot-apache python3-certbot-nginx

ganti port apache ke port 81



https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-debian-10


# Buat ssl certificat

muntaza@kalsel:~$ sudo certbot --nginx -d www.example.com
Saving debug log to /var/log/letsencrypt/letsencrypt.log
Plugins selected: Authenticator nginx, Installer nginx
Enter email address (used for urgent renewal and security notices) (Enter 'c' to
cancel): you@example.com

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Please read the Terms of Service at
https://letsencrypt.org/documents/LE-SA-v1.2-November-15-2017.pdf. You must
agree in order to register with the ACME server at
https://acme-v02.api.letsencrypt.org/directory
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(A)gree/(C)ancel: A

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Would you be willing to share your email address with the Electronic Frontier
Foundation, a founding partner of the Let's Encrypt project and the non-profit
organization that develops Certbot? We'd like to send you email about our work
encrypting the web, EFF news, campaigns, and ways to support digital freedom.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: N
Obtaining a new certificate
Performing the following challenges:
http-01 challenge for www.example.com
Waiting for verification...
Cleaning up challenges
Deploying Certificate to VirtualHost /etc/nginx/sites-enabled/default

Please choose whether or not to redirect HTTP traffic to HTTPS, removing HTTP access.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: No redirect - Make no further changes to the webserver configuration.
2: Redirect - Make all requests redirect to secure HTTPS access. Choose this for
new sites, or if you're confident your site works on HTTPS. You can undo this
change by editing your web server's configuration.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 2
Redirecting all traffic on port 80 to ssl in /etc/nginx/sites-enabled/default

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Congratulations! You have successfully enabled https://www.example.com

You should test your configuration at:
https://www.ssllabs.com/ssltest/analyze.html?d=www.example.com
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/www.example.com/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/www.example.com/privkey.pem
   Your cert will expire on 2020-05-14. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot again
   with the "certonly" option. To non-interactively renew *all* of
   your certificates, run "certbot renew"
 - Your account credentials have been saved in your Certbot
   configuration directory at /etc/letsencrypt. You should make a
   secure backup of this folder now. This configuration directory will
   also contain certificates and private keys obtained by Certbot so
   making regular backups of this folder is ideal.
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le

muntaza@kalsel:~$


$ sudo crontab -l | tail -5
# m h  dom mon dow   command

0   0  *   *   *     nft -f /etc/nftables_level_0.conf
5   0  *   *   *     certbot renew
15  0  *   *   *     nft -f /etc/nftables_level_3.conf










# Alhamdulillah
