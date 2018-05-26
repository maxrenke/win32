---
title: TTM\_GETBUBBLESIZE message
description: Returns the width and height of a tooltip control.
ms.assetid: 6afb971e-f05d-4b7a-b63d-3672bfcc32dc
keywords:
- TTM_GETBUBBLESIZE message Windows Controls
topic_type:
- apiref
api_name:
- TTM_GETBUBBLESIZE
api_location:
- Commctrl.h
api_type:
- HeaderDef
ms.date: 05/31/2018
ms.topic: article
ms.author: windowssdkdev
ms.prod: windows
ms.technology: desktop
---

# TTM\_GETBUBBLESIZE message

Returns the width and height of a tooltip control.

## Parameters

<dl> <dt>

*wParam* 
</dt> <dd>Must be zero.</dd> <dt>

*lParam* 
</dt> <dd>

Pointer to the tooltip [**TOOLINFO**](/windows/win32/Commctrl/ns-commctrl-tagtoolinfoa?branch=master) structure.

</dd> </dl>

## Return value

Returns the width of the tooltip in the low word and the height in the high word if successful. Otherwise, it returns **FALSE**.

## Remarks

If the TTF\_TRACK and TTF\_ABSOLUTE flags are set in the **uFlags** member of the tooltip [**TOOLINFO**](/windows/win32/Commctrl/ns-commctrl-tagtoolinfoa?branch=master) structure, this message can be used to help position the tooltip accurately.

## Requirements



|                                     |                                                                                       |
|-------------------------------------|---------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista \[desktop apps only\]<br/>                                        |
| Minimum supported server<br/> | Windows Server 2003 \[desktop apps only\]<br/>                                  |
| Header<br/>                   | <dl> <dt>Commctrl.h</dt> </dl> |



 

 




