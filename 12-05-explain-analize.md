Analysis
Explain table
This is the table you would see if you ran EXPLAIN without FORMAT=JSON.

Table	Access type	Possible indexes	Index	Index key length	Ref	Rows examined per scan	Filtered	Scalability
f	index		idx_title	514		1000	100.00	O(n)
p	ALL					16500	100.00	O(n)
r	ref	rental_date, idx_fk_inventory_id, idx_fk_customer_id	rental_date	5	sakila.p.payment_date	1	100.00	O(log n)
c	eq_ref	PRIMARY	PRIMARY	2	sakila.r.customer_id	1	100.00	O(log n)
i	eq_ref	PRIMARY	PRIMARY	3	sakila.r.inventory_id	1	100.00	O(log n)
Comments
Are there any full table scans?
Yes.

The following tables are being accessed with a full table scan. MySQL is reading all of the rows in these tables.

Table p with 16500 rows examined per scan.
Are there any full index scans?
Yes.

The following tables are being accessed with a full index scan. MySQL is reading an entire index for these tables.

Table f with index idx_title
Is there anything else interesting?
Yes.

Table f: MySQL is using the 'idx_title' index.
Table r: Matching rows are being accessed. MySQL is using the 'rental_date' index.
Table c: At most one row is accessed from this table using an index. MySQL is using the PRIMARY KEY.
Table i: At most one row is accessed from this table using an index. MySQL is using the PRIMARY KEY.
Estimation (experimental!)
Table	Row count	Estimated row count or scale factor
f	1000	
1000
p	16500	
16500
r	1	
1
c	1	
1
i	1	
1
Latency scale factor: ~1.00x
