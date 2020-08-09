# Code Smells : กลิ่นตุๆ จากโค้ดเน่าเหม็น

## Bloaters : อุ้ยอ้าย

ฺBloaters เป็น code smells ที่เกิดจากโค้ด, method, และหรือ class ต่างๆ มีขนาดใหญ่เกินไปจนทำงานด้วยยาก โดยปกติแล้ว code smells แบบนี้จะไม่เกิดขึ้นในทันที แต่เมื่อพัฒนาโปรแกรมไปเรื่อยๆ ปัญหานี้จะค่อยๆ สะสมจนมากและใหญ่ขึ้นเรื่อยๆ (และโดยเฉพาะอย่างยิ่งเมื่อไม่มีใครพยายามกำจัดมันทิ้งให้สิ้นซาก)

- [Long Method](01-Bloaters/01-Long_Method.md)
- [Large Class](01-Bloaters/02-Large_Class.md)
- [Primitive Obsession](01-Bloaters/03-Primitive_Obsession.md)
- [Long Parameter List](01-Bloaters/04-Long_Parameter_List.md)
- [Data Clumps](01-Bloaters/05-Data_Clumps.md)

## Object-Orientation Abusers

กลิ่นเหม็นๆทั้งหมดนี้คือการใช้หลักการของ object-oriented programming ที่ไม่สมบูรณ์หรือไม่ถูกต้อง

- [Switch Statements](02-Object-Orientation_Abusers/01-Switch_Statements.md)
- [Temporary Field](02-Object-Orientation_Abusers/02-Temporary_Field.md)
- [Refused Bequest](02-Object-Orientation_Abusers/03-Refused_Bequest.md)
- [Alternative Classes with Different Interfaces](02-Object-Orientation_Abusers/04-Alternative_Classes_with_Different_Interfaces.md)

* [Switch Statements](02-Object-Orientation_Abusers/01-Switch_Statements.md)
* [Temporary Field](02-Object-Orientation_Abusers/02-Temporary_Field.md)
* [Refused Bequest](02-Object-Orientation_Abusers/03-Refused_Bequest.md)
* [Alternative Classes with Different Interfaces](02-Object-Orientation_Abusers/04-Alternative_Classes_with_Different_Interfaces.md)

## Change Preventers : ตัวป้องกันการเปลี่ยนแปลง

code smell(กลิ่นตุๆ) นี้หมายความว่าถ้าคุณเปลี่ยนบางอย่างในที่ๆนึงของโค้ดของคุณ คุณจะต้องไปเปลี่ยนโค้ดในจุดๆอื่นด้วยซึ่งผลคือในการพัฒนาโปรแกรมนั้นจะซับซ้อนและยุ่งยาก

- [Divergent Change](03-Change_Preventers/01-Divergent_Change.md)
- [Shotgun Surgery](03-Change_Preventers/02-Shotgun_Surgery.md)
- [Parallel Inheritance Hierarchies](03-Change_Preventers/03-Parallel_Inheritance_Hierarchies.md)

## Dispensables : ความไม่จำเป็น

Dispensable คือบางอย่างที่ไม่มีความจำเป็น และไร้จุดหมาย ซึ่งสิ่งเหล่านี้จะทำให้โค้ดของเราไม่เป็นระเบียบและไม่มีประโยชน์ หากเราสามารถจัดการกับสิ่งเหล่านี้ได้ก็จะทำให้โค้ดสะอาดมากขึ้น มีประสิทธิภาพ และเข้าใจได้ง่ายขึ้น

- [Comments](04-Dispensables/01-Comments.md)
- [Duplicate Code](04-Dispensables/02-Duplicate_Code.md)
- [Lazy Class](04-Dispensables/03-Lazy_Class.md)
- [Data Class](04-Dispensables/04-Data_Class.md)
- [Dead Code](04-Dispensables/05-Dead_Code.md)
- [Speculative Generality](04-Dispensables/06-Speculative_Generality.md)

## Couplers

All the smells in this group contribute to excessive coupling between classes or show what happens if coupling is replaced by excessive delegation.

- [Feature Envy](05-Couplers/01-Feature_Envy.md)
- [Inappropriate Intimacy](05-Couplers/02-Inappropriate_Intimacy.md)
- [Message Chains](05-Couplers/03-Message_Chains.md)
- [Middle Man](05-Couplers/04-Middle_Man.md)

## Other Smells

- [Incomplete Library Class](06-Other_Smells/01-Incomplete_Library_Class.md)
