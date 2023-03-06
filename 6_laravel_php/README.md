# Note

## docker-compose up [service]

해당 service만 실행  
`docker-compose up server php mysql`  
docker-compose.yaml에 `depends_on`에 service가 있으면 해당 service도 실행

## docker-compose up --build [service]

변경된 사항이 있는 경우에 이미지를 다시 생성하도록 강제