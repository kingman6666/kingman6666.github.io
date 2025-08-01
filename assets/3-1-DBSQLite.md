# DB action of SQLite in Server-side

```
// db = sqlite.open({file-name})

// Search: db.all(SELECT * FROM table-name)
// Insert: db.run(`INSERT INTO table-name (column1, column2, ...) VALUES (?, ?)`, [val1, val2]) 
// Update: db.run(`UPDATE table-name SET column1 = ?, column2 = ? WHERE id = ?`, [val1, val2, id])
// Delete: db.run(`DELETE FROM table-name WHERE id = ?`, [id])
```

#### code demo
```
// db.js

import sqlite from "sqlite3";
import { open } from "sqlite";

let db = null

export default async function getDB() {
  if (!db) {
    db = await open({
      filename: './xxx.db',
      driver: sqlite.Database
    })
  }

  await db.exec(`
    CREATE TABLE IF NOT EXISTS table-name (
      id INTEGER PRIMARY KEY AUTOINCREMENT,
      name TEXT NOT NULL,
      desc TEXT
    )
  `)

  return db
}
```

```
// api.js

import getDB from "./db"

function xxx() {
  let db = await getDB()

    //get
  await db.all(`SELECT * FROM table-name`)
    //post
  await db.run(`INSERT INTO table-name (column1, column2) VALUES (?, ?) RETURNING *`, [val1, val2])
    //delete
  await db.run(`DELETE FROM table1 WHERE id = ?`, [id])
}

```