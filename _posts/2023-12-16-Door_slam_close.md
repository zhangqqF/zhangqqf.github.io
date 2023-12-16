---
layout:     post
title:      "Door Slam Close"
subtitle:   ""
date:       2023-12-16
author:     "zhangqq"
header-img: "img/post/bumper_crash.gif"
header-mask: 0.4
catalog: true
published: True
# header-style: text
mathjax: true
lang: en
# header-bg-css: "linear-gradient(to right, #24b94a, #38ef7d);"
tags:
  - LS-Dyna
  - SideDoor
---

## Modeling
The model for door slam close analysis is including.
- [BIP](###-bip-modeling)
- DIP
- DoorTrim

and the patch connectings of PATCH_BIP_DIP, PATCH_DIP_TRIM. And also control cards and databases as well.


### BIP modeling
Cutting a BIP and the cut lines away 500 mm from the door or remin half of the BIP (recommand, because half of the BIP model can use both for analysis of front door and rear door, but the run time is more longer.)

The elements of the BIP model genneraly involing [Sheetmetal](), [Adhesives](), [Beam9]() or [Hexa]() (Spotweld), [Beam6]() (Front of the vehicle) and [Glasses]() of Wingdshield and Roof.

After the mesh prepared, we can create contacts.
- TIED_SHELL_EDGE_TO_SURFACE_OFFSET  
    S: [Adhesive]() (part id containts all of the adhesive elements)  
    M: [Sheetmetal]() (part set containts all of the shell metal properties)
- TIED_SHELL_EDGE_TO_SURFACE  
    S: [Spotweld]() (part id containts all of the spotweld and beam6 elements)  
    M: [Sheetmetal]() (part set containts all of the shell metal properties)
- AUTOMATIC_SINGLE_SURFACE  
    [Windshield]() (part id)  
    [fixedglass]() (part id)  
    [Global]() (Create a box caontaints also including door and trim)

