# Session 06 - Bài 3: Doctor Service

Repo gồm Eureka, Patient Service và `DOCTOR-SERVICE` (cổng `8082`) dùng PostgreSQL.

```bash
docker compose up -d
cd medical-discovery-server
gradle bootRun
# Mở terminal khác:
cd patient-service
gradle bootRun
```

Tạo bệnh nhân:

```bash
curl -i -X POST http://localhost:8081/api/v1/patients \
  -H 'Content-Type: application/json' \
  -d '{"fullName":"Nguyễn Văn An","dateOfBirth":"1990-05-20","gender":"Nam","phoneNumber":"0901234567","address":"Hà Nội","medicalHistory":"Dị ứng Penicillin"}'
```

Endpoint `GET /api/v1/patients/{id}` được thêm để Appointment-Service có thể
kiểm tra bệnh nhân qua Eureka ở bài sau.

Tạo dữ liệu bác sĩ rồi lấy danh sách `id`, `name`, `specialization`:

```bash
curl -X POST http://localhost:8082/api/v1/doctors \
  -H 'Content-Type: application/json' \
  -d '{"name":"Trần Minh","specialization":"Nội khoa","experienceYears":10,"email":"minh@hospital.vn","status":true}'

curl http://localhost:8082/api/v1/doctors
```
