---
description: 'File: Upload/Download/Sync/History'
---

# File: Upload

```fsharp
# File: Upload/Download/Sync/MaintainHistory

- Break One Single File ---into--> Multiple Chunks
- Store: chunkInfo or chunkHashes in metaDataOfaFile

Dropbox Desktop Client: (Core Components)

Local Components:
    - Watcher
    - Chunker // singleFileIntoMultipleChunks // createHashesForChunk //
    - Uploader // uploadsChunks // chunkCloudUrl
    - Indexer // updates: chunkHash & chunkCloudUrl in DB

    - Local DB 


Cloud Components:
    - Messaging Queue
    - Sync Service
    - MetaData DB & Cache


Pub/Sub Model: //to sync across other devices
    - subscriber: clientsMachines subscribed to particular 'fileMetaChange'
    - publisher: publishes the event to subscribedClients whenever 'fileMetaChange'


```



```javascript
/*
const db = {
    file1: {
        chunks: [ 'chunk1Id', 'chunk2Id', ...],
        chunkMap: {
            chunk1Id: { hashStack: ['chunk1kHash1', 'chunk1kHash2', 'chunk1kHash3'] },
            chunk2Id: { hashStack: ['chunk2kHash1'] }
            // ....
        },
        chunkUrlMap: {
            chunk1kHash1: 'chunk1kHash1Url',
            chunk1kHash2: 'chunk1kHash2Url',
            chunk1kHash3: 'chunk1kHash3Url',
            chunk2kHash1: 'chunk1kHash1Url',
            ...
        }
    }
}
*/
```

{% tabs %}
{% tab title="First Tab" %}
{% embed url="https://www.youtube.com/watch?v=U0xTu6E2CT8" %}
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

