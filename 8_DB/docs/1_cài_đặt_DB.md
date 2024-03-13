# CÀI ĐẶT MYSQL, MARIADB, ORACLEDB BẰNG DOCKER


THAM KHẢO:

[1] MYSQL https://hub.docker.com/_/mysql/

[2] MARIADB https://hub.docker.com/_/mariadb

[3] ORACLEDB 


## 1.1. MYSQL.

```

version: '3.8'

services:
  mysql:
    image: mysql
    restart: always
    container_name: my-mysql
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: my_database
      MYSQL_USER: admin
      MYSQL_PASSWORD: admin
    volumes:
      - mysql_data:/var/lib/mysql
    ports:
      - "3306:3306"

volumes:
  mysql_data:

```


## 1.2. MARIADB.


```

version: '3.8'

services:
  mariaDB:
    image: mariadb:11.0.5
    restart: always
    container_name: my-mariaDB
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: my_database
      MYSQL_USER: admin
      MYSQL_PASSWORD: admin
    volumes:
      - mariaDB_data:/var/lib/mysql
    ports:
      - "3306:3306"

volumes:
  mariaDB_data:


```


## 1.3. ORACALDB.



