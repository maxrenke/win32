---
Description: Occurs when the mouse pointer is moved over the InkCollector or InkOverlay object.
ms.assetid: b25aeead-9fb1-4221-82fa-ce2d81f5fed8
title: InkOverlay.MouseMove event
ms.date: 05/31/2018
ms.topic: article
ms.author: windowssdkdev
ms.prod: windows
ms.technology: desktop
---

# InkOverlay.MouseMove event

Occurs when the mouse pointer is moved over the [**InkCollector**](/windows/win32/msinkaut/?branch=master) or [**InkOverlay**](/windows/win32/msinkaut/?branch=master) object.

## Syntax


```C++
void MouseMove(
  [in]      InkMouseButton           Button,
  [in]      InkShiftKeyModifierFlags Shift,
  [in]      long                     pX,
  [in]      long                     pY,
  [in, out] VARIANT_BOOL             *Cancel
);
```



## Parameters

<dl> <dt>

*Button* \[in\]
</dt> <dd>

The mouse button that was pressed.

</dd> <dt>

*Shift* \[in\]
</dt> <dd>

The state of the SHIFT key.

</dd> <dt>

*pX* \[in\]
</dt> <dd>

The x-coordinate, in pixels, of a mouse click.

</dd> <dt>

*pY* \[in\]
</dt> <dd>

The y-coordinate, in pixels, of a mouse click.

</dd> <dt>

*Cancel* \[in, out\]
</dt> <dd>

Whether the event should be canceled for the parent control. The default value is **FALSE**, which specifies that the event should not be canceled.

</dd> </dl>

## Return value

This event does not return a value.

## Remarks

> [!Note]  
> The properties *pX* and *pY* are in pixels, and not the HIMETRIC units that are associated with the ink space. This is because this event replaces the related mouse event of a pen-unaware application and this type of application understands only pixels.

 

> [!Note]  
> Some controls rely on a specific relationship between [**MouseDown**](inkcollector-mousedown.md), [**MouseMove**](inkcollector-mousemove.md), and [**MouseUp**](inkcollector-mouseup.md) events. Canceling some of these events may have unanticipated results.

 

This event method is defined in the \_IInkCollectorEvents, \_IInkOverlayEvents, and \_IInkPictureEvents dispatch-only interfaces (dispinterfaces) with an ID of DISPID\_IPEMouseMove.

## Requirements



|                                     |                                                                                                                     |
|-------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows XP Tablet PC Edition \[desktop apps only\]<br/>                                                       |
| Minimum supported server<br/> | None supported<br/>                                                                                           |
| Header<br/>                   | <dl> <dt>Msinkaut.h (also requires Msinkaut\_i.c)</dt> </dl> |
| Library<br/>                  | <dl> <dt>InkObj.dll</dt> </dl>                               |



## See also

<dl> <dt>

[**InkOverlay Class**](/windows/win32/msinkaut/?branch=master)
</dt> <dt>

[**InkMouseButton Enumeration**](/windows/win32/msinkaut/ne-msinkaut-inkmousebutton?branch=master)
</dt> <dt>

[**InkShiftKeyModifierFlags Enumeration**](/windows/win32/msinkaut/ne-msinkaut-inkshiftkeymodifierflags?branch=master)
</dt> </dl>

 

 



