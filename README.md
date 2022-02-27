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
At this poin you have a invalid certificate genegated, but you already have SSL able at your connection.<br>
Here you can configure Nginx to your pourpose.<br><br>
<br>
<br>
Are you ready? Can we continue? Ok!
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