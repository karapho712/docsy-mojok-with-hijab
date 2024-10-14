---
title: Error mongodb WriteConflict
date: 2024-10-12
categories: [HowTo]
tags: [mongodb, howto, error, tutorial]
description: >
  How to create a write conflict error in MongoDB
---

TL:DR

```
> Open the mongo shell (let's call it shell 1)
> session = db.getMongo().startSession();
> session.startTransaction();
> 
> sessionDb = session.getDatabase("testing");
> sessionDb.test.insertOne({ field1: "value1", field2: "value2" });
> session.commitTransaction();
> 
> After the data is inserted into the collection, open a new mongo shell (let's call it shell 2).
> In shell 1, perform a transaction to update the data that we inserted, but do not commit the transaction.
> 
> session = db.getMongo().startSession();
> session.startTransaction();
> 
> sessionDb = session.getDatabase("testing");
> sessionDb.test.updateOne({ field1: "value1" }, { $set: { field2: "updated_value" } });
> In shell 2, try to execute the same command:
> 
> session = db.getMongo().startSession();
> session.startTransaction();
> 
> sessionDb = session.getDatabase("testing");
> sessionDb.test.updateOne({ field1: "value1" }, { $set: { field2: "updated_value" } });
> 
> An error will appear: MongoServerError[WriteConflict]: WriteConflict
> 
> ![alt](/images/shell-2-error-write-conflict.png)
```

