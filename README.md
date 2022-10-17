# SQL_Server_Admin
SQL Admin Tutorial

By default, SQL Server provides you with four main systems databases:

# 1. master
# 2. msdb
# 3. model
# 4. tempdb

# Master

The master database stores all the system-level information of an SQL Server instance, which includes:

1. Server configuration settings
2. Logon accounts
3. Linked servers information
4. Startup stored procedure
5. File locations of user databases

If the master database is unavailable, the SQL Server cannot start. When you work with the master database, you should:

First, always have a current backup of the master database. If the master database is corrupted, you can restore it from the backup.

Second, back up the master database as soon as possible after the following operations:

a) Creating, modifying, and dropping any database
b) Changing the server configurations
c) Update the logon accounts including adding, removing, and modifying

Third, do not create user objects in the master database.

Finally, do not set the TRUSTWORTHY database property of the master to ON.

Note that if the TRUSTWORTHY database property is ON, the SQL Server will trust the database and the contents within it, which increases the security risk. By default, the TRUSTWORTHY is OFF. More information on the TRUSTWORTHY option.


# MS DB

The msdb is used by the SQL Server Agent for scheduling jobs and alerts. Also, it stores the history of the SQL Agent jobs.

The msdb supports the following:

a) Jobs & alerts
b) Database Mail
c) Service Broker 
d) And the backup & restore history for the databases

# Model
SQL Server uses the model database as the template for creating other databases.

When you create a new database, SQL Server copies the contents of the model database including database options to the new database.

If you modify the model database, all databases that you create afterward will take these changes.

Whenever SQL Server starts, it creates the tempdb from the model database. Therefore, the model database must always exist on the SQL Server.

# tempdb

The tempdb database stores temporary user objects that you explicitly create like temporary tables and table variables. Also, the tempdb stores the internal objects that the database engine creates. For example, the tempdb database stores the immediate sort results for running the queries that include the ORDER BY clause.

SQL Server recreates the tempdb database every time it starts. Since the tempdb is non-permanent storage, you cannot back it up or restore it.

# Summary

SQL Server provides four system databases including master, msdb, model, and tempdb.

The master system database stores system-level information of the SQL server instance.

The msdb database is used by SQL Server Agent for jobs & alerts.

The model database is served as a template for creating other databases.

The tempdb system database stores the temporary objects and is recreated every time the SQL Server starts.
