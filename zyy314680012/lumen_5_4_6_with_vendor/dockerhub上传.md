###### 打包镜像
~~~shell
docker build -t zyy314680012/lumen_5_4_6_with_vendor:latest .
~~~



###### 登录dockerhub
~~~shell
docker login
~~~



###### 推送镜像到dockerhub

~~~shell
docker push zyy314680012/lumen_5_4_6_with_vendor:latest
~~~



