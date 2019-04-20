## 如何用docker-composer构建启动环境

### 已有镜像
先拉取已有镜像
```
docker pull harbor-registry.ucebe.com/magento2/mysql5.7:master

docker pull harbor-registry.ucebe.com/magento2/nginx1.9:master

docker pull harbor-registry.ucebe.com/magento2/php-fpm7.0:master


docker pull harbor-registry.ucebe.com/magento2/phpmyadmin:master
```

### 编写docker-compose.yml文件
1：先创建两个数据卷
```
docker volume create magento2-dbdata

docker volume create magento2-data
         

```

2:编写docker-compose.yml文件

要注意此docker-compose版本为2.4
如果docker-compose版本不够高，用以下命令安装
```
#下载
$ sudo curl -L https://github.com/docker/compose/releases/download/1.17.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose

#授权
sudo chmod +x /usr/local/bin/docker-compose

#查看版本信息

sudo docker-compose --version

```

```
version: "2.4"
services:
     phpmyadmin:
       image: harbor-registry.ucebe.com/magento2/phpmyadmin:master
       container_name: phpmyadmin_1
       environment:
          - PMA_ARBITRARY=1
       ports:
          - 8080:80
       links:
         - "db-service"


     db-service:
       image: harbor-registry.ucebe.com/magento2/mysql5.7:master
       container_name: db_1
       environment:
           - MYSQL_ROOT_PASSWORD=magento2
           - MYSQL_DATABASE=magento2
           - MYSQL_USER=magento2
           - MYSQL_PASSWORD=magento2
           - TERM=meh
       ports:
          - 3306:3306
       volumes:
          - magento2-dbdata:/var/lib/mysql
     
     php-fpm-service:
        image: harbor-registry.ucebe.com/magento2/php-fpm7.0:master
        container_name: php-fpm_1
        ports:
          - 9000:9000
        volumes:
          - magento2-data:/var/www/magento
        healthcheck:
             test: "exit 0"

     nginx:
         image: harbor-registry.ucebe.com/magento2/nginx1.9:master
         container_name: nginx_1
         ports:
           - 80:80
         volumes:
           - magento2-data:/var/www
         depends_on:
             php-fpm-service:
               condition: service_healthy
         links:
           - "php-fpm-service"

volumes:
    magento2-dbdata:
            external: true
    magento2-data:
            external: true



```


