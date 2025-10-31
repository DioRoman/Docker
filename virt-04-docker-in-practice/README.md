# 05-virt-04-docker-in-practice

## Задача 1

```sudo -i```

`mkdir Netology`

`cd Netology`

`git clone https://github.com/DioRoman/shvirtd-example-python`

`cd ..`

`docker pull python:3.9-slim`

`touch root/Netology/shvirtd-example-python/Dockerfile.python`
`touch root/Netology/shvirtd-example-python/.dockerignore`
```
echo "FROM python:3.9-slim

COPY . .
RUN pip install -r requirements.txt
CMD [\"python\", \"main.py\"]" >> root/Netology/shvirtd-example-python/Dockerfile.python
```
```
echo "*
!main.py
!requirements.txt" >> root/Netology/shvirtd-example-python/.dockerignore```
```
`docker build -f /root/shvirtd-example-python/Dockerfile.python -t shvirtd-example-python .`

`docker run shvirtd-example-python`

## Задача 2

`yc container registry test`

`docker tag shvirtd-example-python cr.yandex/crptcho4q9mntnhcce91/shvirtd-example-python:new`

`docker push cr.yandex/crptcho4q9mntnhcce91/shvirtd-example-python:new`

![Снимок экрана 2025-05-24 134418](https://github.com/user-attachments/assets/755ca11d-e59a-4e6d-9a19-4f2af8fd1f49)

## Задача 3

`touch /root/Netology/shvirtd-example-python/compose.yaml`

`docker compose -f /root/Netology/shvirtd-example-python/compose.yaml up -d `

`docker exec -ti dio-mysql mysql -uroot -pYtReWq4321`
```
show databases; 
use virtd; 
show tables; 
SELECT * from requests LIMIT 10;
```
![Снимок экрана 2025-05-24 134910](https://github.com/user-attachments/assets/1b935db2-f93a-457d-8bf3-e94f44755d5f)

## Задача 4 

`touch run.sh`

`chmod +x ./run.sh`

`sudo apt install mc -y`
```
echo "#!/bin/bash
git clone https://github.com/DioRoman/shvirtd-example-python.git
mv shvirtd-example-python /opt
docker compose -f /opt/shvirtd-example-python/compose.yaml up -d" >> run.sh
```
`sudo ./run.sh`

`curl -L http://158.160.176.117:8090`

![Снимок экрана 2025-05-24 151302](https://github.com/user-attachments/assets/f47d0699-d48c-4371-a28c-8b495b9ff48f)

## Задача 6

`docker pull hashicorp/terraform:latest`
```
DIVE_VERSION=$(curl -sL "https://api.github.com/repos/wagoodman/dive/releases/latest" | grep '"tag_name":' | sed -E 's/.*"v([^"]+)".*/\1/')
curl -fOL "https://github.com/wagoodman/dive/releases/download/v${DIVE_VERSION}/dive_${DIVE_VERSION}_linux_amd64.deb"
sudo apt install ./dive_${DIVE_VERSION}_linux_amd64.deb
```
`docker run -ti --rm -v /var/run/docker.sock:/var/run/docker.sock wagoodman/dive hashicorp/terraform:latest`

`docker image save -o /tmp/image.tar.gz hashicorp/terraform:latest`

`tar xf /tmp/image.tar.gz`

`cd /tmp/blobs/sha256/`

`tar xf e0f55b34ca5dc362ab5757d39045589d45aaa6ffe70a3bb2d88b2939592a5806`

![Снимок экрана 2025-05-24 160424](https://github.com/user-attachments/assets/e63e6968-8610-4cf9-a743-efc031c0272b)
![Снимок экрана 2025-05-24 165213](https://github.com/user-attachments/assets/f6f49fa6-3ea8-474a-a7af-ef7d8242f871)

## Задача 6.1

`docker run hashicorp/terraform:latest`

`docker ps -a`

`docker cp terraform:/bin/terraform ./terraform`

`ls -all | grep terra`

![Снимок экрана 2025-05-26 220902](https://github.com/user-attachments/assets/01469ac0-829a-4a38-818b-f35e26731c43)


