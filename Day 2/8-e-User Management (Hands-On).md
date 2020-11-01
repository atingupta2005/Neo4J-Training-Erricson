cypher-shell -u neo4j -p secret

SHOW USERS;

\#Create the user atin in a suspended state and the requirement to
change password.

CREATE USER atin_s

SET PASSWORD \'abc\' CHANGE REQUIRED

SET STATUS SUSPENDED;

SHOW USERS;

\#To set User as Active

CREATE USER atin_a

SET PASSWORD \'abc\' CHANGE REQUIRED

SET STATUS ACTIVE;

SHOW USERS;

\#Reorder the columns using a YIELD clause

\#Filter the results using a WHERE clause to show only the new user

SHOW USERS YIELD user, suspended, passwordChangeRequired, roles

WHERE user = \'atin\';

ALTER USER atin_s

SET PASSWORD \'abc123\' CHANGE **NOT** REQUIRED

SET STATUS ACTIVE;

\#OR

ALTER USER atin_s

SET PASSWORD \'abc123\' CHANGE REQUIRED

SET STATUS ACTIVE

SHOW USERS;

DROP USER atin_s;

\#OR

DROP USER atin_s IF EXISTS;

SHOW USERS;

Role Management
===============

SHOW ROLES;

SHOW ROLE admin PRIVILEGES;

SHOW ROLE PUBLIC PRIVILEGES;

**CREATE ROLE name \[IF NOT EXISTS\] \[AS COPY OF name\]**

CREATE ROLE admin;

CREATE ROLE admin IF NOT EXISTS;

CREATE ROLE admin2 AS COPY OF admin;

SHOW ROLES;

DROP ROLE admin2 IF EXISTS;

\#Assign roles to users.

CREATE USER atin_admin

SET PASSWORD \'abc\' CHANGE REQUIRED

SET STATUS ACTIVE;

**GRANT ROLE name\[, \...\] TO user\[, \...\]**

GRANT ROLE admin TO atin_admin;

### The PUBLIC role

There exists a special built-in role, PUBLIC, which is assigned to all
users. This role cannot be dropped or revoked from any user, but its
privileges may be modified. By default, it is assigned the ACCESS
privilege on the default database.

### Listing roles

SHOW ROLES;

SHOW ALL ROLES;

\#To only show roles that are assigned to users, the command is

SHOW POPULATED ROLES;

\#To see which users are assigned to roles WITH USERS can be appended to
the commands.

SHOW POPULATED ROLES

WITH USERS;

\#It is also possible to filter and sort the results by using YIELD,
ORDER BY and WHERE.

SHOW ROLES YIELD role

ORDER BY role

WHERE role ENDS WITH \'r\';

### Creating roles

CREATE ROLE myrole;

CREATE ROLE myrole_1;

CREATE ROLE myrole_2;

CREATE ROLE myrole_3;

CREATE ROLE mysecondrole AS COPY OF myrole;

SHOW ROLES;

CREATE ROLE myrole IF NOT EXISTS;

CREATE OR REPLACE ROLE myrole;

DROP ROLE mysecondrole;

SHOW ROLES;

DROP ROLE mysecondrole;

DROP ROLE mysecondrole IF EXISTS;

CREATE USER atin SET PASSWORD \'abc\' CHANGE REQUIRED SET STATUS ACTIVE;

CREATE USER atin_1 SET PASSWORD \'abc\' CHANGE REQUIRED SET STATUS
ACTIVE;

CREATE USER atin_2 SET PASSWORD \'abc\' CHANGE REQUIRED SET STATUS
ACTIVE;

CREATE USER atin_3 SET PASSWORD \'abc\' CHANGE REQUIRED SET STATUS
ACTIVE;

GRANT ROLE myrole TO atin;

SHOW USERS;

SHOW ROLES;

GRANT ROLES myrole_1, myrole_2 TO atin_1, atin_2, atin_3;

SHOW POPULATED ROLES WITH USERS WHERE role STARTS WITH \'my\';

REVOKE ROLE myrole_1 FROM atin_1;

SHOW POPULATED ROLES WITH USERS WHERE role STARTS WITH \'my\';

REVOKE ROLES myrole_1, myrole_2 FROM atin_1, atin_2, atin_3;

SHOW POPULATED ROLES WITH USERS;
