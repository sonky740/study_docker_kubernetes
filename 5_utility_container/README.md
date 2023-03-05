# Note

예를 들어, node를 유틸리티화 시켜서 node를 로컬에 설치하지않고 npm init을 할 수 있다.

## docker run -it -d node

node 컨테이너화

## docker exec -v "local PATH:/app" -it [image ID] npm init

이미지화한 node로 바인드 마운트하여 npm init

## docker-compose run --rm npm init

yaml 파일에 여러 서비스가 있는 경우에 단일 서비스로 실행할 수 있다.