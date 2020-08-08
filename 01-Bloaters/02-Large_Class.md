## Large Class : คลาสใหญ่เกิ๊น
### Signs and Symptoms : สัญญาณและอาการของปัญหา 
เกิดจากคลาสที่ประกอบไปด้วย fields, method หรือบรรทัดของโค้ดมากเกินไป
    
![large-class-1](https://sourcemaking.com/images/refactoring-illustrations/2x/large-class-1.png)
    
### Reasons for the Problem : เหตุที่ทำให้เกิดปัญหานี้
ในตอนเแรกๆ คลาสจะมีขนาดเล็ก แต่เมื่อเวลาผ่านไป ขนาดของมันจะใหญ่ขึ้นตามขนาดของโปรแกรมที่ใหญ่ขึ้นเรื่อยๆ
    
เช่นเดียวกับในกรณีของปัญหา Long Method นั่นคือโปรแกรมเมอร์มักจะรู้สึกว่าการทำฟีเจอร์ใหม่ในคลาส ที่มีอยู่แล้วมันง่ายกว่าสร้างคลาสใหม่เพื่อฟีเจอร์นั้นๆ โดยเฉพาะ
    
### Treatment : หนทางเยียวยาปัญหา
เมื่อใดที่คลาสมีฟังก์ชันการทำงานเยอะเกินไป ให้หาทางแยกมันออกจากกัน
    
![large-class-2](https://sourcemaking.com/images/refactoring-illustrations/2x/large-class-2.png)
    
+ [Extract Class](https://sourcemaking.com/refactoring/extract-class)
ใช้ในกรณีที่พฤติกรรมของคลาสที่ใหญ่เกินไปสามารถแยกออกเป็น component ที่แยกจากกันได้
    
+ [Extract Subclass](https://sourcemaking.com/refactoring/extract-subclass)
ใช้ในกรณีที่คลาสที่ใหญ่เกินไปสามารถ implement ในรูปแบบอื่นๆ ได้ หรือใช้ในกรณีหายาก
    
+ [Extract Interface](https://sourcemaking.com/refactoring/extract-interface)
ใช้ในกรณีที่จำเป็นที่จะต้องมีรายการการดำเนินการและ behavior ที่ลูกค้าใช้ได้
    
+ ถ้าคลาสขนาดใหญ่มีหน้าที่ในส่วนของอินเทอร์เฟซแบบกราฟิก คุณอาจพยายามลองย้ายข้อมูลและพฤติกรรมบางอย่างไปยัง domain object ที่แยกออกไปต่างหาก ในการดำเนินการดังกล่าวอาจจำเป็นที่จะต้องจัดเก็บสำเนาของข้อมูลบางส่วนไว้ใน 2 ที่ และต้องเก็บข้อมูลให้สอดคล้องกัน ดังนี้ [Duplicate Observed Data](https://sourcemaking.com/refactoring/duplicate-observed-data)
    
### Payoff : ผลลัพธ์
+ การ refactor คลาสเหล่านี้ช่วยให้นักพัฒนาไม่จำเป็นต้องจำ attributes จำนวนมากมายที่ใช้สำหรับคลาส
    
![large-class-3](https://sourcemaking.com/images/refactoring-illustrations/2x/large-class-3.png)
    
+ ในหลายๆ กรณี การแบ่งคลาสที่ใหญ่ๆ ออกเป็นส่วนๆ เป็นการหลีกเลี่ยงความซ้ำซ้อนของโค้ดและฟังก์ชัน