# MySQL as on-line feature store

## 1. Preconditions for OS Windows

1. Installed **Docker Desktop with WSL 2**
2. You can test success installation
   - check Docker Desktop, cmd `docker --version`
   - check WSL2, cmd `wsl --status` (expected info 'Default Version: 2')
   - check installed distributions, cmd `wsl -l` (expected info 'docker-desktop' and 'docker-desktop-data')

## 2. Run MySQL (in container)

1. Get image from official source
   - get specific redis image version 7.2 `docker pull mysql:8.3`
   - or get last redis image `docker pull mysql:latest`
   - Note
     - available [versions](https://hub.docker.com/_/mysql)/[tags](https://hub.docker.com/_/mysql/tags)


2. Run new container
   - create container with name 'mlrun-mysql', use image 'mysql:8.3' and open ports 8081:8080
     - `docker run --name mlrun-mysql -p 8081:8080 -d mysql:8.3`
   - or create container with name 'mlrun-mysql', use image 'mysql:latest' and open ports 8081:8080
     - `docker run --name mlrun-mysql -p 8081:8080 -d mysql:latest`

## 3. Use MySQL for tests

 - Update `qgate-sln-mlrun.env`, change setting for `QGATE_MYSQL`
   - see `QGATE_MYSQL = http://localhost:8081`
