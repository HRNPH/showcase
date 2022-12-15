---
date: "12-7-22"
title: "Text-to-image synthesis with VQGAN-ThCLIP"
builder: "ภูริช ศิริทิพย์ (มาร์ค)"
builder_info: ""
thumbnail: "/images/2022/32/01.jpg"
links:
    github: "https://colab.research.google.com/github/vikimark/VQGAN-ThCLIP/blob/master/Streamlit_VQGANxThaiCLIP.ipynb"
    facebook: "https://facebook.com/aibuildersx/posts/413224897512622"
    blog: "https://medium.com/@phuritsiritip/%E0%B9%82%E0%B8%84%E0%B8%A3%E0%B8%87%E0%B8%81%E0%B8%B2%E0%B8%A3-ai-builders-%E0%B8%81%E0%B8%B1%E0%B8%9A-ai-%E0%B8%AA%E0%B8%A3%E0%B9%89%E0%B8%B2%E0%B8%87%E0%B8%A0%E0%B8%B2%E0%B8%9E%E0%B8%88%E0%B8%B2%E0%B8%81%E0%B8%82%E0%B9%89%E0%B8%AD%E0%B8%84%E0%B8%A7%E0%B8%B2%E0%B8%A1%E0%B8%AA%E0%B8%A3%E0%B9%89%E0%B8%B2%E0%B8%87%E0%B9%82%E0%B8%94%E0%B8%A2%E0%B9%80%E0%B8%94%E0%B9%87%E0%B8%81%E0%B8%A1%E0%B8%B1%E0%B8%98%E0%B8%A2%E0%B8%A1%E0%B8%9B%E0%B8%A5%E0%B8%B2%E0%B8%A2-%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B9%80%E0%B8%81%E0%B8%B7%E0%B8%AD%E0%B8%9A%E0%B8%88%E0%B8%B0%E0%B8%82%E0%B8%B6%E0%B9%89%E0%B8%99%E0%B8%9B%E0%B8%B5-1-ed5878c7a72c"
---

![image](/images/2022/32/01.jpg)

- โมเดลสร้างรูปภาพจากคำอธิบายภาษาไทยเพื่อสร้างภาพประกอบนิยาย เรื่องสั้น หรือบทความต่าง ๆ; เลือกใช้ VQGAN และ CLIP โดย VQGAN จะทำหน้าที่เป็นเสมือนผู้วาดรูปและ CLIP จะทำหน้าที่เป็นคนที่คอยกำกับรูปที่ VQGAN วาดว่าตรงกับข้อความที่เราวาดไปแค่ไหน,
- CLIP เป็นโมเดลที่เป็นสะพานเชื่อมระหว่างรูปภาพกับข้อความโดยจะทำการ Embed ทั้งสองอย่างนี้ให้อยู่ใน latent space ขนาดเท่ากันจึงสามารถนำทั้ง Text embedding และ Image embedding มาเปรียบเทียบความเหมือนความต่างได้โดยใช้วิธีการทางคณิตศาตร์ต่าง ๆ CLIP จะประกอบไปด้วยโมเดลหลัก 2 ส่วนคือ Text encoder และ Image encoder,
- VQGAN เป็นโมเดลประเภท Generative โดยจะประกอบไปด้วย Generator และ Discriminator โมเดลสองตัวนี้จะแข่งกันและพัฒนาตัวเองไปพร้อม ๆ กันจนในที่สุด Discriminator ไม่สามารถเอาชนะ Generator ได้ เราจึงจะนำ Generator ไปสร้างภาพต่อ นอกจากนี้ก่อนที่ทั้งสองโมเดลนี้จะแข่งกัน Generator จะได้เรียนรู้โครงสร้างของภาพที่ตัวเองจะสร้างไว้ก่อน เปรียบเสมือนมีสมุดเปล่าที่เอาไว้จดวิธีการสร้างสิ่งต่าง ๆ ลงไป,
- เนื่องจากการจะสร้างรูปจาก VQGAN นั้นต้องมี Random input (กลุ่มตัวเลขแบบสุ่ม) ส่งเข้าไปให้ Generator จึงจะสร้างเป็นรูปต่าง ๆ ได้และแน่นอนว่าเราไม่สามารถรู้ได้ว่าการสุ่มแบบไหนจะให้รูปที่เราต้องการได้ จึงต้องใช้ CLIP คอยกำกับและค่อย ๆ เปลี่ยน Random input เหล่านี้ให้เป็นรูปที่เราต้องการ,
- วิธี #1: เริ่มจากการเทรน CLIP ขึ้นมาเองใช้ข้อมูลเริ่มจาก flicker8k (8,000 รูป) ไปจนถึง flicker30k (30,000 รูป) แปลข้อมูล caption จากภาษาอังกฤษไปไทยด้วย PyThaiNLP; ใช้ resnet-50 เป็น image encoder และ WangchanBERTa เป็น text encoder (ThCLIP),
- วิธีแรกยังไม่ได้ผลเป็นที่น่าพึงพอใจด้วยปัจจัยขนาดชุดข้อมูลและเวลาในการเทรน จึงทดลองวิธี knowledge distillation สำหรับ CLIP แทน,
- วิธี #2: เทรนใหม่โดยการสอนให้ ThCLIP สร้าง text embeddings ให้คล้ายกับ OpenAI CLIP มากที่สุดตาม mean-squared error loss; ใช้ปริมาณข้อมูลน้อยกว่าและได้ผลดีกว่ามาก,
- เทรนตามวิธี #2 ด้วยข้อมูล 2 ล้านรูป สุ่มจาก GCC, MSCOCO เหมือนของ SwedishCLIP,
- จากการ "ทดลอง ทดลอง ทดลอง" พบว่า transform ภาพโดยสุ่มเพิ่มระดับ sharpness ให้กับภาพทำให้กราฟ Loss converge เร็วขึ้น, iteration ที่เหมาะที่สุดอยู่ระหว่าง 200–300 รอบ, รวมถึง:,
- ใช้ negative prompt เพื่อพัฒนาคุณภาพรูปภาพได้ เช่น เมื่อสร้างภาพ "เครื่องบิน" ให้ "ภาพเบลอ" เป็น negative prompt (ใส่เข้าไปใน loss function) จะทำให้ได้ภาพเครื่องบินที่ชัดขึ้น,
- ใช้ aesthetic-predictor จาก pretrained model ที่ประเมิน "ความสวย" ของรูป และให้ความสวยเป็นส่วนหนึ่งของ loss function; ทำให้รูปที่ออกมาสวยขึ้น,
- ทดสอบประสิทธิภาพโมเดลด้วยแบบสอบถามจาก 27 คน พบว่า VGQAN-ThCLIP (โมเดลของเรา) ทำได้ดีกว่า VQGAN-CLIP (pretrained จาก OpenAI) เมื่อรูปภาพถูกสร้างจากข้อความสั้นทั้งด้านความสอดคล้องและความหลากหลาย แต่ยิ่งข้อความยาวทำได้ดีกว่าในด้านความสอดคล้องแต่ด้อยกว่าในด้านความหลากหลาย,
- โมเดลสามารถทำ prompting ได้เหมือน text-to-image ชั้นนำทั่วไป เช่น "คฤหาสน์", "คฤหาสน์ แฟนตาซี", "คฤหาสน์ แฮรี่พอตเตอร์" ฯลฯ

### แรงจูงในในการเข้าร่วมโครงการ (จากใบสมัครเข้าร่วมเมื่อ 10 สัปดาห์ที่แล้ว)

> "เราให้นิยามตัวเองว่าเป็นคนที่มีความพยายามต่องานที่ทำอยู่เสมอ จึงมั่นใจได้ว่าเราจะทำโปรเจคนี้อย่างเต็มความสามารถ เรามีความรู้ในการเขียนโปรแกรมภาษา python มาจากการศึกษาด้วยตนเองเพื่อทำ project ในโรงเรียนและมีความกระตือรือร้นที่จะเรียนรู้อีก เรายังได้ทำการศึกษาการเขียนโปรแกรมมาหลากหลายผ่านการเข้าค่ายโอลิมปิกวิชาการคอมพิวเตอร์ค่าย 2 ที่ทำให้เราได้เข้าใจ algorithm ที่หลากหลาย เราได้ร่วมพัฒนาโครงการเครื่องให้อาหารแมวที่ควบคุมบน Web Application และทำงานร่วมกับระบบ IoT โดยตลอดเวลาที่ทำงานเหล่านั้นเราศึกษาบนเว็บต่างประเทศจึงสามารถอ่าน, แปล, และทำความเข้าใจบทความหรือ paper ภาษาอังกฤษได้ดีมาก เรามีแรงบันดาลใจในการสร้าง AI แก้ปัญหาในชีวิตประจำวัน แม้จะเป็นปัญหาเฉพาะกลุ่มแต่ก็สามารถสร้างความแปลกใหม่ได้ เราคาดหวังอย่างยิ่งว่าจะได้รับโอกาสในการทำความฝันนั้นให้เป็นจริง  ปฏิเสธไม่ได้ว่า Artificial Intelligence ได้เข้ามาบทบาทอย่างมากในปัจจุบัน ทั้งช่วยย่นการทำงานของมนุษย์ ช่วยจำแนกหรือวิเคราะห์ข้อมูลที่ซับซ้อน แนะนำ content ที่เกี่ยวข้อง หรือแม้แต่ช่วยตัดสินใจ แต่ก็ใช่ว่า AI จะสามารถทำได้ทุกอย่างหรือแม้แต่การทำงานออกมาได้ perfect 100% ก็เป็นไปได้ยากหากขาด dataset , การจัดการข้อมูลที่ดี หรือ วิธีการ train model ที่เหมาะสม ซึ่งสิ่งนี้จำเป็นต้องศึกษาเพิ่มเติมกว่าความรู้ในม.ปลายไปมาก และจำเป็นต้องพึ่งพาผู้ที่มีประสบการณ์มากกว่า  เราสนใจโครงการ AI Builder ตั้งแต่ปีที่แล้ว แม้จะไม่ผ่านรอบคัดเลือกตัวจริงแต่ก็ได้ศึกษาเนื้อหาไปบ้างในแบบของนักเรียน sit-in หลังจากเห็นโครงงานของเพื่อนหลายคนก็ทำให้เรามีไฟที่อยากจะมาลองสมัครรอบของปีนี้อีก! AI Builder มีเนื้อหาที่เข้มข้นและสิ่งที่สำคัญคือการมี mentor ที่เชี่ยวชาญ และกลุ่มเพื่อนเข้ามาช่วยให้คำปรึกษา เราจึงคิดว่าหากได้เข้าร่วมโครงการนี้แล้ว คงจะได้พัฒนาฝีมือตัวเองให้ดีขึ้นและเข้าใจถึงการพัฒนาโปรเจค AI อย่างเต็มรูปแบบจนอาจสามารถตกตะกอนความรู้และถ่ายทอดให้ผู้อื่นได้ในภายหลัง"