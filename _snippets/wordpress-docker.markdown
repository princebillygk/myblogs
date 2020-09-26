---
layout: snippet
title: Wordpress | PHP | MYSQl docker-compose
catagory: Docker
filename: docker-compose.yml
tag: docker-compose.yml docker-compose docker wordpress php mysql
---

```yml
version: "3"
networks:
  access_network:

services:
  # Database - mysql
  db:
    container_name: access_db_mysql
    image: mysql
    command: --default-authentication-plugin=mysql_native_password
    restart: always
    ports:
      - target: 3306
        published: 3306
        protocol: tcp
        mode: host
    volumes:
        - ./db-data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: access1234
      MYSQL_DATABASE: accessdb
      MYSQL_USER: accessuser
      MYSQL_PASSWORD: access4321
    networks:
      - access_network

  # phpmyadmin
  phpmyadmin:
    container_name: access_phpmyadmin
    depends_on:
      - db
    image: phpmyadmin
    restart: always
    ports:
      - 8000:80
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: access1234
    networks:
      - access_network

  # wordpress site
  wordpress:
    container_name: access_wordpress
    depends_on:
      - db
      - phpmyadmin
    image: wordpress
    restart: always
    ports:
      - 8080:80
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: accessuser
      WORDPRESS_DB_PASSWORD: access4321
      WORDPRESS_DB_NAME: accessdb
    
    volumes: 
      - ./wordpress:/var/www/html
    networks:
      - access_network

```