---
layout:     post
title:      "Bumper crash"
subtitle:   "《基于LS-DYNA和HyperWorks的汽车仿真与分析》案例"
date:       2023-11-17
author:     "zhangqq"
# header-img: "img/post/post-bg-miui6.jpg"
# header-mask: 0.4
catalog: true
published: true
# header-style: text
mathjax: true
lang: en
# header-bg-css: "linear-gradient(to right, #24b94a, #38ef7d);"
tags:
  - Safety
---


政府安全法规：
美国FMVSS

NCAP - New Car Assessment Program



1. Connet the outer and inner plates of the [crash boxes]() with [spotwelds](), and place the spotweld in the new created component called *mass*.

2. Move the elements of the row of the crash boxes closest to the rigid plate representing the full vehicle into the component of the rigid plate.

3. Add the mass points to the rigid plate representing the car, the mass about 1.6 tone.  
    Analysis>safety>0-D elems for HM2021  
    $5331*3E-6=1.5993 t$
    HM cannot calculate the mass

4. **Contacts**
     - Format: type = master + slave
     - SurtfaceToSurface = Set *bumper* + Comp *wall*, *bumper* is a type of part set among all the shell components except the wall.
     - SingleSurface = bumper 

