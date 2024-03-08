# CÀI REDIS




## I. CÀI ĐẶT BẰNG DOCKER


```
version: '3.0'
services:
  redis:
    image: redis:7.0.11
    container_name: redis_loyalty
    user: root
    volumes:
      - ./redis.conf:/usr/local/etc/redis/redis.conf
    ports:
      - 6380:6379

```

cần phải có 1 file `redis.conf` nữa nha:


```


```