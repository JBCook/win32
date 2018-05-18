---
Description: Processing Data in a DMO
ms.assetid: '715482d9-23f4-40d0-9c09-7a81e148c543'
title: Processing Data in a DMO
---

# Processing Data in a DMO

This section explains how to process a stream of data using a DMO. The steps listed in this section are the default behavior; all DMOs must support the methods described here. These methods use separate buffers for input and output. Some DMOs also support in-place processing, using a single buffer. For more information about in-place processing, see [In-Place Processing](in-place-processing.md).

**Allocating Buffers**

The client is responsible for all buffer allocation. After you set the media types on the DMO, query the DMO for each stream's buffer requirements. These can change depending on the media type. For each stream, call the [**IMediaObject::GetInputSizeInfo**](imediaobject-getinputsizeinfo.md) or [**IMediaObject::GetOutputSizeInfo**](imediaobject-getoutputsizeinfo.md) method. These methods return the following information:

-   Minimum buffer size, in bytes.
-   Alignment requirements, if any. A buffer is aligned if the start address is a multiple of some specified integer.
-   The maximum amount of data the DMO will hold for lookahead. This number applies only to input streams. For some kinds of data (for example, MPEG encoding), a DMO might need to look forward in the stream. The lookahead value indicates how much input data the DMO will require before it can produce output.

The client must allocate buffers that match these requirements. In addition, the DMO might have requirements about how the client packages the input data. For example, the DMO might require each buffer to contain exactly one sample (or video frame). To determine these requirements, call the [**IMediaObject::GetInputStreamInfo**](imediaobject-getinputstreaminfo.md) method. The [**IMediaObject::GetOutputStreamInfo**](imediaobject-getoutputstreaminfo.md) method returns similar information about an output stream.

In the default streaming model, the client does not pass raw buffer pointers to the DMO. Instead, it uses a lightweight COM object that exposes the [**IMediaBuffer**](imediabuffer.md) interface. The **IMediaBuffer** interface acts as a COM wrapper for a block of memory. Because it is a COM object, it supports reference counting, which helps to ensure that buffers are not released while still in use.

> [!Note]  
> The **IMediaBuffer** interface serves a function similar to the **IMediaSample** interface in DirectShow.

 

The client must implement the **IMediaBuffer** object. For more information, see [Implementing IMediaBuffer](implementing-imediabuffer.md).

**Processing the Data**

To process data, do the following:

1.  For each input stream, fill a buffer with input data.
2.  Call [**IMediaObject::ProcessInput**](imediaobject-processinput.md) to deliver each buffer.
3.  Call [**IMediaObject::ProcessOutput**](imediaobject-processoutput.md) to process the data. This method takes an array of buffers, one for each output stream.
4.  Repeat until there is no more input data.

The **ProcessInput** method accepts input for one stream at a time. Typically the method returns immediately, and the DMO holds a reference count on the **IMediaBuffer** object. It releases the object after it processes all of the data in the buffer, or when the application flushes the DMO. Do not re-use a buffer until the DMO has released it. To determine whether an input stream can accept more data, call the [**IMediaObject::GetInputStatus**](imediaobject-getinputstatus.md) method. This method returns the DMO\_INPUT\_STATUSF\_ACCEPT\_DATA flag if the stream can accept more input.

The **ProcessOutput** method generates output for all of the output streams at once. The application passes in an array of [**DMO\_OUTPUT\_DATA\_BUFFER**](dmo-output-data-buffer.md) structures, one for each output stream. Each structure in the array has a pointer to an **IMediaBuffer** object. The DMO writes as much output data as it can into the buffers. It also sets various flags to report the status of the operation. The DMO\_OUTPUT\_DATA\_BUFFERF\_INCOMPLETE flag indicates the DMO can produce more output from the existing input. In that case, the client can call **ProcessOutput** again. Otherwise, it should call **ProcessInput** with more input data. The DMO never modifies the data in the input buffers; it writes only to the output buffers.

After you have delivered all of the data to an input stream, call the [**IMediaObject::Discontinuity**](imediaobject-discontinuity.md) method. The DMO does not accept further input to that stream until you process the remaining output (or flush the DMO).

At any point after streaming begins, the DMO is able to receive input or produce output, or both. Therefore, either **GetInputStatus** returns DMO\_INPUT\_STATUSF\_ACCEPT\_DATA, or **ProcessOutput** returns DMO\_OUTPUT\_DATA\_BUFFERF\_INCOMPLETE. The application keeps data flowing by testing for these flags and calling **ProcessInput** or **ProcessOutput** accordingly. To interrupt the data flow, call the [**IMediaObject::Flush**](imediaobject-flush.md) method. This method causes the DMO to discard any buffers it is holding internally.

## Related topics

<dl> <dt>

[Directly Hosting a DMO](directly-hosting-a-dmo.md)
</dt> <dt>

[In-Place Processing](in-place-processing.md)
</dt> </dl>

 

 


