# Database Microservice

To set up this database on a local MySQL 8.0 instance, you must first give permissions
to a user to access the database. Run the following commands which are tailored
to the DB_CONFIG that was provided to the other microservices.

```
> mysql -u root -p
mysql> CREATE DATABASE IF NOT EXISTS devops_project;
mysql> CREATE USER IF NOT EXISTS 'devops_user'@'localhost' IDENTIFIED BY 'devops_pass';
mysql> GRANT ALL PRIVILEGES ON devops_project.* TO 'devops_user'@'localhost';
mysql> FLUSH PRIVILEGES;
mysql> EXIT;
```

Then, to actually populate your database using the `schema/` folder, run these
Powershell-native commands:

```
> cmd /c "mysql -u devops_user -p devops_project < schema/schema.sql"
> cmd /c "mysql -u devops_user -p devops_project < schema/seed.sql"
```

If prompted for a password, use the password from the DB_CONFIG (likely "devops_pass").

The database service should now be up and running!