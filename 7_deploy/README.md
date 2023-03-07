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