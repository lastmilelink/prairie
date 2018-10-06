# united
A distributed framework for state management in microservices

# Why?

Microservices are stateless.  States are stored in DBs.  The problem is that race conditions can occur if writing to DB is not synchronized between different service instances.

Usually, an ACID DB or locking system is used.  But such DBs are usually complex (e.g., MySQL, Oracle) to manage, and data schema change can be difficult.

[NoSQL](https://en.wikipedia.org/wiki/NoSQL) DBs are gaining more attention these days, due to their simplicity and flexibility.  But usually the only concurrency feature they have is atomic operations.  This makes transactional data change a lot harder, especially when state is stored in different tables.

Another novel technology these days is the [actor model](https://en.wikipedia.org/wiki/Actor_model), which is centered around the idea of using actors to encapsulate states and message passing for state changes.  This solves all concurrency issues, since state transtion is handled by one entity (actor) only.

This project is an effort to solve the issue of state management within microservices, so developers can focus on more interesting business logic.

# Goals

* A library (not a framework)
* Managed state transition with ACID properties
* DB agnostic
* Indexing and searching support (by fields in the state)
