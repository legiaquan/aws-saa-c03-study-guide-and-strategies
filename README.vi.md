# Hướng Dẫn Ôn Tập AWS Certified Solutions Architect - Associate (SAA-C03)

## 1. Chiến Lược Làm Bài

- **Phân tích câu hỏi:** Xác định vấn đề cốt lõi, kiến trúc hiện tại (nếu có), và yêu cầu chính.
- **Nhận diện từ khóa:** Các từ khóa trong câu hỏi thường gợi ý giải pháp phù hợp.
- **Ưu tiên các nguyên tắc Well-Architected:** Đáp án đúng thường phù hợp với các nguyên tắc: Vận hành xuất sắc, Bảo mật, Độ tin cậy, Hiệu suất, Tối ưu chi phí.
- **Ưu tiên dịch vụ Managed:** AWS thường ưu tiên dịch vụ được quản lý sẵn để giảm tải vận hành.
- **Cân nhắc trade-off:** Giải pháp thường phải đánh đổi giữa các yếu tố (chi phí, hiệu suất, bảo mật...). Hãy chú ý ưu tiên được nêu trong câu hỏi.

---

## 2. Các Dạng Câu Hỏi Thường Gặp & Pattern Giải Quyết

### 2.1. Giảm Tải Vận Hành / Managed Services

**Từ khóa:** "least operational overhead", "fully managed", "serverless", "no code changes"  
**Giải pháp thường gặp:**  
- **Amazon Athena:** Phân tích log trên S3 bằng SQL, không cần server.
- **AWS Lambda + EventBridge:** Tự động bật/tắt EC2, RDS ngoài giờ làm việc.
- **CloudWatch Container Insights:** Thu thập log, metric từ EKS.
- **Secrets Manager/Parameter Store:** Quản lý mật khẩu, tự động rotation.
- **Session Manager:** Truy cập EC2 bảo mật, không cần SSH.
- **DataSync:** Chuyển dữ liệu từ on-premises SFTP lên EFS.
- **AWS Glue ETL:** Chuyển CSV sang Parquet, ít effort phát triển.
- **Amazon Macie + SNS:** Phát hiện PII trong S3, tự động cảnh báo.

---

### 2.2. Tối Ưu Chi Phí

**Từ khóa:** "cost-effective", "minimize costs", "reduce cost"  
**Giải pháp thường gặp:**  
- **S3 + CloudFront:** Host web tĩnh, cache tại edge.
- **S3 Lifecycle + Glacier Deep Archive:** Lưu trữ lâu dài, tiết kiệm.
- **EC2 Reserved + Spot Instances:** Đáp ứng workload động, tiết kiệm.
- **VPC gateway endpoint for S3:** Giảm chi phí truyền dữ liệu nội vùng.
- **DynamoDB On-demand/Aurora Serverless:** Tối ưu chi phí database biến động.
- **EC2 Spot Instances:** Xử lý batch, job có thể bị gián đoạn.

---

### 2.3. Đảm Bảo Tính Sẵn Sàng/Phục Hồi

**Từ khóa:** "highly available", "resilient", "fault tolerant", "automatic failover", "RPO", "RTO"  
**Giải pháp thường gặp:**  
- **RDS/Aurora Multi-AZ, Aurora Global Database:** Tự động failover, phục hồi nhanh.
- **EFS:** File system dùng chung, tự động scale.
- **ALB + Auto Scaling Group:** Web app đa AZ.
- **Amazon MQ Multi-AZ + Auto Scaling:** Hệ thống message resilient.
- **S3 Versioning + MFA Delete:** Bảo vệ dữ liệu khỏi xóa nhầm.
- **SNS + SQS + Lambda:** Đảm bảo message durability, retry.
- **Global Accelerator + NLB:** Đảm bảo HA cho dịch vụ UDP, low latency.

---

### 2.4. Hiệu Suất/Độ Trễ Thấp

**Từ khóa:** "quickest", "lowest latency", "high I/O", "real-time"  
**Giải pháp thường gặp:**  
- **CloudFront:** CDN giảm latency toàn cầu.
- **RDS Read Replica, ElastiCache:** Tăng hiệu năng đọc database.
- **DynamoDB DAX:** Caching cho DynamoDB, sub-millisecond latency.
- **FSx for Lustre:** HPC workload, tích hợp S3.
- **Kinesis Data Streams/Firehose:** Xử lý dữ liệu real-time.

---

### 2.5. Bảo Mật & Tuân Thủ

**Từ khóa:** "secure", "encrypt", "restrict access", "audit", "compliance"  
**Giải pháp thường gặp:**  
- **VPC endpoint cho S3/DynamoDB:** Truy cập private từ VPC.
- **IAM Role:** Gán quyền truy cập S3 cho EC2.
- **AWS Config, CloudTrail:** Theo dõi thay đổi cấu hình, API call.
- **WAF, Shield Advanced:** Bảo vệ web khỏi tấn công.
- **SSE-KMS:** Mã hóa dữ liệu với key quản lý tự động.
- **EBS encryption default:** Đảm bảo volume mới đều được mã hóa.
- **IAM Role cross-account, SCP:** Quản lý phân quyền nhiều account.

---

### 2.6. Lưu Trữ & Quản Lý Dữ Liệu

**Từ khóa:** "store data", "archive", "long-term retention", "file system", "database"  
**Giải pháp thường gặp:**  
- **S3:** Lưu trữ object, data lake, web tĩnh.
- **EFS:** File system NFS dùng cho EC2 Linux.
- **FSx for Windows:** File server SMB cho workload Windows.
- **RDS:** Database quan hệ, backup, Multi-AZ.
- **DynamoDB:** NoSQL, hiệu năng cao, scale tốt.
- **Storage Gateway:** Hybrid cloud, backup, archive.
- **S3 Object Lock:** Đảm bảo dữ liệu bất biến.

---

### 2.7. Kiến Trúc Sự Kiện & Messaging

**Từ khóa:** "decouple", "asynchronous", "queues", "topics"  
**Giải pháp thường gặp:**  
- **SQS:** Queue giải decouple, buffer, FIFO cho message order.
- **SNS:** Fan-out notification nhiều subscriber.
- **S3 Event + SQS + Lambda:** Xử lý ảnh upload tự động.
- **Kinesis Data Streams:** Event streaming, đảm bảo thứ tự.

---

## 3. Ghi Nhớ Cốt Lõi

- **Shared Responsibility Model:** AWS bảo mật *of* the cloud, khách hàng bảo mật *in* the cloud.
- **Principle of Least Privilege:** Chỉ cấp quyền cần thiết.
- **Separation of Concerns:** Decouple hệ thống bằng SQS/SNS.
- **Infrastructure as Code:** Dùng CloudFormation để tự động hóa hạ tầng.
- **Global vs. Regional Services:** Nhớ dịch vụ nào toàn cầu, dịch vụ nào theo vùng.

---

## 4. Lời Khuyên Ôn Thi

- Luôn đọc kỹ yêu cầu, chú ý từ khóa.
- Học thuộc các pattern giải quyết và dịch vụ chủ chốt.
- Thường xuyên thực hành với các tình huống thực tế.
- Áp dụng tư duy loại trừ khi gặp đáp án gần giống nhau.

**Chúc bạn ôn tập hiệu quả và thi tốt!**
