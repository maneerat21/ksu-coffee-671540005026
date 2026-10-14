# ANSWER — มณรัตน์ ศิริกุล 671540005026-3

- Platform: Render
- Production URL: https://ksu-coffee-671540005026.onrender.com

## คำตอบ

1. เลือก Render ซึ่งรันโค้ดแบบ Container (Web Service) ที่รันต่อเนื่อง บน production ใช้ server.js จริง เพราะ Start Command คือ `node server.js` เซิร์ฟเวอร์นี้ให้บริการทั้งหน้าเว็บใน public/ และ API /api/info

2. ตั้ง STUDENT_ID ในหน้า Environment Variables ของ Render ห้าม commit .env เพราะ repo เป็น Public ใครก็เห็นค่าในไฟล์ได้ และค่าที่ตั้งเฉพาะสภาพแวดล้อมไม่ควรปนกับโค้ด ถ้า /api/info แสดง NOT SET อาจเกิดจากลืมตั้งตัวแปร สะกดชื่อผิด หรือตั้งทีหลังแต่ยังไม่ได้ deploy ใหม่

3. ครั้งแรก 0.510525 วินาที / ครั้งที่สอง 0.336866 วินาที — ครั้งแรกช้ากว่าเล็กน้อย เพราะต้องสร้างการเชื่อมต่อ HTTPS ใหม่และเครือข่ายยังไม่อุ่น ครั้งที่สองเร็วกว่า ตอนที่วัด service ของ Render Free ยังไม่หลับ (เพิ่งถูกเปิดใช้งาน) จึงไม่เห็นความต่างมาก ถ้า service หลับอยู่ ครั้งแรกจะช้ากว่านี้มากเพราะต้องปลุก container ก่อน

4. เมื่อ git push ขึ้น GitHub แล้ว Render ได้รับแจ้งว่ามี commit ใหม่ จึงดึงโค้ดล่าสุดมา รัน npm install แล้วสตาร์ท node server.js ใหม่ หน้า production จึงเปลี่ยนเป็น Menu v2 ค่า commit ใน /api/info มาจากแพลตฟอร์ม และตรงกับผล git log -1 --format=%H

5. deploy ตรง ๆ ไม่ได้ เพราะ Web Service ของ Render รัน 1 service ต่อ 1 repo/คำสั่ง start ไม่อ่าน docker-compose.yml ที่มีหลาย service อีกทั้ง service promo ใช้ image จาก Docker Hub ต้อง deploy แยกกัน และลิงก์ localhost ก็ใช้ไม่ได้บน production