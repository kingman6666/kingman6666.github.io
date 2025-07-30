# DB action of MongoDB

```
// collection = new MongoClient(url) > connect() > db(name) > collection(name)

// Search: await collection.find({}).toArray();
// Insert: 
// Update: 
// Delete: 
```

### client app :
```
fetch(db-server-addr, { method: 'GET/POST/...' })
```

## Server app :

```
// file system :

|----server.js
|----routes/xxx.js
|----controllers/xxxCoontroller.js
```

```
// server.js
import express form 'express';
import xxxRoute from './routes/xxx.js';

let app = express()
app.use('api-url', xxxRoute)
app.listen(PORT)
```

```
// routes/xxx.js
import { Router } from 'express';
import { xxxGetHandle, xxxPostHandle } from "../controllers/xxx.js";

let router = Router()
router.get('/', xxxGetHandle)
router.post('/', xxxPostHandle)

```

```
// controllers/xxxCoontroller.js
import { MongoClient } from 'mongodb'

export const xxxGetHandle = async (request, response) => {
  try {
    let client_mongo = new MongoClient(db_url);
    await client_mongo.connect()
    const mongoDB = client_mongo.db('db_1')
    const collection = mongoDB.collection('xxxCollection')
    const xxxData = await collection.find({}).toArray();

    response.status(200).json({
      suceess: true,
      data: products,
      count: products.length
    })
  } catch (error) {
    response.status(500).json({
      success: false,
      message: 'error...',
      error: error.message
    });
  }
}
```