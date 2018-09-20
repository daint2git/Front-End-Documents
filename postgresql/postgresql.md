# postgresql

## export
```
C:\Program Files\PostgreSQL\10\bin>pg_dump -U postgres {database name} >"D:\{backup file name}.sql"
```

## import
```
C:\Program Files\PostgreSQL\10\bin>psql -h localhost -p 5432  -U postgres {new database name} <"D:\{backup file name}.sql"
```