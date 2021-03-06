---
title: AVC\_FUNCTION\_GET\_PIN\_DESCRIPTOR
description: AVC\_FUNCTION\_GET\_PIN\_DESCRIPTOR
ms.assetid: 1a02c328-e908-4125-abe7-4db9970ac86a
keywords: ["AVC_FUNCTION_GET_PIN_DESCRIPTOR Streaming Media Devices"]
topic_type:
- apiref
api_name:
- AVC_FUNCTION_GET_PIN_DESCRIPTOR
api_type:
- NA
ms.author: windowsdriverdev
ms.date: 11/28/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
ms.localizationpriority: medium
---

# AVC\_FUNCTION\_GET\_PIN\_DESCRIPTOR


## <span id="ddk_avc_function_get_pin_descriptor_ks"></span><span id="DDK_AVC_FUNCTION_GET_PIN_DESCRIPTOR_KS"></span>


The **AVC\_FUNCTION\_GET\_PIN\_DESCRIPTOR** function code obtains the pin descriptor for each pin ID (offset from zero).

### <span id="i_o_status_block"></span><span id="I_O_STATUS_BLOCK"></span>I/O Status Block

If successful, the AV/C protocol driver sets **Irp-&gt;IoStatus.Status** to STATUS\_SUCCESS.

Possible other return values include:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Return Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>STATUS_TIMEOUT</p></td>
<td><p>The request was made, but no response was received before all time-out and retry processing was complete.</p></td>
</tr>
<tr class="even">
<td><p>STATUS_REQUEST_ABORTED</p></td>
<td><p>Immediately abort when the IRP completion status is STATUS_REQUEST_ABORTED. This indicates that the device has been removed or is no longer available on the 1394 bus.</p></td>
</tr>
<tr class="odd">
<td><p>STATUS_*</p></td>
<td><p>Any other return code indicates that an error or warning occurred that was beyond the scope of the AV/C protocol.</p></td>
</tr>
</tbody>
</table>

 

### <span id="comments"></span><span id="COMMENTS"></span>Comments

This function uses the **PinDescriptor** member of the AVC\_MULTIFUNC\_IRB structure as shown below.

```
typedef struct _AVC_MULTIFUNC_IRB {
  AVC_IRB  Common;
  union {
    .
    .
    .
    AVC_PIN_DESCRIPTOR PinDescriptor;
 .
    .
    .
  };
} AVC_MULTIFUNC_IRB, *PAVC_MULTIFUNC_IRB;
```

### <span id="requirements"></span><span id="REQUIREMENTS"></span>Requirements

**Headers:** Declared in *avc.h*. Include *avc.h*.

### <span id="avc_multifunc_irb_input"></span><span id="AVC_MULTIFUNC_IRB_INPUT"></span>AVC\_MULTIFUNC\_IRB Input

<span id="Common"></span><span id="common"></span><span id="COMMON"></span>**Common**  
The **Function** submember of this member must be set to **AVC\_FUNCTION\_GET\_PIN\_DESCRIPTOR** from the AVC\_FUNCTION enumeration.

<span id="PinDescriptor"></span><span id="pindescriptor"></span><span id="PINDESCRIPTOR"></span>**PinDescriptor**  
Specifies the description of a pin on an AV/C subunit device.

This function code is not supported by virtual instances of *avc.sys*.

In addition to the pin descriptor, this function may also return the address of an intersect handler and an opaque context value associated with the intersect handler. If the intersect handler member is **NULL**, the subunit driver must provide an intersect handler. If the intersect handler member is not **NULL**, an intersect handler is provided and the driver may use it.

*Avc.sys* never provides a data intersection, but a filter driver (for example, *avcstrm.sys*) fills it in as the request is being completed back up through the stack.

This must be called at IRQL = PASSIVE\_LEVEL.

### <span id="see_also"></span><span id="SEE_ALSO"></span>See Also

[**AVC\_MULTIFUNC\_IRB**](https://msdn.microsoft.com/library/windows/hardware/ff554177), [**AVC\_PIN\_DESCRIPTOR**](https://msdn.microsoft.com/library/windows/hardware/ff554185), [**AVC\_FUNCTION**](https://msdn.microsoft.com/library/windows/hardware/ff554145), [**KSPIN\_DESCRIPTOR**](https://msdn.microsoft.com/library/windows/hardware/ff563533), [**AV/C Intersect Handler**](https://msdn.microsoft.com/library/windows/hardware/ff556379)

 

 





