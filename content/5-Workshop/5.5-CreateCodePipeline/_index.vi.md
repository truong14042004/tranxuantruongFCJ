---
title: "Tạo Code PipeLine"
date: 2025-09-09
weight: 5
chapter: false
pre: " <b> 5.5 </b> "
---

1. Trong ngăn điều hướng, chọn **Pipelines**, sau đó nhấp **Create repository**:
   ![image1](/5-workshop/5.5-createcodepipeline/image1.png)
2. Trong giao diện Create new pipeline chọn **Build custom pipeline**:
   ![image2](/5-workshop/5.5-createcodepipeline/image2.png)
3. Nhập tên pipeline
   ![image3](/5-workshop/5.5-createcodepipeline/image3.png)
4. Chọn source **GitHub**, tạo connection và chọn repository
   ![image4](/5-workshop/5.5-createcodepipeline/image4.png)
5. Chọn **Other build providers**

- Chọn **AWS CodeBuild**
- Chọn project đã tạo

![image5](/5-workshop/5.5-createcodepipeline/image5.png)

6. Chọn skip test stage
7. Chọn skip deploy stage
8. Tạo pipeline
