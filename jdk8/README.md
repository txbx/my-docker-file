镜像底包用的 alpine，整合了 bash 和 maven

maven配置文件地址：/txb-docker/build-env/maven/apache-maven-3.8.6/conf/settings.xml

maven仓库地址：/root/.m2/repository



由于github单文件限制100m，本地构建的时候需要根据机器cpu架构自行下载  jdk-8u351-linux-x64.tar.gz  和 jdk-8u351-linux-aarch64.tar.gz 放入对应文件夹下



jdk8在x86和arm64机器上所需要的glibc有所不同，这里打arm64的jdk8镜像的时候查了很多资料，所用到的glibc来自于

https://github.com/Lauri-Nomme/alpine-glibc-xb



这里提供了预构建镜像，你也可以直接拉取这些镜像来使用，而无需在本地构建 Docker 镜像

x86:

```bash
docker pull tanxiubiao/jdk8:0.1
```

arm64:

```bash
docker pull tanxiubiao/jdk8-arm64:0.1
```



