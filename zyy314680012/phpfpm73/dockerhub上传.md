###### 打包镜像
~~~shell
docker build -t zyy314680012/phpfpm73:latest .
~~~



###### 登录dockerhub
~~~shell
docker login
~~~



###### 推送镜像到dockerhub

~~~shell
docker push zyy314680012/phpfpm73:latest
~~~

