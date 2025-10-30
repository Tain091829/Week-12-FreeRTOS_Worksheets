Lab Analysis: Time-Sharing System on ESP32

1. ความแตกต่างระหว่าง Manual Time-Sharing กับ Single Task

Single Task System: Task ทำงานทีละตัวแบบ sequential ทำให้ task หนัก ๆ (เช่น processing task) ทำให้ task อื่น ๆ ต้องรอ การตอบสนองต่อเหตุการณ์หรือ input จะช้า
Manual Time-Sharing System: ใช้ scheduler สลับ task ทุก time slice (50 ms ในโค้ด) ทำให้ task ทุกตัวได้รับเวลา CPU อย่างสม่ำเสมอ การตอบสนองเร็วขึ้นแม้ task หนักยังทำงานอยู่
2. ปัญหาที่พบใน Manual Time-Sharing

ไม่มี priority support: Task สำคัญยังต้องรอ task อื่นหมด time slice
Fixed time slice issues: Task เบ็ดยาวอาจถูก interrupt ขณะทำงาน ทำให้ไม่เหมาะกับงานที่ต้องต่อเนื่อง
Context switching overhead: มีเวลาที่เสียไปกับการสลับ task (ในโค้ดจำลอง overhead ด้วย loop)
ไม่มี inter-task communication: Task แต่ละตัวทำงานแยกกัน ไม่สามารถส่งข้อมูลหรือ synchronize ได้อย่างปลอดภัย
3. ข้อดีของ Manual Time-Sharing

Task หลายตัวสามารถทำงานสลับกันได้ เหมาะกับงานที่ต้องทำหลายงานพร้อมกัน
CPU utilization เพิ่มขึ้นเมื่อเทียบกับ Single Task System
เห็นภาพการทำงานแบบ time-sharing และ context switching ได้ชัดเจน
4. ข้อจำกัด

Scheduler แบบ manual ต้องเขียนเอง ทำให้โค้ดซับซ้อน
Task ที่ต้องตอบสนองทันที (real-time) อาจยัง delay เพราะไม่มี priority
ต้องเฝ้าระวัง overhead จาก context switching
5. ข้อสังเกตจากโค้ด

Task แบ่งเป็น 4 ตัว: sensor, processing, actuator, display
Time slice 50 ms ทำให้ทุก task สลับกันทำงาน
มีการคำนวณ CPU utilization และ overhead เพื่อวัดประสิทธิภาพ
สามารถทดลอง time slice ต่าง ๆ (10, 25, 50, 100, 200 ms) เพื่อดูผลต่อ efficiency
