# MySQL basics

```bash
# Sign in db with root user
sudo mysql –u root –p
```

```sql
-- Create new user on host and password 
CREATE USER 'username'@'host' IDENTIFIED BY 'password';
```

If you plan to use database with a PHP application — phpMyAdmin, for example — you may want to create a user that will authenticate with the older, though still secure, mysql_native_password plugin:
```sql
CREATE USER 'sammy'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
``` 
If you aren’t sure, you can always create a user that authenticates with caching_sha2_plugin and then ALTER it later on with this command:
```sql
ALTER USER 'sammy'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```