---
title: ACPI_METHOD_NEXT_ARGUMENT macro
author: windows-driver-content
description: The ACPI_METHOD_NEXT_ARGUMENT structure returns a pointer to the next ACPI_METHOD_ARGUMENT structure in an array of ACPI_METHOD_ARGUMENT structures.
ms.assetid: c723b11b-1657-4a78-a6a1-26bd916604a4
keywords: 
- ACPI_METHOD_NEXT_ARGUMENT macro ACPI Devices
ms.author: windowsdriverdev
ms.date: 07/18/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
ms.localizationpriority: medium
---

# ACPI\_METHOD\_NEXT\_ARGUMENT macro


The ACPI\_METHOD\_NEXT\_ARGUMENT structure returns a pointer to the next [**ACPI\_METHOD\_ARGUMENT**](https://msdn.microsoft.com/library/windows/hardware/ff536125) structure in an array of ACPI\_METHOD\_ARGUMENT structures.

Syntax
------

```ManagedCPlusPlus
 ACPI_METHOD_NEXT_ARGUMENT(
    Argument
);
```

Parameters
----------

*Argument*   
A pointer to an ACPI\_METHOD\_ARGUMENT structure in an array of ACPI\_METHOD\_ARGUMENT structures.

Return value
------------

A pointer to the next ACPI\_METHOD\_ARGUMENT structure in an array of ACPI\_METHOD\_ARGUMENT structures.

Remarks
-------

Given a pointer to an ACPI\_METHOD\_ARGUMENT structure in an array of such structures, a driver can use this macro to calculate a pointer to the next structure in the array, if one exists.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Target platform</p></td>
<td>Desktop</td>
</tr>
<tr class="even">
<td><p>Version</p></td>
<td><p>Windows 2000 and later versions of Windows.</p></td>
</tr>
<tr class="odd">
<td><p>Header</p></td>
<td>Acpiioct.h (include Acpiioct.h)</td>
</tr>
</tbody>
</table>

## See also


[**ACPI\_METHOD\_ARGUMENT**](https://msdn.microsoft.com/library/windows/hardware/ff536125)

 

 




