# Divergent Change : การเแลี่ยนแปลงที่แตกต่าง

Divergent Change คล้ายคลึงกับ [Shotgun Surgery](02-Shotgun_Surgery.md) แต่จริงๆแล้วมันตรงข้ามกัน Divergent Change คือเมื่อมีการ change หลายๆครั้งในคลาสเดียวส่วน Shotgun Surgery จะพูดถึงเมื่อมี change นึงเกินขึ้นกับหลายๆคลาสพร้อมกัน

## Signs and Symptoms : สัญญาณและอาการ

คุณจะพบว่าคุณจำดป็นที่จะต้องเปลี่ยนกระบวนการต่างๆเมื่อคุณสร้าง change บนคลาสของคุณเช่นเมื่อคุณเพิ่มประเภทของผลิตภัณท์คุณจะต้องเปลี่ยนกระบวนการต่างๆสำหรับ ค้นหา แสดงผล และ การจัดเรียงผลิตภัณท์

![Divergent-Change-01](https://sourcemaking.com/images/refactoring-illustrations/divergent-change-1.png)

## Reasons for the problem : สาเหตุของปัญหา

ส่วนใหญ่การปรับเปลี่ยนที่แตกต่างเหล่านี้จะขึ้นอยู่กับโครงสร้างของโปรแกรมที่อ่อนแอหรือ "copypasta programmimg" (การเขียนแบบก็อปวาง)

## Treatment : การบำรุงรักษา

- แยกปฤติกรรมของคลาสโดยการ [Extract Class](https://sourcemaking.com/refactoring/extract-class)
- ถ้ามีคลาสอื่นๆที่มีประฤติกรรมที่เหมือนกันคุณอาจจะต้องการรวมคลาสโดยการสืบทอดกัน ([Extract Superclass](https://sourcemaking.com/refactoring/extract-superclass) and [Extract Subclass](https://sourcemaking.com/refactoring/extract-subclass))

## Payoff : ผลของการขจัดกลิ่นนี้

- ทำใหเการจัดการโค้ดดีขึ้น
- ลดการซ้ำซ้อนของโค้ด
- ทำให้การซัพพอร์ตง่ายขึ้น
