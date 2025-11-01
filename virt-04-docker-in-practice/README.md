<img width="874" height="153" alt="447670514-01469ac0-829a-4a38-818b-f35e26731c43" src="https://github.com/user-attachments/assets/492d5a3b-2a0d-4eda-b7ef-a88f5b6a7548" /># 05-virt-04-docker-in-practice

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

<img width="1203" height="215" alt="447259519-755ca11d-e59a-4e6d-9a19-4f2af8fd1f49" src="https://github.com/user-attachments/assets/70ec47e4-4a2a-4269-ac88-f954538919c5" />

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
<img width="707" height="864" alt="447259642-1b935db2-f93a-457d-8bf3-e94f44755d5f" src="https://github.com/user-attachments/assets/b21c0da1-7862-4b25-84b4-9a7d115b0e3b" />

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

<img width="518" height="1030" alt="447260006-f47d0699-d48c-4371-a28c-8b495b9ff48f" src="https://github.com/user-attachments/assets/7bf2e8b7-1bba-4bcc-a1f5-4f3dd6acdc3b" />

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

<img width="2559" height="1279" alt="447260064-e63e6968-8610-4cf9-a743-efc031c0272b" src="https://github.com/user-attachments/assets/5672d7eb-17c9-4729-818c-dedfaedd3369" />

<img width="2150" height="1186" alt="447260092-f6f49fa6-3ea8-474a-a7af-ef7d8242f871" src="https://github.com/user-attachments/assets/4b49d417-5ad9-4310-ba84-ea256fb92ff5" />

## Задача 6.1

`docker run hashicorp/terraform:latest`

`docker ps -a`

`docker cp terraform:/bin/terraform ./terraform`

`ls -all | grep terra`

<img width="874" height="153" alt="447670514-01469ac0-829a-4a38-818b-f35e26731c43" src="https://github.com/user-attachments/assets/abaf66c1-b7c3-4047-80ec-7cb74caf1822" />


