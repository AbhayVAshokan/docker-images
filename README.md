# Commands to run Dockerfiles

### **AWS Elastic Beanstalk Command Line Interface** <br>
```bash
docker build -t aws-ebcli aws-ebcli --no-cache
```

### **Apache server with php and mysql** <br>
```bash
cd apache_mysql
docker-compose up --build
```

### **Common Docker commands**
1. **docker ps**: Lists all running docker containers
2. **docker ps -a**: Lists all docker containers
3. **docker images**: Lists all images
4. **docker-compose up**: Build containers from the docker-compose.yml file
5. **docker-compose down**: Stop and remove all containers created by docker-compose.yml file
6. **docker system prune**: Removes all stopped containers, unused networks, dangling images, dangling build cache.