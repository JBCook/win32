﻿---
Description: 'The IPrintTicketProvider::GetPrintCapabilities method queries the provider for a complete print capabilities document that describes the printer''s features and parameters.'
ms.assetid: '12dfd953-2336-47ce-8fdc-df8c6138b31d'
title: 'IPrintTicketProvider::GetPrintCapabilities method'
---

# IPrintTicketProvider::GetPrintCapabilities method

The `IPrintTicketProvider::GetPrintCapabilities` method queries the provider for a complete print capabilities document that describes the printer's features and parameters.

## Syntax


```C++
HRESULT GetPrintCapabilities(
  [in]  IXMLDOMDocument2 *pPrintTicket,
  [out] IXMLDOMDocument2 **ppCapabilities
);
```



## Parameters

<dl> <dt>

*pPrintTicket* \[in\]
</dt> <dd>

A pointer to the print ticket. The settings of the print ticket constrain the device capabilities.

</dd> <dt>

*ppCapabilities* \[out\]
</dt> <dd>

A pointer to a variable that receives the address of the device capabilities document.

</dd> </dl>

## Return value

`IPrintTicketProvider::GetPrintCapabilities` should return S\_OK if the operation succeeds. Otherwise, this method should return a standard COM error code.

## Remarks

The input print ticket should be used to determine and describe constraints on the settings in the output print capabilities document. No features, options, and parameters that are described in the output print capabilities document should change because of the contents of the input print ticket. Only the constraint status of the features, options, and parameters are subject to change.

## Requirements



|                            |                                                                                                            |
|----------------------------|------------------------------------------------------------------------------------------------------------|
| Target platform<br/> | <dl> <dt>Desktop</dt> </dl>                         |
| Header<br/>          | <dl> <dt>Prdrvcom.h (include Prdrvcom.h)</dt> </dl> |



 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bprint\print%5D:%20IPrintTicketProvider::GetPrintCapabilities%20method%20%20RELEASE:%20%285/12/2018%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/en-us/default.aspx. "Send comments about this topic to Microsoft")



