---
date: "1-7-22"
title: "BACK (Blind All Can Know) - Action Captioning for Blinds"
builder: "โชติวัฒน์ ตั้งสถาพร (ไนน์)"
builder_info: ""
thumbnail: "/images/2022/21/01.jpg"
links:
    github: "https://colab.research.google.com/github/cninet/BACK/blob/main/BACK.ipynb"
    facebook: "https://facebook.com/aibuildersx/posts/405337768301335"
    blog: "https://medium.com/@cninet.std/back-blind-all-can-know-action-captioning-a10a3fa85695"
---

![image](/images/2022/21/01.jpg)

- โมเดลอธิบายรูปภาพ (image captioning) เพื่ออธิบายภาพตรงหน้าให้กับผู้พิการทางสายตา,
- CLIPCap นำ pretrained CLIP เพื่อสร้าง image embeddings เป็น input ให้กับ pretrained GPT2 สร้างข้อความที่ตรงกับภาพ,
- เทรนโมเดลด้วย Flickr30k (รูป-คำบรรยายภาษาอังกฤษ) เป็นเวลา 17 ชั่วโมง (10 epochs),
- ตัดสินใจใช้ Flickr30k ทั้งที่จำนวนข้อมูลน้อยกว่า COCO เพราะทำแบบสอบถามแล้วพบว่าข้อมูลคำบรรยายของ Flickr30k มีคุณภาพมากกว่า,
- ใช้ PyThaiNLP Translate ในการแปลภาษาคำบรรยายเป็นภาษาไทย เนื่องจากแบบสอบถามพบว่าเป็นธรรมชาติกว่า Google Translate API ในบริบทนี้,
- ใช้ Google TTS ในการเปลี่ยนคำบรรยายที่ถูกแปลเป็นเสียงพูด,
- นอกจากการเทรนโมเดล CLIPCap ตรง ๆ แล้วยังมีการนำมาประกอบการใช้งานกับ pretrained models อื่น ๆ เช่น PyThaiNLP Translate และ Google TTS อีกทั้งการต่อสู้กับคุณภาพข้อมูลอย่างสมศักดิ์ศรี เช่น ลบรูปซ้ำ, แก้ข้อมูลตาราง, แก้คำบรรยายที่มีมากกว่าหนึ่งประโยคต่อกัน ฯลฯ

### แรงจูงในในการเข้าร่วมโครงการ (จากใบสมัครเข้าร่วมเมื่อ 10 สัปดาห์ที่แล้ว)

> "เราให้นิยามตัวเองว่าเป็นคนที่มีความพยายามต่องานที่ทำอยู่เสมอ จึงมั่นใจได้ว่าเราจะทำโปรเจคนี้อย่างเต็มความสามารถ เรามีความรู้ในการเขียนโปรแกรมภาษา python มาจากการศึกษาด้วยตนเองเพื่อทำ project ในโรงเรียนและมีความกระตือรือร้นที่จะเรียนรู้อีก เรายังได้ทำการศึกษาการเขียนโปรแกรมมาหลากหลายผ่านการเข้าค่ายโอลิมปิกวิชาการคอมพิวเตอร์ค่าย 2 ที่ทำให้เราได้เข้าใจ algorithm ที่หลากหลาย เราได้ร่วมพัฒนาโครงการเครื่องให้อาหารแมวที่ควบคุมบน Web Application และทำงานร่วมกับระบบ IoT โดยตลอดเวลาที่ทำงานเหล่านั้นเราศึกษาบนเว็บต่างประเทศจึงสามารถอ่าน, แปล, และทำความเข้าใจบทความหรือ paper ภาษาอังกฤษได้ดีมาก เรามีแรงบันดาลใจในการสร้าง AI แก้ปัญหาในชีวิตประจำวัน แม้จะเป็นปัญหาเฉพาะกลุ่มแต่ก็สามารถสร้างความแปลกใหม่ได้ เราคาดหวังอย่างยิ่งว่าจะได้รับโอกาสในการทำความฝันนั้นให้เป็นจริง  ปฏิเสธไม่ได้ว่า Artificial Intelligence ได้เข้ามาบทบาทอย่างมากในปัจจุบัน ทั้งช่วยย่นการทำงานของมนุษย์ ช่วยจำแนกหรือวิเคราะห์ข้อมูลที่ซับซ้อน แนะนำ content ที่เกี่ยวข้อง หรือแม้แต่ช่วยตัดสินใจ แต่ก็ใช่ว่า AI จะสามารถทำได้ทุกอย่างหรือแม้แต่การทำงานออกมาได้ perfect 100% ก็เป็นไปได้ยากหากขาด dataset , การจัดการข้อมูลที่ดี หรือ วิธีการ train model ที่เหมาะสม ซึ่งสิ่งนี้จำเป็นต้องศึกษาเพิ่มเติมกว่าความรู้ในม.ปลายไปมาก และจำเป็นต้องพึ่งพาผู้ที่มีประสบการณ์มากกว่า  เราสนใจโครงการ AI Builder ตั้งแต่ปีที่แล้ว แม้จะไม่ผ่านรอบคัดเลือกตัวจริงแต่ก็ได้ศึกษาเนื้อหาไปบ้างในแบบของนักเรียน sit-in หลังจากเห็นโครงงานของเพื่อนหลายคนก็ทำให้เรามีไฟที่อยากจะมาลองสมัครรอบของปีนี้อีก! AI Builder มีเนื้อหาที่เข้มข้นและสิ่งที่สำคัญคือการมี mentor ที่เชี่ยวชาญ และกลุ่มเพื่อนเข้ามาช่วยให้คำปรึกษา เราจึงคิดว่าหากได้เข้าร่วมโครงการนี้แล้ว คงจะได้พัฒนาฝีมือตัวเองให้ดีขึ้นและเข้าใจถึงการพัฒนาโปรเจค AI อย่างเต็มรูปแบบจนอาจสามารถตกตะกอนความรู้และถ่ายทอดให้ผู้อื่นได้ในภายหลัง"