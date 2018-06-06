---
title: LVM\_MAPIDTOINDEX message
description: Maps the ID of an item to an index.
ms.assetid: 1082b7c6-c399-473d-aa4a-2b75e9bd2ab0
keywords:
- LVM_MAPIDTOINDEX message Windows Controls
topic_type:
- apiref
api_name:
- LVM_MAPIDTOINDEX
api_location:
- Commctrl.h
api_type:
- HeaderDef
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# LVM\_MAPIDTOINDEX message

Maps the ID of an item to an index.

## Parameters

<dl> <dt>

*wParam* 
</dt> <dd>

The unique ID of an item.

</dd> <dt>

*lParam* 
</dt> <dd>

Must be zero.

</dd> </dl>

## Return value

Returns the most current index.

## Remarks

List-view controls internally track items by index. This can present problems because indexes can change during the control's lifetime.

The list-view control can tag an item with an ID when the item is created. You can use this ID to guarantee uniqueness during the lifetime of the list-view control.

To uniquely identify an item, take the index that is returned from a call such as [**IComponent::GetDisplayInfo**](https://msdn.microsoft.com/library/aa814775) and call [**LVM\_MAPINDEXTOID**](lvm-mapindextoid.md). The return value is a unique ID.

If you need the index of an item after an ID is created you can call **LVM\_MAPIDTOINDEX** with the unique ID and it returns the most current index.

**LVM\_MAPIDTOINDEX** is not supported under the [**LVS\_OWNERDATA**](list-view-window-styles.md) style.

> [!Note]  
> In a multithreaded environment, the index is only guaranteed on the thread that hosts the list-view control, not on background threads.

 

> [!Note]  
> To use this message, you must provide a manifest specifying Comclt32.dll version 6.0. For more information on manifests, see [Enabling Visual Styles](cookbook-overview.md).

 

## Requirements



|                                     |                                                                                       |
|-------------------------------------|---------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista \[desktop apps only\]<br/>                                        |
| Minimum supported server<br/> | Windows Server 2003 \[desktop apps only\]<br/>                                  |
| Header<br/>                   | <dl> <dt>Commctrl.h</dt> </dl> |



 

 




