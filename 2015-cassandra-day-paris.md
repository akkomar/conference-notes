* counters are expensive, they do read-before-write (like lightweight transactions), although they are getting better in next versions (2.1?)
* multi DC - separate clusters for analytics/tests

* consistency levels apply both to Read and Write - CHECK!
* level ALL - fails if replica is down

* system keyspace - schema is stored there

* Primary key(A, B, C)
** A - partition (brackets for multi-column partition key)
** B,C - clustering columns (how to store data on disk)

* cassandra-stress - load test schema apart from the app

* thrift exposes row disk format (gonna change in 3.0)

* cassandra cluster manager (ccm) - github

* cassandra trace - shows communication between nodes

* don't use row cache if you are retrieving only subset of columns (it's caching whole row)
