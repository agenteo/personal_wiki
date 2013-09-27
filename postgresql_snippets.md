# Postgresql snippets

## Export query to CSV file
You can either set this to output the following querieS to a file:
```
\o /tmp/moocow.csv
```

Or use COPY if you got access rights:
```
COPY (SELECT foo,bar FROM whatever) TO ‘/tmp/dump.csv’ WITH CSV HEADER
```

If you run into this error: “ERROR: must be superuser to COPY to or from a file,” try this:
```
echo “COPY (SELECT foo from BAR) TO STDOUT with CSV HEADER” | psql -o filename.csv database_name
```

## Current query
```
select current_query from pg_stat_activity
```


## Restore DB
```
pg_restore -v -O -c -d db_name < file
```
http://www.postgresql.org/docs/8.4/static/app-pgrestore.html


## Restore a pgz DB
-Fc

-c drops the tables


## Show tables
```
SELECT column_name FROM information_schema.columns WHERE table_name =='table';
```

or
```
\d
```


## Show columns
```
\d TABLE
```


## Turn pager off
When you want all the results (not paginated):
```
\pset pager
```

## Clear query cache
The only way I found so far is:
* reset the database
```
pg_ctl -D /usr/local/var/postgres restart
pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log start
```

* purge the disk cache
(OSX): purge
(Linux):  sync && echo 1 > /proc/sys/vm/drop_caches
