# About this Repo

This is the Git repo of the Docker image for MODX.

## How to use this image

1. Start docker containers
```sh
docker-compose up -d
```

2. Copy MODX code into `html` folder

3. Visit [localhost:8000](http://localhost:8000)


## Run modx only
If you have mysql setup externally and you want to run modx and connect to the external MySQL, follow steps below:

1. build modx
```sh
docker build -t modx_apache ./apache
```
2. Copy MODX code into `html` folder

3. Run `modx_apache` image assuming MySQL installed locally
```sh
docker run -d --network=host --volume "$(pwd)/html:/var/www/html" -e MODX_DB_HOST=127.0.0.1:3306 \
-e MODX_DB_PASSWORD=password \
-e MODX_DB_USER=modx \
-e MODX_DB_NAME=modx \
--name modx_apache modx_apache
```