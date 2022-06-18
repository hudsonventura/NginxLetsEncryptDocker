# NginxLetsEncryptDocker
This repo will help and automate to able a SSL with Let's Encrypt on container Docker using docker compose.
<br>
Credits to Phillip https://pentacent.medium.com

## Prerequisites
A distro Linux, docker, docker-compose, some knowledg about it and Nginx.
<br><br>

## Important notes before start
First you will configure the environment to accept ACME challenge (see Let's Encrypt), using a non valid certificate. After then, if all is working normaly, you will configure to certbot generate a valid certificate.

How should you know, the valid certificate geneated by Let's encrypt will expire in some months. Then certbot will regenerate it automatically for you.

___
<br><br>
## Edit file init-letsencrypt.sh
```bash
$ nano init-letsencrypt.sh
```
Edit the line 8 of file, replacing 'yourdomain.com' to your domain name.<br>


## Edit Nginx config
```bash
$ nano data/nginx/app.conf
```
Edit the lines 3, 14, 15 and 16 with exataly the same domain name. The line 27 have the proxy_pass to your system. The hostname in this case will resolve by docker network.
<br>

## Edit docker-compose.yml file
```bash
$ nano docker-compose.yml
```
Edit the line 23 replacing system-or-website to you system. Note that nginx config file (data/nginx/app.conf) must be pointed to your system, so you have to put the same name.
<br>


## Permission and firt run to generate the first certificates
```bash
sudo chmod 777 -R data
chmod +x init-letsencrypt.sh
sudo ./init-letsencrypt.sh
```
You will have to inform some data to generate a new certificate.
<br>


<br>

## Up with Docker Compose
```bash
$ sudo docker-compose up
```
At this poin you have a invalid certificate genegated, but you already have SSL able on your connection.<br>
Here you can configure Nginx to your pourpose. Make sure all is working right.<br><br>
<br>
<br>
Are you ready? Can we continue? Your website is working ok? So.... let's go.
<br>
<br>
____
## Now we will generate a valid certificate
<br>
## Edit file init-letsencrypt.sh
```bash
$ nano init-letsencrypt.sh
```
Edit the line 12 of file <b>init-letsencrypt.sh</b> from 'staging=1' to 'staging=0'.
<br>

## Try to generate a valid certificate
```bash
sudo ./init-letsencrypt.sh
```
<br>
If you get some error on generating process, be right that Nginx config is ok.<br>
Turn staging to 1 in init-letsencrypt.sh to tests.<br>
<br>
<br>

### The valid certificate maybe have some minutes to be really valid.
To all be right, use another browser to teste the valid ceriticate or open a new window in private mode.
<br>
<br>
<br>
<br>

# General Notes
You can generate just 5 valids certificate from 168 hours. So, if you have some trouble, set the staging (from init-letsencrypt.sh) to 1 until the tests is not finished.<br>
Finished it, you can set staging to 0 again.<br>
<br>
The lines 13 and 23 from docker-composer.yml are responsible to renew the certificate.<br>
<br>
Maybe you have to set the DNS records <b>A</b> and <b>AAAA</b> in you domain. If you are testing, you can use the https://www.dynu.com/. It's a free DNS that you can set the DNS records.<br>
<br>
The files 'init-letsencrypt.sh' and 'data/nginx/app.conf' were caught from Philipp Medium page at https://pentacent.medium.com/nginx-and-lets-encrypt-with-docker-in-less-than-5-minutes-b4b8a60d3a71<br>
<br>
Credits to Phillip https://pentacent.medium.com