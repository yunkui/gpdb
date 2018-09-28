# User and permission management {#concept_gbr_cty_52b .concept}

You can do the [user management](#) and [permission management](#) to secure your HybridDB for PostgreSQL databases. This documents describes the corresponding methods.

## User management {#user .section}

During an instance creation, the system requires you to specify an initial user name and password. This initial user is the “root user”. After the instance is ready, you can connect to the database with this root user account. You can view the information of all the users by running the `\du+` command after you connect to the database using [psql](http://gpdb.docs.pivotal.io/4380/client_tool_guides/client/unix/psql.html) \(a client tool of PostgreSQL or Greenplum\). Refer to the following example:

**Note:** Some other internal management users will also be created apart from the root user.

```
postgres=> \du+
                                List of roles
  Role name   |            Attributes             | Member of |  Description
--------------+-----------------------------------+-----------+---------------
 root_user    |                                   |           | rds_superuser
 ...
```

HybridDB for PostgreSQL does not enable the super user permission, but offers a corresponding role of RDS\_SUPERUSER, which is consistent with the permission system in ApsaraDB for RDS \(PostgreSQL\). Therefore, the root user \(such as the root\_user in the preceding example\) has the RDS\_SUPERUSER permission. You can only identify this permission attribute by viewing the user description.

The root user has the following permissions:

-   CREATEROLE, CREATEDB and LOGIN permissions, not including the SUPERUSER permission. You can use the root user account to create databases and users.

-   View and modify the data tables of other non-super users and perform actions such as SELECT, UPDATE, DELETE, and changing Owner.

-   View the connection information of other non-super users, cancel the SQL statement, and terminate the connection.

-   Run the CREATE EXTENSION and DROP EXTENSION commands to create and delete extensions.

-   Create other users with the RDS\_SUPERUSER permission. For example,

    ```
    CRATE ROLE root_user2 RDS_SUPERUSER LOGIN PASSWORD 'xyz' ;
    ```


## Permission management {#permission .section}

You can manage permissions at the database, schema and table levels. For example, if you want to grant the reading permission of a table to a user and revoke the modification permission, you can use the following example:

```
GRANT SELECT ON TABLE t1 TO normal_user1;
REVOKE UPDATE ON TABLE t1 FROM normal_user1;
REVOKE DELETE ON TABLE t1 FROM normal_user1;
```

## Reference { .section}

For more specific user and permission management methods, see [Managing Roles and Privileges](http://gpdb.docs.pivotal.io/4380/admin_guide/roles_privs.html).

