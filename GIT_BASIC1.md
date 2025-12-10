# Git Basic Commands Note

บันทึกคำสั่ง Git พื้นฐานที่เรียนรู้ในสัปดาห์ที่ 1

## 1. การเริ่มต้นโปรเจค
- `git init`: สร้าง Git repository ใหม่ในโฟลเดอร์
- `git config --global user.name "ชื่อ"`: ตั้งชื่อผู้ใช้
- `git config --global user.email "อีเมล"`: ตั้งอีเมลผู้ใช้

## 2. การบันทึกงาน (Save Version)
- `git add .`: นำไฟล์ทั้งหมดเข้าสู่ Staging Area (เตรียมบันทึก)
- `git commit -m "ข้อความ"`: บันทึกไฟล์อย่างเป็นทางการ (Snapshot)

## 3. การเชื่อมต่อ GitHub (Online)
- `git branch -M main`: เปลี่ยนชื่อ branch หลักเป็น main
- `git remote add origin <url>`: เชื่อมต่อกับ GitHub Repository
- `git push -u origin main`: อัปโหลดโค้ดขึ้น GitHub ครั้งแรก