# Duplicate Code (การซ้ำกันของโค้ด)

### Signs and Symptoms : สัญญาณและอาการของปัญหา

Fragments ในโค้ดมีส่วนที่คล้ายกันเกือบทุกส่วน

### Reasons for the Problem : สาเหตุของปัญหา

- สาเหตุหลักๆที่มักทำให้เกิดการซ้ำกันของโค้ด คือการที่นักพัฒนาหลายคนทำงานเดียวกัน ในเวลาเดียวกัน ซึ่งทำให้หลายครั้งพวกเขาไม่รู้ว่าคนอื่นในทีมได้ทำการเขียนโค้ดนั้นๆไปแล้ว ซึ่งสามารถนำมาใช้ใหม่ได้
- นอกจากนี้ยังมีการทำซ้ำกันโดยการที่ลักษณะภายนอก เหมือนจะแตกต่างกันแต่จริงๆการทำงานภายในเหมือนกัน ซึ่งการซ้ำกันแบบนี้หาและแก้ไขได้ยากมาก

### Treatment : วิธีปรับปรุง

- หากพบโค้ดที่เหมือนกันในสองเมธอดหรือมากกว่า ภายในคลาสเดียวกันให้ใช้ [Extract Method](https://sourcemaking.com/refactoring/extract-method) และทำการเรียกใช้เมธอดใหม่ในทั้งสองที่
- หากพบโค้ดเดียวกันในสองคลาสย่อยที่อยู่ในlevelเดียวกัน:

  - ใช้ [Extract Method](https://sourcemaking.com/refactoring/extract-method) สำหรับทั้งสองคลาสตามด้วย [Pull Up Field](https://sourcemaking.com/refactoring/pull-up-field) สำหรับฟิลด์ที่อยู่ในเมธอดนั้น
  - หากโค้ดที่ซ้ำกันอยู่ภายในตัวสร้างให้ใช้ [Pull Up Constructor Body](https://sourcemaking.com/refactoring/pull-up-constructor-body) คือการสร้าง superclass constructor และย้ายไปโค้ดของ subclasses ที่มีลักษณะคล้ายกันไปไว้ และเรียกใช้งาน Superclass constructor ใน subclasses constructor
  - ถ้าโค้ดที่ซ้ำกันคล้ายกัน แต่ไม่เหมือนกันทั้งหมดให้ใช้ [Form Template Method](https://sourcemaking.com/refactoring/form-template-method)
  - หากสอง methods ทำสิ่งเดียวกัน แต่ใช้อัลกอริทึมที่แตกต่างกัน ให้เลือกอัลกอริทึมที่ดีที่สุดและใช้อัลกอริทึมนั้นทดแทน หรือ [Substitute Algorithm](https://sourcemaking.com/refactoring/substitute-algorithm)

- หากพบโค้ดที่ซ้ำกันในสองคลาสที่แตกต่างกัน:

  - ถ้าคลาสไม่ได้เป็นส่วนหนึ่งของลำดับชั้น หรือ hierarchy ให้ใช้ [Extract Superclass](https://sourcemaking.com/refactoring/extract-superclass) เพื่อสร้าง superclass เดียวสำหรับคลาสอื่นๆ เพื่อคงการทำงานก่อนหน้านี้ทั้งหมด
  - หากสร้าง Superclass ได้ยากหรือเป็นไปไม่ได้เลย ให้ใช้วิธี [Extract Class](https://sourcemaking.com/refactoring/extract-class) ในคลาสหนึ่งและใช้ components ใหม่ในอีกคลาส

- หากมี expression ที่มีเงื่อนไขจำนวนมาก และทำงานอยู่ในโค้ดเดียวกัน (แตกต่างกันในเงื่อนไขเท่านั้น) ให้รวมตัวดำเนินการเหล่านี้เป็นเงื่อนไขเดียวโดยใช้ [Consolidate Conditional Expression](https://sourcemaking.com/refactoring/consolidate-conditional-expression) และใช้ [Extract Method](https://sourcemaking.com/refactoring/extract-method) เพื่อวางเงื่อนไขใน method แยกต่างหาก ซึ่งควรตั้งชื่อที่เข้าใจง่าย

- หากมีการใช้ expession ที่เหมือนกันในทุกๆ branch ให้วางโค้ดที่เหมือนกันไว้ด้านนอกของโครงสร้างเงื่อนไขโดยใช้ [Consolidate Duplicate Conditional Fragments](https://sourcemaking.com/refactoring/consolidate-duplicate-conditional-fragments)

### Payoff : ผลลัพธ์

- การรวมโค้ดที่ซ้ำกันทำให้โครงสร้างของโค้ดง่ายขึ้นและทำให้โค้ดสั้นลง
- ง่าย + สั้น = code ที่ง่ายต่อการลดความซับซ้อนและง่ายในการรองรับ

### When to ignore : เราสามารถให้มีการซ้ำกันของโค้ดได้เมื่อไหร่?

ในบางกรณีที่หายากมากๆ การรวมส่วนของโค้ดที่เหมือนกันสองชิ้นเข้าด้วยกัน อาจทำให้โค้ดเข้าใจยากละชัดเจนน้อยลง
