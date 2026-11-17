# CPE312 ML Service
## โครงสร้างโปรเจกต์

```text
ml_service/
├── templates/
│   └── main.html          # หน้าเว็บ UI สำหรับใช้งานผ่านเบราว์เซอร์
├── app.py                 # Web Server และ API Endpoint (/predict)
├── train_model.py         # สคริปต์สำหรับเทรนโมเดลและบันทึกไฟล์ model.pkl
├── Dockerfile             # ไฟล์ตั้งค่าสำหรับสร้าง Docker Image
├── requirements.txt       # รายการ Library ที่ต้องใช้
├── .gitignore             # ไฟล์ยกเว้นการอัปโหลดขึ้น Git
└── README.md              # คู่มือการใช้งานโปรเจกต์
```

---

## วิธีการ Build และ Run ด้วย Docker

### 1. Build Docker Image
```bash
docker build -t ds-ml-service .
```

### 2. Run Container
```bash
docker run --rm -p 5001:5000 ds-ml-service
```
---

## การทดสอบใช้งาน

### 1. ใช้งานผ่านหน้าเว็บ
เปิดเบราว์เซอร์และเข้าไปที่ `http://127.0.0.1:5001`
ตรวจสอบสถานะ `http://127.0.0.1:5001/health`

### 2. ทดสอบยิง API Endpoint

**สำหรับ Windows (PowerShell):**
```powershell
Invoke-WebRequest -Uri "[http://127.0.0.1:5001/predict](http://127.0.0.1:5001/predict)" `
  -Method POST `
  -Body '{"features":[8.3,25.0,6.0,1.0,1200,3.0,34.2,-118.3]}' `
  -ContentType "application/json"
```