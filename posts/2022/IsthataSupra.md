---
date: "20-7-22"
title: "Is that a Supra?!"
builder: "จิตรบุณย์ ทรัพย์สินทวีลาภ (กั๊ต)"
builder_info: ""
thumbnail: "/images/2022/40/01.jpg"
links:
    github: "https://github.com/BikiniGordon/Is-that-a-Supra"
    facebook: "https://facebook.com/aibuildersx/posts/418635413638237"
    blog: "https://medium.com/@gatchanminecraft/is-that-a-supra-thai-version-405cb2231f2b"
---

![image](/images/2022/40/01.jpg)

- โมเดลแยกรุ่นรถโตโยต้าจากรูปภาพรวม 36 รุ่นที่เป็นที่นิยมในประเทศไทย; แรงบันดาลใจจากคุณพ่อผู้เป็นอดีตวิศวกรโตโยต้า นั่งรถไปด้วยกันแล้วถามชื่อรุ่น บางครั้งคุณพ่อตอบไม่ได้เนื่องจากเป็นรถรุ่นใหม่หลังจากที่คุณพ่อออกจากบริษัทแล้วจึงมึความคิดว่า “ถ้าเรามีระบบที่เราสามารถโยนรูปไป แล้วระบบตอบกลับมาเป็นชื่อรุ่นเลยก็คงจะดี”,
- เริ่มจากการใช้ชุดข้อมูลที่จัดทำโดย Occulta Insights บน Kaggle ประกอบด้วยรถ 38 รุ่น แต่มีรุ่นที่เป็นที่นิยมในประเทศไทยน้อย เช่น Vios มีเพียง 141 รูป และไม่มีการแยกรุ่นย่อย เช่น yaris ativ หรือ corolla altis,
- ทำความสะอาดข้อมูล ประเภทรูปที่ไม่ได้ใช้คือ รูปภายในรถ, รูปเครื่องยนต์รถ, รูปที่เจาะจงเฉพาะบางส่วนมากเกินไป และรูปรถคนละรุ่น; มีรูปที่คัดออกทั้งหมด 2,203 จากประมาณ 16,000 รูป หรือประมาณ 13.5% ของจำนวนรูปภาพทั้งหมด,
- แบ่งข้อมูลเป็น train-validation-test ที่ 70-15-15; เริ่มเทรนด้วยการปรับจูน resnet34 (freeze 1 epoch; unfreeze 5 epochs) ได้ balanced accuracy 57%; พบว่ารุ่นที่มีรูปน้อย เช่น estima, revo และ rush ทำให้ได้ผลแย่,
- แก้ปัญหาด้วยความรู้เกี่ยวกับรถโตโยต้า ได้แก่ 1) ยุบ revo รวมกับ hilux เนื่องจากเป็นรุ่นเดียวกัน 2) ใช้ DuckDuckGo Image Search API หารูปมาเพิ่มสำหรับรุ่นที่มีรูปน้อย 3) ตัด previa ออกเนื่องจากเป็นรุ่นเดียวกับ estima ต่างกันเพียงแค่โซนยุโรปกับเอเชีย 4) ตัด avalon ออก เนื่องจากหน้าตาคล้าย camry และมีขายเพียงแค่ในสหรัฐอเมริกา 5) เพิ่มรูปด้านหลังของ avanza เข้าไปเนื่องจากเดิมมีรูปน้อย 6) เนื่องจาก celica, crown, corona รุ่นเก่าจะมีหน้าตาคล้ายกันมาก จึงเลือกเฉพาะ celica 6-7th generation, crown 12-15th generation ที่ยังมีวิ่งให้เห็นตามท้องถนนเท่านั้น 7) หารูป hilux เพิ่ม 8 ) ตัด vitz ออกเนื่องจากเป็นเพียง yaris ดัดแปลงเล็กน้อย มีขายเฉพาะในญี่ปุ่น 9) เพิ่ม wish ที่มีความนิยมสูงในไทย 10) ตัด vios 3rd generation ออกเนื่องจากโครงเหมือน yaris ativ 10) ตัด verso ออกเนื่องจากไม่มีขายในไทย 11) เพิ่ม c-hr และ sienta ที่เป็นที่นิยมในไทย,
- จากการแก้ปัญหาแบบ data centric ทั้งหมดด้านบนทำให้ได้ balanced accuracy เพิ่มเป็น 89% จาก 36 รุ่น

### แรงจูงในในการเข้าร่วมโครงการ (จากใบสมัครเข้าร่วมเมื่อ 10 สัปดาห์ที่แล้ว)

> "เราให้นิยามตัวเองว่าเป็นคนที่มีความพยายามต่องานที่ทำอยู่เสมอ จึงมั่นใจได้ว่าเราจะทำโปรเจคนี้อย่างเต็มความสามารถ เรามีความรู้ในการเขียนโปรแกรมภาษา python มาจากการศึกษาด้วยตนเองเพื่อทำ project ในโรงเรียนและมีความกระตือรือร้นที่จะเรียนรู้อีก เรายังได้ทำการศึกษาการเขียนโปรแกรมมาหลากหลายผ่านการเข้าค่ายโอลิมปิกวิชาการคอมพิวเตอร์ค่าย 2 ที่ทำให้เราได้เข้าใจ algorithm ที่หลากหลาย เราได้ร่วมพัฒนาโครงการเครื่องให้อาหารแมวที่ควบคุมบน Web Application และทำงานร่วมกับระบบ IoT โดยตลอดเวลาที่ทำงานเหล่านั้นเราศึกษาบนเว็บต่างประเทศจึงสามารถอ่าน, แปล, และทำความเข้าใจบทความหรือ paper ภาษาอังกฤษได้ดีมาก เรามีแรงบันดาลใจในการสร้าง AI แก้ปัญหาในชีวิตประจำวัน แม้จะเป็นปัญหาเฉพาะกลุ่มแต่ก็สามารถสร้างความแปลกใหม่ได้ เราคาดหวังอย่างยิ่งว่าจะได้รับโอกาสในการทำความฝันนั้นให้เป็นจริง  ปฏิเสธไม่ได้ว่า Artificial Intelligence ได้เข้ามาบทบาทอย่างมากในปัจจุบัน ทั้งช่วยย่นการทำงานของมนุษย์ ช่วยจำแนกหรือวิเคราะห์ข้อมูลที่ซับซ้อน แนะนำ content ที่เกี่ยวข้อง หรือแม้แต่ช่วยตัดสินใจ แต่ก็ใช่ว่า AI จะสามารถทำได้ทุกอย่างหรือแม้แต่การทำงานออกมาได้ perfect 100% ก็เป็นไปได้ยากหากขาด dataset , การจัดการข้อมูลที่ดี หรือ วิธีการ train model ที่เหมาะสม ซึ่งสิ่งนี้จำเป็นต้องศึกษาเพิ่มเติมกว่าความรู้ในม.ปลายไปมาก และจำเป็นต้องพึ่งพาผู้ที่มีประสบการณ์มากกว่า  เราสนใจโครงการ AI Builder ตั้งแต่ปีที่แล้ว แม้จะไม่ผ่านรอบคัดเลือกตัวจริงแต่ก็ได้ศึกษาเนื้อหาไปบ้างในแบบของนักเรียน sit-in หลังจากเห็นโครงงานของเพื่อนหลายคนก็ทำให้เรามีไฟที่อยากจะมาลองสมัครรอบของปีนี้อีก! AI Builder มีเนื้อหาที่เข้มข้นและสิ่งที่สำคัญคือการมี mentor ที่เชี่ยวชาญ และกลุ่มเพื่อนเข้ามาช่วยให้คำปรึกษา เราจึงคิดว่าหากได้เข้าร่วมโครงการนี้แล้ว คงจะได้พัฒนาฝีมือตัวเองให้ดีขึ้นและเข้าใจถึงการพัฒนาโปรเจค AI อย่างเต็มรูปแบบจนอาจสามารถตกตะกอนความรู้และถ่ายทอดให้ผู้อื่นได้ในภายหลัง"