Logikk, programmeringskonsepter, typeteori

Philip Wadler, på scenen, med superhelt-kappe og lambda på brystet.
Morsomt og underholdene, lærerikt, og tankeprovoserende.

Part 1: History-lessen on programming concepts and type theory.

	Lambda calculus
	Recursive functions
	Turing machines

	Alle kom nesten samtidig. Hvorfor?

	David Hilbert 1862-1943
	Put all mathematiccians out of business -> The decision problem
	Basis: Logic is complete

	Gödel beviser imcompleteness, og Hilbert er screwed.

	> This statement is not provable

	Alonzo Church <- Lambda calculus

	L, M, N ::== X
			|   (lambda N. N)
		    |   (L M)


	Lambda has finally cought up with where Chrch was in the 1930s.

	Turing: Anything a computer (person) can do can be done by a turing machine.

	Er matematikk oppdaget eller oppfunnet?

	At alle tre kom opp med samme definisjon på computability tyder på første.


Part 2: Propositions as types:

	Gentzen (1935): 
	Natural deduction - The main form of deduction used today
	(Upside down forall a)

	Introduserer deduksjonsregler
	Simplifiserer beviser

	(simply) Typed lambda-calculus

	programmer som logiske deduksjons-bevis
	Typene i typet lambdakalkulus korresponderer direkte til Gentzens natural deduction beviser

		propositions -> types
		profs -> programs
		normalization/simplification of proofs -> evaluation of programs

		-> The curry-howard correspondence

	Hva med forall og there-exists? -> løsningen fører oss til dependent types

	> Every good idea will be discovered twice. Once by a logician, and once by a computer scientist.

	> Most of you use programming languages that are invented. And you can tell, can't you?! This is my invitation to you, to use programming languages that are discovered.

