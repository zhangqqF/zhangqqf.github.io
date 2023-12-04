---
layout:     post
title:      "Door slam close"
subtitle:   ""
date:       2023-11-24
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
  - Dura
  - Slam
  - LSDYNA
---


## Model Analysis
### Contacts
**Single Surface**

Body
- windshield single surface
- fixglass single surface
- adhesive as slave contacts to sheetmetal
- spotweld (beam9) as slave contatcs to sheetmetal
- seamweld (beam6) as slave contacts to sheetmetal

- initial stress shell
- damping
- hourglass

patch to the door
1000359
1000360
1000357
1000358
1000361

Strong Recommand: Don't check the "On Set" when you create a nodal rigid body, since we don't want many unuse set case this. This is same as the MPC in ABAQUS.


Contacts
SingSurf

Adhesive of PID, name is important,   BEAM6  BEAM9


Code for translate the rigids on set to not on set, so we can use the compress tool to delete the node sets.