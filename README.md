# OpenLDAP
OpenLDAP + phpldapadmin (Docker / Docker Compose)

> R.H (Ram.Hakimi@gmail.com)
>



#### OpenLDAP

###### Base Image:

```bash
osixia/openldap:latest
```

###### Port:

```bash
- "389:389"
- "636:636"
```

###### Volumes:

```bash
- ./data/certificates:/container/service/slapd/assets/certs
- ./data/slapd/database:/var/lib/ldap
- ./data/slapd/config:/etc/ldap/slapd.d
```

###### Environment:

```bash
- LDAP_ORGANISATION=<ORGANISATION>
- LDAP_DOMAIN=<DOMAIN>
- LDAP_ADMIN_USERNAME=<USER>
- LDAP_ADMIN_PASSWORD=<PASSWORD>
- LDAP_CONFIG_PASSWORD=<PASSWORD>
- "LDAP_BASE_DN=dc=<DOMAIN>,dc=<SUFFIX>"
- LDAP_TLS_CRT_FILENAME=server.crt
- LDAP_TLS_KEY_FILENAME=server.key
- LDAP_TLS_CA_CRT_FILENAME=<DOMAIN>.ca.crt
- LDAP_READONLY_USER=true
- LDAP_READONLY_USER_USERNAME=<USER>
- LDAP_READONLY_USER_PASSWORD=<PASSWORD>
```



#### phpLDAPadmin

###### Base Image:

```bash
osixia/phpldapadmin:latest
```

###### Port:

```bash
- "80:80"
```

###### Environment:

```bash
- PHPLDAPADMIN_LDAP_HOSTS=openldap
- PHPLDAPADMIN_HTTPS=false
```

