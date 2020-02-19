# File: Collaborate Edit

```fsharp
# Problems:
- Concurrency // concurrently many user are working on the same file

- Shared Resource // firstThouht: Lock // doesnt work here

- Pessimistic Concurrency Control // Lock
- Opttimistic Concurrency Control // Versioning & Conflict Resolution


#Sync Strategies
1. Operational Transformation or Event Passing // Google Docs
2. Differential Syncing // Diff Syncing




1. Operational Transformation Alg or Event Passing // Google Docs
    - Char by Char Syncing
    - Line by Line Syncing
    - every modification is an 'Event'  // Client <--event---> Server
    - Pub/Sub
    - Operations:
        - insert(eachChar, pos)
        - delete(pos)
        - modifyStyle(pos)
        
        
    - Operational Transformation Alg Formula
        // xform(a, b) = a' b'
        

    

2. Differential Syncing // Diff Syncing
    - taking 'diff' applying it on sever --> broadcast to other clients


Client [2copies: originalCopy, modifiedCopy] 
    --> getLocalDiff 
    --> Server [2copies: originalCopy, modifiedCopy]
    --> getServerDiff ==> mergeIt()
    --> sendToOtherClients()




```

