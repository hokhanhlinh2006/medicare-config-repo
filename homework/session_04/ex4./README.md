# Bài Tập 4: Tạo Discovery Server và chuyển Config Server sang Git backend

## Yêu cầu 1: Config Repo
Các file cấu hình đã được đẩy lên GitHub tại repo `medicare-config-repo`.

## Yêu cầu 2-4: Hướng dẫn khởi động

Vui lòng khởi động các service theo đúng thứ tự sau để đảm bảo hệ thống hoạt động đúng (Config Server phải khởi động trước để các service khác có thể lấy cấu hình, sau đó đến Discovery Server, và cuối cùng là các Microservice):

1. **Khởi động Config Server (Port 8888):**
   ```bash
   cd config-server
   ./gradlew bootRun
   ```

2. **Khởi động Discovery Server (Port 8761):**
   ```bash
   cd discovery-server
   ./gradlew bootRun
   ```

3. **Khởi động các Microservice (Port 8081 - 8085):**
   Khởi động lần lượt các microservice sau:
   - Patient Service (8081)
     ```bash
     cd patient-service
     ./gradlew bootRun
     ```
   - Doctor Service (8082)
     ```bash
     cd doctor-service
     ./gradlew bootRun
     ```
   - Appointment Service (8083)
     ```bash
     cd appointment-service
     ./gradlew bootRun
     ```
   - Medical Record Service (8084)
     ```bash
     cd medical-record-service
     ./gradlew bootRun
     ```
   - Pharmacy Service (8085)
     ```bash
     cd pharmacy-service
     ./gradlew bootRun
     ```

## Yêu cầu 5: Kiểm thử

- Truy cập [http://localhost:8761](http://localhost:8761) để xem giao diện Eureka Dashboard. Bạn sẽ thấy 5 service (PATIENT-SERVICE, DOCTOR-SERVICE, APPOINTMENT-SERVICE, MEDICAL-RECORD-SERVICE, PHARMACY-SERVICE) đã đăng ký thành công.
- Truy cập [http://localhost:8888/patient-service/default](http://localhost:8888/patient-service/default) để kiểm tra Config Server có lấy đúng cấu hình từ GitHub repo không.
- Thử nghiệm gọi API qua Postman để đảm bảo logic ứng dụng (CRUD) vẫn hoạt động bình thường.
