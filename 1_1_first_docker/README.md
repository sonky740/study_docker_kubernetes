# Note

- 이미지는 읽기/쓰기 액세스 권한이 있는 인스턴스를 실행하는 컨테이너의 템플릿이
  다.
- 여러 컨테이너가 서로 간섭하지 않고 동일한 이미지를 기반으로 할 수 있다.
- 컨테이너는 서로 격리되어 있으며, 디폴트로 공유 데이터나 상태가 없다.
- 이미지의 모든 명령은 캐시 가능한 레이어를 생성하며, 레이어는 이미지 재구축 및
  공유를 위해 사용된다.

## docker run node

최신 버전의 node 이미지를 다운로드 받아서 컨테이너를 생성하고 실행한다.

## docker run -it node

-it 옵션을 주면 컨테이너를 실행하면서 터미널을 연결한다.

## docker build .

현재 디렉토리에 있는 Dockerfile을 읽어서 이미지를 빌드한다.

## docker build -t [NAME]:[TAG] .

이미지를 빌드할 때 이름과 태그를 지정할 수 있다.  
이미지 네임:태그를 지정했다면 `docker run [NAME]:[TAG]` 와 같이 컨테이너를 실행
할 수 있다.

## docker run -p 3000:80 [IMAGE ID]

-p "액세스 하려는 로컬포트:컨테이너 포트"  
컨테이너를 실행(포그라운드 attached)하면서 포트를 연결한다.  
참고로 ID를 입력할 때 앞의 몇 자리만 입력해도 된다. (고유값이라면.)

## docker ps

현재 실행중인 컨테이너를 확인한다.  
-a를 붙이면 모든 컨테이너를 확인한다.

## docker stop [NAMES]

컨테이너를 중지한다.

## docker start [NAMES]

컨테이너를 백그라운드(detached)로 실행한다.  
run과는 다르게 콘솔에는 아무런 출력이 없다.  
`docker run -d [IMAGE ID]` 와 같다. `docker start -a [NAMES]` 는 attached 모드로
실행한다.

## docker attach [NAMES]

detached 모드인 컨테이너에 접속할 수 있다.

## docker logs [NAMES]

컨테이너의 로그를 확인할 수 있다.  
-f 옵션을 주면 실시간으로 로그를 확인할 수 있다.

## docker rm [NAMES]

컨테이너를 삭제한다. 여러개를 삭제하려면 `docker rm [NAMES] [NAMES]` 와 같이 파
싱하면 된다.

## docker rmi [IMAGE ID]

이미지를 삭제한다. 여러개를 삭제하려면 `docker rmi [IMAGE ID] [IMAGE ID]` 와 같
이 파싱하면 된다.

## docker image prune

사용하지 않는 이미지를 전부 삭제한다.

## docker run --rm [NAME]

컨테이너를 실행하고 중지할 때 컨테이너를 자동으로 삭제한다.

## docker image inspect [IMAGE ID]

이미지의 정보를 확인할 수 있다.

## docker cp [OPTIONS] [NAMES]:[PATH] [PATH]

ex) `docker cp dummy/. thirsty_elion:/test` dummy/test.txt  
`docker cp thirsty_elion:/test dummy`를 치면 dummy/test/test.txt가 생성된다.

## docker run --name [NAME] [IMAGE ID]

컨테이너를 실행할 때 이름을 지정할 수 있다.  
로컬에 해당하는 이미지가 존재하지 않으면 docker hub에서 똑같은 이름의 이미지를다
운받아서 실행한다.

## docker tag [name] [name]:[tag]

앞의 이미지를 뒤의 이름:태그로 복사한다.
