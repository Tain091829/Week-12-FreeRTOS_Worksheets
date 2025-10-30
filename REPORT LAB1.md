Lab 1 Analysis: Single Task vs Multitasking Demo

คำตอบสำหรับการวิเคราะห์

1. ความแตกต่างในการตอบสนองปุ่มระหว่างทั้งสองระบบ

Single Task System: การตอบสนองล่าช้า เนื่องจากต้องรอให้ task อื่นทำงานเสร็จก่อน (เช่น การประมวลผลข้อมูลหรือการควบคุม LED)
Multitasking System: การตอบสนองเร็วทันที (<100ms) เพราะมี task เฉพาะสำหรับตรวจสอบปุ่มและตั้ง priority สูงสุด ทำให้สามารถ interrupt งานอื่นได้ทันที
2. ใน Single Task System งานไหนที่ทำให้การตอบสนองล่าช้า

Task การประมวลผลข้อมูล (Processing Task) เป็นงานหนัก ใช้เวลา loop จำนวนมาก ทำให้ task อื่น ๆ ต้องรอ ส่งผลให้การตอบสนองปุ่มล่าช้า
3. ข้อดีของ Multitasking System ที่สังเกตได้

สามารถทำงานหลาย task พร้อมกัน (LED, Sensor, Actuator) โดยไม่บล็อกกัน
การตอบสนองเหตุการณ์ฉุกเฉินรวดเร็ว เพราะ task เฉพาะมี priority สูง
ใช้ CPU อย่างมีประสิทธิภาพมากขึ้น แบ่งเวลาทำงานระหว่าง task ต่าง ๆ
4. ข้อเสียของ Multitasking System ที่สังเกตได้

ความซับซ้อนของโค้ดเพิ่มขึ้น ต้องจัดการ task, stack size, และ priority
หาก task หนึ่งมี priority สูงมาก อาจทำให้ task อื่น starvation ได้
ต้องระวังเรื่อง resource ที่แชร์กัน (เช่น GPIO, variables) เพื่อป้องกัน race condition
