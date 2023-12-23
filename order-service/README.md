## Running MySQL with Docker

To spin up a MySQL container with a specified username and password, use the following command:

```bash
docker run --name mysql-container \
-p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=my-secret \
-d mysql
```    
    
### To access the MySQL server and create user:

```bash
// exec into mysql container
docker exec -it mysql-container mysql -u root -p

// Creating Database
CREATE DATABASE `order-service`;
USE `order-service`

DROP USER admin@localhost;
FLUSH PRIVILEGES;
CREATE USER 'orderApp'@'localhost' IDENTIFIED BY 'orderAppPass';
GRANT ALL PRIVILEGES ON `order-service`.* TO 'orderApp'@'localhost';
FLUSH PRIVILEGES;

SHOW GRANTS FOR 'orderApp'@'localhost';


```