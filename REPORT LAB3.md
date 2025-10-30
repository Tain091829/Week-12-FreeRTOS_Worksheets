Lab 3 Analysis: Cooperative vs Preemptive Multitasking

1. ระบบไหนมีเวลาตอบสนองดีกว่า? เพราะอะไร

Preemptive Multitasking มีเวลาตอบสนองดีกว่า เพราะ RTOS จะสลับ task อัตโนมัติตาม priority
Task สำคัญ (เช่น emergency) สามารถ preempt task อื่นได้ทันที
ใน Cooperative ระบบตอบสนองช้ากว่า เพราะ task ต้องยกสิทธิ์เอง (voluntary yield)
2. ข้อดีของ Cooperative Multitasking

Implementation ง่าย ไม่ซับซ้อน
Resource usage ต่ำ เพราะไม่มี overhead จาก context switching ของ RTOS
Debugging ง่ายกว่า เพราะ flow ของ task เป็นลำดับชัดเจน
เหมาะกับระบบที่งานไม่ต้องตอบสนอง real-time อย่างเคร่งครัด
3. ข้อเสียของ Cooperative Multitasking

Task หนึ่งสามารถ block ระบบได้ หากไม่ยกสิทธิ์
Response time ไม่ deterministic ขึ้นกับ task อื่น
ไม่เหมาะกับงาน real-time ที่ต้องตอบสนองทันที
ต้องมีความระมัดระวังในการเขียนโค้ดแต่ละ task เพื่อให้ yield อย่างเหมาะสม
4. สถานการณ์ที่ Cooperative จะดีกว่า Preemptive

ระบบ resource จำกัด (เช่น RAM, CPU) ไม่สามารถใช้ RTOS full-featured ได้
งานที่ deterministic timing ไม่สำคัญ
ระบบขนาดเล็ก หรือ embedded system ที่ task น้อยและ predictable
5. เหตุใด Preemptive จึงเหมาะสำหรับ Real-time systems

RTOS สามารถสลับ task ตาม priority อัตโนมัติ
Task สำคัญตอบสนองได้ทันที แม้ task อื่นยังทำงานอยู่
Response time deterministic และสามารถคาดการณ์ได้
เหมาะกับระบบที่ต้องการความแม่นยำสูง เช่น control system, sensor monitoring, emergency handling
