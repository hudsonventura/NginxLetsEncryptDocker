# NginxLetsEncryptDocker
This repo will help and automate to able a SSL with Let's Encrypt on container Docker using docker compose.

#### Begin

For each user session, you need to set some environments vars. The vars will be erased on system restart.<br>
The <b>urldomain</b> will define the url for your site or system<br>
The <b>staging</b> will be used to inform to the Lest's Encrypt if you are in testing mode or prodution mode.For test use 1, and production use 0.<br>
This is necessary because you have just 5 tries to generate a valid certificate for each domain.

```
$ urldomain=your.domain.com
$ staging=1
```
<br>

#### Edit Nginx config file
```
$ nano data/nginx/app.conf
```

```
$ nano data/nginx/app.conf
```

<br>

#### Up with Docker Compose
```
$ sudo docker-compose up
```