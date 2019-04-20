# Master

## tags

* [v0.1](/contents/v0_1.md)

* [v0.2](/contents/v0_2.md)


# Develop

# [如何用docker-compose启动环境](contents/use-docker-compose.md)

# How to install

* 第一步 先下载,并将代码copy进相应的数据卷

```
git clone  https://github.com/lushtech/magento2-2.2.7

cp  

#切换到develop分支

git checkout  develop

```
* 第二步 用compose.phar安装依赖

```
# 进入容器php-fpm
# 安装composer.phar

curl -O https://getcomposer.org/download/1.8.4/composer.phar

chmod +x composer.phar

# 编辑授权文件 composer到github上下载东西需要授权

如果是去私有库下载其它插件，需要授权文件。这里并不需要。

# 运行


./composer.phar install

```
* 打开浏览器进行安装








* First step
creat a directory
download composer.phar 
creat an auth.json file

```
mkdir myproject  

cd myproject

curl -O https://getcomposer.org/download/1.8.4/composer.phar


vi auth.json

##add the content below in to auth.json
## the token generaed by github

{

"githubb-oauth": {
                "github.com": "bd0e758aca5f3db94e7d30fedce5b50e589427e4"}


}




```


* second step

run the command  in the directory of myproject

```
./composer.phar create-project lushtech/magento2-2.2.7 mymagento2.2.7 --repository-url http://packages.ucebe.com --no-secure-http



```






* third step

revise the composer.json file


```
#revise 

"name": "lushtech/magento2-2.2.7",

#to


"name": "magento/magento2ce",

```
* fout step


thought browser to install your magento

# [如何用docker-compose启动环境](contents/use-docker-compose.md)
