<h1 align="center">Welcome to Nodejs with Docker 👋</h1>
<p>
  <img alt="Version" src="https://img.shields.io/badge/version-1.0.0-blue.svg?cacheSeconds=2592000" />
  <a href="https://github.com/lberaldodev/node_docker_nginx/blob/master/README.md" target="_blank">
    <img alt="Documentation" src="https://img.shields.io/badge/documentation-yes-brightgreen.svg" />
  </a>
  <a href="#" target="_blank">
    <img alt="License: ISC" src="https://img.shields.io/badge/License-ISC-yellow.svg" />
  </a>
</p>

> Simple NodeJS example with nginx to proxy redirect (by default port 3000 to 8080)

### 🏠 [Homepage](https://github.com/lberaldodev/node_docker_nginx)

## Create the network to use in the both images

```sh
docker network create nodenet
```

## Create your nodejs image

```sh
open server/
```

```sh
docker build -t nodeserver .
```

## Create your nginx image

```sh
open nginx/
```

```sh
docker build -t nginx .
```

## Execute nodejs container and expose port 3000

```sh
docker run -d --network nodenet --name nodeserver -v $(pwd):/var/www/node -p 3000:3000 nodeserver
```

## Execute nginx container and expose port 8080 (after start nodejs container)

```sh
docker run --network nodenet -p 8080:80 nginx
```

## Open your browser

```sh
http://localhost:8080
```

## Author

👤 **Lucas da Silva Beraldo**

* Github: [@lberaldodev](https://github.com/lberaldodev)

## Show your support

Give a ⭐️ if this project helped you!

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_