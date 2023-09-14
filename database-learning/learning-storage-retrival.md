
database needs to do two things get and set data
we wont create a database from scratch but we will select a database for our application. So we need to understand inner workings of each type of storage.

However, first we'll start this chapter by talking about storage engines that are used in the kinds of databases that you're probably familiar with: traditional relational databases, and also most so-called NoSQL databases. We will examine two families of storage engines: log-structured storage engines, and page-oriented storage engines such as B-trees.

This is an important trade-off in storage systems: well-chosen indexes speed up read queries, but every index slows down writes.

 choose indexes manually, using your knowledge of the application's typical query patterns


 