# Note

ssh -i "../../sonky.pem" ec2-user@ec2-3-144-152-155.us-east-2.compute.amazonaws.com

## aws docker init

```bash
sudo amazon-linux-extras install docker
sudo service docker start
sudo docker run -d -p 80:80 --rm sonky740/aws-docker
```

## aws docker update

```bash
sudo docker pull sonky740/aws-docker
```

# AWS ECS(Elastic Container Service)

AWS EC2를 이용하여 Docker를 실행할 수 있지만 수동으로 컨테이너를 관리 및 실행해야하는 귀찮음이 있어서 AWS ECS를 이용하여 더욱 쉽게 컨테이너를 관리할 수 있다. 하지만, 비용이 발생한다.

