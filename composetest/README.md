
# Before use docker-compose

we need to exec the following commands:


## redis container

```
docker run -d -p  6379:6379  redis:alpine

```


## web container
```
docker build -t web .

docker run -d -p 5000:5000 web  

```


##  access the web

```
curl  127.0.0.1:5000

```

###  a little bug here 

```
redis.exceptions.ConnectionError: Error 101 connecting to localhost:6379. Network unreachable.
```

经测试，6379端口的redis服务是正常的 ，那么就是 web容器的问题了 ？

关闭 redis 容器试试 !

居然报一样的错误，这就说明是 web 容器无法正常连接redis服务的问题了。

web容器无法正常连接 redis 容器中的服务！！！

何解 ？




# After use docker-compose

simplely one command 
```

docker-compose up

```


Then just:

```
curl  127.0.0.1:5000

```



#  容器之间的连接

容器连接一般用：

```
--link name:alias

```


## 进入 web 容器中并输入 env:

```
env
```


```

REDIS_PORT=tcp://172.17.0.2:6379
REDIS_PORT_6379_TCP_ADDR=172.17.0.2
REDIS_NAME=/boring_knuth/redis
HOSTNAME=4275b21f2e71
SHLVL=1
PYTHON_PIP_VERSION=10.0.1
HOME=/root
REDIS_PORT_6379_TCP_PORT=6379
REDIS_PORT_6379_TCP_PROTO=tcp
REDIS_ENV_REDIS_DOWNLOAD_URL=http://download.redis.io/releases/redis-4.0.9.tar.gz
GPG_KEY=97FC712E4C024BBEA48A61ED3A5CA953F73C700D
REDIS_ENV_REDIS_VERSION=4.0.9
REDIS_PORT_6379_TCP=tcp://172.17.0.2:6379
TERM=xterm
PATH=/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
LANG=C.UTF-8
REDIS_ENV_REDIS_DOWNLOAD_SHA=df4f73bc318e2f9ffb2d169a922dec57ec7c73dd07bccf875695dbeecd5ec510
PYTHON_VERSION=3.4.8
PWD=/code


```

##  cat /etc/hosts

```
172.17.0.2	redis dd305365179c
172.17.0.3	4275b21f2e71


```


#####  Reference:
https://docs.docker.com/compose/gettingstarted/     

