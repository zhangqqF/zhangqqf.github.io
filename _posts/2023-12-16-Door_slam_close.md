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
  - lsdyna
  - SideDoor
---

## Modeling
The model for door slam close analysis is including.
- BIP
- DIP
- DoorTrim

and the patch connectings of [PATCH_BIP_DIP](), [PATCH_DIP_TRIM](). And also control cards and databases as well.


### BIP Modeling
Cutting a BIP and the cut lines away 500 mm from the door or remin half of the BIP (recommand, because half of the BIP model can be used both analysis for front door and rear door, but the run time is more longer.)

The elements of the BIP model genneraly involing [Sheetmetal](), [Adhesives](), [Beam9]() or [Hexa]() (Spotweld), [Beam6]() (Front of the vehicle) and [Glasses]() of Wingdshield and Roof.

After the mesh prepared, we can create contacts as below.
- TIED_SHELL_EDGE_TO_SURFACE_OFFSET  
    S: [adhesive]() (a part id that containts all of the adhesive elements)  
    M: [sheetmetal]() (a part set that containts all of the shell metal properties)
- TIED_SHELL_EDGE_TO_SURFACE  
    S: [spotweld]() (a part id that containts all of the spotweld and beam6 elements)  
    M: [sheetmetal]() (the part set that containts all of the shell metal properties)
- AUTOMATIC_SINGLE_SURFACE  
    [windshield]() (part id)  
    [fixedglass]() (part id)  
    [global_single_contact]() (Create a box that caontaints BIP and also door and trim)

We need setting several sets and fixed its id.
- [SPC]()
- [sheet_contact_with_door]()

Finally, renumber with range of [10000001-19999999]() (because the number 10000000 is always error as duplicate part id, so we start from 10000001.)

### Door Modeling
The door model has the three statements.
- Glass in full open
- Glass in mid open
- Glass in close

Create contacts for spotweld and adhesive same as the BIP.
- TIED_SHELL_EDGE_TO_SURFACE_OFFSET  
    S: [adhesive]() (part id that containts all of the adhesive elements)  
    M: [sheetmetal]() (part set that containts all of the shell metal properties)
- TIED_SHELL_EDGE_TO_SURFACE  
    S: [spotweld]() (part id that containts all of the spotweld and beam6 elements)  
    M: [sheetmetal]() (part set that containts all of the shell metal properties)

And `important`, we use Beam6 to modeling the door glass seal, and we need create a contact for that.
- SPOTWELD (or TIED_SHELL_EDGE_TO_SURFACE)  
    S: [seal]() (part id that containts all of the seal beam6 elements.)  
    M: [window]() (part set that containts the sheets and glass which contacts with the seal.)

Lock contacts
......

Create a set and fixed its id.
- [sheet_contact_with_BIP]() (contact with BIP)

Renumber range of [31000000-31499999]() for front door, rear door is [32000000-32499999]().


### Door Trim
No pparticularly, there is no contact and other settings.

Renumber range of [31500000-31999999]() for front doot trim, rear door trim is [32500000-32999999]().

### Heading
The heading file generaly like below.
```
*KEYWORD
*INCLUDE





*END
```


