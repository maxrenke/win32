---
Description: MinMergeIdleTime
ms.assetid: 59f2674e-efb8-4119-b1da-a0622ff7b843
title: MinMergeIdleTime
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# MinMergeIdleTime

> [!Note]  
> Indexing Service is no longer supported as of Windows XP and is unavailable for use as of Windows 8. Instead, use [Windows Search](https://msdn.microsoft.com/windows/desktop/6da601c6-3742-40ad-99f2-8817f7f642b3) for client side search and [Microsoft Search Server Express]( http://go.microsoft.com/fwlink/p/?linkid=258445) for server side search.

 

The **MinMergeIdleTime** entry is the minimum percentage of CPU processing time that must be idle during a merge-check period before Indexing Service can initiate an annealing merge.

### Summary



|          |                |
|----------|----------------|
| Type:    | **REG\_DWORD** |
| Units:   | Percent        |
| Default: | 90             |
| Range:   | 10 - 100       |



 

### Remarks

Indexing Service uses the value of the **MinMergeIdleTime** entry to delay merges until there are no other heavy demands on the processor.

## Related topics

<dl> <dt>

[Catalog, Property, and Scope Registry Entries](catalog--property--and-scope-registry-entries.md)
</dt> <dt>

[Main Registry Entries](main-registry-entries.md)
</dt> </dl>

 

 


