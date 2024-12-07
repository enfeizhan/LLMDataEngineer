# SQL Difficulty Level

SQL assumes primary importance for the career of data engineers. As a ubiquitous declarative language, it defines data transformation across various technologies, domains, platforms etc in hundreds of variants.

With the assistance of ChatGPT and based on experience from practice we designed a 10-level structure useful for assessing SQL query difficulty.

|Difficulty Level|Skill Summary|Description|Examples|Required Skills|
|---|---|---|---|---|
|1|Basic|Simple, single-command queries requiring minimal SQL knowledge.|CREATE DATABASE, DROP TABLE, SELECT \*|Basic SQL syntax, understanding of database objects|
|2|Simple query|Basic queries with filtering or sorting.|SELECT * WHERE, SELECT * ORDER BY|Basic SQL syntax, filtering, sorting|
|3|Aggregate functions|Queries using SUM, AVG, COUNT, etc.|SUM(salary), AVG(price), COUNT(\*)|Understanding of aggregate functions, grouping|
|4|Joining tables|Queries combining two or more tables.|INNER JOIN, LEFT JOIN, RIGHT JOIN|Understanding of joins, table relationships|
|5|Advanced querying|Queries using subqueries, CTEs (Common Table Expressions), or WITH statements.|Subqueries: SELECT * FROM table WHERE id IN (SELECT id FROM ...)<br>CTEs: WITH sales AS (SELECT * FROM sales)<br>Recursive CTEs: WITH RECURSIVE ...|Understanding of subqueries, CTEs, recursive queries|
|6|System table queries|Queries accessing system tables and views.|SELECT * FROM pg\_tables, SELECT * FROM information\_schema.columns|Understanding of system table structure, metadata analysis|
|7|Windows functions|Queries using ROW\_NUMBER(), RANK(), etc.|ROW\_NUMBER() OVER (ORDER BY), RANK() OVER (PARTITION BY)|Understanding of window functions, data partitioning|
|8|Advanced aggregation|Queries with grouping sets, rollup, cube.|GROUPING SETS, ROLLUP, CUBE|Advanced aggregation techniques, data analysis|
|9|Optimization|Queries optimized for performance.|Indexing, caching, query rewriting|Understanding of database optimization, performance tuning|
|10|Expert|Complex queries requiring advanced SQL features.|Full-text search, spatial queries, JSON/XML processing|Expert-level SQL knowledge, advanced database concepts|
