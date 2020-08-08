# Speculative Generality

## ลักษณะทั่วไปของการพิจารณา

### Signs and Symptoms (เครื่องหมายและอาการบ่งชี้)

มี class, method, field or parameter ที่ไม่เคยใช้

![SG](https://imgur.com/IilV2kI.jpg)

### Reasons for the Problem (สาเหตุของปัญหา)

บางครั้ง code ก็ถูกสร้างขึ้น "่just in case" หรือแค่สำหรับกรณีนี้เท่านั้น เพื่อรองรับคุณสมบัติในอนาคตที่คาดการณ์ไว้แต่มันไม่เคยได้รับการดำเนินการต่อ สุดท้าย code นั้นก็ยากที่จะเข้าใจและ support

### Treatment (การแก้ไข)

ลองใช้ **[Collapse Hierarchy](https://sourcemaking.com/refactoring/collapse-hierarchy)** เพื่อลบ abstract code ที่ไม่ได้ใช้

![Collapse Hierarchy](https://imgur.com/uExFhQ9.jpg)

- การตั้ง function ที่ไม่จำเป็นไปยัง class อื่น สามารถกำจัดได้ผ่านทาง **[Inline Class](https://sourcemaking.com/refactoring/inline-class)**

- ใช้ **[Inline Method](https://sourcemaking.com/refactoring/inline-method)** เพื่อกำจัด method ที่ไม่ได้ใช้

- Method ที่มี parameters ที่ไม่ได้ใช้ สามารถดูความช่วยเหลือของการ **[Remove Parameter](https://sourcemaking.com/refactoring/remove-parameter)**

- Fields ที่ไม่ได้ใช้สามารถทำการลบได้เลย

### Payoff (ผลลัพธ์)

- Slimmer code
- Easier support

### When to ignore (เมื่อไรที่ควรเมิน)

- หากคุณทำงานอยู่บน framework มันควรอย่างยิ่งที่จะสร้าง function ที่ไม่ได้ใช้ใน framework ตราบใดผู้ใช้ framework ต้องการ function การทำงาน

- ก่อนจะลบ elements ต้องแน่ใจว่าพวกมันไม่ได้ใช้ใน unit tests จริงๆ มันจะส่งผลธ์ร้ายถ้าการ tests ต้องการรับข้อมูลภายในบางอย่างจาก class หรือการดำเนินการที่เกี่ยวข้องกับ special testing-related actions
