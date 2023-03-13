# Note

minikube start --driver=docker

## kubectl create deployment [NAME] --image=[IMAGE]

쿠버네틱스 객체 생성

## kubectl get deployments

쿠버네틱스 객체 조회

## kubectl get pods

쿠버네틱스 포드 조회

## kubectl delete deployment [NAME]

쿠버네틱스 객체 삭제

## minikube dashboard

쿠버네틱스 대시보드 접속

## kubectl expose deployment [NAME] --type=LoadBalancer --port=8080

쿠버네틱스 서비스 생성  
--type=LoadBalancer: 들어오는 트래픽을 모든 pod에 분산

## minikube service [NAME]

쿠버네틱스 서비스 접속

## kubectl scale deployment/[NAME] --replicas=3

쿠버네틱스 객체 스케일링  
--replicas=3: 동일한 pod 3번 실행

## kubectl set image deployment/[NAME] [NAME]=[IMAGE] 

쿠버네틱스 업데이트