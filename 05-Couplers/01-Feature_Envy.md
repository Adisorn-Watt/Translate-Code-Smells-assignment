# Feature Envy

## สัญญาณ และอาการที่แสดง (Signs and Symptoms)

เมื่อวิธีการเข้าถึงข้อมูลของออบเจ็กต์อื่นมากกว่าข้อมูลของตัวเอง

![feature-envy-1 ](https://sourcemaking.com/images/refactoring-illustrations/2x/feature-envy-1.png)

## สาเหตุของปัญหา (Reasons for the Problem)

smell นี้อาจเกิดขึ้นหลังจากย้ายเซตข้อมูลไปยังคลาสของข้อมูล หากเป็นกรณีนี้คุณอาจต้องการย้ายการดำเนินการกับข้อมูลไปยังคลาสนี้ด้วย

## การรักษา (Treatment)

ตามกฏพื้นฐาน หากมีการเปลี่ยนแปลงในเวลาเดียวกัน คุณควรจะเก็บไว้ในที่เดียวกันเช่นกัน โดยปกติข้อมูล และฟังก์ชันที่ใช้ข้อมูลนี้ จะมีการเปลี่ยนแปลงร่วมกัน (ถึงแม้ว่าจะมีข้อยกเว้นก็ตาม)

![feature-envy-2 ](https://sourcemaking.com/images/refactoring-illustrations/2x/feature-envy-2.png)

- หากต้องการใช้วิธีที่ชัดเจน ควรย้ายไปที่อื่นโดยใช้ [Move Method](https://sourcemaking.com/refactoring/move-method)
- วิธีการเข้าถึงข้อมูลเพียงบางส่วนของออบเจ็กต์อื่นๆ ให้ใช้ [Extract Method](https://sourcemaking.com/refactoring/extract-method) เพื่อย้ายส่วนที่มีปัญหา

* วิธีการใช้ฟังก์ชันจากคลาสอื่น ขั้นตอนแรกให้กำหนดคลาสที่มีข้อมูลส่วนใหญ่ที่ใช้ จากนั้นวางในคลาสนี้พร้อมกับข้อมูลอื่นๆ อีกวิธีหนึ่งคือใช้ [Extract Method](https://sourcemaking.com/refactoring/extract-method) เพื่อแบ่งวิธีการออกเป็นหลายๆส่วน ซึ่งสามารถวางไว้ในที่ต่างๆ ในคลาสที่ต่างกันได้

## ผลตอบแทน (Payoff)

- ลดการซ้ำซ้อนของโค้ด (หากใส่โค้ดสำหรับจัดการข้อมูลไว้ที่ศูนย์กลาง)
- มีการจัดระเบียบโค้ดที่ดีขึ้น (วิธีการจัดการข้อมูลอยู่ถัดจากข้อมูลจริง)

![feature-envy-3 ](https://sourcemaking.com/images/refactoring-illustrations/2x/feature-envy-3.png)

## เมื่อใดที่ควรละเว้น (When to Ignore)

บางครั้งพฤติกรรมจะถูกแยกออกจากคลาสที่เก็บข้อมูลโดยเจตนา ประโยชน์ของการทำแบบนี้คือความสามารถที่จะเปลี่ยนพฤติกรรมแบบไดนามิก (ดู [Strategy](http://sourcemaking.com/design_patterns/strategy),[Visitor](http://sourcemaking.com/design_patterns/visitor) และรูปแบบอื่นๆ )
