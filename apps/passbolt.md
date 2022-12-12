# Passbolt

Passbolt is a free and open-source password manager built for collaboration. Secure, flexible, and automation ready. Trusted by 10,000 organizations, including Fortune 500 companies, newspapers, governments and defence forces.

Project Homepage: https://passbolt.com/

---
## Set Up

### Create admin user

```sh
docker-compose exec passbolt su -m -c "/usr/share/php/passbolt/bin/cake \
                                passbolt register_user \
                                -u <your_email> \
                                -f <first_name> \
                                -l <last_name>\
                                -r admin" -s /bin/sh www-data
```

### Backup options

Backup database container
change database-container to the name of your passbolt database container
and change the backup location

   ```
docker exec -i database-container bash -c \
  'mysqldump -u${MYSQL_USER} -p${MYSQL_PASSWORD} ${MYSQL_DATABASE}' \
  > /path/to/backup.sql
```

### Backup server public and private keys
change passbolt-container to the name of your passbolt container
and change the backup location

   ```
docker cp passbolt-container:/etc/passbolt/gpg/serverkey_private.asc \
    /path/to/backup/serverkey_private.asc
docker cp passbolt-container:/etc/passbolt/gpg/serverkey.asc \
    /path/to/backup/serverkey.asc
```

### Backup The avatars

   ```
docker exec -i passbolt-container \
    tar cvfzp - -C /usr/share/php/passbolt/ webroot/img/avatar \
    > passbolt-avatars.tar.gz
```

