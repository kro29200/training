# Lab

## Server Ubuntu

https://ubuntu.com/server/docs/how-to/security

### SSH

https://ubuntu.com/server/docs/how-to/security/openssh-server/

#### Add key

Copy public key to server

#### Root

#### Disable root password

```
sudo passwd -l root
```

#### Disable ssh login

File : /etc/ssh/ssh_config
Add line : ``` PermitRootLogin no ```

```
sudo service ssh restart
```

### Configure 

#### Users Management

Rules:

- 1 application exposed = 1 user
- create user with config :
  - no home
  - no passwd user
  - no login user
  - no ssh login


#### Set timezone 

```
sudo timedatectl set-timezone Europe/Paris
```

### Network

Add a Reverse Proxy to expose any applications.

#### Routing

Iptables only because of Docker : https://docs.docker.com/engine/install/ubuntu/#firewall-limitations


##### Configuration 

https://ubuntu.com/server/docs/how-to/security/firewalls/#open-or-close-a-port

#### AppArmor

https://ubuntu.com/server/docs/how-to/security/apparmor/


### Container  (docker)

https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

https://docs.docker.com/engine/install/linux-postinstall/

### Applications

- 1 application exposed = 1 user

#### Nextcloud

##### Run AIO
```bash
# For Linux and without a web server or reverse proxy already in place:
sudo docker run \
  --init \
  --sig-proxy=false \
  --name nextcloud-aio-mastercontainer \
  --restart always \
  --publish 8080:8080 \
  --volume nextcloud_aio_mastercontainer:/mnt/docker-aio-config \
  --volume /var/run/docker.sock:/var/run/docker.sock:ro \
  ghcr.io/nextcloud-releases/all-in-one:latest
```

##### Expose behind RP

https://github.com/nextcloud/all-in-one/blob/main/reverse-proxy.md

#### CISO Assistant
