---
date: "25-7-22"
title: "Lamiaceae Classification แยกพืชวงศ์กะเพรา 3 ชนิด"
builder: "วชิรวิทย์ ไชยมาตย์ (เจ้านาย)"
builder_info: ""
thumbnail: "/images/2022/45/01.jpg"
links:
    github: "https://github.com/KaiZer003/LamiaceaeClassify"
    facebook: "https://facebook.com/aibuildersx/posts/424327439735701"
    blog: "https://medium.com/@wachirawit003/image-classification-%E0%B9%80%E0%B9%80%E0%B8%A2%E0%B8%81%E0%B8%9E%E0%B8%B7%E0%B8%8A%E0%B8%A7%E0%B8%87%E0%B8%A8%E0%B9%8C%E0%B8%81%E0%B8%B0%E0%B9%80%E0%B8%9E%E0%B8%A3%E0%B8%B2-3-%E0%B8%8A%E0%B8%99%E0%B8%B4%E0%B8%94-480b9b823d85"
---

![image](/images/2022/45/01.jpg)

-  พืชวงศ์กระเพราหรือ Lamiaceae มีลักษณะคล้ายคลึงกันมากจนบางครั้งมนุษย์แยกไม่ออก นำมาซึ่งแรงบันดาลใจในการทำโมเดลแยกกะเพรา โหระพา และแมงลักจากรูป,
- วัดผลเทียบกับมนุษย์ 20 คน (ครู 4 นักเรียน 16) ด้วย mini-validation set 30 รูป (พืชชนิดละ 10 รูป) มี accuracy เฉลี่ยที่ 52.16%; ทำได้ดีที่สุด 76.66% (นักเรียน) และ73.33% (นักเรียน),
- รวบรวมข้อมูลด้วยการถ่ายภาพเอง ระหว่างทางพบชุดข้อมูลกะเพรา-โหระพาจาก TAUTOLOGY-EDUCATION Tautology Thailand; แบ่ง test set 20% (177 รูป),
- เลือกทำ data augmentation เช่น zoom, lighting, affine transformation ด้วย fastai,
- ทดสอบกับสถาปัตยกรรม GoogLeNet, ResNet-152 และ VGG-19 พบว่า GoogLeNet ได้ผลดีที่สุดที่ accuracy 95%; resnet152 และ vgg19 ยังมีความสับสนระหว่างโหระพาและแมงลักอยู่เล็กน้อย,
- เทียบกับมนุษย์บน mini-validation set โมเดลทำได้ 86.66% เทียบกับมนุษย์ที่เก่งที่สุดที่ 76.66%,
- ข้อจำกัดของโมเดล ด้วยปริมาณข้อมูลเเละวิธีการเก็บ ทำให้เกิดข้อจำกัดหลายส่วน คือ 1.เก่งกับใบมากกว่าต้น 2.ความเเม่นยำต่ำเมื่อนำไปใช้กับภาพที่มีสภาพเเวดล้อมเป็นพื้นหลัง 3.ข้อมูลที่ใช้เทรนได้มาจากผักตามตลาดทำให้โมเดลไม่เก่งกับภาพพืชที่ได้รับความเสียหายจากสภาพเเวดล้อม 4.ต้องโฟกัสภาพเพื่อให้เห็นรายละเอียดของใบชัดเจนก่อน เพื่อให้โมเดลมีประสิทธิภาพสูงสุด,
- ลองใช้ชุดข้อมูลได้ที่ https://drive.google.com/drive/folders/1hmc1Io_lg4_Q3fMqsmSPD9XpsBZ93FmJ?usp=sharing

### แรงจูงในในการเข้าร่วมโครงการ (จากใบสมัครเข้าร่วมเมื่อ 10 สัปดาห์ที่แล้ว)

> "เราให้นิยามตัวเองว่าเป็นคนที่มีความพยายามต่องานที่ทำอยู่เสมอ จึงมั่นใจได้ว่าเราจะทำโปรเจคนี้อย่างเต็มความสามารถ เรามีความรู้ในการเขียนโปรแกรมภาษา python มาจากการศึกษาด้วยตนเองเพื่อทำ project ในโรงเรียนและมีความกระตือรือร้นที่จะเรียนรู้อีก เรายังได้ทำการศึกษาการเขียนโปรแกรมมาหลากหลายผ่านการเข้าค่ายโอลิมปิกวิชาการคอมพิวเตอร์ค่าย 2 ที่ทำให้เราได้เข้าใจ algorithm ที่หลากหลาย เราได้ร่วมพัฒนาโครงการเครื่องให้อาหารแมวที่ควบคุมบน Web Application และทำงานร่วมกับระบบ IoT โดยตลอดเวลาที่ทำงานเหล่านั้นเราศึกษาบนเว็บต่างประเทศจึงสามารถอ่าน, แปล, และทำความเข้าใจบทความหรือ paper ภาษาอังกฤษได้ดีมาก เรามีแรงบันดาลใจในการสร้าง AI แก้ปัญหาในชีวิตประจำวัน แม้จะเป็นปัญหาเฉพาะกลุ่มแต่ก็สามารถสร้างความแปลกใหม่ได้ เราคาดหวังอย่างยิ่งว่าจะได้รับโอกาสในการทำความฝันนั้นให้เป็นจริง  ปฏิเสธไม่ได้ว่า Artificial Intelligence ได้เข้ามาบทบาทอย่างมากในปัจจุบัน ทั้งช่วยย่นการทำงานของมนุษย์ ช่วยจำแนกหรือวิเคราะห์ข้อมูลที่ซับซ้อน แนะนำ content ที่เกี่ยวข้อง หรือแม้แต่ช่วยตัดสินใจ แต่ก็ใช่ว่า AI จะสามารถทำได้ทุกอย่างหรือแม้แต่การทำงานออกมาได้ perfect 100% ก็เป็นไปได้ยากหากขาด dataset , การจัดการข้อมูลที่ดี หรือ วิธีการ train model ที่เหมาะสม ซึ่งสิ่งนี้จำเป็นต้องศึกษาเพิ่มเติมกว่าความรู้ในม.ปลายไปมาก และจำเป็นต้องพึ่งพาผู้ที่มีประสบการณ์มากกว่า  เราสนใจโครงการ AI Builder ตั้งแต่ปีที่แล้ว แม้จะไม่ผ่านรอบคัดเลือกตัวจริงแต่ก็ได้ศึกษาเนื้อหาไปบ้างในแบบของนักเรียน sit-in หลังจากเห็นโครงงานของเพื่อนหลายคนก็ทำให้เรามีไฟที่อยากจะมาลองสมัครรอบของปีนี้อีก! AI Builder มีเนื้อหาที่เข้มข้นและสิ่งที่สำคัญคือการมี mentor ที่เชี่ยวชาญ และกลุ่มเพื่อนเข้ามาช่วยให้คำปรึกษา เราจึงคิดว่าหากได้เข้าร่วมโครงการนี้แล้ว คงจะได้พัฒนาฝีมือตัวเองให้ดีขึ้นและเข้าใจถึงการพัฒนาโปรเจค AI อย่างเต็มรูปแบบจนอาจสามารถตกตะกอนความรู้และถ่ายทอดให้ผู้อื่นได้ในภายหลัง"