---
date: "1-8-22"
title: "American Sign Language"
builder: "กรกมล แสงสว่าง (เบลล์)"
builder_info: ""
thumbnail: "/images/2022/52/01.jpg"
links:
    github: "https://github.com/Berubell9/American-sign-language"
    facebook: "https://facebook.com/aibuildersx/posts/434912155343896"
    blog: "https://medium.com/@15192/american-sign-language-asl-b9f1c1a6dc01"
---

![image](/images/2022/52/01.jpg)

- แรงบันดาลใจจากการดูวิดีโอที่มีชื่อว่า “ครู…โลกเงียบ” ของ 7Eleven ที่แสดงให้เห็นถึงครูที่เข้าใจหัวอกของเด็กสาวที่ชื่อว่า “บัว” ซึ่งเธอเป็นผู้พิการที่มีความบกพร่องทางการได้ยิน แต่กลับกันแม่ของเธอกลับไม่เข้าใจถึงโลกที่เธออยู่ และเพิกเฉยต่อสิ่งที่เธอเป็น ทำให้เด็กสาวมีความพยายามที่อยากจะพูดให้ได้ เพื่อที่จะให้แม่ของเธอเข้าใจในสิ่งที่เธอนั้นต้องการ (https://www.youtube.com/watch?v=8n6ocbjrZw8),
- พบข้อจำกัดคือไม่มีชุดข้อมูลภาษามือไทยจึงเริ่มทำโครงงานด้วยชุดข้อมูลตัวอักษรภาษามืออเมริกัน American sign language (ASL) ได้แก่ A , B, C, D, F, G, H, I, J, K, L, M, N, O, P, Q, R, S, T, U, V, W, X, Y, Z, Nothing, Space และ Del,
- ชุดข้อมูลรวบรวมจาก open source บน Kaggle จำนวน 7 แหล่ง; ทำความสะอาดข้อมูลจาก 352,647 รูป คัดอย่างละเอียดเหลือ 14,498 รูป (หนึงประเภทตัวอักษรมีข้อมูลประมาณ 500 รูป),
- ปรับจูนสถาปัตยกรรม ResNet50 จำนวน 30 epoch ได้ accuracy บน test set (แบ่ง 90/10) ที่ 71%,
- พบตัวอักษรที่ใช้สัญลักษณ์มือคล้ายกันทำให้โมเดลอาจจะจำผิดพลาด เช่น A กับ E, S กับ T, G กับ Z เป็นต้น

### แรงจูงในในการเข้าร่วมโครงการ (จากใบสมัครเข้าร่วมเมื่อ 10 สัปดาห์ที่แล้ว)

> "เราให้นิยามตัวเองว่าเป็นคนที่มีความพยายามต่องานที่ทำอยู่เสมอ จึงมั่นใจได้ว่าเราจะทำโปรเจคนี้อย่างเต็มความสามารถ เรามีความรู้ในการเขียนโปรแกรมภาษา python มาจากการศึกษาด้วยตนเองเพื่อทำ project ในโรงเรียนและมีความกระตือรือร้นที่จะเรียนรู้อีก เรายังได้ทำการศึกษาการเขียนโปรแกรมมาหลากหลายผ่านการเข้าค่ายโอลิมปิกวิชาการคอมพิวเตอร์ค่าย 2 ที่ทำให้เราได้เข้าใจ algorithm ที่หลากหลาย เราได้ร่วมพัฒนาโครงการเครื่องให้อาหารแมวที่ควบคุมบน Web Application และทำงานร่วมกับระบบ IoT โดยตลอดเวลาที่ทำงานเหล่านั้นเราศึกษาบนเว็บต่างประเทศจึงสามารถอ่าน, แปล, และทำความเข้าใจบทความหรือ paper ภาษาอังกฤษได้ดีมาก เรามีแรงบันดาลใจในการสร้าง AI แก้ปัญหาในชีวิตประจำวัน แม้จะเป็นปัญหาเฉพาะกลุ่มแต่ก็สามารถสร้างความแปลกใหม่ได้ เราคาดหวังอย่างยิ่งว่าจะได้รับโอกาสในการทำความฝันนั้นให้เป็นจริง  ปฏิเสธไม่ได้ว่า Artificial Intelligence ได้เข้ามาบทบาทอย่างมากในปัจจุบัน ทั้งช่วยย่นการทำงานของมนุษย์ ช่วยจำแนกหรือวิเคราะห์ข้อมูลที่ซับซ้อน แนะนำ content ที่เกี่ยวข้อง หรือแม้แต่ช่วยตัดสินใจ แต่ก็ใช่ว่า AI จะสามารถทำได้ทุกอย่างหรือแม้แต่การทำงานออกมาได้ perfect 100% ก็เป็นไปได้ยากหากขาด dataset , การจัดการข้อมูลที่ดี หรือ วิธีการ train model ที่เหมาะสม ซึ่งสิ่งนี้จำเป็นต้องศึกษาเพิ่มเติมกว่าความรู้ในม.ปลายไปมาก และจำเป็นต้องพึ่งพาผู้ที่มีประสบการณ์มากกว่า  เราสนใจโครงการ AI Builder ตั้งแต่ปีที่แล้ว แม้จะไม่ผ่านรอบคัดเลือกตัวจริงแต่ก็ได้ศึกษาเนื้อหาไปบ้างในแบบของนักเรียน sit-in หลังจากเห็นโครงงานของเพื่อนหลายคนก็ทำให้เรามีไฟที่อยากจะมาลองสมัครรอบของปีนี้อีก! AI Builder มีเนื้อหาที่เข้มข้นและสิ่งที่สำคัญคือการมี mentor ที่เชี่ยวชาญ และกลุ่มเพื่อนเข้ามาช่วยให้คำปรึกษา เราจึงคิดว่าหากได้เข้าร่วมโครงการนี้แล้ว คงจะได้พัฒนาฝีมือตัวเองให้ดีขึ้นและเข้าใจถึงการพัฒนาโปรเจค AI อย่างเต็มรูปแบบจนอาจสามารถตกตะกอนความรู้และถ่ายทอดให้ผู้อื่นได้ในภายหลัง"