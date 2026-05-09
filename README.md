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

#### Firewall

Enable firewall: 

```
sudo ufw enable
```

##### Configuration 

https://ubuntu.com/server/docs/how-to/security/firewalls/#open-or-close-a-port

#### AppArmor

https://ubuntu.com/server/docs/how-to/security/apparmor/



### Applications

- 1 application exposed = 1 user

#### Nextcloud


#### CISO Assistant
