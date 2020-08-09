# Alternative Classes with Different Interfaces

## Class ทางเลือกที่มี interfaces ที่แตกต่างกัน

### Signs and Symptoms (เครื่องหมายและอาการบ่งชี้)

2 classes ที่ทำหน้าที่เหมือนกันแต่มีชื่อ methods ต่างกัน

![same class](https://imgur.com/s7T1UCr.jpg)

### Reasons for the Problem (สาเหตุของปัญหา)

โปรแกรมเมอร์ที่สร้างหนึ่งใน classes ไม่รู้ว่ามี class ที่เทียบเท่า function อยู่แล้ว

### Treatment (การแก้ไข)

ลองใส่ interface ของ classes ในเงื่อนไข่ของตัวส่วนที่ใช้ร่วมกัน

- **[Rename Method](https://sourcemaking.com/refactoring/rename-method)** เพื่อทำให้พวกมันเหมือนกันใน alternative classes ทั้งหมด

- **[Move Method](https://sourcemaking.com/refactoring/move-method)**,**[Add Parameter](https://sourcemaking.com/refactoring/add-parameter)**, และ **[Parameterize Method](https://sourcemaking.com/refactoring/parameterize-method)** เพื่อสร้างสัญลักษณ์และการดำเนินการ methods เดียวกัน

- หากมีเพียงแค่ส่วนของการทำงานของ classes ที่ซ้ำกัน ให้ลองใช้ _\*\*[Extract Superclass](https://sourcemaking.com/refactoring/extract-superclass)_ ในกรณีนี้ classes ที่มีอยู่แล้วจะกลายเป็น subclass

- หลังจากที่คุณตัดสินใจแน่นอนแล้วว่า method ของการแก้ไขที่จะใช้และดำเนินการคืออะไร คุณอาจจะสามารถลบหนึ่งใน classes ที่ซ้ำกันได้

### Payoff (ผลลัพธ์)

- คุณสามารถกำจัดการซ้ำกันของ code ที่ไม่จำเป็นออกไปได้ ทำให้ code ความงุ่มง่ามน้อยลง
- Code สามารถอ่านและเข้าใจได้ง่ายขึ้น (คุณไม่จำเป็นต้องเดาเหตุผลสำหรับการสร้างของ class ที่สองที่ทำหน้าที่เหมือนกับ class แรก)

![payoff](https://imgur.com/F5YvNov.jpg)

### When to ignore (เมื่อไรที่ควรเมิน)

บางครั้งการรวม classes ก็เป็นเรื่องที่เป็นไปไม่ได้หรือยากมากจนไร้จุดหมาย หนึ่งตัวอย่างคือเมื่อ alternative classes อยู่ต่าง libraries กัน ซึ่งแต่ละ class มี version เป็นของตัวเอง
