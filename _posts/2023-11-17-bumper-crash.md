---
layout:     post
title:      "Bumper crash"
subtitle:   "《基于LS-DYNA和HyperWorks的汽车仿真与分析》案例"
date:       2023-11-17
author:     "zhangqq"
header-img: "img/post/bumper_crash.gif"
header-mask: 0.4
catalog: true
published: true
# header-style: text
mathjax: true
lang: en
# header-bg-css: "linear-gradient(to right, #24b94a, #38ef7d);"
tags:
  - Safety
---

>Regulations of governments  
- FMVSS of America  
- EEC and ECE of Europe

>NCAP(New Car Assessment Program)  
- Euro-NCAP  
- US-NCAP  
- J-NCAP  
- C-NCAP

---

The model [bumper.k]() provided has been assigned properties, and it's units system is mm-N-MPa-t-s, which is same as the commonly used in abaqus. But in LS-Dyna explicit analysis we usually use [ms]() as the unit of time since the duration of crashes is very short. So be careful, we need to convert unit by ANSA.

### Spotweld
Connet the outer and inner plates of the [crash boxes]() with [spotwelds](), and place the spotweld in the new created component called *mass*.

### Connect the bumper to the car
The car is simplified as a rigid plate which behind the bumper.
Move the elements of the row of the crash boxes closest to the rigid plate into the component of the rigid plate.

### Mass
Add the mass elements to the rigid plate representing the car, all of the mass about 1.6 tone.  
>5331 * 3E-4 = 1.5993t, 5331 is the number of the nodes of the rigid plate.

### Contacts
>type = master + slave

- SurfaceToSurface = [bumper]() + [wall]()  
    bumper -- *a set the type is part which include all of the shell components except the wall.*
- SingleSurface = [bumper]()

### Constraints and initial velocity
Fixed the [wall](), apply the Vx (velocity in X-Coordination) of [4 mm/ms]() to the [velocity]()(a set the type is node which include all of the shell components except the wall).

### Controls


### Database
