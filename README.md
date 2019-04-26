为了方便部署Laravel，使用docker-compose配置环境。上线时，只需要几行命令，就可以很快部署好环境。
## 项目说明：
- 各种源使用国内镜像
- 使用alpine为linux基础
- laravel环境PHP依赖最小化安装
- 各种依赖程序版本使用最新的稳定版
## 相关版本
- docker compose file version 3
- PHP 7.3
- MySQL 5.7
- Nginx stable

## 安装环境
- docker 1.13.0+
- docker-compose 建议使用最新版

## 使用
```
git clone git@github.com:kyronbao/laravel-docker-compose.git
```
clone laravel项目用来测试
```
git clone git@github.com:laravel/laravel.git laravel-demo

```

复制.docker目录和docker-compose.yml到项目根目录
```
cp -r laravel-docker-compose/.docker laravel-demo \
&& cp laravel-docker-compose/docker-compose.yml laravel-demo \
&& cd laravel-demo
```

配置数据库
```
cp .env.example .env
```
配置下列项
```
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel_docker_compose
DB_USERNAME=root
DB_PASSWORD=secret
```
安装laravel
```
docker-compose run --rm --no-deps app composer install -vvv
docker-compose run --rm --no-deps app php artisan key:generate
```
--no-deps指启动当前服务时不启动其他依赖的服务

修改storage权限

## 启动docker-compose
提示：如果主机端口占用8000，3306，需先停止
```
docker-compose up -d
```
现在，是不是可以在 http://localhost:8000 看到熟悉的画面了，欢迎star一个
## 其他命令
```
docker-compose down # 停止服务
docker exec -ti db sh   # 进入数据库容器：可以创建数据库
docker exec -ti app sh  # 进入容器：可以运行artisan命令 
```


