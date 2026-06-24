# 🚀 Deploy Project

### 🌐 ทดลองใช้งานโปรเจ๊ค

[Open Project](https://test-ypgs.onrender.com/)

---

## 1️⃣ ติดตั้ง Git (ทำครั้งเดียว)

ดาวน์โหลดและติดตั้ง Git จาก:

https://git-scm.com

หลังติดตั้งเสร็จ ตรวจสอบว่าใช้งานได้หรือไม่:

```bash
git --version
```

หากแสดงเวอร์ชัน เช่น `git version 2.x.x` แสดงว่าติดตั้งสำเร็จ

---

## 2️⃣ ตั้งค่า Git (ทำครั้งเดียว)

กำหนดชื่อและอีเมลที่ใช้กับ GitHub

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

ตัวอย่าง

```bash
git config --global user.name "Bunkham Yolai"
git config --global user.email "bun@gmail.com"
```

---

## 3️⃣ อัปโหลดโปรเจกต์ขึ้น GitHub

เปิด Terminal ภายในโฟลเดอร์โปรเจกต์ แล้วรันคำสั่งตามลำดับ

```bash
git init
git add .
git commit -m "first commit" ตั้งชื่ออื่นได้
git branch -M main
git remote add origin https://github.com/bisket77/test2.git
git push -u origin main
```

---

## 🔄 กรณีเคยใช้ Git อยู่แล้ว

หากโปรเจกต์มี Git อยู่แล้ว และต้องการเชื่อมกับ Repository ใหม่ ให้ใช้คำสั่ง:

```bash
git remote add origin https://github.com/bisket77/test2.git
git branch -M main
git push -u origin main
```

---

✅ เมื่อ Push สำเร็จ โค้ดจะถูกอัปโหลดขึ้น GitHub Repository เรียบร้อย

## 🔄 การอัปเดตโปรเจกต์หลังแก้ไขโค้ด

หลังจากแก้ไขไฟล์ในโปรเจกต์แล้ว ให้อัปเดตขึ้น GitHub ด้วยคำสั่งดังนี้

### 1. ตรวจสอบไฟล์ที่มีการเปลี่ยนแปลง

```bash
git status
```

### 2. เพิ่มไฟล์ที่แก้ไขเข้าสู่ Git

```bash
git add .
```

### 3. สร้าง Commit พร้อมระบุรายละเอียด

```bash
git commit -m "Update project"
```

ตัวอย่าง

```bash
git commit -m "Add login page"
```

```bash
git commit -m "Fix database connection"
```

### 4. อัปโหลดขึ้น GitHub

```bash
git push
```

### 📋 ดูประวัติการอัปเดต

```bash
git log --oneline
```

> หมายเหตุ: เมื่อเชื่อม GitHub Repository เรียบร้อยแล้ว ไม่จำเป็นต้องใช้ `git init` หรือ `git remote add origin` ซ้ำทุกครั้ง



```bash
git remote add origin https://github.com/bisket77/SA.git
git branch -M main
git push -u origin main
```


# 📌 สรุปปัญหา Git และวิธีแก้

## 1. Git ถูกสร้างผิดที่

### อาการ

```bash
git status
```

แสดงไฟล์ทั้งเครื่อง เช่น

```text
Documents/
Downloads/
Pictures/
AppData/
```

### วิธีแก้

```powershell
cd "C:\Users\Asus TUF"
Remove-Item -Recurse -Force .git
```

จากนั้นเข้าโปรเจกต์จริงแล้วสร้าง Git ใหม่

```bash
git init
```

---

## 2. Push ไม่ได้ (fetch first)

### อาการ

```text
! [rejected] main -> main (fetch first)
```

### สาเหตุ

GitHub มี Commit อยู่แล้ว แต่ Git ในเครื่องเป็นคนละประวัติ

### ตรวจสอบ

```bash
git remote -v
git log --oneline -n 5
```

### ถ้า GitHub มีแค่ README

```bash
git push -u origin main --force
```

> ⚠️ คำสั่งนี้จะเขียนทับข้อมูลบน GitHub

### ถ้าต้องการเก็บข้อมูลเดิมบน GitHub

```bash
git pull origin main --allow-unrelated-histories
git push origin main
```

---

## 3. อัปโหลดโปรเจกต์ขึ้น GitHub

เข้าโฟลเดอร์โปรเจกต์

```bash
cd "C:\Users\Asus TUF\Desktop\STUDENT 3\TERM 1\SA"
```

ตรวจสอบ Git Repository

```bash
git rev-parse --show-toplevel
```

ถ้าขึ้น

```text
C:/Users/Asus TUF/Desktop/STUDENT 3/TERM 1/SA
```

แสดงว่าใช้งานได้

### อัปโหลดขึ้น GitHub

```bash
git add .
git commit -m "Update SA project"
git push
```

---

## 4. ไม่มีไฟล์ให้ Commit

### อาการ

```text
nothing to commit, working tree clean
```

### ความหมาย

- ไม่มีไฟล์ใหม่
- ไม่มีไฟล์ที่แก้ไข
- GitHub กับเครื่องตรงกันแล้ว

---

## 5. มี Git ซ้อนกัน (Nested Repository)

### อาการ

```text
modified: week1 (modified content)
```

หรือ

```text
modified: my-project (modified content)
```

### ตัวอย่างโครงสร้าง

```text
SA
└── week1
    └── .git
```

หรือ

```text
SA
└── week1
    └── my-project
        └── .git
```

### วิธีแก้

เข้าไปในโปรเจกต์ย่อยก่อน

```bash
cd week1
```

หรือ

```bash
cd my-project
```

จากนั้น

```bash
git add .
git commit -m "Update project"
git push
```

---

## 6. อัปเดตโปรเจกต์หลังแก้ไขโค้ด

```bash
git add .
git commit -m "Update project"
git push
```

### ตัวอย่าง

```bash
git commit -m "Add login page"
```

```bash
git commit -m "Fix database connection"
```

```bash
git commit -m "Update frontend"
```

---

## 7. คำสั่งตรวจสอบที่ใช้บ่อย

### ตรวจสอบสถานะไฟล์

```bash
git status
```

### ดูประวัติ Commit

```bash
git log --oneline
```

### ดู Repository ที่เชื่อมอยู่

```bash
git remote -v
```

