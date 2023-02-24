# 이미지 생성
FROM node:14

# 작업 디렉토리 설정 (후속 명령이 해당 디렉토리에서 실행할 것을 알림)
WORKDIR /app

# 원하는 경로의 파일들 (Dockerfile은 제외) => 해당 경로로 복사
# COPY <src>... <dest>
# WORKDIR에서 root경로가 /app이므로 "COPY . ./"으로 표현 가능.
COPY package.json /app

# 이미지 생성시 실행할 명령
RUN npm install

# COPY . /app을 "npm install" 뒤로 놓으면서 소스 코드를 변경할 때마다 npm install을 다시하지 않음.
COPY . /app

# 컨테이너 실행시 특정 포트를 개방
EXPOSE 80

# 컨테이너 실행시 실행할 명령
CMD ["node", "server.js"]