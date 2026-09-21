# Spring Boot DevOps Task

This project packages the completed Spring Guides Java application in Docker.

Original source: https://github.com/spring-guides/gs-spring-boot

## Tools used
Git, Java JDK 25, Maven Wrapper and Docker Desktop with Linux containers.

## Setup
Clone this repository and open Windows PowerShell in its root folder.

## Build with Maven
```powershell
Set-Location .\complete
.\mvnw.cmd clean package
Set-Location ..
```

## Build the Docker image
Run this after the Maven build succeeds:
```powershell
docker build -t spring-app .
```

## Run the container
```powershell
docker run -d --name spring-app-container -p 127.0.0.1:8080:8080 spring-app
```

## Open the application
Visit http://localhost:8080

Expected response: Greetings from Spring Boot!

## Show the running container
```powershell
docker ps --filter "name=spring-app-container"
```

## Restart an existing stopped container
```powershell
docker start spring-app-container
```
