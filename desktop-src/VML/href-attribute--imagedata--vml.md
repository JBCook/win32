---
title: HRef Attribute (ImageData)(VML)
description: HRef Attribute (ImageData)(VML)
ms.assetid: 'c55ede90-3d57-4f27-9940-1fe4751cef71'
---

# HRef Attribute (ImageData)(VML)

This topic describes VML, a feature that is deprecated as of Windows Internet Explorer 9. Webpages and applications that rely on VML should be [migrated to SVG](http://go.microsoft.com/fwlink/p/?LinkID=236964) or other widely supported standards.

> [!Note]  
> As of December 2011, this topic has been archived. As a result, it is no longer actively maintained. For more information, see [Archived Content](https://msdn.microsoft.com/library/hh772377). For information, recommendations, and guidance regarding the current version of Windows Internet Explorer, see [Internet Explorer Developer Center](http://go.microsoft.com/fwlink/p/?linkid=204313).

 

Defines a URL for an image. Read/write. **String**.

**Applies To**

[ImageData](msdn-online-vml-imagedata-element.md)

**Tag Syntax**

&lt;v: *element* o:href=" *expression* "&gt;

**Script Syntax**

*element* .href="*expression*"

*expression*=*element*.href

**Remarks**

When the shape is clicked, the browser will load the URL. The **HRef** attribute is similar to the standard HTML **HRef** attribute of anchors.

Using this attribute makes it easy to create buttonswith images on a Web page.

This attribute is used by Microsoft Office only if a picture has been linked and embedded.Microsoft Word has a user interface for inserting pictures this way.

*Microsoft Offfice Extensions Attribute*

**Example**

When the image is clicked, the browser will load the Microsoft Corporation home page.


```HTML
   <v:shape id="rect01"
   coordorigin="0 0" coordsize="200 200"
   strokecolor="red"
   style="top:1;left:1;width:300;height:200"
   path="m 1,1 l 1,200, 200,200, 200,1 x e">
   <v:imagedata o:href="http://www.microsoft.com" src="kids.jpg"/>
   </v:shape>
```



 

 



