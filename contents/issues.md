## issue1 unknow version
what: 
* show "unknow version"
* the check redlines show "php version is."

The install cant continue via the browser,but can continue via the commandline.

But , after installed via the commandline, cant show the version in correct.

when: install 

where: magentoce2.2.7 version

snapshot:

reproduce:


solution:

* The cause of the matter

In the composer.json file which localed in the root directory of magento, the name must be :

```
 "name": "magento/magento2ce",

```

but in my composer.json file , because I  use a private repository ,it is:

```

"name": "lushtech/magento2-2.2.7",

```

* How to solve

Change the composer.json file 's field :


```

"name": "lushtech/magento2-2.2.7",

```
to

```
 "name": "magento/magento2ce",

```
and then the all things will be ok.
