---
title: Error mongodb WriteConflict
date: 2024-10-12
categories: [HowTo]
tags: [mongodb, howto, error, tutorial]
description: >
  Cara membuat error writeconflict di mongodb
---

TL:DR

```
> Buka mongo shell (kita sebut saja shell 1)
> session = db.getMongo().startSession();
> session.startTransaction();
> 
> sessionDb = session.getDatabase("testing");
> sessionDb.test.insertOne({ field1: "value1", field2: "value2" });
> session.commitTransaction();
>
> setelah data masuk ke collection, buka mongo shell baru (kita sebut saja shell 2)
> pada shell 1 lakukan transaction untuk update data yang sudah kita insert, namun 
kita tidak melakukan commit pada transaction tersebut
>
> session = db.getMongo().startSession();
> session.startTransaction();
> 
> sessionDb = session.getDatabase("testing");
> sessionDb.test.updateOne({ field1: "value1" }, { $set: { field2: "updated_value" } });
> pada shell 2, coba lakukan perintah yang sama 
>
> session = db.getMongo().startSession();
> session.startTransaction();
> 
> sessionDb = session.getDatabase("testing");
> sessionDb.test.updateOne({ field1: "value1" }, { $set: { field2: "updated_value" } });
>
> Error akan muncul: MongoServerError[WriteConflict]: WriteConflict

> ![alt](/images/shell-2-error-write-conflict.png)
```