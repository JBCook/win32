---
title: Load(int,int,int,uint) function
description: Reads texture data and returns status of the operation.
ms.assetid: 'F5EA2FFF-7E43-4A34-9358-EA54382641DC'
keywords: ["Load function HLSL"]
topic_type:
- apiref
api_name:
- Load
api_type:
- NA
---

# Load(int,int,int,uint) function

Reads texture data and returns status of the operation.

## Syntax


```C++
 Load(
  _In_  int  Location,
  _In_  int  sampleindex,
  _In_  int  Offset,
  _Out_ uint Status
);
```



## Parameters

<dl> <dt>

*Location* \[in\]
</dt> <dd>

Type: **int**

The texture coordinates.

</dd> <dt>

*sampleindex* \[in\]
</dt> <dd>

Type: **[**int**](https://msdn.microsoft.com/library/windows/desktop/aa383751)**

The sample index.

</dd> <dt>

*Offset* \[in\]
</dt> <dd>

Type: **int**

An offset applied to the texture coordinates before sampling.

</dd> <dt>

*Status* \[out\]
</dt> <dd>

Type: **uint**

The status of the operation. You can't access the status directly; instead, pass the status to the [**CheckAccessFullyMapped**](checkaccessfullymapped.md) intrinsic function. **CheckAccessFullyMapped** returns **TRUE** if all values from the corresponding **Sample**, **Gather**, or **Load** operation accessed mapped tiles in a [tiled resource](https://msdn.microsoft.com/library/windows/desktop/dn312084#tile). If any values were taken from an unmapped tile, **CheckAccessFullyMapped** returns **FALSE**.

</dd> </dl>

## Return value

Type:

The return type matches the type in the declaration for the [**Texture2DMSArray**](sm5-object-texture2dmsarray.md) object.

## See also

<dl> <dt>

[Load methods](texture2dmsarray-load.md)
</dt> <dt>

[**Texture2DMSArray**](sm5-object-texture2dmsarray.md)
</dt> </dl>

 

 



