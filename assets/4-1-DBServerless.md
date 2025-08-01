# DB Action of serverless ( vercel:neon )

## server-side db action in API ( called in client-side )
```
import { neon } from "@neondatabase/serverless";

let neonQuery = neon(process.env.DATABASE_URL)
let data = await neonQuery`SELECT * FROM table-name`;
let res = await neonQuery`INSERT INTO table-name (k1, k2) VALUES (v1, v2)`;

// Search: SELECT * FROM table-name
// Insert: INSERT INTO table-name (column1, column2, ...) VALUES (val1, val2, ...)
// Update: UPDATE table-name SET column1 = val1, column2 = val2 WHERE condition(eg: id=1)
// Delete: DELETE FROM table-name WHERE condition(eg: id=1)
```

## server-side refresh client-side's page
```
import { revalidatePath } from 'next/cache';

revalidatePath('/client-route')
```


