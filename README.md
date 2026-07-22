# คู่มือการติดตั้งและเปิดใช้งานเว็บไซต์แบบฟรี 100%

โฟลเดอร์นี้บรรจุโค้ดเว็บไซต์ตัวอย่างพร้อมระบบ Admin และคู่มือการเปิดใช้งานสาธารณะ (Public Deploy)

---

## 📁 โครงสร้างไฟล์ในโฟลเดอร์
- `index.html` : หน้าแสดงผลฝั่งผู้ใช้ทั่วไป (Public View)
- `admin.html` : หน้าหลังบ้านสำหรับ Admin ในการแก้ไขข้อมูล
- `README.md`   : คู่มือการตั้งค่าและการ Deploy

---

## 🚀 ขั้นตอนการเปิดใช้งาน (Deploy) แบบละเอียด

### ขั้นตอนที่ 1: เตรียมฐานข้อมูลด้วย Supabase (ฟรี)
1. สมัครใช้งานที่ [supabase.com](https://supabase.com)
2. สร้าง New Project
3. เข้าเมนู **Table Editor** -> **New Table** ตั้งชื่อตารางว่า `site_settings`
   - เพิ่ม Column: `key` (text, unique) และ `value` (text)
4. ไปที่ **Project Settings** -> **API** คัดลอก `Project URL` และ `anon key`
5. เปิดไฟล์ `index.html` และ `admin.html` ในโฟลเดอร์นี้ แล้วนำ URL และ Key ไปวางแทนที่คำว่า `YOUR_SUPABASE_URL` และ `YOUR_SUPABASE_ANON_KEY`

---

### ขั้นตอนที่ 2: นำโค้ดขึ้นเว็บออนไลน์ (Vercel)
1. สมัครใช้งานที่ [GitHub.com](https://github.com) แล้วสร้าง Repository ใหม่ อัปโหลดไฟล์ในโฟลเดอร์นี้ขึ้นไป
2. สมัครใช้งาน [Vercel.com](https://vercel.com) แล้วเชื่อมต่อกับ GitHub
3. เลือก Repository ที่สร้างขึ้น แล้วกด **Deploy** 
4. คุณจะได้ URL เว็บไซต์ฟรีมาใช้งานทันที (เช่น `https://my-website.vercel.app`)

---

### ขั้นตอนที่ 3: เปิดการป้องกันด้วย Cloudflare Zero Trust (ป้องกันหน้า Admin)
1. นำโดเมนของคุณมาผูกกับ [Cloudflare.com](https://cloudflare.com)
2. เข้าไปที่เมนู **Zero Trust** -> **Access** -> **Applications**
3. กด Add Application เลือกแบบ **Self-hosted**
4. ตั้งค่า Domain เป็นโดเมนของคุณ และระบุ Path เป็น `admin.html`
5. ในช่อง Policy ให้ใส่ **อีเมลของคุณ** 
6. **ผลลัพธ์**: เวลาเข้าหน้า `admin.html` Cloudflare จะบังคับส่งรหัส OTP 6 หลักเข้าอีเมลของคุณก่อนเสมอ ทำให้คนอื่นหรือบอทไม่สามารถเข้าหน้า Admin ได้เลย!
