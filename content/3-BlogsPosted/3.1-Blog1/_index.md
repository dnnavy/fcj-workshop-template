---
title: "Blog 1"
date: 2026-07-29
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# DSQL SQL Dialect: How Amazon Aurora DSQL Differs from Single-Instance PostgreSQL

Amazon Aurora DSQL is based on open-source PostgreSQL, but due to its distributed nature, there are key differences in supported features and behaviors. Understanding the distinctions between Aurora DSQL and standard PostgreSQL helps mitigate risks and design optimal schemas right from the start.

This article is intended for database architects, developers, and database administrators (DBAs) evaluating Aurora DSQL or working with PostgreSQL workloads on a distributed database.

---

### Similarities

Amazon Aurora DSQL and single-instance PostgreSQL are nearly identical in many aspects:

* **Version & Wire Protocol:** Uses standard PostgreSQL v16 and wire protocol v3.0+.
* **Ecosystem Tools:** Popular tools and libraries such as `psql`, `pgjdbc`, `psycopg`, Django, ActiveRecord, and Hibernate connect and operate seamlessly.
* **Query Execution:** Supported SQL queries return identical results (same `NULL` handling, sort order, arithmetic precision, and string behavior).
* **Core SQL Capabilities:** Standard DML, DDL, transaction controls, and core data types remain intact. Applications using standard SQL statements will enjoy very high compatibility.

---

### Differences and Reasons

Syntax and behavioral differences in Aurora DSQL stem from its distributed, shared-nothing architecture:

* **Primary Key-Ordered Storage:** Traditional PostgreSQL uses a heap structure where rows are stored non-sequentially. In DSQL, data is strictly stored and ordered by the primary key for both base tables and secondary indexes.
* **Compute & Storage Separation:**
  * *Index Key Type Restrictions:* Not all PostgreSQL data types can serve as index keys in DSQL.
  * *Pushdown Operations:* Simple equality and range queries are pushed down to storage. Complex expressions and function calls are evaluated at the compute layer after row retrieval.
  * *Index-Only Queries:* Queries answered entirely from index data avoid an additional storage access round-trip.
* **Optimistic Concurrency Control (OCC):** Replaces traditional MVCC row-locking with OCC (transactions validate for conflicts at commit time). This eliminates locking bottlenecks and serialization errors. The system operates on a single, fixed isolation level: `Repeatable Read`.
* **Asynchronous DDL:** Certain DDL operations execute asynchronously. Constraints include: maximum one DDL statement per transaction, no mixing DDL and DML in the same transaction, and verifying job completion via `sys.jobs` before performing dependent schema changes.
* **IAM-Based Authentication:** Replaces `pg_hba.conf` and password authentication with AWS IAM short-lived tokens.
* **Unsupported Features:** Certain single-instance PostgreSQL features do not have direct equivalents in Aurora DSQL.

---

### Conclusion

Amazon Aurora DSQL shares PostgreSQL's parser, planner, and type system, making the SQL language fundamentally compatible. Successful implementation relies on understanding how its distributed architecture alters execution and storage patterns.

---

### References

* [Amazon Aurora DSQL SQL Dialect Documentation](https://docs.aws.amazon.com/aurora-dsql/latest/userguide/what-is-aurora-dsql.html)
* [SQL feature compatibility in Aurora DSQL](https://docs.aws.amazon.com/aurora-dsql/latest/userguide/working-with-postgresql-compatibility.html)
* [Aurora DSQL and PostgreSQL](https://docs.aws.amazon.com/aurora-dsql/latest/userguide/working-with.html)
* [What is Amazon Aurora DSQL](https://docs.aws.amazon.com/aurora-dsql/latest/userguide/what-is-aurora-dsql.html)

---

**Blog Link:** [Facebook Group Post](https://web.facebook.com/groups/awsstudygroupfcj/permalink/2227753051322988/)