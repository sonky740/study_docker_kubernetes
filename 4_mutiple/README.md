# Note

## root

<!-- 따로 버전 -->
<!-- - docker run --name mongodb --rm -d -p 27017:27017 mongo -->

<!-- 통합 버전 -->
<!-- - docker network create goals-net
- docker run --name mongodb --rm -d --network goals-net mongo -->

<!-- 통합 버전 & 지속성 & 보안 & DB 액세스 방지 -->

- docker network create goals-net

<!-- 계정 연결이 안됨 - 왜 안되는지... => 볼륨 data가 남아있어서 안됐던듯 volume 삭제하고 다시 하니까 됨. -->

- docker run --name mongodb --rm -d --network goals-net -v data:/data/db -e MONGO_INITDB_ROOT_USERNAME=sonky740 -e MONGO_INITDB_ROOT_PASSWORD=eqwwr mongo

## backend

<!-- 따로 버전 -->
<!-- - docker build -t goals-node .
- docker run --name goals-backend --rm -d -p 80:80 goals-node -->

<!-- 통합 버전 -->

- docker build -t goals-node .
- docker run --name goals-backend --rm -d -p 80:80 --network goals-net goals-node

## frontend

<!-- 따로 버전 -->
<!-- - docker build -t goals-react .
- docker run --name goals-frontend --rm -it -p 3000:3000 goals-react -->

<!-- 통합 버전 -->

- docker build -t goals-react .
- docker run --name goals-frontend --rm -p 3000:3000 -it goals-react
