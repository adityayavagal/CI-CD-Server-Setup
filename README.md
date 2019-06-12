# Setting up SonarQube for continuous inspection of code quality

## PostgreSQL Setup on Ubuntu 18.04

Postgres, is a relational database management system that provides an implementation of the SQL querying language. It is a popular choice for many small and large projects and has the advantage of being standards-compliant and having many advanced features like reliable transactions and concurrency without read locks.

### Step 1 - Installation

```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
```

### Step 2 - Using PostgreSQL  Roles and Databases

Switch to Over to PostgreSQL account using
```bash
sudo -i -u postgres
```
To Enter the shell type
```bash
psql
```

Alternatively, to enter psql Shell directly
```bash
sudo -u postgres psql
```

