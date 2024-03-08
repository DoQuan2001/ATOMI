# CÀI PLUGIN TRÊN NEXTCLOUD.


## MỤC LỤC:


[I. CÀI PLUGIN](#i-cài-plugin)

[II. TÍCH HỢP API](#ii-tích-hợp-api)


[III. FULL TEXT SEARCH, OCR FILE](#iii-full-text-search-ocr-file)


## I. CÀI PLUGIN.

Nextcloud là một hệ thống lưu trữ và quản lý tệp mã nguồn mở, và có khả năng mở rộng thông qua ứng dụng và plugin. Nextcloud hỗ trợ việc cài đặt các ứng dụng và plugin từ cộng đồng hoặc từ cửa hàng ứng dụng Nextcloud.

Tại phần quản trị ứng dụng, có 3 mục :

- Active App : ứng dụng đã được cài đặt và sử dụng
- Disabled App : ứng dụng đã được cài đặt nhưng chưa sử dụng
- App Bundle : tổ hợp các app được nhóm theo từng mục tiêu sử dụng
- ngoài ra có những plugin khác theo chủ đề có sẵn. 





![hinh ](../images/7.png)



![hinh ](../images/8.png)


---

*Tham khảo*

[1] https://blog.cloud365.vn/nextcloud/nextcloud-p12-cai-dat-quan-ly-cac-ung-dung/

[2] https://najigram.com/2022/02/setup-elasticsearch-7-for-nextcloud/


## II. TÍCH HỢP API.

Nextcloud cho phép tích hợp API vào các ứng dụng khác. 


---

*Tham khảo*


[2] https://nextcloud.com/blog/integrate-nextcloud-into-your-app-with-the-help-of-the-ocs-api-viewer/



## III. FULL TEXT SEARCH, OCR FILE.


### 3.1. ĐẦU TIÊN PHẢI CÀI ELASTIC SEARCH TRƯỚC.

#### CÀI ELASTIC SEARCH

```
sudo apt install openjdk-11-jre

wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -

echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list

sudo apt update && sudo apt install elasticsearch

sudo /usr/share/elasticsearch/bin/elasticsearch-plugin install ingest-attachment

sudo systemctl start elasticsearch
sudo systemctl enable elasticsearch


cat << 'EOF' >> /etc/elasticsearch/elasticsearch.yml

xpack.security.enabled: true
discovery.type: single-node

EOF


sudo systemctl restart elasticsearch


```

#### LẤY MẬT KHẨU.

`sudo /usr/share/elasticsearch/bin/elasticsearch-setup-passwords auto`

![hinh ](../images/11.png)



#### TEST THỬ NHA.

`curl -X GET "http://localhost:9200" -u elastic:PASSWORD`


![hinh ](../images/12.png)



### 3.2. CẤU HÌNH TRÊN NEXTCLOUD KẾT NỐI VỚI ELASTIC SEARCH.

![hinh ](../images/9.png)

#### TRƯỚC TIÊN CẦN VÀO PLUGIN LẤY HẾT PHẦN SEACH VỚI ELASTIC VỀ.



#### TIẾP THEO. TRUY CẬP VÀO SETING ADMINSTRASION CHỌN PHẦN FULL TEXT SEARCH VÀ LÀM NHƯ SAU:


CHỖ ADDRESS THÌ ĐIỀN NHƯ SAU NHA: http://elastic:PASS@localhost:9200

![hinh ](../images/10.png)


![hinh ](../images/13.png)

![hinh ](../images/14.png)

### KIỂM TRA.


![hinh ](../images/15.png)

![hinh ](../images/16.png)







---

*Tham khảo*

[1] https://najigram.com/2022/02/setup-elasticsearch-7-for-nextcloud/

[2] https://help.nextcloud.com/t/help-setting-up-pdf-search-and-ocr/163760


