# mahadana/mail

A Docker-based [Postfix](http://www.postfix.org/) email server to store or
forward emails.

## Local storage

To store emails locally (e.g., for testing), configure your `docker-compose.yml`
as follows:

```
version: "3"

services:
  mail:
    image: mahadana/mail
    restart: unless-stopped
```

Postfix will listen on port 25. Any emails sent to it will be received and
stored locally.

To read the stored emails:

```
docker-compose exec mail mail
```

## Forward emails

To forward emails to an outgoing email relay (e.g., Gmail, Mailgun, etc.),
configre your `docker-compose.yml` as follows:

```
version: "3"

services:
  mail:
    image: mahadana/mail
    environment:
      MAIL_RELAY_HOST: smtp.server.com
      MAIL_RELAY_PORT: 587
      MAIL_RELAY_USER: me@gmail.com
      MAIL_RELAY_PASSWORD: mysecretpassword
    restart: unless-stopped
```
