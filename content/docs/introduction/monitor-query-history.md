---
title: Monitor query history
subtitle: View and analyze query history for your Neon database
enableTableOfContents: true
updatedOn: '2025-03-05T21:09:38.754Z'
---

You can monitor query history for your Neon project from the **Monitoring** page in the Neon Console.

1. In the Neon Console, select a project.
2. Go to **Monitoring**.
3. Select the **Query History** tab.

The **Query History** view shows the top 100 previously run queries for the selected **Branch**, **Compute**, and **Database**. Queries are grouped by their normalized form, with identical queries shown as a single row with a **Frequency** column indicating the number of times that query has been executed. Queries can be sorted by **Frequency** or **Average time**. Use the **Refresh** button to load the latest queries.

![Neon query history tab](/docs/introduction/query_history.png)

The **Query History** view is powered by the `pg_stat_statements` Postgres extension, installed on a system managed database in your Postgres instance. Query history includes all queries run against your database, regardless of where they were issued from (Neon SQL Editor, external clients, or applications).

<Admonition type="note" title="query restore window">
In Neon, data collected by the `pg_stat_statements` extension is not retained when your Neon compute (where Postgres runs) is suspended or restarted. For example, if your compute scales down to zero due to inactivity, your query history is lost. New data will be gathered once your compute restarts.
</Admonition>

## Running your own queries

To run your own queries on `pg_stat_statements` data, you can install the `pg_stat_statements` extension to your database and run your queries from the [Neon SQL Editor](/docs/get-started-with-neon/query-with-neon-sql-editor) or any SQL client, such as [psql](/docs/connect/query-with-psql-editor). For details on `pg_stat_statements`, including how to install it, what data it collects, and queries you can run, refer to our [pg_stat_statements](/docs/extensions/pg_stat_statements) extension guide.
