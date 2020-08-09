# Incomplete Library Class : คลาสคลังชุดข้อมูลที่ไม่สมบูรณ์

## Signs and Symptoms : สัญญาณและอาการ

ไม่ช้าก็เร็ว [libraries](<https://en.wikipedia.org/wiki/Library_(computing)>) ไม่สามารถตอบสนองความต้องการของผู้ใช้ได้ ทางแก้เพียงทางเดียว-การเปลี่ยน library-นั้นมีความเป็นไปได้ที่จะเกิดขึ้นบ่อยตั้งแต่ library นั้นเป็นเพียงการอ่านเพียงอย่างเดียว

## Reasons for the problem : สาเหตุของปัญหา

ผู้เขียน library ไม่ได้ให้คุณสมบัติที่คุณต้องการหรือปฎิเสธที่จะนำคุณสมบัติเหล่านั้นออกมา

## Treatment : การบำรุงรักษา

- เพื่อที่จะแนะนำกระบวนการต่างๆไปยัง คลาสของlibraryใช้ [Introduce Foreign Method](https://sourcemaking.com/refactoring/introduce-foreign-method)
- สำหรับ change ที่มีปริมาณเยอะในคลาสของ libraryใช้ [Introduce Local Extension](https://sourcemaking.com/refactoring/introduce-local-extension)

## Payoff : ผลของการขจัดกลิ่นนี้

ลดการซ้ำซ้อนของโค้ด (แทนที่จะสร้าง library เองตั้งแต่ต้นคุณสามารถที่จะพ่วงกับสิ่งที่มีอยู่แล้วได้)

## When to Ignore : เมื่อไหร่ควรที่จะละเว้น

การขยาย library สามารถสร้างงานเพิ่มเติมได้ถ้า change ใน library เกี่ยวข้องกับ change ในโค้ด
