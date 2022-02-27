# NginxLetsEncryptDocker
This repo will help and automate to able a SSL with Let's Encrypt on container Docker using docker compose.
<br>

## Prerequisites
docker, docker-Compose
<br>


## Edit file init-letsencrypt.sh
```bash
$ nano init-letsencrypt.sh
```
Edit the line 8 of file <b>init-letsencrypt.sh</b>. Set the 'woodspop.ddnsfree.com' to your domain name.<br>


## Edit Nginx config
```bash
$ nano data/nginx/app.conf
```
Edit the line 3, 14, 15 and 16 of file <b>data/nginx/app.conf</b> with exataly the same domain name.
<br>


## Permission and firt run to generate the first certificates
```bash
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
Here you can configure Nginx to your pourpose.<br><br>
<br>
<br>
Are you ready? Can we continue? Your website is working ok? So.... let's go.
<br>
<br>
## Edit file init-letsencrypt.sh
```bash
$ nano init-letsencrypt.sh
```
Edit the line 12 of file <b>init-letsencrypt.sh</b> from 'staging=1' to 'staging=0'.
<br>

## Try to generate a valid certificates
```bash
sudo ./init-letsencrypt.sh
```
<br>
If you get some error on generating process, be right that Nginx congis is ok.<br>
Turn staging to 1 in init-letsencrypt.sh to tests.<br>
<br>
<br>

### The valid certificate maybe have some minutes to be really valid.
<br>
<br>
<br>
<br>

# Inform
You can generate just 5 valids certificate from 168 hours. So, if you have some trouble, set the staging (from init-letsencrypt.sh) to 1 until the tests is not finished.<br>
Finished it, you can set staging to 0 again.<br>
<br>
Maybe you have to set the DNS records <b>A</b> and <b>AAAA</b> in you domain. If you are testing, you can use the https://www.dynu.com/. It's a free DNS that you can set the DNS records.<br>
<br>
The files 'init-letsencrypt.sh' and 'data/nginx/app.conf' 
were caught from Philipp Medium page at https://pentacent.medium.com/nginx-and-lets-encrypt-with-docker-in-less-than-5-minutes-b4b8a60d3a71<br>
