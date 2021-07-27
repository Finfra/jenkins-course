# Artifactory 설치
* Lab1의 JenkinsInstall 을 실행해 설치하였다면 본 챕터는 진행할 필요 없음.

* 아래의 스크립트를 Artifactory를 운영할 서버에서 실행합니다.(Root 계정에서 실행)
* 스크립트 안에 IP를 지정 후 실행 하세요.
```

curl -s https://get.docker.com/ | sudo sh


echo '
mkdir -p  /artifactory
chmod 777 -R /artifactory

docker rm -f artifactory ;docker run -d        \
   --name artifactory                          \
   -p 8081:8081                                \
   -p 8082:8082                                \
   -v /artifactory:/var/opt/jfrog/artifactory  \
   docker.bintray.io/jfrog/artifactory-oss:latest
    # -v /vagrant/artifactory:/var/opt/jfrog/artifactory \

# docker exec -d artifactory chmod 777 /var/opt/jfrog/artifactory
# docker exec -d artifactory chown -R 1030:1030 /var/opt/jfrog/artifactory
'>/usr/local/sbin/artifactoryReset.sh
chmod +x /usr/local/sbin/artifactoryReset.sh
bash /usr/local/sbin/artifactoryReset.sh


echo '
echo "
172.22.101.101  jenkins1
172.22.101.111  jm1
172.22.101.121  jm2
">> /etc/hosts
'> /tmp/tnowage.sh
docker cp /tmp/tnowage.sh artifactory:/tmp/
docker exec -d --user root artifactory bash /tmp/tnowage.sh
chmod +x /usr/local/sbin/artifactoryReset.sh

ufw allow 8081
ufw allow 8082

```
