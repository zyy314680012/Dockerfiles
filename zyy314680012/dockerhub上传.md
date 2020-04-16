###### 打包镜像
docker build -t zyy314680012/php56:latest .



###### 登录dockerhub
docker login



###### 推送镜像到dockerhub

docker push zyy314680012/php56:latest