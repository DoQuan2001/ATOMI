# CÀI ĐẶT REDIS TRÊN UBUNTU.

chạy script sau:



## I. CÀI ĐẶTH REDIS.


```
sudo apt install lsb-release curl gpg

curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list

sudo apt-get update
sudo apt-get install redis


```

## II. TRUY CẬP REDIS.


`redis-cli`: truy cập vào cli của redis


`redis-cli -p <port_number>`: truy cập với port khác.











---

*THAM KHẢO

[1] https://redis.io/docs/install/install-redis/install-redis-on-linux/

