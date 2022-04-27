---
date: "2021-07-10"
title: "Thai Music (Ranat Ek) Generation with Variational Autoencoder"
builder: "Noppawat Tantisiriwat (Rew)"
builder_info: "มัธยมศึกษาปีที่ 6 / กรุงเทพมหานคร"
thumbnail: "/images/2021/007/01.jpg"
links:
  github: "https://github.com/Noppawat-Tantisiriwat/Thai-Music-Generation"
  facebook: "https://www.facebook.com/aibuildersx/posts/169658958535885"
  blog: "https://noppawat-tan.medium.com/thai-music-generation-ranat-ek-with-variational-autoencoder-753e69f0b323"
---

![Rew](/images/2021/007/03.jpg)

- ได้ทำโมเดลเพื่อ generate เสียงระนาดเอกโดยมีจุดประสงค์เพื่อให้ดนตรีไทยเป็นที่รู้จักกันอย่างกว้างขวางมากขึ้น
- ทำการเก็บชุดข้อมูลเองโดยได้รับความร่วมมือจากครูประจำโรงเรียน
- ได้ใช้รูปแบบโมเดลที่ชื่อ ​Variational Auto Encoder (VAE) เพื่อเรียนรู้การสร้างเพลง
- ได้ทดลองรูปแบบสถาปัตยกรรมโมเดลทั้งหมดสามแบบ โดยแต่ละแบบจะเป็น CNN based model
- train โมเดลด้วยการให้โมเดลเรียนที่จะสร้าง spectrogram ขึ้นมาจาก latent space
- ทำการวัดผลโมเดลตัวเองด้วย Mean Opinion Score (MOS) ได้ผลลัพท์ดีที่สุดอยู่ที่ 3.56 (เต็ม 5)
- สามารถเล่น demo app ได้ทีทาง heroku app

![Generation example](/images/2021/007/01.jpg)

![Model Architecture](/images/2021/007/02.jpg)


### แรงจูงใจในการเข้าร่วมโครงการ (จากใบสมัครเข้าร่วมเมื่อ 9 สัปดาห์ที่แล้ว)

> “นับเป็นโอกาสที่ดีที่จะได้เข้าร่วมในโครงการ AI Builder เพื่อศึกษาต่อยอดความรู้ทางด้าน Machine Learning เนื่องจากว่า Artificial Intelligence กำลังมีบทบาทสำคัญในหลายสาขาวิชา และมีประโยชน์ในการพัฒนาเทคโนโลยีเพื่อแก้ไขปัญหาในทุกๆระดับ ตั้งแต่ระดับบุคคล ไปจนถึงระดับชาติ ดังนั้นผมจึงอยากเข้าเป็นส่วนหนึ่งของโครงการนี้เพื่อ
>1. เปิดวิสัยทัศน์จากการได้เรียนรู้จากอาจารย์และพี่ๆในโครงการที่มีความรู้ด้านการพัฒนาปัญญาประดิษฐ์โดยตรง รวมทั้งได้คำปรึกษาที่มีประโยชน์อย่างมากในการพัฒนาต่อยอดองค์ความรู้
>2. ได้มีส่วนร่วมในการทำโครงการที่เกี่ยวข้องกับปัญญาประดิษฐ์ ซึ่งเป็นการเรียนรู้แบบ learning by doing ซึ่งเป็นการเรียนรู้จากประสบการณ์จริง ได้ผลงานที่สามารถจำต้องได้
>3. ได้เป็นส่วนเล็กๆส่วนหนึ่งที่สำคัญของ AI community ในฐานะยุวทูตด้านดิจิทัล ได้มีส่วนร่วมในการแบ่งปันความรู้ และทำให้เกิด community ที่แข็งแรง
>สุดท้ายนี้ผมคาดหวังที่จะสามารถเป็นผู้นำในการพัฒนานวัตกรรมด้านปัญญาประดิษฐ์ที่เป็นประโยชน์ต่อสังคมและประเทศชาติต่อไปในอนาคต”