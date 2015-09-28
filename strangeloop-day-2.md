#I see what you mean
peter alvero

(key note)

hva man må kunne løse i dist.sys
tror kjetil tok notat. evt. se om videoen legges ut.
(ca 60% ut i talken)

#causality and wall clocks (Jon moore)

lamport clocks. timestamps events. piggybacked 
between processes. 

Hvordan avgjøre hvilken event som skjedde først ?
causality of events


##Hybrid logical clocks: wall clock + lamport clocks

først prøver man å hente klokkeslett. 

hvis klokkeslett > forrige klokkeslett. bruk nytt klokkeslett, sett counter = 0
else: bruk forrige klokkeslett, increment counter +.

man får lokal timestamp + riktig rekkefølge på events i dist.sys.

##NTP: sub-miliseconds syncronization in a datacentre.

problem med NTP: NTP gir opp hvis en klokke er en del i usync med resten. hva skjer da?

Problem med hybrid logical cloks:
i.e man setter feil år på en server. 2051.

da vil alle events på klokkeslett til år 2051, og det kan ikke fikses før det året. Det er kjipt

##Løsning?: Distributed monotonic clocks:

epoch:local-clock:counter

hvis shits hits the fan: øk epoch med en. sett riktig klokkeslett(type tilbake i tid). Win.

Hvordan oppdage at min klokke er kjappere en resten i systemet?

bruke Population protocols til å løse syncronisering av klokker.
(type flokk-behaviour. tenk fugler, fisk, bier etc)

Dette for å løse problemet når NTP ikke funker.

av ett sett av servere:
lagg ett subset: regel. ingen noder i subsettet kan være adjacent.
resten av nodene finner en av nodene i forrige subset som de er adjcent til.
da får man mange tre. Hvert av treene er ansvarlig for å finne en median time.
så vil lederne av treene bli enige om en median clock.
så synkroniserer man.


Det hele koker ned til klokker som er alt for langt foran korrekt tid.
Klokker som er bak korrekt tid kan man bare rette opp.
klokker som er foran korrekt tid vil ødelegge alle timestamps inntil korrekt tid tar igjen den tiden.


#Immutable data architecture with datomic, spark and kafka


#When worst is best, in distributed systems design

designing for the rorst case often penalizes the average case

more and more edge cases -> worse and worse performance.


"alle" systemer er distribuert.
distribution happens over a network.
many things can go wrong:
* packets may be delayed
* packets may be dropped

kan ikke skille på om en pakke er forsinket eller er tapt

Availability addresses delays, drops.

hva hvis servere ikke må snakke sammen? 
(coordination-free systems).
1. Enable infinite scale-out
2. Improve throughput(ingen throughput-tap p.g.a coordination)
3. Ensure low latency. (rtt rundt ekvator er 133.7 ms)
4. Guarantee "always on" response

(harvest in yeild? paper )

Hvorfor communicate ? share state

Common (incorrect) conclusion på cap: availibality is too expensive, only matters during failures, so forget about it

scenario - worst case: 
goal: never read from uncommitted transactions
legacy impl: lock records during access
research quest: is coordination necessary?
result: no! for example, buffer writes until commit
result: oom speedups over classic implementations.

punchline: systems that behave well during network faults can behave better in non-faulty environments too.

bailis.org

##replication helps capacity
replication for å håndtere feilende disker.
gir andre fordeler: nedefritid delployment, større lagringsplass

##tail latency in microservices
99.9th %ile latency: 100ms -> 10ms
avg latency: 1.2ms -> 1.09 ms

som er veldig liten gevinst for en server. ser det aldri.

men har du 100 servere:
avg. latency: 64 ms -> 6.7 ms


your service's corner case may be its consumer's average case.

##Universal design
i.e subtiles
accessibility. w3c there is also a strong business case for accessibiity.

##when does this apply?
When corner cases are common
when environmental conditions are variable
when "normal" isn't as normal as you think

defining "normal" defines our designs.

worst raises though questions:
* what's our scale-out strategy


#Ideology
Gary bernhardt

ideology: things you don't know that you know

Film: Pervert's guide to ideology
dan grossman, CSE341

destroyallsoftware.com/book

#Building scalable stateful services
sateless services

flytter state fra service til databasen

for chatty clients som ofte sender data kan bli load-balansert til forskjellige services - MYE overhead

##Data Locality
send request til maskinen som har dataen du trenger.
Bra for low latency og data-intensive services.

man lagrer staten i servicen slik at nye kall etter samme data ligger "cachet" i servicen.

##Sticky connections & consistency
lettere å ressonere rundt?
###Naiv metode: persisent connection til en maskin  i clusteret.
problem: connection breaks. load balancing.
må implementere back-pressure for å unngo overload.(slik at clienten blir disconnecteed og connecter til en annen server)

###Routing logic
problems: cluster membership, work distribution.
naiv løsning: static cluster membership. (problem hvis maskin detter ned, ikke veldig fleksibelt)

Dynamic cluster membership:
* Gossip protocols(availability)
* Consensus systems(consistency)

Work distribution:
* random placement(write anywhere, read from everywhere)
* consistent hashing
* distributed hash table

##Stateful services in the real world

Scuba - in-memory database. random write, read everywhere.

Uber ringpop 

Orleans. sjekk ut paper

##caution
1. unbounded data structures - killer of distributed systems.
man trenger bounds for å unngå å bruke opp all minnet.
Ikke stol på klient

2. Memory management

3. Reloading state.
first connection - må hente init. data. forsiktig med hvor mye data man henter...
hvordan recovre fra crash?

paper: Fast restarts at facebook. 


#Jay Kreps Kafka

3 paradigms:
1. request / response
2. batch
3. stream processing

##Stream processing
some inputs - some outputs...
it isn't:
transient
approximate
lossy

du kan få stabil, korrekt svar med stream processing.

fremstille det som skjer i ett firma som strømmer av data..

Eks: Retail

input: sales, shipments
output->input: inventory adjustments, price adjustments
output: fraud, analytics

##problems:
* partitioning & scalability
* semantics & fault tolerance
* unifying tables and streams
* time
* re-processing

##Kafka:
distributed, fault tolerant...

kafka is about logs.

logs == streams...

Kafka streams - native stream processing i kafka?

##local state

