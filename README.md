<p align="center">
    <a href="https://laravel.com" target="_blank">
        <img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo">
    </a>
</p>

# Laravel Docker 
_In this project, my goal was to learn how to run Laravel with Docker. It has since become a solid starting point for anyone looking to set up Laravel in a Dockerized environment for seamless development and deployment_

## **Table of Contents** 📌  
- [Features](#features)  
- [Prerequisites](#prerequisites)  
- [Setup Instructions](#setup-instructions)  
- [Accessing Services](#accessing-services)  
- [Todo](#todo)  
- [Credit](#credit)  

## Features
This starter template includes the following services:
- **Laravel**
- **PHP 8.3**
- **MySQL**
- **phpMyAdmin**
- **Mailpit**
- **Node.js**
- **NPM**
- **Vite**
- **Redis**

## Prerequisites
Ensure you have the following installed on your system:
- [Docker](https://docs.docker.com/engine/install/) (stable version)
- [Docker Compose](https://docs.docker.com/compose/install/#install-compose) (compatible version)

## Setup Instructions

### Initial Setup
Follow these steps the first time you set up the project:
1. Build and launch the Docker containers:
    ```bash
    docker compose up -d --build
    ```
2. Set the correct permissions for phpMyAdmin sessions:
    ```bash
    docker compose exec phpmyadmin chmod 777 /sessions
    ```

3. Modify ownership and permissions for the necessary directories:
    ```bash
    docker compose exec php chown -R www-data:www-data /var/www/storage /var/www/bootstrap/cache
    ```
    ```bash
    docker compose exec php chmod -R 775 /var/www/storage /var/www/bootstrap/cache
    ```
4. Complete the Laravel setup:
    ```bash
    docker compose exec php composer setup
    ```

### Subsequent Starts
For future startups, simply run:
- Start the Docker containers:
    ```bash
    docker compose up -d
    ```

## Accessing Services

### Laravel Application
- **URL**: [http://localhost](http://localhost)

### Mailpit
- **URL**: [http://localhost:8025](http://localhost:8025)

### phpMyAdmin
- **URL**: [http://localhost:8080](http://localhost:8080)
- **Server**: `db`
- **Username**: `data`
- **Password**: `data`
- **Database**: `data`

### Database
- **Driver**: `MySQL`
- **Host**: `localhost`
- **Port**: `3306`
- **Username**: `data`
- **Password**: `data`
- **Database**: `data`

## Handy Laravel Commands
Use these Laravel Artisan commands for common tasks:
- **Show basic information about the app**:
    ```bash
    php artisan about
    ```
- **Clear the configuration cache**:
    ```bash
    php artisan config:clear
    ```
- **Clear the application cache**:
    ```bash
    php artisan cache:clear
    ```
- **Clear all cached events and listeners**:
    ```bash
    php artisan event:clear
    ```
- **Clear the queue**:
    ```bash
    php artisan queue:clear
    ```
- **Clear the route cache**:
    ```bash
    php artisan route:clear
    ```
- **Clear compiled view files**:
    ```bash
    php artisan view:clear
    ```
- **Clear compiled classes**:
    ```bash
    php artisan clear-compiled
    ```
- **Clear cached bootstrap files**:
    ```bash
    php artisan optimize:clear
    ```
- **Clear the scheduler's cached mutex files**:
    ```bash
    php artisan schedule:clear-cache
    ```
- **Flush expired password reset tokens**:
    ```bash
    php artisan auth:clear-resets
    ```

## Todo

- **Improve Runtime Performance**: https://stackoverflow.com/questions/63036490/docker-is-extremely-slow-when-running-laravel-on-nginx-container-wsl2
- **xdebug**
- **composer installation**: Are all lines really needed?


## Credits

This project was inspired by and uses code from the following repositories:

- [laravel](https://github.com/laravel/laravel) by [laravel](https://github.com/laravel)
- [laravel-docker](https://github.com/refactorian/laravel-docker) by [refactorian](https://github.com/refactorian)
