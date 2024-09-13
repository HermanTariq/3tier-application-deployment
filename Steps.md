# Steps to install 3-tier application
## React-NodeAPI-Mysql
### Update server
```
 sudo apt-get update
  ```

### Step up nginx 
```
sudo apt install nginx 
Systemctl enable nginx
systemctl status nginx
```

### Clone app in nginx dub

```
cd \var\www
```
* clone app
  
  ```
  git clone http\\app path
  ```
  
### Database MSQL
* Step : 1 Install MYSQL in server
```
sudo apt install mysql-server
sudo mysql_secure_installation

sudo systemctl start mysql
sudo systemctl enable mysql
   ```
* Step : 2 Acess MYSQL
 
  ```
  sudo MYSQL
  ```
  
  *Extra Security-Step*
  
  *If you wann create a user and password for the localhost to enter MYSQL database*

  ```
  sudo mysql
  USE mysql;
  ALTER USER 'root'@'localhost'IDENTIFIED WITH mysql_native_password BY'your_new_password';
  FLUSH PRIVILEGES;
  exit
  sudo mysql -u root -p
  ```
* Step : 3 Creating database
  ```
  create database `devops-db`;
  ```
* Step : 4 Creating a user who have all access to the Database
  ```
  CREATE USER 'devops-user'@'%' IDENTIFIED BY 'qwe123!@#QWE';
  GRANT ALL PRIVILEGES ON `devops-db`.* TO 'devops-user'@'%';
  ```
* Step 5 create tables or import from .sql file
  ```
  use devops-db;

  CREATE TABLE users (
  id int(255) NOT NULL,
  name varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  email varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  work varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL
  ) ; 
  ```
   **Or Import form file .sql**
   ``` 
   sudo mysql -u root -p devops-db < users.sql
   ```

* *tid bid*
  
  *show command is use to table and database in SQL*
```
Show databases;
show table; 
```
   *to exist MYSQL  use* **exit** *key word*.
### Install NodeJS | NPM 
*Before start working on app install all packages on the server*
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
source ~/.bashrc
nvm install 18


curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs


```

### BACKEND

* Step : 1  install npm 
  
  ``` 
  cd /backend
  sudo npm i
  ```
*after npm i you get **node_modules** file*.

 ![Alternative text](images/node%20module%20file.PNG)
* Step : 2 Configure database in index.js file

    ![Alternative text](images/connect%20database%20with%20backend.PNG)

* Step : 3 sudo npm run start 
  
     ```
       sudo npm run  star 
     ```
   *result*

   ![Alt text](images/sudo%20npm%20run%20start.PNG)

* Step:4 for keep runing with the help of porgram manager
  
  ``` 
  sudo pm2 start npm --name "my-backend" -- run start
  ```
  *if the pm2 not working run command*
   ```
   npm install pm2@latest -g
   ```
   *extra important command for pm2*

   ```
   pm2 logs 

   pm2 list  
   ```