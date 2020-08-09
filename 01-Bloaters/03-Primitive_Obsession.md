## Primitive Obsession : การถูกตัวแปรแบบ primitive ครอบงำ
#### Signs and Symptoms : สัญญาณและอาการของปัญหา 
+ ใช้ตัวแปรแบบ primitive แทนที่จะใช้ object เล็กๆ สำหรับงานง่ายๆ (เช่น แปลงคำเงิน, วัดระยะ, ตัวอักษรพิเศษสำหรับเบอร์โทรศัพท์ ฯลฯ)
    
+ ใช้ ค่าคงที่(constant) สำหรับข้อมูลที่ต้องเข้ารหัส (เช่น constant `USER_ADMIN_ROLE = 1` สำหรับการอ้างถึงผู้ใช้ที่มีสิทธิของผู้ดูแลระบบ)
    
+ ใช้ค่าคงที่ชนิด String เป็นชื่อ field เพื่อใช้ใน array ของข้อมูล
    
![primitive-obsession-1](https://sourcemaking.com/images/refactoring-illustrations/2x/primitive-obsession-1.png)
    
#### Reasons for the Problem : เหตุที่ทำให้เกิดปัญหานี้
ก็เหมือนกับปัญหาอื่นๆ การถูกตัวแปรแบบ primitive ครอบงำเกิดขึ้นในช่วงเวลาแห่งความอ่อนแอ "ก็แค่ field ที่เอาไว้เก็บข้อมูลเอง!" มิตรสหายโปรแกรมเมอร์ท่านหนึ่งได้กล่าวไว้ การสร้าง primitive field ขึ้นมานั้นมันง่ายกว่าการที่จะต้องสร้าง class ใหม่ขึ้นมาอยู่แล้ว จริงมั้ย? เอาล่ะ เสร็จละ เห็นมั้ยแค่สร้าง primitive field ก็เสร็จละ จากนั้น field อื่นๆ ที่จำเป็นก็ถูกเพิ่มเข้ามาในลักษณะเดียวกันไปเรื่อยๆ แล้วพอผ่านไปสักพักคลาสก็กลายเป็นว่ามีขนาดใหญ่โตและเทอะทะ
    
Primitives มักถูกใช้เพื่อ "จำลอง" type ต่างๆ ดังนั้นแทนที่จะแยกข้อมูลออกเป็น type คุณควรที่มีชุดของตัวเลขหรือ string ที่ไว้สร้าง list ของค่าที่ได้รับอนุญาตสำหรับบาง entity จากนั้นก็กำหนดชื่อที่เข้าใจได้ง่ายให้กับตัวเลขและ string ที่เฉพาะเจาะจงเหล่านี้ผ่านทาง ค่าคงที่ ซึ่งเป็นเหตุผลว่าทำไมพวกมันถึงได้กระจายไปได้กว้างและไกล
    
อีกตัวอย่างหนึ่งของการใช้ primitive แบบไม่ที่โอเคก็คือ การใช้ในการจำลอง field ซึ่งทำให้ class ประกอบไปด้วย array ขนาดใหญ่ที่มีข้อมูลหลากหลายรูปแบบ และค่าคงที่ชนิด string (ซึ่งถูกระบุอยู่ในคลาส) ถูกใช้เป็นดัชนี array (Array indices) สำหรับการเก็บข้อมูลเหล่านี้
    
#### Treatment : หนทางเยียวยาปัญหา
ถ้าคุณมี primitive field ขนาดใหญ่หลากหลายรูปแบบ อาจจะเป็นไปได้ที่จะจัดกลุ่มบาง field เข้าไว้ใน class เดียวกัน หรือถ้าจะให้ดีกว่านั้น ให้ย้าย behavior ที่เกี่ยวข้องกับข้อมูลชุุดนี้ไปไว้อีกคลาสด้วย ซึ่งการทำแบบนี้ให้ลองใช้นี่ [Replace Data Value with Object](https://sourcemaking.com/refactoring/replace-data-value-with-object).
    
![primitive-obsession-2](https://sourcemaking.com/images/refactoring-illustrations/2x/primitive-obsession-2.png)
    
+ ถ้าหากว่าค่าของ primitive field ถูกใช้ใน method parameter ให้ใช้ [Introduce Parameter Object](https://sourcemaking.com/refactoring/introduce-parameter-object) หรือ [Preserve Whole Object](https://sourcemaking.com/refactoring/preserve-whole-object).
    
+ ถ้าข้อมูลที่มีความซับซ้อนถูกใช้ในตัวแปร ให้ใช้ [Replace Type Code with Class](https://sourcemaking.com/refactoring/replace-type-code-with-class), [Replace Type Code with Subclasses](https://sourcemaking.com/refactoring/replace-type-code-with-subclasses) หรือ [Replace Type Code with State/Strategy](https://sourcemaking.com/refactoring/replace-type-code-with-state-strategy).
    
+ ถ้ามี array รวมอยู่ในพวกตัวแปรด้วย ให้ใช้  [Replace Array with Object](https://sourcemaking.com/refactoring/replace-array-with-object).
    
#### Payoff : ผลลัพธ์
+ โค้ดมีความยืดหยุ่นมากขึ้น ซึ่งต้องขอบคุณการใช้ object แทนการใช้ตัวแปร primitive
    
+ โค้ดเข้าใจง่าย และจัดการง่ายขึ้น การดำเนินการกับข้อมูลที่เฉพาะเจาะจงถูกรวมอยู่ในที่เดียวกัน แทนที่จะอยู่กระจัดกระจายออกไป ทำให้ไม่ต้องเดาอีกต่อไปเกี่ยวกับสาเหตุของค่าคงที่แปลกๆ และเหตุใดมันจึงมาอยู่ใน array
    
+ หาโค้ดที่ซ้ำซ้อนได้ง่าย
    
![primitive-obsession-3](https://sourcemaking.com/images/refactoring-illustrations/2x/primitive-obsession-3.png)