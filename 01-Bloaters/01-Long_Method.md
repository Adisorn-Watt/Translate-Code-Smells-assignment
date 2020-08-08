# Long Method : Method ยาวเกินไป
### Signs and Symptoms : สัญญาณและอาการของปัญหา 
เกิดจาก method ที่มีโค้ดหลายบรรทัดจนเกินไป โดยทั่วไปแล้ว method ใดๆ ที่ยาวเกิน 10 บรรทัด ก็ควรเริ่มตั้งคำถามกับความยาวของมันได้แล้ว
    
![long-method-1](https://sourcemaking.com/images/refactoring-illustrations/2x/long-method-1.png)
    
### Reasons for the Problem : เหตุที่ทำให้เกิดปัญหานี้
เกิดจากการเขียนโค้ดเพิ่มเข้าไปยัง method แต่ไม่เคยลบอะไรทิ้งเลยอยู่เสมอ เนื่องจากการเขียนโค้ดนั้นง่ายกว่าการอ่านโค้ด จึงทำให้มักจะไม่มีใครสังเกตเห็นปัญหานี้จนกระทั่ง method นั้นๆ กลายร่างเป็น method ที่ใหญ่โตจนน่าเกลียด
    
โดยปกติแล้วการสร้าง method ใหม่มักจะยากกว่าการเพิ่มโค้ดลงไปใน method ที่มีอยู่แล้วเสมอ ดังคำบ่นนี้: “เพิ่มโค้ดอีกแค่ 2-3 บรรทัดเอง จะสร้าง method ใหม่ไปทำไมล่ะ?... ” และก็นั่นแหละครับ โค้ดใน method นั้นๆ ก็เพื่มแล้วเพิ่มอีกจนก่อกำเนิดโค้ดแบบสปาเก็ตตี้ที่แสนจะยุ่งเหยิง
    
### Treatment : หนทางเยียวยาปัญหา
หลักการง่ายๆ ในการแแก้ปัญหานี้ คือ เมื่อใดที่คุณรู้สึกว่าต้อง comment อธิบายอะไรบางอย่างใน method คุณควรเอาโค้ดส่วนนั้นๆ ยกไปไว้ที่ method ใหม่ แม้จะเพียงแค่บรรทัดเดียวก็สามารถทำได้และควรเป็นอย่างยิ่งที่จะแยกออกไปยังอีก method หากว่ามันต้อง comment อธิบาย
และถ้าหาก method มีชื่อที่สื่อความหมายถึงสิ่งที่ทำในตัวมันเอง ก็จะไม่มีใครจำเป็นต้องมองโค้ดด้วยซ้ำว่ามันเอาไว้ทำอะไร
    
![long-method-2](https://sourcemaking.com/images/refactoring-illustrations/2x/long-method-2.png)
    
+ ในการลดความยาวของ method ให้ใช้ [การแยกเป็นอีก method (Extract Method)](https://sourcemaking.com/refactoring/extract-method)    
    
+ หากตัวแปรและพารามิเตอร์แบบ Local ทำให้วิธีการแยกเป็นอีก method มีปัญหา ให้ [Replace Temp with Query](https://sourcemaking.com/refactoring/replace-temp-with-query), [Introduce Parameter Object](https://sourcemaking.com/refactoring/introduce-parameter-object) หรือ [Preserve Whole Object](https://sourcemaking.com/refactoring/preserve-whole-object)
    
+ หากวิธีการข้างต้นที่กล่าวมาไม่ได้ช่วยอะไรเลย ให้ลองทำการย้ายทั้ง method ไปยังอีก object ที่อยู่แยกออกไป ดังนี้[Replace Method with Method Object](https://sourcemaking.com/refactoring/replace-method-with-method-object).
    
+ พวกเงื่อนไข(พวก If-else) กับลูป(พวก for-while) เป็นจุดเริ่มต้นที่ดีในการย้ายโค้ดไปยัง method ที่อยู่แยกออกไป สำหรับพวกเงื่อนไขให้[ลดองค์ประกอบของเงื่อนไข (Decompose Conditional)](https://sourcemaking.com/refactoring/decompose-conditional) หากมีการวนลูปให้ลอง [แยกเป็นอีก method (Extract Method)](https://sourcemaking.com/refactoring/extract-method).
    
### Payoff : ผลลัพธ์
+ ในบรรดาโค้ดแบบ Object ทั้งหมด คลาสที่มีเมธอดที่สั้นจะดูแลรักษาง่ายที่สุด ยิ่งเมธอดหรือฟังก์ชันยาวมากเท่าไร ก็ยิ่งยากต่อการทำความเข้าใจและดูแลรักษา
    
+ นอกจากนี้แล้ว เมธอดที่ยาวเกินไปยังเป็นที่ซ่อนที่สมบูรณ์แบบสำหรับโค้ดซ้ำซ้อนที่เราไม่ต้องการ    
![long-method-3](https://sourcemaking.com/images/refactoring-illustrations/2x/long-method-3.png)
    
### Performance : ประสิทธิภาพ
การเพิ่มจำนวนเมธอดทำให้ประสิทธิภาพแย่ลงอย่างที่ใครหลายๆ คนบอกมั้ย? คำตอบก็คือ โดยส่วนมากแล้วจะส่งผลกระทบเล็กน้อยมากๆ จนไม่จำเป็นที่จะต้องเป็นกังวล
    
อีกอย่าง การเพิ่มเมธอดทำให้คุณมีโค้ดที่ชัดเจนและเข้าใจได้ง่าย ซึ่งทำให้คุณมีแนวโน้มที่จะค้นพบวิธีที่มีประสิทธิภาพอย่างแท้จริงในการปรับเปลี่ยนโครงสร้างของโค้ด และทำให้ประสิทธิภาพเพิ่มขึ้นได้อย่างแท้จริง ถ้าหากจะทำ