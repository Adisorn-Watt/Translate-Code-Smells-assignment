# Dead Code

### Signs and Symptoms : สัญญาณและอาการของปัญหา

ไม่มีการใช้ตัวแปร, พารามิเตอร์, ฟิลด์, เมธอดหรือคลาสอีกต่อไป (โดยปกติจะเป็นเพราะล้าสมัยหรือเลิกใช้แล้ว)

### Reasons for the Problem : สาเหตุของปัญหา

- เมื่อข้อกำหนดสำหรับซอฟต์แวร์มีการเปลี่ยนแปลงหรือมีการแก้ไขไม่มีใครมารับผิดชอบหรือจัดการกับโค้ดเก่า
- โค้ดนั้นๆสามารถพบได้ในเงื่อนไขที่ซับซ้อนมากๆ เมื่อหนึ่งใน branches ไม่สามารถเข้าถึงได้ (เนื่องจากข้อผิดพลาดหรือสถานการณ์อื่นๆ)

### Treatment : วิธีปรับปรุง

- วิธีที่เร็วที่สุดในการค้นหา Dead code คือการใช้ [IDE](https://en.wikipedia.org/wiki/Integrated_development_environment) ที่ดี
- ลบโค้ดที่ไม่ได้ใช้และไฟล์ที่ไม่จำเป็น
- ในกรณีของคลาสที่ไม่จำเป็นสามารถใช้ [Inline Class](https://sourcemaking.com/refactoring/inline-class) หรือ [Collapse Hierarchy](https://sourcemaking.com/refactoring/collapse-hierarchy) ได้หากใช้ subclass หรือ superclass
  ถ้าต้องการลบพารามิเตอร์ที่ไม่จำเป็นให้ใช้ [Remove Parameter](https://sourcemaking.com/refactoring/remove-parameter)

### Payoff : ผลลัพธ์

- ขนาดโค้ดลดลง
- สามารถซับพอร์ตได้ง่ายขึ้น
