# # DevOps For Backend Developer
---
Lộ trình khoá học được xây dựng trên một lộ trình tutorial từ các source code backend (Go và Node), frontend (React). Các học viên sẽ được trải nghiệm từng bước triển khai các công cụ thông dụng trong DevOps để triển khai và vận hành các service một cách hiệu quả nhất.
- Docker & Kubernetes (k8s) on AWS.
- Fluentd (Log collector).
- Monitoring (Grafana + Prometheus).
- CI & CD.
- Logging (Grafana Loki).

**TOPIC:**
- ĐỊNH HƯỚNG & CHIA SẺ VỀ DEVOPS [[#TOPIC 1 ĐỊNH HƯỚNG & CHIA SẺ VỀ DEVOPS]]
- DOCKER CƠ BẢN ĐẾN NÂNG CAO [[#TOPIC 2 DOCKER CƠ BẢN ĐẾN NÂNG CAO]]
- DOCKER COMPOSE [[#TOPIC 3 DOCKER COMPOSE]]
- PROMETHEUS & GRAFANA: MONITORING & THEO DÕI METRIC [[#TOPIC 4 PROMETHEUS & GRAFANA MONITORING & THEO DÕI METRIC]]
-  FLUENTD: LOG COLLECTOR [[#TOPIC 5 FLUENTD LOG COLLECTOR]]
- CI/CD - GITHUB ACTION [[#TOPIC 6 CI/CD - GITHUB ACTION]]
- Kubernestes [[#TOPIC 7 Kubernestes]]
- Kubernetes on Cloud [[#TOPIC 8 Kubernetes on Cloud]]

---
## Chương trình học DevOps

## TOPIC 1:  ĐỊNH HƯỚNG & CHIA SẺ VỀ DEVOPS
- Tổng quan về DevOps.
- Định hướng, mục tiêu phát triển trong ngành.
- Các công việc hằng ngày của một DevOps.
- Cơ hội nghề nghiệp, tiềm năng phát triển hiện tại và tương lai.
- Chia sẻ kinh nghiệm thực tế khi làm DevOps.
 ![[DEVOPS-01.png]]
---

## TOPIC 2: DOCKER CƠ BẢN ĐẾN NÂNG CAO
- Tìm hiểu các thành phần quan trọng của Docker: Container, Image, Network, Volume, Docker Registry.
- Sử dụng Container để khởi tạo service.
- Tạo Image từ Container.
- Automation để tạo image từ Dockerfile.
- Backup và migrate data của service.
- Chia sẻ và dùng lại container image.
- **Practice: Deploy source Backend (Golang, Nodejs) & Frontend (Reactjs).**
- **Practice: Thiết lập Network để Frontend và Backend có thể giao tiếp với nhau.**
- **Practice: Sử dụng volume để backup data.**
- **Practice: Từ Container Frontend và Backend đã thiết lập trước đó, tạo thành Image.**

![[Docker-01.png | 600]]

---

## TOPIC 3: DOCKER COMPOSE
- Tìm hiểu về Docker Compose và các câu lệnh cơ bản.
- Thiết lập các service trong file Docker Compose.
- Sử dụng câu lệnh để build và run các service.
- Practice: Thiết lập file Docker Compose từ source Frontend và Backend đã có.
- Practice: Sử dụng câu lệnh Docker Compose để chạy nhiều Container cùng một thời điểm.
![[Docker -compose-01.png | 600]]

---
## TOPIC 4: PROMETHEUS & GRAFANA: MONITORING & THEO DÕI METRIC
- Thiết lập và cài đặt Prometheus, Grafana.
- Cấu hình **Scrape** cho Prometheus để **collect metrics** từ các **Node Exporter**.
- Tìm hiểu các câu **Query trong Grafana** và sử dụng để **Query Metrics** từ Prometheus và build **Dashboard** để **Monitor**.
- Practice: sử dụng Docker để chạy Prometheus, Grafana và khởi tạo các file config.
- Practice: chạy Node Exporter, Database Exporter để tạo metrics service và database từ Docker.
- Practice: sử dụng Docker chạy Node Exporter, Database Exporter để tạo metrics cho service và database.
- Practice: cài đặt Prometheus để Collector Metrics từ các service đang expose.
- Practice: sử dụng Grafana để query metrics và hiển thị trên UI.

![[Grafana-01.png | 600]]

![[CPU-Network-01.png | 600]]

![[Metric-Process-01.png | 600]]

![[Usage-System-01.png | 600]]

---

## TOPIC 5: FLUENTD: LOG COLLECTOR
- Thiết lập và cài đặt **EFK (Elasticsearch, Fluentd và Kibana)**.
- Sử dụng Fluentd để **Collector Log** từ các service và gửi về Elasticsearch.
- Query từ Elasticsearch và **Data Visualization** trên Kibana.
- **Trace Log Real Time** từ Kibana.
- Practice: Sử dụng Docker để tạo container: Fluentd, Elasticsearch và Kibana.

![[Logging-01.png]]

![[MySQL-Network-Traffic-01.png | 600]]

![[Logging-02.png | 600]]

---

## TOPIC 6: CI/CD - GITHUB ACTION
- Tìm hiểu về GitHooks.
- Thiết lập và cài đặt Jenkins.
- Kết nối Jenkins và GitHooks để thiết lập CI/CD
- Define **Pipeline** bằng **Jenkinsfile**.
- Thiết lập **Agent** và kết nối với Jenkins.
- Thiết lập **Multiple Stages & Steps** trong **Pipeline**.
- Run **Build & Unit Test & Deploy** source code.
- Practice: sử dụng Docker để setup Jenkins.
- Practice: thiết lập connection giữa Jenkins và Githook để trigger event.
- Practice: tạo script trên Jenkins để build và deploy sourcecode khi commit lên Git.

![[CI-CD-Git-Action-01.png | 600]]

---

## TOPIC 7: Kubernestes
- Kiến trúc và các thành phần quan trọng của Kubernestes: Node, Cluster, Pod, Service, Deployment, RBAC,…
- Thiết lập, phân quyền truy cập của User bằng **RBAC**.
- Sử dụng Docker để tạo **Node**, kết nối **Cluster**. Sử dụng Pod để tạo service.
- **Automation Deployment & Scalability** dựa trên traffic của service.
- **Backup & Restore data** hệ thống.
- Practice: cài đặt Minikube để sử dụng K8s trên local machine. Sử dụng Docker tạo Node và kết nối với Cluster.
- Practice: tạo và giả lập môi trường Dev, Staging.
- Practice: phân quyền truy cập môi trường và deploy.
- Practice: sử dụng Pod để khởi tạo service từ source FE và BE đã có.
- Practice: tìm hiểu và sử dụng YAML để run Pod, Deployment,... Thiết lập network để giao tiếp giữa FE và BE.

![[Kubernestes-01.png | 600]]

---

## TOPIC 8: Kubernetes on Cloud
- Sử dụng **IAM** của **AWS** để phân quyền truy cập.
- Tìm hiểu các bước để thiết lập và sử dụng **Kubernetes on Cloud.**
- Sử dụng các công cụ Cloud hỗ trợ để **Monitor** hệ thống.
- Thiết lập **Multiple Environment on Cloud**.
- **Build & Deploy service** lên Cloud.
- Practice: tìm hiểu và sử dụng AWS.
- Practice: thiết lập IAM (Identity and Access Management) để phân quyền.
- Practice: thiết lập Kubernetes trên AWS.
- Practice: sử dụng CRUD bằng AWS CLI để thiết lập các thành phần cần thiết của Kubernetes (Cluster, Node, …)
- Practice: monitoring System thông qua Dashboard AWS cung cấp.

![[Kubernetes-on -Cloud-01.png | 600]]

---
## Tài liệu & Source code
- Slide, tài liệu, Ebook & demo trong khoá học.
- Các script, configuration files trong khoá học.
- Source code Backend: Golang & NodeJS.
- Source code Front-end: ReactJS.

******