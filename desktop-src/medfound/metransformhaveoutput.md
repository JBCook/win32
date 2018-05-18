﻿---
Description: 'Sent by an asynchronous Media Foundation transform (MFT) when new output data is available from the MFT.'
ms.assetid: 'a9403ad3-81bf-4cd7-ba7f-816b901bb02c'
title: METransformHaveOutput event
---

# METransformHaveOutput event

Sent by an asynchronous Media Foundation transform (MFT) when new output data is available from the MFT.

## Event values

Possible values retrieved from [**IMFMediaEvent::GetValue**](imfmediaevent-getvalue.md) include the following.



| VARTYPE              | Description               |
|----------------------|---------------------------|
| VT\_EMPTY<br/> | No event data.<br/> |



## Attributes

No attributes are defined for this event.

## Remarks

Asynchronous MFTs send this event through the [**IMFMediaEventGenerator**](imfmediaeventgenerator.md) interface. Synchronous MFTs never send this event.

When the client of the MFT receives this event, it should call [**IMFTransform::ProcessOutput**](imftransform-processoutput.md) to get the output.

## Requirements



|                                     |                                                                                                          |
|-------------------------------------|----------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows 7 \[desktop apps only\]<br/>                                                               |
| Minimum supported server<br/> | Windows Server 2008 R2 \[desktop apps only\]<br/>                                                  |
| Header<br/>                   | <dl> <dt>Mfobjects.h (include Mfidl.h)</dt> </dl> |



## See also

<dl> <dt>

[Media Foundation Events](media-foundation-events.md)
</dt> <dt>

[Asynchronous MFTs](asynchronous-mfts.md)
</dt> </dl>

 

 



