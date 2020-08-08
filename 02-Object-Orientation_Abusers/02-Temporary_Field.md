# Temporary Field

## Field ชั่วคราว

### Signs and Symptoms (เครื่องหมายและอาการบ่งชี้)

Temporary fields ได้รับค่าของตัวเอง (และนั่นจึงทำให้มันเป็นที่ต้องการของ objects) ภายใต้สถานการณ์ที่แน่นอนเท่านั้น นอกเหนือจากมันพวกมันจะว่างเปล่า
![temp field](https://imgur.com/FGL8B0f.jpg)

### Reasons for the Problem (สาเหตุของปัญหา)

บ่อยครั้งที่ temporary field ถูกสร้างสำหรับการใช้ใน algorithm ที่มีความต้องการ input จำนวนมาก ดังนั้น แทนที่จะสร้าง parameter จำนวนมากใน method โปรแกรมเมอร์จึงตัดสินใจสร้าง fields สำหรับข้อมูลนี้ใน class ทำให้ field เหล่านี้ถูกใช้เพียงแค่ใน algorithm และไม่ได้ใช้งานในช่วงเวลาที่เหลือ

code ประเภทนี้ยากที่จะเข้าใจ คุณคาดหวังที่จะเห็นข้อมูลใน object fields แต่เพราะเหตุผลบางอย่างพวกมันจะว่างเปล่าอยู่เสมอ

### Treatment (การแก้ไข)

Temporary field และ code ทั้งหมดที่ใช้งานอยู่บนนั้นสามารถใส่ใน class แยกกันได้ผ่าน **[Extract Class](https://sourcemaking.com/refactoring/extract-class)** ในทางกลับกัน คุณก็กำลังสร้าง method object และได้รับผลลัพธ์ดียวกันราวกับว่าคุณกำลังทำ **[Replace Method with Method Object](https://sourcemaking.com/refactoring/replace-method-with-method-object)**

![replace method](https://imgur.com/nVpeXm2.jpg)

**[Introduce Null Object](https://sourcemaking.com/refactoring/introduce-null-object)** และการ integrate มันในเงื่อนไข code ที่ถูกใช้ในการตรวจสอบค่าของ temporary field สำหรับการมีอยู่

### Payoff (ผลลัพธ์)

ระบบของ code ได้รับการปรับปรุงให้ดีและชัดเจนขึ้น
![payoff](https://imgur.com/XF0vS4a.jpg)
