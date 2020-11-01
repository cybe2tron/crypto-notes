# User Management

**Users and Groups
- users and groups exist for access permission.

- when running a process, it will run as owner of that process.

- the system uses user id(Uid) to manage users.

- the system also uses groups to manage the permission.

- groups are just set of users with permission set by that group.

- groups are identified by group ID

**etc/passwd**
This file shows you a list of users and detailed information about them

> root:x:0:0:root:/root:/bin/bash

1. username
2. user pw
3. user id
4. group id
5. GECOS field : comment about user or account
6. users home dir
7. users shell.

**etc/shadow**
this file stored encrypted password.

> root:MyEPTEa$6Nonsense:15000:0:99999:7:::

1. username
2. encrypted passwrod
3. date of last pw changed.
4. minimum pw age
5. maximum pw age
6. pw warning period : number of days before pwd going to expire
7. pw inactivity period.
8. account expiration date
9. reserved field for future use.


**/etc/groups**

> root:\*:0:pete

1. group name
2. group pw
3. group id
4. list of users

**User management tools**

1. adding user
		sudo useradd bob
2. removing user
		sudo userdel bob
3. changing pw
		passwd bob