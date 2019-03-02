# How to install

## first step
clone the code from the github

change the owner

```
mkdir /var/www/magento

sudo git clone https://github.com/lushtech/magento2.2.7-marketplace.git


sudo mv ./magento2.2.7-marketplace/*    ../magento

sudo mv ./magento2.2.7-marketplace/.*   ../magento

sudo rm -rf magento2.2.7-marketplace

git checkout feature/test-magento2.2.7

cd ..

sudo chown -R www-data:www-data magento

```

## second step


```
sudo docker ps |grep php-fpm

sudo docker exec -it container_php-fpm_id   /bin/bash

cd /var/www/magento

../html/composer.phar   install  #you had put composer.phar and auth.json in /var/www/html directory before 
                                 #run this command.

cd ..

chown -R www-data:www-data magento

```



