# SETUP SQL DEVELOPER TRÊN UBUNTU.





---

## BƯỚC 1: TẢI VỀ BẢN KAFKA

LINK TẢI: https://kafka.apache.org/downloads




```
#GIẢI NÉN.

tar -xzf kafka*.tgz


#DI CHUYỂN VÀO /HOME/KAFKA.
sudo mv kafka*src /home/kafka



```


## BƯỚC 2: CẤU HÌNH KAFKA.


1 file cấu hình server của kafka ở đường dẫn /etc/systemd/system/kafka.service

```
sudo sh -c 'cat <<EOF > /etc/systemd/system/kafka.service

[Unit]

Description=Apache Kafka Server

Documentation=http://kafka.apache.org/documentation.html

Requires=zookeeper.service

[Service]

Type=simple

Environment="JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64"

ExecStart=/home/kafka/bin/kafka-server-start.sh /home/kafka/config/server.properties

ExecStop=/home/kafka/bin/kafka-server-stop.sh

Restart=on-abnormal

[Install]

WantedBy=multi-user.target


EOF'


```


## BƯỚC 3: CẤU HÌNH ZOOKEPPER.

Kafka sử dụng Zookeeper để quản lý cluster state

1 file cấu hình server của Zookeeper ở đường dẫn /etc/systemd/system/zookeeper.service


```
sudo sh -c 'cat <<EOF > /etc/systemd/system/zookeeper.service

[Unit]
 
Description=Apache Zookeeper server
 
Documentation=http://zookeeper.apache.org
 
Requires=network.target remote-fs.target
 
After=network.target remote-fs.target
 
[Service]
 
Type=simple
 
ExecStart=/home/kafka/bin/zookeeper-server-start.sh /home/kafka/config/zookeeper.properties
 
ExecStop=/home/kafka/bin/zookeeper-server-stop.sh
 
Restart=on-abnormal
 
[Install]
 
WantedBy=multi-user.targe

EOF'

```


## BƯỚC 4: KHỞI ĐỘNG KAFKA VÀ ZOOKEPER.


```

#RELOAD
sudo systemctl daemon-reload


#KHOI DONG ZOOKEPER

sudo systemctl enable zookeeper
sudo systemctl start zookeeper

#KHOI DONG KAFKA.

sudo systemctl enable kafka
sudo systemctl start kafka

#XEM TRANG THAI.


sudo systemctl status kafka

sudo systemctl status zookeeper


```


## SCRIPT NGUYÊN BẢN:


```
#GIAI NEN.

tar -xzf kafka*.tgz


#DI CHUYỂN VÀO /HOME/KAFKA.
sudo mv kafka*src /home/kafka


#CAU HINH KAFKA

sudo sh -c 'cat <<EOF > /etc/systemd/system/kafka.service

[Unit]

Description=Apache Kafka Server

Documentation=http://kafka.apache.org/documentation.html

Requires=zookeeper.service

[Service]

Type=simple

Environment="JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64"

ExecStart=/home/kafka/bin/kafka-server-start.sh /home/kafka/config/server.properties

ExecStop=/home/kafka/bin/kafka-server-stop.sh

Restart=on-abnormal

[Install]

WantedBy=multi-user.target


EOF'


#CAU HINH ZOOKEPPER.

sudo sh -c 'cat <<EOF > /etc/systemd/system/zookeeper.service

[Unit]
 
Description=Apache Zookeeper server
 
Documentation=http://zookeeper.apache.org
 
Requires=network.target remote-fs.target
 
After=network.target remote-fs.target
 
[Service]
 
Type=simple
 
ExecStart=/home/kafka/bin/zookeeper-server-start.sh /home/kafka/config/zookeeper.properties
 
ExecStop=/home/kafka/bin/zookeeper-server-stop.sh
 
Restart=on-abnormal
 
[Install]
 
WantedBy=multi-user.target

EOF'


#RELOAD
sudo systemctl daemon-reload


#KHOI DONG ZOOKEPER

sudo systemctl enable zookeeper
sudo systemctl start zookeeper

#KHOI DONG KAFKA.

sudo systemctl enable kafka
sudo systemctl start kafka

#XEM TRANG THAI.


sudo systemctl status kafka

sudo systemctl status zookeeper



```


sudo sh -c 'cat <<EOF > /etc/systemd/system/zookeeper.service

[Unit]
Requires=zookeeper.service
After=zookeeper.service

[Service]
Type=simple
User=kafka
ExecStart=/bin/sh -c '/opt/kafka/bin/kafka-server-start.sh /opt/kafka/config/server.properties > /opt/kafka/logs/start-kafka.log 2>&1'
ExecStop=/opt/kafka/bin/kafka-server-stop.sh
Restart=on-abnormal

[Install]
WantedBy=multi-user.target

EOF'







---

*tham khảo*

https://dev.to/ishakantony/how-to-install-oracle-sql-developer-on-ubuntu-20-04-3jpd



