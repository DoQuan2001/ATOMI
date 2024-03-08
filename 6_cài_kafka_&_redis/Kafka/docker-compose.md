# CÀI KAFKA.



```

version: "3"

services:

  zookeeper:
    image: 'bitnami/zookeeper:3.7.0'
    ports:
      - '2181:2181'
    environment:
      - ALLOW_ANONYMOUS_LOGIN=yes

  kafka:
    image: 'bitnami/kafka:3.7.0'
    user: root
    ports:
      - '9092:9092'
    environment:
      - KAFKA_BROKER_ID=1
      - KAFKA_LISTENERS=PLAINTEXT://:9092
      - KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://10.33.237.85:9092 # Đổi địa chỉ ip thành máy của mình
      - KAFKA_ZOOKEEPER_CONNECT=zookeeper:2181
      - ALLOW_PLAINTEXT_LISTENER=yes
    volumes:
      - ./data:/bitnami/kafka
    depends_on:
      - zookeeper


```


---

*Tham khảo*

[1] https://www.linkedin.com/pulse/setting-up-kafka-zookeeper-locally-using-docker-nassuf-sefdine-wlaqe/

[2] https://github.com/confluentinc/demo-scene/blob/master/community-components-only/docker-compose.yml#L22-L51


[1] https://topdev.vn/blog/cai-dat-apache-kafka-su-dung-docker-compose/ 