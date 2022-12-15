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

> "เพราะโครงการ AI Builders และ อาจารย์หรือนักวิจัยหลายๆที่ได้รับเชิญเป็นหนึ่งในแรงบันดาลใจ ทำให้เริ่มต้นเส้นทางสาย AI ด้วยการศึกษาจากในอินเตอร์และเน็ตจึงทำให้มีพื้นฐาน ภาษาpython การใช้ numpy pandas ในการจัดการข้อมูล แล้วนำมาทำ Data visualization สามารถทำ web scraping ได้ รู้จักโมเดล machine learning ต่างๆ มีพื้นฐาน deep learning เล็กน้อย  เหตุผลที่ทำให้อยากเข้าร่วมโครงการเริ่มจากในปีที่แล้วได้เห็นโครงการที่มีชื่อว่า AI Builders และเกิดความสนใจเป็นอย่างมากแต่เนื่องจากปิดรับสมัคร จึงตัดสินใจติดตามกิจกรรมที่ได้ลงย้อนหลังใน facebook เป็นจุดเริ่มต้นที่จุดประกายความชอบด้าน AI จึงได้เริ่มศึกษาการเขียนโปรแกรมภาษา python และ library ต่างๆที่ใช้การจัดข้อมูลทำให้รู้สึกสนุกกับคณิตศาสตร์มากขึ้นเพราะไม่ได้ใช้คิดคำนวนเพียงในห้องเรียน แต่สามารถนำมาประยุกต์ตอบปัญหาต่างๆได้ ต่อมาค่อยศึกษาด้าน AI มากขึ้นพบว่าศาสตร์นี้มีความน่าหลงใหล ทั้งในเรื่องของการใช้แก้ปัญหา และ ในด้านแนวคิดเชิงปรัชญาในกระบวนการทำงานของ AI เมื่อโอกาศที่ดีอย่างโครงการนี้กลับมาอีกครั้งผมเลยคิดว่าต้องลงให้ได้ ถ้าได้รับคัดเลือกผมจะนำความรู้ด้านต่างๆ เช่น NLP image pocessing ฯลฯ และ ประสบการณ์ที่ได้ถ่ายถอด เหล่าพี่ๆ mentor ไปทำ project ที่ก่อให้เกิดประโยชน์ต่อสังคมไม่มากก็น้อย ขอบคุณครับ  ปัญหาเมื่อมีการบึกทึกภาพในที่มืดแล้วนั้นทำให้รายละละเอียดภายในภาพไม่ชัดเจนและคลุมเครือ และ อาจนําไปสู่การตีความสิ่งอยู่ในภาพผิดไปจากความเป็นจริง ซึ่งการเพิ่มแสงด้วยโปรแกรมแต่งภาพจะทำให้รายละละเอียดไปได้หากไฟล์คุณภาพต่ำ ผมจึงอยากจะทำAI ที่สามารถ generate ภาพจากภาพที่มืดและมีรายละเอียดไม่ชัดเจนให้มีความสว่างให้สามารถมองเห็นสีและรายละเอียดวัตถุภายในภาพได้ชัดเจนเหมือนตอนกลางวัน ในส่วนของ Data set จะเป็นถ่ายภาพในสถาที่และมุมกล้องเดี่ยวกันแต่แบ่งออกเป็น ภาพที่สว่าง และ ภาพที่มืด"