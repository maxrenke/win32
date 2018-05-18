﻿---
Description: 'The Restart method restarts the failed outbound fax job. For example, if the fax job has exceeded the number of retries, Restart will restart the fax job.'
ms.assetid: 'e94cd556-16b1-46d7-b373-d5e6ae75b39e'
title: 'FaxOutgoingJob.Restart method'
---

# FaxOutgoingJob.Restart method

The **Restart** method restarts the failed outbound fax job. For example, if the fax job has exceeded the number of retries, **Restart** will restart the fax job.

## Syntax


```VB
FaxOutgoingJob.Restart() As Long
```



## Parameters

This method has no parameters.

## Remarks

To use this method, a user must have the [**farSUBMIT\_LOW**](-mfax-fax-access-rights-enum.md) or **farMANAGE\_JOBS** access right. With the **farSUBMIT\_LOW** access right, users will be able to use this method only for their own faxes. With the **farMANAGE\_JOBS** access right, users will be able to use this method for all faxes on the server.

## Requirements



|                                     |                                                                                         |
|-------------------------------------|-----------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows XP \[desktop apps only\]<br/>                                             |
| Minimum supported server<br/> | Windows Server 2003 \[desktop apps only\]<br/>                                    |
| Header<br/>                   | <dl> <dt>FaxComex.h</dt> </dl>   |
| DLL<br/>                      | <dl> <dt>Fxscomex.dll</dt> </dl> |



## See also

<dl> <dt>

[Visual Basic Example](-mfax-managing-outgoing-jobs.md)
</dt> <dt>

[**FaxOutgoingJob**](-mfax-faxoutgoingjob.md)
</dt> <dt>

[**IFaxOutgoingJob**](-mfax-faxoutgoingjob-cpp.md)
</dt> </dl>

 

 



