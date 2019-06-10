
## Introduction

This repository is a collection of different approaches to use docker and docker-compose together with OpenMage.



## Examples

### static demo

This Setup is approaching setting up a demo store in a simplified approach,
which does not have the intend to be used for development.

starting up and installing OpenMage afterwards
```
docker-compose -f compose/static_demo/docker-compose.yaml up -d
docker-compose -f compose/static_demo/docker-compose.yaml exec php-fpm /usr/local/bin/magerun install --dbHost="db" --dbUser="magento" --dbPass="magento" --dbName="magento" --installSampleData=yes --useDefaultConfigParams=yes --magentoVersionByName="openmage-lts-1.9.4.x" --installationFolder="/var/www/" --baseUrl="http://www.openmage.test/"
```

## Development snippets

rebuild php-fpm package

```
docker-compose -f compose/static_demo/docker-compose.yaml up --build php-fpm
```
