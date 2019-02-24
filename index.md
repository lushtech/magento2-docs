# Master

## tags

* [v0.1](/contents/v0_1.md)

* [v0.2](/contents/v0_2.md)


# Develop

# How to install

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
