# Using docker compose
 Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a Compose file to configure your application’s services. Then, using a single command, you create and start all the services from your configuration. (from https://docs.docker.com/compose/overview)

To start: docker-compose up
To remove: docker-compose down

When you get this message:

```shell
... (other things...)
** Database 'zabbix' does not exist. Creating...
** Creating 'zabbix' schema in MySQL
** Fill the schema with initial data
** Preparing Zabbix server configuration file
```

>This process can take fill minutes go get ready

# Zabbix lab architecture

* zabbix agent
* zabbix proxy
* zabbix server
* zabbix web server

![Image of zabbix architecture](https://raw.githubusercontent.com/ericogr/docker-zabbix-lab/master/zabbix_architecture.png "Image of zabbix architecture")

## Zabbix web interface

 http://localhost

``` html
username: Admin
password: zabbix
hostname: zabbix-web-server
```

## E-mail interface

http://localhost:8025

 MailHog is an email testing tool for developers.
 * Configure your application to use MailHog for SMTP delivery
 * View messages in the web UI, or retrieve them with the JSON API
 * Optionally release messages to real SMTP servers for delivery

## Zabbix proxy server

``` html
  hostname: zabbix-proxy
```

## Zabbix server

``` html
  hostname: zabbix-proxy
```

## Zabbix agent

``` html
  hostname: zabbix-agent
```

## MariaDB

``` html
  hostname: db
  username: root
  password: admin
```

# Initial configuration

## Add zabbix proxy server
 1. Access web interface: http://localhost
 2. Login (username/password): Admin/zabbix
 3. Click Administration/Proxies
 4. Click "Create Proxy" button
 5. Fill Proxy name with "zabbix-proxy"
 6. Click Add

## Configure e-mail server
 1. Access web interface: http://localhost
 2. Login (username/password): Admin/zabbix
 3. Click Administration/Media types
 4. Click Email to edit current e-mail settings
 5. Fill SMTP server with "mailserver" and SMTP server port with "1025"
 6. Do not touch other parameters and click Update
