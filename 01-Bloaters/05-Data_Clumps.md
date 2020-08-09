# Data Clumps : การกระจุกตัวเป็นกลุ่มของข้อมูล
### Signs and Symptoms : สัญญาณและอาการของปัญหา 
บางครั้งส่วนต่างๆ ของโค้ดจะประกอบไปด้วยกลุ่มของ variable ที่มีความเหมือนกัน (เช่น parameter สำหรับการเชื่อมต่อกับฐานข้อมูล) กลุ่มของโค้ดเหล่านี้ควรถูกเปลี่ยนเป็นคลาสของพวกมันเอง
    
![data-clumps-1](https://sourcemaking.com/images/refactoring-illustrations/data-clumps-1.png)
    
### Reasons for the Problem : เหตุที่ทำให้เกิดปัญหานี้
บ่อยครั้งที่กลุ่มข้อมูลเหล่านี้เกิดจากโครงสร้างโปรแกรมที่ไม่ดีหรือเรียกเล่นๆ ว่า "การเขียนโปรแกรมแบบก็อปแปะ(copypasta programming)"
    
หากคุณต้องการที่จะทำให้แน่ใจว่าข้อมูลบางส่วนเป็นกลุ่มข้อมูลกันหรือไม่ เพียงแค่ลบค่าของข้อมูลทิ้งไปค่าใดค่าหนึ่ง และดูว่าค่าที่เหลือยังสมเหตุสมผลอยู่หรือไม่ ถ้าไม่ ก็ควรที่จะรวม variable กลุ่มนี้ให้กลายเป็น object 
    
### Treatment : หนทางเยียวยาปัญหา
+ หากการทำซ้ำข้อมูลประกอบด้วยฟิลด์ของคลาสให้ใช้ [Extract Class](https://sourcemaking.com/refactoring/extract-class)เพื่อย้าย field ไปยังคลาสของมันเอง
    
+ หากมีการส่งกลุ่มข้อมูลเดียวกันใน parameter ของ method ให้ใช้  Introduce Parameter Object](https://sourcemaking.com/refactoring/introduce-parameter-object) เพื่อกำหนดให้พวกมันเป็น class
    
+ หากข้อมูลบางส่วนถูกส่งผ่านไปยัง method อื่นๆ ให้ลองใช้การส่งข้อมูลทั้งหมดเป็น object ไปยัง method อื่น แทนที่จะส่งไปเพียง field เดียว ซึ่งการ [Preserve Whole Object](https://sourcemaking.com/refactoring/preserve-whole-object) จะช่วยได้

    
+ ดูโค้ดที่ถูกใช้โดย field เหล่านี้ อาจจะเป็นไอเดียที่ดีที่จะย้ายโค้ดเหล่านี้ไปยังคลาสของข้อมูล
    
### Payoff : ผลลัพธ์
+ ทำให้โค้ดเข้าใจง่าย และจัดการได้ง่ายขึ้น การดำเนินการกับข้อมูลที่เฉพาะเจาะจงถูกรวมอยู่ในที่เดียวกัน แทนที่จะกระจัดกระจายไปทั่วแบบมั่วซั่ว
    
+ ลดขนาดของโค้ด.
    
![data-clumps-3](https://sourcemaking.com/images/refactoring-illustrations/data-clumps-3.png)
    
### When to Ignore : เราสามารถใช้ comment ได้เมื่อไหร่?
การส่งผ่าน object ทั้งหมดใน parameter ของ method แทนที่จะส่งแค่ค่า (ชนิด primitive) อาจสร้างการพึ่งพากันที่ไม่พึงประสงค์ระหว่างคลาสทั้งสอง