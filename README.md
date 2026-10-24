# Spring Boot and MySQL with Docker Compose

## Description

This project runs the completed Spring Guides Java application and a MySQL
database together using Docker Compose.

Original application:
https://github.com/spring-guides/gs-spring-boot

The application reads its database settings from environment variables.
The Dockerfile builds the application with Maven, then runs the resulting JAR.

## Requirements

- Git
- Docker Desktop running Linux containers

Java and Maven run inside the Docker build, so they do not need separate
local installation for this Compose workflow.

## Get the Task 2 branch

While the Pull Request is open:

    git clone --branch docker-compose https://github.com/786-Syed/spring-boot-devops.git
    cd spring-boot-devops

## First-time environment setup

On a fresh clone:

    Copy-Item .env.example .env
    notepad .env

Replace the password placeholders with two different local passwords.
Save the file before starting the containers.

Keep an existing .env file unchanged when restarting this project.
Do not commit .env or share its passwords.

MySQL initialization settings apply when its database volume is first created.
Changing .env later does not automatically change an existing database password.

## Run the application

Start Docker Desktop, then run from the repository root:

    docker compose up --build

This builds the application image and starts MySQL and Spring Boot.
The application waits until the database health check succeeds.

Keep this terminal open while using the application.

## Check the containers

In another terminal, from the repository root:

    docker compose ps

Both app and db should be running. The database should be healthy.

## Basic testing

Open:

    http://localhost:8080

Expected response:

    Greetings from Spring Boot!

Then open:

    http://localhost:8080/actuator/health

Confirm that the db component reports status UP and database MySQL.

The Maven build uses H2 only for automated tests.
The running Compose application uses MySQL.

## Stop and restart

Press Ctrl+C in the terminal running docker compose up to stop the services.

To start them again:

    docker compose up

To run in the background instead:

    docker compose up -d

To stop background services:

    docker compose stop

Database files are stored in the mysql_data volume.

## Evidence

- compose-containers.png
- compose-database-check.png

## Scope

This is a local learning setup.
The application port is bound to localhost.
MySQL is not published on a host port.
Detailed health output is enabled for local verification.
