# Long Parameter List : จำนวน parameter ยาวเป็นหางว่าว
### Signs and Symptoms : สัญญาณและอาการของปัญหา 
มีมากกว่า 3 หรือ 4 parameters ใน method นั้นๆ
    
![long-parameter-list-1](https://sourcemaking.com/images/refactoring-illustrations/2x/long-parameter-list-1.png)
    
### Reasons for the Problem : เหตุที่ทำให้เกิดปัญหานี้
การมี parameters จำนวนมากเกินไปใน Method อาจจะเกิดขึ้นหลังจากอัลกอริทึมหลากหลายรูปแบบถูกรวมอยู่ใน method เพียงอันเดียว จำนวน parameters มากมายมหาศาลที่ว่านี้ อาจจะถูกสร้างขึ้นเพื่อควบคุมว่าอัลกอริทึมใดที่จะรันบ้าง แล้วรันอย่างไร
    
parameters ที่มีจำนวนมากเกินไปอาจเป็นผลพลอยได้จากความพยายามในการทำให้คลาสมีความเป็นอิสระจากกันและกันมากยิ่งขึ้น ตัวอย่างเช่น ย้ายโค้ดสำหรับสร้าง object เฉพาะที่จำเป็นใน method นั้นๆ โดยย้ายจาก method นั้นๆ  ไปยังโค้ดสำหรับการเรียกใช้ method นั้นๆ แทน, แต่ object ที่ถูกสร้างขึ้นมาส่งค่าเป็น parameters ดังนั้นคลาสดั้งเดิมจึงไม่รู้ว่าความสัมพันธ์ระหว่าง object เป็นอย่างไรอีกต่อไป และทำให้การพึ่งพากันระหว่างคลาสลดลง แต่หากมีการสร้าง object เหล่านี้หลายๆ ตัว และแต่ละตัวก็จำเป็นที่จะต้องมี parameter เฉพาะของมันเอง ก็จะทำให้จำนวน parameters มากขึ้น
    
จำนวน parameters ที่มากเกินไปจะทำให้ method เข้าใจได้ยาก ใช้งานงานได้ยาก และอาจจะขัดแย้งกันในตัวของมันเอง ดังนั้น แทนที่จะมีจำนวน parameters เยอะๆ ก็ให้ method ใช้ข้อมูลใน object ของตัวเองไปเลย ถ้า object ปัจจุบันไม่ได้มีข้อมูลที่จำเป็นทั้งหมด object อื่นๆ ซึ่งจะได้รับข้อมูลที่จำเป็น จะสามารถส่งค่าเป็น method parameter ได้
    
### Treatment : หนทางเยียวยาปัญหา
ให้เช็คว่าค่าอะไรที่ถูกส่งไปยัง parameters หาก arguments บางส่วนเป็นเพียงผลลัพธ์ของการเรียกใช้ method ของ object อื่นๆ ให้ใช้ [การแทนค่า parameter ด้วย method call (Replace Parameter with Method Call)](https://sourcemaking.com/refactoring/replace-parameter-with-method-call) ซึ่งทำให้ object ที่ว่านี้สามารถที่จะถูกวางไว้ใน field ของคลาสมันเองได้ หรือส่งผ่านเป็น method parameter
    
![long-parameter-list-2](https://sourcemaking.com/images/refactoring-illustrations/2x/long-parameter-list-2.png)
    
+ แทนที่จะทำการส่งผ่านกลุ่มข้อมูลที่ได้รับมาจาก object อื่นๆ เป็น parameter ก็ให้ส่งเป็น object โดยใช้ [Preserve Whole Object](https://sourcemaking.com/refactoring/preserve-whole-object).
    
+ ถ้าหากว่ามีองค์ประกอบข้อมูลที่ไม่เกี่ยวข้องกันอยู่หลายองค์ประกอบ บางครั้งคุณสามารถที่จะรวมองค์ประกอบเหล่านี้เป็น parameter object อันเดียวได้ ผ่านทาง [Introduce Parameter Object](https://sourcemaking.com/refactoring/introduce-parameter-object).
    
### Payoff : ผลลัพธ์
+ อ่านเข้าใจง่ายขึ้น, โค้ดสั้นลง
    
+ การ refactor อาจจะทำให้ค้นพบโค้ดซ้ำซ้อนที่ไม่ได้สังเกตเห็นแต่แรกได้
    
### When to Ignore : : เราสามารถใช้ comment ได้เมื่อไหร่?
ห้ามกำจัด Parameters ทิ้ง หากทำจะทำให้เกิด depandency ที่ไม่พึงปรารถนาระหว่างคลาสได้