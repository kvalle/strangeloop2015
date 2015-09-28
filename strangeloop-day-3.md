#hopelessness and confidence in distributed systems design

goals of dist.sys

* scale
* failure tolerance

(goals in conflick with eachother)

(DynamoDB post mortem read)


global service discovery

naive: one node. central coordinator
nei: tregt.

husk: fallacies of dist.sys

peter bailies keynoate makerconf?

make things independent

make things independent

folk er smarte, skjønner asynkronitet, kan tilgi deg
(så lenge det ikke er snakk om penger)



#OMG Streams - the data structure we need

Pam Selle

#History
kommer fra unix? seff
pipe operator!

SICP (structure interpretation in computer science)


#Why Streams?
can't/won't hold everything in memory
bandwidth is expensive

represent infinite data

E.G:
* natural numbers
* weather
* user input
* large data sets*
* your heartbeat* 

* = have an end

Not storing things
NOT mutating data

##Two types of stream. Push/pull
Push:

* Callbacks
* Non-blockng
* Downside is possible overload

Pull:
* Iterators
* Blocking 
* Timeout


##Node Streams
node streams are push streams

ES6 generators are resuable and pausable functions

generators: Read once


##Libraries & Emerging standards

BackonJS. HighlandJS RxJS

Browser streams standard:

https://streams.spec.whatwg.org

https://fetch.spec.whatwg.org

#Transactions

book: designing data-intensive applications

opphav: system r

ACID:

##Durability - archive tape, fsync to disk.
today: replication

##Consistency
...

##Atomicity
not about concurrency
Handeling faults
transactions
== abortability

e.g deadlock, network fault, constraint violation, crash/ppower failure --> abort

##Isolation
serializable?

* Read committed (default in postgres, oracle, sql server)
Prevents dirty reads and dirty writes. (don't read uncommitted data. 

how to do cross-service transactions?

* ( A in ACID) transaction abort/rollback at app level
* ( C IN ACID) apologies to the customer ;)
  detect / fix constraint violations
  after the fact, rather than preventing


causal relationshhip (implicit) mellom microservices. (ordering og events...)

typisk: eventually consistent
causual: partial order of read/writes. obays happends-before relationship

Causality can be maintained without global coordination

"Consistent snapshot" in SI(acid)

tenk read committed i databaser. Coordination free.

(har tweetet link til slidedene)


# Sync ???

enforce order.
eliminate accindental nondeterminism(no race cond.)
techniques: locks, mutexes semaphores...

sync == expensive

Difficult cases with sync:

* IoT: low power, limited memory and connectivity
* Mobile Gaming. offline operation with replicated, shared state

Idea: Zero sync as a starting point.
coordination-free computations? gjenganger!

## Distributed computation
partial failure. 

do dist. sys imaginging "single system". 

strong consistency model: enforced through sync

consistency model: analogous to a programming paradigm.

## the avatars of time

time in computing:
    * mutable state in sequential systems. (take different values over time)
    * Nondeterminism in concurrent systems
    * Network latency. 

kan ikke løse mye uten synkronisering(kommunikasjon mellom servere)

men: strong eventual consistency(SEC)

requirement: eventual replica-to-replica communication

order insensitive(commutativity)
duplicate insensitive(idempotent)

how to suceseed:
1. eliminate accidental nondeterminism. 
    CRDT - conflict-free replicated data types. Sets, counters, registers, flags, maps, graphs.
    -> strong eventual consistency per object.
2. retain the properties of functional programming
3. distributed and fault-tolerant runtime

## Lattice processing(Lasp)
* Distributed, deterministic dataflow



