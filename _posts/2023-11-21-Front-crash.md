---
layout:     post
title:      "Front crash"
subtitle:   ""
date:       2023-11-21
author:     "zhangqq"
header-img: "img/post/bumper_crash.gif"
header-mask: 0.4
catalog: true
published: false
# header-style: text
mathjax: true
lang: en
# header-bg-css: "linear-gradient(to right, #24b94a, #38ef7d);"
tags:
  - Safety
---

## ff
- Regular revanted
- Full vehicle model without any other things
- Add
    - Rigid walls
    - ACC sensors
    - Initial velocity
    - Gravity
    - Controls and Database

## Post processing
- **Energy**
标准能量曲线
- total ener
- kinetic energy
- inner energy
- hourglass energy
- sliding interface energy

add mass和hourglass energy < 5%

- **ACC of B-pillar**
filter>inverse>/9800

- **前围板侵入量**

tracking systems

- **deforming of door frame**

- **转向管柱跳动量**

- **Reforce of the wall**


Applications>Tool>HvTrans
File>Open Result File>d3plot

Add the path of the **hvtrans.exe** located folder to the PATH, you can search *hvtrans* on the root directory of the hwdestop if you don't known where the excute file placed. Execute the command to translate the d3plot of the current directory.
```
hvtrans d3plot -o out.h3d -ar
```

.../hwdestopio/result_readers/bin/win64/



Body
- windshield single surface
- fixglass single surface
- adhesive as slave contacts to sheetmetal
- spotweld as slave contatcs to sheetmetal

- initial stress shell
- damping
- hourglass

patch to the door
1000359
1000360
1000357
1000358
1000361