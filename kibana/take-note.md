# Take note kibana

---

# ELK stack 

- Gồm bộ 3 phần mềm đi chung với nhau:
  1. **Elasticsearch**: Cơ sở dữ liệu để lưu trữ, tìm kiếm và query log.
  2. **Logstash**: Tiếp nhận log từ nhiều nguồn, sau đó xử lý log và ghi dữ liệu vào Elasticsearch.
  3. **Kibana**: Giao diện để quản lý, thống kê log. Đọc thông tin từ Elasticsearch.
- ELK work:
  1. Log sẽ được đưa đến Logstash (thông qua network protocol)
  2. Logtash sẽ xử lí dữ liệu sau đó ghi xuống Elasticsearch
  3. Kibana sẽ hiển thị log từ Elasticsearch

---

# Kibana

