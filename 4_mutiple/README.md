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

<!-- 통합 버전 & 실시간 반영 -->
- docker build -t goals-node .
- docker run --rm --name goals-backend -v logs:/app/logs -v "D:\\code\study_docker_kubernetes\4_mutiple\backend\:/app" -v /app/node_modules -e MONGODB_USERNAME=sonky740 -d -p 80:80 --network goals-net goals-node

## frontend

<!-- 따로 버전 -->
<!-- - docker build -t goals-react .
- docker run --name goals-frontend --rm -it -p 3000:3000 goals-react -->

<!-- 통합 버전 -->

- docker build -t goals-react .
- docker run --name goals-frontend --rm -p 3000:3000 -it goals-react

<!-- 통합 버전 & 실시간 반영 -->

- docker build -t goals-react .
- docker run -e CHOKIDAR_USEPOLLING=true -v "D:\\code\study_docker_kubernetes\4_mutiple\frontend\src\:/app/src" --name goals-frontend --rm -p 3000:3000 -it goals-react

## etc

윈도우에서 실시간 반영을 하려면

backend의 경우 `"scripts": "nodemon -L server.js"`  
frontend의 경우 `docker run -e CHOKIDAR_USEPOLLING=true ...` 을 쓰거나

Windows 시스템에서 Linux 파일 시스템을 사용하도록 설정해야 한다.
https://devblogs.microsoft.com/commandline/access-linux-filesystems-in-windows-and-wsl-2/

## docker-compose

여러개의 도커를 하나의 yaml 파일로 관리할 수 있다.  
더불어 동일한 컴포즈 파일에 정의된 컨테이너는 동일한 네트워크에 연결되고 동일한 볼륨을 공유할 수 있다.

### docker-compose up -d

docker compose를 detached mode로 실행한다.

### docker-compose up --build

강제로 리빌드하고 실행한다.

### docker-compose down -v

docker compose를 종료하고 volume을 삭제한다.