There seem to be two main ways to deal with writing many things to clickhouse: client-side batching/throttling, and async.

# sources

https://clickhouse.com/docs/en/cloud/bestpractices/bulk-inserts

https://clickhouse.com/docs/en/cloud/bestpractices/asynchronous-inserts
    -> https://github.com/ClickHouse/clickhouse-java/issues/820
        -> https://github.com/CurtizJ/ClickHouse/blob/f6191b98e74af57ae4ace34c21b269fedcf8ecbd/tests/queries/0_stateless/02015_async_inserts_4.sh#L7
        -> https://github.com/ClickHouse/clickhouse-java/blob/c69c8a8c5a4c273beb3b61b940009072d7a4d85f/clickhouse-jdbc/src/test/java/com/clickhouse/jdbc/ClickHouseStatementTest.java#L124-L155


# snippets

writing a file to clickhouse: https://gist.github.com/den-crane/fd8e0c187fc6f7ee6037d254fb99667b

easy enough to change to tsv format (instead of parquet)