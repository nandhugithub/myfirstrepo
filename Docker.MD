yum install docker </br>
systemctl start docker </br>
systemctl status docker </br>

docker hub:

httpd - image

docker pull httpd </br>
ls -lrt </br>
docker image ls </br>
mkdir Dockerfile </br>
docker run -d --name myhttpd -p 8080:80 httpd </br>
docker container ls </br>
docker container exec -it (container id) /bin/bash </br>

Step: 1 Disable selinux </br>
vi /etc/selinux/config SELINUX=disabled </br>

Step: 2 Restart Linux Server

step 3: Check docker service is running </br>
systemctl status docker Start the service if not running </br>
systemctl start docker </br>
systemctl enable docker </br>
 
step 5: create Dockerfile directory under /var/lib/docker </br>
cd /var/lib/docker/Dockerfile </br>
mkdir httpd </br>
cd httpd </br>
touch Mytestfile </br>
vi test_httpd_copy </br>
FROM httpd:latest </br>
COPY Mytestfile . </br>
save this file using :wq and exit </br>

step 6: build new image
docker build -t myhttpd:1 . </br>

step 7: start container
docker run -d -it -p 8086:80 myhttpd:1 </br>

step 8: validate copied file
docker exec -it myhttpd /bin/bash </br>
ls Mytestfile </br>

It will list the copied file.

Like this you can test ubuntu OS along with COPY module in docker file

Test Complete.
