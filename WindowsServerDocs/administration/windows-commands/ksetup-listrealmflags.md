---
title: ksetup:listrealmflags
description: "Windows Commands topic for **** - "
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aa96e4da-6b98-4c05-bccf-73cbf33258c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
---
# ksetup:listrealmflags

>Applies To: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

lists the available realm flags that can be reported by **ksetup**. For examples of how this command can be used, see [Examples](#BKMK_Examples).
## Syntax
```
ksetup /listrealmflags
```
### Parameters
None
## remarks
The realm flags specify additional features of a non-Windows-based Kerberos realm. Computers that are running Windows Server 2003,  Windows Server 2008 , or  Windows Server 2008 R2  can use a non-Windows-based Kerberos server to administer authentication instead of using a domain that is running a Windows Server operating system. These systems participate in a Kerberos realm instead of a Windows domain. This entry establishes the features of the realm. The following table describes each.
|Value|Realm flag|Description|
|-----|-------|--------|
|0xF|All|All realm flags are set.|
|0x00|None|No realm flags are set, and no additional features are enabled.|
|0x01|Sendaddress|The IP address will be included within the ticket-granting tickets.|
|0x02|TcpSupported|The Transmission Control Protocol (TCP) and the User Datagram Protocol (UDP) are supported in this realm.|
|0x04|delegate|Everyone in this realm is trusted for delegation.|
|0x08|NcSupported|This realm supports name canonicalization, which allows for DNS and realm naming standards.|
|0x80|RC4|This realm supports RC4 encryption to enable cross-realm trust, which allows for the use of TLS.|
Realm flags are stored in the registry in **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\Kerberos\Domains\\***Realm-name*. This entry does not exist in the registry by default. You can use the [ksetup:addrealmflags](ksetup-addrealmflags.md) command to populate the registry.
## <a name="BKMK_Examples"></a>Examples
list the known realm flags on this computer:
```
ksetup /listrealmflags
```
Set the available realm flags that **ksetup** does not know by typing either of the following commands at the command line:
```
ksetup /setrealmflags CORP.CONTOSO.COM sendaddress tcpsupported delete ncsupported
```
```
ksetup /setrealmflags CORP.CONTOSO.COM 0xF
```
## additional references
-   [ksetup:setrealmflags](ksetup-setrealmflags.md)
-   [ksetup:addrealmflags](ksetup-addrealmflags.md)
-   [ksetup:delrealmflags](ksetup-delrealmflags.md)
-   [ksetup](ksetup.md)
-   [Command-Line Syntax Key](command-line-syntax-key.md)
