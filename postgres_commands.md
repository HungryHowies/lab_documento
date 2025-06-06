## select database
```
\c documenso
```
```
SELECT * FROM "public"."User";
```
```
documenso=# DELETE FROM "public"."User" WHERE id=3 RETURNING *;
```
