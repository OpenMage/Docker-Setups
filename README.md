
## Introduction

This repository is a collection of different approaches to use docker and docker-compose together with OpenMage.



## Examples

### static demo

This Setup is approaching setting up a demo store in a simplified approach,
which does not have the intend to be used for development.

```
docker-compose -f compose/static_demo/docker-compose.yaml up
```

## Development snippets

rebuild php-fpm package

```
docker-compose -f compose/static_demo/docker-compose.yaml up --build php-fpm
```
