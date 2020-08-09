# Shotgun Surgery : การผ่าตัดของปืนลูกซอง

Shotgun Surgery คล้ายคลึงกับ [Divergent Change](03-Change_Preventers/02-Shotgun_Surgery.md) แต่จริงๆแล้วมันตรงข้ามกัน Divergent Change คือเมื่อมีการ change หลายๆครั้งในคลาสเดียวส่วน Shotgun Surgery จะพูดถึงเมื่อมี change นึงเกินขึ้นกับหลายๆคลาสพร้อมกัน

## Signs and Symptoms : สัญญาณและอาการ

การทำการปรับแต่งใดๆคุณจะต้องทำการเปลี่ยนแปลง change เล็กๆหลายๆอันในหลายๆคลาส

![Shotgun-Surgery-01](https://sourcemaking.com/images/refactoring-illustrations/2x/shotgun-surgery-1.png)

## Reasons for the problem : สาเหตุของปัญหา

หน้าที่ความรับผิดชอบอย่างนึงถูกแยกออกจากกันไปอยู่ในหลายคลาสสิ่งนี้เกิดขึ้นหลังจากการทำ [Divergent Change](03-Change_Preventers/02-Shotgun_Surgery.md) มากเกินไป

## Treatment : การบำรุงรักษา

ใช้ [Move Method](https://sourcemaking.com/refactoring/move-method) และ [Move Field](https://sourcemaking.com/refactoring/move-field)เพื่อย้ายปรฤติกรรมของคลาสที่มีอยู่ไปอยู่รวมกับในคลาสเดียวถ้าไม่มีคลาสไหนเหมาะสมให้สร้างคลาสใหม่ขึ้นมา

![Shotgun-Surgery-02](https://sourcemaking.com/images/refactoring-illustrations/2x/shotgun-surgery-2.png)

ถ้าการย้ายโค้ดไปยังคลาสเดียวกัน ทำให้คลาสเดิมเกือบที่จะว่างเปล่าคุณควรพยายามที่จะหนีจาก now-redundant class (คลาสปัจจุบันที่ซ้ำซ้อน) โดย [Inline Class](https://sourcemaking.com/refactoring/inline-class)

## Payoff : ผลของการขจัดกลิ่นนี้

- การจัดการที่ดีขึ้น
- มีโค้ดที่ซ้ำกันน้อยลง
- ง่ายต่อการดูแลรักษา

![Shotgun-Surgery-02](https://sourcemaking.com/images/refactoring-illustrations/2x/shotgun-surgery-3.png)
