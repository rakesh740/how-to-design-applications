# google docs collaborative architecture

## requirements

1. create, storage, update, delete of documents ( onno vasai CRUD )
2. sharing w/ permissions ( edit and view )
3. sharing with link
4. offline access of documents - edit and view in offline
5. versioning of documents
6. profile creation? done with gmail services.
7. notification mail
8. comments on docs
9. spell checks? - external service/ black box

## main challanges

1. users from around the globe software ta use korbe etar jonno minimum latency and bhalo UX
2. eker theke besi lok eksathe ektay jinis er opor kaj korle ekta concurrency problem
3. concurrency problem theke data consistency problem toiri hobe

## Document Database Schema

What would be the database schema of a stored document?

How would we store the metadata of the document?

What technology solution should we use to store documents? File Storage, RDBMS or NoSQL?

How large can a document be?

How do we store a document of any size?

Where should we store this document? What type of database is suitable for this?

Maintaining version history in a document that is updated often is a challenge.

With what frequency should we store versions of this document?

Where do we store these versions?

How do we store changes?

 `Thundering herd problem` :

Problem: How do you take a single job of size X, to be done in Y time, and have a constant flow of X/Y operations in your system?

Challenge: This is a cron job, so the operation is called from time to time.

Solution: Hash the job candidates into Y pieces, and run cron jobs at much smaller intervals.
