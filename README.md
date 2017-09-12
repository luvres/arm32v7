### Ubuntu Slim
#### Reference: (https://github.com/tianon/docker-brew-ubuntu-core)
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

