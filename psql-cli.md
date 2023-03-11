## Grant SELECT for ALL tables

```Shell
grant select on all tables in schema {schema_name} to {username};
```

## Test tables index hits

```Shell
SELECT relname, seq_scan-idx_scan AS too_much_seq, CASE WHEN seq_scan-idx_scan>0 THEN 'Missing Index?' ELSE 'OK' END, pg_relation_size(relname::regclass) AS rel_size, seq_scan, idx_scan FROM pg_stat_all_tables WHERE schemaname='public' AND pg_relation_size(relname::regclass)>80000 ORDER BY too_much_seq DESC;
```

## Remove rows from table that don't match expression (text data type)

```Shell
DELETE FROM {TABLE} WHERE NOT ({COLUMNNAME} ~ '^\d{10}$');
```
