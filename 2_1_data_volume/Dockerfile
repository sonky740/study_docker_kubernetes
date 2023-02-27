FROM node:14

ARG DEFAULT_PORT=80

WORKDIR /app

COPY package.json /app/

RUN npm install 

COPY . .

# 환경변수 설정
ENV PORT $DEFAULT_PORT

# 환경변수 사용
EXPOSE $PORT

# VOLUME ["/app/feedback"]

CMD ["npm", "start"]
