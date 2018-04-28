
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


#####  Reference:
https://docs.docker.com/compose/gettingstarted/     

