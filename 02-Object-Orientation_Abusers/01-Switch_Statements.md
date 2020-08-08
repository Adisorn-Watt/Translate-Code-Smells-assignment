# Switch Statements

## การสลับ statements

### Signs and Symptoms (เครื่องหมายและอาการบ่งชี้)

เมื่อคุณมีตัวดำเนินการ `switch` ที่หรือลำดับคำสั่งของ `if` ที่ซับซ้อน

![Switch and Statements](https://imgur.com/tm9ooTM.jpg)

### Reasons for the Problem (สาเหตุของปัญหา)

การใช้งานตัวดำเนินการ `switch` และ `case` ที่ค่อนข้างหายากคือหนึ่งในลักษณะเฉพาะของ object-oriented code ซึ่ง code ส่วนมากสำหรับ `switch` แบบเดี่ยวนั้นจะกระจัดกระจายอยู่ในที่ต่างๆของ program เมื่อมีเงื่อนไข่ใหม่เพิ่มเข้ามา คุณจะต้องหา `switch` code ทั้งหมดและทำการปรับปรุงมัน

ง่ายๆก็คือ เมื่อไหร่ที่คุณเจอ `switch` คุณควรคิดถึงสิ่งที่อาจจะเกิดขึ้นในรูปแบบต่างๆ(Polymorphism)

### Treatment (การแก้ไข)

- เพื่อที่จะแยก `switch` และวางมันในที่ที่ถูกต้อง คุณอาจจะต้องการ **[Extract Method](https://sourcemaking.com/refactoring/extract-method)** และตามด้วย **[Move Method](https://sourcemaking.com/refactoring/move-method)**
- ถ้า `switch` ขึ้นอยู่กับลีกษณะของ code เช่น เมื่อ mode runtime ของ program ถูก switch ให้ใช้ **[Replace Type Code with Subclasses](https://sourcemaking.com/refactoring/replace-type-code-with-subclasses)** หรือ **[Replace Type Code with State/Strategy](https://sourcemaking.com/refactoring/replace-type-code-with-state-strategy)**

* หลังจากกำหนดโครงสร้าง inheritance ให้ใช้ **[Replace Conditional with Polymorphism](https://sourcemaking.com/refactoring/replace-conditional-with-polymorphism)**
* ถ้ามีเงื่อนไขที่ไม่มากเกินไปในการดำเนินการและพวกมันเรียกใช้ method เดียวกันด้วย parameters ที่ไม่เหมือนกัน polymorphism จะเกินความต้องการ ในกรณีนี้ คุณสามารถทำลาย method นั้นเป็น method ที่เล็กกว่าเดิมด้วย **[Replace Parameter with Explicit Methods](https://sourcemaking.com/refactoring/replace-parameter-with-explicit-methods)** และเปลี่ยน `switch` ให้สอดคล้องกัน
* ถ้าหนึ่งในทางเลือกเงื่อนไขเป็น `null` ให้ใช้ **[Introduce Null Object](https://sourcemaking.com/refactoring/introduce-null-object)**

### Payoff (ผลลัพธ์)

ระบบของ code ได้รับการปรับปรุงให้ดีขึ้น

![payoff](https://imgur.com/PUyuEQv.jpg)

### When to ignore (เมื่อไรที่ควรเมิน)

- เมื่อตัวดำเนินการ `switch` แสดง actions ง่ายๆไม่ซับซ้อน มันก็ไม่มีเหตุผลอะไรที่ต้องแก้ code
- เมื่อตัวดำเนินการ `switch` ถูกใช้บ่อยๆโดย patterns ที่ได้รับการออกแบบมาแล้ว(**[Factory Method](https://sourcemaking.com/design_patterns/factory_method)** และ **[Abstract Factory](https://sourcemaking.com/design_patterns/abstract_factory)**) เพื่อเลือก class ที่สร้างขึ้น
