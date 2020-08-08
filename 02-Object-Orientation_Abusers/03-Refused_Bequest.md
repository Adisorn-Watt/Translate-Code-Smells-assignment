# Refused Bequest

## ปฏิเสธ Bequest

### Signs and Symptoms (เครื่องหมายและอาการบ่งชี้)

ถ้า subclass ใช้เพียงแค่บาง methods และคุณสมบัติ ที่ inherited จาก parents จะทำให้ลำดับชั้นไม่ถูกต้อง methods ที่ไม่จำเป็นอาจจะใช้ไม่ได้หรือได้รับการกำหนดใหม่และให้ข้อยกเว้น

![refuesd](https://imgur.com/PE5zP3R.jpg)

### Reasons for the Problem (สาเหตุของปัญหา)

ใครบางคนถูกกระตุ้นให้สร้าง inherited ระหว่าง classes โดยปรารถนาที่จะนำ code ใน superclass มาใช้เท่านั้น แต่ superclass และ subclass นั้นแตกต่างกันอย่างสิ้นเชิง

### Treatment (การแก้ไข)

หาก inherited ไม่มีเหตุผล และ subclass ไม่มีอะไรที่เหมือนกับ superclass จริงๆ ให้กำจัดมันด้วย **[Replace Inheritance with Delegation](https://sourcemaking.com/refactoring/replace-inheritance-with-delegation)**

![Replace Inheritance with Delegation](https://imgur.com/SbOpum9.jpg)

หาก inherited มีความเหมะสม ให้กำจัด fields ที่ไม่จำเป็นพร้อมทั้ง methods ใน subclass ดึง fields ทั้งหมด และ methods ที่จำเป็นต่อ subclass จาก parent class ออกมาแล้ววางพวกมันใน subclass ใหม่ จากนั้น set ทั้งสอง class เพื่อ inherit จาก class นั้น (\*\*\*\*[Extract Superclass](https://sourcemaking.com/refactoring/extract-superclass))

### Payoff (ผลลัพธ์)

ปรับปรุงความชัดเจนของ code คุณจะไม่จำเป็นที่จะต้องกังวลว่าทำไม `dog` class มัน inherit จาก `chair` class (แม้ว่าพวกมันจะมี 4 ขา)

![dog](https://imgur.com/gZB7Ffg.jpg)
