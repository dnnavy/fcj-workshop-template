---
title: "Blog 1"
date: 2026-07-29
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# DSQL SQL Dialect: How Amazon Aurora DSQL Differs from Single-Instance PostgreSQL

* Amazon Aurora DSQL is based on open-source PostgreSQL, but due to its distributed nature, there are key differences in supported features and behaviors. Understanding the distinctions between Aurora DSQL and standard PostgreSQL helps mitigate risks and design optimal schemas right from the start.
* This article is intended for database architects, developers, and database administrators (DBAs) evaluating Aurora DSQL or working with PostgreSQL workloads on a distributed database.
* Similarities: They are nearly identical in many aspects.
    * Amazon Aurora DSQL uses standard PostgreSQL v16 and wire protocol v3.0+.
    * Popular tools and libraries such as psql, pgjdbc, psycopg, Django, ActiveRecord, and Hibernate can connect and operate normally.
    * SQL queries—assuming they use supported features—will return identical results (same NULL handling, sort order, arithmetic precision, and string behavior).
    * Core SQL features remain intact (standard DML, DDL, transaction control, core data types). If your application uses standard SQL statements for transactional workloads, compatibility is very high.
---
* Differences and Reasons: Syntax and behavioral differences in Aurora DSQL stem from its distributed, shared-nothing architecture.
    * Primary Key-Ordered Storage: This is the most fundamental difference. Traditional PostgreSQL uses a heap storage structure where rows are stored in non-sequential pages unrelated to the primary key. In DSQL, data is stored and maintained in order by the primary key (applying to both tables and secondary indexes, which are ordered by their key columns).
    * Not all operations are pushed down to the storage layer: Aurora DSQL separates compute and storage, which is a key factor enabling automatic scaling and fully serverless operation. This affects the dialect in two specific ways: index key type restrictions (not all PostgreSQL data types can be used as index keys in Aurora DSQL) and pushdown operations (simple equality and range comparisons on supported data types are usually pushed down to the storage layer; complex expressions, function calls, or operations on unsupported data types are evaluated at the compute layer after retrieving rows). Due to this compute-storage separation, a query that can be answered entirely from an index (without fetching base table rows) avoids an additional storage access round-trip.
    * Optimistic Concurrency Control (OCC): PostgreSQL uses MVCC with row-level locks for write operations (concurrent write transactions hold locks that can block each other upon conflict). Aurora DSQL uses Optimistic Concurrency Control (OCC) (transactions execute without locking and are validated for conflicts at commit time). This does not change SQL syntax, but alters application behavior. It helps reduce bottlenecks and serialization errors; read-only transactions do not cause conflicts, and the isolation level is equivalent to PostgreSQL Repeatable Read (this is the single, fixed isolation level provided by the system).
    * Asynchronous DDL: In PostgreSQL, DDL operates synchronously: when CREATE TABLE returns, the table exists. In Aurora DSQL, some DDL statements operate synchronously while others do not. This introduces several dialect constraints: only one DDL statement per transaction; DDL and DML cannot be combined in the same transaction; for asynchronous DDL, you must verify that the DDL operation has completed (by running SELECT * FROM sys.jobs or waiting for the job_id to finish) before executing operations dependent on that schema change. Read and write operations continue without interruption during DDL execution.
    * IAM-Based Authentication (Not Passwords): Aurora DSQL replaces PostgreSQL's pg_hba.conf and username/password login mechanism with AWS Identity and Access Management (IAM). Connections are made using short-lived tokens generated via the AWS SDK. This does not change the SQL language, but changes every connection string and authentication flow in the application.
    * Unsupported Features Affecting the Dialect: Not all PostgreSQL features have direct equivalents in Aurora DSQL.
---
* Conclusion: Amazon Aurora DSQL uses PostgreSQL's parser, planner, and type system, so the SQL language is fundamentally compatible. The focus is on understanding how Aurora DSQL is similar to and different from PostgreSQL.
---
References:
Tài liệu tham khảo:
https://aws.amazon.com/...dsql-sql-dialect-how-amazon.../
---
Blog's link: https://web.facebook.com/groups/awsstudygroupfcj/permalink/2227753051322988/?rdid=4BxzLitflB0OFY8E#
