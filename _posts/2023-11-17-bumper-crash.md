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
  - lsdyna
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

The model [bumper.k]() provided has been assigned properties, and it's units system is **mm-N-MPa-t-s**, which is same as the commonly used in abaqus. But in LS-Dyna explicit analysis we usually use **millisecond** as the unit of time since the duration of crashes is very short. So be careful, we need to convert unit by ANSA (the unit of the strain rate is 1/s).

### Spotweld
Connect the outer and inner plates of the **crash boxes** with **spotwelds**, and place the spotweld in the new created component called **mass**.

### Connect the bumper to the car
The car is simplified as a rigid plate which behind the bumper.
Move the elements of the row of the crash boxes closest to the rigid plate into the component of the rigid plate.

### Mass
Add the mass elements to the rigid plate representing the car, all of the mass about 1.6 tonnes.  
>5331 * 3E-4 = 1.5993t, 5331 is the number of the nodes of the rigid plate.

### Contacts
>type = master + slave

- SurfaceToSurface = **bumper** + **wall**  
    bumper -- *a set the type is part which include all of the shell components except the wall.*
- SingleSurface = **bumper**

```
*CONTACT_SURFACE_TO_SURFACE_ID
         1
         6         1         3         2
$     SSID      MSID     SSTYP     MSTYP
$  0 -- Segment Set
$  1 -- Shell Set
$  2 -- Part Set
$  3 -- Part
$  4 -- Node Set
$  5 -- All
$  6 -- Exempted
*CONTACT_SINGLE_SURFACE_ID
         2
         1                   2
```

### Constraints and initial velocity
Fixed the **wall**, apply the Vx (velocity in X-Coordination) of **4 mm/ms** to the **velocity** (a set the type is node which include all of the shell components except the wall).

```
*INITIAL_VELOITY
        2
       4.
```

### Controls
```
*CONTROL_TERMINATION
        50
*CONTROL_TIMESTEP
                                   0.001
```

### Database
```
*DATABASE_GLSTAT
      0.01         1
*DATABASE_MATSUM
      0.01         1
*DATABASE_NODFOR
      0.01         1
*DATABASE_NODOUT
      0.01         1
*DATABASE_BINARY_D3PLOT
       2.5
```

