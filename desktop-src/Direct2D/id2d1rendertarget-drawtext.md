---
title: ID2D1RenderTarget DrawText methods
description: Draws the specified text using the format information provided by an IDWriteTextFormat object.
ms.assetid: 7cda7854-f9df-48d3-bc62-6aaee769e6f9
keywords:
- DrawText methods Direct2D
topic_type:
- apiref
api_location:
- D2d1.dll
api_type:
- DllExport
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# ID2D1RenderTarget::DrawText methods

Draws the specified text using the format information provided by an [**IDWriteTextFormat**](https://msdn.microsoft.com/library/windows/desktop/dd316628) object.

### Overload list



| Method                                                                                                                                                                                                                                                                               | Description                                                                                                                                     |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------|
| [**DrawText(WCHAR\*,IDWriteTextFormat\*,D2D1\_RECT\_F&,ID2D1Brush\*,D2D1\_DRAW\_TEXT\_OPTIONS,DWRITE\_TEXT\_MEASURING\_METHOD)**](/windows/desktop/api/d2d1/)  | Draws the specified text using the format information provided by an [**IDWriteTextFormat**](https://msdn.microsoft.com/library/windows/desktop/dd316628) object.<br/>  |
| [**DrawText(WCHAR\*,IDWriteTextFormat\*,D2D1\_RECT\_F\*,ID2D1Brush\*,D2D1\_DRAW\_TEXT\_OPTIONS,DWRITE\_TEXT\_MEASURING\_METHOD)**](/windows/desktop/api/d2d1/) | Draws the specified text using the format information provided by an [**IDWriteTextFormat**](https://msdn.microsoft.com/library/windows/desktop/dd316628) object. <br/> |



## Remarks

To draw text with Direct2D, use the [**ID2D1RenderTarget::DrawText**](/windows/desktop/api/d2d1/) method for text that has a single format, or the [**ID2D1RenderTarget::DrawTextLayout**](/windows/desktop/api/d2d1/) method when you need multiple formats, advanced OpenType features, or hit testing. These methods use the DirectWrite API to provide high-quality text display.

This method doesn't return an error code if it fails. To determine whether a drawing operation (such as **DrawText**) failed, check the result returned by the [**ID2D1RenderTarget::EndDraw**](/windows/desktop/api/d2d1/) or [**ID2D1RenderTarget::Flush**](/windows/desktop/api/d2d1/) methods.

## Examples

For an example, see [How to Draw Text](how-to--draw-text.md).

## Requirements



|                    |                                                                                     |
|--------------------|-------------------------------------------------------------------------------------|
| Library<br/> | <dl> <dt>D2d1.lib</dt> </dl> |
| DLL<br/>     | <dl> <dt>D2d1.dll</dt> </dl> |



## See also

<dl> <dt>

[**ID2D1RenderTarget**](/windows/desktop/api/d2d1/)
</dt> <dt>

[**IDWriteTextFormat**](https://msdn.microsoft.com/library/windows/desktop/dd316628)
</dt> <dt>

[How to Draw Text](how-to--draw-text.md)
</dt> <dt>

[Text Formatting and Layout Overview](https://msdn.microsoft.com/library/windows/desktop/dd742752)
</dt> </dl>

 

 




