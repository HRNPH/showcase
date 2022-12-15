---
date: "9-7-22"
title: "Image Transfer Day-to-Night and Night-to-Day"
builder: "ณฐกร คเชนทร (เท็น)"
builder_info: ""
thumbnail: "/images/2022/29/01.jpg"
links:
    github: "https://github.com/TENet1010/cycleGAN_Night2day"
    facebook: "https://facebook.com/aibuildersx/posts/411124194389359"
    blog: "https://medium.com/@nattakorn2713/image-transfer-night-to-day-and-day-to-night-2086edc6b298"
---

![image](/images/2022/29/01.jpg)

- เริ่มด้วยปัญหาเวลาเล่น social media ต่างๆแล้วเจอคลิปที่ถ่ายสิ่งลี้ลับ, อะไรที่ดูน่ากลัว หรือพลังงานบางอย่าง เมื่อถูกจับภาพไว้ได้ก็มักจะเป็นภาพที่ไม่ชัดและส่วนใหญ่เป็นตอนกลางคืน บางทีสิ่งเหล่านี้อาจเกินจากการตีความที่ผิดพลาดเนื่องจากละเอียดหายไปกับความมืดจึงอยากที่จะเปลี่ยนภาพพวกนี้ให้เป็นตอนกลางวันสดใส เพื่อดึงรายละเอียดที่หายได้กับความมืดกลับมา,
- สาเหตุของความไม่ชัดคาดว่าเกิดจาก ความไวแสง (ISO; ยิ่งเพิ่มยิ่งสว่างแต่อยากทำให้เกิด noise), F-stop (เมื่อค่า F-stop ต่ำรูปจะชัดเพียงที่โฟกัสและสว่าง แต่ถ้าค่า F-stop มากก็จะทำให้ชัดทั้งภาพ แต่ภาพก็จะมืด), รวมถึงคุณภาพของกล้องและเลนส์,
- วิธีแก้โดยไม่ใช้ ML เช่น ใช้ Adobe Lightroom ปรับค่า exposure แต่ก็จะทำให้เสียคุณภาพของรูปไป,
- ใช้ CycleGAN ในการทำ image-to-image translation; ข้อดีคือไม่จำเป็นต้องใช้คู่รูปกลางวัน-กลางคืนของรูปเดียวกันเพราะ CycleGAN ใช้วิธี optimize ค่า cycle-consistency loss จากรูปภาพเดียวกันที่ถูกแปลงจากกลางวันเป็นกลางคืน หรือกลับกัน,
- ใช้ PatchGAN เป็น discriminator และ generator เป็น autoencoder ที่มี residual block 9 ชั้น,
- ทดลองรูปภาพจาก Aachen Day-Night dataset, Day-night Dataset จาก Kaggle, Mapillary Vistas Dataset, Day time and Night time road Images, Dataset Night city image; สุดท้ายใช้ภาพกลางวันจาก Mapillary Vistas Dataset และกลางคืนจาก Dataset Night city image อย่างละ 2,500 ภาพเป็น training set และอย่างละ 600 ภาพเป็น test set,
- แปลงรูปภาพได้ค่อนข้างน่าพอใจหลังเทรนไป 55 epochs; หลัง error analysis พบภาพที่ผิด เช่น การเติมแสงไฟในรูปที่ไม่ควรเติมเมื่อแปลงรูปจากกลางวันเป็นกลางคืน คาดว่าอาจเกิดจากการที่ใน Dataset มี ภาพที่เป็นแสงไฟจากเมืองรถค่อนข้างมาก, ภาพจริงมีสะพานอยู่ แต่ภาพที่โมเดลสร้างขึ้นได้ลบสะพานให้กลายเป็นท้องฟ้า คาดว่าน่าจะเกิดจากการที่สะพานอยู่ซ้อนทับกับท้องฟ้าเลยอาจทำให้โมเดลคิดว่าสะพานเป็นส่วนหนึ่งของท้องฟ้า,
- ใช้ FID score (Fréchet inception distance) ในการวัดคุณภาพ ในการ generate ภาพ FID score วัดได้โดยการนำรูปที่ generate หลายๆรูปกับภาพจริงจำนวนเท่ามาโยนเข้า inception v3 แล้วนำ distribution ของภาพจริงและภาพที่ generate มาเทียบกัน โดย FID ยิ่งน้อยเท่าไรก็นิ่งดีเท่านั้น; night-to-day FID = 75.68 vs day-to-night FID = 57.80 คาดว่าการเปลี่ยนภาพกลางวันเป็นกลางคืนนั้นเป็นการลดรายละเอียดของภาพซึ่งทำได้ง่ายกว่า night to day ที่เป็นการเพิ่มรายละเอียดของภาพ

### แรงจูงในในการเข้าร่วมโครงการ (จากใบสมัครเข้าร่วมเมื่อ 10 สัปดาห์ที่แล้ว)

> "เราให้นิยามตัวเองว่าเป็นคนที่มีความพยายามต่องานที่ทำอยู่เสมอ จึงมั่นใจได้ว่าเราจะทำโปรเจคนี้อย่างเต็มความสามารถ เรามีความรู้ในการเขียนโปรแกรมภาษา python มาจากการศึกษาด้วยตนเองเพื่อทำ project ในโรงเรียนและมีความกระตือรือร้นที่จะเรียนรู้อีก เรายังได้ทำการศึกษาการเขียนโปรแกรมมาหลากหลายผ่านการเข้าค่ายโอลิมปิกวิชาการคอมพิวเตอร์ค่าย 2 ที่ทำให้เราได้เข้าใจ algorithm ที่หลากหลาย เราได้ร่วมพัฒนาโครงการเครื่องให้อาหารแมวที่ควบคุมบน Web Application และทำงานร่วมกับระบบ IoT โดยตลอดเวลาที่ทำงานเหล่านั้นเราศึกษาบนเว็บต่างประเทศจึงสามารถอ่าน, แปล, และทำความเข้าใจบทความหรือ paper ภาษาอังกฤษได้ดีมาก เรามีแรงบันดาลใจในการสร้าง AI แก้ปัญหาในชีวิตประจำวัน แม้จะเป็นปัญหาเฉพาะกลุ่มแต่ก็สามารถสร้างความแปลกใหม่ได้ เราคาดหวังอย่างยิ่งว่าจะได้รับโอกาสในการทำความฝันนั้นให้เป็นจริง  ปฏิเสธไม่ได้ว่า Artificial Intelligence ได้เข้ามาบทบาทอย่างมากในปัจจุบัน ทั้งช่วยย่นการทำงานของมนุษย์ ช่วยจำแนกหรือวิเคราะห์ข้อมูลที่ซับซ้อน แนะนำ content ที่เกี่ยวข้อง หรือแม้แต่ช่วยตัดสินใจ แต่ก็ใช่ว่า AI จะสามารถทำได้ทุกอย่างหรือแม้แต่การทำงานออกมาได้ perfect 100% ก็เป็นไปได้ยากหากขาด dataset , การจัดการข้อมูลที่ดี หรือ วิธีการ train model ที่เหมาะสม ซึ่งสิ่งนี้จำเป็นต้องศึกษาเพิ่มเติมกว่าความรู้ในม.ปลายไปมาก และจำเป็นต้องพึ่งพาผู้ที่มีประสบการณ์มากกว่า  เราสนใจโครงการ AI Builder ตั้งแต่ปีที่แล้ว แม้จะไม่ผ่านรอบคัดเลือกตัวจริงแต่ก็ได้ศึกษาเนื้อหาไปบ้างในแบบของนักเรียน sit-in หลังจากเห็นโครงงานของเพื่อนหลายคนก็ทำให้เรามีไฟที่อยากจะมาลองสมัครรอบของปีนี้อีก! AI Builder มีเนื้อหาที่เข้มข้นและสิ่งที่สำคัญคือการมี mentor ที่เชี่ยวชาญ และกลุ่มเพื่อนเข้ามาช่วยให้คำปรึกษา เราจึงคิดว่าหากได้เข้าร่วมโครงการนี้แล้ว คงจะได้พัฒนาฝีมือตัวเองให้ดีขึ้นและเข้าใจถึงการพัฒนาโปรเจค AI อย่างเต็มรูปแบบจนอาจสามารถตกตะกอนความรู้และถ่ายทอดให้ผู้อื่นได้ในภายหลัง"