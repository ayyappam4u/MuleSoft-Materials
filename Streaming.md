**Streaming Overview in MuleSoft**    
    In MuleSoft, streaming refers to the method of processing data incrementally as it is received, rather than loading the entire dataset into memory at once. 
    This technique enhances performance by reducing memory consumption, particularly when handling large files. 
    MuleSoft’s streaming capabilities facilitate the efficient management of large datasets, enabling the rapid and effective processing of millions of records.

There are three types of Streams in Mule 4:

 1. Non-Repeatable Stream 
 2. Repeatable In-Memory Stream
 3. Repeatable File Stored Stream


**Non-Repeatable Stream**
  Non-repeatable stream is a data stream that can only be consumed once. Once the stream is read or processed, its data is no longer accessible for subsequent operations.
  You are receiving a file via an HTTP request, and you want to read the contents of the file. After reading the file, you need to process the data, but since the stream is non-repeatable, you cannot read the file again in the same flow.

**Repeatable In-Memory Stream**
  Repeatable In-Memory Stream is a type of stream that allows data to be read and processed multiple times. The data is stored in the application’s memory (heap memory), which works best for small to medium-sized datasets. If the data fits within the memory, it can be accessed again and again during the flow.
  This streaming strategy is different from others because the data is stored directly in memory (heap memory), not on the disk. so if you are passing payload more than heap size, you will get an error saying "Buffer has exceeded".
  ![image](https://github.com/user-attachments/assets/7737d5db-3200-4e53-8a9c-2bb866af7d9d)


**Repeatable File Stored Stream**
  The File-Stored Repeatable Stream is the default strategy that helps save memory when dealing with large files. It first uses a 512 KB buffer in memory to hold the data. If the file is too big for this buffer, it saves the rest to a temporary file on disk, avoiding memory overload. This way, the data can be processed multiple times without using too much memory.
  For example, with an application deployed with 0.1 vCore (512 MB memory), even if you are passing 1 GB payload, the application can execute successfully. This is because the File Stored Repeatable Stream strategy is enabled by default, allowing large payloads to be handled efficiently without exceeding memory limits.

  ![image](https://github.com/user-attachments/assets/af7cc30d-4d4b-4edc-8a22-2b4ae9d25dda)


  Key Considerations:
  1. Avoid using sizeOf(payload) while reading huge files
  2. Use isEmpty(payload)
  3. Dont apply transform directly to huge streams, use batch or for each to avoid out of memory error.

