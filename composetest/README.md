
# Before use docker-compose

we need to exec the following commands:

## web container
```
docker build -t web .

docker run -d -p 5000:5000 web

```


## redis container

```
docker run -d -p  6379:6379  redis:alpine

```

##  access the web

```
curl  127.0.0.1:5000

```



# After use docker-compose

simplely one command 
```

docker-compose up

```


#####  Reference:
https://docs.docker.com/compose/gettingstarted/     

