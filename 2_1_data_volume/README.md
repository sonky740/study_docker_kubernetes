# Note

컨테이너와 이미지와 로컬 파일 시스템 간에는 연결되어 있지 않음.  
이를 해결하기 위해 Volumes을 사용함.

## docker volume ls

volume 목록을 확인

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
