# Review: Designing Data-Intensive Applications

Designing Data Intensive Applications（The big ideas behind reliable, scalable, and maintainable systems)
There are computation-intensive and data-intensive applications. This book is for designing the latter.

When designing data-intensive application, there are 3 main challenges:
- High volume of data
- Complex data
- Constant change in data

###Outline
------

**Part 1: The fundamental ideas around designing a data intensive application.**
- Define scalability, reliability and maintainability
- Data models and query language; when to use which
- Storage engine, how data is layout and how we can retrieve them efficiently
- Serialization and schema evolution

**Part 2: When data is distributed across multiple machines for scalability reasons and the challenges that come with it.**
- Replication
- Partitioning/Sharding
- Transactions
- Problems with distributed systems
- Consistency and consensus in distributed systems

**Part 3: Integrating multiple data systems.**
- Batch processing
- Stream processing
- Opinions on the future of data systems