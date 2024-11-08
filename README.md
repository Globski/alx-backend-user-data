# Alx Backend User Data - Personal data

## Description

This project focuses on the secure handling of personally identifiable information (PII) and the implementation of robust security measures in back-end systems. It covers key topics such as **Obfuscating PII in Logs**, ensuring that sensitive data such as personal information does not appear in log files, **Password Encryption**, storing and verifying hashed passwords to protect user credentials, **Securing Database Connections**, Using environment variables for secure database authentication to keep sensitive information such as database credentials secure. By implementing a logger that filters out PII and using environment variables for authentication, this project provides a solid foundation for learning how to securely manage sensitive data in a back-end system.

## Features
- How to handle Personally Identifiable Information (PII) securely.
- Techniques for encrypting sensitive data such as passwords.
- How to connect to a secure database while keeping authentication details hidden.

## Project Structure

| **Task**                                   | **Description**                                                                                                    | **Source Code**                                                                                       |
|--------------------------------------------|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| **0. Regex-ing**                            | Write a function called `filter_datum` that obfuscates log fields using regex.                                      | [filtered_logger.py](#)                                                                                |
| **1. Log formatter**                       | Create a `RedactingFormatter` class that filters PII fields in log records.                                        | [filtered_logger.py](#)                                                                                |
| **2. Create logger**                       | Implement `get_logger` function to return a logger with specific formatting using `RedactingFormatter`.             | [filtered_logger.py](#)                                                                                |
| **3. Connect to secure database**          | Implement `get_db` function to connect to a MySQL database using environment variables for credentials.            | [filtered_logger.py](#)                                                                                |
| **4. Read and filter data**                | Implement a `main` function to retrieve and display filtered user data from the database.                          | [filtered_logger.py](#)                                                                                |
| **5. Encrypting passwords**                | Implement a `hash_password` function to hash user passwords using bcrypt.                                          | [encrypt_password.py](#)                                                                               |
| **6. Check valid password**                | Implement `is_valid` function to check if the provided password matches the hashed password.                       | [encrypt_password.py](#)                                                                               |

## Environment

- Python 3.7+
- MySQL or MariaDB
- bcrypt
- mysql-connector-python
- Ubuntu 18.04 LTS (or compatible environment)

## Requirements

- All your files will be interpreted/compiled on Ubuntu 18.04 LTS using python3 (version 3.7)
- All your files should end with a new line
- The first line of all your files should be exactly #!/usr/bin/env python3
- Your code should use the pycodestyle style (version 2.5)
- All your files must be executable
- The length of your files will be tested using wc
- All your modules should have a documentation (python3 -c 'print(__import__("my_module").__doc__)')
- All your classes should have a documentation (python3 -c 'print(__import__("my_module").MyClass.__doc__)')
- All your functions (inside and outside a class) should have a documentation (python3 -c 'print(__import__("my_module").my_function.__doc__)' and python3 -c 'print(__import__("my_module").MyClass.my_function.__doc__)')
- A documentation is not a simple word, it’s a real sentence explaining what’s the purpose of the module, class or method (the length of it will be verified)
- All your functions should be type annotated

## Learning Objectives

By the end of this project, you should be able to:
- Examples of Personally Identifiable Information (PII)
- How to implement a log filter that will obfuscate PII fields
- How to encrypt a password and check the validity of an input password
- How to authenticate to a database using environment variables

## Prototypes Table

| **Prototype**         | **Description**                                                  | **Source Code**                                      |
|-----------------------|------------------------------------------------------------------|------------------------------------------------------|
| `filter_datum`        | Filters and obfuscates fields in log messages using regex.       | [filtered_logger.py](#)                             |
| `RedactingFormatter`  | Custom logging formatter that obfuscates PII fields in logs.     | [filtered_logger.py](#)                             |
| `get_logger`          | Creates and returns a logger with a specific formatting handler. | [filtered_logger.py](#)                             |
| `get_db`              | Returns a database connection using environment variables.      | [filtered_logger.py](#)                             |
| `hash_password`       | Hashes the password using bcrypt with a salt.                   | [encrypt_password.py](#)                            |
| `is_valid`            | Checks if the provided password matches the hashed one.         | [encrypt_password.py](#)                            |


## How to Use

1. **Install Dependencies**:
   Install the required Python packages using `pip`:
   ```bash
   pip install mysql-connector-python bcrypt
   ```
  - `bcrypt` for password hashing and checking.

2. **Set Up MySQL Database**:
   Ensure you have MySQL installed and running. Set up the database and table as described in `main.sql`:
   ```bash
   mysql -u root -p < main.sql
   ```
  - `mysql-connector-python` for database connectivity.
  - Database schema and user data must be set up for testing.

3. **Set Environment Variables**:
   Set the following environment variables before running the application:

   Set the required environment variables for database connection:
   - `PERSONAL_DATA_DB_USERNAME` (default: `root`)
   - `PERSONAL_DATA_DB_PASSWORD` (default: empty string)
   - `PERSONAL_DATA_DB_HOST` (default: `localhost`)
   - `PERSONAL_DATA_DB_NAME` (your database name)

   ```bash
   export PERSONAL_DATA_DB_USERNAME="root"
   export PERSONAL_DATA_DB_PASSWORD="root"
   export PERSONAL_DATA_DB_HOST="localhost"
   export PERSONAL_DATA_DB_NAME="my_db"
   ```

5. **Run the Application**:
   Execute `filtered_logger.py` to filter and redact PII from the database entries:
   ```bash
   python3 filtered_logger.py
   ```
Run the script for each task, ensuring that all functionality works as expected. The `main.py` will execute your code and interact with the loggers and database.

- Encrypts and checks passwords using bcrypt
- Obfuscates PII in log files
- Authenticates with a database using environment variables
  - Always handle sensitive information like passwords securely by hashing them before storing them in a database ensuring that sensitive data is never exposed in logs.
  - Environment variables should be used for storing sensitive data like database credentials to avoid exposing them in the source code.
  - Use logging formats and filters to redact sensitive data when logging.

## Additional Notes

- Identify Personally Identifiable Information (PII) and obfuscate it in logs.
- Implement password hashing and validation using bcrypt.
- Connect to a MySQL database using environment variables for credentials.
- Use logging to filter out sensitive data in a formatted and secure way.

1. **Personally Identifiable Information (PII)**:
    - **Definition**: PII refers to any data that can be used to identify an individual. This includes names, email addresses, phone numbers, Social Security numbers, etc.
    - **Examples**: 
      - Full Name: "John Doe"
      - Email: "johndoe@example.com"
      - Phone Number: "123-456-7890"
      - Address: "123 Main St, Springfield"

2. **Log Filter to Obfuscate PII**:
    - When logging information (for example, in a log file), you must ensure that PII is not exposed in plain text.
    - This can be achieved by masking or obfuscating sensitive fields. For instance:
        - Original: `"Email: johndoe@example.com"`
        - Obfuscated: `"Email: ******@example.com"`
   
3. **Password Encryption and Validation**:
    - **Encryption with bcrypt**: This library helps securely hash and verify passwords. When storing passwords, they should always be hashed (not stored in plain text).
    - To use `bcrypt`:
    
4. **Environment Variables for Database Authentication**:
    - Sensitive credentials (like database passwords) should never be hardcoded in the code. Instead, store them in environment variables for security.
    - **Using environment variables**:
    

### **Examples of Personally Identifiable Information (PII)**:
   - **Names** (full name, maiden name)
   - **Email addresses**
   - **Phone numbers**
   - **Social Security numbers (SSNs)**
   - **Addresses** (home, work)
   - **Credit card information**
   - **Date of birth**
   - **Biometric data** (fingerprints, facial recognition)

### **How to Implement a Log Filter that Will Obfuscate PII Fields**:
   - **Objective**: Prevent PII from being logged, to protect user privacy.
   - **Approach**: Use regular expressions or custom logic to identify PII in logs and replace or mask it.
   - **Example**: Mask email addresses in logs by replacing characters: `"user@example.com"` becomes `"*****@example.com"`.

### **How to Encrypt a Password and Check the Validity of an Input Password**:
   - **Encrypting Passwords**: Use a hashing algorithm like **bcrypt** or **argon2** to hash passwords before storing them in the database.
     - Example: `hashed_password = bcrypt.hashpw(password.encode(), bcrypt.gensalt())`
   - **Checking Validity**: To verify if a given input password matches the stored hash, use the same hashing algorithm to compare the input password with the stored hash.
     - Example: `bcrypt.checkpw(input_password.encode(), stored_hash)`

### **How to Authenticate to a Database Using Environment Variables**:
   - **Objective**: Securely manage database credentials by using environment variables instead of hardcoding them in code.
   - **Approach**: Store sensitive values like database username, password, and host in environment variables, then access them in the application.

## Tasks

## 0. Regex-ing
 
Write a function called `filter_datum` that returns the log message obfuscated:

Arguments:  
- `fields`: a list of strings representing all fields to obfuscate  
- `redaction`: a string representing by what the field will be obfuscated  
- `message`: a string representing the log line  
- `separator`: a string representing by which character is separating all fields in the log line (message)

The function should use a regex to replace occurrences of certain field values.  
`filter_datum` should be less than 5 lines long and use `re.sub` to perform the substitution with a single regex.
```python
bob@dylan:~$ cat main.py
#!/usr/bin/env python3
"""
Main file
"""

filter_datum = __import__('filtered_logger').filter_datum

fields = ["password", "date_of_birth"]
messages = ["name=egg;email=eggmin@eggsample.com;password=eggcellent;date_of_birth=12/12/1986;", "name=bob;email=bob@dylan.com;password=bobbycool;date_of_birth=03/04/1993;"]

for message in messages:
    print(filter_datum(fields, 'xxx', message, ';'))

bob@dylan:~$
bob@dylan:~$ ./main.py
name=egg;email=eggmin@eggsample.com;password=xxx;date_of_birth=xxx;
name=bob;email=bob@dylan.com;password=xxx;date_of_birth=xxx;
bob@dylan:~$
```
**File**: `filtered_logger.py`

---

## 1. Log formatter

Copy the following code into `filtered_logger.py`.

```python
import logging


class RedactingFormatter(logging.Formatter):
    """ Redacting Formatter class """
    
    REDACTION = "***"
    FORMAT = "[HOLBERTON] %(name)s %(levelname)s %(asctime)-15s: %(message)s"
    SEPARATOR = ";"

    def __init__(self):
        super(RedactingFormatter, self).__init__(self.FORMAT)

    def format(self, record: logging.LogRecord) -> str:
        NotImplementedError
```

Update the class to accept a list of strings `fields` as a constructor argument.

Implement the `format` method to filter values in incoming log records using `filter_datum`. Values for fields in `fields` should be filtered.

DO NOT extrapolate `FORMAT` manually. The `format` method should be less than 5 lines long.
```python
bob@dylan:~$ cat main.py
#!/usr/bin/env python3
"""
Main file
"""

import logging
import re

RedactingFormatter = __import__('filtered_logger').RedactingFormatter

message = "name=Bob;email=bob@dylan.com;ssn=000-123-0000;password=bobby2019;"
log_record = logging.LogRecord("my_logger", logging.INFO, None, None, message, None, None)
formatter = RedactingFormatter(fields=("email", "ssn", "password"))
print(formatter.format(log_record))

bob@dylan:~$
bob@dylan:~$ ./main.py
[HOLBERTON] my_logger INFO 2019-11-19 18:24:25,105: name=Bob; email=***; ssn=***; password=***;
bob@dylan:~$
```
**File**: `filtered_logger.py`

---

## 2. Create logger

Use [`user_data.csv`](https://s3.amazonaws.com/alx-intranet.hbtn.io/uploads/misc/2019/11/a2e00974ce6b41460425.csv?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIARDDGGGOUSBVO6H7D%2F20241108%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241108T112927Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Signature=d0af45bcf38bd64b78a301e512b333b18daacd18566ec9788fb300a7fb5866e9) for this task.

Implement a `get_logger` function that takes no arguments and returns a `logging.Logger` object.

The logger should be named "user_data" and only log up to `logging.INFO` level. It should not propagate messages to other loggers. It should have a `StreamHandler` with `RedactingFormatter` as the formatter.

Create a tuple `PII_FIELDS` constant at the root of the module containing the fields from `user_data.csv` that are considered PII. `PII_FIELDS` can contain only 5 fields - choose the right list of fields that are considered as “important” PIIs or information that you must hide in your logs. Use it to parameterize the formatted.
**Tips:**

- [What Is PII, non-PII, and personal data?](https://piwik.pro/blog/what-is-pii-personal-data/)
- [Uncovering Password Habits](https://www.digitalguardian.com/blog)

```python
bob@dylan:~$ cat main.py
#!/usr/bin/env python3
"""
Main file
"""

import logging

get_logger = __import__('filtered_logger').get_logger
PII_FIELDS = __import__('filtered_logger').PII_FIELDS

print(get_logger.__annotations__.get('return'))
print("PII_FIELDS: {}".format(len(PII_FIELDS)))

bob@dylan:~$
bob@dylan:~$ ./main.py
<class 'logging.Logger'>
PII_FIELDS: 5
bob@dylan:~$
```
**File**: `filtered_logger.py`

---

## 3. Connect to secure database

Database credentials should NEVER be stored in code or checked into version control. One secure option is to store them as environment variables on the application server.

In this task, you will connect to a secure Holberton database to read a `users` table. The database is protected by a username and password that are set as environment variables on the server named `PERSONAL_DATA_DB_USERNAME` (set the default as “root”), `PERSONAL_DATA_DB_PASSWORD` (set the default as an empty string), and `PERSONAL_DATA_DB_HOST` (set the default as “localhost”).

The database name is stored in `PERSONAL_DATA_DB_NAME`.

Implement a `get_db` function that returns a connector to the database (`mysql.connector.connection.MySQLConnection` object).

Use the `os` module to obtain credentials from the environment.  
Use the module `mysql-connector-python` to connect to the MySQL database (`pip3 install mysql-connector-python`).
```python
bob@dylan:~$ cat main.sql
-- setup mysql server
-- configure permissions
CREATE DATABASE IF NOT EXISTS my_db;
CREATE USER IF NOT EXISTS root@localhost IDENTIFIED BY 'root';
GRANT ALL PRIVILEGES ON my_db.* TO 'root'@'localhost';

USE my_db;

DROP TABLE IF EXISTS users;
CREATE TABLE users (
    email VARCHAR(256)
);

INSERT INTO users(email) VALUES ("bob@dylan.com");
INSERT INTO users(email) VALUES ("bib@dylan.com");

bob@dylan:~$ 
bob@dylan:~$ cat main.sql | mysql -uroot -p
Enter password: 
bob@dylan:~$ 
bob@dylan:~$ echo "SELECT COUNT(*) FROM users;" | mysql -uroot -p my_db
Enter password: 
2
bob@dylan:~$ 
bob@dylan:~$ cat main.py
#!/usr/bin/env python3
"""
Main file
"""

get_db = __import__('filtered_logger').get_db

db = get_db()
cursor = db.cursor()
cursor.execute("SELECT COUNT(*) FROM users;")
for row in cursor:
    print(row[0])
cursor.close()
db.close()

bob@dylan:~$
bob@dylan:~$ PERSONAL_DATA_DB_USERNAME=root PERSONAL_DATA_DB_PASSWORD=root PERSONAL_DATA_DB_HOST=localhost PERSONAL_DATA_DB_NAME=my_db ./main.py
2
bob@dylan:~$
```
**File**: `filtered_logger.py`

---

## 4. Read and filter data
 
Implement a `main` function that takes no arguments and returns nothing.

The function will obtain a database connection using `get_db` and retrieve all rows in the `users` table and display each row under a filtered format like this:

```
[HOLBERTON] user_data INFO 2019-11-19 18:37:59,596: name=***; email=***; phone=***; ssn=***; password=***; ip=e848:e856:4e0b:a056:54ad:1e98:8110:ce1b; last_login=2019-11-14T06:16:24; user_agent=Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; WOW64; Trident/5.0; KTXN);
```

Filtered fields:  
- name  
- email  
- phone  
- ssn  
- password  

Only your `main` function should run when the module is executed.
```python
bob@dylan:~$ cat main.sql
-- setup mysql server
-- configure permissions
CREATE DATABASE IF NOT EXISTS my_db;
CREATE USER IF NOT EXISTS root@localhost IDENTIFIED BY 'root';
GRANT ALL PRIVILEGES ON my_db.* TO root@localhost;

USE my_db;

DROP TABLE IF EXISTS users;
CREATE TABLE users (
    name VARCHAR(256), 
        email VARCHAR(256), 
        phone VARCHAR(16),
    ssn VARCHAR(16), 
        password VARCHAR(256),
    ip VARCHAR(64), 
        last_login TIMESTAMP,
    user_agent VARCHAR(512)
);

INSERT INTO users(name, email, phone, ssn, password, ip, last_login, user_agent) VALUES ("Marlene Wood","hwestiii@att.net","(473) 401-4253","261-72-6780","K5?BMNv","60ed:c396:2ff:244:bbd0:9208:26f2:93ea","2019-11-14 06:14:24","Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.157 Safari/537.36");
INSERT INTO users(name, email, phone, ssn, password, ip, last_login, user_agent) VALUES ("Belen Bailey","bcevc@yahoo.com","(539) 233-4942","203-38-5395","^3EZ~TkX","f724:c5d1:a14d:c4c5:bae2:9457:3769:1969","2019-11-14 06:16:19","Mozilla/5.0 (Linux; U; Android 4.1.2; de-de; GT-I9100 Build/JZO54K) AppleWebKit/534.30 (KHTML, like Gecko) Version/4.0 Mobile Safari/534.30");

bob@dylan:~$ 
bob@dylan:~$ cat main.sql | mysql -uroot -p
Enter password: 
bob@dylan:~$ 
bob@dylan:~$ echo "SELECT COUNT(*) FROM users;" | mysql -uroot -p my_db
Enter password: 
2
bob@dylan:~$ 
bob@dylan:~$ PERSONAL_DATA_DB_USERNAME=root PERSONAL_DATA_DB_PASSWORD=root PERSONAL_DATA_DB_HOST=localhost PERSONAL_DATA_DB_NAME=my_db ./filtered_logger.py
[HOLBERTON] user_data INFO 2019-11-19 18:37:59,596: name=***; email=***; phone=***; ssn=***; password=***; ip=60ed:c396:2ff:244:bbd0:9208:26f2:93ea; last_login=2019-11-14 06:14:24; user_agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.157 Safari/537.36;
[HOLBERTON] user_data INFO 2019-11-19 18:37:59,621: name=***; email=***; phone=***; ssn=***; password=***; ip=f724:c5d1:a14d:c4c5:bae2:9457:3769:1969; last_login=2019-11-14 06:16:19; user_agent=Mozilla/5.0 (Linux; U; Android 4.1.2; de-de; GT-I9100 Build/JZO54K) AppleWebKit/534.30 (KHTML, like Gecko) Version/4.0 Mobile Safari/534.30;
bob@dylan:~$
```
**File**: `filtered_logger.py`

---

## 5. Encrypting passwords

User passwords should NEVER be stored in plain text in a database.

Implement a `hash_password` function that expects one string argument named `password` and returns a salted, hashed password, which is a byte string.

Use the `bcrypt` package to perform the hashing (`hashpw`).
```python
bob@dylan:~$ cat main.py
#!/usr/bin/env python3
"""
Main file
"""

hash_password = __import__('encrypt_password').hash_password

password = "MyAmazingPassw0rd"
print(hash_password(password))
print(hash_password(password))

bob@dylan:~$
bob@dylan:~$ ./main.py
b'$2b$12$Fnjf6ew.oPZtVksngJjh1.vYCnxRjPm2yt18kw6AuprMRpmhJVxJO'
b'$2b$12$xSAw.bxfSTAlIBglPMXeL.SJnzme3Gm0E7eOEKOVV2OhqOakyUN5m'
bob@dylan:~$
```
**File**: `encrypt_password.py`

---

## 6. Check valid password

Implement an `is_valid` function that expects 2 arguments and returns a boolean.

Arguments:  
- `hashed_password`: bytes type  
- `password`: string type  

Use `bcrypt` to validate that the provided password matches the hashed password.
```python
bob@dylan:~$ cat main.py
#!/usr/bin/env python3
"""
Main file
"""

hash_password = __import__('encrypt_password').hash_password
is_valid = __import__('encrypt_password').is_valid

password = "MyAmazingPassw0rd"
encrypted_password = hash_password(password)
print(encrypted_password)
print(is_valid(encrypted_password, password))

bob@dylan:~$
bob@dylan:~$ ./main.py
b'$2b$12$Fnjf6ew.oPZtVksngJjh1.vYCnxRjPm2yt18kw6AuprMRpmhJVxJO'
True
bob@dylan:~$
```
**File**: `encrypt_password.py`
