# Note

컨테이너와 이미지와 로컬 파일 시스템 간에는 연결되어 있지 않음.  
이를 해결하기 위해 Volumes을 사용함.

## docker volume ls

volume 목록을 확인

## docker volume create [VOL_NAME]

volume 생성  
네임드 볼륨에 사용할 수 있다.

## docker volume inspect [VOL_NAME]

volume 정보 확인

## docker volume rm [VOL_NAME]

volume 삭제 `docker volume prune`로 전체 삭제 가능

## docker -v [CONTAINER_PATH]

익명 볼륨을 컨테이너에 마운트

## docker -v [VOL_NAME]:[CONTAINER_PATH]

네임드 볼륨을 컨테이너에 마운트

## docker -v [VOL_NAME]:[CONTAINER_PATH] -v [HOST_PATH]:[CONTAINER_PATH]

네임드 볼륨을 바인드 마운트  
windows인 경우 [HOST_PATH]를 `D:\\~~\~~\` 형식으로 지정해야 함.  
근데 git bash에서는 안되고 powershell을 써야 함.

## docker -v [VOL_NAME]:[CONTAINER_PATH] -v [HOST_PATH]:[CONTAINER_PATH] -v [CONTAINER_PATH]

네임드 볼륨을 바인드 마운트하고 익명 볼륨 지정  
node_modules때문에 익명 볼륨을 지정해야 함. ex) docker run -d -p 3000:80 --rm
--name feedback-app -v feedback:/app/feedback -v
"D:\\code\study_docker_kubernetes\2_1_data_volume\:/app" -v /app/node_modules
feedback-node:volumes

## docker -v [HOST_PATH]:[CONTAINER_PATH]:ro

익명 볼륨을 읽기 전용으로 바인드 마운트

## docker --env [ENV_NAME]=[ENV_VALUE]

컨테이너에 환경변수를 지정  
`-e [ENV_NAME]=[ENV_VALUE]` 로도 가능  
`--env-file [FILE_PATH]` 로도 가능

## docker build --build-arg [ARG_NAME]=[ARG_VALUE]

build할 때 환경변수 인자를 지정 (ARG)
