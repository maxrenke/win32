---
Description: 'Explains how to create custom security packages by using the custom security package API.'
ms.assetid: 'af8b9796-77e7-43c1-8f8e-acee01a62bf9'
title: Custom Security Packages
---

# Custom Security Packages

To implement new security protocols that are integrated with the Windows�Server and Windows operating systems, use the custom security package API and the [*Local Security Authority*](https://msdn.microsoft.com/library/windows/desktop/ms721592#-security-local-security-authority-gly) (LSA) functions.

The custom security package API supports combined development of custom [*security support providers*](https://msdn.microsoft.com/library/windows/desktop/ms721625#-security-security-support-provider-gly) (SSPs), which provide [Noninteractive Authentication](noninteractive-authentication.md) services and secure message exchange to client/server applications, with the development of custom [*authentication packages*](https://msdn.microsoft.com/library/windows/desktop/ms721532#-security-authentication-package-gly), which provide services for applications that perform [Interactive Authentication](interactive-authentication.md). These services, when combined in a single package, are called a security support provider/authentication package (SSP/AP).

As with Microsoft-provided security packages, users of the custom security package access interactive authentication services using the [LSA Logon Functions](authentication-functions.md#lsa-logon-functions). Noninteractive authentication and message protection services can be accessed directly using [Security Support Provider Interface](sspi.md) (SSPI).

The security packages deployed in SSP/APs are fully integrated with the LSA. Using the LSA support functions available to custom security packages, developers can implement advanced security features such as token creation, [*supplemental credentials*](https://msdn.microsoft.com/library/windows/desktop/ms721625#-security-supplemental-credentials-gly) support, and pass-through authentication. For a list of these support functions, see [LSA Functions Called by Authentication Packages](authentication-functions.md#lsa-functions-called-by-authentication-packages). For information about how to implement custom security packages, see [Creating Custom Security Packages](creating-custom-security-packages.md).

For more information about custom security packages, see the following topics.



| Topic                                                                                                                                                 | Description                                                                                             |
|-------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| [SSP/APs vs. SSPs](ssp-aps-versus-ssps.md)<br/>                                                                                                | Information about how to determine whether a security package should be in an SSP/AP or SSP.<br/> |
| [LSA Mode vs. User Mode](lsa-mode-versus-user-mode.md)<br/>                                                                                    | Details about how LSA mode and user mode are different.<br/>                                      |
| [Restrictions around Registering and Installing a Security Package](restrictions-around-registering-and-installing-a-security-package.md)<br/> | Actions by security packages that are not supported in Windows.<br/>                              |



�

�

�



