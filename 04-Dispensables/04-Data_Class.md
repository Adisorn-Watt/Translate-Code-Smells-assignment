# Data Class

### Signs and Symptoms : สัญญาณและอาการของปัญหา

คลาสข้อมูลหมายถึงคลาสที่มีเฉพาะฟิลด์และเมธอดคร่าวๆในการเข้าถึงเท่านั้น (getters และ setters) สิ่งเหล่านี้เป็นเพียงคอนเทนเนอร์สำหรับข้อมูลที่คลาสอื่นใช้ คลาสเหล่านี้ไม่มีฟังก์ชันเพิ่มเติมใด ๆ และไม่สามารถดำเนินการกับข้อมูลที่ตนเองเป็นเจ้าของได้อย่างอิสระ

### Reasons for the Problem : สาเหตุของปัญหา

เป็นเรื่องปกติเมื่อคลาสที่สร้างขึ้นใหม่มี pulic field ไม่กี่ฟิล์ด แต่พลังที่แท้จริงของออบเจ็กต์ก็คือสามารถเก็บ behavior type หรือ operations บนข้อมูลได้

### Treatment : วิธีปรับปรุง

- หากคลาสมี public field ให้ใช้ [Encapsulate Field](https://sourcemaking.com/refactoring/encapsulate-field) เพื่อซ่อนไม่ให้เข้าถึงโดยตรงและกำหนดให้เข้าถึงได้ผ่าน getters และ setters เท่านั้น
- ใช้ [Encapsulate Collection](https://sourcemaking.com/refactoring/encapsulate-collection) สำหรับข้อมูลที่จัดเก็บในคอลเลกชัน (เช่นอาร์เรย์)
- ตรวจทานไคลเอ็นต์โค้ดที่ใช้โดยคลาส ในนั้นอาจพบฟังก์ชันการทำงานที่ดีกว่า หากเป็นกรณีนี้ให้ใช้ [Move Method](https://sourcemaking.com/refactoring/move-method) และ [Extract Method](https://sourcemaking.com/refactoring/extract-method) เพื่อย้ายฟังก์ชันนี้ไปยังคลาสข้อมูล

### Payoff : ผลลัพธ์

- ช่วยปรับปรุงความเข้าใจและการจัดระเบียบโค้ด ซึ่งการดำเนินการบนข้อมูลเฉพาะจะถูกรวบรวมไว้ในที่เดียว
- ช่วยให้เห็นการซ้ำซ้อนของไคลเอนต์โค้ด
