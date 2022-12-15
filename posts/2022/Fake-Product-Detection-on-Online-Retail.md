---
date: "3-7-22"
title: "Fake Product Detection on Online Retail"
builder: "เจษฎา ปราณี (แจ็ค)"
builder_info: ""
thumbnail: "/images/2022/23/01.jpg"
links:
    github: "https://github.com/JackJessada/fake_product_detect"
    facebook: "https://facebook.com/aibuildersx/posts/406851801483265"
    blog: "https://medium.com/@jessadajackpranee/%E0%B8%82%E0%B8%AD%E0%B8%87%E0%B8%9B%E0%B8%A5%E0%B8%AD%E0%B8%A1%E0%B8%81%E0%B8%B1%E0%B8%9A-e-commerce-c2d1bb142e2e"
---

![image](/images/2022/23/01.jpg)

- โมเดลประเมินว่าสินค้าที่ขายออนไลน์ในเว็บไซต์เป็นของแท้, ของปลอม หรือของไม่มีแบรนด์โดยใช้ข้อมูลจากหน้า product detail page,
- แรงบันดาลใจจากการสำรวจของ intelligencenode ที่ว่าช่วงโรคระบาด COVID-19 มีผู้ใช้พบของปลอมระหว่างเลือกซื้อสินค้าออนไลน์ถึง 38% จากผู้ตอบแบบสอบถามทั้งหมด,
- เก็บข้อมูลโดยการใช้ selenium ดึงข้อมูลจากหมวดหมู่เครื่องใช้ไฟฟ้าของ Shopee.co.th จำนวนเกือบ 5,000 รายการ แล้วจำแนกเป็นของแท้ (79%), ของปลอม (9%) และของไม่มีแบรนด์ (12%) **ด้วยมือเองทั้งหมด**,
- ทำการ rebalance training set ด้วย SMOTE เป็นของแท้ 55%, ของปลอม 20% และของไม่มีแบรนด์ 25% เพื่อให้โมเดลเรียนรู้ได้ดีขึ้น,
- ไม่ลืมที่จะแบ่ง test set ออกมาก่อน เพื่อไม่ให้มีการทดสอบหา metric ด้วยข้อมูลสังเคราะห์ จะทำให้โมเดลดูดีเกินจริง,
- ใช้ feature จากหน้า product detail page โดยอ้างอิงสิ่งที่มนุษย์ใช้จำแนกของแท้-ของปลอม เช่น ราคา (ไม่ถูกหรือแพงเกินไป), จำนวนสินค้าที่ถูกขาย (ยอดขายไม่เวอร์จนเกินไป), จำนวนรีวิวสินค้า (รีวิวไม่เยอะหรือน้อยจนผิดสังเกต), จำสินค้าที่ร้านค้าขายทั้งหมด (ยิ่งขายเยอะยิ่งน่าเชื่อถือ), อัตราการตอบกลับของร้านค้า (ยิ่งตอบเร็วยิ่งใส่ใจลูกค้า), จำนวนผู้ติดตามร้านค้า (ไม่ได้มีผู้ติดตามปลอมเยอะจนผิดสัดส่วน), ระยะเวลาที่เปิดร้านค้ามา (ยิ่งยาวนานยิ่งน่าเชื่อถือ), เรตติ้งของสินค้า (ไม่ถูกปลอมขึ้นมา) ฯลฯ,
- เลือกโมเดลที่ดีที่สุดด้วย cross-validation จาก KNN, Random Forest, และ XGBoost; เลือกใช้ Random Forest เนื่องจากผลงานดีพอๆกับ XGBoost แต่ใช้งานได้เร็วกว่า,
- ลองนำคอมเม้นท์ในหน้า product detail page มาเป็น feature เพิ่มแล้ว แต่ผลไม่ดีขึ้น สันนิษฐานว่าเกิดจากโมเดลไม่สามารถแบ่งคุณภาพคอมเม้นท์ได้ เช่น คอมเม้นท์ปลอม มีคอมเม้นท์ประเภทร้านค้าขอให้พิมพ์ และคอมเม้นท์ที่ไม่เกี่ยวกับเนื้อหาเลย เป็นต้น,
- ได้ผลดีถึง F1 score ที่ 0.9x ใน test set ทั้ง micro/macro average และในแต่ละประเภทสินค้าที่ทำนาย,
- แต่เมื่อไปทดสอบกับประเภทสินค้าที่ไม่คุ้นเคย, product detail page จากเว็บไซต์อื่นที่ไม่ใช่ Shopee.co.th, หรือสินค้าที่ไม่ครอบคลุมจาก training set ยังพบเห็นความผิดพลาด; ต้องการข้อมูลเพิ่มเพื่อทำให้สมบูรณ์แบบ,
- ทำการวิเคราะห์ข้อผิดพลาดอย่างเข้มข้นด้วย SHAP; หนึ่งในข้อสรุปที่น่าสนใจคือต้นไม้บางต้นตัดสินว่า "ยิ่งยอดขายมาก ยิ่งมีโอกาสเป็นของปลอม" ทั้งนี้เนื่องจากพฤติกรรมการปั๊มยอดขายของสินค้าปลอมนั่นเอง

### แรงจูงในในการเข้าร่วมโครงการ (จากใบสมัครเข้าร่วมเมื่อ 10 สัปดาห์ที่แล้ว)

> "ผมชอบและถนัดทางคณิตศาสตร์ครับ การแก้ปัญหาต่าง ๆ และชอบลองอะไรใหม่ ๆ ผมมีประสบการณ์ภาษา python มาบ้างรวมทั้งการใช้ libraries อื่น ๆ เช่น numpy pandas matplotlib  ผมอยากใช้เวลาว่างในช่วงปิดเทอมนี้เรียนรู้ในสิ่งที่ผมสนใจ ส่วนตัวผมรู้ตัวช้าไปว่าสนใจในด้านนี้ จึงอยากจะหาความรู้ให้ทันคนอื่น และนำความรู้ที่ได้ตรงนี้ไปต่อยอดในโครงงานต่อ ๆ ไป อีกอย่างผมเองก็สนใจทางด้าน AI มาสักพักหนึ่งแล้วเลยอยากใช้โอกาสที่ทาง AI Builders จัดโครงการดี ๆ แบบนี้ศึกษาเรื่องนี้ไปพร้อมกับโครงการเลย  โมเดลเช็คว่าสินค้ามีโอกาสเป็นของปลอมหรือไม่ ช่วยในการแก้ปัญหาสินค้าปลอมที่เห็นตามแพลตฟอร์มออนไลน์ต่าง ๆ โดยหาชุดข้อมูลจากการทำ web scraping ในหมวด เรตติ้ง ความคิดเห็น คะแนนร้านค้า รูปภาพ ราคา และนำมาเปรียบเทียบข้อมูลกับสินค้าประเภทเดียวกันอื่น ๆ"