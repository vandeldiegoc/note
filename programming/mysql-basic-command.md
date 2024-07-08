---
id: "1719962483"
aliases: 
tags:
  - mysql
  - commands
---

## Show policy password in mysql

```sql
SHOW VARIABLE LIKE 'validate_password_policy;
```

example:
+------------------------+------------------+
| Variable_name | Value |
+------------------------+------------------+
| validate_password.changed_characte | 0 |
| validate_password.check_user_name  | 1 |
| validate_password.dictionary_file         |    | 
| validate_password.length                      | 8 |
| validate_password.mixed_case_count  | 1 |
| validate_password.number_count         | 1 |
| validate_password.policy | MEDIUM|
| validate_password.special_characte      | 1 |
+------------------------+------------------+

## Enter to mysql with root user

```mysql
mysql  -u root -p
```

## create new user and add permission in mysql

```sql

-- create new user
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';

-- give permission to select database
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';

-- apply permition
FLUSH PRIVILEGES;
```
