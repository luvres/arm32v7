### Alpine
##### Pull image
```
docker pull izone/arm32v7
```

##### run Nginx
```
mkdir $HOME/www

docker run --name Nginx -h nginx \
--link MariaDB:mariadb-host \
-p 80:80 \
-v $HOME/www:/usr/share/nginx/html \
-d izone/arm32v7:nginx
```
##### Enable file browser mode
```
docker exec -ti ftp sed -i '/sendfile/s/on;/on;\n    autoindex       on;/' /etc/nginx/nginx.conf \
&& docker restart ftp
```
#### Build in armhf
```
docker build -t izone/arm32v7 .
```
#### Build QEMU
```
sudo apt-get install qemu-user-static binfmt-support
sudo update-binfmts --enable qemu-arm
sudo update-binfmts --display qemu-arm 
cp /usr/bin/qemu-arm-static .
```
```
```
```
docker build -t izone/arm32v7 .
```

### Nginx in armhf
```
docker pull izone/arm32v7:nginx
```
#### Build in armhf
```
docker build -t izone/arm32v7:nginx ./nginx/
```

### Ubuntu Slim
#### Reference: (https://hub.docker.com/r/arm32v7/ubuntu/)
```
mkdir ROOTFS
cp ubuntu-xenial-core-cloudimg-armhf-root-orig.tar.gz ROOTFS/ubuntu-xenial-core-cloudimg-armhf-root.tar.gz
cd ROOTFS
sudo tar zxf ubuntu-xenial-core-cloudimg-armhf-root.tar.gz
sudo rm usr/share/doc/* usr/share/locale/* usr/share/man/* usr/share/info/* usr/share/lintian/* *.tar.gz -fR
sudo tar zcf ubuntu-xenial-core-cloudimg-armhf-root.tar.gz *
mv ubuntu-xenial-core-cloudimg-armhf-root.tar.gz ..
cd ..
sudo chown -R $USER. ubuntu-xenial-core-cloudimg-armhf-root.tar.gz
sudo rm ROOTFS/ -fR
```

```
docker build -t izone/arm32v7:xenial-slim ./xenial-slim/
```

