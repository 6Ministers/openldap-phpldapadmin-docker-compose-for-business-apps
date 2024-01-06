# Installing OpenLDAP+PhpLdapAdmin with docker-compose.

## Quick Installation

**Before starting the instance, direct the domain (subdomain) to the ip of the server where OpenLDAP+PhpLdapAdmin will be installed!**

## 1. OpenLDAP+PhpLdapAdmin Server Requirements
From and more
- 2 CPUs
- 2 RAM 
- 10 Gb 

Run for Ubuntu 22.04

``` bash
sudo apt-get purge needrestart
```

## 2.Install docker and docker-compose:

``` bash
curl -s https://raw.githubusercontent.com/6Ministers/openldap-phpldapadmin-docker-compose-for-business-apps/master/setup.sh | sudo bash -s
```

## 3.Download OpenLDAP+PhpLdapAdmin instance:


``` bash
curl -s https://raw.githubusercontent.com/6Ministers/openldap-phpldapadmin-docker-compose-for-business-apps/master/download.sh | sudo bash -s ldap
```

If `curl` is not found, install it:

``` bash
$ sudo apt-get install curl
# or
$ sudo yum install curl
```

Go to the catalog

``` bash
cd ldap
```


To change the domain in the `Caddyfile` to your own

``` bash
https://ldap.your-domain:443 {
    reverse_proxy :8080
 #   tls admin@example.org
	encode zstd gzip

...	
}
```

Change the data in docker-compose.yml

Password

``` bash
LDAP_ADMIN_PASSWORD: "adminldap"
```

Specify your domain name

``` bash
domainname: "domain.com" # important: same as hostname
hostname: "domain.com"
```


## 5.Run OpenLDAP+PhpLdapAdmin:

``` bash
docker-compose up -d
```

Then open `https://ldap.domain.com:` to access OpenLDAP+PhpLdapAdmin


Access data

``` bash
Login: cn=admin,dc=domain,dc=com
Password: adminldap # If you haven't changed it
```


## OpenLDAP+PhpLdapAdmin container management

**Run**:

``` bash
docker-compose up -d
```

**Restart**:

``` bash
docker-compose restart
```

**Restart**:

``` bash
sudo docker-compose down && sudo docker-compose up -d
```

**Stop**:

``` bash
docker-compose down
```

## Documentation
